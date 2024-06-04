# Use the ComboBox component

A ComboBox component allows a user to make a single selection from a drop-down
list. A ComboBox can be static or editable. An editable ComboBox allows a user
to enter text directly into the text field at the top of the list. If the
drop-down list hits the bottom of the document, it opens up instead of down. The
ComboBox is made up of three subcomponents: the BaseButton, TextInput, and List
components.

In an editable ComboBox, only the button is the hit area—not the text box. For a
static ComboBox, the button and the text box constitute the hit area. The hit
area responds by opening or closing the drop-down list.

When the user makes a selection in the list, either with the mouse or through
the keyboard, the label of the selection is copied to the text field at the top
of the ComboBox.

## User interaction with the ComboBox component

You can use a ComboBox component in any form or application that requires a
single choice from a list. For example, you could provide a drop-down list of
states in a customer address form. You can use an editable ComboBox for more
complex scenarios. For example, in an application that provides driving
directions, you could use an editable ComboBox, to allow a user to enter her
origin and destination addresses. The drop-down list would contain her
previously entered addresses.

If the ComboBox is editable, meaning the `editable` property is `true`, the
following keys remove focus from the text input box and leave the previous
value. The exception is the Enter key, which applies the new value first, if the
user entered text.

| Key         | Description                                                                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Shift + Tab | Moves focus to the previous item. If a new item is selected, a `change` event is dispatched.                                                                   |
| Tab         | Moves focus to the next item. If a new item is selected, a `change` event is dispatched.                                                                       |
| Down Arrow  | Moves the selection down one item.                                                                                                                             |
| End         | Moves the selection to the bottom of the list.                                                                                                                 |
| Escape      | Closes the drop-down list and returns focus to the ComboBox.                                                                                                   |
| Enter       | Closes the drop-down list and returns focus to the ComboBox. When the ComboBox is editable and the user enters text, Enter sets the value to the entered text. |
| Home        | Moves the selection to the top of the list.                                                                                                                    |
| Page Up     | Moves the selection up one page.                                                                                                                               |
| Page Down   | Moves the selection down one page.                                                                                                                             |

When you add the ComboBox component to an application, you can make it
accessible to a screen reader by adding the following lines of ActionScript
code:

    import fl.accessibility.ComboBoxAccImpl;

    ComboBoxAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances you have of the component.

## ComboBox component parameters

You can set the following parameters in the Property inspector or in the
Component inspector for each ComboBox instance: `dataProvider`, `editable`,
`prompt`, and `rowCount`. Each of these parameters has a corresponding
ActionScript property of the same name. For information on the possible values
for these parameters, see the ComboBox class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
For information on using the dataProvider parameter, see
[Use the dataProvider parameter](../working-with-components/work-with-a-dataprovider.md#use-the-dataprovider-parameter).

## Create an application with the ComboBox component

The following procedure describes how to add a ComboBox component to an
application while authoring. The ComboBox is editable and if you type **Add**
into the text field, the example adds an item to the drop-down list.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a ComboBox to the Stage and give it an instance name of **aCb**. On the
    Parameters tab, set the `editable` parameter to `true` **.**

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following code:

        import fl.data.DataProvider;
        import fl.events.ComponentEvent;

        var items:Array = [
            {label:"screen1", data:"screenData1"},
            {label:"screen2", data:"screenData2"},
            {label:"screen3", data:"screenData3"},
            {label:"screen4", data:"screenData4"},
            {label:"screen5", data:"screenData5"},
        ];
        aCb.dataProvider = new DataProvider(items);

        aCb.addEventListener(ComponentEvent.ENTER, onAddItem);

        function onAddItem(event:ComponentEvent):void {
            var newRow:int = 0;
            if (event.target.text == "Add") {
                newRow = event.target.length + 1;
                event.target.addItemAt({label:"screen" + newRow, data:"screenData" + newRow},
                event.target.length);
            }
        }

4.  Select Control \> Test Movie.

### Create a ComboBox using ActionScript

The following example creates a ComboBox with ActionScript and populates it with
a list of universities in the San Francisco, California, area. It sets the
ComboBox's `width` property to accommodate the width of the prompt text and sets
the `dropdownWidth` property to be slightly wider to accommodate the longest
university name.

The example creates the list of universities in an Array instance, using the
`label` property to store the school names and the `data` property to store the
URLs of each school's website. It assigns the Array to the ComboBox by setting
its `dataProvider` property.

When a user selects a university from the list, it triggers an Event. `CHANGE`
event and a call to the `changeHandler()` function, which loads the `data`
property into a URL request to access the school's website.

Notice that the last line sets the ComboBox instance's `selectedIndex` property
to -1 to redisplay the prompt when the list closes. Otherwise, the prompt would
be replaced by the name of the school that was selected.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ComboBox component from the Components panel to the Library panel.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.ComboBox;
        import fl.data.DataProvider;
        import flash.net.navigateToURL;

        var sfUniversities:Array = new Array(
            {label:"University of California, Berkeley",
                        data:"http://www.berkeley.edu/"},
            {label:"University of San Francisco",
                        data:"http://www.usfca.edu/"},
            {label:"San Francisco State University",
                        data:"http://www.sfsu.edu/"},
            {label:"California State University, East Bay",
                        data:"http://www.csuhayward.edu/"},
            {label:"Stanford University", data:"http://www.stanford.edu/"},
            {label:"University of Santa Clara", data:"http://www.scu.edu/"},
            {label:"San Jose State University", data:"http://www.sjsu.edu/"}
        );

        var aCb:ComboBox = new ComboBox();
        aCb.dropdownWidth = 210;
        aCb.width = 200;
        aCb.move(150, 50);
        aCb.prompt = "San Francisco Area Universities";
        aCb.dataProvider = new DataProvider(sfUniversities);
        aCb.addEventListener(Event.CHANGE, changeHandler);

        addChild(aCb);

        function changeHandler(event:Event):void {
            var request:URLRequest = new URLRequest();
            request.url = ComboBox(event.target).selectedItem.data;
            navigateToURL(request);
            aCb.selectedIndex = -1;
        }

4.  Select Control \> Test Movie.

You can implement and run this example in the Flash authoring environment but
you will receive warning messages if you attempt to access the university web
sites by clicking items in the ComboBox. To access the fully functional ComboBox
on the Internet, access the the following location:

<https://web.archive.org/web/20071228061810/http://www.helpexamples.com/peter/bayAreaColleges/bayAreaColleges.html>
