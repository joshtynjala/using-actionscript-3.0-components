# Customize the FLVPlaybackCaptioning component

To start using the FLVPlaybackCaptioning component quickly, you can choose to
use the FLVPlaybackCaptioning defaults which place the captioning directly over
the FLVPlayback component. You may want to customize the FLVPlaybackCaptioning
component to move the captioning away from the video.

The following code demonstrates how to dynamically create an FLVPlayback object
with the toggle captioning button:

1.  Place the FLVPlayback component on the stage at 0,0 and provide the instance
    name **player**.

2.  Place the FLVPlaybackCaptioning component on the stage at 0,0 and provide
    the instance name **captioning**.

3.  Place the CaptionButton component on the stage.

4.  In the following code example, set the `testVideoPath:String` variable to an
    FLV file (using an absolute or relative path).

    **Note:** The code example sets the `testVideoPath` variable to the Flash
    video sample, [`caption_video.flv`](../img/helpexamples/caption_video.flv).
    Change this variable to the path of the captioning video component to which
    you are adding a caption button component.

5.  In the following code example, set the `testCaptioningPath:String` variable
    to an appropriate Timed Text XML file (using an absolute or relative path).

    > **Note:** The code example sets the `testCaptioningPath` variable to the
    > Timed Text XML file,
    > [`caption_video.xml`](../img/helpexamples/caption_video.xml). Change this
    > variable to the path of the Timed Text XML file that contains captions for
    > your video.

6.  Save the following code as FLVPlaybackCaptioningExample.as in the same
    directory as your FLA file.

7.  Set the DocumentClass in the FLA file to FLVPlaybackCaptioningExample.

        package
        {
            import flash.display.Sprite;
            import flash.text.TextField;
            import fl.video.FLVPlayback;
            import fl.video.FLVPlaybackCaptioning;

            public class FLVPlaybackCaptioningExample extends Sprite {

                private var testVideoPath:String = "http://www.example.com/caption_video.flv";
                private var testCaptioningPath:String = "http://www.example.com/caption_video.xml";

                public function FLVPlaybackCaptioningExample() {
                    player.source = testVideoPath;
                    player.skin = "SkinOverAllNoCaption.swf";
                    player.skinBackgroundColor = 0x666666;
                    player.skinBackgroundAlpha = 0.5;

                    captioning.flvPlayback = player;
                    captioning.source = testCaptioningPath;
                    captioning.autoLayout = false;
                    captioning.addEventListener("captionChange",onCaptionChange);
                }
                private function onCaptionChange(e:*):void {
                    var tf:* = e.target.captionTarget;
                    var player:FLVPlayback = e.target.flvPlayback;

                    // move the caption below the video
                    tf.y = 210;
                }
            }
        }

    For more information on all of the FLVPlaybackCaptioning parameters, see the
    _ActionScript 3.0 Reference for the Adobe Flash Platform_.
