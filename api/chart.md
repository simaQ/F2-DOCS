# Chart

## Create a chart instance

A `<canvas>` or a canvas context must be created before drawing a chart.

```javascript
const chart = new F2.Chart({
  id: 'c1', 
  width: 500,
  height: 500
});
```

## Properties

### `id`

* type: `String`
* description:  id of the canvas element
* default: null

### `el`

* type: `HTMLElement`
* description: A canvas html element object can be passed directly if the id is not specified
* default: null

```javascript
const chart = new F2.Chart({
  el: document.getElementById('c1')
});
```

### `context`

* type: `CanvasRenderingContext2D`
* description: context of canvas
* default: null

```javascript
const chart = new F2.Chart({
  context: document.getElementById('c1').getContext('2d')
});
```

**NOTE: One of the three properties, `id`, `el`, `context` must be set one.**

### `width`

* type: `Number`
* description: width of the chart, if the width of `<canvas>` is set, you don't have to set the property.
* default: null

### `height`

* type: `Number`
* description: height of the chart, if the height of `<canvas>` is set, you don't have to set the property.
* default: null

```javascript
// <canvas id="myChart" width=375 height=260></canvas>
const chart = new F2.Chart({
  id: 'myChart'
});

// <canvas id="myChart"></canvas>
const chart = new F2.Chart({
  id: 'myChart',
  width: 375,
  height: 260
});
```

### `padding`

* type: `Number` / `Array` / `String`
* description: the spacing between the chart plot area and the canvas border.
* default: 'auto', which is calculated automatically

```javascript
const chart = new F2.Chart({
  id: 'c1',
  padding: 'auto' // default value, calculate padding automatically
});

const chart = new F2.Chart({
  id: 'c1',
  padding: [ 0, 10, 40, 100 ] // set paddings of top, right, bottom, left
});

const chart = new F2.Chart({
  id: 'c1',
  padding: 40 // single value
});

const chart = new F2.Chart({
  id: 'c1',
  padding: [ 40, 10, 'auto', 'auto' ]  // top 40px, right 10px, bottom and left is auto calculated
});
```

**NOTE: The usage of the padding here is the same as the padding in the CSS box model.**

### **appendPadding**

* type: `Number` / `Array` / `String`
* description: The reserved spacing on the four sides of the chart canvas area, that is, we will add the `appendPadding` value to the four sides based on the padding. The default is 15 px.
* default: 15

![the red area corresponds to appendPadding, the yellow area ](../.gitbook/assets/group-2%20%281%29.png)

### `pixelRatio`

* type: `Number`
* description: Override the window's default devicePixelRatio.
* default: 1

By default the chart's canvas will use a 1:1 pixel ratio, unless the physical display has a higher pixel ratio \(e.g. Retina displays\).

Setting `pixelRatio` to a value other than 1 will force the canvas size to be scaled by that amount, relative to the container size. There should be no visible difference on screen; the difference will only be visible when the image is zoomed or printed.

```javascript
// Global configuration, all charts take effect
F2.Global.pixelRatio = window.devicePixelRatio;
// Set pixel ratio just for a chart instance
const chart = new F2.Chart({
  id: 'c1',
  pixelRatio: window.devicePixelRatio
});
```

### `plugins`

* type: `Object` / `Array`
* description: register plugins for chart instance
* default: null

See [Plugin](https://antv.gitbook.io/f2/developer/plugin) for more details about plug-ins.

### `animate`

* type: `Boolean`
* description: turn animation on or off
* default: true

### `limitInPlot`

* type: `Boolean`
* description: whether to limit the geometry to the plot area, often used in the interaction of the chart, see [demo](https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/x-pan.html)
* default: false

## Methods

### `chart.get()`

* description: get properties
* return: the value of the property

The method is used to get properties of the chart, for example, `chart.get('width')`. The properties are listed as follows:

| **Property** | **Description** |
| :--- | :--- |
| `id` | the id of the canvas |
| `data` | chart's data |
| `width` | width of the chart |
| `height` | height of the chart |
| `pixelRatio` | the pixel ratio of the chart |
| `el` | the dom object corresponds to canvas |
| `canvas` | the canvas instance of F2. \(G.Canvas\) |
| `geoms` | all the geometry objects, can be get after chart rendering |

### chart.source\(\)

* description: load the data
* return: the current chart instance

**`chart.source(data)`**

* `data`: Array, chart's data

**`chart.source(data, colDefs)`**

* `data`: Array, chart's data
* `colDefs`: Object, scale configuration for each data field. **Optional**.

```javascript
chart.source(data, {
  a: {
    min: 0,
    max: 100
  }
});
```

Scale configuration is used to describe the data field, such as the type of the field, alias of the field name, the display format of the data value. Different data types have different configuration options, the supported data types are listed below:

* `linear`: Numerical data type, such 1, 2,3,4
* `cat`: Quantize data, such 'dog', 'pig'
* `timeCat`: Time data

F2 will automatically detect the type of the data, and users are also allowed to define in need. For more details of scale, see [Scale](https://antv.gitbook.io/f2/api/scale).

### chart.scale\(\)

* description: scale definition for data field
* return: current chart instance

**Warning**: If the data field is both defined in `chart.source()` and `chart.scale()`, the configuration which is defined latter will override previous configuration.

**`chart.scale('field', colDef)`**

scale definition for the data field

* `field`: String, data field name
* `colDef`: Object, configuration of the scale, see [scale](https://antv.gitbook.io/f2/api/scale) for more details

Example:

```javascript
const data = [
  { x: 0, y: 1 },
  { x: 1, y: 2 },
  { x: 2, y: 3 }
];

// scale definition for 'x' field
chart.scale('x', {
  type: 'cat',
  values: [ 'A', 'B', 'C' ], // set display value
  alias: 'letter' // alias for attribute
});
```

**`chart.scale(colDef)`**

Scale definition for one or multiple data fields.

* `colDef`: Object, configuration of the scale, see [scale](https://antv.gitbook.io/f2/api/scale) for more details.

Example:

```javascript
const data = [
  { x: 0, y: 1 },
  { x: 1, y: 2 },
  { x: 2, y: 3 }
];

// scale definition for multiple data fields
chart.scale({
  x: {
    type: 'cat',
    values: [ 'A', 'B', 'C' ], // set display value
    alias: 'letter' // alias for attribute
  },
  y: {
    type: 'cat'
  }
});
```

### chart.coord\(\)

* description: coordinate setting
* return: the current chart instance

See [Coordinate](https://antv.gitbook.io/f2/api/coordinate) for more details.

### chart.axis\(\)

* description: chart's axes configuration
* return: the current chart instance

See [Axis](https://antv.gitbook.io/f2/api/axis) for more details.

### `chart.lengend()`

* description: chart's legend configuration
* return: the current chart instance

See [Legend](https://antv.gitbook.io/f2/api/legend) for more details

### `chart.tooltip()`

* description: chart's tooltip configuration
* return: the current chart instance

See [Tooltip](https://antv.gitbook.io/f2/api/tooltip) for more details.

### `chart.guide()`

* description: chart's guides configuration
* return: the current `guideController` instance

See [Guide](https://antv.gitbook.io/f2/api/guide) for more details.

### `chart.animate()`

* description: config animation for chart
* return: the current chart instance

See [Animation](https://antv.gitbook.io/f2/api/animation) for more details

### `chart.point()`

* description: create a point geometry, for scatter chart or bubble chart
* return: a point geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.line()`

* description: create a line geometry, for line chart
* return: a line geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.area()`

* description: create a area geometry, for area chart
* return: a area geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.path()`

* description: create a path geometry, for path chart
* return: a path geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.interval()`

* description: create a interval geometry, for bar chart
* return: a interval geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.polygon()`

* description: create a polygon geometry, for heatmap chart or map
* return: a polygon geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.schema()`

* description: create a schema geometry, for candlestick chart
* return: a schema geometry instance

See [Geometry](https://antv.gitbook.io/f2/api/geometry) for more details.

### `chart.render()`

* description: render the chart and call it at the end
* return: the current chart instance

### `chart.clear()`

* description: clear the content of the chart
* return: the current chart instance

### `chart.repaint()`

* description: repaint the chart
* return: the current chart instance

### `chart.changeData(data)`

*  `data` : Array, 
* description: change the chart's data and re-render the chart
* return: the current chart instance

### `chart.changeSize(width, height)`

* `width`: Number / null, if null is specified, the width remains unchanged; 
* `height`: Number / null, if null is specified, the he remains unchanged;
* description: change the size of the chart and re-render the chart
* return: the current chart instance

`chart.changeSize(300)` only changes the width; `chart.changeSize(300, 500)` changes both width and height; `chart.changeSize(, 300)` only changes height.

### `chart.destroy()`

* description: destroy the chart instance, but the html element `<canvas>` won't be destroyed

### `chart.getPosition(record)`

* `record` : Object, is the data object
* description: get the coordinates of the original data corresponding to the canvas
* return: an coordinate object represents the coordinate of the record on canvas, in the format of `{x: , y: }`

```javascript
const point = chart.getPosition({ time: '2010-02-02', value: 20 });
```

### `chart.getRecord(point)`

* `point` : Object, is a coordinate object describes the coordinate on canvas, in the format of `{x: , y: }`
* description: get the original data record according to the coordinate on canvas
* return: the data record object corresponds to the coordinate

```javascript
const obj = chart.getRecord({ x: 100, y: 100 });
```

### `chart.getSnapRecords(point)`

* `point` : Object, is the coordinate object in the format of `{x: , y: }`
* description: get the nearby data set according to the coordinate on canvas
* return: the nearby data set which each element contains the mapped and corresponding original data. The structure of the return data is shown as below:

  ```javascript
  [
    {
      _origin: { year: '1959 年', sales: 38 }, // the original data correspnds to the shape
      points: [
        { x: 0.65625, y: 0 },
        { x: 0.65625, y: 0.2375 },
        { x: 0.71875, y: 0.2375 },
        { x: 0.71875, y: 0 }
      ], // the key points with normalized data, consiting of the shape
      _originY: 38, // the original data of y-axis
      x: 260.53499698638916, // shape's x-axis coordinate on canvas
      y: 165.34375, // shape's y-axis coordiante on canvas
      index: 5 // index of the shape
    },
    ...
    {}
  ]
  ```

```text
const obj = chart.getSnapRecords({x: 100, y: 100});
```

### `chart.getLegendItems()`

* description: get the items of the chart's legend, used for some legend operations
* return: an array of items

### `chart.getXScale()`

* description: get the scale of the chart's x-axis
* return: the scale object of the chart's x-axis

### `chart.getYScales()`

* description: get the scales of the chart's y-axes, there may be multiple y-axes
* return: the scale object array of the chart's y-axes

### `chart.showTooltip(point)`

* `point` : Object, which is the coordinate on canvas, in the format of `{x: , y: }`
* description: show tooltip of this point
* return: the current chart instance

### `chart.hideTooltip()`

* description: hide the chart's tooltip
* return: the current chart instance

