# Use the TileList component

The TileList component consists of a list that is made up of rows and columns
that are supplied with data by a data provider. An _item_ refers to a unit of
data that is stored in a cell in the TileList. An item, which originates in the
data provider, typically has a `label` property and a `source` property. The
`label` property identifies the content to display in a cell and the `source`
provides a value for it.

You can create an Array instance or retrieve one from a server. The TileList
component has methods that proxy to its data provider, for example, the
`addItem()` and `removeItem()` methods. If no external data provider is provided
to the list, these methods create a data provider instance automatically, which
is exposed through `List.dataProvider`.

## User interaction with the TileList component

A TileList renders each cell using a Sprite that implements the ICellRenderer
interface. You can specify this renderer with the TileList `cellRenderer`
property. The TileList component's default CellRenderer is the ImageCell, which
displays an image (class, bitmap, instance, or URL), and an optional label. The
label is a single line that always aligns to the bottom of the cell. You can
scroll a TileList in only one direction.

When a TileList instance has focus, you can also use the following keys to
access the items within it:

| Key                        | Description                                                                                                                                                                                        |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Up Arrow and Down Arrow    | Allow you to move up and down through a column. If the `allowMultipleSelection` property is `true`, you can use these keys in combination with the Shift key to select multiple cells.             |
| Left Arrow and Right Arrow | Allow you to move to the left or right in a row. If the `allowMultipleSelection` property is `true`, you can use these keys in combination with the Shift key to select multiple cells.            |
| Home                       | Selects the first cell in a TileList. If the `allowMultipleSelection` property is `true`, holding Shift and pressing Home will select all the cells from your current selection to the first cell. |
| End                        | Selects the last cell in a TileList. If the `allowMultipleSelection` property is `true`, holding Shift and pressing End will select all the cells from your current selection to the last cell.    |
| Ctrl                       | If the `allowMultipleSelection` property is set to `true`, allows you to select multiple cells, in no specific order.                                                                              |

When you add the TileList component to an application, you can make it
accessible to a screen reader by adding the following lines of ActionScript
code:.

    import fl.accessibility.TileListAccImpl;

    TileListAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances the component has. For more information, see Chapter 18, "Creating
Accessible Content," in _Using Flash_.

## TileList component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each TileList component instance:
`allowMultipleSelection`, `columnCount`, `columnWidth`, `dataProvider`,
`direction`, `horizontalScrollLineSize`, `horizontalScrollPageSize`, `labels`,
`rowCount`, `rowHeight`,
`ScrollPolicy, verticalScrollLineSize, and verticalScrollPageSize`. Each of
these parameters has a corresponding ActionScript property of the same name. For
information on using the dataProvider parameter, see
[Use the dataProvider parameter](../working-with-components/work-with-a-dataprovider.md#use-the-dataprovider-parameter).

You can write ActionScript to set additional options for TileList instances
using its methods, properties, and events. For more information, see the
TileList class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the TileList component

This example uses MovieClips to fill a TileList with an array of paint colors.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a TileList component to the Stage and give it an instance name of
    **aTl**.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.data.DataProvider;
        import flash.display.DisplayObject;

        var aBoxes:Array = new Array();
        var i:uint = 0;
        var colors:Array = new Array(0x00000, 0xFF0000, 0x0000CC, 0x00CC00, 0xFFFF00);
        var colorNames:Array = new Array("Midnight", "Cranberry", "Sky", "Forest", "July");
        var dp:DataProvider = new DataProvider();
        for(i=0; i < colors.length; i++) {
            aBoxes[i] = new MovieClip();
            drawBox(aBoxes[i], colors[i]);    // draw box w next color in array
            dp.addItem( {label:colorNames[i], source:aBoxes[i]} );
        }
        aTl.dataProvider = dp;
        aTl.columnWidth = 110;
        aTl.rowHeight = 130;
        aTl.setSize(280,150);
        aTl.move(150, 150);
        aTl.setStyle("contentPadding", 5);

        function drawBox(box:MovieClip,color:uint):void {
            box.graphics.beginFill(color, 1.0);
            box.graphics.drawRect(0, 0, 100, 100);
            box.graphics.endFill();
        }

4.  Select Control \> Test Movie to test the application.

### Create a TileList component using ActionScript

This example dynamically creates a TileList instance and adds instances of the
ColorPicker, ComboBox, NumericStepper, and CheckBox components to it. It creates
an Array that contains labels and the names of the component to display and
assigns the Array ( `dp`) to the TileList's `dataProvider` property. It uses the
`columnWidth` and `rowHeight` properties and the `setSize()` method to lay out
the TileList, the `move()` method to position it on the Stage, and the
`contentPadding` style to put space between the TileList instance's borders and
its content, and the `sortItemsOn()` method to sort the content by its labels.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the following components from the Components panel to the Library
    panel: ColorPicker, ComboBox, NumericStepper, CheckBox, and TileList.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.CheckBox;
        import fl.controls.ColorPicker;
        import fl.controls.ComboBox;
        import fl.controls.NumericStepper;
        import fl.controls.TileList;
        import fl.data.DataProvider;

        var aCp:ColorPicker = new ColorPicker();
        var aCb:ComboBox = new ComboBox();
        var aNs:NumericStepper = new NumericStepper();
        var aCh:CheckBox = new CheckBox();
        var aTl:TileList = new TileList();

        var dp:Array = [
            {label:"ColorPicker", source:aCp},
            {label:"ComboBox", source:aCb},
            {label:"NumericStepper", source:aNs},
            {label:"CheckBox", source:aCh},
        ];
        aTl.dataProvider = new DataProvider(dp);
        aTl.columnWidth = 110;
        aTl.rowHeight = 100;
        aTl.setSize(280,130);
        aTl.move(150, 150);
        aTl.setStyle("contentPadding", 5);
        aTl.sortItemsOn("label");
        addChild(aTl);

4.  Select Test \> Control Movie to test the application.
