# Your First Chart

### Usage

F2 can be used with ES6 modules, plain JavaScript and module loaders.

### Creating a Chart

To create a chart, we need to instantiate the `Chart` class. To do this, we need to pass in the node, id, or 2d context of the canvas of where we want to draw the chart. Here's an example.

* STEP 1: Create a canvas node

```markup
<canvas id="myChart"></canvas>
```

* STEP 2: Instantiate the `Chart` class

```javascript
// Any of the following formats may be used, just choose one!
const chart = new F2.Chart({
  id: 'myChart', // pass node's id
  width: 375,
  height: 260,
  pixelRatio: window.devicePixelRatio
});

const chart = new F2.Chart({
  el: document.getElementById('myChart'), // or pass node
  width: 375,
  height: 260,
  pixelRatio: window.devicePixelRatio
});

const chart = new F2.Chart({
  context: document.getElementById('myChart').getContext('2d'), // or pass 2d context of the canvas 
  width: 375,
  height: 260,
  pixelRatio: window.devicePixelRatio
});
```

* STEP 3: Load data. The date below shows the different types of game's sales.

```javascript
const data = [ 
  { genre: 'Sports', sold: 275 },
  { genre: 'Strategy', sold: 115 },
  { genre: 'Action', sold: 120 },
  { genre: 'Shooter', sold: 350 },
  { genre: 'Other', sold: 150 },
];

chart.source(data); // load the data
```

* STEP 4: Draw the bar chart.

```javascript
chart.interval().position('genre*sold').color('genre');
```

* STEP 5: Render.

```javascript
chart.render();
```

![](../.gitbook/assets/image%20%288%29.png)

