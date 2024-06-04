# Use the ProgressBar component

The ProgressBar component displays the progress of loading content, which is
reassuring to a user when the content is large and can delay the execution of
the application. The ProgressBar is useful for displaying the progress of
loading images and pieces of an application. The loading process can be
determinate or indeterminate. A _determinate_ progress bar is a linear
representation of a task's progress over time and is used when the amount of
content to load is known. An _indeterminate_ progress bar is used when the
amount of content to load is unknown. You can also add a Label component to
display the progress of loading as a percentage.

The ProgressBar component uses 9-slice scaling and has a bar skin, a track skin,
and an indeterminate skin.

## User interaction with the ProgressBar component

There are three modes in which to use the ProgressBar component. The most
commonly used modes are the event mode and the polled mode. These modes specify
a loading process that either emits `progress` and `complete` events (event and
polled mode) or exposes `bytesLoaded` and `bytesTotal` properties (polled mode).
You can also use the ProgressBar component in manual mode by setting the
`maximum`, `minimum`, and `value` properties along with calls to the
`ProgressBar.setProgress()` method. You can set the indeterminate property to
indicate whether the ProgressBar has a striped fill and a source of unknown size
( `true`) or a solid fill and a source of known size ( `false`).

You set the ProgressBar's mode by setting its `mode` property, either through
the `mode` parameter in the Property inspector or the Component inspector or by
using ActionScript.

If you use the ProgressBar to show processing status, like parsing 100,000
items, if it is in a single frame loop there will be no visible updates to the
ProgressBar because there are no redraws of the screen.

## ProgressBar component parameters

You can set the following parameters in the Property inspector or in the
Component inspector for each ProgressBar instance: `direction`, `mode`, and
`source`. Each of these has a corresponding ActionScript property of the same
name.

You can write ActionScript to control these and additional options for the
ProgressBar component using its properties, methods, and events. For more
information, see the ProgressBar class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the ProgressBar

The following procedure shows you how to add a ProgressBar component to an
application while authoring. In this example, the ProgressBar uses the event
mode. In event mode, the loading content emits `progress` and `complete` events
that the ProgressBar dispatches to indicate progress. When the `progress` event
occurs, the example updates a label to show the percent of content that has
loaded. When the `complete` event occurs, the example displays "Loading
complete" and the value of the `bytesTotal` property, which is the size of the
file.

> **Note:** The example below uses the file
> [`song1.mp3`](../../img/helpexamples/song1.mp3).

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ProgressBar component from the Components panel to the Stage.

    - In the Property inspector, enter the instance name **aPb**.

    - In the Parameters section, Enter **200** for the X value.

    - Enter **260** for the Y value.

    - Select `event` for the `mode` parameter.

3.  Drag the Button component from the Components panel to the Stage.

    - In the Property inspector, enter **loadButton** as the instance name.

    - Enter **220** for the X parameter.

    - Enter **290** for the Y parameter.

    - Enter **Load Sound** for the `label` parameter.

4.  Drag the Label component to the Stage and give it an instance name of
    **progLabel**.

    - Enter **150** for the W value.

    - Enter **200** for the X parameter.

    - Enter **230** for the Y parameter.

    - In the Parameters section, clear the value for the `text` parameter.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code, which loads an mp3 audio file:

        import fl.controls.ProgressBar;
        import flash.events.ProgressEvent;
        import flash.events.IOErrorEvent;

        var aSound:Sound = new Sound();
        aPb.source = aSound;
        var url:String = "http://www.example.com/song1.mp3";
        var request:URLRequest = new URLRequest(url);

        aPb.addEventListener(ProgressEvent.PROGRESS, progressHandler);
        aPb.addEventListener(Event.COMPLETE, completeHandler);
        aSound.addEventListener(IOErrorEvent.IO_ERROR, ioErrorHandler);
        loadButton.addEventListener(MouseEvent.CLICK, clickHandler);

        function progressHandler(event:ProgressEvent):void {
            progLabel.text = ("Sound loading ... " + aPb.percentComplete);
        }

        function completeHandler(event:Event):void {
            trace("Loading complete");
            trace("Size of file: " + aSound.bytesTotal);
            aSound.close();
            loadButton.enabled = false;
        }

        function clickHandler(event:MouseEvent) {
            aSound.load(request);
        }

        function ioErrorHandler(event:IOErrorEvent):void {
            trace("Load failed due to: " + event.text);
        }

6.  Select Control \> Test Movie.

#### Create an application with the ProgressBar component in polled mode

The following example sets the ProgressBar to polled mode. In polled mode,
progress is determined by listening for `progress` events on the content that is
loading and using its `bytesLoaded` and `bytesTotal` properties to calculate
progress. This example loads a Sound object, listens for its `progress` events,
and calculates the percent loaded using its `bytesLoaded` and `bytesTotal`
properties. It displays the percent loaded in both a label and in the Output
panel.

> **Note:** The example below uses the file
> [`song1.mp3`](../../img/helpexamples/song1.mp3).

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a ProgressBar component from the Components panel to the Stage and
    enter the following values in the Property inspector:

    - Enter **aPb** for the instance name.

    - Enter **185** for the X value.

    - Enter **225** for the Y value.

3.  Drag the Label component to the Stage and enter the following values in the
    Property inspector:

    - Enter **progLabel** for the instance name.

    - Enter **180** for the X value.

    - Enter **180** for the Y value.

    - In the Parameters section, clear the value for the text parameter.

4.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code, which creates a Sound object ( `aSound`) and
    calls `loadSound()` to load a sound into the Sound object:

        import fl.controls.ProgressBarMode;
        import flash.events.ProgressEvent;
        import flash.media.Sound;

        var aSound:Sound = new Sound();
        var url:String = "http://www.example.com/song1.mp3";
        var request:URLRequest = new URLRequest(url);

        aPb.mode = ProgressBarMode.POLLED;
        aPb.source = aSound;
        aSound.addEventListener(ProgressEvent.PROGRESS, loadListener);

        aSound.load(request);

        function loadListener(event:ProgressEvent) {
            var percentLoaded:int = event.target.bytesLoaded / event.target.bytesTotal * 100;
            progLabel.text = "Percent loaded: " + percentLoaded + "%";
            trace("Percent loaded: " + percentLoaded + "%");
        }

5.  Select Control \> Test Movie to run the application.

#### Create an application with the ProgressBar component in manual mode

The following example sets the ProgressBar to manual mode. In manual mode, you
must set progress manually by calling the `setProgress()` method and provide it
with the current and maximum values to determine the extent of progress. You do
not set the `source` property in manual mode. The example uses a NumericStepper
component, with a maximum value of 250, to increment the ProgressBar. When the
value in the NumericStepper changes and triggers a `CHANGE` event, the event
handler ( `nsChangeHander`) calls the `setProgress()` method to advance the
ProgressBar. It also displays the percent of progress completed, based on the
maximum value.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ProgressBar component from the Components panel to the Stage and
    give it the following values in the Property inspector:

    - Enter **aPb** for the instance name.

    - Enter **180** for the X value.

    - Enter **175** for the Y value.

3.  Drag a NumericStepper component to the Stage and enter the following values
    in the Property inspector:

    - Enter **aNs** for the instance name.

    - Enter **220** for the X value.

    - Enter **215** for the Y value.

    - In the Parameters section, enter **250** for the maximum parameter, **0**
      for the minimum value, **1** for the `stepSize` parameter, and **0** for
      the `value` parameter.

4.  Drag a Label component to the Stage and enter the following values in the
    Property inspector:

    - Enter **progLabel** for the instance name.

    - Enter **150** for the W value.

    - Enter **180** for the X value.

    - Enter **120** for the Y value.

    - In the Parameters tab, clear the value Label for the text parameter.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following code:

        import fl.controls.ProgressBarDirection;
        import fl.controls.ProgressBarMode;
        import flash.events.Event;

        aPb.direction = ProgressBarDirection.RIGHT;
        aPb.mode = ProgressBarMode.MANUAL;
        aPb.minimum = aNs.minimum;
        aPb.maximum = aNs.maximum;
        aPb.indeterminate = false;

        aNs.addEventListener(Event.CHANGE, nsChangeHandler);

        function nsChangeHandler(event:Event):void {
            aPb.value = aNs.value;
            aPb.setProgress(aPb.value, aPb.maximum);
            progLabel.text = "Percent of progress = " + int(aPb.percentComplete) + "%";
        }

6.  Select Control \> Test Movie to run the application.

7.  Click the Up Arrow on the NumericStepper to advance the ProgressBar.

#### Create a ProgressBar using ActionScript

This example creates a ProgressBar using ActionScript. Apart from that, it
duplicates the functionality of the preceding example, which creates a
ProgressBar in manual mode.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the ProgressBar component to the Library panel.

3.  Drag the NumericStepper component to the Library panel.

4.  Drag the Label component to the Library panel.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following code:

        import fl.controls.ProgressBar;
        import fl.controls.NumericStepper;
        import fl.controls.Label;
        import fl.controls.ProgressBarDirection;
        import fl.controls.ProgressBarMode;
        import flash.events.Event;

        var aPb:ProgressBar = new ProgressBar();
        var aNs:NumericStepper = new NumericStepper();
        var progLabel:Label = new Label();

        addChild(aPb);
        addChild(aNs);
        addChild(progLabel);

        aPb.move(180,175);
        aPb.direction = ProgressBarDirection.RIGHT;
        aPb.mode = ProgressBarMode.MANUAL;

        progLabel.setSize(150, 22);
        progLabel.move(180, 150);
        progLabel.text = "";

        aNs.move(220, 215);
        aNs.maximum = 250;
        aNs.minimum = 0;
        aNs.stepSize = 1;
        aNs.value = 0;

        aNs.addEventListener(Event.CHANGE, nsChangeHandler);

        function nsChangeHandler(event:Event):void {
            aPb.setProgress(aNs.value, aNs.maximum);
            progLabel.text = "Percent of progress = " + int(aPb.percentComplete) + "%";
        }

6.  Select Control \> Test Movie to run the application.

7.  Click the Up Arrow on the NumericStepper to advance the ProgressBar.
