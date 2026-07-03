# Building Apps

This page is for developers preparing local test builds or release builds. Normal operators should use the installed app and the [User Guide](user-guide.md).

## Before You Build

Run the local checks from the repo root:

```bash
python3 tools/octane_farm_app/check_local.py
```

These checks compile Python files, validate the example config, run repo hygiene checks, and run runtime unit tests. They do not replace Windows installer smoke testing.

## Windows Development Run

From a Windows machine:

```bat
cd /d "Z:\AlexPearce3D Dropbox\Sim-Plates Dropbox\Sim-Plates Team Folder\00_SIM-PLATES\04_PIPELINE\08_ALEX_DEV\apOctaneRenderFarm\tools\octane_farm_app"
run_dev.bat
```

Use the dev run for quick UI testing before building an executable.

## Windows EXE

Build the one-file Windows executable:

```bat
cd /d "Z:\AlexPearce3D Dropbox\Sim-Plates Dropbox\Sim-Plates Team Folder\00_SIM-PLATES\04_PIPELINE\08_ALEX_DEV\apOctaneRenderFarm\tools\octane_farm_app"
build_windows.bat
```

The main output is:

```text
tools\octane_farm_app\dist\SPRenderfarm.exe
```

The build also stages the app into the current versioned release folder.

## Windows Installer

After building the EXE, build the installer:

```bat
cd /d "Z:\AlexPearce3D Dropbox\Sim-Plates Dropbox\Sim-Plates Team Folder\00_SIM-PLATES\04_PIPELINE\08_ALEX_DEV\apOctaneRenderFarm\tools\octane_farm_app"
build_installer.bat
```

This uses Inno Setup and writes installer artifacts under:

```text
tools\octane_farm_app\dist\installer
```

## Full Windows Release

For a normal Windows release, use the full release pipeline:

```bat
cd /d "Z:\AlexPearce3D Dropbox\Sim-Plates Dropbox\Sim-Plates Team Folder\00_SIM-PLATES\04_PIPELINE\08_ALEX_DEV\apOctaneRenderFarm\tools\octane_farm_app"
build_release.bat
```

This runs:

- App build.
- Installer build.
- Release staging.
- Manifest refresh.
- Release verification.

The final handoff folder is:

```text
Releases\SPRenderfarm_<version>
```

Before handing off, complete:

- `tools/octane_farm_app/RELEASE_CHECKLIST.md`
- `tools/octane_farm_app/SMOKE_TEST.md`

## macOS App / Launcher

For macOS testing, use the checked-in launcher at the repo root:

```text
_Run OctaneFarm Mac.command
```

There is also an app wrapper:

```text
_Run OctaneFarm Mac.app
```

macOS is normally used as a Controller-only machine in this pipeline. Controller-only machines do not need Octane CLI. A Mac can still run the app UI, manage projects, monitor machines, publish status, and create preview cache.

## Build The Documentation Site

Install MkDocs:

```bash
python3 -m pip install mkdocs
```

Run the local docs server from the repo root:

```bash
mkdocs serve
```

Open:

```text
http://127.0.0.1:8000
```

Build static HTML:

```bash
mkdocs build
```

The generated site is written to:

```text
site
```

Do not commit the generated `site` folder unless you intentionally decide to publish static documentation from the repo.
