# Data

All charts require data. F2 charts require data to be an array of objects, just like this:

```javascript
const data = [
  { year: 2010, sales: 40 },
  { year: 2011, sales: 30 },
  { year: 2012, sales: 50 },
  { year: 2013, sales: 60 },
  { year: 2014, sales: 70 },
  { year: 2015, sales: 80 },
  { year: 2016, sales: 80 },
  { year: 2017, sales: 90 },
  { year: 2018, sales: 120 }
];
```

After instantiate chart, pass in the data by:

```javascript
chart.source(data);
```

When data changes, call the following method:

```javascript
chart.changeData(data);
```

###  Data for some charts

#### Pie Chart

If you want to draw a pie chart, there should be a constant field in data, just like the **`a`** field in the following dataset:

```javascript
const data = [
  { name: '芳华', percent: 0.4, a: '1' },
  { name: '妖猫传', percent: 0.2, a: '1' },
  { name: '机器之血', percent: 0.18, a: '1' },
  { name: '心理罪', percent: 0.15, a: '1' },
  { name: '寻梦环游记', percent: 0.05, a: '1' },
  { name: '其他', percent: 0.02, a: '1' }
];
```

See pie chart [demo](https://antv.alipay.com/zh-cn/f2/3.x/demo/pie/pie.html).

#### Column Range Chart

If you want to draw a column range chart, the y axis' data should be an array type, just like **`y`** field in the following data:

```javascript
const data = [
  { x: '分类一', y: [ 76, 100 ] },
  { x: '分类二', y: [ 56, 108 ] },
  { x: '分类三', y: [ 38, 129 ] },
  { x: '分类四', y: [ 58, 155 ] },
  { x: '分类五', y: [ 45, 120 ] },
  { x: '分类六', y: [ 23, 99 ] },
  { x: '分类七', y: [ 18, 56 ] },
  { x: '分类八', y: [ 18, 34 ] },
];
```

See column range chart [demo](https://antv.alipay.com/zh-cn/f2/3.x/demo/bar/range-column.html).

#### Candlestick Chart

If you want to draw a candlestick chart, the y axis' data should be an array type, just like **`range`** field in the following data:

```javascript
const data = [
  { time: '2015-09-02', range: [ 6.2, 5.99, 6.84, 5.98 ], trend:1 },
  { time: '2015-09-07', range: [ 6.19, 6.2, 6.45, 6.09 ], trend: 0 },
  { time: '2015-09-08', range: [ 6.26, 6.64, 6.7, 6.01 ], trend: 0 },
  { time: '2015-09-09', range: [ 6.76, 6.93, 7.03, 6.65 ], trend: 0 },
  { time: '2015-09-10', range: [ 6.7, 6.86, 7.17, 6.65 ], trend: 0 },
  { time: '2015-09-11', range: [ 6.87, 6.81, 7.01, 6.68 ], trend: 1 }
];
```

See candlestick chart [demo](https://antv.alipay.com/zh-cn/f2/3.x/demo/other/candle.html).



