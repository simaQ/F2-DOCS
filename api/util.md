# Util

## F2.Util

## Methods

### `upperFirst([string=''])`

Converts the first character of string to upper case.

**Arguments**

* `[string='']` _\(string\)_: The string to convert.

**Returns**

_\(string\)_: Returns the converted string.

**Example**

```javascript
F2.Util.upperFirst('fred');
// => 'Fred'
 
F2.Util.upperFirst('FRED');
// => 'FRED
```

### `lowerFirst([string=''])`

Converts the first character of `string` to lower case.

**Arguments**

* `[string='']` _\(string\)_: The string to convert.

**Returns**

_\(string\)_: Returns the converted string.

**Example**

```javascript
F2.Util.lowerFirst('Fred');
// => 'fred'
 
F2.Util.lowerFirst('FRED');
// => 'fRED'
```

### `isString(value)`

Checks if `value` is classified as a `String` primitive or object.

  
**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is a string, else `false`.

**Example**

```javascript
F2.Util.isString('abc');
// => true
 
F2.Util.isString(1);
// => false
```

### `isNumber(value)`

Checks if `value` is classified as a `Number` primitive or object.

**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is a number, else `false`.

**Example**

```javascript
F2.Util.isNumber(3);
// => true

F2.Util.isNumber(Infinity);
// => true
 
F2.Util.isNumber('3');
// => false
```

### `isBoolean(value)`

Checks if `value` is classified as a boolean primitive or object.

**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is a boolean, else `false`.

**Example**

```javascript
F2.Util.isBoolean(false);
// => true
 
F2.Util.isBoolean(null);
// => false
```

### `isFunction(value)`

Checks if `value` is classified as a `Function` object.

**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is a function, else `false`.

**Example**

```javascript
F2.Util.isFunction(_);
// => true
```

### `isPlainObject(value)`

Checks if `value` is a plain object, that is, an object created by the `Object` constructor or one with a `[[Prototype]]` of `null`.

**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is a plain object, else `false`.

**Example**

```javascript
function Foo() {
  this.a = 1;
}
 
F2.Util.isPlainObject(new Foo);
// => false
 
F2.Util.isPlainObject([1, 2, 3]);
// => false
 
F2.Util.isPlainObject({ 'x': 0, 'y': 0 });
// => true
 
F2.Util.isPlainObject(Object.create(null));
// => true
```

### `isArray(value)`

Checks if `value` is classified as an `Array` object.

  
**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is an array, else `false`.

**Example**

```javascript
F2.Util.isArray([1, 2, 3]);
// => true

F2.Util.isArray('abc');
// => false
```

### `isDate(value)`

Checks if `value` is classified as a `Date` object.

  
**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is a date object, else `false`.

**Example**

```javascript
F2.Util.isDate(new Date);
// => true
 
F2.Util.isDate('Mon April 23 2012');
// => false
```

### `isNil(value)`

Checks if `value` is `null` or `undefined`.

  
**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is nullish, else `false`.

**Example**

```javascript
F2.Util.isNil(null);
// => true
 
F2.Util.isNil(void 0);
// => true
 
F2.Util.isNil(NaN);
// => false
```

### `isObject(value)`

Checks if `value` is the [language type](http://www.ecma-international.org/ecma-262/7.0/#sec-ecmascript-language-types) of `Object`. _\(e.g. arrays, functions, objects, regexes, `new Number(0)`, and `new String('')`\)_  


**Arguments**

* `value` _\(\*\)_: The value to check.

**Returns**

_\(boolean\)_: Returns `true` if `value` is an object, else `false`.

**Example**

```javascript
F2.Util.isObject({});
// => true
 
F2.Util.isObject([1, 2, 3]);
// => true
 
F2.Util.isObject(null);
// => false
```

### `mix(object, [sources])`

Assigns own enumerable string keyed properties of source objects to the destination object. Source objects are applied from left ****to right. Subsequent sources overwrite property assignments of previous sources.

**Arguments**

1. `object` _\(Object\)_: The destination object.
2. `[sources]` _\(...Object\)_: The source objects. Support for up to 3 objects

**Returns**

_\(Object\)_: Returns `object`.

**Example**

```javascript
const target = {
  a: {
    value: 1
  }
};

const source = {
  a: {
    value: 2
  },
  b: 2
};

F2.Util.mix(target, source);
// => target will be { a: { value: 2 }, b2: 2 }
```

### `deepMix(object, [sources])`

This method is like `F2.Util.mix` except that it iterates over own source properties.

**Arguments**

1. `object` _\(Object\)_: The destination object.
2. `[sources]` _\(...Object\)_: The source objects.

**Returns**

_\(Object\)_: Returns `object`.

**Example**

```javascript
const target = {
  a: {
    type: 'a'
  }
};

const source = {
  a: {
    value: 2
  },
  b: 2
};

F2.Util.mix(target, source);
// => target will be { a: { type: 'a', value: 2 }, b2: 2 }
```

### `indexOf(array, value)`

Gets the index at which the first occurrence of `value` is found in `array`.

**Arguments**

1. `array` _\(Array\)_: The array to inspect.
2. `value` _\(\*\)_: The value to search for.

**Returns**

_\(number\)_: Returns the index of the matched value, else `-1`.

**Example**

```javascript
F2.Util.indexOf([1, 2, 1, 2], 2);
// => 1
```

### `forEach(collection, [iteratee=_.identity])`

Iterates over elements of `collection` and invokes `iteratee` for each element. The iteratee is invoked with three arguments: _\(value, index\|key, collection\)_. Iteratee functions may exit iteration early by explicitly returning `false`.

**Arguments**

1. `collection` _\(Array\|Object\)_: The collection to iterate over.
2. `[iteratee=_.identity]` _\(Function\)_: The function invoked per iteration.

**Returns**

_\(\*\)_: Returns `collection`.

**Example**

```javascript
F2.Util.each([1, 2], function(value) {
  console.log(value);
});
// => Logs `1` then `2`.
 
F2.Util.each({ 'a': 1, 'b': 2 }, function(value, key) {
  console.log(key);
});
// => Logs 'a' then 'b' (iteration order is not guaranteed).

F2.Util.each([1, 2, 3, 4, 5, 6], function(value) {
  console.log(value);
  if (value === 4) {
    return false;
  }
});
// => Logs `1`,`2`,`3`,`4`.
```

### `getPixelRatio()`

Get the current pixel ratio.

**Returns**

_\(number\)_: Returns the current pixel ratio.

### `getRelativePosition(point, canvas)`

Convert the position of the mouse to the relative coordinate of the canvas.

**Arguments**

1. `point` _\(Object\)_: the point need to convert.
2. `canvas` _\(Canvas\)_: the canvas instance of chart.

**Returns**

_\(object\)_: Returns the relative coordinate of the canvas.

**Example**

```javascript
const mousePoint = {
  x: 10,
  y:39
};
const canvas = chart.get('canvas');
const canvasPoint = F2.Util.getRelativePosition(mousePoint, canvas);
// => { x: , y: }
```

