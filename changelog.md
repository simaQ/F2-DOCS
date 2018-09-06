# Changelog

### **3.2.2 \(2018-09-06\)**

#### **Chores**

* upgrade babel7. \([ee2087e2](https://github.com/antvis/f2/commit/ee2087e23ef61293395048306d9db1b6a2205e26)\)

#### **Bug Fixes**

* Guide.point, the render method should return the point shape. \([e83a3a1c](https://github.com/antvis/f2/commit/e83a3a1cc7f4a16cf83d371818d07235e6ede061)\)
* attrs should be deep clone. Closed [\#288](https://github.com/antvis/f2/pull/288). \([2e4a90b9](https://github.com/antvis/f2/commit/2e4a90b9d16224d217a8f1b6c935c4847e9c5599)\)
* when Text shape's text attribute is updated, the textArr attribute should be reset. Closed [\#302](https://github.com/antvis/f2/pull/302). \([1625a22e](https://github.com/antvis/f2/commit/1625a22e52e529d3c5bf2c45b620c95d139fd160)\)
* if text shape's x or y is NaN, there will be a drawing error in webchart mini program. Related to [https://github.com/antvis/wx-f2/issues/81](https://github.com/antvis/wx-f2/issues/81). \([4f0ca529](https://github.com/antvis/f2/commit/4f0ca529731476d9618c32bc911f1b6e7c17a873)\)
* if there is a point with NaN value in the Polyline's points, there will be a drawing error in webchart mini program. \([d5b39bef](https://github.com/antvis/f2/commit/d5b39bef589197544a4df29a81581610d50af562)\)
* when text shape's content is 0, ensure it will be rendered. Closed [\#282](https://github.com/antvis/f2/pull/282). \([b35dedf2](https://github.com/antvis/f2/commit/b35dedf2512b86f4332df3440b6a9151cb2693dd)\)

#### **Other Changes**

* add Node.js 10 \([c6adb987](https://github.com/antvis/f2/commit/c6adb9871debcc81e36e9513aab65f6b8a3f770b)\)

### **3.2.1 \(2018-08-24\)**

#### **New Features**

* support set gradient color in default. Closed [\#243](https://github.com/antvis/f2/pull/243). \([20b18a90](https://github.com/antvis/f2/commit/20b18a90c42b75eb98b60c1fa31d72db20152ffc)\)
* support `syncY` property to unify multiple Y-axis data ranges. Related to [\#258](https://github.com/antvis/f2/pull/258). \([854685e8](https://github.com/antvis/f2/commit/854685e829b160583cf62ede0a9faf621a572e75)\)
* support set default selected shape for pie-select and interval-select interaction. Related to [\#248](https://github.com/antvis/f2/pull/248). \([55364d59](https://github.com/antvis/f2/commit/55364d598065fbc414e6c4c39bb9d6e56bda1214)\)

#### **Bug Fixes**

* when geom clear, the `_width` should be reset. Closed [\#273](https://github.com/antvis/f2/pull/273). \([a36aa67f](https://github.com/antvis/f2/commit/a36aa67f7c5a36be81fdbcc1d38dd305973c596a)\)
* when chart update, tooltip's `_lastActive` should be reset. Closed [\#271](https://github.com/antvis/f2/pull/271). \([297ae475](https://github.com/antvis/f2/commit/297ae47518ecb73807aa51c1683a5a1bd02f8390)\)
* define calculateBBox method for smooth area shape for getBBox\(\). \([ebf8539d](https://github.com/antvis/f2/commit/ebf8539d73a62f4ed720a11feda50410a3d10ca1)\)
* Fix sorting problem for categorical data. Closed [\#257](https://github.com/antvis/f2/pull/257). \([3a129289](https://github.com/antvis/f2/commit/3a129289515fff4a04e84823a517e38b2f103356)\)

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

