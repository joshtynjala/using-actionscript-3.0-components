# Component architecture

Adobe® ActionScript® 3.0 components are supported by Adobe® Flash Player version
9.0.28.0 and later. These components are not compatible with components built
using ActionScript 2.0. For information on using Adobe® ActionScript® 2.0
components, see _Using Adobe® ActionScript® 2.0 Components_ and the _Adobe®
ActionScript® 2.0 Components Language Reference_.

The Adobe ActionScript 3.0 User Interface (UI) components are implemented as
FLA-based components but Flash CS5 supports both SWC and FLA-based components.
The FLVPlayback and FLVPlaybackCaptioning components are SWC-based components,
for example. You can place either type of component in the Components folder to
have it appear in the Components panel. These two types of components are built
differently so they are described separately here.

## ActionScript 3.0 FLA-based components

The ActionScript 3.0 User Interface components are FLA-based (.fla) files with
built-in skins that you can access for editing by double-clicking the component
on the Stage. The component's skins and other assets are placed on Frame 2 of
the Timeline. When you double-click the component, Flash automatically jumps to
Frame 2 and opens a palette of the component's skins. The following illustration
shows the palette with skins that display for the Button component.

![](../img/wo_button_skins.png)

<caption>Skins for the Button component</caption>

For more information on component skins and customizing components, see
[Customizing the UI Components](../customizing-the-ui-components/index.md) and
[Customize the FLVPlayback component](../using-the-flvplayback-component/customize-the-flvplayback-component/index.md).

To speed up compilation for your applications and to avoid conflicts with your
ActionScript 3.0 settings, the Flash CS5 FLA-based UI components also contain a
SWC that contains the component's already compiled ActionScript code. The
ComponentShim SWC is placed on Stage on Frame 2 in every User Interface
component to make available the precompiled definitions. To be available for
ActionScript, a component must either be on Stage or be in the library with the
Export In First Frame option selected in its Linkage properties. To create a
component using ActionScript, you also must import the class with an `import`
statement to access it. For information on the `import` statement, see the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## SWC-based Components

SWC-based components have a FLA file and an ActionScript class file, too, but
they have been compiled and exported as a SWC. A SWC file is a package of
precompiled Flash symbols and ActionScript code that allows you to avoid
recompiling symbols and code that will not change.

The FLVPlayback and FLVPlaybackCaptioning components are SWC-based components.
They have external rather than built-in skins. The FLVPlayback component has a
default skin that you can change by selecting one from a collection of
predesigned skins, by customizing controls from the UI controls in the
Components panel (BackButton, BufferingBar, and so on), or by creating a custom
skin. For more information, see
[Customize the FLVPlayback component](../using-the-flvplayback-component/customize-the-flvplayback-component/index.md).

In Flash, you can convert a movie clip to a compiled clip as follows:

#### Compile a movie clip

- Right-click (Windows) or Control-click (Macintosh) the movie clip in the
  Library panel, and then select Convert To Compiled Clip.

  The compiled clip behaves just like the movie clip from which it was compiled,
  but compiled clips appear and publish much faster than ordinary movie clips.
  Compiled clips can't be edited, but their properties can appear in the
  Property inspector and the Component inspector.

  SWC components contain a compiled clip, the component's pre-compiled
  ActionScript definitions, and other files that describe the component. If you
  create your own component, you can export it as a SWC file to distribute it.

#### Export a SWC file

- Select the movie clip in the Library panel and right-click (Windows) or
  Control-click (Macintosh), and then select Export SWC File.

  > **Note:** The format of a Flash CS4 or later SWC file is compatible with the
  > Flex SWC format so that SWC files can be exchanged between the two products,
  > but not necessarily without modifications.

For information on creating SWC-based components, see
[ Creating ActionScript 3.0 components in Flash – Part 1: Introducing components](https://web.archive.org/web/20111120120346/http://www.adobe.com/devnet/flash/articles/creating_as3_components.html).

## The ActionScript 3.0 Components API

Each ActionScript 3.0 component is built on an ActionScript 3.0 class that is
located in a package folder and has a name of the format
**fl._packagename_._classname_**. The Button component, for example, is an
instance of the Button class and has a package name of `fl.controls.Button`. You
must reference the package name when you import a component class in your
application. You would import the Button class with the following statement:

    import fl.controls.Button;

For more information about the location of component class files, see
[Working with component files](./working-with-component-files.md).

A component's class defines the methods, properties, events, and styles that
enable you to interact with it in your application. The ActionScript 3.0 UI
components are subclasses of the Sprite and UIComponent classes and inherit
properties, methods, and events from them. The Sprite class is the basic display
list building block and is similar to a MovieClip but does not have a Timeline.
The UIComponent class is the base class for all visual components, both
interactive and non-interactive. The inheritance path of each component, as well
as its properties, methods, events, and styles are described in the _Adobe
[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

All ActionScript 3.0 components use the ActionScript 3.0 event handling model.
For more information on event handling, see
[Handling events](./handling-events.md) and
_[ActionScript 3.0 Developer's Guide](https://web.archive.org/web/20150322151545/http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7fca.html)_.
