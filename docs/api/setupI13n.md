## setupI13n

We provide `setupI13n` as a convenient [higher order function](https://medium.com/@dan_abramov/mixins-are-dead-long-live-higher-order-components-94a0d2f9e750) to setup the ReactI13n, you will need to pass your `top level component`, `options`, and `plugins` into it. This takes care of creating a `ReactI13n` instance and setting up the plugins. 

 * `Component` - the top level application component.
 * `options` - the options passed into ReactI13n.
 * `options.rootModelData` - define the `i13nModel` data of the root.
 * `options.I13nNodeClass` - you can inherit the `I13nNode` and add the functionality you need, just pass the class.
 * `options.isViewportEnabled` - define if you want to enable the viewport checking.
 * `options.handlerTimeout` - define the timeout of the event handler, the event callback will be executed even if handlers don't finish in time, default to 1000ms.
 * `options.displayName` - display name of the wrapper component, will fallback to `I13n` + original display name
 * `plugins` - plugins array that you defined according to the definition below.

```js
var React = require('react');
var setupI13n = require('react-i13n').setupI13n;
var someReactI13nPlugin = require('some-react-i13n-plugin');

var DemoApp = React.createClass({
    ...
});

var I13nDempApp = setupI13n(DemoApp, {
    rootModelData: {site: 'foo'}, // the default i13n model data to apply to all i13n nodes
    isViewportEnabled: true,
    handlerTimeout: 500
}, [someReactI13nPlugin]);

// then you could use I13nDemoApp to render you app
```

### Util Functions

You will get i13n util functions automatically via `this.props.i13n` by using `setupI13n`, more detail please refer to [util functions](../guides/utilFunctions.md).
