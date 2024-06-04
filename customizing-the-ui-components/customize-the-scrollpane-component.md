# Customize the ScrollPane component

You can transform a ScrollPane component horizontally and vertically while
authoring and at run time. While authoring, select the component on the Stage
and use the Free Transform tool or any of the Modify \> Transform commands. At
run time, use the `setSize()` method or any applicable properties or methods of
the ScrollPane class, such as the `height`, `width`, `scaleX`, and `scaleY`.

The ScrollPane component has the following graphical characteristics:

- The registration point (also _origin point_ or _zero point_) of its content is
  in the upper-left corner of the pane.

- When the horizontal scroll bar is turned off, the vertical scroll bar is
  displayed from top to bottom along the right side of the scroll pane. When the
  vertical scroll bar is turned off, the horizontal scroll bar is displayed from
  left to right along the bottom of the scroll pane. You can also turn off both
  scroll bars.

- If the scroll pane is too small, the content may not display correctly.

- When the scroll pane is resized, the scroll track and scroll box (thumb)
  expand or contract, and their hit areas are resized. The buttons remain the
  same size.

## Use styles with the ScrollPane component

The style properties of the ScrollPane component specify values for its skins
and padding for its layout when the component is drawn. The various skin styles
allow you to specify different classes to use for the component's skins. For
more information on using skin styles, see [About Skins](./about-skins.md).

> **Note:** The example below uses the file
> [`image1.jpg`](../img/helpexamples/image1.jpg).

1.  Create a new Flash document (ActionScript 3.0).

2.  Drag a ScrollPane component to the Stage and give it an instance name of
    **mySp**.

3.  Click the Parameters tab in the Property inspector and enter the following
    value for the `source` parameter: **image1.jpg**.

4.  On Frame 1 of the main Timeline, add the following code to the Actions
    panel.

        mySp.setStyle("contentPadding", 5);

    Note that the padding is applied between the component's border and its
    content, on the outside of the scroll bars.

5.  Select Control \> Test Movie.

## Skins and the ScrollPane

The ScrollPane component uses a border and scroll bars for scroll assets. For
information on skinning scroll bars see
[Use skins with the UIScrollBar component](./customize-the-uiscrollbar-component.md#use-skins-with-the-uiscrollbar-component).
