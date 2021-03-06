# Button

[`Button`](https://github.com/zakness/birchbox-gitbook/tree/1ad9356b440d8ffd191f6222475ef6f0c15444b0/src/components/Button/index.js) is a component with button-like styling that executes a function `onClick`.

If you want a link that looks like a Button, use [ButtonLink](buttonlink.md).

Buttons can be grouped together \(with their adjoining edges collapsed\) using [ButtonGroup](buttongroup.md).

## Props

### authRequired

```text
PropTypes.bool
```

If `true` and the user is not logged in, shows a login modal on click. Performs the `onClick` action upon successful login.

### buttonGroup

```text
PropTypes.shape({
  isFirst: PropTypes.bool,
  isLast: PropTypes.bool,
})
```

This prop controls which sides of the button are collapsed. You will not generally need to mess with this, as [ButtonGroup](buttongroup.md) sets it automatically on its Button children.

### color

```text
PropTypes.string
```

The text color. Can be a color name \(`colorTurquoise`\), theme color name \(`majorColorDark`\), or hex code \(`#41b1c0`\).

If the `strokeColor` prop is not set it will default to this value.

### disabled

```text
PropTypes.bool
```

If `true`, `onClick` will not execute when the Button is clicked. Disabled Buttons have a lower opacity style applied.

### fillColor

```text
PropTypes.string
```

The fill \(background\) color. Can be a color name \(`colorNeutral1F`\), theme color name \(`majorColorDark`\), or hex code \(`#41b1c0`\).

This prop is relevant for all `variant` values.

Defaults to `colorTransparent`.

### fullWidth

```text
PropTypes.bool
```

If `true`, the Button will take up the entire width of its container. If `false` the Button width will be determined by the Button’s children.

### onClick

```text
PropTypes.func.isRequired
```

The function to execute on click.

### preset

```text
PropTypes.string
```

One of the defined [Button presets](https://github.com/zakness/birchbox-gitbook/tree/1ad9356b440d8ffd191f6222475ef6f0c15444b0/src/components/Button/presets.js).

Presets are a way to easily set a commonly-used set of Button styling props. For example, these two Button declarations are equivalent:

```text
<Button preset='primary' />
<Button color='colorWhite' fillColor='majorColorDark' variant='fill' />
```

When a prop and a preset address the same value, the prop takes precedence. For example, the following Button will have yellow text:

```text
<Button preset='primary' color='colorYellow' />
```

See [massageProps](https://github.com/zakness/birchbox-gitbook/tree/1ad9356b440d8ffd191f6222475ef6f0c15444b0/src/components/Button/massageProps.js) for the precise logic of how this works.

### size

```text
PropTypes.oneOf([ 'mini', 'small', 'large' ])
```

The size of the Button \(controls the min-width and padding\).

Defaults to `large`.

### strokeColor

```text
PropTypes.string
```

The stroke \(border\) color. Can be a color name \(`colorNeutral1F`\), theme color name \(`majorColorDark`\), or hex code \(`#41b1c0`\).

This prop is only relevant if `variant` is `stroke`.

If this prop is not set it will default to the `color` value.

### trackingProps

```text
PropTypes.object
```

This object is merged into the default tracking props sent to the tag manager and Event API on click.

### variant

```text
PropTypes.oneOf([ 'fill', 'stroke' ])
```

If `stroke`, the Button will have a border controlled by the `strokeColor` prop.

Defaults to `fill`.

