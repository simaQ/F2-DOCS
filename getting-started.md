# Getting Started

Let's get started using F2!

First, we need to have a canvas in our page.

```markup
<canvas id="myChart"></canvas>
```

Now that we have a canvas we can use, we need to include F2 in our page.

```markup
<!-- online -->
<script src="https://gw.alipayobjects.com/os/antv/assets/f2/3.2.3/f2.js"></script>
```

Now, we can create a chart:

* **Instantiate the `Chart` class**. To do this, we need to pass in the node, id, or 2d context of the canvas of where we want to draw the chart.

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

* **then relate with data**. The data below shows the different types of game's sales.

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

* **Draw the bar chart.**

```javascript
chart.interval().position('genre*sold').color('genre');
```

* **Render!** And you must call it.

```javascript
chart.render();
```

![](.gitbook/assets/image%20%2819%29.png)

It's that easy to get started using F2! From here you can explore more options that can help you customize your charts with scales, tooltip, axis, guides, legends and much more.

There are many examples of F2 that are available in the AntV [demos](https://antv.alipay.com/zh-cn/f2/3.x/demo/index.html). You also can scan the QR code below to experience our demos on you phone.

![](.gitbook/assets/image%20%287%29.png)

