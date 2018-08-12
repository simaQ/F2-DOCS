# Canvas

### `Canvas`

```javascript
new Canvas(config);
```

Canvas Renderer constructor.

-  `config` : Object, the configuration needed to create a canvas object, it includes the following attributes:

| Attribute | Type | Description |
| :--- | :--- | :--- |
| `el` | String/HtmlElement | Container selector or DOM element |
| `context` | CanvasRenderingContext2D | The context of the canvas. |
| `width` | Number | Optional, width of the canvas. If it is omitted, the actual width of the canvas DOM is used by default. |
| `height` | Number | Optional, height of the canvas. If it is omitted, the actual height of the canvas DOM is used by default. |
| `pixelRatio` | Number | F2 automatically handles pixel ratio adjustments in order to render crisp drawings on all devices. Unless otherwise specified, the pixel ratio will be defaulted to the actual device pixel ratio: `window.devicePixelRatio`. You can override the device pixel ratio for special situations, or, if you don't want the pixel ratio to be taken into account, you can set it to 1. |

Example:

```javascript
const canvas = new Canvas({
  id: 'canvas',
  width: 500,
  height: 500,
  pixelRatio: 1
});
```



#### Methods

**getChildren\(\)**

```javascript
/**
 * Get the elements contained in the container
 * @return {Array}
 */
getChildren()
```

**isDestroyed\(\)**

```javascript
/**
 * Wether the object is destroyed.
 * @return {Boolean}
 */
isDestroyed()
```

**getWidth\(\)**

```javascript
/**
 * Get width of the canvas
 * @return {Number}
 */
getWidth()
```

**getHeight\(\)**

```javascript
/**
 * Get height of the canvas
 * @return {Number}
 */
getHeight()
```

**changeSize\(width, height\)**

```javascript
/**
 * Change the size of the canvas
 * @param  {Number} width  
 * @param  {Number} height 
 */
changeSize(width, height)
```

**getPointByClient\(clientX, clientY\)**

```javascript
/**
 * Convert the coordinate on browser to coordinate on canvas
 * @param  {Number} clientX Coordinate of x-axis on browser
 * @param  {Number} clientY Coordinate of y-axis on browser
 * @return {Object}
 */
getPointByClient(clientX, clientY)
```

**addShape\(type, config\)**

```javascript
/**
 * Create a shape and add it to canvas
 * @param {String} type Type of shape
 * @param {Object} config  Configuration of the shape
 * @return {Shape}
 */
addShape(type, config = {})
```

The `config` parameter passed in is the configuration of the shape, includes:

```javascript
{
  className: String, // class name specified by users
  zIndex: Number, // z-index of the shape
  visible: Boolean, // wether the shape is visible
  attrs: Object // graphic attributes of the shape, different shapes have different attributes, see Shape for more details.
}
```

**addGroup\(config\)**

```javascript
/**
 * Create and add a group
 * @param {Object||Null} cfg Configuration for group
 * @return {Group}
 */
addGroup(config)
```

`config` can be Null or Object, if the `config` is an object, passed in is the configuration for Group can be:

```javascript
{
  className: String, // user specified class name
  zIndex: Number, // hierarchical index of the group
  visible: Boolean // wether the group is visible
}
```

**add\(items\)**

```javascript
/**
 * Add elements to canvas
 * @param {Array||Group||Shape} Items can be a shape instance, a group instance, a shape array or a group array
 * @return {Canvas}
 */
add(items)
```

**contain\(item\)**

```javascript
/**
 * Wether current canvas contains the item
 * @param  {Shape||Group} Item can be a shape instance or group instance
 * @return {Boolean}
 */
contain(item)
```

**sort\(\)**

```javascript
/**
 * Sort the elements in the container by their zIndex, in descending order
 * @return {Canvas||Group} The container itself
 */
sort()
```

**get\(name\)**

```javascript
/**
 * Get the attribute from canvas by attribute name
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

**clear\(\)**

```text
/**
  * Clear all the elements
  * @return {Canvas|Group} The container itself
  */
clear()
```

**draw\(\)**

Draw the canvas.

**destroy\(\)**

Destroy the canvas object.

