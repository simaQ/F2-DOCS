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
new Shape.Line(config)
```

Line constructor.  

* `config` : Object, it includes the following attributes:

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
new Shape.Arc(config)
```

Arc constructor.  

* `config` : Object, it includes the following attributes:

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
new Shape.Circle(config)
```

Circle constructor.  

* `config` : Object, it includes the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| x | Number |  |
| y | Number |  |
| r | Number |  |
| fill | String/CanvasGradient/CanvasPattern |  |
| fillStyle | String/CanvasGradient/CanvasPattern |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

