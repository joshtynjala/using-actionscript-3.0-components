# Benefits of using components

Components enable you to separate the process of designing your application from
the process of coding. They allow developers to create functionality that
designers can use in applications. Developers can encapsulate frequently used
functionality into components and designers can customize the size, location,
and behavior of components by changing their parameters. They can also change
the appearance of a component by editing its graphical elements, or skins.

Components share core functionality such as styles, skins, and focus management.
When you add the first component to an application, this core functionality
accounts for approximately 20 kilobytes of the size. When you add other
components, that initial memory allocation is shared by the added components,
reducing the growth in the size of your application.

This section outlines some of the benefits of the ActionScript 3.0 components.

The power of ActionScript 3.0  
provides a powerful, object-oriented programming language that is an important
step in the evolution of Flash Player capabilities. The language is designed for
building rich Internet applications on a reusable code base. ActionScript 3.0 is
based on ECMAScript, the international standardized language for scripting, and
is compliant with the ECMAScript (ECMA-262) edition 3 language specification.
For a thorough introduction to ActionScript 3.0, see
_[ActionScript 3.0 Developer's Guide](https://web.archive.org/web/20150414032840/http://help.adobe.com/en_US/as3/dev/index.html)_.
For reference information on the language, see the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

FLA-based User Interface components  
provide easy access to skins for easy customizing while authoring. These
components also provide styles, including skin styles, that allow you to
customize aspects of the components appearance and load skins at run time. For
more information, see
[Customizing the UI Components](../customizing-the-ui-components/index.md) and
the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).

New FVLPlayback component adds FLVPlaybackCaptioning  
component along with full screen support, improved live preview, skins that
allow you to add color and alpha settings, and improved FLV download and layout
features.

The Property inspector and Component inspector  
allow you to change component parameters while authoring in Flash. For more
information, see
[Working with component files](../working-with-components/index.md) and
[Set parameters and properties](../working-with-components/set-parameters-and-properties.md).

New collection dialog box  
for the ComboBox, List, and TileList components allows you to populate their
`dataProvider` property through the user interface. For more information, see
[Create a DataProvider](../working-with-components/work-with-a-dataprovider.md#create-a-dataprovider).

The ActionScript 3.0 event model  
allows your application to listen for events and invoke event handlers to
respond. For more information, see
[ActionScript 3.0 event handling model](./actionscript-3.0-event-handling-model.md)
and [Handling events](../working-with-components/handling-events.md).

Manager classes  
provide an easy way to handle focus and manage styles in an application. For
more information, see the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).

The UIComponent base class  
provides core methods, properties, and events to components that extend it. All
of the ActionScript 3.0 user interface components inherit from the UIComponent
class. For more information see the UIComponent class in the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).

Use of a SWC  
in the UI FLA-based components provide ActionScript definitions as an asset
inside the component's Timeline to speed compilation.

An easily extendable class hierarchy  
using ActionScript 3.0 allows you to create unique namespaces, import classes as
needed, and subclass easily to extend components.

For more information, see the
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html).

Note: Flash CS5 supports both FLA-based and SWC-based components. For more
information, see
[Component architecture](../working-with-components/component-architecture.md).
