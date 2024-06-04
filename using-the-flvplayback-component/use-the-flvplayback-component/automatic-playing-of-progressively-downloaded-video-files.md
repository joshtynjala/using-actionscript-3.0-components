# Automatic playing of progressively downloaded video files

When loading a progressively downloaded video file, FLVPlayback starts playing
the video file only when enough of it has downloaded so that it can play the
video file from start to finish.

If you want to play the video file before enough of it has downloaded, call the
`play()` method without any parameters.

If you want to return to the state of waiting for enough of the video file to
download, call the `pause()` method and then call the
`playWhenEnoughDownloaded()` method.
