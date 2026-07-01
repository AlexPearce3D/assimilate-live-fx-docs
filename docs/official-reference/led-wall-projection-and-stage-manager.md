# LED Wall Projection and Stage Manager

!!! info "Official source"

    Summary based on Assimilate's [02 - Live FX User Guide](https://www.assimilatesupport.com/akb/KnowledgebaseArticle51035.aspx).

The official guide separates the concept of LED wall projection from the Stage Manager data that describes the physical stage.

## LED wall projection

Live FX supports projection of 2D, equirectangular, 2.5D, and 3D media onto LED wall configurations including single walls, multiple walls, and curved walls. Projection can be combined with camera tracking and color-managed grading.

## Stage Manager

Stage Manager defines the physical LED stage. The official guide breaks this into stage management, wall specifications, stage model, mapper, and mapper examples.

Wall definitions and mapping matter because projection nodes, switcher nodes, stage matte operations, and set-extension workflows all depend on knowing where the LED surfaces exist in 3D space.

## How this connects to our docs

- Use [LED Workflow](../led-workflow/README.md) for the practical workflow entry point.
- Use [Stage Manager](../led-workflow/stage-manager.md) for the local Stage Manager page.
- Use [Setting up an LED Wall](../led-workflow/setting-up-an-led-wall/README.md) for setup-oriented guidance.
- Use [Projection Mapping Tutorials](../led-workflow/projection-mapping-tutorials/README.md) for projection examples.

!!! note "Review note"

    Treat Stage Manager geometry and wall mapping as foundational data. Projection workflow pages should not imply that projection behavior is independent from the stage definition.
