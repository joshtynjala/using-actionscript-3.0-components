# Working with component files

This section explains where component files are stored, where to find the
ActionScript source files, and how to add and remove components from the
Components panel.

## Where component files are stored

Flash components are stored in the application-level Configuration folder.

> **Note:** For information about these folders, see "Configuration folders
> installed with Flash" in Using Flash.

Components are installed in the following locations:

- Windows:

  C:\Program Files\Adobe\Adobe Flash CS5\\ _language_ \Configuration\Components

- Mac OS X:

  Macintosh HD:Applications:Adobe Flash CS5:Configuration:Components

  Within the Components folder, the User Interface (UI) components are in the
  User Interface.fla file and the FLVPlayback (FLVPlaybackAS3.swc) and
  FLVPlaybackCaptioning components are in the Video folder.

You can also store components in the following user-based locations:

- Windows:

  C:\Documents and Settings\\ _username\\_ Local Settings\Application
  Data\Adobe\Adobe Flash CS5\en\Configuration\Components

- Windows Vista:

  C:\Users\\ _username\\_ Local Settings\Application Data\Adobe\Adobe Flash
  CS5\en\Configuration\Components

- Windows 7:

  C:\Users\\ _username_ \AppData\Local\Adobe\Flash
  CS5\en\Configuration\Components

  > **Note:** In Windows, the Application Data folder (Windows 2000, XP, Vista)
  > and AppData folder (Windows7) is hidden by default. To show hidden folders
  > and files, select My Computer to open Windows Explorer, select Tools \>
  > Folder Options and then select the View tab. Under the View tab, select the
  > Show hidden files and folders radio button.

- Mac OS X:

  Macintosh HD:Users:\<username\>:Library:Application Support:Adobe:Flash
  CS5:Configuration:Components

## Where component source files are stored

The ActionScript (.as) class files (or _source files_) for components are
installed in the following application folders for Windows 2000, XP, Vista, and
7:

User Interface components  
C:\Program Files\Adobe\Adobe Flash CS5\en\Configuration\Component
Source\ActionScript 3.0\User Interface\fl

FLVPlayback  
C:\Program Files\Adobe\Adobe Flash CS5\en\Configuration\Component
Source\ActionScript 3.0\FLVPlayback\fl\video

FLVPlaybackCaptioning  
C:\Program Files\Adobe\Adobe Flash CS5\en\Configuration\Component
Source\ActionScript 3.0\FLVPlaybackCaptioning\fl\video

For Mac OS X, the component source files are located here:

User Interface components  
Macintosh HD:Applications:Adobe Flash CS5:Configuration:Component
Source:ActionScript 3.0:User Interface:fl

FLVPlayback  
Macintosh HD:Applications:Adobe Flash CS5:Configuration:Component
Source:ActionScript 3.0:FLVPlayback:fl:video

FLVPlaybackCaptioning  
Macintosh HD:Applications:Adobe Flash CS5:Configuration:Component
Source:ActionScript 3.0:FLVPlaybackCaptioning:fl:video

## Component source files and Classpath

Because the ActionScript 3.0 components have their code compiled in, you should
not specify the location of the ActionScript class files in your Classpath
variable. If you do include their location in the Classpath, it will increase
the time required to compile your applications. However, if Flash finds
component class files in your Classpath setting, the class file will always take
precedence over the component's compiled-in code.

One time that you might wish to add the location of the component source files
to your Classpath setting is when you're debugging an application with
components. For more information see
[Debug component applications](./debug-component-applications.md).

## Modify the component files

If you update, add, or remove SWC-based components or add new FLA-based
components to Flash, you must reload them to the Components panel to make them
available. You can reload the components either by restarting Flash or by
selecting Reload from the Components panel menu. This will cause Flash to pick
up any components that you've added to the Components folder.

#### Reload components in the Components panel while Flash is running:

- Select Reload from the Components panel menu.

#### Remove a component from the Components panel:

- Remove the FLA, SWC, or MXP file from the Components folder and either restart
  Flash or select Reload from the Components panel menu. An MXP file is a
  component file that has been downloaded from the Adobe Exchange.

  You can remove and replace SWC-based components while Flash is running, and
  reloading will reflect the changes, but if you change or delete FLA-based
  components, the changes are not reflected until you terminate and restart
  Flash. You can, however, add FLA-based components and load them with the
  Reload command.

  > ![](../img/tip_help.png) Adobe recommends that you first make a copy of any
  > Flash component file (.fla or .as) that you are going to alter. Then you can
  > restore it, if necessary.
