# Use the Button component

The Button component is a resizable, rectangular button that a user can press
with the mouse or the spacebar to initiate an action in the application. You can
add a custom icon to a Button. You can also change the behavior of a Button from
push to toggle. A toggle Button stays pressed when clicked and returns to its up
state when clicked again.

A Button is a fundamental part of many forms and web applications. You can use
buttons wherever you want a user to initiate an event. For example, most forms
have a Submit button. You could also add Previous and Next buttons to a
presentation.

## User interaction with the Button component

You can enable or disable a button in an application. In the disabled state, a
button doesn't receive mouse or keyboard input. An enabled button receives focus
if you click it or tab to it. When a Button instance has focus, you can use the
following keys to control it:

| Key          | Description                                                                             |
| ------------ | --------------------------------------------------------------------------------------- |
| Shift+Tab    | Moves focus to the previous object.                                                     |
| Spacebar     | Presses or releases the button and triggers the `click` event.                          |
| Tab          | Moves focus to the next object.                                                         |
| Enter/Return | Moves focus to the next object if a button is set as the FocusManager's default Button. |

For more information about controlling focus, see the IFocusManager interface
and the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

A live preview of each Button instance reflects changes made to parameters in
the Property inspector or Component inspector during authoring.

> **Note:** If an icon is larger than the button, it extends beyond the button's
> borders.

To designate a button as the default push button in an application (the button
that receives the click event when a user presses Enter), set
`FocusManager.defaultButton`. For example, the following code sets the default
button to be a Button instance called `submitButton`.

    FocusManager.defaultButton = submitButton;

When you add the Button component to an application, you can make it accessible
to a screen reader by adding the following lines of ActionScript code:

    import fl.accessibility.ButtonAccImpl;

    ButtonAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances you create.

## Button component parameters

You can set the following authoring parameters in the Property inspector
(Window \> Properties \> Properties) or in the Component inspector (Window \>
Component Inspector) for each Button instance: `emphasized`, `label`,
`labelPlacement`, `selected`, and `toggle`. Each of these parameters has a
corresponding ActionScript property of the same name. When you assign a value to
these parameters you are setting the initial state of the property in the
application. Setting the property in ActionScript overrides the value you set in
the parameter. For information on the possible values for these parameters, see
the Button class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the Button component

The following procedure explains how to add a Button component to an application
while authoring. In this example, the Button changes the state of a ColorPicker
component when you click it.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a Button component from the Components panel to the Stage and enter the
    following values for it in the Property inspector:

    - Enter the instance name **aButton**.

    - Enter **Show** for the label parameter.

3.  Add a ColorPicker to the Stage and give it an instance name of **aCp**.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        aCp.visible = false;

        aButton.addEventListener(MouseEvent.CLICK, clickHandler);

        function clickHandler(event:MouseEvent):void {
            switch(event.currentTarget.label) {
                case "Show":
                    aCp.visible = true;
                    aButton.label = "Disable";
                    break;
                case "Disable":
                    aCp.enabled = false;
                    aButton.label = "Enable";
                    break;
                case "Enable":
                    aCp.enabled = true;
                    aButton.label = "Hide";
                    break;
                case "Hide":
                    aCp.visible = false;
                    aButton.label = "Show";
                    break;
            }
        }

    The second line of code registers the function `clickHandler()` as the event
    handler function for the `MouseEvent.CLICK` event. The event occurs when a
    user clicks the Button, causing the `clickHandler()` function to take one of
    the following actions depending on the Button's value:

    - Show makes the ColorPicker visible and changes the Button's label to
      Disable.

    - Disable disables the ColorPicker and changes the Button's label to Enable.

    - Enable enables the ColorPicker and changes the Button's label to Hide.

    - Hide makes the ColorPicker invisible and changes the Button's label to
      Show.

5.  Select Control \> Test Movie to run the application.

### Create an application with the Button component

The following procedure creates a toggle Button using ActionScript and displays
the event type in the Output panel when you click the Button. The example
creates the Button instance by invoking the class's constructor and it adds it
to the Stage by calling the `addChild()` method.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the Button component from the Components panel to the current
    document's Library panel.

    This adds the component to the library, but doesn't make it visible in the
    application.

3.  Open the Actions panel, select Frame 1 in the main Timeline and enter the
    following code to create a Button instance:

        import fl.controls.Button;

        var aButton:Button = new Button();
        addChild(aButton);
        aButton.label = "Click me";
        aButton.toggle =true;
        aButton.move(50, 50);

    The `move()` method positions the button at location 50 (x coordinate), 50
    (y coordinate) on the Stage.

4.  Now, add the following ActionScript to create an event listener and an event
    handler function:

        aButton.addEventListener(MouseEvent.CLICK, clickHandler);

        function clickHandler(event:MouseEvent):void {
            trace("Event type: " + event.type);
        }

5.  Select Control \> Test Movie.

    When you click the button, Flash displays the message, "Event type: click"
    in the Output panel.
