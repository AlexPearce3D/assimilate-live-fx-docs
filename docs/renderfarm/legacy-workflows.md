# Legacy Workflows

The current product-facing app is the PySide6 application in `tools/octane_farm_app`.

These older scripts remain in the repo for reference, migration, or narrow operational use. They should not be treated as the main customer workflow unless a release note explicitly says so.

## Current Product Path

- `tools/octane_farm_app/run_dev.bat`: run the app from source on Windows.
- `tools/octane_farm_app/build_release.bat`: official release build path.
- `tools/octane_farm_app/build_installer.bat`: lower-level installer build helper.
- `tools/octane_farm_app/check_local.py`: non-Windows compile/help/config/hygiene/unit-test check.
- `cmdBatchRender.lua`: Octane-side render script used by the app.

## Legacy Or Manual Helpers

| Path | Status |
| --- | --- |
| `OctaneFarmGUI.ps1` | Legacy PowerShell UI. Keep only for historical reference unless a specific production workflow still depends on it. |
| `_Build OctaneFarm EXE.bat` | Legacy build helper. Prefer `tools/octane_farm_app/build_release.bat`. |
| `_EstimateRenderETA.ps1` | Legacy ETA helper. The PySide app has built-in ETA estimation now. |
| `_EstimateRenderETA.command` | Legacy macOS launcher for the old ETA helper. |
| `_OctaneFarmApp.cmd` | Legacy app launcher. Prefer the installed app or `tools/octane_farm_app/run_dev.bat`. |
| `_OctaneRenderFarm.cmd` | Legacy render launcher. Prefer the PySide app. |
| `_OctaneRenderFarm.cmd - Shortcut.lnk` | Legacy shortcut artifact. Do not distribute in new releases. |
| `_Test Octane CLI Network Log.bat` | Manual diagnostic helper for Octane CLI/network logging. |
| `_OctaneNodeStatusWatcher.bat` | Legacy/manual helper for older render-node status publishing. Prefer the app's Render Node Daemon role in 1.1+. |
| `_OctaneNodeStatusWatcher.ps1` | Legacy/manual helper for older render-node status publishing. Prefer the app's Render Node Daemon role in 1.1+. |
| `dashboard/` | Earlier browser dashboard/status experiment. Not the primary customer-facing UI. |
| `Releases/` | Historical release bundles. New distribution should use versioned release output plus GitHub Releases or another external release channel. |

## Rules For New Work

- Put new user-facing product behavior in the PySide app.
- Put testable non-UI behavior in Python runtime modules under `tools/octane_farm_app/octane_farm_app`.
- Keep Lua limited to Octane-side render execution.
- Keep PowerShell limited to Windows integration tasks that are awkward or impossible from the app.
- Do not add new product workflows that require users to run root-level `.ps1`, `.bat`, or `.cmd` files directly.

## Future Cleanup

Before a commercial source-code handoff, consider moving legacy scripts into a dedicated `legacy/` folder after confirming no active shortcuts, docs, or deployment scripts depend on their root-level paths.
