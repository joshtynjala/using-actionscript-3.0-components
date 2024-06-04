# Modify skin behavior

The `bufferingBarHidesAndDisablesOthers` property and the `skinAutoHide`
property allow you to customize the behavior of your FLVPlayback skin.

Setting the `bufferingBarHidesAndDisablesOthers` property to `true` causes the
FLVPlayback component to hide the SeekBar and its handle as well as disable the
Play and Pause buttons when the component enters the buffering state. This can
be useful when an FLV file is streaming from FMS over a slow connection with a
high setting for the `bufferTime` property (10, for example). In this situation,
an impatient user might try to start seeking by clicking the Play and Pause
buttons, which could delay playing the file even longer. You can prevent this
activity by setting `bufferingBarHidesAndDisablesOthers` to `true` and disabling
the SeekBar element and the Pause and Play buttons while the component is in the
buffering state.

The `skinAutoHide` property affects only predesigned skin SWF files and not
controls created from the FLV Playback Custom UI components. If set to `true`,
the FLVPlayback component hides the skin when the mouse is not over the viewing
area. The default value of this property is `false`.
