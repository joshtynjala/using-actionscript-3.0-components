# Use the DataGrid component

The DataGrid component lets you display data in a grid of rows and columns,
drawing the data from an array or an external XML file that you can parse into
an array for the DataProvider. The DataGrid component includes vertical and
horizontal scrolling, event support (including support for editable cells), and
sorting capabilities.

You can resize and customize characteristics such as the font, color, and the
borders of columns in a grid. You can use a custom movie clip as a cell renderer
for any column in a grid. (A cell renderer displays the contents of a cell.) You
can turn off scroll bars and use the DataGrid methods to create a page view
style display. For more information about customization, see the DataGridColumn
class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## User interaction with the DataGrid component

You can use the mouse and the keyboard to interact with a DataGrid component.

If the `sortableColumns` property and the column's `sortable` property are both
`true`, clicking in a column header sorts the data based on the column's values.
You can disable sorting for an individual column by setting its `sortable`
property to `false`.

If the `resizableColumns` property is `true`, you can resize columns by dragging
the column dividers in the header row.

Clicking in an editable cell gives focus to that cell; clicking a noneditable
cell has no effect on focus. An individual cell is editable when both the
`DataGrid.editable` and `DataGridColumn.editable` properties of the cell are
`true`.

For more information, see the DataGrid and DataGridColumn classes in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
_._

When a DataGrid instance has focus either from clicking or tabbing, you can use
the following keys to control it:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Key</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Down Arrow</p></td>
<td><p>When a cell is being edited, the insertion point shifts to the
end of the cell's text. If a cell is not editable, the Down Arrow key
handles selection as the List component does.</p></td>
</tr>
<tr class="even">
<td><p>Up Arrow</p></td>
<td><p>When a cell is being edited, the insertion point shifts to the
beginning of the cell's text. If a cell is not editable, the Up Arrow
key handles selection as the List component does.</p></td>
</tr>
<tr class="odd">
<td><p>Shift+Up/Down Arrow</p></td>
<td><p>If the DataGrid is not editable and
<samp>allowMultipleSelection</samp> is <samp>true</samp>, selects
contiguous rows. Reversing direction with the opposite arrow deselects
selected rows until you pass the starting row, at which point rows in
that direction are selected.</p></td>
</tr>
<tr class="even">
<td><p>Shift+Click</p></td>
<td><p>If <samp>allowMultipleSelection</samp> is <samp>true</samp>,
selects all rows between selected row and current caret position
(highlighted cell).</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+Click</p></td>
<td><p>If <samp>allowMultipleSelection</samp> is <samp>true</samp>,
selects additional rows, which do not need to be contiguous.</p></td>
</tr>
<tr class="even">
<td><p>Right Arrow</p></td>
<td><p>When a cell is being edited, the insertion point shifts one
character to the right. If a cell is not editable, the Right Arrow key
does nothing.</p></td>
</tr>
<tr class="odd">
<td><p>Left Arrow</p></td>
<td><p>When a cell is being edited, the insertion point shifts one
character to the left. If a cell is not editable, the Left Arrow key
does nothing.</p></td>
</tr>
<tr class="even">
<td><p>Home</p></td>
<td><p>Selects the first row in the DataGrid.</p></td>
</tr>
<tr class="odd">
<td><p>End</p></td>
<td><p>Selects the last row in the DataGrid.</p></td>
</tr>
<tr class="even">
<td><p>PageUp</p></td>
<td><p>Selects the first row in a page of the DataGrid. A page consists
of the number of rows that the DataGrid can display without
scrolling.</p></td>
</tr>
<tr class="odd">
<td><p>PageDown</p></td>
<td><p>Selects the last row in a page of the DataGrid. A page consists
of the number of rows that the DataGrid can display without
scrolling.</p></td>
</tr>
<tr class="even">
<td><p>Return/Enter/Shift+Enter</p></td>
<td><p>When a cell is editable, the change is committed, and the
insertion point is moved to the cell on the same column, next row (up or
down, depending on the shift toggle).</p></td>
</tr>
<tr class="odd">
<td><p>Shift+Tab/Tab</p></td>
<td><p>If the DataGrid is editable, moves focus to the previous/next
item until the end of the column is reached and then to the
previous/next row until the first or last cell is reached. If the first
cell is selected, Shift+Tab moves focus to the preceding control. If the
last cell is selected, Tab moves focus to the next control.</p>
<p>If the DataGrid is not editable, moves focus to the previous/next
control.</p></td>
</tr>
</tbody>
</table>

You can use the DataGrid component as the foundation for numerous types of
data-driven applications. You can easily display a formatted tabular view of
data, but you can also use the cell renderer capabilities to build more
sophisticated and editable user interface pieces. The following are practical
uses for the DataGrid component:

- A webmail client

- Search results pages

- Spreadsheet applications such as loan calculators and tax form applications

When you design an application with the DataGrid component, it is helpful to
understand the design of the List component because the DataGrid class extends
the SelectableList class. For more information on the SelectableList class and
the List component, see the SelectableList and List classes in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
_._

When you add a DataGrid component to your application, you can make it
accessible to a screen reader by adding the following lines of ActionScript
code:

    import fl.accessibility.DataGridAccImpl;
    DataGridAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances the component has. For more information, see Chapter 18, "Creating
Accessible Content," in _Using Flash_.

## DataGrid component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each DataGrid component instance:
`allowMultipleSelection`, `editable`, `headerHeight`,
`horizontalLineScrollSize`, `horizontalPageScrollSize`,
`horizontalScrolllPolicy`, `resizableColumns`, `rowHeight`, `showHeaders`,
`verticalLineScrollSize`, `verticalPageScrollSize`, and `verticalScrollPolicy`.
Each of these parameters has a corresponding ActionScript property of the same
name. For information on the possible values for these parameters, see the
DataGrid class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the DataGrid component

To create an application with the DataGrid component, you must first determine
where your data is coming from. Typically, data comes from an Array, which you
can pull into the grid by setting the `dataProvider` property. You can also use
the methods of the DataGrid and DataGridColumn classes to add data to the grid.

#### Use a local data provider with a DataGrid component:

This example creates a DataGrid to display a softball team's roster. It defines
the roster in an Array ( `aRoster`) and assigns it to the DataGrid's
`dataProvider` property.

1.  In Flash, select File \> New, and then select Flash File (ActionScript 3.0).

2.  Drag the DataGrid component from the Components panel to the Stage.

3.  In the Property inspector, enter the instance name **aDg**.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.data.DataProvider;

        bldRosterGrid(aDg);
        var aRoster:Array = new Array();
        aRoster = [
            {Name:"Wilma Carter", Bats:"R", Throws:"R", Year:"So", Home: "Redlands, CA"},
            {Name:"Sue Pennypacker", Bats:"L", Throws:"R", Year:"Fr", Home: "Athens, GA"},
            {Name:"Jill Smithfield", Bats:"R", Throws:"L", Year:"Sr", Home: "Spokane, WA"},
            {Name:"Shirley Goth", Bats:"R", Throws:"R", Year:"Sr", Home: "Carson, NV"},
            {Name:"Jennifer Dunbar", Bats:"R", Throws:"R", Year:"Fr", Home: "Seaside, CA"},
            {Name:"Patty Crawford", Bats:"L", Throws:"L", Year:"Jr", Home: "Whittier, CA"},
            {Name:"Angelina Davis", Bats:"R", Throws:"R", Year:"So", Home: "Odessa, TX"},
            {Name:"Maria Santiago", Bats:"L", Throws:"L", Year:"Sr", Home: "Tacoma, WA"},
            {Name:"Debbie Ferguson", Bats:"R", Throws:"R", Year: "Jr", Home: "Bend, OR"},
            {Name:"Karen Bronson", Bats:"R", Throws:"R", Year: "Sr", Home: "Billings, MO"},
            {Name:"Sylvia Munson", Bats:"R", Throws:"R", Year: "Jr", Home: "Pasadena, CA"},
            {Name:"Carla Gomez", Bats:"R", Throws:"L", Year: "Sr", Home: "Corona, CA"},
            {Name:"Betty Kay", Bats:"R", Throws:"R", Year: "Fr", Home: "Palo Alto, CA"},
        ];
        aDg.dataProvider = new DataProvider(aRoster);
        aDg.rowCount = aDg.length;

        function bldRosterGrid(dg:DataGrid){
            dg.setSize(400, 300);
            dg.columns = ["Name", "Bats", "Throws", "Year", "Home"];
            dg.columns[0].width = 120;
            dg.columns[1].width = 50;
            dg.columns[2].width = 50;
            dg.columns[3].width = 40;
            dg.columns[4].width = 120;
            dg.move(50,50);
        }

    The `bldRosterGrid()` function sets the size of the DataGrid and sets the
    order of the columns and their sizes.

5.  Select Control \> Test Movie.

#### Specify columns and add sorting for a DataGrid component in an application

Notice that you can click any column heading to sort the DataGrid's content in
descending order by that column's values.

The following example uses the `addColumn()` method to add DataGridColumn
instances to a DataGrid. The columns represent player names and their scores.
The example also sets the `sortOptions` property to specify the sort options for
each column: `Array.CASEINSENSITIVE` for the Name column and `Array.NUMERIC` for
the Score column. It sizes the DataGrid appropriately by setting the length to
the number of rows and the width to 200.

1.  In Flash, select File \> New, and then select Flash File (ActionScript 3.0).

2.  Drag the DataGrid component from the Components panel to the Stage.

3.  In the Property inspector, enter the instance name **aDg**.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.dataGridClasses.DataGridColumn;
        import fl.events.DataGridEvent;
        import fl.data.DataProvider;
        // Create columns to enable sorting of data.
        var nameDGC:DataGridColumn = new DataGridColumn("name");
        nameDGC.sortOptions = Array.CASEINSENSITIVE;
        var scoreDGC:DataGridColumn = new DataGridColumn("score");
        scoreDGC.sortOptions = Array.NUMERIC;
        aDg.addColumn(nameDGC);
        aDg.addColumn(scoreDGC);
        var aDP_array:Array = new Array({name:"clark", score:3135}, {name:"Bruce", score:403}, {name:"Peter", score:25})
        aDg.dataProvider = new DataProvider(aDP_array);
        aDg.rowCount = aDg.length;
        aDg.width = 200;

5.  Select Control \> Test Movie.

#### Create a DataGrid component instance using ActionScript

This example creates a DataGrid using ActionScript and populates it with an
Array of player names and scores.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the DataGrid component from the Components panel to the current
    document's Library panel.

    This adds the component to the library but doesn't make it visible in the
    application.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.DataGrid;
        import fl.data.DataProvider;

        var aDg:DataGrid = new DataGrid();
        addChild(aDg);
        aDg.columns = [ "Name", "Score" ];
        aDg.setSize(140, 100);
        aDg.move(10, 40);

    This code creates the DataGrid instance and then sizes and positions the
    grid.

4.  Create an array, add data to the array, and identify the array as the data
    provider for the DataGrid:

        var aDP_array:Array = new Array();
        aDP_array.push({Name:"Clark", Score:3135});
        aDP_array.push({Name:"Bruce", Score:403});
        aDP_array.push({Name:"Peter", Score:25});
        aDg.dataProvider = new DataProvider(aDP_array);
        aDg.rowCount = aDg.length;

5.  Select Control \> Test Movie.

#### Load a DataGrid with an XML file

The following example uses the DataGridColumn class to create the DataGrid's
columns. It populates the DataGrid by passing an XML object as the `value`
parameter of the `DataProvider()` constructor.

1.  Using a text editor create an XML file with the following data and save it
    as `team.xml` in the same folder where you will save the FLA file.

        <team>
        <player name="Player A" avg="0.293" />
        <player name="Player B" avg="0.214" />
        <player name="Player C" avg="0.317" />
        </team>

2.  Create a new Flash (ActionScript 3.0) document.

3.  In the Components panel, double-click the DataGrid component to add it to
    the Stage.

4.  In the Property inspector, enter the instance name **aDg**.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.dataGridClasses.DataGridColumn;
        import fl.data.DataProvider;
        import flash.net.*;
        import flash.events.*;

        var request:URLRequest = new URLRequest("team.xml");
        var loader:URLLoader = new URLLoader;


        loader.load(request);
        loader.addEventListener(Event.COMPLETE, loaderCompleteHandler);

        function loaderCompleteHandler(event:Event):void {

            var teamXML:XML = new XML(loader.data);

            var nameCol:DataGridColumn = new DataGridColumn("name");
            nameCol.headerText = "Name";
            nameCol.width = 120;
            var avgCol:DataGridColumn = new DataGridColumn("avg");
            avgCol.headerText = "Average";
            avgCol.width = 60;

            var myDP:DataProvider = new DataProvider(teamXML);

            aDg.columns = [nameCol, avgCol];
            aDg.width = 200;
            aDg.dataProvider = myDP;
            aDg.rowCount = aDg.length;
        }

6.  Select Control \> Test Movie.

More Help topics

[Creating, populating, and resizing the DataGrid component](https://web.archive.org/web/20111113074757/http://www.adobe.com/devnet/flash/quickstart/datagrid_pt1.html)

[Customizing and sorting the DataGrid component](https://web.archive.org/web/20111113074802/http://www.adobe.com/devnet/flash/quickstart/datagrid_pt2.html)

[Filtering and formatting data in the DataGrid component](https://web.archive.org/web/20111113074819/http://www.adobe.com/devnet/flash/quickstart/datagrid_pt3.html)
