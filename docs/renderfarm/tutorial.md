# Sim-Plates Renderfarm Video Tutorial Script

This is a presenter script for a full walkthrough video, roughly 30 minutes long. It is written so you can follow it while recording: each section includes the goal, what to show on screen, and suggested narration.

For reference docs, see the [User Guide](user-guide.md) and [Farm Machine Monitoring](farm-machine-monitoring.md).

## Problems This Solves

Open the video by explaining that this app exists because Octane Standalone is excellent at rendering, but it does not cover the full production workflow around queueing, coordinating, monitoring, previewing, and reviewing many renders across many machines.

### Say

"Before I go through the app, I want to explain the problems it is solving. Octane Standalone can render, but on a real production job we also need to coordinate machines, manage passes, monitor progress, estimate finish time, preview frames, and review output. This app wraps those production needs into one workflow."

"It is also intentionally easy to set up. It works with any shared storage that all machines can read and write to, like a local NAS, Dropbox, Google Drive, or another synced/shared folder."

### Render Problems

- Queue multiple projects and render targets, then let all selected machines contribute to the work.
- Delete unwanted passes automatically, such as Denoise Albedo and Denoise Normal.
- Organize render passes into folders.
- Override render settings when needed, including resolution, samples, and colorspace.
- Use PC or Mac as a Controller or Worker.
- Build a Mac-based Octane render farm workflow with this app. As of this writing, Octane Network Render Daemons are not a practical Mac option in this pipeline, so direct Controller/Worker rendering is the straightforward Mac farm path.

### Control Problems

- Start, cancel, monitor, and preview many machines from one master machine, either PC or Mac.
- See live status for all app machines and Octane Daemon clients.
- Keep Controller-only machines lightweight because they do not need Octane CLI.

### Preview Problems

- Easily see the last rendered frame.
- Cache preview files for real-time playback at full, half, or quarter resolution.
- Cache and inspect specific render passes instead of accidentally previewing the wrong output.
- Support 360 preview workflows.
- Use Mac Metal accelerated playback where available.
- Export ProRes or H.264 videos for QC.

### Monitor Problems

- Estimate finish time more accurately by including real completed-frame timing instead of relying only on Octane's render-time estimate. Octane does not include loading and saving time, so its estimate can be far off even on a single machine, and it does not estimate across multiple machines.
- Show status for all machines and projects from a central dashboard.
- Publish a mobile-friendly status page so progress can be checked from a phone.

## Recording Prep

Before recording, have these ready:

- The controller machine open, preferably the Mac if that is the real production workflow.
- At least one render PC open and visible in Farm Machines.
- A small test `.ocs` or `.orbx` project that can render quickly.
- A known exports folder with a few frames already rendered, so Preview can demonstrate Live Render and Frame Playback.
- The public status page open on a phone or browser tab: `https://docs.sim-plates.com/farm-status/`.
- Preferences already mostly configured, but reset enough fields that you can demonstrate the important parts.

Avoid recording private tokens, passwords, or customer-only paths. If the token field is shown, keep it blank or blur it in post.

## Chapter Plan

```text
00:00 - 04:00  What the app is for and problems it solves
04:00 - 07:00  Machine roles
07:00 - 10:00  Farm Directory, status, and control folders
10:00 - 13:00  Controller setup
13:00 - 16:00  Worker setup
16:00 - 20:00  Build a project queue
20:00 - 23:00  Start a farm render
23:00 - 26:00  Monitor machines, ETA, and storage
26:00 - 29:00  Preview, cache, passes, playback, fullscreen
29:00 - 31:00  Mobile/public status
31:00 - 33:00  Cancel, kill, troubleshooting, recap
```

It is fine if the final video lands around 30 to 35 minutes. The important thing is that the viewer sees one complete loop: configure, start, monitor, preview, and recover.

## 00:00 - 04:00 - Introduction And Problems Solved

### Show

- App open on the Render Monitor or Project Setup page.
- A worker machine visible in Farm Machines if possible.
- Optional quick flash of the phone status page.
- A quick cut through Project Setup, Render Monitor, Preview, and Mobile/Public Status if you want a fast overview montage.

### Say

"This is the Sim-Plates Renderfarm app. The goal is to make Octane command-line rendering and small render-farm coordination manageable from one interface. We can build a queue, send it to render machines, monitor progress, preview frames while they arrive, and optionally publish a phone-friendly status page."

"The reason this exists is that Octane Standalone is great at rendering, but there are a lot of production problems around the render that it either does not solve, or does not solve well enough for a multi-machine workflow."

"For example, I can queue multiple projects and render targets, have all machines contribute, delete unwanted passes, organize passes into folders, override settings like resolution or samples, and use either a PC or Mac as the controller."

"On the control side, I can start, cancel, monitor, and preview many machines from one master machine. I can also see the live status of Octane Daemon clients."

"On the preview side, I can see the last rendered frame, cache previews at full, half, or quarter resolution, inspect specific render passes, work with 360 material, use accelerated playback where available, and export ProRes or H.264 videos for QC."

"And for monitoring, the ETA is based on real completed-frame timing. Octane's own estimate does not include loading and saving time, so it can be way off even on one machine, and it does not estimate across a whole farm. This app gives me a central monitor and an optional mobile dashboard."

"The main thing to understand is that the project file and the machine setup are separate. The project says what to render. The machine settings say how this particular computer finds Octane, projects, exports, and the shared farm folders."

"In this walkthrough, I am going to set up the roles, explain the shared Farm Directory, create a project, start a farm render, monitor it, preview frames, and show the mobile status workflow."

### Checkpoint

The viewer should understand that this is not just a render launcher. It is a production layer around Octane for queueing, control, preview, monitoring, and review.

## 04:00 - 07:00 - Machine Roles

### Show

- Open **Preferences > Workflow**.
- Show **Machine Role** dropdown.

### Say

"The first decision is the machine role. There are five roles."

"Single Machine is the simplest. It renders only on this computer and hides the farm-control parts."

"Controller is the role I use for a Mac or any machine that should manage the farm but not render. A Controller can edit projects, start jobs, cancel jobs, generate shared preview cache, and publish status. It does not need Octane CLI, which is important on Mac."

"Controller/Worker is for a render PC that can do both things. It can control the farm, but it can also render locally."

"Worker is for a machine that waits for commands from a controller and renders project jobs."

"Daemon is for OTOY Octane Network Render Node daemon management. That is separate from direct `.apo` project rendering."

### On-Screen Example

```text
MacBook Pro: Controller
Main render PC: Controller/Worker or Worker
Extra render PCs: Worker
Network Render machines: Daemon
```

### Say

"For a normal Sim-Plates setup, the MacBook is usually Controller, the main render PC is Controller/Worker or Worker, and additional render machines are Workers or Daemons depending on whether they render project frames directly or run Octane Network Render Node."

### Checkpoint

The viewer should know which role to choose for each computer.

## 07:00 - 10:00 - Farm Directory, Status, And Control

### Show

- Finder or Explorer open to the shared folder containing `_farm_status` and `_farm_control`.
- Preferences or Add / Update This Machine showing Farm Directory.

### Say

"The most important shared path is the Farm Directory. This is the stable shared folder every participating app needs to see."

"Inside it are two folders: `_farm_status` and `_farm_control`."

```text
_farm_status
_farm_control
```

"`_farm_status` is where each machine writes heartbeat files. That is how the controller knows which machines are online, rendering, idle, stale, and what project or target they are working on."

"`_farm_control` is where the controller writes commands. Start Queue, Cancel Render, and Start Daemon commands go here. Worker machines poll this folder, claim commands meant for them, and write results."

"Project Root and Exports Root can be different on each machine because each computer might mount Dropbox or storage differently. But the Farm Directory should usually be the same shared location for every project and every participating machine."

### Say

"If machines do not see each other, this is the first thing to check. Are they pointed at the same Farm Directory, and can they read and write to it?"

### Checkpoint

The viewer should understand that Farm Directory is the shared communication hub.

## 10:00 - 13:00 - Controller Setup

### Show

- Open app on Mac or controller machine.
- Open **Preferences > Workflow**.
- Open **Add / Update This Machine**.

### Say

"Now let us set up the controller. In this example, I am using the Mac as Controller. This machine is not going to render frames, so it does not need Octane CLI."

### Steps To Show

1. Set **Machine Role** to **Controller**.
2. Open **Add / Update This Machine**.
3. Show Machine name.
4. Set Project Root.
5. Set Exports Root.
6. Set Farm Directory.
7. Click **Test Paths**.
8. Save.

### Say

"Project Root is where this machine sees the projects. Exports Root is where this machine sees rendered outputs. Farm Directory is the stable shared folder with `_farm_status` and `_farm_control`."

"Because this is Controller-only, Octane CLI is not required. If you see Octane CLI hidden or marked not required for Controller role, that is correct."

### Optional Note

"A PC can also be Controller-only. The idea is not Mac-specific. Controller simply means this app can manage the farm without being expected to render locally."

### Checkpoint

The controller should have valid project/export roots and a shared Farm Directory.

## 13:00 - 16:00 - Worker Or Controller/Worker Setup

### Show

- Switch to render PC or show screenshots.
- Open Preferences.
- Open Add / Update This Machine.

### Say

"Now we set up a render machine. This is the machine that actually needs Octane CLI."

### Steps To Show

1. Choose **Worker** or **Controller/Worker**.
2. Confirm Octane CLI points to `octane-cli.exe`.
3. Open **Add / Update This Machine**.
4. Set Project Root for this PC.
5. Set Exports Root for this PC.
6. Set the same Farm Directory as the controller.
7. Click **Test Paths**.
8. Save.
9. Leave the app open.

### Say

"The key detail is that paths can be different per machine. The Mac might see Dropbox under `/Users/alex/...`, while the PC might see it as `E:\...` or `Z:\...`. That is fine. Each machine saves its own local roots."

"The project can still be shared because the app resolves project and output paths through each machine's local settings."

"Once this is saved and the app is open, the machine should appear in Farm Machines on the controller."

### Checkpoint

The worker should appear in Farm Machines with a fresh Last Seen time.

## 16:00 - 20:00 - Create A Project Queue

### Show

- Controller app, **Project Setup** tab.
- Add Scene.
- Show queue rows and project details.

### Say

"Now we will create a project. The project file stores what to render: scenes, targets, ranges, passes, frame order, and queue order."

### Steps To Show

1. Click **Project Setup**.
2. Click **Add Scene**.
3. Choose an `.ocs` or `.orbx`.
4. Choose the exports folder.
5. Confirm render target names.
6. Set frame range.
7. Show target rows if the project has multiple targets.
8. Set frame order.
9. Show optional render passes.
10. Save the project.

### Say

"Frame order can be forward, backward, or smart pick. Backward starts from the high frame number. Smart Pick spreads work around more randomly."

"For render passes, the rule is simple: checked means keep, unchecked means delete, if cleanup is enabled. This is safer than thinking in terms of delete flags."

"If you have a pass you specifically want to preview, that is set in Preferences as Preferred Pass. We will come back to that in the Preview section."

### Show

- **Preview Farm Plan** or **Dry Run**.

### Say

"Before starting, I like to use Preview Farm Plan or Dry Run. This gives me a sanity check: which projects are active, which frames are going to render, and which machines are expected to participate."

### Checkpoint

The project should be saved and ready to start.

## 20:00 - 23:00 - Start A Farm Render

### Show

- Click **Start Queue**.
- Show machine picker.
- Show command summary.

### Say

"When I click Start Queue in a farm setup, the app asks which machines should receive the command."

"I can choose local rendering, remote machines, or both depending on the role and setup."

"The command summary is important. This is the last safety check before anything starts. It shows target machines, project details, storage warnings, and what the app is going to ask each machine to do."

### Steps To Show

1. Click **Start Queue**.
2. Select one or more worker/controller-worker machines.
3. Review storage warnings.
4. Click **OK**.
5. Switch to Render Monitor.

### Say

"The controller writes a command JSON into `_farm_control`. The worker sees it, writes a claim, resolves the paths through its own machine settings, and starts only if it is idle."

"If a selected machine is already rendering, it reports busy and keeps doing what it was already doing. Farm start does not cancel active work."

### Checkpoint

At least one worker should begin rendering or report a useful result.

## 23:00 - 26:00 - Monitor Machines, ETA, And Storage

### Show

- Render Monitor top cards.
- Farm Machines table/cards.
- Bottom status bar.
- ETA panel.

### Say

"Render Monitor is where I watch the active job. The top section shows current project, progress, current frame, frames remaining, last frame time, and status."

"The ETA is estimated from completed frames and marker timestamps. Early in a render, it is a rough guide. Around one percent complete, it starts becoming useful. Around five percent, it should be much closer. Around fifteen percent, for consistent frame sizes, it is usually pretty dependable."

"The Farm Machines area shows each machine's role, state, project, target, last frame, free storage, and last seen time."

### Explain States

- **Rendering**: actively rendering or connected.
- **Idle**: app is open but not rendering.
- **Online**: app is reachable.
- **Stale**: no recent heartbeat.
- **Offline**: daemon process is not found or the machine is not active.

### Say

"Stale does not always mean a machine is broken. It means the app has not written a fresh heartbeat recently. The app might be closed, Dropbox might be delayed, the machine might be offline, or it might be pointed at a different Farm Directory."

"Storage estimates are warning-only. If a selected machine looks low on space, the app warns you, but it does not block you. That is intentional because sometimes the estimate is conservative or you already know the destination is okay."

### Checkpoint

The viewer should know how to read live render health.

## 26:00 - 29:00 - Preview, Cache, Passes, Playback, Fullscreen

### Show

- Preview page.
- Live Render, Frame Playback, Video Playback tabs.
- Zoom controls and Fullscreen.
- Preferences > Preview.

### Say

"The Preview page is for inspecting output without leaving the app. There are three modes."

"Live Render shows the most recently completed frame the app can find. This matters for backward and smart-pick renders. If a worker renders 1440, then 1439, then 1438, Live Render follows what actually finished most recently."

"Frame Playback plays cached preview images."

"Video Playback plays generated proxy or full-res preview videos."

### Show Controls

- Play/Pause.
- Loop.
- Reveal Cache.
- Clear Cache.
- Clear Video Cache in Video Playback.
- Zoom out, zoom in, Fit, 100%.
- Fullscreen.

### Say

"Space plays and pauses. Left and right arrows step frames. Command or Ctrl plus equals zooms in, and Command or Ctrl minus zooms out. Fit fits the image to the viewer. 100 percent shows actual size. Fullscreen opens the fullscreen preview window with the same basic controls."

"Preview cache is created from EXR frames. JPEG is the default at quality 92 because it is much smaller and usually better for Dropbox and playback. PNG is still available when you need lossless cache frames."

"Cache generation happens in the background. When the app is converting EXRs, you will see Creating Cache, and when possible it shows a count like 34 out of 85."

### Preferred Pass

Show **Preferences > Preview > Preferred Pass**.

### Say

"Preferred Pass is how you tell the preview which pass you want to see. If I type `Output AOV 5`, the preview uses only Output AOV 5. If that pass is not on disk yet, it waits instead of showing some other pass by accident."

"You can also use names like `AOV 6`, `Emission`, or `Light ID 18`. The app tries to normalize common pass names, but the safest option is to type the pass name as it appears in the output folder."

### Checkpoint

The viewer should understand preview modes, cache format, preferred pass, and playback controls.

## 29:00 - 31:00 - Mobile / Public Status

### Show

- Preferences > Mobile / Public Status.
- Public page in browser or on phone.

### Say

"If you want to check progress from a phone, the controller can publish a condensed status document to a web endpoint."

### Steps To Show

1. Open **Preferences > Mobile / Public Status**.
2. Enable **Publish farm status to a web endpoint**.
3. Enter Publish URL.
4. Enter token if required.
5. Click **Test Publish**.

### Sim-Plates Values

```text
Publish URL: https://sim-plates-farm-status.alex-6ab.workers.dev
Token secret name in Cloudflare: FARM_STATUS_WRITE_TOKEN
Public page: https://docs.sim-plates.com/farm-status/
```

### Say

"The app sends the token as `X-Farm-Status-Token`. If the public page is old, it usually means publishing is not enabled, the controller app is closed, the URL is wrong, the token does not match the Worker secret, or the last publish failed."

"Cloudflare secrets cannot be read back after they are saved. If the token is lost, reset the `FARM_STATUS_WRITE_TOKEN` secret and paste the same new value into the app."

### Checkpoint

The viewer should know where the public page gets its data and how to test publishing.

## 31:00 - 33:00 - Cancel, Kill, Troubleshooting, Recap

### Show

- Cancel Render button.
- Tools menu with Kill Octane.
- Farm Machines stale row if available.

### Say

"For stopping work, use Cancel Render first. Cancel asks the selected app machines to stop their active local render and release the current lock when possible."

"Kill Octane is more forceful. It is for stuck or orphaned Octane processes on render-capable machines. Controller-only machines do not need render-only controls."

### Troubleshooting Summary

Say:

"If machines do not appear, check that the app is open, the role is correct, the Farm Directory is the same shared folder, and Dropbox or the network share is syncing."

"If public status is old, use Test Publish and confirm the URL and token."

"If Preview shows the wrong pass, set Preferred Pass and make sure the pass exists on disk."

"If ETA differs between machines, remember that the controller builds its view from status files and completed frames. A worker may know something locally before the controller sees the latest heartbeat."

### Closing

"The overall pattern is: set machine roles, make sure everyone shares the same Farm Directory, build and save the project, preview the farm plan, start the queue, monitor the farm, and use Preview or the mobile page to keep an eye on progress."

"Once those pieces are solid, adding more machines is mostly repeating the machine setup: local roots, same Farm Directory, correct role, and leave the app open."

## Optional Add-On Segments

Use these if you want a longer 35 to 45 minute version.

### Optional: Single Machine Workflow

Show setting role to Single Machine, creating a project, and starting locally. Emphasize that this is best for test renders or a user with one render PC.

### Optional: Daemon Workflow

Show Daemon role, OTOY folder detection, Start Daemon, Install Daemon, and daemon status. Explain that Daemon is for Octane Network Render Node work and does not render `.apo` frames directly.

### Optional: Missing Frames And ETA Tools

Show Tools > Missing Frames and Tools > Estimate ETA. Explain that these reports go to the Logs tab and do not replace the Live Log.

### Optional: Support Bundle

Show Tools > Copy Diagnostics and Tools > Export Support Bundle. Explain that this is what to send when troubleshooting a machine setup or render failure.

## Quick Reference

### Role Cheat Sheet

```text
Single Machine      Local-only render
Controller          Manage farm, no local render required
Controller/Worker   Manage farm and render locally
Worker              Receive jobs and render
Daemon              Manage Octane Network Render Node
```

### Farm Directory Must Contain

```text
_farm_status
_farm_control
```

### Preview Shortcuts

```text
Space              Play/Pause
Left/Right Arrow   Step frames
Command/Ctrl =     Zoom in
Command/Ctrl -     Zoom out
Fit                Fit to viewer
100%               Actual size
Fullscreen         Larger preview window
```

### Public Status

```text
Publish URL: https://sim-plates-farm-status.alex-6ab.workers.dev
Worker secret: FARM_STATUS_WRITE_TOKEN
Public page: https://docs.sim-plates.com/farm-status/
Header: X-Farm-Status-Token
```
