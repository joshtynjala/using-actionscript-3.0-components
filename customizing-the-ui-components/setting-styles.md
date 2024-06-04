# Setting styles

A component's styles generally specify values for its skins, icons, text
formatting, and padding when Flash draws the component in its various states.
For example, Flash draws a Button with a different skin to show its down state,
which occurs when you click the mouse button on it, than it does to show its up
or normal state. It also uses a different skin when it's in a disabled state,
which is caused by setting the `enabled` property to `false.`

You can set styles for components at the document, class, and instance levels.
In addition, some style properties can be inherited from a parent component. For
example, the List component inherits ScrollBar styles by inheriting from
BaseScrollPane.

You can set styles to customize a component in the following ways:

- Set styles on a component instance. You can change color and text properties
  for a single component instance. This is effective in some situations, but it
  can be time-consuming if you need to set individual properties on all the
  components in a document.

- Set styles for all components of a given type in a document. If you want to
  apply a consistent look to all components of a given type, for example to all
  CheckBoxes or all Buttons in a document, you can set styles at the component
  level.

  The values of style properties set on containers are inherited by contained
  components.

  Flash does not display changes made to style properties when you view
  components on the Stage using the Live Preview feature.

## Understanding style settings

Here are a few key points about using styles:

Inheritance  
A component child is set to inherit a style from the parent component by design.
You cannot set inheritance for styles within ActionScript.

Precedence  
If a component style is set in more than one way, Flash uses the first style it
encounters according to its order of precedence. Flash looks for styles in the
following order until a value is found:

1.  Flash looks for a style property on the component instance.

2.  If the style is one of the inheriting styles, Flash looks through the parent
    hierarchy for an inherited value.

3.  Flash looks for the style on the component.

4.  Flash looks for a global setting on StyleManager.

5.  If the property is still not defined, the property has the value
    `undefined`.

## Accessing a component's default styles

You can access the default styles for a component using the static
`getStyleDefinition()` method for the component class. For example, the
following code retrieves the default styles for the ComboBox component and
displays the default values for the `buttonWidth` and `downArrowDownSkin`
properties:

    import fl.controls.ComboBox;
    var styleObj:Object = ComboBox.getStyleDefinition();
    trace(styleObj.buttonWidth); // 24
    trace(styleObj.downArrowDownSkin); // ScrollArrowDown_downSkin

## Setting and getting styles on a component instance

Any UI component instance can call the `setStyle()` and `getStyle()` methods
directly to set or retrieve a style. The following syntax sets a style and value
for a component instance:

    instanceName.setStyle("styleName", value);

This syntax retrieves a style for a component instance:

    var a_style:Object = new Object();
    a_style = instanceName.getStyle("styleName");

Notice that the `getStyle()` method returns the type Object because it can
return multiple styles having different data types. For example, the following
code sets the font style for a TextArea instance ( `aTa`) and then retrieves it
using the `getStyle()` method. The example casts the returned value to a
TextFormat object to assign it to a TextFormat variable. Without the cast, the
compiler would issue an error for attempting to coerce an Object variable to a
TextFormat variable.

    import flash.text.TextFormat;

    var tf:TextFormat = new TextFormat();
    tf.font = "Georgia";
    aTa.setStyle("textFormat",tf);
    aTa.text = "Hello World!";
    var aStyle:TextFormat = aTa.getStyle("textFormat") as TextFormat;
    trace(aStyle.font);

### Use TextFormat to set text properties

Use the TextFormat object to format text for a component instance. The
TextFormat object has properties that allow you to specify text characteristics
such as `bold`, `bullet`, `color`, `font`, `italic`, `size`, and several others.
You can set these properties in the TextFormat object and then call the
`setStyle()` method to apply them to a component instance. For example, the
following code sets the `font`, `size`, and `bold` properties of a TextFormat
object and applies them to a Button instance:

    /* Create a new TextFormat object to set text formatting properties. */
    var tf:TextFormat = new TextFormat();
    tf.font = "Arial";
    tf.size = 16;
    tf.bold = true;
    a_button.setStyle("textFormat", tf);

The following illustration shows the effect of these settings on a button having
a Submit label:

![Button with new textFormat style applied to its label](../img/cu_submit_bttn.png)

Style properties set on a component instance through `setStyle()` have the
highest priority and override all other style settings. However, the more
properties you set using `setStyle()` on a single component instance, the slower
the component will render at run time.

## Setting a style for all instances of a component

You can set a style for all instances of a component class using the static
`setComponentStyle()` method of the StyleManager class. For example, you can set
the color of text to red for all Buttons by first dragging a Button to the Stage
and then adding the following ActionScript code to the Actions panel on Frame 1
of the Timeline:

    import fl.managers.StyleManager;
    import fl.controls.Button;

    var tf:TextFormat = new TextFormat();
    tf.color = 0xFF0000;
    StyleManager.setComponentStyle(Button, "textFormat", tf);

All Buttons that you subsequently add to the Stage will have red labels.

## Set a style for all components

You can set a style for all component using the static `setStyle()` method of
the StyleManager class.

1.  Drag a List component to the Stage and give it an instance name of **aList**
    .

2.  Drag a Button component to the Stage and give it an instance name of
    **aButton**.

3.  Press **F9** or select Actions from the Window menu to open the Actions
    panel, if it isn't already open, and enter the following code in Frame 1 of
    the Timeline to set the color of text to red for all components:

        import fl.managers.StyleManager;

        var tf:TextFormat = new TextFormat();
        tf.color = 0xFF0000;
        StyleManager.setStyle("textFormat", tf);

4.  Add the following code to the Actions panel to populate the List with text.

        aList.addItem({label:"1956 Chevy (Cherry Red)", data:35000});
        aList.addItem({label:"1966 Mustang (Classic)", data:27000});
        aList.addItem({label:"1976 Volvo (Xcllnt Cond)", data:17000});
        aList.allowMultipleSelection = true;

5.  Select Control \> Test Movie or press Ctrl+Enter to compile the code and
    test your content. The text in both the button label and in the list should
    be red.
