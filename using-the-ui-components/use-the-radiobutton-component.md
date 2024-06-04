# Use the RadioButton component

The RadioButton component lets you force a user to make a single choice within a
set of choices. This component must be used in a group of at least two
RadioButton instances. Only one member of the group can be selected at any given
time. Selecting one radio button in a group deselects the currently selected
radio button in the group. You set the `groupName` parameter to indicate which
group a radio button belongs to.

A radio button is a fundamental part of many form applications on the web. You
can use radio buttons wherever you want a user to make one choice from a group
of options. For example, you would use radio buttons in a form to ask which
credit card a customer wants to use.

## User interaction with the RadioButton component

A radio button can be enabled or disabled. A disabled radio button doesn't
receive mouse or keyboard input. When the user clicks or tabs into a RadioButton
component group, only the selected radio button receives focus. The user can
then use the following keys to control it:

| Key                    | Description                                                                     |
| ---------------------- | ------------------------------------------------------------------------------- |
| Up Arrow/Left Arrow    | The selection moves to the previous radio button within the radio button group. |
| Down Arrow/Right Arrow | The selection moves to the next radio button within the radio button group.     |
| Tab                    | Moves focus from the radio button group to the next component.                  |

For more information about controlling focus, see the IFocusManager interface
and the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

A live preview of each RadioButton instance on the Stage reflects changes made
to parameters in the Property inspector or Component inspector during authoring.
However, the mutual exclusion of selection does not display in the live preview.
If you set the selected parameter to `true` for two radio buttons in the same
group, they both appear selected even though only the last instance created
appears selected at run time. For more information, see
[RadioButton component parameters](#radiobutton-component-parameters).

When you add the RadioButton component to an application, you can make it
accessible to a screen reader by adding the following lines of code:

    import fl.accessibility.RadioButtonAccImpl;
    RadioButtonAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances you have of the component. For more information, see Chapter 18,
"Creating Accessible Content," in Using Flash _._

## RadioButton component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each RadioButton component instance:
`groupName, label, LabelPlacement, selected`, and `value`. Each of these
parameters has a corresponding ActionScript property of the same name. For
information on the possible values for these parameters, see the RadioButton
class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

You can write ActionScript to set additional options for RadioButton instances
using the methods, properties, and events of the RadioButton class.

## Create an application with the RadioButton component

The following procedure explains how to add RadioButton components to an
application while authoring. In this example, the RadioButtons are used to
present a yes-or-no question. The data from the RadioButton is displayed in a
TextArea.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag two RadioButton components from the Components panel to the Stage.

3.  Select the first radio button. In the Property inspector, give it an
    instance name of **yesRb** and a group name of **rbGroup.**

4.  Select the second radio button. In the Property inspector, give it an
    instance name of **noRb** and a group name of **rbGroup.**

5.  Drag a TextArea component from the Components panel to the Stage and give it
    an instance name of **aTa**.

6.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        yesRb.label = "Yes";
        yesRb.value = "For";
        noRb.label = "No";
        noRb.value = "Against";

        yesRb.move(50, 100);
        noRb.move(100, 100);
        aTa.move(50, 30);
        noRb.addEventListener(MouseEvent.CLICK, clickHandler);
        yesRb.addEventListener(MouseEvent.CLICK, clickHandler);

        function clickHandler(event:MouseEvent):void {
            aTa.text = event.target.value;
        }

7.  Select Control \> Test Movie to run the application.

### Create a RadioButton using ActionScript

This example uses ActionScript to create three RadioButtons for the colors red,
blue, and green and draws a gray box. The `value` property for each RadioButton
specifies the hexadecimal value for the color associated with the button. When a
user clicks one of the RadioButtons, the `clickHandler()` function calls
`drawBox()`, passing the color from the RadioButton's `value` property to color
the box.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the RadioButton component to the Library panel.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.RadioButton;
        import fl.controls.RadioButtonGroup;

        var redRb:RadioButton = new RadioButton();
        var blueRb:RadioButton = new RadioButton();
        var greenRb:RadioButton = new RadioButton();
        var rbGrp:RadioButtonGroup = new RadioButtonGroup("colorGrp");

        var aBox:MovieClip = new MovieClip();
        drawBox(aBox, 0xCCCCCC);

        addChild(redRb);
        addChild(blueRb);
        addChild(greenRb);
        addChild(aBox);

        redRb.label = "Red";
        redRb.value = 0xFF0000;
        blueRb.label = "Blue";
        blueRb.value = 0x0000FF;
        greenRb.label = "Green";
        greenRb.value = 0x00FF00;
        redRb.group = blueRb.group = greenRb.group = rbGrp;
        redRb.move(100, 260);
        blueRb.move(150, 260);
        greenRb.move(200, 260);

        rbGrp.addEventListener(MouseEvent.CLICK, clickHandler);

        function clickHandler(event:MouseEvent):void {
            drawBox(aBox, event.target.selection.value);
        }

        function drawBox(box:MovieClip,color:uint):void {
            box.graphics.beginFill(color, 1.0);
            box.graphics.drawRect(125, 150, 100, 100);
            box.graphics.endFill();
        }

4.  Select Control \> Test Movie to run the application.

For more information, see the RadioButton class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
