# Re-Map EXR channels

To re-map the layers of EXR files, select the layer you want to change and in the top left of the main menu, select the "Node" menu.

Select the channel selection, then re-map R,G,B and A to the correct channels.

After we re-map the values correctly, the image looks correct.

Some EXRs and some Render Passes from various 3d programs will have other passes, that do not correspond with R,G,B and A. For these you may need to experiment to get the desired results.

In this example, this is the Z-Depth Pass, and instead of R,G,B,A, we need to re-map R,G,B,A to Y,Y,Y,A
