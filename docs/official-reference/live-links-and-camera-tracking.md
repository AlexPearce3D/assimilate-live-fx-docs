# Live Links and Camera Tracking

!!! info "Official source"

    Summary based on Assimilate's [02 - Live FX User Guide](https://www.assimilatesupport.com/akb/KnowledgebaseArticle51035.aspx).

Live Links are the official mechanism for dynamic metadata inside Live FX. They can come from global sources such as camera tracking systems or OSC, from outgoing sources such as Unreal Live Link, or from nodes inside a composition.

## Live Links Manager

The Live Links Manager is used to activate and manage incoming and outgoing metadata sources. Officially, Live Link data is tied to timecode, and the guide notes that an alternate timecode provider can be used when tracking needs to follow a specific capture source.

## Camera trackers

The official guide distinguishes tracker capabilities by the data they provide:

- rotation and translation
- focal length, zoom, and focus data
- lens distortion data
- origin calibration behavior
- tracker-to-nodal-point mount offsets
- automatic discovery or manual IP/port setup
- license availability

## Unreal and other sources

Live FX can forward virtual camera metadata to Unreal through the Unreal Live Link workflow. OSC sources can also be captured and mapped into Live Links for use in animation or composition parameters.

## How this connects to our docs

- Use [Camera Tracking](../camera-tracking/README.md) for workflow-level tracking notes.
- Use [Camera Trackers](../camera-tracking/camera-trackers/README.md) for tracker-specific pages.
- Use [Set up Unreal Engine with Live FX](../unreal-engine/set-up-unreal-engine-with-live-fx.md) for the Unreal workflow.
- Use [Control UE through OSC](../unreal-engine/control-ue-through-osc.md) for OSC-oriented Unreal control.

!!! note "Review note"

    Tracker support and license availability can change by Live FX version. Use the official guide as the baseline and keep tracker-specific tutorials version-aware.
