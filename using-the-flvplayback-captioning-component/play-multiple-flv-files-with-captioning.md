# Play multiple FLV files with captioning

You can open multiple video players within a single instance of the FLVPlayback
component to play multiple videos and switch between them as they play. You can
also associate captioning with each video player within the FLVPlayback
component. For more information on how to open multiple video players, see
[Use multiple video players](../using-the-flvplayback-component/use-the-flvplayback-component/play-multiple-video-files.md#use-multiple-video-players).
To use captioning in multiple video players, create one instance of the
FLVPlaybackCaptioning component for each `VideoPlayer` and set the
FLVPlaybackCaptioning `videoPlayerIndex` to the corresponding index. The
`VideoPlayer` index defaults to 0 when only one `VideoPlayer` exists.

The following is an example of code that assigns unique captioning to unique
videos. To run this example, the fictional URLs in the example must be replaced
with working URLs.

    captioner0.videoPlayerIndex = 0;
    captioner0.source = "http://www.example.com/mytimedtext0.xml";
    flvPlayback.play("http://www.example.com/myvideo0.flv");
    captioner1.videoPlayerIndex = 1;
    captioner1.source = "http://www.example.com/mytimedtext1.xml";
    flvPlayback.activeVideoIndex = 1;
    flvPlayback.play ("http://www.example.com/myvideo1.flv");
