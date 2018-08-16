# Changelog

### **3.2.0 \(2018-08-16\)**

#### **New Features**

* add interactions for chart, includes: 'pie-select', 'interval-select', 'pan' and 'pinch'.
* add chart.guide\(\).regionFilter\({}\).
* add chart.guide\(\).point\({}\).
* add scrollBar plugin for pan and pinch interaction. \([08b18c38](https://github.com/antvis/f2/commit/08b18c388242bb19fa38831942c1c8a8aa86834a)\)
* add guide.repaint\(\) method. \([e626def6](https://github.com/antvis/f2/commit/e626def63607f86b2ef2cfb6ebd12defa1f7a570)\)
* Guide component add `limitInPlot` property to limit guide draw in chart plot area. Closed [\#203](https://github.com/antvis/f2/pull/203) \([05bf832c](https://github.com/antvis/f2/commit/05bf832c195338973bc76104dfe7480708f42ed5)\)
* add show\(\) and hide\(\) methods for `Geometry` instance. \([652ce741](https://github.com/antvis/f2/commit/652ce741d44087bec8a00de79608ec2913ed34b8)\)
* add `limitInPlot` property for chart, to limit the drawing area of geometrys. \([74e53218](https://github.com/antvis/f2/commit/74e53218e9bc970feeab5e79ffb62310c31444cf)\)
* the drawing order of geoms can be decided by scale values. \([1f2993e6](https://github.com/antvis/f2/commit/1f2993e6ba818d795108522b56f9d5949a8b7d2c)\)

#### **Bug Fixes**

* Fix problem with element zIndex in tooltip. Closed [\#216](https://github.com/antvis/f2/pull/216) \([2b83bb83](https://github.com/antvis/f2/commit/2b83bb83ab881b9ab073998e59355309126f00c6)\)
* fix axis label animation. \([8b1f7b19](https://github.com/antvis/f2/commit/8b1f7b19d19c3a62af7d7033f7d0fc4154251429)\)
* when x scale is category, do not need to sort data. Closed [\#202](https://github.com/antvis/f2/pull/202). \([184f3937](https://github.com/antvis/f2/commit/184f3937822f7b05ac689ec44e634a10d1c2105e)\)
* The position of the canvas in the parent container needs to be considered when calculating the Guide.Html position. \([512e025d](https://github.com/antvis/f2/commit/512e025d6d60a4e9837722b6585b7ac296a73a9e)\)
* timeCat type scale setting values caused an error in chart drawing. \([d1391bd3](https://github.com/antvis/f2/commit/d1391bd33440e5d817e984a333da268bba8e6a27)\)

#### **Chores**

* remove index-common and update index. \([38e89096](https://github.com/antvis/f2/commit/38e89096c8a7e96e086d62efdf8bf43d27812ff5)\)
* configuration update. \([45333936](https://github.com/antvis/f2/commit/453339369509c439ad024dba18670e61af0b260f)\)
* handle the compatibility of Element.prototype.remove\(\). \([97215b9a](https://github.com/antvis/f2/commit/97215b9ad0c9ea2cf723f3b00a63e5f9fe457b6d)\)
* require from lib folder. \([b06507b1](https://github.com/antvis/f2/commit/b06507b1d75d77c73814e3ce8fd649214e564de9)\)
* use public package `@antv/scale` and `@antv/adjust`. \([84e9a90f](https://github.com/antvis/f2/commit/84e9a90f8614967abab393ac287af9142eea8ce2)\)
* use public module `@antv/attr`. \([357679bc](https://github.com/antvis/f2/commit/357679bc298f998d20ef0bfda3250dbc868a64a8)\)
* use @antv/util as utility methods. \([c619b66b](https://github.com/antvis/f2/commit/c619b66b1dffef5cea94cb1bbd7f3eb4d36192fa)\)

#### **Other Changes**

* optimize the process of data. \([6f00f7ec](https://github.com/antvis/f2/commit/6f00f7ecb7e820420502bd7f157a5a09c0f8adb0)\)
* add 16ms delay for canvas draw. \([012c9fcc](https://github.com/antvis/f2/commit/012c9fcc51a0fae11eca797741e941df31aed89d)\)

#### **Tests**

* add test cases for all of the interactions. \([77ffa62c](https://github.com/antvis/f2/commit/77ffa62c27e2287931479a8d6ac10744aaf17c8c)\)
* add test case for scrollBar plugin. \([b8ac2974](https://github.com/antvis/f2/commit/b8ac29745e735c145e063a435a42ecf2ea967019)\)

