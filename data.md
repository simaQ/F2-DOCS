# Data

F2's standard format of data is JSON Array.

### Data format

The data format that F2 receives is very simple: a standard JSON array where each array element is a standard JSON object.

Example:

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

### How to load data

After the chart is created, data can be loaded.

```text
chart.source(data);
```

