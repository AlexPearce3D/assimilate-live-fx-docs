# Keyers and Alpha Output

!!! info "Official source"

    Summary based on Assimilate's [02 - Live FX User Guide](https://www.assimilatesupport.com/akb/KnowledgebaseArticle51035.aspx).

The official guide covers keyers, alpha output, keyer pre/post options, and alpha output over SDI or dual-head output.

## Keyers

Live FX keying uses qualifier and matte controls to create alpha from a source. The official guide calls out pre-options and post-options such as denoising before a key and clipping alpha after a key.

## Alpha output

Alpha can be part of a compositing workflow and can also be sent out through supported output configurations. When alpha must leave Live FX, output routing and format support should be checked against the official guide and current hardware setup.

## How this connects to our docs

- Use [Compositing](../compositing/README.md) for the compositing overview.
- Use [Working with the Alpha Channel](../compositing/working-with-the-alpha-channel.md) for practical alpha channel handling.
- Use [Working with Mattes](../compositing/working-with-mattes.md) for matte-oriented workflows.
- Use [Qualifiers](../green-screen-workflow/qualifiers.md) for green-screen qualifier context.

!!! note "Review note"

    Alpha-capable recording and output paths depend on codec, output configuration, and hardware. Use the official guide as the baseline before presenting a workflow as supported.
