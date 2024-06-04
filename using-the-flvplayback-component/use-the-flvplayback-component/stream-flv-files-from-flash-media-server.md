# Stream FLV files from Flash Media Server

The requirements for streaming FLV files from Flash Media Server are different
depending on whether native bandwidth detection is available from your Flash
Video Streaming Service provider. Native bandwidth detection means that the
bandwidth detection is built-in to the streaming server and it provides better
performance. Check with your provider to determine whether native bandwidth
detection is available.

To access your FLV files on Flash Media Server, use a URL such as rtmp://
_my_servername/my_application/stream._ flv.

When playing a live stream with Flash Media Server, you need to set the
FLVPlayback `isLive` property to `true`. For more information, see the
FLVPlayback.isLive property in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

For more information on administering Flash Media Server, including how to set
up a live stream, see the Flash Media Server documentation at
[www.adobe.com/support/documentation/en/flashmediaserver/](https://web.archive.org/web/20140330140150/http://help.adobe.com/en_US/flashmediaserver/techoverview/index.html).

## For native bandwidth detection or no bandwidth detection

The NCManagerNative class is a subclass of NCManager that supports native
bandwidth detection, which some Flash Video Streaming Service providers may
support. When you use NCManagerNative, no special files are needed on the Flash
Media Server. NCManagerNative also allows connection to any version of Flash
Media Server, without a main.asc file, if bandwidth detection is not required.

To use NCManagerNative instead of the default NCManager class, add the following
lines of code in the first frame of your FLA file:

    import fl.video*;
    VideoPlayer.iNCManagerClass = fl.video.NCManagerNative;

## For non-native bandwidth detection

If native bandwidth detection is not available from your Flash Video Streaming
Service provider but you need bandwidth detection, you must add the main.asc
file to your Flash Media Server FLV application. You can find the main.asc file
online at
[www.adobe.com/go/learn_fl_samples](https://web.archive.org/web/20120303062950/http://www.adobe.com/devnet/flash/samples.html).
It's contained in the Samples.zip file -- within the
Samples\ComponentsAS2\FLVPlayback directory.

#### To set up your Flash Media Server for streaming FLV files:

1.  Create a folder in your Flash Media Server application folder, and give it a
    name such as **my_application**.

2.  Copy the main.asc file into the my_application folder.

3.  Create a folder named **streams** in the my_application folder.

4.  Create a folder named **\_definst\_** inside the streams folder.

5.  Place your FLV files in the **\_definst\_** folder.
