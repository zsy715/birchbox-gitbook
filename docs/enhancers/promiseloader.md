# PromiseLoader

[`PromiseLoader`](https://github.com/zakness/birchbox-gitbook/tree/1ad9356b440d8ffd191f6222475ef6f0c15444b0/src/enhancers/PromiseLoader/index.js) is a module which, when combined with a React component, executes a promise based on the component’s props and merges the response and status of the promise into the components props when complete.

`PromiseLoader` uses a visibility sensor, by default, to determine whether the composed component is visible to the user before executing the underlying promise.

> NB: `PromiseLoader` is a global module in the Bernard Black application.

## Usage

Add a method to a React component that returns a promise. This method will be passed the current props of the component when `PromiseLoader` attempts to execute the promise.

```text
MyComponent.loadPromisedProps = (props) => (
  // return a promise here
)
```

Compose the React component with the `PromiseLoader.compose` method.

```text
PromiseLoader.compose(MyComponent)
```

Turn on use of the visibility sensor via the following property:

```text
MyComponent.useVisibilitySensor = true
```

## PropTypes

Additional PropTypes can be used in conjunction with `PromiseLoader`. These PropTypes are defined the same as any standard React PropType.

### input

`input` properties are properties that are required for the underlying promise object to execute. If any `input` properties are equal to `undefined` the promise will not execute until they have a defined value. If their value changes, the output data will be cleared and the promise re-executed.

```text
PromiseLoader.PropTypes.input.[React PropType validator]
```

### output

`output` properties are properties that contain data returned by the underlying promise. These are read-only properties that should not be modified or set by component code.

```text
PromiseLoader.PropTypes.output.[React PropType validator]
```

## Example

```text
const AboutView = (props) =>
  <MaskContainer className={layout.gutter} status={props.status}>
    <PageHeader>{props.title}</PageHeader>
    <Markdown className={typo.body} content={props.body} />
  </MaskContainer>

AboutView.propTypes = {
  status: CustomPropTypes.status,
  body: PromiseLoader.PropTypes.output.string,
  title: PromiseLoader.PropTypes.output.string,
}

AboutView.loadPromisedProps = (props) =>
  loadContent(props.params.slug, 'about')

export default PromiseLoader.compose(AboutView)
```

