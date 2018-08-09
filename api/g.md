# G

`G` is the renderer engine of F2, it has following feature:

1. Hierarchical structure
2. Supports the creation, modification and destruction of the groups and shapes.
3. Animation
4. Matrix transformation.

![](../.gitbook/assets/untitled-diagram-1.png)

* Canvas is the entrance, it includes all the Group and Shape objects;
* Group can contains Group and Shape Objects
* G offers a variety of Shape types

### How to Get `G` 

```javascript
const F2 = require('@antv/f2');
const { G } = F2;

const { Canvas, Group, Shape, Matrix, Vector2 } = G;
```

### `Canvas`

Create a  `Canvas` instance.

```javascript
new Canvas(config);
```

- parameter:  `config` 

Type: Object, the configuration needed to create a canvas object, it includes the following attributes:

| Attribute | Type | Description |
| :--- | :--- | :--- |
| `el` | String/HtmlElement | The id of the canvas dom or canvas dom instance. |
| `context` | CanvasRenderingContext2D | The context of the canvas. |
| `width` | Number | Optional, width of the canvas. If it is omitted, the actual width of the canvas is used by default. |
| `height` | Number | Optional, height of the canvas. If it is omitted, the actual height of the canvas is used by default. |
| `pixelRatio` | Number | The display  pixel ratio of the canvas, `window.devicePixelRatio` is used by default. |

#### Properties

* [children](https://github.com/antvis/f2/blob/better-docs/docs/en-us-bak/api/g.md#_children)
* [destroyed](https://github.com/antvis/f2/blob/better-docs/docs/en-us-bak/api/g.md#_destroyed)

After a Canvas instance is created, we can use method `canvas.get('children')` to get properties.

| Name | Type | Description |
| :--- | :--- | :--- |
| children | Array | The elements contained in the container |
| destroyed | Boolean | Wether the canvas instance is destroyed. |

#### Methods

----------- 2018-08-09 ----------------------

* **getWidth\(\)**

```text
/**
 * Get width of the canvas
 * @return {Number} Corresponding width
 */
getWidth()	
```

**getHeight\(\)**

```text
/**
 * Get height of the canvas's corresponding dom object
 * @return {Number} Corresponding height
 */
getHeight()
```

**changeSize\(width, height\)**

```text
/**
 * Change the size of the canvas
 * @param  {Number} width  
 * @param  {Number} height 
 */
changeSize(width, height)
```

**getPointByClient\(clientX, clientY\)**

```text
/**
 * Convert the coordinate on client window to coordinate on canvas
 * @param  {Number} clientX Coordinate of x-axis on client window
 * @param  {Number} clientY Coordinate of y-axis on client window
 * @return {Object} canvas Coordinate on canvas
 */
getPointByClient(clientX, clientY)
```

**addShape\(type, config\)**

```text
/**
 * Create a shape and add it to canvas
 * @param {String} type Type of shape to create and add
 * @param {Object} config  Configuration of the shape
 * @return {Shape} The created shape instance
 */
addShape(type, config = {})
```

The `config` parameter passed in is the configuration of the shape, includes:

```text
{
  className: String, // class name specified by users
  zIndex: Number, // hierarchical index of the shape
  visible: Boolean, // wether the shape is visible
  attrs: Object // graphic attributes of the shape, different shapes have different attributes, see Shape for more details.
}
```

**addGroup\(config\)**

```text
/**
 * Create and add a group
 * @param {Object||null} cfg Configuration for group
 * @return {Group} The created group instance
 */
addGroup(config)
```

The `config` parameter passed in is the configuration for Group, includes:

```text
{
  className: String, // user specified class name
  zIndex: Number, // hierarchical index of the group
  visible: Boolean // wether the group is visible
}
```

**add\(items\)**

```text
/**
 * Add items to canvas
 * @param {Array||Group||Shape} Items can be a shape instance, a group instance, a shape array or a group array
 * @return {Canvas}  The current canvas object
 */
add(items)
```

**contain\(item\)**

```text
/**
 * Wether current canvas contains the item
 * @param  {Shape||Group} Item can be a shape instance or group instance
 * @return {Boolean} True means canvas contains the item, otherwise it's false.
 */
contain(item)
```

**sort\(\)**

```text
/**
 * Sort the elements in the container by their zIndexes, in descending order
 * @return {Canvas||Group} The container itself
 */
sort()
```

**get\(name\)**

Get the attribute from canvas by attribute name

**set\(name, value\)**

Set the attribute value for the corresponding attribute name.

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

