# Getting Started

Let's get started using F2!

First, we need to have a canvas in our page.

```markup
<canvas id="myChart"></canvas>
```

Now that we have a canvas we can use, we need to include F2 in our page.

```markup
<!-- online -->
<script src="https://gw.alipayobjects.com/os/antv/assets/f2/3.1.15/f2.js"></script>
```

Now, we can create a chart. We add a script to our page:

```javascript
const data = [
  { year: '1951', sales: 38 },
  { year: '1952', sales: 52 },
  { year: '1956', sales: 61 },
  { year: '1957', sales: 145 },
  { year: '1958', sales: 48 },
  { year: '1959', sales: 38 },
  { year: '1960', sales: 38 },
  { year: '1962', sales: 38 }
];
const chart = new F2.Chart({
  id: 'myChart',
  width: 375,
  height: 265,
  pixelRatio: window.devicePixelRatio
});

chart.source(data);
chart.interval().position('year*sales');
chart.render();
```

A bar chart is done!

![](../.gitbook/assets/image%20%2810%29.png)

It's that easy to get started using F2! From here you can explore more options that can help you customize your charts with scales, tooltip, axis, guides, legends and much more.

There are many examples of F2 that are available in the AntV [demos](https://antv.alipay.com/zh-cn/f2/3.x/demo/index.html). You also can scan the QR code below to experience our demos on you phone.

![](../.gitbook/assets/image%20%284%29.png)

