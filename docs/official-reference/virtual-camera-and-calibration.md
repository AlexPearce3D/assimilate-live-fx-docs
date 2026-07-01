# Virtual Camera and Calibration

!!! info "Official source"

    Summary based on Assimilate's [02 - Live FX User Guide](https://www.assimilatesupport.com/akb/KnowledgebaseArticle51035.aspx).

The virtual camera model is the official bridge between real camera metadata, Live Links, calibration, and projection/compositing behavior.

## Camera model

The official guide groups virtual camera settings into general camera controls, lens and sensor values, position and animation offsets, and configuration options. The camera model uses focal length, sensor size, and crop to determine field of view.

## Calibration

Calibration is split into setup, lens calibration, nodal point calibration, and position calibration. The official guide notes that calibration may vary focal length or crop depending on whether the documented focal length must remain fixed.

Nodal point calibration is especially important when a tracker does not already account for the physical offset between the tracker and the camera nodal point.

## How this connects to our docs

- Use [Camera and Lens Calibration](../camera-tracking/camera-and-lens-calibration.md) for the practical calibration walkthrough.
- Use [How to apply FIZ from Camera Tracking](../camera-tracking/how-to-apply-fiz-zoom-and-focus-from-camera-tracking.md) for zoom/focus metadata workflows.
- Use [How to manually adjust camera tracking speed and delay](../camera-tracking/how-to-manually-adjust-camera-tracking-speed-and-delay.md) when tracking needs timing adjustment.

!!! note "Review note"

    Calibration values are project- and camera-specific. When tutorial advice conflicts with measured calibration results, the measured calibration should win.
