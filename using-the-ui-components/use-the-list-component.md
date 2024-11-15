# Use the List component

The List component is a scrollable single- or multiple-selection list box. A
list can also display graphics, including other components. You add the items
displayed in the list by using the Values dialog box that appears when you click
in the labels or data parameter fields. You can also use the `List.addItem()`
and `List.addItemAt()` methods to add items to the list.

The List component uses a zero-based index, where the item with index 0 is the
top item displayed. When adding, removing, or replacing list items using the
List class methods and properties, you may need to specify the index of the list
item.

## User interaction with the List component

You can set up a list so that users can make either single or multiple
selections. For example, a user visiting an e-commerce website needs to select
which item to buy. There are 30 items in a list that the user scrolls through
and selects an item by clicking it.

You can also design a List that uses custom movie clips as rows so you can
display more information to the user. For example, in an e-mail application,
each mailbox could be a List component and each row could have icons to indicate
priority and status.

The List receives focus when you click it or tab to it, and you can then use the
following keys to control it:

| Key               | Description                                                                          |
| ----------------- | ------------------------------------------------------------------------------------ |
| Alphanumeric keys | Jump to the next item that has `Key.getAscii()` as the first character in its label. |
| Control           | Toggle key that allows multiple noncontiguous selections and deselections.           |
| Down Arrow        | Selection moves down one item.                                                       |
| Home              | Selection moves to the top of the list.                                              |
| Page Down         | Selection moves down one page.                                                       |
| Page Up           | Selection moves up one page.                                                         |
| Shift             | Allows for contiguous selection.                                                     |
| Up Arrow          | Selection moves up one item.                                                         |

> **Note:** Note that scroll sizes are in pixels and not rows.

> **Note:** The page size used by the Page Up and Page Down keys is one less
> than the number of items that fit in the display. For example, paging down
> through a ten-line drop-down list shows items 0-9, 9-18, 18-27, and so on,
> with one item overlapping per page.

For more information about controlling focus, see the IFocusManager interface
and the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html),_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

A live preview of each List instance on the Stage reflects changes made to
parameters in the Property inspector or Component inspector during authoring.

When you add the List component to an application, you can make it accessible to
a screen reader by adding the following lines of ActionScript code:

    import fl.accessibility.ListAccImpl;

    ListAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances the component has. For more information, see Chapter 18, "Creating
Accessible Content," in _Using Flash_.

## List component parameters

You can set the following parameters in the Property inspector or in the
Component inspector for each List component instance: `allowMultipleSelection`,
`dataProvider, horizontalLineScrollSize, horizontalPageScrollSize, horizontalScrollPolicy, multipleSelection, verticalLineScrollSize, verticalPageScrollSize`,
and `verticalScrollPolicy`. Each of these parameters has a corresponding
ActionScript property of the same name. For information on the possible values
for these parameters, see the List class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
For information on using the dataProvider parameter, see
[Use the dataProvider parameter](../working-with-components/work-with-a-dataprovider.md#use-the-dataprovider-parameter).

## Create an application with the List component

The following examples describe how to add a List component to an application
while authoring.

#### Add a simple List component to an application

In this example, the List consists of labels that identify car models and data
fields that contain prices.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a List component from the Components panel to the Stage.

3.  In the Property inspector, do the following:

    - Enter the instance name **aList**.

    - Assign a value of **200** to the W (width).

4.  Use the Text tool to create a text field below `aList` and give it an
    instance name of **aTf** `.`

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.List;
        import flash.text.TextField;

        aTf.type = TextFieldType.DYNAMIC;
        aTf.border = false;

        // Create these items in the Property inspector when data and label
        // parameters are available.
        aList.addItem({label:"1956 Chevy (Cherry Red)", data:35000});
        aList.addItem({label:"1966 Mustang (Classic)", data:27000});
        aList.addItem({label:"1976 Volvo (Xcllnt Cond)", data:17000});
        aList.allowMultipleSelection = true;

        aList.addEventListener(Event.CHANGE, showData);

        function showData(event:Event) {
            aTf.text = "This car is priced at: $" + event.target.selectedItem.data;
        }

    This code uses the `addItem()` method to populate `aList` with three items,
    assigning each one a `label` value, which appears in the list, and a `data`
    value. When you select an item in the List, the event listener calls the
    `showData()` function, which displays the `data` value for the selected
    item.

6.  Select Control \> Test Movie to compile and run this application.

#### Populate a List instance with a data provider

This example creates a List of car models and their prices. It uses a data
provider to populate the List, however, rather than the `addItem()` method.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a List component from the Components panel to the Stage.

3.  In the Property inspector, do the following:

    - Enter the instance name **aList**.

    - Assign a value of **200** to the W (width).

4.  Use the Text tool to create a text field below `aList` and give it an
    instance name of **aTf** `.`

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.List;
        import fl.data.DataProvider;
        import flash.text.TextField;

        aTf.type = TextFieldType.DYNAMIC;
        aTf.border = false;

        var cars:Array = [
            {label:"1956 Chevy (Cherry Red)", data:35000},
            {label:"1966 Mustang (Classic)", data:27000},
            {label:"1976 Volvo (Xcllnt Cond)", data:17000},
        ];
        aList.dataProvider = new DataProvider(cars);
        aList.allowMultipleSelection = true;

        aList.addEventListener(Event.CHANGE, showData);

        function showData(event:Event) {
            aTf.text = "This car is priced at: $" + event.target.selectedItem.data;
        }

6.  Select Control \> Test Movie to see the List with its items.

#### Use a List component to control a MovieClip instance

The following example creates a List of color names and when you select one, it
applies the color to a MovieClip.

1.  Create a Flash (ActionScript 3.0) document.

2.  Drag the List component from the Components panel to the Stage and give it
    the following values in the Property inspector:

    - Enter **aList** for the instance name.

    - Enter **60** for the H value.

    - Enter **100** for the X value.

    - Enter **150** for the Y value.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        aList.addItem({label:"Blue", data:0x0000CC});
        aList.addItem({label:"Green", data:0x00CC00});
        aList.addItem({label:"Yellow", data:0xFFFF00});
        aList.addItem({label:"Orange", data:0xFF6600});
        aList.addItem({label:"Black", data:0x000000});

        var aBox:MovieClip = new MovieClip();
        addChild(aBox);

        aList.addEventListener(Event.CHANGE, changeHandler);
        function changeHandler(event:Event) {
            drawBox(aBox, event.target.selectedItem.data);
        }

        function drawBox(box:MovieClip,color:uint):void {
            box.graphics.beginFill(color, 1.0);
            box.graphics.drawRect(225, 150, 100, 100);
            box.graphics.endFill();
        }

4.  Select Control \> Test Movie to run the application.

5.  Click colors in the List to see them displayed in a MovieClip.

#### Create a List component instance using ActionScript:

This example creates a simple list using ActionScript, and populates it using
the `addItem()` method.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the List component from the Components panel to the Library panel.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.List;

        var aList:List = new List();
        aList.addItem({label:"One", data:1});
        aList.addItem({label:"Two", data:2});
        aList.addItem({label:"Three", data:3});
        aList.addItem({label:"Four", data:4});
        aList.addItem({label:"Five", data:5});
        aList.setSize(60, 40);
        aList.move(200,200);
        addChild(aList);

        aList.addEventListener(Event.CHANGE, changeHandler);
        function changeHandler(event:Event):void {
            trace(event.target.selectedItem.data);
        }

4.  Select Control \> Test Movie to run the application.
