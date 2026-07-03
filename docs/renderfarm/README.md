# Sim-Plates Renderfarm

Sim-Plates Renderfarm is a desktop app for Octane command-line rendering, project queues, multi-machine farm coordination, preview playback, and live farm monitoring.

The app wraps the production tasks around Octane Standalone:

- Build a queue of projects and render targets.
- Let selected machines contribute to the same render.
- Delete unwanted passes, organize render passes, and apply render overrides.
- Start, cancel, monitor, and preview farm renders from one controller.
- Use Windows or macOS machines as controllers, workers, or controller/workers.
- Manage OTOY Octane Network Render Node daemon machines from the app.
- Cache EXR previews as JPEG or PNG for real-time frame playback.
- Export preview videos for QC.
- Publish a phone-friendly public status page.

## Start Here

- [User Guide](user-guide.md): operator workflow for the installed app.
- [Farm Machine Monitoring](farm-machine-monitoring.md): roles, Farm Directory, status files, farm control, daemon machines, and mobile status.
- [Video Tutorial Script](tutorial.md): a long-form walkthrough script for a 30 minute overview video.
- [Building Apps](building-apps.md): how to build the Windows app, Windows installer, macOS app, and local documentation site.

## Machine Roles

The app supports five roles:

- **Single Machine**: local-only rendering.
- **Controller**: builds projects, starts/cancels farm jobs, publishes status, and can create preview cache without rendering locally.
- **Controller/Worker**: controls the farm and also renders local project jobs.
- **Worker**: listens for controller commands and renders project jobs.
- **Daemon**: manages an OTOY Octane Network Render Node daemon.

## Shared Farm Directory

All participating machines must point at the same shared Farm Directory. It contains:

```text
_farm_status
_farm_control
```

`_farm_status` contains heartbeat files so machines appear in Farm Machines. `_farm_control` contains command files for remote start, cancel, and daemon start commands.

## Public Status

The current Sim-Plates Cloudflare Worker endpoint is:

```text
https://sim-plates-farm-status.alex-6ab.workers.dev
```

The public page is:

```text
https://docs.sim-plates.com/farm-status/
```

The token field should contain the Worker secret value for `FARM_STATUS_WRITE_TOKEN`.

## Documentation Site

Run the local documentation site from the repo root:

```bash
python3 -m pip install mkdocs
mkdocs serve
```

Then open:

```text
http://127.0.0.1:8000
```
