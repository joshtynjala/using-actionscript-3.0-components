# Create an application with the FLVPlayback component

You can include the FLVPlayback component in your application in the following
ways:

- Drag the FLVPlayback component from the Components panel to the Stage, and
  specify a value for the `source` parameter.

- Use the Video Import wizard to create the component on the Stage, and
  customize it by selecting a skin.

- Use the `FLVPlayback()` constructor to dynamically create an FLVPlayback
  instance on the Stage, assuming the component is in the library.

  > **Note:** If you create an FLVPlayback instance with ActionScript, you must
  > also assign a skin to it by setting the `skin` property with ActionScript.
  > When you apply a skin this way, it is not automatically published with the
  > SWF file. You must copy both the application SWF file and the skin SWF file
  > to your application server or the skin SWF file won't be available when you
  > run the application.

#### Drag the FLVPlayback component from the Components panel

1.  In the Components panel, click the Plus (+) button to open the video entry.

2.  Drag the FLVPlayback component to the Stage.

3.  With the FLVPlayback component selected on the Stage, locate the Value cell
    for the `source` parameter on the Parameters tab of the Component inspector,
    and enter a string that specifies one of the following:

    - A local path to a video file

    - A URL to a video file

    - A URL to a synchronized Multimedia Integration Language (SMIL) file that
      describes how to play a video file

      For information on how to create a SMIL file to describe one or more FLV
      files, see [Use a SMIL file](../use-a-smil-file.md).

4.  On the Parameters tab in the Component inspector, with the FLVPlayback
    component selected on the Stage, click the Value cell for the `skin`
    parameter.

5.  Click the magnifying glass icon to open the Select Skin dialog box.

6.  Select one of the following options:

    - From the drop-down Skin list, select one of the predesigned skins to
      attach a set of playback controls to the component.

    - If you created a custom skin, select Custom Skin URL from the pop-up menu,
      and enter, in the URL box, the URL for the SWF file that contains the
      skin.

    - Select None, and drag individual FLV Playback Custom UI components to the
      Stage to add playback controls.

      > **Note:** In the first two cases, a preview of the skin appears in the
      > viewing pane above the pop-up menu. You can use the Color picker to
      > change the color of the skin.

      To change the color of a custom UI control, you must customize it. For
      more information on using custom UI controls, see
      [Skin FLV Playback Custom UI components individually](../customize-the-flvplayback-component/skin-flv-playback-custom-ui-components-individually.md).

7.  Click OK to close the Select Skin dialog box.

8.  Select Control \> Test Movie to execute the SWF file and start the video.

    The following procedure uses the Video Import wizard to add an FLVPlayback
    component:

#### Use the Video Import wizard:

1.  Select File \> Import \> Import Video.

2.  Indicate the location of the video file by selecting one of the following
    options:

    - On my local computer

    - Already deployed to a web server, Flash Video Streaming Service, or Flash
      Media Server

3.  Depending on your choice, enter either the path or the URL that specifies
    the location of the video file, then click Next.

4.  If you selected a file path, you'll see a Deployment dialog box next in
    which you can select one of the options listed to specify how you would like
    to deploy your video:

    - Progressive download from a standard web server

    - Stream from Flash Video Streaming Service

    - Stream from Flash Media Server

    - Embed video in a SWF file and play in the Timeline

    > **Important:** Do not select the Embed Video option. The FLVPlayback
    > component plays only external streaming video. This option will not place
    > an FLVPlayback component on the Stage.

5.  Click Next.

6.  Select one of the following options:

    - From the drop-down Skin list, select one of the predesigned skins to
      attach a set of playback controls to the component.

    - If you created a custom skin for the component, select Custom Skin URL
      from the pop-up menu, and enter the URL for the SWF file that contains the
      skin in the URL box.

    - Select None, and drag individual FLV Playback Custom UI components to the
      Stage to add playback controls.

      > **Note:** In the first two cases, a preview of the skin appears in the
      > viewing pane above the pop-up menu.

7.  Click OK to close the Select Skin dialog box.

8.  Read the Finish Video Import dialog box to note what happens next, and then
    click Finish.

9.  If you have not saved your FLA file, a Save As dialog box appears.

10. Select Control \> Test Movie to execute the SWF, and start the video.

    The following procedure adds the FLVPlayback component using ActionScript.

#### Create an instance dynamically using ActionScript:

1.  Drag the FLVPlayback component from the Components panel to the Library
    panel (Window \> Library).

2.  Add the following code to the Actions panel on Frame 1 of the Timeline.
    Change _install_drive_ to the drive on which you installed Flash and modify
    the path to reflect the location of the Skins folder for your installation:

    On a Windows computer:

        import fl.video.*;
        var my_FLVPlybk = new FLVPlayback();
        my_FLVPlybk.x = 100;
        my_FLVPlybk.y = 100;
        addChild(my_FLVPlybk);
        my_FLVPlybk.skin = "file:///install_drive|/Program Files/Adobe/Adobe Flash CS5/en/Configuration/FLVPlayback Skins/ActionScript 3.0/SkinOverPlaySeekMute.swf"
        my_FLVPlybk.source = "http://www.example.com/water.flv";

    On a Macintosh computer:

        import fl.video.*;
        var my_FLVPlybk = new FLVPlayback();
        my_FLVPlybk.x = 100;
        my_FLVPlybk.y = 100;
        addChild(my_FLVPlybk);
        my_FLVPlybk.skin = "file:///Macintosh HD:Applications:Adobe Flash CS5:Configuration:FLVPlayback Skins:ActionScript 3.0SkinOverPlaySeekMute.swf"
        my_FLVPlybk.source = "http://www.example.com/water.flv";

    > **Note:** If you do not set the `source` and `skin` properties, the
    > generated movie clip appears to be empty.

    > **Note:** The examples above use the file
    > [`water.flv`](../../img/helpexamples/water.flv).

3.  Select Control \> Test Movie to execute the SWF file and start the video
    file.
