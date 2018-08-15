# Scale

Scales are a convenient abstraction for a fundamental task in visualization: mapping a dimension of abstract data to a visual representation. Different data types have different type of scales.

* For continuous quantitative data, you typically want **a linear scale**. 
* For time series data, **a timeCat scale**
* For discrete ordinal \(ordered\) or categorical \(unordered\) data, **a cat scale** specifies an explicit mapping from a set of data values to a corresponding set of visual attributes \(such as colors, shapes\). 
* **A identity scale** is for constant.

Scales have no intrinsic visual representation. However, most scales can **generate** and **format ticks** for reference marks to aid in the construction of axes.

F2 will generate scales for the data automatically. But still offers two methods to configure.Here is an example：

```javascript
const data = [
  { State: 'WY', Age: 'Under 5 Years', Population: 25635 },
  { State: 'WY', Age: '5 to 13 Years', Population: 1890 },
  { State: 'WY', Age: '14 to 17 Years', Population: 9314 },
  { State: 'DC', Age: 'Under 5 Years', Population: 30352 },
  { State: 'DC', Age: '5 to 13 Years', Population: 20439 },
  { State: 'DC', Age: '14 to 17 Years', Population: 10225 },
  { State: 'VT', Age: 'Under 5 Years', Population: 38253 },
  { State: 'VT', Age: '5 to 13 Years', Population: 42538 },
  { State: 'VT', Age: '14 to 17 Years', Population: 15757 },
  { State: 'ND', Age: 'Under 5 Years', Population: 51896 },
  { State: 'ND', Age: '5 to 13 Years', Population: 67358 },
  { State: 'ND', Age: '14 to 17 Years', Population: 18794 },
  { State: 'AK', Age: 'Under 5 Years', Population: 72083 },
  { State: 'AK', Age: '5 to 13 Years', Population: 85640 },
  { State: 'AK', Age: '14 to 17 Years', Population: 22153 }
];
```

 In the data,  'State' is a cat scale, 'Age' is a cat scale and 'Population' is a linear scale. Now we can set the maximum and minimum values ​​of `Population`

```javascript
chart.source(data, {
  Population: {
    min: 1000,
    max: 100000
  }
});
```

Or

```javascript
chart.scale('Population', {
  min: 1000,
  max: 100000
});
```

### Common C**onfiguration**

```javascript
chart.scale('fieldName', {
  // configurations
})
```

The **common configuration** properties of  scale are described below：

| **Name** | **Type** | **Default**  | **Description**  |
| :--- | :--- | :--- | :--- |
| `type` | String | null | Specify the type of the scale, supported scale types are: `identify`, `linear`, `cat`, `timeCat`. |
| `formatter` | `Function` | null | It is used to format the text of the scale point in the axis and will affect the display of the data on axis, legend, and tooltip. |
| `range` | Array | \[ 0, 1 \] | Used to control the drawing range of data on the coordinate, in the format of \[ min, max \], and both min and max are data in the range 0 to 1. |
| `alias` | String | null | Alias of the data field, if it is set, we will display the `alias` value in the chart. |
| `tickCount` | Number |  | Number of tick points in the axis, different scale types have different default values. |
| `ticks` | Array | null | Used to specify the scale text on the axis. When the user sets ticks, it will display according to ticks. |
| `values` | Array | null | Set the data collection of the scale, the default will automatically read from the data source, see **Cat scale** for detail usage. |

```javascript
chart.source(data, {
  value: {
    min: 0,
    ticks: [ 0, 500, 1000, 1300, 1600 ]
  }
});
```

![](../.gitbook/assets/image%20%2822%29.png)

Except for the above general configuration properties, different scale types have different configuration items.

### Linear

| **Name** | **Type** | **Default** | **Description** |
| :--- | :--- | :--- | :--- |
| `nice` | Boolean | true | used to optimize the range of values so that ticks on axes are evenly distributed. For example, the range \[ 3, 97 \] will be optimized to \[ 0, 100 \], if `nice` is set to be `true`. |
| `min` | Number |  | the minimum value of the data set |
| `max` | Number |  | the maximum value of the data set |
| `tickInterval` | Number |  | Used to specify the distance between the scale points of the axis, which is the difference between the original data. Note that`tickCount`and`tickInterval` **cannot both be defined**. |

![tickInterval explanation](../.gitbook/assets/group-3%20%281%29.png)

```javascript
  const data = [
    { year: '1951 年', sales: 38 },
    { year: '1952 年', sales: 52 },
    { year: '1956 年', sales: 61 },
    { year: '1957 年', sales: 145 },
    { year: '1958 年', sales: 48 },
    { year: '1959 年', sales: 38 },
    { year: '1960 年', sales: 38 },
    { year: '1962 年', sales: 38 },
  ];
  const chart = new F2.Chart({
    id: 'mountNode',
    pixelRatio: window.devicePixelRatio
  });

  chart.source(data, {
    sales: {
      tickInterval: 80 // set tickInterval
    }
  });
  chart.interval().position('year*sales');
  chart.render();
```

### Cat

Cat scale has no other configuration items. But we will introduce the usage of `values` ​​here.

**1. When you need to specify the display order of the categorical data.**

        We use the following data to draw a bar chart:

![](../.gitbook/assets/image%20%2835%29.png)

```javascript
  const data = [
    { name: 'A', value: 38 },
    { name: 'B', value: 52 },
    { name: 'C', value: 61 },
  ];
  const chart = new F2.Chart({
    id: 'mountNode',
    pixelRatio: window.devicePixelRatio
  });

  chart.source(data);
  chart.interval().position('name*value').color('name');
  chart.render();
```

Now we can change the display order of the bar by setting `values`, including legend:

```javascript
chart.source(data, {
  name: {
    type: 'cat', // In fact, you can also do not need to set, F2 will automatically recognize
    values: [ 'C', 'B', 'A' ]
  }
});
```

After set this, the bar chart will be rendered as follow:

![](../.gitbook/assets/image%20%289%29.png)

**2. Convert index values ​​to corresponding data. But the original value of the field must be indexed value, start from 0.**

```javascript
  const data = [
    { month: 0, tem: 7, city: 'Tokyo' },
    { month: 1, tem: 6.9, city: 'Tokyo' },
    { month: 2, tem: 9.5, city: 'Tokyo' },
    { month: 3, tem: 14.5, city: 'Tokyo' },
    { month: 4, tem: 18.2, city: 'Tokyo' },
    { month: 5, tem: 21.5, city: 'Tokyo' },
    { month: 6, tem: 25.2, city: 'Tokyo' }
  ];
  const chart = new F2.Chart({
    id: 'mountNode',
    width: 375,
    height: 260,
    pixelRatio: window.devicePixelRatio
  });
  chart.source(data, {
    month: {
      type: 'cat',
      values: ['Jan.', 'Feb.', 'Mar.', 'Apr.', 'May.', 'Jun.', 'Jul.']
    }
  });
  chart.interval().position('month*tem');
  chart.render();
```

![](../.gitbook/assets/image%20%2827%29.png)

**3. Control the display of data.**

Case 1: we just have 3 items in data, but we can set 10 ticks on the axis:

```javascript
  const data = [
    { name: 'A', value: 38 },
    { name: 'B', value: 52 },
    { name: 'C', value: 61 },
  ];
  const chart = new F2.Chart({
    id: 'mountNode',
    pixelRatio: window.devicePixelRatio
  });

  chart.source(data, {
    name: {
      values: [ 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K' ]
    }
  });
  chart.interval().position('name*value');
  chart.render();
```

![](../.gitbook/assets/image%20%2825%29.png)

Case 2: we just have 3 items in data, but we can just want to display one:

```javascript
  const data = [
    { name: 'A', value: 38 },
    { name: 'B', value: 52 },
    { name: 'C', value: 61 },
  ];
  const chart = new F2.Chart({
    id: 'mountNode',
    pixelRatio: window.devicePixelRatio
  });

  chart.source(data, {
    name: {
      values: [ 'B' ]
    }
  });
  chart.interval().position('name*value');
  chart.render();
```

![](../.gitbook/assets/image%20%2821%29.png)

### TimeCat

For time series data, we will sort the data set by default.

| Name | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `mask` | String | 'YYYY-MM-DD' | To Format the display of date, we use [fecha](https://github.com/taylorhakes/fecha) lib, the format tokens can see [here](https://github.com/taylorhakes/fecha#formatting-tokens) |

**NOTE: `mask` and `formmater` cannot both be specified, if both are defined, the `formatter` attribute will be used in priority**.

