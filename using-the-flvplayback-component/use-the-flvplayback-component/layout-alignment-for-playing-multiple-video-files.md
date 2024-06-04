# Layout alignment for playing multiple video files

ActionScript 3.0 FLVPlayback has an `align` property that specifies whether the
video file should be centered when it is resized or positioned at the top,
bottom, left, or right of the component. In addition to the component's `x`,
`y`, `width`, and `height` properties, the ActionScript 3.0 component also has
`registrationX`, `registrationY`, `registrationWidth`, and `registrationHeight`
properties. Initially, these match the `x`, `y`, `width`, and `height`
properties. When loading subsequent video files, automatic re-layout does not
change these so the new video file can be centered in the same place. If
`scaleMode` = `VideoScaleMode.MAINTAIN_ASPECT_RATIO`, subsequent FLV files can
fit into the component's original dimensions rather than causing the component's
width and height to be altered.
