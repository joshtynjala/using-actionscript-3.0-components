# Create a new skin

The best way to create a skin SWF file is to copy one of the skin files that
come with Flash, and use it as a starting point. You can find the FLA files for
these skins in the Flash application folder in Configuration/FLVPlayback
Skins/FLA/ActionScript 3.0/. To make your finished skin SWF file available as an
option in the Select Skin dialog box, put it in the Configuration/FLVPlayback
Skins/ActionScript 3.0 folder, either in the Flash application folder or in a
user's local Configuration/FLVPlayback Skins/ActionScript 3.0 folder.

Because you can set the color of a skin independently of choosing the skin, you
do not need to edit the FLA file to modify the color. If you create a skin that
has a specific color and you do not want it to be editable in the Select Skin
dialog box, set `this.border_mc.colorMe = false;` in the skin FLA file
ActionScript code. For information on setting a skin's color, see
[Select a predesigned skin](./select-a-predesigned-skin.md).

When looking at the installed Flash skin FLA files, it might seem that certain
things on the Stage are unnecessary, but many of these things are put into guide
layers. With live preview using scale 9, you can quickly see what will actually
appear in the SWF file.

The following sections cover more complex customizations and changes to the
SeekBar, BufferingBar, and VolumeBar movie clips.

## Use the skin layout

When you open a Flash skin FLA file, you will find the skin's movie clips laid
out on the main Timeline. These clips and the ActionScript code that you find on
the same frame define how the controls will be laid out at run time.

Although the Layout layer looks a lot like how the skin will look like at run
time, the contents of this layer are not visible at run time. It is used only to
calculate where to place the controls. The other controls on the Stage are used
at run time.

Within the Layout layer is a placeholder for the FLVPlayback component named
video_mc. All the other controls are laid out relative to video_mc. If you start
with one of the Flash FLA files and change the size of the controls, you can
probably fix the layout by moving these placeholder clips.

Each of the placeholder clips has a specific instance name. The names of the
placeholder clips are playpause_mc, play_mc, pause_mc, stop_mc,
captionToggle_mc, fullScreenToggle_mc, back_mc, bufferingBar_mc,
bufferingBarFill_mc, seekBar_mc, seekBarHandle_mc, seekBarProgress_mc,
volumeMute_mc, volumeBar_mc, and volumeBarHandle_mc. The piece that is recolored
when you choose a skin color is called border_mc.

Which clip is used for a control is not important. Generally, for buttons the
normal state clip is used. For other controls the clip for that control is used,
but this is only for convenience. All that is important are the _x_ (horizontal)
and _y_ (vertical) location and the height and the width of the placeholder.

You can also have as many additional clips as you want beside the standard
controls. The only requirement for these clips is that their library symbols
have Export for ActionScript checked in the Linkage dialog box. The custom clips
in the Layout layer can have any instance name, other than the reserved instance
names listed above. An instance name is only needed to set ActionScript on the
clips to determine the layout.

The border_mc clip is special. If you set the `FlvPlayback.skinAutoHide`
property to `true,` the skin shows when the mouse is over the border_mc clip.
This is important for skins that appear outside the bounds of the video player.
For information on the `skinAutoHide` property, see
[Modify skin behavior](./modify-skin-behavior.md).

In the Flash FLA files, border_mc is used for the chrome and for the border
around the Forward and Back buttons.

The border_mc clip is also the part of the skin that has its alpha and color
changed by the `skinBackgroundAlpha` and `skinBackgroundColor` properties. To
allow customizable color and alpha, the ActionScript in the skin FLA file must
include the following:

    border_mc.colorMe = true;

### ActionScript and skin layout

The following ActionScript code generally applies to all controls. Some controls
have specific ActionScript that defines additional behavior, and that is
explained in the section for that control.

The initial ActionScript is a large section that specifies the class names for
each state of each component. You can see all of these class names in the
SkinOverAll.fla file. The code looks like this for the Pause and Play buttons,
for example:

    this.pauseButtonDisabledState = "fl.video.skin.PauseButtonDisabled";
    this.pauseButtonDownState = "fl.video.skin.PauseButtonDown";
    this.pauseButtonNormalState = "fl.video.skin.PauseButtonNormal";
    this.pauseButtonOverState = "fl.video.skin.PauseButtonOver";
    this.playButtonDisabledState = "fl.video.skin.PlayButtonDisabled";
    this.playButtonDownState = "fl.video.skin.PlayButtonDown";
    this.playButtonNormalState = "fl.video.skin.PlayButtonNormal";
    this.playButtonOverState = "fl.video.skin.PlayButtonOver";

The class names do not have actual external class files; they are just specified
in the Linkage dialog box for all the movie clips in the library.

In the ActionScript 2.0 component, there were movie clips on Stage that were
actually used at run time. In the ActionScript 3.0 component, those movie clips
are still in the FLA file, but just to make editing convenient. Now, they are
all in guide layers and are not exported. All of the skin assets in the library
are set to export on the first frame and they are created dynamically with code
like this, for example:

    new fl.video.skin.PauseButtonDisabled();

Following that section is ActionScript code that defines the minimum width and
height for the skin. The Select Skin dialog box shows these values and they are
used at run time to prevent the skin from scaling below its minimum size. If you
do not want to specify a minimum size, leave it as undefined or less than or
equal to zero.

    // minimum width and height of video recommended to use this skin,
    // leave as undefined or <= 0 if there is no minimum
    this.minWidth = 270;
    this.minHeight = 60;

Each placeholder can have the following properties applied to it:

| Property       | Description                                                                                                                                                                                 |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `anchorLeft`   | Boolean. Positions the control relative to the left side of the FLVPlayback instance. Defaults to `true` unless `anchorRight` is explicitly set to `true`, and then it defaults to `false`. |
| `anchorRight`  | Boolean. Positions the control relative to the right side of the FLVPlayback instance. Defaults to `false`.                                                                                 |
| `anchorBottom` | Boolean. Positions the control relative to the bottom of the FLVPlayback instance. Defaults to `true`, unless `anchorTop` is explicitly set to `true`, and then it defaults to `false`.     |
| `anchorTop`    | Boolean. Positions the control relative to the top of the FLVPlayback instance. Defaults to `false`.                                                                                        |

If both the `anchorLeft` and `anchorRight` properties are `true`, the control is
scaled horizontally at run time. If both the `anchorTop` and `anchorBottom`
properties are `true`, the control is scaled vertically at run time.

To see the effects of these properties, see how they are used in the Flash
skins. The BufferingBar and SeekBar controls are the only ones that scale, and
they are laid on top of one another and have both the `anchorLeft` and
`anchorRight` properties set to `true`. All controls to the left of the
BufferingBar and SeekBar have `anchorLeft` set to `true`, and all controls to
their right have `anchorRight` set to `true`. All controls have `anchorBottom`
set to `true`.

You can try editing the movie clips on the Layout layer to make a skin where the
controls sit at the top rather than at the bottom. You simply need to move the
controls to the top, relative to `video_mc`, and set `anchorTop` equal to `true`
for all controls.

## Buffering bar

The buffering bar has two movie clips: bufferingBar_mc and bufferingBarFill_mc.
Each clip's position on the Stage relative to the other clip is important
because this relative positioning is maintained. The buffering bar uses two
separate clips because the component scales bufferingBar_mc but not
bufferingBarFill_mc.

The bufferingBar*mc clip has 9-slice scaling applied to it, so the borders won't
distort when it scales. The bufferingBarFill_mc clip is extremely wide, so that
it will always be wide enough without needing to be scaled. It is automatically
masked at run time to show only the portion above the stretched bufferingBar_mc.
By default, the exact dimensions of the mask will maintain an equal margin on
the left and right within the bufferingBar_mc, based on the difference between
the \_x* (horizontal) positions of bufferingBar_mc and bufferingBarFill_mc. You
can customize the positioning with ActionScript code.

If your buffering bar does not need to scale or does not use 9-slice scaling,
you could set it up like the FLV Playback Custom UI BufferingBar component. For
more information, see
[BufferingBar component](./skin-flv-playback-custom-ui-components-individually.md#bufferingbar-component).

The buffering bar has the following additional property:

| Property            | Description                                                                             |
| ------------------- | --------------------------------------------------------------------------------------- |
| `fill_mc:MovieClip` | Specifies the instance name of the buffering bar fill. Defaults to bufferingBarFill_mc. |

## Seek bar and volume bar

The seek bar also has two movie clips: seekBar_mc and seekBarProgess_mc. Each
clip's position on the Layout layer relative to the other clip is important
because this relative positioning is maintained. Although both clips scale, the
seekBarProgress_mc cannot be nested within seekBar_mc because seekBar_mc uses
9-slice scaling, which does not work well with nested movie clips.

The seekBar_mc clip has 9-slice scaling applied to it, so the borders won't
distort when it scales. The seekBarProgress_mc clip also scales, but it does
distort. It does not use 9-slice scaling because it is a fill, which looks fine
when distorted.

The seekBarProgress*mc clip works without a fill_mc, much like the way a
progress_mc clip works in FLV Playback Custom UI components. In other words, it
is not masked and is scaled horizontally. The exact dimensions of the
seekBarProgress_mc at 100% are defined by left and right margins within the
seekBarProgress_mc clip. These dimensions are, by default, equal and based on
the difference between the \_x* (horizontal) positions of seekBar_mc and
seekBarProgress_mc. You can customize the dimensions with ActionScript in the
seek bar movie clip, as shown in the following example:

    this.seekBar_mc.progressLeftMargin = 2;
    this.seekBar_mc.progressRightMargin = 2;
    this.seekBar_mc.progressY = 11;
    this.seekBar_mc.fullnessLeftMargin = 2;
    this.seekBar_mc.fullnessRightMargin = 2;
    this.seekBar_mc.fullnessY = 11;

You can put this code either in the SeekBar movie clip Timeline or you could put
it with the other ActionScript code on the main Timeline. If you customize with
code instead of modifying the layout, the fill doesn't need to be on the Stage.
It just needs to be in the library, set to export for ActionScript on Frame 1
with the correct class name.

As with the FLV Playback Custom UI SeekBar component, it is possible to create a
fullness movie clip for the seek bar. If your seek bar does not need to scale,
or if it does scale but does not use 9-slice scaling, you could set up your
progress_mc or fullness_mc using any of the methods used for FLV Playback Custom
UI components. For more information, see
[Progress and fullness movie clips](./skin-flv-playback-custom-ui-components-individually.md#progress-and-fullness-movie-clips).

Because the volume bar in the Flash skins does not scale, it is constructed the
same way as the VolumeBar FLV Playback Custom UI component. For more
information, see
[SeekBar and VolumeBar components](./skin-flv-playback-custom-ui-components-individually.md#seekbar-and-volumebar-components).
The exception is that the handle is implemented differently.

### Seekbar and VolumeBar handles

The SeekBar and VolumeBar handles are placed on the Layout layer next to the
bar. By default, the handle's left margin, right margin, and _y_ -axis values
are set by its position relative to the bar movie clip. The left margin is set
by the difference between the handle's _x_ (horizontal) location and the bar's
_x_ (horizontal) location, and the right margin is equal to the left margin. You
can customize these values through ActionScript in the SeekBar or VolumeBar
movie clip. The following example is the same ActionScript code that is used
with the FLV Playback Custom UI components:

    this.seekBar_mc.handleLeftMargin = 2;
    this.seekBar_mc.handleRightMargin = 2;
    this.seekBar_mc.handleY = 11;

You can put this code either in the SeekBar movie clip Timeline or you could put
it with the other ActionScript code on the main Timeline. If you customize with
code instead of modifying the layout, the handle doesn't need to be on the
Stage. It just needs to be in the library, set to export for ActionScript on
Frame 1 with the correct class name.

Beyond these properties, the handles are simple movie clips, set up the same way
as they are in the FLV Playback Custom UI components. Both have rectangle
backgrounds with the `alpha` property set to 0. These are present only to
increase the hit region and are not required.

## Background and foreground clips

The movie clips chrome_mc and forwardBackBorder_mc are implemented as background
clips.

Of the ForwardBackBorder, ForwardBorder, and BackBorder movie clips on the Stage
and the placeholder Forward and Back buttons, the only one that is _not_ on a
guide layer is ForwardBackBorder. It is only in the skins that actually use the
Forward and Back buttons.

The only requirement for these clips is that they need to be exported for
ActionScript on Frame 1 in the library.
