# Skin FLV Playback Custom UI components individually

The FLV Playback Custom UI components allow you to customize the appearance of
the FLVPlayback controls within your FLA file and allow you to see the results
when you preview your web page. These components are not designed to be scaled,
however. You should edit a movie clip and its contents to be a specific size.
For this reason, it is generally best to have the FLVPlayback component on the
Stage at the desired size, with the `scaleMode` set to `exactFit`.

To begin, simply drag the FLV Playback Custom UI components that you want from
the Components panel, place them where you want them on the Stage and give them
instance names.

These components can work without any ActionScript. If you put them on the same
timeline and frame as the FLVPlayback component and there is no skin set in the
component, the FLVPlayback component will connect automatically to them. If you
have multiple FLVPlayback components on Stage, or if the custom control and the
FLVPlayback instance are not on the same Timeline, then Action is needed.

After your components are on the Stage, you edit them as you would any other
symbol. After you open the components, you can see that each one is set up a
little differently from the others.

## Button components

The button components have a similar structure. The buttons include the
BackButton, ForwardButton, MuteButton, PauseButton, PlayButton, PlayPauseButton,
and StopButton. Most have a single movie clip on Frame 1 with the instance name
placeholder_mc. This is usually an instance of the normal state for the button,
but not necessarily so. On Frame 2, there are four movie clips on the Stage for
each display state: normal, over, down, and disabled. (At run time, the
component never actually goes to Frame 2; these movie clips are placed here to
make editing more convenient and to force them to load into the SWF file without
selecting the Export in First Frame check box in the Symbol Properties dialog
box. You must still select the Export for ActionScript option, however.)

To skin the button, you simply edit each of these movie clips. You can change
their size as well as their appearance.

Some ActionScript usually appears on Frame 1. You should not need to change this
script. It simply stops the playhead on Frame 1 and specifies which movie clips
to use for which states.

#### PlayPauseButton, MuteButton, FullScreenButton, and CaptionButton buttons

The PlayPauseButton, MuteButton, FullScreenButton, and CaptionButton buttons are
set up differently than the other buttons; they have only one frame with two
layers and no script. On that frame, there are two buttons, one on top of the
other—in the case of PlayPauseButton, a Play and a Pause button; in the case of
MuteButton, a Mute-on and a Mute-off button; in the case of FullScreenButton, a
full-screen-on and a full-screen-off button; in the case of CaptionButton, a
caption-on and a caption-off button. To skin these buttons, skin each of these
two internal buttons as described in
[Skin FLV Playback Custom UI components individually](./skin-flv-playback-custom-ui-components-individually.md)
; no additional action is required.

The CaptionButton is for the FLVPlaybackCaptioning component and must be
attached to that component and not the FLVPlayback component.

#### BackButton and ForwardButton buttons

The BackButton and ForwardButton buttons are also set up differently than the
other buttons. On Frame 2, they have extra movie clips that you can use as a
frame around one or both of the buttons. These movie clips are not required and
have no special capability; they are provided only as a convenience. To use
them, simply drag them on the Stage from your Library panel and place them where
you want them. If you don't want them, either don't use them or delete them from
your Library panel.

Most of the buttons, as supplied, are based on a common set of movie clips so
that you can change the appearance of all the buttons at once. You can use this
capability, or you can replace those common clips and make every button look
different.

## BufferingBar component

The buffering bar component is simple: It consists of an animation that is made
visible when the component enters the buffering state, and it does not require
any special ActionScript to configure it. By default, it is a striped bar moved
from left to right with a rectangular mask on it to give it a "barber pole"
effect, but there is nothing special about this configuration.

Although the buffering bars in the skin SWF files use 9-slice scaling because
they need to be scaled at run time, the BufferingBar FLV Custom UI Component
does not and _cannot_ use 9-slice scaling because it has nested movie clips. If
you want to make the BufferingBar wider or taller, you might want to change its
contents rather than scale it.

## SeekBar and VolumeBar components

The SeekBar and VolumeBar components are similar, although they have different
functions. Each has handles, uses the same handle tracking mechanisms, and has
support for clips nested within to track progress and fullness.

There are many places where the ActionScript code in the FLVPlayback component
assumes that the registration point (also _origin point_ or _zero point_) of
your SeekBar or VolumeBar component is at the upper-left corner of the content,
so it is important to maintain this convention. Otherwise, you might have
problems with handles and with progress and fullness movie clips.

Although the seek bars in the skin SWF files use 9-slice scaling because they
need to be scaled at run time, the SeekBar FLV Custom UI component does not and
_cannot_ use 9-slice scaling because it has nested movie clips. If you want to
make the SeekBar wider or taller, you might want to change its contents rather
than scale it.

#### Handle

An instance of the handle movie clip is on Frame 2. As with the BackButton and
ForwardButton components, the component never actually goes to Frame 2; these
movie clips are placed here to make editing more convenient and as a way to
force them to be loaded into the SWF file without selecting the Export in First
Frame check box in the Symbol Properties dialog box. You still must select the
Export for ActionScript option, however.

You might notice that the handle movie clip has a rectangle in the background
with alpha set to 0. This rectangle increases the size of the handle's hit area,
making it easier to grab without changing its appearance, similar to the hit
state of a button. Because the handle is created dynamically at run time, it
must be a movie clip and not a button. This rectangle with alpha set to 0 is not
necessary for any other reason and, generally, you can replace the inside of the
handle with any image you want. It works best, however, to keep the registration
point centered horizontally in the middle of the handle movie clip.

The following ActionScript code is on Frame 1 of the SeekBar component to manage
the handle:

    stop();
    handleLinkageID = "SeekBarHandle";
    handleLeftMargin = 2;
    handleRightMargin = 2;
    handleY = 11;

The call to the `stop()` function is necessary due to the content of Frame 2.

The second line specifies which symbol to use as the handle, and you should not
need to change this if you simply edit the handle movie clip instance on
Frame 2. At run time, the FLVPlayback component creates an instance of the
specified movie clip on the Stage as a sibling of the Bar component instance,
which means that they have the same parent movie clip. So, if your bar is at the
root level, your handle must also be at the root level.

The variable `handleLeftMargin` determines the handle's original location (0%),
and the variable `handleRightMargin` determines where it is at the end (100%).
The numbers give the offsets from the left and right ends of the bar control,
with positive numbers marking the limits within the bar and negative numbers
marking the limits outside the bar. These offsets specify where the handle can
go, based on its registration point. If you put your registration point in the
middle of the handle, the handle's far left and right sides will go past the
margins. A seek bar movie clip must have its registration point as the
upper-left corner of its content to work properly.

The variable `handleY` determines the `y` position of the handle, relative to
the bar instance. This is based on the registration points of each movie clip.
The registration point in the sample handle is at the tip of the triangle to
place it relative to the visible part, disregarding the invisible hit state
rectangle. Also, the bar movie clip must keep its registration point as the
upper-left corner of its content to work properly.

So, for example, with these limits, if a bar control is set at (100, 100) and it
is 100 pixels wide, the handle can range from 102 to 198 horizontally and stay
at 111 vertically. If you change the `handleLeftMargin` and `handleRightMargin`
to -2 and `handleY` to -11, the handle can range from 98 to 202 horizontally and
stay at 89 vertically.

#### Progress and fullness movie clips

The SeekBar component has a _progress_ movie clip and the VolumeBar has a
_fullness_ movie clip, but in practice, any SeekBar or VolumeBar can have
either, neither, or both of these movie clips. They are structurally the same
and behave similarly but track different values. A progress movie clip fills up
as the FLV file downloads (which is useful for an HTTP download only, because it
is always full if streaming from FMS) and a fullness movie clip fills up as the
handle moves from left to right.

The FLVPlayback component finds these movie clip instances by looking for a
specific instance name, so your progress movie clip instance must have your bar
movie clip as its parent and have the instance name progress_mc. The fullness
movie clip instance must have the instance name fullness_mc.

You can set the progress and fullness movie clips with or without the fill*mc
movie clip instance nested inside. The VolumeBar fullness_mc movie clip shows
the method \_with* the fill*mc movie clip, and the SeekBar progress_mc movie
clip shows the method \_without* the fill_mc movie clip.

The method with the fill_mc movie clip nested inside is useful when you want a
fill that cannot be scaled without distorting the appearance.

In the VolumeBar fullness_mc movie clip, the nested fill_mc movie clip instance
is masked. You can either mask it when you create the movie clip, or a mask will
be created dynamically at run time. If you mask it with a movie clip, name the
instance **mask_mc** and set it up so that fill_mc appears as it would when
percentage is 100%. If you do not mask fill_mc, the dynamically created mask
will be rectangular and the same size as fill_mc at 100%.

The fill_mc movie clip is revealed with the mask in one of two ways, depending
on whether fill_mc.slideReveal is `true` or `false`.

If fill_mc.slideReveal is `true`, then fill_mc is moved from left to right to
expose it through the mask. At 0%, it is all the way to the left, so none of it
shows through the mask. As the percentage increases, it moves to the right,
until at 100%, it is back where it was created on the Stage.

If fill_mc.slideReveal is `false` or undefined (the default behavior), the mask
will be resized from left to right to reveal more of fill_mc. When it is at 0%,
the mask will be scaled to 05 horizontally, and as the percentage increases, the
`scaleX` increases until, at 100%, it reveals all of fill_mc. This is not
necessarily `scaleX` = 100 because mask_mc might have been scaled when it was
created.

The method without fill_mc is simpler than the method with fill_mc, but it
distorts the fill horizontally. If you do not want that distortion, you must use
fill_mc. The SeekBar progress_mc illustrates this method.

The progress or fullness movie clip is scaled horizontally based on the
percentage. At 0%, the instance's `scaleX` is set to 0, making it invisible. As
the percentage grows, the `scaleX` is adjusted until, at 100%, the clip is the
same size it was on the Stage when it was created. Again, this is not
necessarily `scaleX` = 100 because the clip instance might have been scaled when
it was created.

## Connect your FLV Playback Custom UI components

If you put your custom UI components on the same Timeline and frame as the
FLVPlayback component and you have not set the `skin` property, FLVPlayback will
automatically connect to them without the need for any ActionScript.

> **Note:** The example below uses the file
> [`cuepoints.flv`](../../img/helpexamples/cuepoints.flv).

If you have multiple FLVPlayback components on Stage or if the custom control
and the FLVPlayback are not on the same Timeline, you must write ActionScript
code to connect your Custom UI components to your instance of the FLVPlayback
component. First, you must assign a name to the FLVPlayback instance and then
use ActionScript to assign your FLV Playback Custom UI component instances to
the corresponding FLVPlayback properties. In the following example, the
FLVPlayback instance is my_FLVPlybk, the FLVPlayback property names follow the
periods (.), and the FLV Playback Custom UI control instances are to the right
of the equal (=) signs:

    //FLVPlayback instance = my_FLVPlybk
    my_FLVPlybk.playButton = playbtn; // set playButton prop. to playbtn, etc.
    my_FLVPlybk.pauseButton = pausebtn;
    my_FLVPlybk.playPauseButton = playpausebtn;
    my_FLVPlybk.stopButton = stopbtn;
    my_FLVPlybk.muteButton = mutebtn;
    my_FLVPlybk.backButton = backbtn;
    my_FLVPlybk.forwardButton = forbtn;
    my_FLVPlybk.volumeBar = volbar;
    my_FLVPlybk.seekBar = seekbar;
    my_FLVPlybk.bufferingBar = bufbar;

The following steps create custom StopButton, PlayPauseButton, MuteButton, and
SeekBar controls:

1.  Drag the FLVPlayback component to the Stage, and give it an instance name of
    **my_FLVPlybk**.

2.  Set the `source` parameter through the Component inspector to
    **cuepoints.flv**.

3.  Set the Skin parameter to None.

4.  Drag a StopButton, a PlayPauseButton, and a MuteButton to the Stage, and
    place them over the FLVPlayback instance, stacking them vertically on the
    left. Give each button an instance name in the Property inspector (such as
    **my_stopbttn**, **my_plypausbttn**, and **my_mutebttn**).

5.  In the Library panel, open the FLVPlayback Skins folder, and then open the
    SquareButton folder below it.

6.  Select the SquareBgDown movie clip, and double-click it to open it on the
    Stage.

7.  Right-click (Windows) or Control-click (Macintosh), select Select All from
    the menu, and delete the symbol.

8.  Select the oval tool, draw an oval in the same location, and set the fill to
    blue (**\#0033FF**).

9.  In the Property inspector, set the width (W:) to **40** and the height (H:)
    to **20**. Set the x-coordinate (X:) to **0.0** and the y-coordinate (Y:) to
    **0.0**.

10. Repeat steps 6 to 8 for SquareBgNormal, but change the fill to yellow
    (**\#FFFF00**).

11. Repeat steps 6 to 8 for SquareBgOver, but change the fill to green
    (**\#006600**).

12. Edit the movie clips for the various symbol icons within the buttons
    (PauseIcon, PlayIcon, MuteOnIcon, MuteOffIcon, and StopIcon). You can find
    these movie clips in the Library panel under FLV Playback Skins/ _Label_
    Button/Assets, where _Label_ is the name of the button, such as Play, Pause,
    and so on. Follow these steps for each one:

    1.  Select the Select All option.

    2.  Change the color to red (**\#FF0000**).

    3.  Scale to 300%.

    4.  Change the X: location of the content to **7.0** to alter the horizontal
        placement of the icon in every button state.

        > **Note:** By changing the location this way, you avoid opening every
        > button state and moving the icon movie clip instance.

13. Click the blue Back arrow above the Timeline to return to Scene 1, Frame 1.

14. Drag a SeekBar component to the Stage, and place it in the lower-right
    corner of the FLVPlayback instance.

15. In the Library panel, double-click the SeekBar to open it on the Stage.

16. Scale it to 400%.

17. Select the outline, and set the color to red (**\#FF0000**).

18. Double-click SeekBarProgress in the FLVPlayback Skins/Seek Bar folder, and
    set the color to yellow (**\#FFFF00**).

19. Double-click SeekBarHandle in the FLVPlayback Skins/Seek Bar folder and set
    the color to red (**\#FF0000**).

20. Click the blue Back arrow above the Timeline to return to Scene 1, Frame 1.

21. Select the SeekBar instance on the Stage, and give it an instance name of
    **my_seekbar**.

22. In the Actions panel on Frame 1 of the Timeline, add an `import` statement
    for the video classes, and assign the button and seek bar names to the
    corresponding FLVPlayback properties, as shown in the following example:

        import fl.video.*;
        my_FLVPlybk.stopButton = my_stopbttn;
        my_FLVPlybk.playPauseButton = my_plypausbttn;
        my_FLVPlybk.muteButton = my_mutebttn;
        my_FLVPlybk.seekBar = my_seekbar;

23. Press Control+Enter to test the movie.
