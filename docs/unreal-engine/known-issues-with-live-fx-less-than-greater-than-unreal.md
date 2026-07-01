# Known Issues with Live FX <> Unreal

!!! warning

    **Live FX cannot be used with AR or XR workflows currently. There is no known way to get an object with a clean alpha channel from Unreal Engine Texture share or otherwise. You can likely develop your own pipeline using 3rd party plug-ins to make this work, but we currently do not have a documented way forward.**


!!! warning

    **Live FX cannot be used with Unreal Engine and Green Screen to record the composite or the source capture without serious consequences in post-production. If you want to use Live FX and Unreal with Green Screen, you should plan to use Take Recorder in Unreal Engine to record the tracking data, so that you can re-render and get desired results directly from Unreal Engine.**


!!! info

    Live FX with Unreal Engine, for ICVFX captured in camera can be a viable solution with proper testing in advance and with the assumption that you never have to go back and re-render anything from the UE project.




There are several known issues that hopefully we can address shortly, but you should be aware of them before starting down the Live FX > Unreal Engine road.

1. Multi-Node setups are not easily setup or at least not well defined. It may be possible to set up a Multi-User Session and have one machine render the outer frustum and one machine ender the inner frustum, but this workflow has not fully been tested. So for now, we can only do inner frustum with real-time rendering.
2.  You should test the Live Link auto-record and auto scene-take before using it in production, it currently gets off by at least one take after your first recording.  
      
    For example, if you set the Slate to 1a Take 1 in Live FX, it will update the UE Scene to 1a Take 1. But when you press record and then stop the recording in Live FX, Live FX ups the take once, then in UE ups the take again, so in Live FX you'd be on 1a Take 2 and in UE you'd be on 1a Take 3.  
      
    One thing you can do is to use the Auto Record function but do not use the auto-update scene-take function and just be VERY diligent in setting the correct Scene and Take in both Live FX and Unreal Engine. <br>

    <figure><img src="../../assets/image (82).png" alt=""><figcaption></figcaption></figure>
3. In Live FX, if the timecode source is sdi and there is no timecode coming through that sdi signal, it may lock the Unreal Engine Live Link.
4.  You cannot record the Full Shot option from the Record settings and maintain a decent frame rate. If you want to record the composite you would need to find another way of doing so.   
      
    One recommendation is to use an external recorder as your dual head, and record the composite onto that.<br>

    <figure><img src="../../assets/image (83).png" alt=""><figcaption><p>Cannot Record the Full Shot</p></figcaption></figure>
5.  You cannot currently record the Source Capture and expect to be able to re-render or do anything meaningful with the tracking data. The way Live FX handles the tracking data, and the way Unreal Engine works, when you go to playback your source captured tracking data from Live FX, it may likely be a different part of your Unreal Sequence that plays back, and you may get different results (due to performance or otherwise). A very simple example is if you use a cloud system, what you record on the day may be at a drastically different part of the cloud animation if you go back to the source capture. You would also need to have Unreal Engine playing live. <br>

    <figure><img src="../../assets/image (78).png" alt=""><figcaption></figcaption></figure>
6. Currently, there is no pipeline to import the USD that is recorded from Live FX and get that into Unreal Engine.
7. The only way to control custom things in your scene directly in Live FX is a [short-term hack](control-ue-through-osc.md). You are better off building your own OSC interface using something like Open Stage Control if you need to fully control UE outside of UE.

