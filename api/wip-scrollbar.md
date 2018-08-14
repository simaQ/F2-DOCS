# ScrollBar

![](../.gitbook/assets/image%20%2835%29.png)

ScrollBar is a plugin for pan and pinch interaction, it will show the current data range.

### How to Register ScrollBar Plugin

```javascript
const F2 = require('@antv/f2/lib/index');
const ScrollBar = require('@antv/f2/lib/plugin/scroll-bar');

// register ScrollBar
F2.Chart.plugins.register(ScrollBar); 

// another way for register ScrollBar
const chart = new F2.Chart({
  id: 'canvas',
  plugins: ScrollBar
});
```

After register the ScrollBar, the method \`chart.scrollBar\(\)\` can be called.

```javascript
chart.scrollBar({
  // some configuration
});
```

### Configuration

| Name | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `mode` | String | 'x' | The direction of the scroll bar, optional value includes 'x', 'y', 'xy'. |
| `xStyle` | Object | `see below` | The style for scroll bar in  x direction:   |
| `yStyle` | Obect | see below | The style for scroll bar in y direction:  |

* `xStyle` default value:

```javascript
{
    backgroundColor: 'rgba(202, 215, 239, .2)',
    fillerColor: 'rgba(202, 215, 239, .5)',
    size: 4,
    lineCap: 'round',
    offsetX: 0,
    offsetY: 8
}
```

* `yStyle` default value:

```javascript
{
    backgroundColor: 'rgba(202, 215, 239, .2)',
    fillerColor: 'rgba(202, 215, 239, .5)',
    size: 4,
    lineCap: 'round',
    offsetX: 8,
    offsetY: 0
}
```

Example:

* [pan for line chart](https://antv.alipay.com/zh-cn/f2/3.x/demo/interaction/pan-for-line-chart.html)



