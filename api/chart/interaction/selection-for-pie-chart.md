# Selection for Pie Chart

![](../../../.gitbook/assets/pie.gif)

### How to use

```javascript
const F2 = require('@antv/f2/lib/index'); // require F2
require('@antv/f2/lib/interaction/pie-select'); // require the interaction

// ... create a chart instance

// call the interaction, should be call before chart.render()
chart.interaction('pie-select');
```

### Configuration options {#configuration-options}

```javascript
chart.interaction('pie-select', {
  startEvent: {String},
  animate: {Boolean} / {Object},
  offset: {Number},
  appendRadius: {Number},
  style: {Object},
  cancelable: {Boolean},
  onStart: {Function},
  onEnd: {Function},
  defaultSelected: {Object}
});
```

| Name | Type | Default | Desc |
| :--- | :--- | :--- | :--- |
| `startEvent` | String | 'tap' | This interaction is triggered  by touch or touch gesture. Optional 'touchstart' or 'tap'. |
| `animate` | Boolean / Object | false | Animation configuration, defaults to false, which can be turned on by setting this property to true. Used for animation configuration when it is of type Object:`animate: {  duration: 1000,  delay: 10,  easing: 'bounceOut'}` |
| `offset` | Number | 1 | The distance between the halo and the pie chart that appears after selection. |
| `appendRadius` | Number | 8 | The axial length of the halo that appears after selection. |
| `style` | Object | `{ fillOpacity: 0.5 }` | The style configuration for halo. |
| `cancelable` | Boolean | true | After the shape is selected, click again to allow unchecked. The default is true, indicating that it will be unchecked. |
| `onStart` | Function | null | The callback after the start event is triggered. |
| `onEnd` | Function | null | The callback after the event\('touchend'\) is triggered.  |
| `defaultSelected` | Object | null | If you want shape to be selected when chart inited, you can pass in the shape value to `defaultSelected`, see [demo](https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/selection-for-pie-chart.html). |

#### `onEnd` callback

```javascript
/**
 * @param {Object} ev
 */ 
onEnd(ev) {
  // ev.data: Object, dataset of the selected shape
  // ev.shapeInfo: Object, information of the selected shape
  // ev.shape: Shape, the selected shape
  // ev.selected: the status of the current shape
  const { data, shapeInfo, shape, selected } = ev;
}
```

### Demo

url: [https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/selection-for-pie-chart.html](https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/selection-for-pie-chart.html)



