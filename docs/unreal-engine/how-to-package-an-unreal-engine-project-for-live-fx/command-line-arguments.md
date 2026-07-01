# Command Line Arguments

Here are some of the most useful Command Line arguments that can be passed through the shortcut's target area at the end. it would look something like this:<br>

<figure><img src="../../../assets/image (520).png" alt=""><figcaption></figcaption></figure>

| Command Line Argument                      | Description                                                                                          |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| -Game                                      | Launches a UE Project as a game instead of with the editor.                                          |
| -RenderOffscreen                           | Renders offscreen (Still seen by Live FX)                                                            |
| -ForceRes -ResX=1920 -ResY=1080            | Sets the resolution. (Usually needs to match what you want your inner frustum to be).                |
| -RCWebControlEnable                        | Required to use Web Remote Control                                                                   |
| -RCWebInterfaceEnable                      | Required to use Web Remote Control                                                                   |
| -t.maxfps = 23.976                         | Sets the max frame rate. Helpful if you do not set a project frame rate or need to limit it further. |
| /Game/Maps/MyMap                           | Before the other flags, this can launch a specific Map                                               |
|  -DisableAllScreenMessages (isn't working) |                                                                                                      |



[For Optimizing Command Line Arguments, see this article.](../unreal-optimization/console-commands-command-line-arguments.md)
