# Use the Label component

The Label component displays a single line of text, typically to identify some
other element or activity on a web page. You can specify that a label be
formatted with HTML to take advantage of its text formatting tags. You can also
control the alignment and size of a label. Label components don't have borders,
cannot be focused, and don't broadcast any events.

A live preview of each Label instance reflects changes made to parameters in the
Property inspector or Component inspector during authoring. The label doesn't
have a border, so the only way to see its live preview is to set its text
parameter.

## User interaction with the Label component

Use a Label component to create a text label for another component in a form,
such as a "Name:" label to the left of a TextInput field that accepts a user's
name. It's a good idea to use a Label component instead of a plain text field
because you can use styles to maintain a consistent look and feel.

If you want to rotate a Label component, you must embed the fonts; otherwise
they won't show when you test the movie.

## Label component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each Label component instance: `autoSize`,
`condenseWhite`, `selectable`, `text`, and `wordWrap`. Each of these parameters
has a corresponding ActionScript property of the same name. For information on
the possible values for these parameters, see the Label class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the Label component

The following procedure explains how to add a Label component to an application
while authoring. In this example, the label simply displays the text "Expiration
Date."

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a Label component from the Components panel to the Stage and give it
    the following values in the Property inspector:

    - Enter **aLabel** for the instance name.

    - Enter **80** for the W value.

    - Enter **100** for the X value.

    - Enter **100** for the Y value.

    - Enter **Expiration Date** for the `text` parameter.

3.  Drag a TextArea component to the Stage and give it the following values in
    the Property inspector:

    - Enter **aTa** for the instance name.

    - Enter **22** for the H value.

    - Enter **200** for the X value.

    - Enter **100** for the Y value.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        var today:Date = new Date();
        var expDate:Date = addDays(today, 14);
        aTa.text = expDate.toDateString();

        function addDays(date:Date, days:Number):Date {
            return addHours(date, days*24);
        }

        function addHours(date:Date, hrs:Number):Date {
            return addMinutes(date, hrs*60);
        }

        function addMinutes(date:Date, mins:Number):Date {
            return addSeconds(date, mins*60);
        }

        function addSeconds(date:Date, secs:Number):Date {
            var mSecs:Number = secs * 1000;
            var sum:Number = mSecs + date.getTime();
            return new Date(sum);
        }

5.  Select Control \> Test Movie.

### Create a Label component instance using ActionScript

The following example creates a Label parameter using ActionScript. It uses a
Label to identify the function of a ColorPicker component and it uses the
`htmlText` property to apply formatting to the Label's text.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the Label component from the Components panel to the current document's
    Library panel.

3.  Drag the ColorPicker component from the Components panel to the current
    document's Library panel.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.Label;
        import fl.controls.ColorPicker;

        var aLabel:Label = new Label();
        var aCp:ColorPicker = new ColorPicker();

        addChild(aLabel);
        addChild(aCp);

        aLabel.htmlText = '<font face="Arial" color="#FF0000" size="14">Fill:</font>';
        aLabel.x = 200;
        aLabel.y = 150;
        aLabel.width = 25;
        aLabel.height = 22;

        aCp.x = 230;
        aCp.y = 150;

5.  Select Control \> Test Movie.
