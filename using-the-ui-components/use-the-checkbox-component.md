# Use the CheckBox component

A CheckBox is a square box that can be selected or deselected. When it is
selected, a check mark appears in the box. You can add a text label to a
CheckBox and place it to the left, right, above, or below the CheckBox.

You can use CheckBoxes to gather a set of `true` or `false` values that aren't
mutually exclusive. For example, an application that gathers information about
what kind of car you want to buy might use CheckBoxes to let you select
features.

## User interaction with the CheckBox

You can enable or disable a CheckBox in an application. If a CheckBox is enabled
and a user clicks it or its label, the CheckBox receives input focus and
displays its pressed appearance. If a user moves the pointer outside the
bounding area of a CheckBox or its label while pressing the mouse button, the
component's appearance returns to its original state and retains input focus.
The state of a CheckBox does not change until the mouse is released over the
component. Additionally, the CheckBox has two disabled states, selected and
deselected, which use `selectedDisabledSkin` and `disabledSkin`, respectively,
that do not allow mouse or keyboard interaction.

If a CheckBox is disabled, it displays its disabled appearance, regardless of
user interaction. In the disabled state, a CheckBox doesn't receive mouse or
keyboard input.

A CheckBox instance receives focus if a user clicks it or tabs to it. When a
CheckBox instance has focus, you can use the following keys to control it:

| Key       | Description                                                         |
| --------- | ------------------------------------------------------------------- |
| Shift+Tab | Moves focus to the previous element.                                |
| Spacebar  | Selects or deselects the component and triggers the `change` event. |
| Tab       | Moves focus to the next element.                                    |

For more information about controlling focus, see
[Work with FocusManager](../working-with-components/work-with-focusmanager.md)
and the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

A live preview of each CheckBox instance reflects changes made to parameters in
the Property inspector or Component inspector during authoring.

When you add the CheckBox component to an application, you can make it
accessible to a screen reader by adding the following lines of ActionScript
code:

    import fl.accessibility.CheckBoxAccImpl;

    CheckBoxAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances you have of the component.

## CheckBox component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each CheckBox component instance: `label`,
`labelPlacement`, and `selected`. Each of these parameters has a corresponding
ActionScript property of the same name. For information on the possible values
for these parameters, see the CheckBox class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application using the CheckBox

The following procedure explains how to add a CheckBox component to an
application while authoring, using an excerpt from a loan application form. The
form asks if the applicant is a home owner and provides a CheckBox for the user
to answer "yes." If so, the form presents two radio buttons for the user to
indicate the relative value of the house.

### Create an application using the Checkbox component

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a CheckBox component from the Components panel to the Stage.

3.  In the Property inspector, do the following:

    - Enter **homeCh** for the instance name.

    - Enter **140** for the width (W) value.

    - Enter " **Own your home** ?" for the label parameter.

4.  Drag two RadioButton components from the Components panel to the Stage and
    place them below and to the right of the CheckBox. Enter the following
    values for them in the Property inspector:

    - Enter **underRb** and **overRb** for the instance names.

    - Enter **120** for the W (width) parameter of both RadioButtons.

    - Enter **Under \$500,000?** for the label parameter of `underRb`.

    - Enter **Over \$500,000?** for the label parameter of `overRb`.

    - Enter **valueGrp** for the groupName parameter for both RadioButtons.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        homeCh.addEventListener(MouseEvent.CLICK, clickHandler);
        underRb.enabled = false;
        overRb.enabled = false;

        function clickHandler(event:MouseEvent):void {
            underRb.enabled = event.target.selected;
            overRb.enabled = event.target.selected;
        }

    This code creates an event handler for a `CLICK` event that enables the
    `underRb` and `overRb` RadioButtons if the `homeCh` CheckBox is selected,
    and disables them if `homeCh` is not selected. For more information, see the
    MouseEvent class in the
    _[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
    .

6.  Select Control \> Test Movie.

The following example duplicates the preceding application but creates the
CheckBox and RadioButtons with ActionScript.

### Create a Checkbox using ActionScript

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the CheckBox component and the RadioButton component from the
    Components panel to the current document's Library panel. If the Library
    panel is not open, press Ctrl+L or select Window \> Library to open the
    Library panel.

    This makes the components available to your application but does not put
    them on the Stage.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following code to create and position the component instances:

        import fl.controls.CheckBox;
        import fl.controls.RadioButton;

        var homeCh:CheckBox = new CheckBox();
        var underRb:RadioButton = new RadioButton();
        var overRb:RadioButton = new RadioButton();
        addChild(homeCh);
        addChild(underRb);
        addChild(overRb);
        underRb.groupName = "valueGrp";
        overRb.groupName = "valueGrp";
        homeCh.move(200, 100);
        homeCh.width = 120;
        homeCh.label = "Own your home?";
        underRb.move(220, 130);
        underRb.enabled = false;
        underRb.width = 120;
        underRb.label = "Under $500,000?";
        overRb.move(220, 150);
        overRb.enabled = false;
        overRb.width = 120;
        overRb.label = "Over $500,000?";

    This code uses the `CheckBox()` and `RadioButton()` constructors to create
    the components and the `addChild()` method to place them on the Stage. It
    uses the `move()` method to position the components on the Stage.

4.  Now, add the following ActionScript to create an event listener and an event
    handler function:

        homeCh.addEventListener(MouseEvent.CLICK, clickHandler);

        function clickHandler(event:MouseEvent):void {
            underRb.enabled = event.target.selected;
            overRb.enabled = event.target.selected;
        }

    This code creates an event handler for the `CLICK` event that enables the
    `underRb` and `overRb` radio buttons if the `homeCh` CheckBox is selected,
    and disables them if `homeCh` is not selected. For more information, see the
    MouseEvent class in the
    _[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

5.  Select Control \> Test Movie.
