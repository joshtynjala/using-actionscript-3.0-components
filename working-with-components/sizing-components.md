# Sizing components

Use the Free Transform tool or the `setSize()` method to resize component
instances. You can call the `setSize()` method from any component instance (see
`UIComponent.setSize()`) to resize it. The following code resizes an instance of
the List component to 200 pixels wide and 300 pixels high:

    aList.setSize(200, 300);

A component does not resize automatically to fit its label. If a component
instance that has been added to a document is not large enough to display its
label, the label text is clipped. You must resize the component to fit its
label.

For more information about sizing components, see their individual entries in
the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
