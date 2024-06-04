# A simple application

This section takes you through the steps to create a simple ActionScript 3.0
application using Flash components and the Flash authoring tool. The example is
provided both as a FLA file with the ActionScript code included on the Timeline
and also as an external ActionScript class file with a FLA file that contains
only the components in the library. In general, you will want to develop larger
application using external class files so that you can share code between
classes and applications and to make your applications easier to maintain. For
more information on programming with ActionScript 3.0, see _Programming
ActionScript 3.0_.

## Design of the application

Our first example of an ActionScript component application is a variation of the
standard "Hello World" application, so its design is fairly simple:

- The application will be called Greetings.

- It uses a TextArea to display a greeting that is initially Hello World.

- It uses a ColorPicker that allows you to change the color of the text.

- It uses three RadioButtons that allow you to set the size of the text to
  small, larger or largest.

- It uses a ComboBox that allows you to select a different greeting from a
  drop-down list.

- The application uses components from the Components panel and also creates
  application elements through ActionScript code.

  With that definition in place, you can start building the application.

## Create the Greetings application

The following steps create the Greetings application using the Flash authoring
tool to create a FLA file, place components on the Stage, and add ActionScript
code to the Timeline.

#### Create the Greetings application in a FLA file:

1.  Select File \> New.

2.  In the New Document dialog box, select Flash File (ActionScript 3.0), and
    click OK.

    A new Flash window opens.

3.  Select File \> Save, name the Flash file **Greetings.fla**, and click the
    Save button.

4.  In the Flash Components panel, select a TextArea component and drag it to
    the Stage.

5.  In the Properties window, with the TextArea selected on the Stage, type
    **aTa** for the instance name, and enter the following information:

    - Enter **230** for the W value (width).

    - Enter **44** for the H value (height).

    - Enter **165** for the X value (horizontal position).

    - Enter **57** for the Y value (vertical position).

    - Enter **Hello World!** for the text parameter, on the Parameters tab.

6.  Drag a ColorPicker component to the Stage, place it to the left of the
    TextArea and give it an instance name of **txtCp.** Enter the following
    information in the Property inspector:

    - Enter **96** for the X value.

    - Enter **72** for the Y value.

7.  Drag three RadioButton components to the Stage, one at a time and give them
    instance names of **smallRb**, **largerRb**, and **largestRb**. Enter the
    following information for them in the Property inspector:

    - Enter **100** for the W value and **22** for the H value for each of them.

    - Enter **155** for the X value.

    - Enter **120** for the Y value for smallRb, **148** for largerRb, and
      **175** for largestRb.

    - Enter **fontRbGrp** for the groupName parameter for each of them.

    - Enter labels for them on the Parameters tab of **Small**, **Larger**,
      **Largest**.

8.  Drag a ComboBox to the Stage and give it an instance name of **msgCb**.
    Enter the following information for it in the Property inspector:

    - Enter **130** for the W value.

    - Enter **265** for the X value.

    - Enter **120** for the Y value.

    - On the Parameters tab, enter **Greetings** for the prompt parameter.

    - Double-click the text field for the dataProvider parameter to open the
      Values dialog box.

    - Click the plus sign and replace the label value with **Hello World!**

    - Repeat the preceding step to add the label values **Have a nice day!** and
      **Top of the Morning!**

    - Click OK to close the Values dialog box.

9.  Save the file.

10. If it is not already open, open the Actions panel by hitting **F9** or
    selecting Actions from the Window menu. Click Frame 1 on the main Timeline
    and enter the following code in the Actions panel:

        import flash.events.Event;
        import fl.events.ComponentEvent;
        import fl.events.ColorPickerEvent;
        import fl.controls.RadioButtonGroup;

        var rbGrp:RadioButtonGroup = RadioButtonGroup.getGroup("fontRbGrp");
        rbGrp.addEventListener(MouseEvent.CLICK, rbHandler);
        txtCp.addEventListener(ColorPickerEvent.CHANGE,cpHandler);
        msgCb.addEventListener(Event.CHANGE, cbHandler);

    The first three lines import the event classes that the application uses. An
    event occurs when a user interacts with one of the components. The next five
    lines register event handlers for the events that the application wants to
    listen for. A `click` event occurs for a RadioButton when a user clicks on
    it. A `change` event occurs when a user selects a different color in the
    ColorPicker. A `change` event occurs on the ComboBox when a user chooses a
    different greeting from the drop-down list.

    The fourth line imports the RadioButtonGroup class so that the application
    can assign an event listener to the group of RadioButtons, rather than
    assigning the listener to each button individually.

11. Add the following line of code to the Actions panel to create the `tf`
    TextFormat object, which the application uses to change the `size` and
    `color` style properties of the text in the TextArea.

        var tf:TextFormat = new TextFormat();

12. Add the following code to create the `rbHandler` event handling function.
    This function handles a `click` event when a user clicks on one of the
    RadioButton components.

        function rbHandler(event:MouseEvent):void {
        switch(event.target.selection.name) {
            case "smallRb":
                tf.size = 14;
                break;
            case "largerRb":
                tf.size = 18;
                break;
            case "largestRb":
                tf.size = 24;
                break;
            }
            aTa.setStyle("textFormat", tf);
        }

    This function uses a `switch` statement to examine the `target` property of
    the `event` object to determine which RadioButton triggered the event. The
    `currentTarget` property contains the name of the object that triggered the
    event. Depending on which RadioButton the user clicked, the application
    changes the size of the text in the TextArea to 14, 18, or 24 points.

13. Add the following code to implement the `cpHandler()` function, which
    handles a change to the value in the ColorPicker:

        function cpHandler(event:ColorPickerEvent):void {
            tf.color = event.target.selectedColor;
            aTa.setStyle("textFormat", tf);
        }

    This function sets the `color` property of the `tf` TextFormat object to the
    color selected in the ColorPicker and then calls `setStyle()` to apply it to
    the text in the `aTa` TextArea instance.

14. Add the following code to implement the `cbHandler()` function, which
    handles a change to the selection in the ComboBox:

        function cbHandler(event:Event):void {
            aTa.text = event.target.selectedItem.label;
        }

    This function simply replaces the text in the TextArea with the selected
    text in the ComboBox, `event.target.selectedItem.label`.

15. Select Control \> Test Movie or press Control+Enter to compile the code and
    test the Greetings application.

    The following section shows you how to build the same application with an
    external ActionScript class and a FLA file that has only the required
    components in the library.

#### Create the Greetings2 application with an external class file:

1.  Select File \> New.

2.  In the New Document dialog box, select Flash File (ActionScript 3.0), and
    click OK.

    A new Flash window opens.

3.  Select File \> Save, name the Flash file **Greetings2.fla**, and click the
    Save button.

4.  Drag each of the following components from the Components panel to the
    library:

    - ColorPicker

    - ComboBox

    - RadioButton

    - TextArea

      The compiled SWF file will use each of these assets, so you need to add
      them to the library. Drag the components to the bottom of the Library
      panel. As you add these components to the library, other assets (such as
      List, TextInput, and UIScrollBox) are added automatically.

5.  In the Properties window, for the Document Class, type **Greetings2**.

    If Flash displays a warning, saying that "a definition for the document
    class could not be found," ignore it. You will define the Greetings2 class
    in the following steps. This class defines the main functionality for the
    application.

6.  Save the Greetings2.fla file.

7.  Select File \> New.

8.  In the New Document dialog box, select ActionScript File, and click OK.

    A new script window opens.

9.  Add the following code into the script window:

        package {
        import flash.display.Sprite;
        import flash.events.Event;
        import flash.events.MouseEvent;
        import flash.text.TextFormat;
        import fl.events.ComponentEvent;
        import fl.events.ColorPickerEvent;
        import fl.controls.ColorPicker;
        import fl.controls.ComboBox;
        import fl.controls.RadioButtonGroup;
        import fl.controls.RadioButton;
        import fl.controls.TextArea;
        public class Greetings2 extends Sprite {
            private var aTa:TextArea;
            private var msgCb:ComboBox;
            private var smallRb:RadioButton;
            private var largerRb:RadioButton;
            private var largestRb:RadioButton;
            private var rbGrp:RadioButtonGroup;
            private var txtCp:ColorPicker;
            private var tf:TextFormat = new TextFormat();
            public function Greetings2() {

    The script defines an ActionScript 3.0 class, named Greetings2. The script
    does the following:

    - It imports classes that we will use in the file. Normally you would add
      these `import` statements as you reference different classes in the code,
      but for the sake of brevity, this example imports them all in this one
      step.

    - It declares variables that represent the different types of component
      objects that we will add to the code. Another variable creates the `tf`
      TextFormat object.

    - It defines a constructor function, `Greetings2()`, for the class. We will
      add lines to this function, and add other methods to the class in the
      following steps.

10. Select File \> Save, name the file **Greetings2.as**, and click the Save
    button.

11. Add the following lines of code to the `Greeting2()` function:

            createUI();
            setUpHandlers();
        }

    The function should now look like the following:

        public function Greetings2() {
            createUI();
            setUpHandlers();
        }

12. Add the following lines of code after the closing brace of the `Greeting2()`
    method:

        private function createUI() {
            bldTxtArea();
            bldColorPicker();
            bldComboBox();
            bldRadioButtons();
        }
        private function bldTxtArea() {
            aTa = new TextArea();
            aTa.setSize(230, 44);
            aTa.text = "Hello World!";
            aTa.move(165, 57);
            addChild(aTa);
        }
        private function bldColorPicker() {
            txtCp = new ColorPicker();
            txtCp.move(96, 72);
            addChild(txtCp);
        }
        private function bldComboBox() {
            msgCb = new ComboBox();
            msgCb.width = 130;
            msgCb.move(265, 120);
            msgCb.prompt = "Greetings";
            msgCb.addItem({data:"Hello.", label:"English"});
            msgCb.addItem({data:"Bonjour.", label:"Français"});
            msgCb.addItem({data:"¡Hola!", label:"Español"});
            addChild(msgCb);
        }
        private function bldRadioButtons() {
            rbGrp = new RadioButtonGroup("fontRbGrp");
            smallRb = new RadioButton();
            smallRb.setSize(100, 22);
            smallRb.move(155, 120);
            smallRb.group = rbGrp; //"fontRbGrp";
            smallRb.label = "Small";
            smallRb.name = "smallRb";
            addChild(smallRb);
            largerRb = new RadioButton();
            largerRb.setSize(100, 22);
            largerRb.move(155, 148);
            largerRb.group = rbGrp;
            largerRb.label = "Larger";
            largerRb.name = "largerRb";
            addChild(largerRb);
            largestRb = new RadioButton();
            largestRb.setSize(100, 22);
            largestRb.move(155, 175);
            largestRb.group = rbGrp;
            largestRb.label = "Largest";
            largestRb.name = "largestRb";
            addChild(largestRb);
        }

    These lines do the following:

    - Instantiate the components used in the application.

    - Set each component's size, position, and properties.

    - Add each component to the Stage, using the `addChild()` method.

13. After the closing brace of the `bldRadioButtons()` method, add the following
    code for the `setUpHandlers()` method:

                private function setUpHandlers():void {
                    rbGrp.addEventListener(MouseEvent.CLICK, rbHandler);
                    txtCp.addEventListener(ColorPickerEvent.CHANGE,cpHandler);
                    msgCb.addEventListener(Event.CHANGE, cbHandler);
                }
                private function rbHandler(event:MouseEvent):void {
                    switch(event.target.selection.name) {
                        case "smallRb":
                            tf.size = 14;
                            break;
                        case "largerRb":
                            tf.size = 18;
                            break;
                        case "largestRb":
                            tf.size = 24;
                            break;
                    }
                    aTa.setStyle("textFormat", tf);
                }
                private function cpHandler(event:ColorPickerEvent):void {
                    tf.color = event.target.selectedColor;
                    aTa.setStyle("textFormat", tf);
                }
                private function cbHandler(event:Event):void {
                    aTa.text = event.target.selectedItem.data;
                }
            }
        }

    These functions define event listeners for the components.

14. Select File \> Save to save the file.

15. Select Control \> Test Movie or press Control+Enter to compile the code and
    test the Greetings2 application.

## Develop and run subsequent examples

Having developed and run the Greetings application, you should have the basic
knowledge you need to run the other code examples presented in this book. The
relevant ActionScript 3.0 code in each example will be highlighted and discussed
and you should be able to cut and paste each of the examples in this book into a
FLA file, compile and run it.
