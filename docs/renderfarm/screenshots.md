# Screenshot Guide

Use this guide when refreshing screenshots for GitHub documentation. Capture from the installed Windows build when possible so the screenshots match the release users download.

## Required Screenshots

Save screenshots in `docs/images/` with these filenames:

| File | What To Capture |
| --- | --- |
| `project-setup.png` | Project Setup with at least one scene in the queue, target rows visible, and Optional Render Passes visible. |
| `render-monitor.png` | Render Monitor during or immediately after a small `.apo` render, with progress/status/farm machines visible. |
| `preview.png` | Preview page showing a rendered frame or a clear empty-state if no frame exists. |
| `preferences.png` | Preferences showing Appearance and Workflow settings. |
| `machine-role.png` | First-run machine role dialog. |
| `daemon-monitor.png` | Daemon Monitor with daemon controls, Daemon Info, and Farm Machines visible. |
| `farm-machines.png` | Farm Machines table with Controller, Worker, and Daemon rows if available. |

Older screenshots can remain in place until the matching new screenshot is available, but avoid mixing old labels such as `Render Node` if the current UI says `Daemon`.

## Capture Checklist

Before capturing:

1. Install the current release.
2. Open the app normally, not from a debugger.
3. Use a clean test `.apo` project with safe paths.
4. Use a 1920x1080 or larger monitor.
5. Choose either Light or Dark theme and keep it consistent across the set.
6. Crop only browser/desktop clutter, not app controls.

For daemon screenshots:

1. Set **Preferences > Workflow > Machine Role** to **Render Node Daemon**.
2. Confirm the top navigation says **Daemon Monitor**.
3. Confirm Preview is hidden.
4. Confirm `.apo` render cards such as Last Frame and Project Queue are hidden.
5. Confirm Daemon Info is visible.

For controller/worker screenshots:

1. Set one machine to **Render Farm Controller**.
2. Set another to **Render Farm Worker** if available.
3. Confirm Farm Machines labels are `Controller`, `Worker`, and `Daemon`.

## Markdown References

The user guide references screenshots like this:

```md
![Project setup screen](images/project-setup.png)
```

After replacing screenshots, run:

```bash
python3 tools/octane_farm_app/check_local.py
```

Then commit the image updates and documentation together.
