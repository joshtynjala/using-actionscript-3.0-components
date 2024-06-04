# Use the FLVPlaybackCaptioning component

You use the FLVPlaybackCaptioning component with one or more FLVPlayback
components. In the simplest scenario, you drag a FLVPlayback component on stage,
drag a FLVPlaybackCaptioning component on the same stage, identify your
caption's URL, and set captions to display. In addition, you can also set
various parameters to customize your FLVPlayback captioning.

## Add captioning to the FLVPlayback component

You can add the FLVPlaybackCaptioning component to any FLVPlayback component.
For information on adding FLVPlayback components to your application, see
[Create an application with the FLVPlayback component](../using-the-flvplayback-component/use-the-flvplayback-component/create-an-application-with-the-flvplayback-component.md).

#### Add the FLVPlaybackCaptioning component from the Components panel:

1.  In the Components panel, open the Video folder.

2.  Drag (or double-click) the FLVPlaybackCaptioning component and add it to the
    same stage as the FLVPlayback component to which you want to add captioning.

    > **Note:** Adobe provides two files to help you learn the
    > FLVPlaybackCaptioning component quickly:
    > [caption_video.flv](../img/helpexamples/caption_video.flv) (a FLVPlayback
    > sample) and [caption_video.xml](../img/helpexamples/caption_video.xml) (a
    > captioning sample).

3.  (Optional) Drag the CaptionButton component to the same stage as the
    FLVPlayback and FLVPlaybackCaptioning components. The CaptionButton
    component enables a user to turn captioning on and off.

    > **Note:** To enable the CaptionButton component, you must drag it to the
    > same stage as the FLVPlayback and FLVPlaybackCaptioning components.

4.  With the FLVPlaybackCaptioning component selected on the Stage, on the
    Parameters tab of the Property inspector, specify the following required
    information:

    - Set `showCaptions` to `true`.

    - Specify the `source` of the Timed Text XML file to download.

      > ![](../img/tip_help.png) While working in Flash to test your captions,
      > you should set the `showCaptions` property to `true`. However, if you
      > include the `CaptionButton` component to allow users to turn captioning
      > on and off, you should set the `showCaptions` property to `false` _._

    Other parameters are available to help you customize the
    FLVPlaybackCaptioning component. For more information, see
    [Customize the FLVPlaybackCaptioning component](./customize-the-flvplaybackcaptioning-component.md)
    and the _ActionScript 3.0 Reference for the Adobe Flash Platform_.

5.  Select Control \> Test Movie to start the video.

#### Create an instance dynamically using ActionScript:

1.  Drag the FLVPlayback component from the Component panel to the Library panel
    (Windows \> Library).

2.  Drag the FLVPlaybackCaptioning component from the Component panel to the
    Library panel.

3.  Add the following code to the Actions panel on Frame 1 of the Timeline.

        import fl.video.*;
        var my_FLVPlybk = new FLVPlayback();
        my_FLVPlybk.x = 100;
        my_FLVPlybk.y = 100;
        addChild(my_FLVPlybk);
        my_FLVPlybk.skin = "install_drive:/Program Files/Adobe/Adobe Flash CS5/en/Configuration/FLVPlayback Skins/ActionScript 3.0/SkinUnderPlaySeekCaption.swf";
        my_FLVPlybk.source = "http://www.example.com/caption_video.flv";
        var my_FLVPlybkcap = new FLVPlaybackCaptioning();
        addChild (my_FLVPlybkcap);
        my_FLVPlybkcap.source = "http://www.example.com/caption_video.xml";
        my_FLVPlybkcap.showCaptions = true;

4.  Change _install_drive_ to the drive on which you installed Flash, and modify
    the path to reflect the location of the Skins folder for your installation:

    > **Note:** If you create an FLVPlayback instance with ActionScript, you
    > must also assign a skin to it dynamically by setting the skin property
    > with ActionScript. When you apply a skin with ActionScript, it is not
    > automatically published with the SWF file. Copy the skin SWF file and the
    > application SWF file to your server, or the skin SWF file won't be
    > available when a user executes it.

## Set the FLVPlaybackCaptioning component parameters

For each instance of the FLVPlaybackCaptioning component, you can set the
following parameters in the Property inspector or in the Component inspector to
further customize the component. The following list identifies and provides a
brief explanation of the properties:

`autoLayout`  
Determines if the FLVPlaybackCaptioning component controls the size of the
captioning area. The default is `true`.

`captionTargetName`  
Identifies the TextField or MovieClip instance name containing captions. The
default is auto.

`flvPlaybackName`  
Identifies the FLVPlayback instance name that you want to caption. The default
is auto.

`simpleFormatting`  
Limits formatting instructions of the Timed Text XML file when set to true. The
default is `false`.

`showCaptions`  
Determines if captions display. The default is `true`.

`source`  
Identifies the location of the Timed Text XML file.

For more information on all of the FLVPlaybackCaptioning parameters, see the
_ActionScript 3.0 Reference for the Adobe Flash Platform_.

### Specify the source parameter

Use the `source` parameter to specify the name and location of the Timed Text
XML file that contains the captions for your movie. Enter the URL path directly
in the source cell in the Component inspector.

### Display captions

To view captioning, set the `showCaptions` parameter to `true`.

For more information on all of the FLVPlaybackCaptioning component parameters,
see the _ActionScript 3.0 Reference for the Adobe Flash Platform_.

In the previous examples, you learned how to create and enable the
FLVPlaybackCaptioning component to display captions. There are two sources you
can use for your captions: (1) a Timed Text XML file containing your captions,
or (2) an XML file with captioning text that you associate with embedded event
cue points.
