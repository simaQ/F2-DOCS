# Require on demand

F2 is designed for mobile visualization, therefore the package size is very important. F2 has modular structure provides  package size optimization. 

### How to require on demand

* STEP 1: Install F2
* STEP 2: Require core library of F2 \(**must be done\)**
* STEP 3: Require modules what you want

#### Install F2

```bash
$ npm install @antv/f2
```

#### Import core library of F2

```javascript
const Core = require('@antv/f2/lib/core');
```

This library contains the core processing logic of grammar of graphics, which contains the following:

* `Chart`: Chart Class
* `Geom`: The parent class of geometry, only contains the core processing of data, without any implementation of specific geometries such as line, area, bar i.e.
* `Attr`: Attributes classes of charts, such as position, color, shape and size.
* `Scale`: Only container the Linear, Cat and Identity these three basic types.
* `Coord`: Only includes Cartesian coordinate.
* `Axis`: Only contains the axes of Cartesian coordinate.
* `G`: Rendering engine.

#### Require the demanded modules

The dynamically loadable modules are the following:

**Geometry**

Geometry module, used for drawing a specific chart:

* require all of the geometries

```javascript
require('@antv/f2/lib/geom/'); // require all the charts
```

* require specific geometry

```javascript
require('@antv/f2/lib/geom/line'); // only line chart is required
require('@antv/f2/lib/geom/area'); // only the area chart is required
require('@antv/f2/lib/geom/interval'); // only the histogram is required
require('@antv/f2/lib/geom/path'); // only the path map is required
require('@antv/f2/lib/geom/point'); // only the dot chart is required
require('@antv/f2/lib/geom/polygon'); // only the color map is required
require('@antv/f2/lib/geom/schema'); // only the box chart, stock chart are required
```

**Coordinate**

```javascript
require('@antv/f2/lib/coord/polar'); // polar coordinate

require('@antv/f2/lib/coord/cartesian'); // Cartesian coordinate（already included in the core library）
```

**Axis**

```javascript
require('@antv/f2/lib/component/axis/circle'); // Arc axis for polar coordinate

require('@antv/f2/lib/component/axis/line'); // Axes for Cartesian coordinate（already included in the core library）
```

**Adjust**

* require all types of adjust

```javascript
require('@antv/f2/lib/geom/adjust/');
```

* require specific adjust type

```javascript
require('@antv/f2/lib/geom/adjust/dodge'); // only grouped adjust is required
require('@antv/f2/lib/geom/adjust/stack'); // only stacked adjust is required
```

**Scale**

```javascript
require('@antv/f2/lib/scale/time-cat'); // timeCat is required
```

**Animation**

**The animation module serves as a plugin for chart, therefore you need to register the module on chart after it is loaded.**

```javascript
const Animation = require('@antv/f2/lib/animation/detail');
Chart.plugins.register(Animation); // Global registration，you can also just register it
```

**Guide**

Guide also serves as an plugin for chart. When using Guide, users can dynamically select the specific guide component to use, and then register the corresponding plug-in to the chart.

```javascript
// Step 1: require the demanded guide componments
require('@antv/f2/lib/component/guide'); // require all guide components

// Or just require the specific guide component you want
require('@antv/f2/lib/component/guide/arc'); // only Guide.Arc is required
require('@antv/f2/lib/component/guide/html'); // only Guide.Html is required
require('@antv/f2/lib/component/guide/text'); // only Guide.Text is required
require('@antv/f2/lib/component/guide/rect'); // only Guide.Rect is required
require('@antv/f2/lib/component/guide/line'); // only Guide.Line is required
require('@antv/f2/lib/component/guide/tag'); // only Guide.Tag is required
require('@antv/f2/lib/component/guide/region-filter'); // only Guide.RegionFilter is required
require('@antv/f2/lib/component/guide/point'); // only Guide.Point is required

// Step 2: require the Guide plugin
const Guide = require('@antv/f2/lib/plugin/guide');

// Step 3： register Guide
Chart.plugins.register(Guide); // Global registration，you can also just register it
```

**Tooltip**

Tooltip also serves as an plugin for chart.

```javascript
// Step 1：require tooltip
const Tooltip = require('@antv/f2/lib/plugin/tooltip');
// Step 2：register Tooltip
Chart.plugins.register(Tooltip); // Global registration，you can also just register it
```

**Legend**

Legend also serves as an plugin for chart.

```javascript
// Step 1: require Legend
const Legend = require('@antv/f2/lib/plugin/legend');
// Step 2: register Legend
Chart.plugins.register(Legend); // Global registration，you can also just register it
```

**Interaction**

* require all of the interactions

```javascript
require('@antv/f2/lib/interaction/');
```

* require the specific interaction

```javascript
require('@antv/f2/lib/interaction/pie-select'); // selection for pie chart

require('@antv/f2/lib/interaction/interval-select');  // selection for bar chart

require('@antv/f2/lib/interaction/pan'); // chart pan

require('@antv/f2/lib/interaction/pinch'); // chart pinch
```

**ScrollBar**

ScrollBar also serves as a plugin for chart.

```javascript
const ScrollBar = require('@sntv/f2/lib/plugin/scroll-bar');
F2.Chart.plugins.register(ScrollBar);
```

### Example

If you only need to draw a pie chart without animation:

```javascript
const F2 = require('@antv/f2/lib/core'); // must be required
require('@antv/f2/lib/geom/interval'); // require interval geometry
require('@antv/f2/lib/coord/polar'); // require polar coordinate
require('@antv/f2/lib/geom/adjust/stack'); // requre the type of data adjust
```

### Visualization tool

For convenience, we provide UI-based require-on-demand packaging tool to help developers download the required charts and components. The usage is as follows:

```bash
# Go to the root directory of the F2 project and run:
$ npm run bundler
```

In the interface that appears, check the required module, and finally package and download it.

![](https://gw.alipayobjects.com/zos/rmsportal/RmUwBPLSWIbecmKEgoSw.png)

