# ActionScript 3.0 event handling model

ActionScript 3.0 introduces a single event handling model that replaces the
different event handling mechanisms that existed in previous versions of
ActionScript. The new event model is based on the Document Object Model (DOM)
Level 3 Events Specification.

For developers with experience using the ActionScript 2.0 `addListener()`
method, it may be helpful to point out the differences between the ActionScript
2.0 event listener model and the ActionScript 3.0 event model. The following
list describes a few of the major differences between the two event models:

- To add event listeners in ActionScript 2.0, you use `addListener()` in some
  cases and `addEventListener()` in others, whereas in ActionScript 3.0 you use
  `addEventListener()` in all cases.

- There is no event flow in ActionScript 2.0, which means that the
  `addListener()` method can be called only on the object that broadcasts the
  event, whereas in ActionScript 3.0 the `addEventListener()` method can be
  called on any object that is part of the event flow.

- In ActionScript 2.0, event listeners can be either functions, methods, or
  objects, whereas in ActionScript 3.0, only functions or methods can be event
  listeners.

- The `on(` _event_ `)` syntax is no longer supported in ActionScript 3.0, so
  you cannot attach ActionScript event code to a movie clip. You can only use
  `addEventListener()` to add an event listener.

  The following example, which listens for a `MouseEvent.CLICK` event on a
  Button component called `aButton`, illustrates the basic ActionScript 3.0
  event handling model:

      aButton.addEventListener(MouseEvent.CLICK, clickHandler);
      function clickHandler(event:MouseEvent):void {
          trace("clickHandler detected an event of type: " + event.type);
          trace("the event occurred on: " + event.target.name);
      }

  For more information on ActionScript 3.0 event handling, see _Programming
  ActionScript 3.0_. For more information on ActionScript 3.0 event handling for
  components, see
  [Handling events](../working-with-components/handling-events.md).
