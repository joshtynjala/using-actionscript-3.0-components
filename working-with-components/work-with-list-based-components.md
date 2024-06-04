# Work with List-based components

The List, DataGrid, and TileList components all inherit from the SelectableList
base class. For this reason, these components are considered List-based
components. A ComboBox consists of a text box and a List so it, too, is a
List-based component.

A List is composed of rows. A DataGrid and a TileList are composed of rows that
can be divided into multiple columns. The intersection of a row and a column is
a cell. In a List, which is a single column of rows, each row is a cell. A cell
has the following two important aspects:

- The data values that cells hold are called items. An _item_ is an ActionScript
  object used for storing the units of information in a List. A List can be
  thought of as an array with each indexed space of the array being an item. In
  a List, an item is an object that typically has a `label` property that is
  displayed and a `data` property that is used for storing data. A _data
  provider_ is a data model of the items in a List. A data provider allows you
  to populate a List-based component simply by assigning it to the component's
  `dataProvider` property.

- A cell can hold different types of data that range from text to images,
  MovieClips, or any class that you can create. For this reason, a cell must be
  drawn or rendered in a way that is appropriate for its content. Consequently,
  List-based components have a _cell renderer_ to render its cells. In the case
  of the DataGrid, each column is a DataGridColumn object, which also has a
  `cellRenderer` property, so that each column can be rendered appropriately for
  its content.

  All List-based components have `cellRenderer` and `dataProvider` properties
  that you can set to load and render the cells of these components. For
  information on using these properties and working with List-based components,
  see
  [Work with a DataProvider](../working-with-components/work-with-a-dataprovider.md)
  and
  [Work with a CellRenderer](../working-with-components/work-with-a-cell-renderer.md).
