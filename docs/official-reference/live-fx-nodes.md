# Live FX Nodes

!!! info "Official source"

    Summary based on Assimilate's [02 - Live FX User Guide](https://www.assimilatesupport.com/akb/KnowledgebaseArticle51035.aspx).

The official guide describes Live FX nodes as building blocks for capture, projection, switching, masking, tracking, lens correction, GPU sharing, USD, and Notch workflows.

## Core nodes

**Video Capture Node** represents live input and includes range handling such as full range versus video range.

**Projection Node** projects source media onto wall geometry. The official guide distinguishes 2D-to-wall and equirectangular-to-wall projection modes.

**Switcher Node** can combine wall outputs and optional live capture channels. In projection workflows, switchers can coordinate multiple projection channels using stage and camera data.

**Stage Matte** uses the stage definition and camera view to matte between projected content and live capture, especially for set extensions.

## Specialized nodes

The official guide also covers Matte Wrap, Live Tracker, Lens (Un)distort, Spout/Syphon GPU sharing, equirectangular-to-2D transforms, USD nodes, Notch Blocks, and NotchLC.

## How this connects to our docs

- Use [Switcher Node](../led-workflow/switcher-node.md) for switcher setup notes.
- Use [Projection Mapping Tutorials](../led-workflow/projection-mapping-tutorials/README.md) for projection node workflows.
- Use [Part 5: Set Extensions](../led-workflow/projection-mapping-tutorials/part-5-set-extensions.md) for stage matte style workflows.
- Use [Video-IO Settings](../video-playback/video-io-settings.md) for signal/range setup.

!!! note "Review note"

    Node behavior depends on where the node sits in the composition graph. Tutorial pages should keep node role and graph placement explicit.
