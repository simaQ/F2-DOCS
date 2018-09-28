# ScrollBar

![](../../.gitbook/assets/image%20%2839%29.png)

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

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Default</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>mode</code>
      </td>
      <td style="text-align:left">String</td>
      <td style="text-align:left">'x'</td>
      <td style="text-align:left">The direction of the scroll bar, optional value includes 'x', 'y', 'xy'.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>xStyle</code>
      </td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left"><code>see below</code>
      </td>
      <td style="text-align:left">
        <p>The style for scroll bar in x direction:</p>
        <ul>
          <li><code>backgroundColor</code>: the background color for scroll bar</li>
          <li><code>fillerColor</code>: the color for range bar</li>
          <li><code>size</code>: the size of scroll bar</li>
          <li><code>lineCap</code>: determines how the end points in a line are drawn</li>
          <li><code>offsetX</code>: the offset value of scroll bar in x-axis direction</li>
          <li><code>offsetY</code>: the offset value of scroll bar in y-axis direction</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>yStyle</code>
      </td>
      <td style="text-align:left">Obect</td>
      <td style="text-align:left">see below</td>
      <td style="text-align:left">
        <p>The style for scroll bar in y direction:</p>
        <ul>
          <li><code>backgroundColor</code>: the background color for scroll bar</li>
          <li><code>fillerColor</code>: the color for range bar</li>
          <li><code>size</code>: the size of scroll bar</li>
          <li><code>lineCap</code>: determines how the end points in a line are drawn</li>
          <li><code>offsetX</code>: the offset value of scroll bar in x-axis direction</li>
          <li><code>offsetY</code>: the offset value of scroll bar in y-axis direction</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>* `xStyle` default value:

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



