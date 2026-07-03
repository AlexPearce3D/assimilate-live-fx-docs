# Farm Machine Monitoring

The app shows farm machine status by reading small JSON heartbeat files from shared folders. This is separate from Octane's own Network Render UI. Every participating app writes status into the shared status folder, and controllers read those files.

## Roles

### Controller

A **Controller** is a machine running `apOctane_RenderFarm` with the **Controller** role.

Controllers can:

* Edit `.apo` projects.
* Start local queues.
* Send Start Queue commands to workers/controllers.
* Send Cancel Render commands.
* Send Start Daemon commands to daemon machines.
* Receive commands from other controllers.
* Publish their own status.
* Publish mobile/public status when configured.

Controller-only machines do not need Octane CLI. This is useful for a Mac or office PC that should control the farm and generate preview cache, but should not render frames locally.

### Controller/Worker

A **Controller/Worker** is a machine running `apOctane_RenderFarm` with the **Controller/Worker** role.

Controller/Worker machines can:

* Do everything a Controller can do.
* Render `.apo` project queues locally.
* Listen for shared farm-control commands from another controller.
* Publish local render progress while rendering.

Use this role for a render PC that should sometimes be operated directly.

### Worker

A **Worker** is a machine running `apOctane_RenderFarm` with the **Worker** role.

Workers can:

* Listen for shared farm-control commands.
* Render `.apo` project queues sent by a controller.
* Resolve relative project/export paths through that machine's own settings.
* Report `started`, `busy`, `failed`, `ignored`, or `expired` command results.
* Publish status while idle or rendering.

Workers hide project-setup controls so the machine behaves like an endpoint.

### Daemon

A **Daemon** is a machine running `apOctane_RenderFarm` with the **Daemon** role.

Daemon machines can:

* Scan `C:\Program Files\OTOY` for OTOY Network Render Node installs.
* Install or uninstall the OTOY daemon helper.
* Start the installed daemon.
* Kill running Octane node daemon processes after confirmation.
* Auto-start the daemon on app launch when enabled.
* Publish daemon status to Farm Machines.

Daemon machines are for OTOY Octane Network Render Node work. They are not `.apo` render workers.

## Farm Directory

The Farm Directory is the stable shared folder used by all participating machines. It contains:

```
_farm_status
_farm_control
```

Project Root and Exports Root can be different on each machine because each computer may mount Dropbox or network storage differently. The Farm Directory should usually stay the same across projects. If two machines use different Farm Directories, they will not see each other's status or commands.

## Status Folder

The shared status folder is usually:

```
...\00_EXPORTS\20_MASTERS\_farm_status
```

The app chooses this folder from `status_dir` when set. If `status_dir` is blank, it can infer a sibling `_farm_status` folder near the exports folder.

All farm machines that should appear in the app need read/write access to the same status folder. Status files are heartbeats. If they stop updating, the machine eventually shows as Stale.

## Farm Control Folder

The Farm Control Folder is a shared directory used for commands. It is normally auto-derived near the status/exports folder:

```
...\00_EXPORTS\20_MASTERS\_farm_control
```

It contains:

* `commands`: queued start/cancel/start-daemon commands.
* `claims`: per-machine command claim files.
* `results`: per-machine command result files.
* `archive`: reserved for cleanup/archive workflows.

In Preferences, keep **Farm Control Folder** set to **Auto** unless you need a custom shared path. Use **Reveal** to open the resolved folder.

## How A Remote Start Works

1. A controller opens an `.apo` project.
2. The user clicks **Start Queue**.
3. In Multiple Machines mode, the controller shows a machine picker.
4. The controller writes a command JSON into `_farm_control\commands`.
5. Target machines poll the shared folder.
6. Each target writes a claim before acting.
7. Idle targets start the received queue.
8. Busy targets keep working and report `busy`.
9. Each target writes a result JSON.

Remote start never cancels active work. A selected busy machine reports `busy` and continues its current render.

## How Remote Cancel Works

1. A controller clicks **Cancel Render**.
2. In Multiple Machines mode, the controller shows a target picker.
3. The controller writes a cancel command.
4. Target machines cancel only if the command is meant for them.
5. Each target writes `canceled`, `idle`, `ignored`, or `failed`.

## How Remote Start Daemon Works

1. A controller uses the farm-control daemon command.
2. Target daemon machines receive `start_daemon`.
3. Each daemon machine stops existing Octane node daemon processes if needed.
4. The machine runs its local installed daemon start command.
5. It reports whether the daemon started.

This works only if the target machine is running the app and has the Daemon role.

## Farm Machines Table

![Farm machines list](../../.gitbook/assets/farm-machines.png)

Columns include:

* Machine.
* Role: `Controller`, `Controller/Worker`, `Worker`, or `Daemon`.
* State.
* Project.
* Target.
* Last frame, when relevant.
* Detail.
* Last seen.

Common states:

* **Ready**: daemon is running or machine is available.
* **Rendering**: app render is active or daemon appears connected.
* **Idle**: app is open but not rendering.
* **Offline**: daemon process is not found or machine is not active.
* **Stale**: no recent heartbeat. The machine may be closed, offline, unable to sync, or pointed at a different Farm Directory.

Ready is shown as yellow, Rendering as green, and Offline/Stale/problem states as red or muted warning states.

## Mobile / Public Status

Controller and Controller/Worker machines can publish a condensed status document to a web endpoint. This is meant for phone-friendly monitoring outside the desktop app.

In Preferences:

1. Open **Mobile / Public Status**.
2. Enable **Publish farm status to a web endpoint**.
3. Enter the Publish URL.
4. Enter the token if the endpoint requires one.
5. Use **Test Publish** to verify it.

For the Sim-Plates Cloudflare Worker setup:

```
Publish URL: https://sim-plates-farm-status.alex-6ab.workers.dev
Token secret name: FARM_STATUS_WRITE_TOKEN
Public page: https://docs.sim-plates.com/farm-status/
```

The app sends the token in this HTTP header:

```
X-Farm-Status-Token
```

If the public page is old while the desktop app is current, check that a Controller or Controller/Worker app is open, publishing is enabled, the URL is correct, and the token value matches the Worker secret. The browser page refreshes itself, but it can only show the latest document the app successfully published.

## Daemon Monitor

When a machine role is **Daemon**, the monitor changes to **Daemon Monitor**. It hides `.apo` render cards such as ETA, Last Frame, and Project Queue.

Daemon Monitor shows:

* Status.
* PID.
* Executable.
* Installed OTOY folders.
* Command availability.
* Start-on-launch preference.
* Farm Machines.

The app detects daemon state from `octane_node_daemon.exe` and `octane_node.exe`. It waits before treating the temporary `octane_node.exe` startup probe as real rendering.

If **Start Daemon on launch** is enabled and an OTOY daemon was already running before the app opened, the app restarts it through the Sim-Plates Renderfarm daemon-start flow. This lets the app own the session status and publish a clearer heartbeat.

## Troubleshooting Missing Machines

If a machine does not appear in Farm Machines:

1. On that machine, open **Preferences > Machine Settings** and confirm the Farm Directory.
2. Use **Add / Update This Machine** and click **Test Paths**.
3. Confirm that the Farm Directory exists and contains both `_farm_status` and `_farm_control`.
4. Open the shared `_farm_status` folder and look for a current heartbeat file:
   * App render/controller machines write `MACHINE.status.json`.
   * Daemon machines write `MACHINE.node.json`.
5. Confirm the modified time updates while the app is open.
6. On the controller, confirm it is pointed at the same Farm Directory and `_farm_status` folder.

If the heartbeat file exists but the controller does not show it, the controller is usually reading a different `_farm_status` folder or the sync provider has not synced the latest file yet.

If a daemon is working in Octane but the app says **Offline**, run this in PowerShell on the daemon machine:

```powershell
Get-CimInstance Win32_Process |
  Where-Object { $_.Name -match '^octane_node(_daemon)?\.exe$' } |
  Select-Object Name, ProcessId, ExecutablePath
```

If no process is returned, OTOY may be using a different process name. If the command works but the app still reports Offline, check whether PowerShell can be found from the installed app environment.

## OTOY Daemon Folder

The app scans:

```
C:\Program Files\OTOY
```

for folders like:

```
OctaneRender Studio+ Network Render Node 2025.1
OctaneRender Studio+ Network Render Node 2025.2
OctaneRender Studio+ Network Render Node 2026.1
```

If multiple installable versions are present, **Install Daemon** asks which one to install. Starting the daemon uses the installed daemon command.

Use **Reveal OTOY Folder** to open the folder, and **OTOY Downloads** to open the download page.

## Legacy Render Node Watcher

Older setups may still use:

```bat
_OctaneNodeStatusWatcher.bat
```

and:

```
_OctaneNodeStatusWatcher.ps1
```

Those scripts are now legacy/manual troubleshooting helpers. The preferred 1.1 workflow is to run the installed app in **Daemon** role.

## Troubleshooting

### A machine does not appear

Check:

* The app is open on that machine.
* The machine role is configured.
* The shared status folder is writable.
* Dropbox or the shared drive is syncing.
* The `Last Seen` timestamp on other machines is current.

### A worker ignores a command

Check:

* The command targets the exact Windows machine name.
* The worker is idle.
* The worker can read the `.apo` paths or resolve relative roots.
* The worker can write to `_farm_control\claims` and `_farm_control\results`.

### A daemon is offline

Check:

* OTOY Network Render Node is installed.
* `octane_node_daemon.exe` is running.
* The app is in Daemon role.
* **Start Daemon on launch** is enabled if this should happen automatically.
* **Reveal OTOY Folder** shows the expected Network Render Node install.

### A daemon briefly says Rendering during startup

The OTOY daemon can launch `octane_node.exe` briefly to gather information. The app waits before treating that as real rendering, but a short transition may still appear in logs.

### Stale rows remain visible

Stale rows usually mean old status JSON is still in `_farm_status`, or that a machine has stopped writing fresh heartbeats. This is harmless. To reset the list, close participating apps and delete old JSON status files from:

```
...\00_EXPORTS\20_MASTERS\_farm_status
```

Restart the apps. Fresh status files should reappear.
