# Group

### `Group`

```javascript
new Group(config);
```

Group constructor. Groups are used to contain shapes or other groups.

* `config`: Object or Null, if `config` is an object, it can contain the following attributes:

| Name | Type | Description |
| :--- | :--- | :--- |
| `zIndex` | Number | z-index for group, used to adjust the drawing order. |
| `visible` | Boolean | visible or hidden |
| `className` | String | mark of the object, specified by users |

Example:

```javascript
const group = new F2.G.Group();
```

#### Methods

####  **getChildren\(\)**

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

**isVisible\(\)**

```javascript
/**
 * Wether the current group object is visible.
 * @return {Boolean}
 */
isVisible()
```

**isGroup\(\)**

```javascript
/**
 * If true, the current object is a group object.
 * @return {Boolean}
 */
isGroup()
```

**addShape\(type, config\)**

```javascript
/**
 * Create a shape and add it to group
 * @param {String} type Type of shape to create and add
 * @param {Object} config  Configuration of the shape
 * @return {Shape}
 */
addShape(type, config = {})
```

The `config` parameter passed in is the configuration of the shape, includes:

```javascript
{
  className: {String}, // class name specified by users
  zIndex: {Number}, // z-index of the shape
  visible: {Boolean}, // wether the shape is visible
  attrs: {Object} // graphic attributes of the shape, different shapes have different attributes, see Shape for more details.
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
  className: {String}, // user specified class name
  zIndex: {Number}, // hierarchical index of the group
  visible: Boolean // wether the group is visible
}
```

**add\(items\)**

```javascript
/**
 * Add elements to group
 * @param {Array||Group||Shape} Items can be a shape instance, a group instance, a shape array or a group array
 * @return {Group}
 */
add(items)
```

**contain\(item\)**

```javascript
/**
 * Wether current grop contains the item
 * @param  {Shape||Group} Item can be a shape instance or group instance
 * @return {Boolean}
 */
contain(item)
```

**sort\(\)**

```javascript
/**
 * Sort the elements in the container by their zIndex, in descending order
 * @return {Group}
 */
sort()
```

**getBBox\(\)**

```javascript
/**
 * Get the minimum bounding box of the current group
 * @return {Object}
 */
getBBox()
```

The bounding box returned has the following structure:

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
 * @return {Group || Canvas} The parent element of the current object, may be a group object or canvas object
 */
getParent()
```

**show\(\)**

```javascript
/**
 * Display the group
 */
show()
```

**hide\(\)**

```javascript
/**
 * Hide the group
 */
hide()
```

**get\(name\)**

```javascript
/**
 * Get the attribute from group by attribute name
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

**clear\(\)**

```javascript
/**
  * Clear all the elements
  * @return {Group} The container itself
  */
clear() 
```

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

