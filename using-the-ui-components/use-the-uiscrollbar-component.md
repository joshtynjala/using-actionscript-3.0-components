# Use the UIScrollBar component

The UIScrollBar component allows you to add a scroll bar to a text field. You
can add a scroll bar to a text field while authoring, or at run time with
ActionScript. To use the UIScrollBar component, create a text field on the Stage
and drag the UIScrollBar component from the Components panel to any quadrant of
the text field's bounding box.

If the length of the scroll bar is smaller than the combined size of its scroll
arrows, it does not display correctly. One of the arrow buttons becomes hidden
behind the other. Flash does not provide error checking for this. In this case
it is a good idea to hide the scroll bar with ActionScript. If the scroll bar is
sized so that there is not enough room for the scroll box (thumb), Flash makes
the scroll box invisible.

The UIScrollBar component functions like any other scroll bar. It contains arrow
buttons at either end and a scroll track and scroll box (thumb) in between. It
can be attached to any edge of a text field and used both vertically and
horizontally.

For information on the TextField, see the TextField class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## User interaction with the UIScrollBar component

Unlike many other components, the UIScrollBar component can receive continuous
mouse input, such as when the user holds the mouse button down, rather than
requiring repeated clicks.

There is no keyboard interaction with the UIScrollBar component.

## UIScrollBar component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each UIScrollBar component instance: `direction` and
`scrollTargetName`. Each of these parameters has a corresponding ActionScript
property of the same name.

You can write ActionScript to set additional options for UIScrollBar instances
using class methods, properties, and events. For more information, see the
UIScrollBar class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the UIScrollBar component

The following procedure describes how to add a UIScrollBar component to an
application while authoring.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Create a dynamic text field that is tall enough to hold one or two lines of
    text and give it an instance name **myText** in the Property inspector.

3.  In the Property inspector, set the Line Type of the text input field to
    Multiline or to Multiline No Wrap if you plan to use the scroll bar
    horizontally.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code to fill the `text` property so that a user will
    need to scroll it to view it all:

        myText.text="When the moon is in the seventh house and Jupiter aligns with Mars, then peace will guide the planet and love will rule the stars."

    > **Note:** Make sure that the text field on the Stage is small enough that
    > you need to scroll it to see all the text. If it isn't, the scroll bar
    > does not appear or may appear simply as two lines with no thumb grip (the
    > part you drag to scroll the content).

5.  Verify that object snapping is turned on (View \> Snapping \> Snap To
    Objects).

6.  Drag a UIScrollBar instance from the Components panel onto the text input
    field near the side you want to attach it to. The component must overlap
    with the text field when you release the mouse in order for it to be
    properly bound to the field. Give it an instance name of **mySb.**

    The `scrollTargetName` property of the component is automatically populated
    with the text field instance name in the Property and Component inspectors.
    If it does not appear on the Parameters tab, you may not have overlapped the
    UIScrollBar instance enough.

7.  Select Control \> Test Movie.

### Create a UIScrollBar component instance using ActionScript

You can create a UIScrollBar instance with ActionScript and associate it with a
text field at run time. The following example creates a horizontally oriented
UIScrollBar instance and attaches it to the bottom of a text field instance
named **myTxt**, which is loaded with text from a URL. The example also sets the
size of the scroll bar to match the size of the text field.

> **Note:** The example below uses the file
> [`lorem.txt`](../img/helpexamples/lorem.txt).

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ScrollBar component to the Library panel.

3.  Open the Actions panel, select Frame 1 of the main Timeline, and enter the
    following ActionScript code:

        import flash.net.URLLoader;
        import fl.controls.UIScrollBar;
        import flash.events.Event;

        var myTxt:TextField = new TextField();
        myTxt.border = true;
        myTxt.width = 200;
        myTxt.height = 16;
        myTxt.x = 200;
        myTxt.y = 150;

        var mySb:UIScrollBar = new UIScrollBar();
        mySb.direction = "horizontal";
        // Size it to match the text field.
        mySb.setSize(myTxt.width, myTxt.height);

        // Move it immediately below the text field.
        mySb.move(myTxt.x, myTxt.height + myTxt.y);

        // put them on the Stage
        addChild(myTxt);
        addChild(mySb);
        // load text
        var loader:URLLoader = new URLLoader();
        var request:URLRequest = new URLRequest("http://www.example.com/lorem.txt");
        loader.load(request);
        loader.addEventListener(Event.COMPLETE, loadcomplete);

        function loadcomplete(event:Event) {
            // move loaded text to text field
            myTxt.text = loader.data;
            // Set myTxt as target for scroll bar.
            mySb.scrollTarget = myTxt;
        }

4.  Select Control \> Test Movie.
