# Matrix

## F2.G.Matrix

`Matrix` provides operations for 2x3 matrix. 

**Methods**

### `multiply(m1, m2)`

Multiply the two matrix.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `m1` | Array | left matrix |
| `m2` | Array | right matrix |

**Returns:**  Type: Array

### `scale(out, m, v)`

Scale operation.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array |  the result of the scale operation |
| `m` | Array | the matrix to scale |
| `v` | Array | scale vector \[sx, sy\] |

**Returns:**  Type: Array

### rotate\(out, m, radian\)

Rotation operation.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array |  the result of the rotate operation |
| `m` | Array | the matrix to rotate |
| `radian` | Number | rotation radian |

**Returns:**  Type: Array

### `translate(out, m, v)`

Translation operation.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array |  the result of the translation operation |
| `m` | Array | the matrix to translate |
| `radian` | Number | translation vector \[ x, y \] |

**Returns:**  Type: Array

### transform\(m, actions\)

Perform translation, rotation and scale operations. All operations are configured and stored in actions, the supported operations in actions attribute are: 't' \(translate\), 's' \(scale\), 'r' \(rotate\). Operations can be combined in any combination. For example:  


```javascript
[
  [ 't', x, y ], // t for translate, x for offset on x-axis direction, y for offset in y-axis direction
  [ 's', sx, sy ], // s for scale, sx for scale on x-axis direction, sy for scale on y-axis direction
  [ 'r', radian] // r for rotate，radian for the radians of the rotation
]
```

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `m` | Array | the matrix to transform |
| `actions` | Array | operation setting |

**Returns:**  Type: Array  






