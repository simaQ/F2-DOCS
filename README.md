---
description: Introduction to F2
---

# F2

[![](https://img.shields.io/travis/antvis/f2.svg)](https://travis-ci.org/antvis/f2) ![](https://img.shields.io/badge/language-javascript-red.svg) ![](https://img.shields.io/badge/license-MIT-000000.svg)

[![npm package](https://img.shields.io/npm/v/@antv/f2.svg)](https://www.npmjs.com/package/@antv/f2) [![NPM downloads](http://img.shields.io/npm/dm/@antv/f2.svg)](https://npmjs.org/package/@antv/f2) [![Percentage of issues still open](http://isitmaintained.com/badge/open/antvis/f2.svg)](http://isitmaintained.com/project/antvis/f2)

F2 is a powerful **mobile** data visualization solution, pure in javascript. F2 is based on [**the grammar of graphics**](https://www.cs.uic.edu/~wilkinson/TheGrammarOfGraphics/GOG.html), and it is light-weighted, high-performance and easily expandable. Also, F2 charts are well designed for mobile.

TODO: website and demos' page

TODO:  show some charts images here

**Special thanks to** [**Leland Wilkinson**](https://en.wikipedia.org/wiki/Leland_Wilkinson)**, the author of** [_**The Grammar Of Graphics**_](https://www.cs.uic.edu/~wilkinson/TheGrammarOfGraphics/GOG.html)**, whose book served as the foundation for F2 and G2.**

### Features

* **Elegant user experience**: Designed for mobile experience
* **Flexible**: Customizable shapes and animations, flexible charting components, infinite creativity
* **High performance**: F2 pursues the ultimate performance for drawing, lots of optimization have been done for mobile devices
* **Light-weighed**: F2 maintains a compact code size while supporting more than 45 kinds of charts

### Other runtime support

* F2 on **Node.js** ：[https://antv.alipay.com/zh-cn/f2/3.x/tutorial/node-env.html](https://antv.alipay.com/zh-cn/f2/3.x/tutorial/node-env.html)
* TODO: other runtime

### Installation

```bash
$ npm install @antv/f2
```

### Getting Started

![](.gitbook/assets/image%20%2828%29.png)

```markup
<canvas id="c1"></canvas>
```

```javascript
import F2 from '@antv/f2';

const data = [
  { year: '1951', sales: 38 },
  { year: '1952', sales: 52 },
  { year: '1956', sales: 61 },
  { year: '1957', sales: 145 },
  { year: '1958', sales: 48 },
  { year: '1959', sales: 38 },
  { year: '1960', sales: 38 },
  { year: '1962', sales: 38 },
];
const chart = new F2.Chart({
  id: 'mountNode',
  width: 375,
  height: 265,
  pixelRatio: window.devicePixelRatio
});
chart.source(data);
chart.interval().position('year*sales');
chart.render();
```

### Development

```bash
$ npm install

# run test case
$ npm run test-live

# build watching file changes and run demos
$ npm run dev

# run demos
$ npm run demos

# run pack
$ npm run bundler
```

### How to Contribute

Please let us know how can we help. Do check out [issues](https://github.com/antvis/f2/issues) for bug reports or suggestions first.

To become a contributor, please follow our [contributing guide](https://github.com/antvis/f2/blob/master/CONTRIBUTING.md).

### License

[MIT license](./LICENSE).

