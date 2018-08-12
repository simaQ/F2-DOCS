# Vector2

## F2.G.Vector2 {#f-2-g-matrix}

`Vector2` provides operations for 2-dimensinal vectors.

**Methods**

### `create()`

Create a new 2-dimensional vector, \[0, 0\] is returned.

**Returns:** Type Array

### `length(v)`

The length of the vector.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | Array | vector to calculate length |

**Returns:** Type Number

### `normalize(out, v)`

Normalize the vector.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | stores the normalization result |
| `v` | Array | vector to normalize |

**Returns:** Type Array

### `add(out, v1, v2)`

Add the two vectors v1, v2.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | stores the result |
| `v1` | Array | vector v1 to add |
| `v2` | Array | vector v2 to add |

**Returns:** Type Array

### `sub(out, v1, v2)`

Subtraction of the two vectors v1, v2.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | stores the result |
| `v1` | Array | vector v1 to subtraction |
| `v2` | Array | vector v2 to subtraction |

**Returns:** Type Array

### `scale(out, v, s)`

Scale the vector.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | stores the result |
| `v` | Array | vector to scale |
| `s` | Array | scale vector \[ sx, sy \] |

**Returns:** Type Array

### `dot(v1, v2)`

Calculates the dot product of two vec2's.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v1` | Array | the first operand |
| `v2` | Array | the second operand |

**Returns:** Type Number

### `direction(v1, v2)`

Calculate the direction formed by two vectors v1, v2.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v1` | Array | the first operand |
| `v2` | Array | the second operand |

**Returns:** Type Boolean

### `angleTo(v1, v2, direction)`

Calculate the angle between the two vectors v1, v2.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v1` | Array | the first operand |
| `v2` | Array | the second operand |
| `direction` | Boolean | the direction of two vector2's |

**Returns:** Type Number

### `zero(v)`

Determine if vector v is 0 vector.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | Array | the vector |

**Returns:** Type Boolean

### `clone(v)`

Creates a new vec2 initialized with values from an existing vector.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `v` | Array | vector to clone |

**Returns:** Type Array

### `min(out, v1, v2)`

Returns the minimum of two vec2's.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | store the result |
| `v1` | Array | the first operand |
| `v2` | Array | the second operand |

**Returns:** Type Array

### `max(out, v1, v2)`

Returns the maximum of two vec2's.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | store the result |
| `v1` | Array | the first operand |
| `v2` | Array | the second operand |

**Returns:** Type Array

### `transformMat2d(out, v, m)`

Transforms the vector with a matrix.

**Parameters:**

| Name | Type | Description |
| :--- | :--- | :--- |
| `out` | Array | store the result |
| `v` | Array | the vector to transform |
| `m` | Array | matrix to transform with |

**Returns:** Type Array

