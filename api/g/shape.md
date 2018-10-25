# Shape

### `Shape`

`new Shape(config)`

Shape constructor. Shapes are primitive objects such as rectangles,  
circles, text, lines, etc.

* `config`: Object, it contains the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `zIndex` | Number | z-index for shape, used to adjust the drawing order. |
| `visible` | Boolean | visible or hidden |
| `className` | String | mark of the object, specified by users |
| `attrs` | Object | graphical attributes for shape, must be set. |

We provide the following shape classes:

```javascript
const { 
  Line, 
  Arc, 
  Circle, 
  Polygon, 
  Polyline, 
  Rect, 
  Sector, 
  Text, 
  Custom
} = Shape;
```

These shapes have general attributes and different shapes have their own `attrs`.

Use `new Shape[shapeType](config)` to create a specific type of shape.

Example:

```javascript
// create a line
const line = new F2.G.Shape.Line({
  zIndex: 0,
  visible: true,
  attrs: {
    x1: 10,
    y1: 10,
    x2: 100,
    y2: 10,
    lineWidth: 1,
    stroke: '#1890ff'
  }
});
```

#### Methods

**getType\(\)**

```javascript
/**
 * The type of shape
 * @return {String}
 */
getType()
```

**isDestroyed\(\)**

```javascript
/**
 * Wether the object is destroyed.
 * @return {Boolean}
 */
isDestroyed()
```

**isVisible\(\)**

```javascript
/**
 * Wether the current shape object is visible.
 * @return {Boolean}
 */
isVisible()
```

**isShape\(\)**

```javascript
/**
 * Wether that the current object is a shape type
 * @return {Boolean}
 */
isShape()
```

**attr\(\)**

set or get the attributes.

```javascript
/**
 * Return all the graphical attributes
 * @return {Object}
 */
attr()

/**
 * get the graphical attribute of the name
 * @return The corresponding attribute
 */
attr(name)

/**
 * Set graphical attribute value for the attribute name
 * @param  {String} name  Attribue name
 * @param  {Any} value    Attribute value
 * @return {Shape}       The current shape object
 */
attr(name, value)

/**
 * Set multiple graphical attributes
 * @param  {Object} config  Object contains attributes
 * @return {Shape}       The current shape object	
 */
attr(config)
```

Example:

Use `attr('matrix')` to get matrix attribute.  
Use `attr('clip')` to get clip attribute.

**getBBox\(\)**

```javascript
/**
 * Get the minimum bounding box of the shape
 * @return {Object} The minimum bounding box
 */
getBBox()
```

The structure of the bounding box is as follows:

```text
{
  minX: 39.17999267578125, 
  minY: 52.131654999999995,
  maxX: 211,
  maxY: 116.58097999999998,
  width: 171.82000732421875,
  height: 64.44932499999999
}
```

[![](https://camo.githubusercontent.com/81bf784d719510013cf99e0ae4f834957ed56294/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f726d73706f7274616c2f795750566e4555614f7a485a4974634b654957442e706e67)](https://camo.githubusercontent.com/81bf784d719510013cf99e0ae4f834957ed56294/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f726d73706f7274616c2f795750566e4555614f7a485a4974634b654957442e706e67)

**getParent\(\)**

```javascript
/**
 * Get the parent element
 * @return {Group || Canvas} The parent of the current object, may be a group instance or canvas instance
 */
getParent()
```

**show\(\)**

```javascript
/**
 * Display the shape
 */
show()
```

**hide\(\)**

```javascript
/**
 * Hide the shape
 */
hide()
```

**get\(name\)**

```javascript
/**
 * Get the attribute from shape by attribute name
 * @param {String} name attribute name 
 * @return {*} 
 */
get(name)
```

**set\(name, value\)**

```javascript
/**
 * Set the attribute value for the corresponding attribute name
 * @param {String} name attribute name 
 * @param {String} value the value setting for the attribute 
 */
set(name, value)
```

**getMatrix\(\)**

```javascript
/**
  * Get the current matrix
  * @return {Array}
  */
getMatrix() 
```

**setMatrix\(m\)**

```javascript
/**
 * Set matrix
 * @param {Array} m Matrix array
 */
setMatrix(m)
```

**transform\(actions\)**

Perform matrix transformation on the current object.

```javascript
transform(actions) // actions is an array containing the set of operations
```

The operations supported in actions are 't' \(translate\), 's' \(scale\), 'r' \(rotate\), operations can be combined in any combination order. For example:

```javascript
[
  [ 't', x, y ], // t for translate, x for offset on x-axis direction, y for offset in y-axis direction
  [ 's', sx, sy ], // s for scale, sx for scale on x-axis direction, sy for scale on y-axis direction
  [ 'r', radian] // r for rotate，radian for the radians of the rotation
]
```

**translate\(x, y\)**

```javascript
/**
 * Translate the current element
 * @param  {Number} x Offset in x-axis direction
 * @param  {Number} y Offset in y-axis direction
 */
translate(x, y)
```

**rotate\(radians\)**

```javascript
/**
 * Rotate the current element
 * @param  {Number} radian The radians of the rotation
 */
rotate(radian)
```

**scale\(sx, sy\)**

```javascript
/**
 * Perform scale operation on current object
 * @param  {Number} sx The scale on x-axis direction
 * @param  {Number} sy The scale on y-axis direction
 */
scale(sx, sy)
```

**setTransform\(actions\)**

Do translating, rotating and scaling operations **after resetting the matrix**.

```javascript
setTransform(actions) // actions is an array containing operations
```

The `actions` parameter is same as the parameter in `transform(actions)`.

**remove\(destroy\)**

```javascript
/**
 * Remove item itself from its parent
 * @param  {Boolean} destroy true means to destroy iteself after removing, false means just remove but not destroy.
 * @return {null}
 */
remove(destroy)
```

**destroy\(\)**

Destroy the element itself, if it has a parent, remove it from parent.

### Shape.Line

```javascript
new Shape.Line({
  attrs: {}
})
```

Line constructor.  

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `x1` | Number | x value for first line point |
| `y1` | Number | y value or first line point |
| `x2` | Number | x value for second line point |
| `y2` | Number | y value or second line point |
| `lineWidth` | Number | set the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineCap` | String | determines how the end points of every line are drawn.See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `stroke` | String/[`CanvasGradient`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasGradient) /[`CanvasPattern`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasPattern) | the color or style to use for the lines around shapes. |
| `strokeStyle` | `String/CanvasGradient/CanvasPatter` | same as `stroke` |
| `strokeOpacity` | Number | the opacity for stroke. |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |

Example:

```javascript
const line = new G.Shape.Line({
  attrs: {
    x1: 50,
    y1: 50,
    x2: 100,
    y2: 100,
    lineWidth: 40,
    strokeStyle: '#223273',
    lineCap: 'round'
  }
});
```

### Shape.Arc

```javascript
new Shape.Arc({
  attrs: {}
})
```

Arc constructor.  

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | Number | center's x coordinate |
| `y` | Number | center's y coordinate |
| `r` | Number | radius |
| `startAngle` | Number | Start angle of the arc, this should be in radian. |
| `endAngle` | Number | End angle of the circle, this should be in radian. |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes.  |
| `strokeStyle` | String/CanvasGradient/CanvasPatter | same as `stroke.` |
| `strokeOpacity` | Number | the opacity for `stroke`. |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |
| `lineCap` | String | determines how the end points of every line are drawn.See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineWidth` | Number | sets the thickness of lines in space units.See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |

Example:

```javascript
const arc = new G.Shape.Arc({
  attrs: {
    x: 20, 
    y: 20,
    r: 50, 
    startAngle: 0,
    endAngle: Math.PI / 2,
    lineWidth: 2,
    stroke: '#18901f'
  }
});
```

### Shape.Circle

```javascript
new Shape.Circle({
  attrs: {}
})
```

Circle constructor.  

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | Number | center's x coordinate |
| `y` | Number | center's y coordinate |
| `r` | Number | radius |
| `fill` | String/CanvasGradient/CanvasPattern | the color or style to use inside shapes |
| `fillStyle` | String/CanvasGradient/CanvasPattern | same as `fill` |
| `fillOpacity` | Number | the opacity for `fill` style |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes. |
| `strokeStyle` | String/CanvasGradient/CanvasPattern | same as `stroke`. |
| `strokeOpacity` | Number | the opacity for `stroke` style. |
| `lineWidth` | Number | sets the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |

Example:

```javascript
const circle = new G.Shape.Circle({
  attrs: {
    x: 10,
    y: 10,
    r: 50,
    fill: 'red'
  }
});
```

### Shape.Polyline <a id="shape-circle"></a>

```text
new Shape.Polyline({
  attrs: {}
})
```

Polyline constructor.

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `points` | Array | points array, which constructs the polyline. |
| `smooth` | `Boolean` | Wether to draw a curve line, the default value is false. |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes. |
| `strokeStyle` | String/CanvasGradient/CanvasPattern | same as `stroke`. |
| `strokeOpacity` | Number | the opacity for `stroke` style. |
| `lineCap` | String | determines how the end points of every line are drawn.See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineJoin` | String | determines how two connecting segments.See Line Styl |
| `lineWidth` | Number | sets the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |

Example:

```javascript
const polyline = new G.Shape.Polyline({
  attrs: {
    points: [
      { x: 10, y: 10 },
      { x: 20, y: 45 },
      { x: 40, y: 80 },
      { x: 123, y: 70 },
      { x: 80, y: 32 }
    ],
    smooth: true,
    lineWidth: 1,
    stroke: 'red'
  }
})
```

### Shape.Polygon

```text
new Shape.Polygon({
  attrs: {}
})
```

Polygon constructor.

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `points` | Array | points array, which constructs the polygon. |
| `fill` | String/CanvasGradient/CanvasPattern | the color or style to use inside shapes |
| `fillStyle` | String/CanvasGradient/CanvasPattern | same as `fill` |
| `fillOpacity` | Number | the opacity for `fill` style |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes. |
| `strokeStyle` | String/CanvasGradient/CanvasPattern | same as `stroke`. |
| `strokeOpacity` | Number | the opacity for `stroke` style. |
| `lineWidth` | Number | sets the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |

Example:

```javascript
const polygon = new G.Shape.Polygon({
  attrs: {
    points: [
      { x: 10, y: 10 },
      { x: 20, y: 45 },
      { x: 40, y: 80 },
      { x: 123, y: 70 },
      { x: 80, y: 32 }
    ], // the points the make up the polygon
    lineWidth: 1,
    fill: 'red'
  }
});
```

### Shape.Rect

```text
new Shape.Rect({
  attrs: {}
})
```

Rect constructor.

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | Number | x coordinate of upper left point of the rectangle. |
| `y` | Number | x coordinate of upper left point of the rectangle. |
| `height` | Number | the height of rectangle. |
| `width` | Number | the width of rectangle. |
| `radius` | Number/Array | the border radius for rectangle. |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes. |
| `strokeStyle` | String/CanvasGradient/CanvasPattern | same as `stroke`. |
| `strokeOpacity` | Number | the opacity for `stroke` style. |
| `fill` | String/CanvasGradient/CanvasPattern | the color or style to use inside shapes. |
| `fillStyle` | String/CanvasGradient/CanvasPattern | same as `fill`. |
| `fillOpacity` | Number | the opacity for `fill` style. |
| `lineWidth` | Number | sets the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |

Example:

```javascript
const rect = new G.Shape.Rect({
  attrs: {
    x: 50,
    y: 50,
    height: 20,
    width: 80,
    lineWidth: 1,
    fill: '#1890FF',
    strokeStyle: '#000',
    radius: 2
  }
});
```

The `radius` usage:

![](../../.gitbook/assets/image%20%282%29.png)

### Shape.Sector

```javascript
new Shape.Sector({
  attrs: {}
})
```

Sector constructor.  

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | Number | center's x coordinate |
| `y` | Number | center's y coordinate |
| `r` | Number | radius |
| `r0` | Number | the inner radius |
| `startAngle` | Number | start angle of sector, it should be a radian. |
| `endAngle` | Number | end angle of sector, it should be a radian. |
| `fill` | String/CanvasGradient/CanvasPattern | the color or style to use inside shapes |
| `fillStyle` | String/CanvasGradient/CanvasPattern | same as `fill` |
| `fillOpacity` | Number | the opacity for `fill` style |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes. |
| `strokeStyle` | String/CanvasGradient/CanvasPattern | same as `stroke`. |
| `strokeOpacity` | Number | the opacity for `stroke` style. |
| `lineWidth` | Number | sets the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `lineDash` | Array | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\).See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |

Example:

```javascript
const sector = new G.Shape.Sector({
  attrs: {
    x: 100, 
    y: 150,
    r: 50,
    r0: 30, 
    startAngle: -Math.PI / 3, 
    endAngle: Math.PI / 2, 
    lineWidth: 0, 
    fill: '#223273' 
  }
});
```

### Shape.Text

```javascript
new Shape.Text({
  attrs: {}
})
```

Text constructor.  

* `attrs` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `x` | Number | x coordinate of the display position |
| `y` | Number | y coordinate of the display position |
| `text` | String | text content, if you want a text wrapping, just write '\n' in the text, such as 'maximum \n200'. |
| `rotate` | Number | the rotate angle, it should be a radian. |
| `fill` | String/CanvasGradient/CanvasPattern | the color or style to use inside shapes |
| `fillStyle` | String/CanvasGradient/CanvasPattern | same as `fill` |
| `fillOpacity` | Number | the opacity for `fill` style |
| `stroke` | String/CanvasGradient/CanvasPattern | the color or style to use for the lines around shapes. |
| `strokeStyle` | String/CanvasGradient/CanvasPattern | same as `stroke`. |
| `strokeOpacity` | Number | the opacity for `stroke` style. |
| `lineWidth` | Number | sets the thickness of lines in space units. See [Line Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#line-style). |
| `opacity` | Number | the alpha value that is applied to shapes and images before they are drawn onto the canvas. |
| `textAlign` | String | specifies the horizontal alignment of text in an element. See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `textBaseline` | String | sets the vertical alignment of an element.See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `fontStyle` | String | specifies the font style for text.See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `fontSize` | String | specifies the font size of text.See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `fontFamily` | String | specifies the font family for text.See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `fontWeight` | String / Number | specifies the weight of a font.See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `fontVariant` | String | specifies whether or not a text should be displayed in a small-caps font.See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |
| `lineHeight` | Number | specifies the height of a line. See [Text Style](https://antv.gitbook.io/f2/api/canvas-api-in-f2#text-style). |

Example:

```javascript
const sector = new G.Shape.Text({
  attrs: {
    x: 30,
    y: 30,
    fontFamily: 'Arial',
    fontSize: 12,
    fontStyle: 'normal',
    fontWeight: 'normal',
    fontVariant: 'normal',
    fill: 'red',
    lineWidth: 1,
    rotate: Math.PI
  }
});
```

### Shape.Custom

```javascript
new Shape.Custom({
  attrs: {},
  createPath(context) {
    // draw shape here
  },
  calculateBox() {
    // calculate the bounding box
  }
});
```

Custom shape constructor.  

