# Selection for Bar Chart

![](../../.gitbook/assets/ezgif.com-video-to-gif-5.gif)

### How to use

```javascript
const F2 = require('@antv/f2/lib/index'); // require F2
require('@antv/f2/lib/interaction/interval-select'); // require the interaction

// ... create a chart instance

// call the interaction, should be call before chart.render()
chart.interaction('interval-select');
```

### Configuration options {#configuration-options}

```javascript
chart.interaction('interval-select', {
  startEvent: {String},
  selectStyle: {Object},
  unSelectStyle: {Object},
  selectAxis: {Boolean},
  selectAxisStyle: {Object},
  cancelable: {Boolean},
  onStart: {Function}, 
  onEnd: {Function}, 
  mode: {String}
});
```

| Name | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `startEvent` | String | 'tap' | This interaction is triggered by touch or touch gesture. Optional 'touchstart' or 'tap'. |
| `selectStyle` | Object | `{ fillOpacity: 1 }` | Set the display style of the selected bar. |
| `unSelectStyle` | Object | `{ fillOpacity: 0.4 }` | Set the display style of the unselected bar. If you don't need to set it, you can set it to `null` directly. |
| `selectAxis` | Boolean | true | Whether to highlight the axis label, the default is `true`. If not needed, you can choose to turn it off: `selectAxis: false`. |
| `selectAxisStyle` | Object | `{ fontWeight: 'bold' }` | Set the style for axis label which its bar is selected. Only works if `selectAxis` is true. |
| `cancelable` | Boolean | true | After the shape is selected, click again to allow unchecked. The default is true, indicating that it will be unchecked. |
| `onStart` | Function | null | The callback after the start event is triggered. |
| `onEnd` | Function | null | The callback after the end event is triggered. |
| `mode` | String | 'shape' | The default is 'shape', that is, hitting the bar will trigger the interaction. Another optional value is 'range', which means that the selected interaction is triggered as long as the concentration point falls within a certain x-direction range of the bar. |

#### `onStart` callback

```javascript
/**
 * @param {Object} ev
 */ 
onStart(ev) {
  // ev.data: Object, dataset of the selected shape
  // ev.shapeInfo: Object, information of the selected shape
  // ev.shape: Shape, the selected shape
  // ev.selected: the status of the current shape
  const { data, shapeInfo, shape, selected } = ev;
}
```

#### `onEnd` callback {#onend-callback}

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

### Demo:[https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/selection-for-bar-chart.html](https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/selection-for-bar-chart.html)

