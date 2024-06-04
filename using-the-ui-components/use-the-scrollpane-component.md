# Use the ScrollPane component

You can use the ScrollPane component to display content that is too large for
the area into which it is loaded. For example, if you have a large image and
only a small space for it in an application, you could load it into a
ScrollPane. The ScrollPane can accept movie clips, JPEG, PNG, GIF, and SWF
files.

Components such as the ScrollPane and the UILoader have `complete` events that
allow you to determine when content has finished loading. If you want to set
properties on the content of a ScrollPane or UILoader component, listen for the
`complete` event and set the property in the event handler. For example, the
following code creates a listener for the Event. `COMPLETE` event and an event
handler that sets the `alpha` property of the ScrollPane's content to .5:

    function spComplete(event:Event):void{
        aSp.content.alpha = .5;
    }
    aSp.addEventListener(Event.COMPLETE, spComplete);

If you specify a location when loading content to the ScrollPane, you must
specify the location (X and Y coordinates) as 0, 0. For example, the following
code loads the ScrollPane properly because the box is drawn at location 0, 0:

    var box:MovieClip = new MovieClip();
    box.graphics.beginFill(0xFF0000, 1);
    box.graphics.drawRect(0, 0, 150, 300);
    box.graphics.endFill();
    aSp.source = box;    //load ScrollPane

For more information, see the ScrollPane class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## User interaction with the ScrollPane component

A ScrollPane can be enabled or disabled. A disabled ScrollPane doesn't receive
mouse or keyboard input. A user can use the following keys to control a
ScrollPane when it has focus:

| Key         | Description                                            |
| ----------- | ------------------------------------------------------ |
| Down Arrow  | Content moves up one vertical line scroll.             |
| Up Arrow    | Content moves down one vertical line scroll.           |
| End         | Content moves to the bottom of the ScrollPane.         |
| Left Arrow  | Content moves to the right one horizontal line scroll. |
| Right Arrow | Content moves to the left one horizontal line scroll.  |
| Home        | Content moves to the top of the ScrollPane.            |
| End         | Content moves to the bottom of the ScrollPane.         |
| PageDown    | Content moves up one vertical scroll page.             |
| PageUp      | Content moves down one vertical scroll page.           |

A user can use the mouse to interact with the ScrollPane both on its content and
on the vertical and horizontal scroll bars. The user can drag content by using
the mouse when the `scrollDrag` property is set to `true`. The appearance of a
hand pointer on the content indicates that the user can drag the content. Unlike
most other controls, actions occur when the mouse button is pressed and continue
until it is released. If the content has valid tab stops, you must set
`scrollDrag` to false. Otherwise all mouse hits on the contents will invoke
scroll dragging.

## ScrollPane component parameters

You can set the following parameters for each ScrollPane instance in the
Property inspector or in the Component inspector: `horizontalLineScrollSize`,
`horizontalPageScrollSize`,
`horizontalScrollPolicy, scrollDrag, source, verticalLineScrollSize, verticalPageScrollSize,`
and `verticalScrollPolicy`. Each of these parameters has a corresponding
ActionScript property of the same name. For information on the possible values
for these parameters, see the ScrollPane class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

You can write ActionScript to control these and additional options for a
ScrollPane component using its properties, methods, and events.

## Create an application with the ScrollPane component

The following procedure explains how to add a ScrollPane component to an
application while authoring. In this example, the ScrollPane loads a picture
from a path specified by the `source` property.

> **Note:** The examples below use the file
> [`image1.jpg`](../img/helpexamples/image1.jpg).

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ScrollPane component from the Components panel to the Stage and
    give it an instance name of **aSp**.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.events.ScrollEvent;

        aSp.setSize(300, 200);

        function scrollListener(event:ScrollEvent):void {
            trace("horizontalScPosition: " + aSp.horizontalScrollPosition +
                ", verticalScrollPosition = " + aSp.verticalScrollPosition);
        }
        aSp.addEventListener(ScrollEvent.SCROLL, scrollListener);

        function completeListener(event:Event):void {
            trace(event.target.source + " has completed loading.");
        }
        // Add listener.
        aSp.addEventListener(Event.COMPLETE, completeListener);

        aSp.source = "http://www.example.com/image1.jpg";

4.  Select Control \> Test Movie to run the application.

### Create a ScrollPane instance using ActionScript

The example creates a ScrollPane, sets its size, and loads an image to it using
the `source` property. It also creates two listeners. The first one listens for
a `scroll` event and displays the image's position as the user scrolls
vertically or horizontally. The second one listens for a `complete` event and
displays a message in the Output panel that says the image has completed
loading.

This example creates a ScrollPane using ActionScript and places a MovieClip (a
red box) in it that is 150 pixels wide by 300 pixels tall.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ScrollPane component from the Components panel to the Library
    panel.

3.  Drag the DataGrid component from the Components panel to the Library panel.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.containers.ScrollPane;
        import fl.controls.ScrollPolicy;
        import fl.controls.DataGrid;
        import fl.data.DataProvider;

        var aSp:ScrollPane = new ScrollPane();
        var aBox:MovieClip = new MovieClip();
        drawBox(aBox, 0xFF0000);    //draw a red box

        aSp.source = aBox;
        aSp.setSize(150, 200);
        aSp.move(100, 100);

        addChild(aSp);

        function drawBox(box:MovieClip,color:uint):void {
            box.graphics.beginFill(color, 1);
            box.graphics.drawRect(0, 0, 150, 300);
            box.graphics.endFill();
        }

5.  Select Control \> Test Movie to run the application.
