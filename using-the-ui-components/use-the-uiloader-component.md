# Use the UILoader component

The UILoader component is a container that can display SWF, JPEG, progressive
JPEG, PNG, and GIF files. You can use a UILoader whenever you need to retrieve
content from a remote location and pull it into a Flash application. For
example, you could use a UILoader to add a company logo (JPEG file) to a form.
You could also use the UILoader component in an application that displays
photos. Use the `load()` method to load content, the `percentLoaded` property to
determine how much content has loaded, and the `complete` event to determine
when loading is finished.

You can scale the contents of the UILoader or resize the UILoader itself to
accommodate the size of the contents. By default, the contents are scaled to fit
the UILoader. You can also load content at run time and monitor loading progress
(although after content has been loaded once it is cached, the progress jumps to
100% quickly). If you specify a location when loading content in the UILoader,
you must specify the location (X and Y coordinates) as 0, 0.

> **Note:** The examples below use the file
> [`image1.jpg`](../img/helpexamples/image1.jpg).

## User interaction with the UILoader component

A UILoader component can't receive focus. However, content loaded into the
UILoader component can accept focus and have its own focus interactions. For
more information about controlling focus, see the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

## UILoader component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each UILoader component instance: `autoLoad`,
`maintainAspectRatio`, `source`, and `scaleContent`. Each of these parameters
has a corresponding ActionScript property of the same name.

A live preview of each UILoader instance reflects changes made to parameters in
the Property inspector or Component inspector during authoring.

You can write ActionScript to set additional options for UILoader instances
using its methods, properties, and events. For more information, see the
UILoader class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the UILoader component

The following procedure explains how to add a UILoader component to an
application while authoring. In this example, the loader loads a JPG image of a
logo.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a UILoader component from the Components panel to the Stage.

3.  In the Property inspector, enter the instance name **aUI**.

4.  Select the loader on the Stage and in the Component inspector, and enter
    **image1.jpg** for the `source` parameter.

## Create a UILoader component instance using ActionScript

This example creates a UILoader component using ActionScript and loads a JPEG
image of a flower. When the `complete` event occurs, it displays the number of
bytes loaded in the Output panel.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the UILoader component from the Components panel to the Library panel.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.containers.UILoader;

        var aLoader:UILoader = new UILoader();
        aLoader.source = "http://www.example.com/image1.jpg";
        aLoader.scaleContent = false;
        addChild(aLoader);

        aLoader.addEventListener(Event.COMPLETE, completeHandler);
        function completeHandler(event:Event) {
            trace("Number of bytes loaded: " + aLoader.bytesLoaded);
        }

4.  Select Control \> Test Movie.
