# Play multiple video files

You can play video files sequentially in an FLVPlayback instance simply by
loading a new URL in the `source` property when the previous video file finishes
playing. For example, the following ActionScript code listens for the `complete`
event, which occurs when a video file finishes playing. When this event occurs,
the code sets the name and location of a new video file in the `source` property
and calls the `play()` method to play the new video.

    import fl.video.*;
    my_FLVPlybk.source = "http://www.example.com/clouds.flv";
    my_FLVPlybk.addEventListener(VideoEvent.COMPLETE, complete_listener);
    // listen for complete event; play new FLV
    function complete_listener(eventObject:VideoEvent):void {
        if (my_FLVPlybk.source == "http://www.example.com/clouds.flv") {
            my_FLVPlybk.play("http://www.example.com/water.flv");
        }
    }

> The examples on this page use the files
> [`clouds.flv`](../../img/helpexamples/clouds.flv) and
> [`water.flv`](../../img/helpexamples/water.flv).

## Use multiple video players

You can also open multiple video players within a single instance of the
FLVPlayback component to play multiple videos and switch between them as they
play.

You create the initial video player when you drag the FLVPlayback component to
the Stage. The component automatically assigns the initial video player the
number 0 and makes it the default player. To create an additional video player,
simply set the `activeVideoPlayerIndex` property to a new number. Setting the
`activeVideoPlayerIndex` property also makes the specified video player the
_active_ video player, which is the one that will be affected by the properties
and methods of the FLVPlayback class. Setting the `activeVideoPlayerIndex`
property does not make the video player visible, however. To make the video
player visible, set the `visibleVideoPlayerIndex` property to the video player's
number. For more information on how these properties interact with the methods
and properties of the FLVPlayback class, see the
FLVPlayback.activeVideoPlayerIndex and FLVPlayback.visibleVideoPlayerIndex
properties in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
`.`

The following ActionScript code loads the `source` property to play a video file
in the default video player and adds a cue point for it. When the `ready` event
occurs, the event handler opens a second video player by setting the
`activeVideoPlayerIndex` property to the number 1. It specifies a FLV file and a
cue point for the second video player and then makes the default player (0) the
active video player again.

    /**
        Requires:
        - FLVPlayback component on the Stage with an instance name of my_FLVPlybk
    */
    // add a cue point to the default player
    import fl.video.*;
    my_FLVPlybk.source = "http://www.example.com/clouds.flv";
    my_FLVPlybk.addASCuePoint(3, "1st_switch");
    my_FLVPlybk.addEventListener(VideoEvent.READY, ready_listener);
    function ready_listener(eventObject:VideoEvent):void {
        // add a second video player and create a cue point for it
        my_FLVPlybk.activeVideoPlayerIndex = 1;
        my_FLVPlybk.source = "http://www.example.com/water.flv";
        my_FLVPlybk.addASCuePoint(3, "2nd_switch");
        my_FLVPlybk.activeVideoPlayerIndex = 0;
    }

To switch to another FLV file while one is playing, you must make the switch in
your ActionScript code. Cue points allow you to intervene at specific points in
the FLV file using a `cuePoint` event. The following code creates a listener for
the `cuePoint` event and calls a handler function that pauses the active video
player (0), switches to the second player (1), and plays its FLV file:

    import fl.video.*;
    // add listener for a cuePoint event
    my_FLVPlybk.addEventListener(MetadataEvent.CUE_POINT, cp_listener);
    // add the handler function for the cuePoint event
    function cp_listener(eventObject:MetadataEvent):void {
        // display the no. of the video player causing the event
        trace("Hit cuePoint event for player: " + eventObject.vp);
        // test for the video player and switch FLV files accordingly
        if (eventObject.vp == 0) {
            my_FLVPlybk.pause();     //pause the first FLV file
            my_FLVPlybk.activeVideoPlayerIndex = 1; // make the 2nd player active
            my_FLVPlybk.visibleVideoPlayerIndex = 1; // make the 2nd player visible
            my_FLVPlybk.play(); // begin playing the new player/FLV
        } else if (eventObject.vp == 1) {
            my_FLVPlybk.pause(); // pause the 2nd FLV
            my_FLVPlybk.activeVideoPlayerIndex = 0; // make the 1st player active
            my_FLVPlybk.visibleVideoPlayerIndex = 0; // make the 1st player visible
            my_FLVPlybk.play(); // begin playing the 1st player
        }
    }
    my_FLVPlybk.addEventListener(VideoEvent.COMPLETE, complete_listener);
    function complete_listener(eventObject:VideoEvent):void {
        trace("Hit complete event for player: " + eventObject.vp);
        if (eventObject.vp == 0) {
            my_FLVPlybk.activeVideoPlayerIndex = 1;
            my_FLVPlybk.visibleVideoPlayerIndex = 1;
            my_FLVPlybk.play();
        } else {
            my_FLVPlybk.closeVideoPlayer(1);
        }
    };

When you create a new video player, the FLVPlayback instance sets its properties
to the value of the default video player, except for the `source`, `totalTime,`
and `isLive` properties, which the FLVPlayback instance always sets to the
default values: empty string, 0, and `false`, respectively. It sets the
`autoPlay` property, which defaults to `true` for the default video player, to
`false`. The `cuePoints` property has no effect, and it has no effect on a
subsequent load into the default video player.

The methods and properties that control volume, positioning, dimensions,
visibility, and the user interface controls are always global and their behavior
is not affected by setting the `activeVideoPlayerIndex` property. For more
information on these methods and properties and the effect of setting the
`activeVideoPlayerIndex` property, see the FLVPlayback.activeVideoPlayerIndex
property in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
The remaining properties and methods target the video player identified by the
value of the `activeVideoPlayerIndex` property.

Properties and methods that control dimensions _do_ _interact_ with the
`visibleVideoPlayerIndex` property, however. For more information, see the
FLVPlayback.visibleVideoPlayerIndex property in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
