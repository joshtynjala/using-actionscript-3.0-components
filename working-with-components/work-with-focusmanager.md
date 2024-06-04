# Work with FocusManager

When a user presses the Tab key to navigate in a Flash application or clicks in
an application, the FocusManager class determines which component receives input
focus. You don't need to add a FocusManager instance to an application or write
any code to activate the FocusManager unless you are creating a component.

If a RadioButton object receives focus, the FocusManager examines that object
and all objects with the same `groupName` value and sets focus on the object
with the `selected` property set to `true`.

Each modal Window component contains an instance of the FocusManager, so the
controls on that window become their own tab set. This prevents a user from
inadvertently navigating to components in other windows by pressing the Tab key.

The FocusManager uses the depth level (or _z_ -order) of elements in the
container as the default navigation scheme or _tab loop_. A user typically
navigates the tab loop by using the Tab key, with focus moving from the first
component that has focus, to the last, and then back again to the first.The
depth levels are set up primarily by the order in which components are dragged
to the Stage; however, you can also use the Modify \> Arrange \> Bring To
Front/Send To Back commands to determine the final _z_ -order. For more
information on depth levels, see
[Work with the display list](./work-with-the-display-list.md).

You can call the `setFocus()` method to give focus to a component instance in an
application. For example, the following example creates a FocusManager instance
for the current container ( `this`) and gives focus to the Button instance
`aButton`.

    var fm:FocusManager = new FocusManager(this);
    fm.setFocus(aButton);

You can determine which component has focus by calling the `getFocus()` method
and you can determine which component in the tab loop will receive focus next by
calling the `getNextFocusManagerComponent()` method. In the following example, a
CheckBox, a RadioButton, and a Button are on the Stage and each component has
listeners for `MouseEvent.CLICK` and `FocusEvent.MOUSE_FOCUS_CHANGE` events.
When the `MouseEvent.CLICK` event occurs, because the user clicked on the
component, the `showFocus()` function calls the `getNextFocusManagerComponent()`
method to determine which component in the tab loop would receive focus next. It
then calls the `setFocus()` method to give focus to that component. When the
`FocusEvent.MOUSE_FOCUS_CHANGE` event occurs, the `fc()` function displays the
name of the component on which this event occurred. This event is triggered when
the user clicks on a component other than the next one in the tab loop.

    // This example assumes a CheckBox (aCh), a RadioButton (aRb) and a Button
    // (aButton) have been placed on the Stage.

    import fl.managers.FocusManager;
    import flash.display.InteractiveObject;

    var fm:FocusManager = new FocusManager(this);

    aCh.addEventListener(MouseEvent.CLICK, showFocus);
    aRb.addEventListener(MouseEvent.CLICK, showFocus);
    aButton.addEventListener(MouseEvent.CLICK, showFocus);
    aCh.addEventListener(FocusEvent.MOUSE_FOCUS_CHANGE, fc);
    aRb.addEventListener(FocusEvent.MOUSE_FOCUS_CHANGE, fc);
    aButton.addEventListener(FocusEvent.MOUSE_FOCUS_CHANGE, fc);

    function showFocus(event:MouseEvent):void {
        var nextComponent:InteractiveObject = fm.getNextFocusManagerComponent();
        trace("Next component in tab loop is: " + nextComponent.name);
        fm.setFocus(nextComponent);
    }

    function fc(fe:FocusEvent):void {
        trace("Focus Change: " + fe.target.name);
    }

To create a Button that receives focus when a user presses Enter (Windows) or
Return (Macintosh), set the `FocusManager.defaultButton` property to the Button
instance that you want to be the default Button, as in the following code:

    import fl.managers.FocusManager;

    var fm:FocusManager = new FocusManager(this);
    fm.defaultButton = okButton;

The FocusManager class overrides the default Flash Player focus rectangle and
draws a custom focus rectangle with rounded corners.

For more information about creating a focus scheme in a Flash application, see
the `FocusManager class` in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
To create a custom focus manager, you must create a class that implements the
_IFocusManager_ interface. For more information, see `IFocusManager` in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
