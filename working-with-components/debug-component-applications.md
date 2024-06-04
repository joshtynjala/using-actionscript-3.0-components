# Debug component applications

The ActionScript 3.0 components contain all their source code to reduce
compilation time when you compile your application. The Flash debugger, however,
cannot inspect code inside compiled clips. Therefore, if you want to debug your
application down into the components' source code, you must add the component
source files to your Classpath setting.

The location of the component package folders is relative to the location of the
source files for the component type. To reference all of the ActionScript 3.0
source files for all UI components, add the following location to your Classpath
for the User Interface packages:

- \$(AppConfig)/Component Source/ActionScript 3.0/User Interface

Note: This will override the compiled-in code for all UI components and increase
compilation time for your application. If you have changed a component's source
file for any reason, that component might exhibit different behavior as a
result.

To set the Classpath, select Preferences from the Edit menu and then select
ActionScript from the Category list and click the ActionScript 3.0 Settings
button. To add a new entry, click the plus above the window that displays the
current settings.

The `$(AppConfig)` variable refers to the Flash CS5 Configuration folder in the
location where you installed Flash CS5. Typically, the path looks like this:

- Windows: C:\Program Files\Adobe\Adobe Flash CS5\language\Configuration\\

- Mac OS X: Macintosh HD:Applications:Adobe Flash CS5:Configuration

Note: If you must change a component source file, Adobe strongly recommends that
you copy the original source file to a different location and add that location
to your Classpath.

For more information about the location of component source files, see
[Where component source files are stored](./working-with-component-files.md#where-component-source-files-are-stored).
