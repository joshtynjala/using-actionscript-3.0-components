# Use the TextArea component

The TextArea component is a wrapper for the native ActionScript TextField
object. You can use the TextArea component to display text and also to edit and
receive text input if the `editable` property is `true`. The component can
display or receive multiple lines of text and wraps long lines of text if the
`wordWrap` property is set to `true`. The `restrict` property allows you to
restrict the characters that a user can enter and `maxChars` allows you to
specify the maximum number of characters that a user can enter. If the text
exceeds the horizontal or vertical boundaries of the text area, horizontal and
vertical scroll bars automatically appear unless their associated properties,
`horizontalScrollPolicy` and `verticalScrollPolicy`, are set to `off`.

You can use a TextArea component wherever you need a multiline text field. For
example, you could use a TextArea component as a comment field in a form. You
could set up a listener that checks whether the field is empty when a user tabs
out of the field. That listener could display an error message indicating that a
comment must be entered in the field.

If you need a single-line text field, use the TextInput component.

You can set the `textFormat` style using the `setStyle()` method to change the
style of text that appears in a TextArea instance. You can also format a
TextArea component with HTML using the `htmlText` property in ActionScript, and
you can set the `displayAsPassword` property to `true` to mask text with
asterisks. If you set the `condenseWhite` property to `true`, Flash removes
extra white space in new text that is due to spaces, line breaks, and so on. It
has no effect on text that is already in the control.

## User interaction with the TextArea component

A TextArea component can be enabled or disabled in an application. In the
disabled state, it cannot receive mouse or keyboard input. When enabled, it
follows the same focus, selection, and navigation rules as an ActionScript
TextField object. When a TextArea instance has focus, you can control it using
the following keys:

| Key        | Description                                                                                 |
| ---------- | ------------------------------------------------------------------------------------------- |
| Arrow keys | Move the insertion point up, down, left, or right within the text, if the text is editable. |
| Page Down  | Moves the insertion point to the end of the text, if the text is editable.                  |
| Page Up    | Moves the insertion point to the beginning of the text, if the text is editable.            |
| Shift+Tab  | Moves focus to the previous object in the Tab loop.                                         |
| Tab        | Moves focus to the next object in the Tab loop.                                             |

For more information about controlling focus, see the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

## TextArea component parameters

You can set the following authoring parameters for each TextArea component
instance in the Property inspector or the Component inspector: `condenseWhite`,
`editable`, `hortizontalScrollPolicy`, `maxChars`, `restrict`, `text`,
`verticalScrollPolicy`, and `wordwrap`. Each of these parameters has a
corresponding ActionScript property of the same name. For information on the
possible values for these parameters, see the TextArea class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

A live preview of each TextArea instance reflects changes made to parameters in
the Property inspector or Component inspector during authoring. If a scroll bar
is needed, it appears in the live preview, but it does not function. Text is not
selectable in the live preview, and you cannot enter text in the component
instance on the Stage.

You can write ActionScript to control these and additional options for the
TextArea component using its properties, methods, and events. For more
information, see the TextArea class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the TextArea component

The following procedure explains how to add a TextArea component to an
application while authoring. The example sets up a `focusOut` event handler on
the TextArea instance that verifies that the user typed something in the text
area before giving focus to a different part of the interface.

1.  Create a new Flash document (ActionScript 3.0).

2.  Drag a TextArea component from the Components panel to the Stage and give it
    an instance name of **aTa**. Leave its parameters set to the default
    settings.

3.  Drag a second TextArea component from the Components panel to the Stage,
    place it below the first one and give it an instance name of **bTa**. Leave
    its parameters set to the default settings.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import flash.events.FocusEvent;

        aTa.restrict = "a-z,'\" \"";
        aTa.addEventListener(Event.CHANGE,changeHandler);
        aTa.addEventListener(FocusEvent.KEY_FOCUS_CHANGE, k_m_fHandler);
        aTa.addEventListener(FocusEvent.MOUSE_FOCUS_CHANGE, k_m_fHandler);

        function changeHandler(ch_evt:Event):void {
            bTa.text = aTa.text;
        }
        function k_m_fHandler(kmf_event:FocusEvent):void {
            kmf_event.preventDefault();
        }

    This example restricts the characters you can enter into the `aTa` text area
    to lowercase characters, the comma, the apostrophe, and spaces. It also sets
    up event handlers for the `change`, `KEY_FOCUS_CHANGE`, and
    `MOUSE_FOCUS_CHANGE` events on the `aTa` text area. The `changeHandler()`
    function causes the text that you enter in the `aTa` text area to
    automatically appear in the `bTa` text area by assigning `aTa.text` to
    `bTa.text` on each `change` event. The `k_m_fHandler()` function for the
    `KEY_FOCUS_CHANGE` and `MOUSE_FOCUS_CHANGE` events prevents you from
    pressing the Tab key to move to the next field without entering any text. It
    does this by preventing the default behavior.

5.  Select Control \> Test Movie.

    If you press the Tab key to move focus to the second text area without
    entering any text, you should see an error message and focus should return
    to the first text area. As you enter text in the first text area, you will
    see it duplicated in the second text area.

### Create a TextArea instance using ActionScript

The following example creates a TextArea component with ActionScript. It sets
the `condenseWhite` property to `true` to condense white space and assigns text
to the `htmlText` property to take advantage of HTML text formatting attributes.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the TextArea component to the Library panel.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.TextArea;

        var aTa:TextArea = new TextArea();

        aTa.move(100,100);
        aTa.setSize(200, 200);
        aTa.condenseWhite = true;
        aTa.htmlText = '<b>Lorem ipsum dolor</b> sit amet, consectetuer adipiscing elit. <u>Vivamus quis nisl vel tortor nonummy vulputate.</u> Quisque sit amet eros sed purus euismod tempor. Morbi tempor. <font color="#FF0000">Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos hymenaeos.</font> Curabitur diam. Suspendisse at purus in ipsum volutpat viverra. Nulla pellentesque libero id libero.';
        addChild(aTa);

    This example uses the `htmlText` property to apply HTML bold and underline
    attributes to a block of text and display it in the `a_ta` text area. The
    example also sets the `condenseWhite` property to `true` to condense the
    white space within the text block. The `setSize()` method sets the text
    area's height and width, and the `move()` method sets its position. The
    `addChild()` method adds the TextArea instance to the Stage.

4.  Select Control \> Test Movie.
