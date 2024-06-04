# Find the version of the component

Flash ActionScript 3.0 components have a version property that you can display
if you need to provide it to Adobe Technical Support or you need to know what
version of the component you are using.

#### Display the version number for a user interface component:

1.  Create a new Flash file (ActionScript 3.0) document.

2.  Drag the component to the Stage and give it an instance name. For example,
    drag a ComboBox to the Stage and call it **aCb**.

3.  Press the **F9** key or select Window \> Actions to open the Actions panel.

4.  Click Frame 1 on the main Timeline and add the following code to the Actions
    panel:

        trace(aCb.version);

    The version number, similar to the one in the following illustration, should
    appear in the Output panel.

    For the FLVPlayback and FLVPlaybackCaptioning components, you must refer to
    the class name rather than the instance name because the version number is
    stored in a class constant.

#### Display the version number for the FLVPlayback and FLVPlaybackCaptioning components:

1.  Create a new Flash file (ActionScript 3.0) document.

2.  Drag the FLVPlayback and FLVPlaybackCaptioning components into the Library
    panel.

3.  Press the **F9** key or select Window \> Actions to open the Actions panel.

4.  Click Frame 1 on the main Timeline and add the following code to the Actions
    panel.

        import fl.video.*;
        trace("FLVPlayback.VERSION: " + FLVPlayback.VERSION);
        trace("FLVPLaybackCaptioning.VERSION: " + FLVPlaybackCaptioning.VERSION);

    The version numbers will appear in the Output panel.
