# Use the TextInput component

The TextInput component is a single-line text component that is a wrapper for
the native ActionScript TextField object. If you need a multiline text field,
use the TextArea component. For example, you could use a TextInput component as
a password field in a form. You could also set up a listener that checks whether
the field has enough characters when a user tabs out of the field. That listener
could display an error message indicating that the proper number of characters
must be entered.

You can set the `textFormat` property using the `setStyle()` method to change
the style of text that appears in a TextInput instance. A TextInput component
can also be formatted with HTML or as a password field that disguises the text.

## User interaction with the TextInput component

A TextInput component can be enabled or disabled in an application. In the
disabled state, it doesn't receive mouse or keyboard input. When enabled, it
follows the same focus, selection, and navigation rules as an ActionScript
TextField object. When a TextInput instance has focus, you can also use the
following keys to control it:

| Key        | Description                                           |
| ---------- | ----------------------------------------------------- |
| Arrow keys | Move the insertion point one character left or right. |
| Shift+Tab  | Moves focus to the previous object.                   |
| Tab        | Moves focus to the next object.                       |

For more information about controlling focus, see the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

A live preview of each TextInput instance reflects changes made to parameters in
the Property inspector or Component inspector during authoring. Text is not
selectable in the live preview, and you cannot enter text in the component
instance on the Stage.

When you add the TextInput component to an application, you can use the
Accessibility panel to make it accessible to screen readers.

## TextInput component parameters

You can set the following authoring parameters for each TextInput component
instance in the Property inspector or the Component inspector: `editable`,
`displayAsPassword`, `maxChars`, `restrict`, and `text`. Each of these
parameters has a corresponding ActionScript property of the same name. For
information on the possible values for these parameters, see the TextInput class
in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

You can write ActionScript to control these and additional options for the
TextInput component using its properties, methods, and events. For more
information, see the TextInput class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the TextInput component

The following procedure explains how to add a TextInput component to an
application. The example uses two TextInput fields to receive and confirm a
password. It uses an event listener to see that a minimum of eight characters
have been entered and that the text for the two fields matches.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a Label component from the Components panel to the Stage and give it
    the following values in the Property inspector:

    - Enter the instance name **pwdLabel**.

    - Enter a value for W of **100**.

    - Enter a value for X of **50**.

    - Enter a value for Y of **150**.

    - In the Parameters section, enter a value of **Password:** for the text
      parameter.

3.  Drag a second Label component from the Components panel to the Stage and
    give it the following values:

    - Enter the instance name **confirmLabel**.

    - Enter a value for W of **100**.

    - Enter a value for X of **50**

    - Enter a value for Y of **200**.

    - In the Parameters section, enter a value of **Confirm** **Password:** for
      the text parameter.

4.  Drag a TextInput component from the Components panel to the Stage and give
    it the following values:

    - Enter the instance name **pwdTi**.

    - Enter a value for W of **150**.

    - Enter a value for X of **190**.

    - Enter a value for Y of **150**.

    - In the Parameters section, double-click the value for the
      `displayAsPassword` parameter and select **true**. This causes the value
      entered in the text field to be masked with asterisks.

5.  Drag a second TextInput component from the Components panel to the Stage and
    give it the following values:

    - Enter the instance name **confirmTi**.

    - Enter a value for W of **150**.

    - Enter a value for X of **190**.

    - Enter a value for Y of **200**.

    - In the Parameters section, double-click the value for the `displayA` s
      `Password` parameter and select **true**. This causes the value entered in
      the text field to be masked with asterisks.

6.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        function tiListener(evt_obj:Event){
            if(confirmTi.text != pwdTi.text || confirmTi.length < 8)
            {
                trace("Password is incorrect. Please reenter it.");
            }
            else
            {
                trace("Your password is: " + confirmTi.text);
            }
        }
        confirmTi.addEventListener("enter", tiListener);

    This code sets up an `enter` event handler on the TextInput instance called
    `confirmTi`. If the two passwords don't match or the user types fewer than
    eight characters, the example displays the message: "Password is incorrect.
    Please reenter it." If the passwords are eight characters or more and they
    match, the example displays the value entered in the Output panel.

7.  Select Control \> Test Movie.

### Create a TextInput instance using ActionScript

The following example creates a TextInput component using ActionScript. The
example also creates a Label that it uses to prompt a user to enter his or her
name. The example sets the component's `restrict` property to allow only
uppercase and lowercase letters, a period, and a space. It also creates a
TextFormat object that it uses to format the text in both the Label and
TextInput components.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a TextInput component from the Components panel to the Library panel.

3.  Drag a Label component from the Components panel to the Library panel.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.Label;
        import fl.controls.TextInput;

        var nameLabel:Label = new Label();
        var nameTi:TextInput = new TextInput();
        var tf:TextFormat = new TextFormat();

        addChild(nameLabel);
        addChild(nameTi);

        nameTi.restrict = "A-Z .a-z";

        tf.font = "Georgia";
        tf.color = 0x0000CC;
        tf.size = 16;

        nameLabel.text = "Name: " ;
        nameLabel.setSize(50, 25);
        nameLabel.move(100,100);
        nameLabel.setStyle("textFormat", tf);
        nameTi.move(160, 100);
        nameTi.setSize(200, 25);
        nameTi.setStyle("textFormat", tf);

5.  Select Control \> Test Movie to run the application.
