# Work with the display list

All ActionScript 3.0 components inherit from the DisplayObject class and,
therefore, have access to its methods and properties to interact with the
display list. The _display list_ is the hierarchy of displayed objects and
visual elements in an application. This hierarchy includes the following
elements:

- The Stage, which is the top-level container

- Display objects, which include shapes, MovieClips, and text fields, among
  others

- Display object containers, which are special types of display objects that can
  contain child display objects.

The order of objects in the display list determines their depth in the parent
container. An object's depth refers to its position from top to bottom or front
to back on the Stage or in its display container. The order of depth is apparent
when objects overlap but it exists even when they do not. Every object in the
display list has a corresponding depth on the Stage. If you want to change an
object's depth by placing it in front of or moving it behind other objects, you
need to change its position in the display list. The default order of objects in
the display list is the order in which they are placed on the Stage. Position 0
in the display list is the object at the bottom of the depth order.

## Add a component to the display list

You can add an object to a DisplayObjectContainer object by calling the
container's `addChild()` or `addChildAt()` method. In the case of the Stage, you
can also add an object to its display list during authoring by creating it, or
in the case of components, by dragging it to the Stage from the Components
panel. To add an object to a container with ActionScript, first create an
instance of it by invoking its constructor with the `new` operator and then call
the `addChild()` or `addChildAt()` method to place it on the Stage and in the
display list. The `addChild()` method places the object at the next position in
the display list, while `addChildAt()` specifies the position at which to add
the object. If you specify a position that is already occupied, the object at
that position, and those at higher positions, move up by 1. The `numChildren`
property of a DisplayObjectContainer object contains the number of display
objects that it contains. You can retrieve an object from the display list by
calling the `getChildAt()` method and specifying the position, or if you know
the name of the object, by calling the `getChildByName()` method.

Note: When you add a component with ActionScript, you must assign a name to it's
name property if you want to access it by name in the display list.

The following example displays the names and positions of three components in
the display list. First, drag a NumericStepper, a Button, and a ComboBox to the
Stage so that they overlap each other and give them instance names of **aNs**,
**aButton**, and **aCb**. Then add the following code to the Actions panel on
Frame 1 of the Timeline:

    var i:int = 0;
    while(i < numChildren) {
        trace(getChildAt(i).name + " is at position: " + i++);
    }

You should see the following lines in the Output panel:

    aNs is at position: 0
    aButton is at position: 1
    aCb is at position: 2

## Move a component in the display list

You can change the position of an object in the display list, and its display
depth, by calling the `addChildAt()` method and supplying the name of an object
and the position where you want to place it as the method's parameters. For
example, add the following code to the preceding example to place the
NumericStepper on top and repeat the loop to display the components' new
positions in the display list:

    this.addChildAt(aNs, numChildren - 1);
    i = 0;
    while(i < numChildren) {
        trace(getChildAt(i).name + " is at position: " + i++);
    }

You should see the following in the Output panel:

    aNs is at position: 0
    aButton is at position: 1
    aCb is at position: 2
    aButton is at position: 0
    aCb is at position: 1
    aNs is at position: 2

The NumericStepper should also appear in front of the other components on the
screen.

Note that `numChildren` is the number of objects (from 1 to _n_) in the display
list while the first position in the list is 0. So if there are three objects in
the list, the index position of the third object is 2. This means that you can
reference the last position in the display list, or the top object in terms of
display depth, as `numChildren - 1`.

## Remove a component from the display list

You can remove a component from a display object container and its display list
with the `removeChild()` and `removeChildAt()` methods. The following example
places three Button components in front of each other on the Stage and adds an
event listener for each of them. When you click each Button, the event handler
removes it from the display list and the Stage.

1.  Create a new Flash file (ActionScript 3.0) document.

2.  Drag a Button from the Components panel to the Library panel.

3.  Open the Actions panel, select Frame 1 in the main Timeline and add the
    following code:

        import fl.controls.Button;

        var i:int = 0;
        while(i++ < 3) {
            makeButton(i);
        }
        function removeButton(event:MouseEvent):void {
            removeChildAt(numChildren -1);
        }
        function makeButton(num) {
            var aButton:Button = new Button();
            aButton.name = "Button" + num;
            aButton.label = aButton.name;
            aButton.move(200, 200);
            addChild(aButton);
            aButton.addEventListener(MouseEvent.CLICK, removeButton);
        }

    For a complete explanation of the display list, see
    [Display programming](https://web.archive.org/web/20150322151545/http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7e58.html)
    in
    _[ActionScript 3.0 Developer's Guide](https://web.archive.org/web/20150322151545/http://help.adobe.com/en_US/as3/dev/index.html)_.
