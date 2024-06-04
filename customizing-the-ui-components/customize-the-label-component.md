# Customize the Label component

You can transform a Label component horizontally and vertically while authoring
and at run time. While authoring, select the component on the Stage and use the
Free Transform tool or any of the Modify \> Transform commands. You can also set
the `autoSize` authoring parameter; setting this parameter doesn't change the
bounding box in the live preview, but the Label is resized. The Label is resized
depending on the `wordwrap` parameter. If the parameter is `true`, the Label is
resized vertically to fit the text. If the parameter is `false`, the Label is
resized horizontally. At run time, use the `setSize()` method. For more
information see the `Label.setSize()` method and `Label.autoSize` property in
the _ActionScript 3.0 Reference for the Adobe Flash Platform_. Also see
[Create an application with the Label component](../using-the-ui-components/use-the-label-component.md#create-an-application-with-the-label-component).

## Use styles with the Label component

You can set style properties to change the appearance of a label instance. All
text in a Label component instance must share the same style. The Label
component has a `textFormat` style, which has the same attributes as the
TextFormat object and allows you to set the same properties for the content of
`Label.text` as you can for a regular Flash TextField. The following example
sets the color of text in a label to red.

1.  Drag the Label component from the Components panel to the Stage and give it
    an instance name of `a_label`.

2.  Click the Parameters tab and replace the value of the text property with the
    text:

    **Color me red**

3.  Select Frame 1 in the main Timeline, open the Actions panel, and enter the
    following code:

        /* Create a new TextFormat object, which allows you to set multiple text properties at a time. */

        var tf:TextFormat = new TextFormat();
        tf.color = 0xFF0000;
        /* Apply this specific text format (red text) to the Label instance. */
        a_label.setStyle("textFormat", tf);

4.  Select Control \> Test Movie.

    For more information about Label styles, see the Label class in the
    _[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Skins and the Label

The Label component does not have any visual elements to skin.
