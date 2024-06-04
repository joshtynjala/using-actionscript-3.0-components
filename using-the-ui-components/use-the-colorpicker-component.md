# Use the ColorPicker component

The ColorPicker component allows a user to select a color from a swatch list.
The default mode of the ColorPicker shows a single color in a square button.
When a user clicks the button, the list of available colors appears in a swatch
panel along with a text field that displays the hexadecimal value of the current
color selection.

You can set the colors that appear in the ColoPicker by setting its `colors`
property with the color values that you want to display.

## User interaction with the ColorPicker component

A ColorPicker allows a user to select a color and apply it to another object in
the application. For example, if you want to allow the user to personalize
elements of the application, such as a background color or the color of text,
you can include a ColorPicker and apply the color that the user selects.

A user chooses a color by clicking its swatch in the panel or by entering its
hexadecimal value in the text field. Once the user selects a color, you can use
the ColorPicker's `selectedColor` property to apply the color to text or another
object in the application.

A ColorPicker instance receives focus if a user moves the pointer over it or
tabs to it. When a ColorPicker's swatch panel is open, you can use the following
keys to control it:

| Key         | Description                                                     |
| ----------- | --------------------------------------------------------------- |
| Home        | Moves the selection to the first color in the swatch panel.     |
| Up Arrow    | Moves the selection up one row in the swatch panel.             |
| Down Arrow  | Moves the selection down one row in the swatch panel.           |
| Right Arrow | Moves the selection in the swatch panel one color to the right. |
| Left Arrow  | Moves the selection in the swatch panel one color to the left.  |
| End         | Moves the selection to the last color in the swatch panel.      |

## ColorPicker component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each ColorPicker instance: `selectedColor` and
`showTextField`. Each of these parameters has a corresponding ActionScript
property of the same name. For information on the possible values for these
parameters, see the ColorPicker class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the ColorPicker component

The following example adds a ColorPicker component to an application while
authoring. In this example, each time you change the color in the ColorPicker,
the `changeHandler()` function calls the `drawBox()` function to draw a new box
with the color you selected in the ColorPicker.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a ColorPicker from the Components panel to the center of the Stage and
    give it an instance name of **aCp**.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.events.ColorPickerEvent;

        var aBox:MovieClip = new MovieClip();
        drawBox(aBox, 0xFF0000);    //draw a red box
        addChild(aBox);

        aCp.addEventListener(ColorPickerEvent.CHANGE,changeHandler);

        function changeHandler(event:ColorPickerEvent):void {
            drawBox(aBox, event.target.selectedColor);
        }

        function drawBox(box:MovieClip,color:uint):void {
            box.graphics.beginFill(color, 1);
            box.graphics.drawRect(100, 150, 100, 100);
            box.graphics.endFill();
        }

4.  Select Control \> Test Movie.

5.  Click the ColorPicker and select a color to color the box.

### Create a ColorPicker using ActionScript

This example uses the `ColorPicker()` constructor and `addChild()` to create a
ColorPicker on the Stage. It sets the `colors` property to the color values for
red (0xFF0000), green (0x00FF00), and blue (0x0000FF) to specify the colors that
the ColorPicker will display. It also creates a TextArea and each time you
select a different color in the ColorPicker, the example changes the color of
the text in the TextArea to match.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ColorPicker component from the Components panel to the Library
    panel.

3.  Drag the TextArea component from the Components panel to the Library panel.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.ColorPicker;
        import fl.controls.TextArea;
        import fl.events.ColorPickerEvent;

        var aCp:ColorPicker = new ColorPicker();
        var aTa:TextArea = new TextArea();
        var aTf:TextFormat = new TextFormat();

        aCp.move(100, 100);
        aCp.colors = [0xff0000, 0x00ff00, 0x0000ff];
        aCp.addEventListener(ColorPickerEvent.CHANGE, changeHandler);

        aTa.text = "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Vivamus quis nisl vel tortor nonummy vulputate. Quisque sit amet eros sed purus euismod tempor. Morbi tempor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos. Curabitur diam. Suspendisse at purus in ipsum volutpat viverra. Nulla pellentesque libero id libero.";
        aTa.setSize(200, 200);
        aTa.move(200,100);

        addChild(aCp);
        addChild(aTa);

        function changeHandler(event:ColorPickerEvent):void {
            if(TextFormat(aTa.getStyle("textFormat"))){
                aTf = TextFormat(aTa.getStyle("textFormat"));
            }
            aTf.color = event.target.selectedColor;
            aTa.setStyle("textFormat", aTf);
        }

5.  Select Control \> Test Movie.
