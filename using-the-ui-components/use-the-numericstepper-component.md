# Use the NumericStepper component

The NumericStepper component allows a user to step through an ordered set of
numbers. The component consists of a number in a text box displayed beside small
up and down arrow buttons. When a user presses the buttons, the number is raised
or lowered incrementally according to the unit specified in the `stepSize`
parameter until the user releases the buttons or until the maximum or minimum
value is reached. The text in the NumericStepper component's text box is also
editable.

A live preview of each NumericStepper instance reflects the setting of the value
parameter in the Property inspector or Component inspector. However, there is no
mouse or keyboard interaction with the NumericStepper's arrow buttons in the
live preview.

## User interaction with the NumericStepper component

You can use the NumericStepper component anywhere you want a user to select a
numeric value. For example, you could use a NumericStepper component in a form
to set the month, day, and year of a credit card expiration date. You could also
use a NumericStepper component to allow a user to increase or decrease a font
size.

The NumericStepper component handles only numeric data. Also, you must resize
the stepper while authoring to display more than two numeric places (for
example, the numbers 5246 or 1.34).

You can enable or disable a NumericStepper in an application. In the disabled
state, a NumericStepper doesn't receive mouse or keyboard input. When it's
enabled, the NumericStepper receives focus if you click it or tab to it, and its
internal focus is set to the text box. When a NumericStepper instance has focus,
you can use the following keys to control it:

| Key         | Description                                                 |
| ----------- | ----------------------------------------------------------- |
| Down Arrow  | Value changes by one unit.                                  |
| Left Arrow  | Moves the insertion point to the left within the text box.  |
| Right Arrow | Moves the insertion point to the right within the text box. |
| Shift+Tab   | Moves focus to the previous object.                         |
| Tab         | Moves focus to the next object.                             |
| Up Arrow    | Value changes by one unit.                                  |

For more information about controlling focus, see the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

## NumericStepper component parameters

You can set the following parameters in the Property inspector or in the
Component inspector for each NumericStepper instance: `maximum`, `minimum`,
`stepSize`, and `value`. Each of these parameters has a corresponding
ActionScript property of the same name. For information on the possible values
for these parameters, see the NumericStepper class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the NumericStepper

The following procedure explains how to add a NumericStepper component to an
application while authoring. The example places a NumericStepper component and a
Label component on the Stage and creates a listener for an `Event`. `CHANGE`
event on the NumericStepper instance. When the value in the numeric stepper
changes, the example displays the new value in the `text` property of the Label
instance.

1.  Drag a NumericStepper component from the Components panel to the Stage.

2.  In the Property inspector, enter the instance name **aNs**.

3.  Drag a Label component from the Components panel to the Stage.

4.  In the Property inspector, enter the instance name **aLabel**.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import flash.events.Event;

        aLabel.text = "value = " + aNs.value;

        aNs.addEventListener(Event.CHANGE, changeHandler);
        function changeHandler(event:Event) :void {
            aLabel.text = "value = " + event.target.value;
        }

    This example sets the `text` property of the label to the value of the
    NumericStepper. The `changeHandler()` function updates the label's `text`
    property whenever the value in the NumericStepper instance changes.

6.  Select Control \> Test Movie.

#### Create a NumericStepper using ActionScript:

This example creates three NumericSteppers with ActionScript code, one each for
entering the month, day, and year of the user's date of birth. It also adds
Labels for a prompt and for identifiers for each of the NumericSteppers.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a Label to the Library panel.

3.  Drag a NumericStepper component to the Library panel.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.Label;
        import fl.controls.NumericStepper;

        var dobPrompt:Label = new Label();
        var moPrompt:Label = new Label();
        var dayPrompt:Label = new Label();
        var yrPrompt:Label = new Label();

        var moNs:NumericStepper = new NumericStepper();
        var dayNs:NumericStepper = new NumericStepper();
        var yrNs:NumericStepper = new NumericStepper();

        addChild(dobPrompt);
        addChild(moPrompt);
        addChild(dayPrompt);
        addChild(yrPrompt);
        addChild(moNs);
        addChild(dayNs);
        addChild(yrNs);

        dobPrompt.setSize(65, 22);
        dobPrompt.text = "Date of birth:";
        dobPrompt.move(80, 150);

        moNs.move(150, 150);
        moNs.setSize(40, 22);
        moNs.minimum = 1;
        moNs.maximum = 12;
        moNs.stepSize = 1;
        moNs.value = 1;

        moPrompt.setSize(25, 22);
        moPrompt.text = "Mo.";
        moPrompt.move(195, 150);

        dayNs.move(225, 150);
        dayNs.setSize(40, 22);
        dayNs.minimum = 1;
        dayNs.maximum = 31;
        dayNs.stepSize = 1;
        dayNs.value = 1;

        dayPrompt.setSize(25, 22);
        dayPrompt.text = "Day";
        dayPrompt.move(270, 150);

        yrNs.move(300, 150);
        yrNs.setSize(55, 22);
        yrNs.minimum = 1900;
        yrNs.maximum = 2006;
        yrNs.stepSize = 1;
        yrNs.value = 1980;

        yrPrompt.setSize(30, 22);
        yrPrompt.text = "Year";
        yrPrompt.move(360, 150);

5.  Select Control \> Test Movie to run the application.
