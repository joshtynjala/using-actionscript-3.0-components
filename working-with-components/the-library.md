# The library

When you first add a component to a document, Flash imports it as a movie clip
into the Library panel. You can also drag a component from the Components panel
directly to the Library panel and then add an instance of it to the Stage. In
any case, you must add a component to the library before you can access its
class elements.

If you add a component to the library and create an instance of it using
ActionScript, you must first import its class with the `import` statement. In
the `import` statement, you must specify both the component's package name and
its class name. For example, the following statement imports the Button class:

    import fl.controls.Button;

When you place a component in the library, Flash also imports a folder of its
assets, which contain the skins for its different states. A component's _skins_
comprise the collection of symbols that make up its graphical display in the
application. A single skin is the graphical representation, or movie clip, that
indicates a particular state for the component.

The contents of the Component Assets folder allow you to change the component's
skins if you wish to do that. For more information, see
[Customizing the UI Components](../customizing-the-ui-components/index.md).

Once a component is in the library, you can add more instances of it to your
document by dragging its icon to the Stage from either the Components panel or
the Library panel.
