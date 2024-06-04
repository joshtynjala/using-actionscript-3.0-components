# Add to and delete from a document

When you drag a FLA-based component from the Components panel to the Stage,
Flash imports an editable movie clip to the library. When you drag a SWC-based
component to the Stage, Flash imports a compiled clip to the library. After a
component has been imported to the library, you can drag instances of it to the
Stage from either the Library panel or the Components panel.

## Add components during authoring

You can add a component to a document by dragging it from the Components panel.
You can set properties for each instance of a component in the Property
inspector or in the Parameters tab in the Component inspector.

1.  Select Window \> Components.

2.  Either double-click the component in the Components panel or drag the
    component to the Stage.

3.  Select the component on the Stage.

4.  If the Property inspector is not visible, select Window \> Properties \>
    Properties.

5.  In the Property inspector, enter an instance name for the component
    instance.

6.  Select Window \> Component inspector and select the Parameters tab to
    specify parameters for the instance.

    For more information, see
    [Set parameters and properties](../working-with-components/set-parameters-and-properties.md).

7.  Change the size of the component as desired by editing the values for the
    width (W:) and height (H:).

    For more information on sizing specific component types, see
    [Customizing the UI Components](../customizing-the-ui-components/index.md).

8.  Select Control \> Test Movie or press Control+Enter to compile the document
    and see the results of your settings.

    You can also change the color and text formatting of a component by setting
    style properties for it or customize its appearance by editing the
    component's skins. For more information on these topics, see
    [Customizing the UI Components](../customizing-the-ui-components/index.md).

    If you drag a component to the Stage during authoring, you can refer to the
    component by using its instance name (for example, `myButton`).

## Add components at run time with ActionScript

To add a component to a document at run time with ActionScript, the component
must first be in the application's library (Window \> Library) when the SWF file
is compiled. To add a component to the library, drag the component from the
Components panel into the Library panel. For more information on the library,
see [The library](../working-with-components/the-library.md).

You must also import the component's class file to make its API available to
your application. Component class files are installed in _packages_ that contain
one or more classes. To import a component class, use the `import` statement and
specify the package name and class name. You would import the Button class, for
example, with the following `import` statement:

    import fl.controls.Button;

For information on what package a component is in, see the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).
For information about the location of component source files, see
[Working with component files](../working-with-components/working-with-component-files.md).

To create an instance of the component, you must invoke the component's
ActionScript constructor method. For example, the following statement creates an
instance of a Button called `aButton`:

    var aButton:Button = new Button();

The final step is to call the static `addChild()` method to add the component
instance to the Stage or application container. For example, the following
statement adds the `aButton` instance:

    addChild(aButton);

At this point, you can use the component's API to dynamically specify the
component's size and position on the Stage, listen for events, and set
properties to modify its behavior. For more information on the API for a
particular component, see the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).

For more information on the `addChild()` method, see
[Work with the display list](../working-with-components/work-with-the-display-list.md).

## Delete a component

To delete a component instance from the Stage while authoring, simply select it
and press the Delete key. This will remove the instance from the Stage but does
not remove the component from your application.

To delete a component from your Flash document after you've placed it on the
Stage or in the library, you must delete it and its associated assets from the
library. It isn't enough to delete the component from the Stage. If you don't
remove it from the library, it will be included in your application when you
compile it.

1.  In the Library panel, select the symbol for the component.

2.  Click the Delete button at the bottom of the Library panel, or select Delete
    from the Library panel menu.

    Repeat these steps to delete any assets associated with the component.

    For information on how to remove a component from its container while your
    application is running, see
    [Remove a component from the display list](../working-with-components/work-with-the-display-list.md#remove-a-component-from-the-display-list).
