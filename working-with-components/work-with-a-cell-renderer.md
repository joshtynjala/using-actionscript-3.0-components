# Work with a CellRenderer

CellRenderer is a class that List-based components, such as List, DataGrid,
TileList, and ComboBox, use to manipulate and display custom cell content for
their rows. A customized cell can contain text, a prebuilt component, such as a
CheckBox, or any display object class you can create. To render data using a
custom CellRenderer, you can either extend the CellRenderer class or implement
the ICellRenderer interface to create your own custom CellRenderer class.

The List, DataGrid, TileList, and ComboBox classes are subclasses of the
SelectableList class. The SelectableList class includes a `cellRenderer` style.
This style defines the display object that the component uses to render cells.

You can adjust the formatting of the styles used by the CellRenderer, by calling
the `setRendererStyle()` method of the List object (see
[Format cells](#format-cells)). Or you can define a custom class to use as the
CellRenderer (see
[Define a custom CellRenderer class](#define-a-custom-cellrenderer-class)).

## Format cells

The CellRenderer class includes a number of styles that let you control the
format of the cell.

The following styles let you define the skins used for the different states of
the cell (disabled, down, over, and up):

- `disabledSkin` and `selectedDisabledSkin`

- `downSkin` and `selectedDownSkin`

- `overSkin` and `selectedOverSkin`

- `upSkin` and `selectedUpSkin`

  The following styles apply to the text formatting:

- `disabledTextFormat`

- `textFormat`

- `textPadding`

You can set these styles by calling the `setRendererStyle()` method of the List
object or by calling the `setStyle()` method of the CellRenderer object. You can
get these styles by calling the `getRendererStyle()` method of the List object
or by calling the `getStyle()` method of the CellRenderer object. You can also
access an object that defines all renderer styles (as named properties of the
object) via the `rendererStyles` property of the List object or the
`getStyleDefinition()` method of the CellRenderer object.

You can call the `clearRendererStyle()` method to reset a style to its default
value.

To get or set the height of the rows in the list, use the `rowHeight` property
of the List object.

## Define a custom CellRenderer class

### Create a class that extends the CellRenderer class to define a custom CellRenderer

For example, the following code includes two classes. The ListSample class
instantiates a List component, and it uses the other class, CustomRenderer, to
define the cell renderer to use for the List component. The CustomRenderer class
extends the CellRenderer class.

1.  Select File \> New.

2.  In the New Document dialog box that is displayed, select Flash File
    (ActionScript 3.0), and then click OK.

3.  Select Window \> Components to display the Components panel.

4.  In the Components panel, drag a List component to the Stage.

5.  If Flash is not displaying the Property inspector, select Window \>
    Properties \> Properties.

6.  With the List component selected, set the properties in the Property
    inspector:

    - Instance Name: myList

    - W (width): 200

    - H (height): 300

    - X: 20

    - Y: 20

7.  Select Frame 1 of Layer 1 in the Timeline, and select Window \> Actions.

8.  Type the following script in the Actions panel:

        myList.setStyle("cellRenderer", CustomCellRenderer);
        myList.addItem({label:"Burger -- $5.95"});
        myList.addItem({label:"Fries -- $1.95"});

9.  Select File \> Save. Give the file a name and click the OK button.

10. Select File \> New.

11. In the New Document dialog box that is displayed, select ActionScript File
    and then click the OK button.

12. In the script window, enter the following code to define the
    CustomCellRenderer class:

        package {
            import fl.controls.listClasses.CellRenderer;
            import flash.text.TextFormat;
            import flash.filters.BevelFilter;
            public class CustomCellRenderer extends CellRenderer {
                public function CustomCellRenderer() {
                    var format:TextFormat = new TextFormat("Verdana", 12);
                    setStyle("textFormat", format);
                    this.filters = [new BevelFilter()];
                }
            }
        }

13. Select File \> Save. Name the file CustomCellRenderer.as, put it in the same
    directory as the FLA file, and click the OK button.

14. Select Control \> Test Movie.

### Use a class that implements the ICellRenderer interface to define a custom CellRenderer

You can also define a CellRenderer using any class that inherits the
DisplayObject class and implements the ICellRenderer interface. For example the
following code defines two classes. The ListSample2 class adds a List object to
the display list and defines its CellRenderer to use the CustomRenderer class.
The CustomRenderer class extends the CheckBox class (which extends the
DisplayObject class) and implements the ICellRenderer interface. Note that the
CustomRenderer class defines getter and setter methods for the `data` and
`listData` properties, defined in the ICellRenderer interface. Other properties
and methods defined in the ICellRenderer interface (the `selected` property and
the `setSize()` method) are already defined in the CheckBox class:

1.  Select File \> New.

2.  In the New Document dialog box that is displayed, select Flash File
    (ActionScript 3.0), and then click OK.

3.  Select Window \> Components to display the Components panel.

4.  In the Components panel, drag a List component to the Stage.

5.  If Flash is not displaying the Property inspector, select Window \>
    Properties \> Properties.

6.  With the List component selected, set the properties in the Property
    inspector:

    - Instance Name: myList

    - W (width): 100

    - H (height): 300

    - X: 20

    - Y: 20

7.  Select Frame 1 of Layer 1 in the Timeline, and select Window \> Actions.

8.  Type the following script in the Actions panel:

        myList.setStyle("cellRenderer", CustomCellRenderer);
        myList.addItem({name:"Burger", price:"$5.95"});
        myList.addItem({name:"Fries", price:"$1.95"});

9.  Select File \> Save. Give the file a name and click the OK button.

10. Select File \> New.

11. In the New Document dialog box that is displayed, select ActionScript File
    and then click the OK button.

12. In the script window, enter the following code to define the
    CustomCellRenderer class:

        package
        {
            import fl.controls.CheckBox;
            import fl.controls.listClasses.ICellRenderer;
            import fl.controls.listClasses.ListData;
            public class CustomCellRenderer extends CheckBox implements ICellRenderer {
                private var _listData:ListData;
                private var _data:Object;
                public function CustomCellRenderer() {
                }
                public function set data(d:Object):void {
                    _data = d;
                    label = d.label;
                }
                public function get data():Object {
                    return _data;
                }
                public function set listData(ld:ListData):void {
                    _listData = ld;
                }
                public function get listData():ListData {
                    return _listData;
                }
            }
        }

13. Select File \> Save. Name the file CustomCellRenderer.as, put it in the same
    directory as the FLA file, and click the OK button.

14. Select Control \> Test Movie.

### Use a symbol to define a CellRenderer

You can also use a symbol in the library to define a CellRenderer. The symbol
must be exported for ActionScript and the class name for the library symbol must
have an associated class file that either implements the ICellRenderer interface
or that extends the CellRenderer class (or one of its subclasses).

The following example defines a custom CellRenderer using a library symbol.

1.  Select File \> New.

2.  In the New Document dialog box that is displayed, select Flash File
    (ActionScript 3.0), and then click OK.

3.  Select Window \> Components to display the Components panel.

4.  In the Components panel, drag a List component to the Stage.

5.  If Flash is not displaying the Property inspector, select Window \>
    Properties \> Properties.

6.  With the List component selected, set the properties in the Property
    inspector:

    - Instance Name: myList

    - W (width): 100

    - H (height): 400

    - X: 20

    - Y: 20

7.  Click the Parameters panel, and then double-click the second column in the
    dataProvider row.

8.  In the Values dialog box that is displayed, click the plus sign twice to add
    two data elements (with labels set to label0 and label1), and then click the
    OK button.

9.  With the Text tool, draw a text field on the Stage.

10. With the text field selected, set the properties in the Property inspector:

    - Text type: Dynamic Text

    - Instance Name: textField

    - W (width): 100

    - Font size: 24

    - X: 0

    - Y: 0

11. With the text field selected, select Modify \> Convert To Symbol.

12. In the Convert To Symbol dialog box, make the following settings and then
    click OK.

    - Name: MyCellRenderer

    - Type: MovieClip

    - Export for ActionScript: Selected

    - Export in First Frame: Selected

    - Class: MyCellRenderer

    - Base Class: flash.display.MovieClip

      If Flash displays an ActionScript Class Warning, click the OK button in
      the warning box.

13. Delete the instance of the new movie clip symbol from the Stage.

14. Select Frame 1 of Layer 1 in the Timeline, and select Window \> Actions.

15. Type the following script in the Actions panel:

        myList.setStyle("cellRenderer", MyCellRenderer);

16. Select File \> Save. Give the file a name and click the OK button.

17. Select File \> New.

18. In the New Document dialog box that is displayed, select ActionScript File
    and then click the OK button.

19. In the script window, enter the following code to define the MyCellRenderer
    class:

        package {
            import flash.display.MovieClip;
            import flash.filters.GlowFilter;
            import flash.text.TextField;
            import fl.controls.listClasses.ICellRenderer;
            import fl.controls.listClasses.ListData;
            import flash.utils.setInterval;
            public class MyCellRenderer extends MovieClip implements ICellRenderer {
                private var _listData:ListData;
                private var _data:Object;
                private var _selected:Boolean;
                private var glowFilter:GlowFilter;
                public function MyCellRenderer() {
                    glowFilter = new GlowFilter(0xFFFF00);
                    setInterval(toggleFilter, 200);
                }
                public function set data(d:Object):void {
                    _data = d;
                    textField.text = d.label;
                }
                public function get data():Object {
                    return _data;
                }
                public function set listData(ld:ListData):void {
                    _listData = ld;
                }
                public function get listData():ListData {
                    return _listData;
                }
                public function set selected(s:Boolean):void {
                    _selected = s;
                }
                public function get selected():Boolean {
                    return _selected;
                }
                public function setSize(width:Number, height:Number):void {
                }
                public function setStyle(style:String, value:Object):void {
                }
                public function setMouseState(state:String):void{
                }
                private function toggleFilter():void {
                    if (textField.filters.length == 0) {
                        textField.filters = [glowFilter];
                    } else {
                        textField.filters = [];
                    }
                }
            }
        }

20. Select File \> Save. Name the file MyCellRenderer.as, put it in the same
    directory as the FLA file, and click the OK button.

21. Select Control \> Test Movie.

## CellRenderer properties

The `data` property is an object that contains all properties that are set for
the CellRenderer. For example, in the following class, which defines a custom
CellRenderer that extends the Checkbox class, note that the setter function for
the `data` property passes the value of `data.label` to the `label` property
that is inherited from the CheckBox class:

        public class CustomRenderer extends CheckBox implements ICellRenderer {
            private var _listData:ListData;
            private var _data:Object;
            public function CustomRenderer() {
            }
            public function set data(d:Object):void {
                _data = d;
                label = d.label;
            }
            public function get data():Object {
                return _data;
            }
            public function set listData(ld:ListData):void {
                _listData = ld;
            }
            public function get listData():ListData {
                return _listData;
            }
        }
    }

The `selected` property defines whether or not a cell is selected in the list.

## Apply a CellRenderer for a column of a DataGrid object

A DataGrid object can have multiple columns and you can specify different cell
renderers for each column. Each column of a DataGrid is represented by a
DataGridColumn object and the DataGridColumn class includes a `cellRenderer`
property, for which you can define the CellRenderer for the column.

## Define a CellRenderer for an editable cell

The DataGridCellEditor class defines a renderer used for editable cells in a
DataGrid object. It becomes the renderer for a cell when the `editable` property
of the DataGrid object is set to `true` and the user clicks the cell to be
edited. To define a CellRenderer for the editable cell, set the `itemEditor`
property for each element of the `columns` array of the DataGrid object.

## Use an image, SWF file, or movie clip as a CellRenderer

The ImageCell class, a subclass of CellRenderer, defines an object used to
render cells in which the main content of the cell is an image, SWF file, or
movie clip. The ImageCell class includes the following styles for defining the
appearance of the cell:

- `imagePadding` —The padding that separates the edge of the cell from the edge
  of the image, in pixels

- `selectedSkin` —The skin that is used to indicate the selected state

- `textOverlayAlpha` —The opacity of the overlay behind the cell label

- `textPadding` —The padding that separates the edge of the cell from the edge
  of the text, in pixels

  The ImageCell class is the default CellRenderer for the TileList class.
