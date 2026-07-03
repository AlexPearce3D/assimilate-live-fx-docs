# Camera and Lens Calibration

!!! info "Official reference"

```
For the official virtual camera and calibration model, see [Virtual Camera and Calibration](../official-reference/virtual-camera-and-calibration.md) and the full guide section [Calibrate](../official-reference/live-fx-user-guide-full.md#calibrate-2).
```

> Video/resource: [https://player.vimeo.com/video/727369885](https://player.vimeo.com/video/727369885)

!!! warning

```
When you are in the Setup menu for Camera Calibration, make sure you measure the Square separately from the Aruco. The square values are on the Left (orange) and the Aruco Size is on the Right (purple).
```

Currently, Live FX can only work with Prime Lenses or at fixed focal length for calibration.

For example, if using an 18-55mm Zoom lens. You could calibrate it at 18mm, 24mm, 35mm, and 50mm, but it cannot dynamically change as you zoom.

When you make your calibration, make sure your shot resolution and frame rate are correct.

!!! info

```
You may want to create a new timeline and shot specifically to make your calibration.
```

**Leave the Sensor at Generic** and default Width, Height, and Crop factor of 1.

Change your focal length to the lens size that you are using on your camera.

If you do enter your sensor size, you have to make sure the aspect ratio and crop factor are correct.

What you see in your camera viewfinder should be the same in Live FX with no cropping or scaling.

!!! info

```
It's important that after you do your calibration, the focal length in the Live FX Camera is very close to or the same as the physical lens on your camera.

For example, if your lens is 24mm on your camera, the calculated Focal length in Live FX should be close to 24mm so that it will forward 24mm to Unreal Engine.
```

!!! warning

```
If entering in sensor size, **make sure to get the correct sensor size and crop** factor from your camera manufacturer, and make sure you calculate it based on the **Resolution Setting** and **Aspect Ratio** you are using.

For example, Red Cameras:

At 6k 16:9 the crop factor is 1.49x and the Focal Length is 35.7.  
At 6k 17:9 the crop factor is 1.42 and the Focal Length is 34mm.
```

## Testing and validating your calibration

Here is a link to a USD model of an Inverted Cone, which you can use to calibrate your camera:\
[https://www.dropbox.com/scl/fi/x1m4tyy21ezxdsrb6h9h0/00\_InvertedCone\_510\_100x.usdz?rlkey=xln83c4l3c2105yaf2f3ppxw8\&dl=0](https://www.dropbox.com/scl/fi/x1m4tyy21ezxdsrb6h9h0/00_InvertedCone_510_100x.usdz?rlkey=xln83c4l3c2105yaf2f3ppxw8\&dl=0)

You can load this by creating a new layer>Plug Ins and selecting USD (only available for Windows currently.

With this inverted cone, you should be able to see your world origin and verify if the world is slipping or not and if your world origin set by your tracking system (Or in Live FX) is where you think it should be.
