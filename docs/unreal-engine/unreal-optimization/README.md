# Unreal Optimization

## Quick Tips

Use the commands "stat fps" and "stat gpu" to help troubleshoot.

<table data-full-width="true"><thead><tr><th width="404">Command</th><th></th></tr></thead><tbody><tr><td>-scalability=1</td><td>Sets Scalability to Medium. Go up or down as needed</td></tr><tr><td>-sg.ResolutionQuality=50</td><td>sg.ResolutionQuality 50 (Halves the resolution)</td></tr><tr><td>-r.Shadow.Virtual.ResolutionLodBiasDirection=5</td><td>-1 Also affected it positively</td></tr><tr><td>rVolumetricCloud=0</td><td></td></tr><tr><td>r.ShadowQuality=0</td><td>Turns off all Shadows and increases performance</td></tr></tbody></table>



r.Shadow.Virtual.ResolutionLodBiasDirection -1  (Default was 0, 5 was also good)







