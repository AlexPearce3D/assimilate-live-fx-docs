# Working with the Alpha Channel

!!! info "Official reference"

```
For official keyer and alpha output behavior, see [Keyers and Alpha Output](../official-reference/keyers-and-alpha-output.md) and the full guide section [Alpha output over SDI / Dual head](../official-reference/live-fx-user-guide-full.md#alpha-output-over-sdi-dual-head).
```

The main tab that you should think of when you are using a file with an alpha channel, is the Fill/Matte tab on the bottom left.

It may also help to start your project with a Filler, such as Black.

After you've created a Filler layer and entered your project, you can now add your foreground elements, in this case, I'm adding a Noisy and De-Noised beauty pass. These both have alpha channels and by default, they are enabled, so the sky looks black.

Now I drop in my environment pass on the top of the layer stack, so that it goes behind the other two files.

Some times you may have an alpha channel off by default and you want to turn it on, such as this exr:

In the Fill/Matte menu, enable the alpha menu, and now the alpha channel will be active.
