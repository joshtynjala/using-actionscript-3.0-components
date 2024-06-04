# Customize the UILoader component

You can transform a UILoader component horizontally and vertically while
authoring and at run time. While authoring, select the component on the Stage
and use the Free Transform tool or any of the Modify \> Transform commands. At
run time, use the `setSize()` method or the appropriate properties such as the
`width`, `height`, `scaleX`, and `scaleY` properties.

The sizing behavior of the UILoader component is controlled by the
`scaleContent` property. When `scaleContent` is `true`, the content is scaled to
fit within the bounds of the loader (and is rescaled when `setSize()` is
called). When `scaleContent` is `false`, the size of the component is fixed to
the size of the content and `setSize()` and the sizing properties have no no
effect.

The UILoader component has no user interface elements to which you can apply
styles or skins.
