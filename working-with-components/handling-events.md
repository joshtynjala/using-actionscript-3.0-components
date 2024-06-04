# Handling events

Every component broadcasts events when a user interacts with it. When a user
clicks a Button, for example, it dispatches a `MouseEvent.CLICK` event and when
a user selects an item in a List, the List dispatches an Event. `CHANGE` event.
An event can also occur when something significant happens to a component such
as when content finishes loading for a UILoader instance, generating an
`Event.COMPLETE` event. To handle an event, you write ActionScript code that
executes when the event occurs.

A component's events include the events of any class from which the component
inherits. This means that all ActionScript 3.0 User Interface components inherit
events from the UIComponent class because it is the base class for the
ActionScript 3.0 User Interface components. To see the list of events a
component broadcasts, see the Events section of the component's class entry in
the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

For a complete explanation of event handling in ActionScript 3.0, see the
_[ActionScript 3.0 Developer's Guide](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/index.html)_.

## About event listeners

The following key points apply to handling events for ActionScript 3.0
components:

- All events are broadcast by an instance of a component class. The component
  instance is the _broadcaster_.

- You register an event _listener_ by calling the `addEventListener()` method
  for the component instance. For example, the following line of code adds a
  listener for the `MouseEvent.CLICK` event to the Button instance `aButton`:

      aButton.addEventListener(MouseEvent.CLICK, clickHandler);

  The second parameter of the `addEventListener()` method registers the name of
  the function, `clickHandler`, to be called when the event occurs. This
  function is also referred to as a _callback function_.

- You can register multiple listeners to one component instance.

      aButton.addEventListener(MouseEvent.CLICK, clickHandler1);
      aButton.addEventListener(MouseEvent.CLICK, clickHandler2);

- You can register one listener to multiple component instances.

      aButton.addEventListener(MouseEvent.CLICK, clickHandler1);
      bButton.addEventListener(MouseEvent.CLICK, clickHandler1);

- The event handler function is passed to an event object that contains
  information about the event type and the instance that broadcast the event.
  For more information, see [About the event object](#about-the-event-object).

- The listener remains active until the application terminates or you explicitly
  remove it using the `removeEventListener()` method. For example, the following
  line of code removes the listener for the `MouseEvent.CLICK` event on
  `aButton`:

      aButton.removeEventListener(MouseEvent.CLICK, clickHandler);

## About the event object

The event object inherits from the Event object class and has properties that
contain information about the event that occurred, including the `target` and
`type` properties, which provide essential information about the event:

| Property | Description                                                   |
| -------- | ------------------------------------------------------------- |
| `type`   | A string indicating the type of the event.                    |
| `target` | A reference to the component instance broadcasting the event. |

When an event has additional properties, they are listed in the event's class
description in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

The event object is automatically generated and passed to the event handler
function when an event occurs.

You can use the event object inside the function to access the name of the event
that was broadcast or the instance name of the component that broadcast the
event. From the instance name, you can access other component properties. For
example, the following code uses the `target` property of the `evtObj` event
object to access the `label` property of `aButton` and display it in the Output
panel:

    import fl.controls.Button;
    import flash.events.MouseEvent;

    var aButton:Button = new Button();
    aButton.label = "Submit";
    addChild(aButton);
    aButton.addEventListener(MouseEvent.CLICK, clickHandler);

    function clickHandler(evtObj:MouseEvent){
        trace("The " + evtObj.target.label + " button was clicked");
    }
