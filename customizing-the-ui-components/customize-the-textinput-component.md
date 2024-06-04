# Customize the TextInput component

You can change the size of a TextInput instance while authoring and at run time.
While authoring, select the component on the Stage and use the Free Transform
tool or any of the Modify \> Transform commands. At run time, use the
`setSize()` method or applicable properties of the TextInput class, such as
`height`, `width`, `scaleX`, and `scaleY`.

When a TextInput component is resized, the border is resized to the new bounding
box. The TextInput component doesn't use scroll bars, but the insertion point
scrolls automatically as the user interacts with the text. The text field is
then resized within the remaining area; there are no fixed-size elements in a
TextInput component. If the TextInput component is too small to display the
text, the text is clipped.

## Styles and the TextInput component

The TextInput component's styles specify values for its skins, padding, and text
formatting when the component is drawn. The `texFormat` and `disabledTextFormat`
styles govern the style of the text that displays in the component. For more
information about skin style properties, see
[Skins and the TextInput component](#skins-and-the-textinput-component).

The following example sets the `textFormat` style to set the font, size, and
color of the text that displays in the TextInput component. The same process
applies to setting the `disabledTextFormat` style that is applied when the
component is disabled.

1.  Create a new Flash document (ActionScript 3.0).

2.  Drag a TextInput component to the Stage and give it an instance name of
    **myTi**.

3.  Add the following code to the Actions panel on Frame 1 of the main Timeline.

        var tf:TextFormat = new TextFormat();
        tf.color = 0x0000FF;
        tf.font = "Verdana";
        tf.size = 30;
        tf.align = "center";
        tf.italic = true;
        myTi.setStyle("textFormat", tf);
        myTi.text = "Enter your text here";
        myTi.setSize(350, 50);
        myTi.move(100, 50);

4.  Select Control \> Test Movie.

## Skins and the TextInput component

The TextInput component uses the following skins, which you can edit to change
its appearance:

![](../img/cu_ti_skins.png)

<caption>TextInput skins</caption>

The following procedure changes the border and background colors of a TextInput
component:

1.  Create a new Flash file.

2.  Drag a TextInput component to the Stage and double-click it to open its
    panel of skins.

3.  Double-click the Normal skin.

4.  Set the zoom control to 800% to enlarge the icon for editing.

5.  Select each edge of the Normal skin's border, one at a time, and set its
    color to \#993399 to apply it.

6.  Double-click the background until its color appears in the Fill color picker
    in the Property inspector. Select color \#99CCCC to apply it to the
    background.

7.  Click the Back button at the left side of the edit bar above the Stage to
    return to document-editing mode.

8.  Select Control \> Test Movie.

    The TextInput component should appear as shown in the following
    illustration:

    ![TextInput component with changed border and background colors.](../img/cu_Ti_skin_ex.png)
