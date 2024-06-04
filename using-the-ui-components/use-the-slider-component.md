# Use the Slider component

The Slider component lets a user select a value by sliding a graphical _thumb_
between the end points of a track that corresponds to a range of values. You can
use a slider to allow a user to choose a value such as a number or a percentage,
for example. You can also use ActionScript to cause the slider's value to
influence the behavior of a second object. For example, you could associate the
slider with a picture and shrink it or enlarge it based on the relative
position, or value, of the slider's thumb.

The current value of the Slider is determined by the thumb's relative location
between the end points of the track or the Slider's minimum and maximum values.

The Slider allows for a continuous range of values between its minimum and
maximum values, but you can also set the `snapInterval` parameter to specify
intervals between the minimum and maximum value. A Slider can show tick marks,
which are independent of the slider's assigned values, at specified intervals
along the track.

The slider has a horizontal orientation by default, but you can give it a
vertical orientation by setting the value of the `direction` parameter to
vertical. The slider track stretches from end to end and the tick marks are
placed from left to right just above the track.

## User interaction with the Slider component

When a Slider instance has focus, you can use the following keys to control it:

| Key         | Description                                             |
| ----------- | ------------------------------------------------------- |
| Right Arrow | Increases the associated value for a horizontal slider. |
| Up Arrow    | Increases the associated value for a vertical slider.   |
| Left Arrow  | Decreases the associated value for a horizontal slider. |
| Down Arrow  | Decreases the associated value for a vertical slider.   |
| Shift+Tab   | Moves focus to the previous object.                     |
| Tab         | Moves focus to the next object.                         |

For more information about controlling focus, see the IFocusManager interface
and the FocusManager class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_
and
[Work with FocusManager](../working-with-components/work-with-focusmanager.md).

A live preview of each Slider instance reflects changes made to parameters in
the Property inspector or the Component inspector during authoring.

## Slider component parameters

You can set the following authoring parameters in the Property inspector or in
the Component inspector for each Slider component instance: `direction`,
`liveDragging`, `maximum`, `minimum`, `snapInterval`, `tickInterval`, and
`value`. Each of these parameters has a corresponding ActionScript property of
the same name. For information on the possible values for these parameters, see
the Slider class in the
_[ActionScript 3.0 Reference for the Adobe Flash Platform](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/index.html)_.

## Create an application with the Slider

The following example creates a Slider instance to allow the user to express his
or her level of satisfaction with some hypothetical event. The user moves the
Slider to the right or the left to indicate a higher or lower level of
satisfaction.

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag a Label component from the Components panel to the center of the Stage.

    - Give it an instance name of **valueLabel**.

    - Assign the value **0** **percent** to the `text` parameter.

3.  Drag a Slider component from the Components panel and center it below
    `value_lbl`.

    - Give it an instance name of **aSlider**.

    - Assign it a width (W:) of **200**.

    - Assign it a height (H:) of **10**.

    - Assign a value of **100** to the `maximum` parameter.

    - Assign a value of **10** to both the `snapInterval` and `tickInterval`
      parameters.

4.  Drag another Label instance from the Library panel and center it below
    `aSlider.`

    - Give it an instance name of **promptLabel.**

    - Assign it a width (W:) of 250.

    - Assign it a height (H:) of 22.

    - Enter **Please indicate your level of satisfaction** for the `text`
      parameter.

5.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following ActionScript code:

        import fl.controls.Slider;
        import fl.events.SliderEvent;
        import fl.controls.Label;

        aSlider.addEventListener(SliderEvent.CHANGE, changeHandler);

        function changeHandler(event:SliderEvent):void {
            valueLabel.text = event.value + "percent";
        }

6.  Select Control \> Test Movie.

    In this example, as you move the thumb of the slider from one interval to
    another, a listener for the `SliderEvent.CHANGE` event updates the `text`
    property of `valueLabel` to display the percentage that corresponds to the
    thumb's position.

## Create an application with the Slider component using ActionScript

The following example creates a Slider using ActionScript.The example downloads
an image of a flower and uses the Slider to let the user fade or brighten the
image by changing its `alpha` property to correspond to the Slider's value.

> **Note:** The examples below use the file
> [`image1.jpg`](../img/helpexamples/image1.jpg).

1.  Create a new Flash (ActionScript 3.0) document.

2.  Drag the Label component and the Slider component from the Components panel
    to the current document's Library panel.

    This adds the components to the library, but doesn't make them visible in
    the application.

3.  Open the Actions panel, select Frame 1 in the main Timeline, and enter the
    following code to create and position the component instances:

        import fl.controls.Slider;
        import fl.events.SliderEvent;
        import fl.controls.Label;
        import fl.containers.UILoader;

        var sliderLabel:Label = new Label();
        sliderLabel.width = 120;
        sliderLabel.text = "< Fade - Brighten >";
        sliderLabel.move(170, 350);

        var aSlider:Slider = new Slider();
        aSlider.width = 200;
        aSlider.snapInterval = 10;
        aSlider.tickInterval = 10;
        aSlider.maximum = 100;
        aSlider.value = 100;
        aSlider.move(120, 330);

        var aLoader:UILoader = new UILoader();
        aLoader.source = "http://www.example.com/image1.jpg";
        aLoader.scaleContent = false;

        addChild(sliderLabel);
        addChild(aSlider);
        addChild(aLoader);

        aLoader.addEventListener(Event.COMPLETE, completeHandler);

        function completeHandler(event:Event) {
            trace("Number of bytes loaded: " + aLoader.bytesLoaded);
        }

        aSlider.addEventListener(SliderEvent.CHANGE, changeHandler);

        function changeHandler(event:SliderEvent):void {
            aLoader.alpha = event.value * .01;
        }

4.  Select Control \> Test Movie to run the application.

5.  Move the Slider's thumb to the left to fade the image and to the right to
    brighten it.
