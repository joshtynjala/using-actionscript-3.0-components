# Make components accessible

You can make visual content in your Flash applications accessible to visually
impaired users through a screen reader, which provides an audio description of
the screen's content. For information on how to make your Flash application
accessible to a screen reader, see Chapter 18, "Creating Accessible Content," in
_Using Flash_.

To make an ActionScript 3.0 component accessible to a screen reader, you must
also import its accessibility class and call that class's
`enableAccessibility()` method. You can make the following ActionScript 3.0
components accessible to a screen reader:

| Component   | Accessibility Class  |
| ----------- | -------------------- |
| Button      | `ButtonAccImpl`      |
| CheckBox    | `CheckBoxAccImpl`    |
| ComboBox    | `ComboBoxAccImpl`    |
| List        | `ListAccImpl`        |
| RadioButton | `RadioButtonAccImpl` |
| TileList    | `TileListAccImpl`    |

The component accessibility classes are in the `fl.accessibility` package. To
make a CheckBox accessible to a screen reader, for example, you would add the
following statements to your application:

    import fl.accessibility.CheckBoxAccImpl;

    CheckBoxAccImpl.enableAccessibility();

You enable accessibility for a component only once, regardless of how many
instances you create.

Note: Enabling accessibility marginally increases file size by including the
required classes during compilation.

Most components are also navigable through the keyboard. For more information on
enabling accessible components and navigating with the keyboard, see the User
Interaction sections of
[Using the UI Components](../using-the-ui-components/index.md) and the
accessibility classes in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.
