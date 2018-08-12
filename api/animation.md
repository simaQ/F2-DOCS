# Animation

The charts for mobile should be more vividness. So F2 provides an animation mechanism.

## How to Register Animation Plugin

F2 has modular structure provides best tree-shaking results and package size optimization. 

If you just **`import F2 from '@antv/f2'`**, then **it has included `Animation` by default**. But if you want a better package size optimization, you can register manually:

```javascript
const F2 = require('@antv/f2/lib/core');
const Animation = require('@antv/f2/lib/animation/detail');
// Method 1: Global Registeration
F2.Chart.plugins.register(Animation); 

// Or Method2: Registeration for a Chart instance
const chart = new F2.Chart({
  id: 'canvas',
  plugins: Animation
});
```

## Animation Introduction

F2 animations are all animated in shapes. According to the change of the chart's data, we classified animation into four types in F2:

| Type | Description | Trigger Timing |
| :--- | :--- | :--- |
| appear | The entrance animation when the chart is first loaded. | first time calling `chart.render()` |
| enter | The entrance animation when the chart is re-rendered after the change of data. | `chart.changeData(data)` |
| update | The update animation when the chart is re-rendered and the chart's shapes' status  is updated after the change of the data. | `chart.changeData(data)` |
| leave | The destroy animation when the chart's shapes are destroyed after the change of the data | `chart.changeData(data)` |

## Methods

### `chart.animate(false)`

Close the chart's animation.

### `chart.<geomType>().animate(config)`

Animation configuration for geometry.

```javascript
chart.line().animate({
  appear: {
    animation: 'fadeIn',
    duration: 1000
  },
  update: false
});
```

**Parameters:**

* `config`: Object / false. 

         If `config`'s value is false, means close the animation for the geometry. 

         If `config` is an object, the properties can configure include:

| Name | Type | Description |
| :--- | :--- | :--- |
| `appear` | Object / Boolean | Configuration for appear animation. If `appear` is false, means close the appear animation for the geometry. |
| `enter` | Object / Boolean | Configuration for enter animation. If `enter` is false, means close the enter animation for the geometry. |
| `update` | Object / Boolean | Configuration for update animation. If `update` is false, means close the update animation for the geometry. |
| `leave` | Object / Boolean | Configuration for leave animation. If `leave` is false, means close the leave animation for the geometry. |

The configurable properties for `appear`, `enter`, `update` and `leave` are as follows:

| Name | Type | Description |
| :--- | :--- | :--- |
| `animation` | String / Function | It is the animation action which can be specific with a string, in this way, you are using the animation provided by F2 \(see below，todo\). Or be a Function\(todo\) for customizing. |
| `easing` | String / Function | easing action for animation.You can use the default easing functions provided by F2 or pass the function directly. See below\(todo\). |
| `delay` | Number / Function | delay time for animation, in millisecond.You can specify delay time directly or pass a callback\(todo\). |
| `duration` | Number | duration of the animation, in millisecond. |

Example:

```javascript
{
  appear: {
    animation: 'fadeIn',
    easing: 'elasticIn', 
    delay: 1000, 
    duration: 600
  },
  update: false
}
```

#### Default Animations

 The animations provided by default are shown below:

| Name | Demo |  |
| :--- | :--- | :--- |
| `groupWaveIn` | [![](https://camo.githubusercontent.com/acaa5827f1e5742c1c2fa4a784d7e64c11fd1d98/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f37663662366131392d623762662d343265652d623866642d6439313238333930636130322f323031382f6769662f62313234653666302d646364642d343435302d396364362d6663643765356464666338612e676966)](https://camo.githubusercontent.com/acaa5827f1e5742c1c2fa4a784d7e64c11fd1d98/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f37663662366131392d623762662d343265652d623866642d6439313238333930636130322f323031382f6769662f62313234653666302d646364642d343435302d396364362d6663643765356464666338612e676966) | ![](https://camo.githubusercontent.com/0492b46f8e9e4bcbc5cba53bf6cfe6784feb1f18/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f36333431333730332d323836342d346161302d383036362d3839353233356135656634342f323031382f6769662f61656538383838382d313762332d343861652d383633622d3864663333313361666462642e676966) |
| `groupScaleInX` | [![](https://camo.githubusercontent.com/8b35680cd640f769b08bf8d7ea0044910a3a1367/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f32306238376130342d653634302d346130622d396665372d3535623061363632353365392f323031382f6769662f37323564666430382d333162652d346134302d616164372d3739656166613062663235322e676966)](https://camo.githubusercontent.com/8b35680cd640f769b08bf8d7ea0044910a3a1367/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f32306238376130342d653634302d346130622d396665372d3535623061363632353365392f323031382f6769662f37323564666430382d333162652d346134302d616164372d3739656166613062663235322e676966) | ![](https://camo.githubusercontent.com/a4e25bfb85b61bafff4bb68f7e716bf5ef8e8add/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f37623033386261382d323038662d346636392d383539632d6665356636383637303534632f323031382f6769662f30376464396334622d353437622d343466352d393532662d3762353839346634313931642e676966) |
| `groupScaleInY` | [![](https://camo.githubusercontent.com/8ae720e725a58b259911ec80562ebb73a14eb698/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f37663236396664382d323237312d343037342d386661632d3631356566633039623236392f323031382f6769662f64396530616632312d653362612d343339342d613239612d6462303532653861303762622e676966)](https://camo.githubusercontent.com/8ae720e725a58b259911ec80562ebb73a14eb698/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f37663236396664382d323237312d343037342d386661632d3631356566633039623236392f323031382f6769662f64396530616632312d653362612d343339342d613239612d6462303532653861303762622e676966)  | ![](https://camo.githubusercontent.com/a5b8cd4394f171e5977b221d7a5abfb391d2dd96/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f36346432333864302d363739382d343262302d613362622d3566626362393166616135662f323031382f6769662f37343933623031622d616466312d343630332d383130352d3334336334656563373138662e676966) |
| `groupScaleInXY` | [![](https://camo.githubusercontent.com/92b89e592dac7094b16d093916b3135e5e966837/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f34366463633336332d656634662d343665392d386666622d6664326263333333333831662f323031382f6769662f36376135626365632d666139612d343838302d396566642d3962386631616430643861322e676966)](https://camo.githubusercontent.com/92b89e592dac7094b16d093916b3135e5e966837/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f34366463633336332d656634662d343665392d386666622d6664326263333333333831662f323031382f6769662f36376135626365632d666139612d343838302d396566642d3962386631616430643861322e676966) | ![](https://camo.githubusercontent.com/65d01da96499698f3ebf5bb6a23f9d21e92888cc/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f64383965376663612d393164622d346564662d393364612d6463373165313634366463312f323031382f6769662f61323066386532312d333532322d346338332d613336652d3165663666646531663736652e676966) |
| `shapesScaleInX` | [![](https://camo.githubusercontent.com/544457a69f28ad2a7330ccbee62fe0c62720be85/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f64326237313462652d343261612d343138332d386465362d3234396333396138633264332f323031382f6769662f36356530353066322d313738392d346230342d396138392d3635353233333463393436632e676966)](https://camo.githubusercontent.com/544457a69f28ad2a7330ccbee62fe0c62720be85/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f64326237313462652d343261612d343138332d386465362d3234396333396138633264332f323031382f6769662f36356530353066322d313738392d346230342d396138392d3635353233333463393436632e676966) |  |
| `shapesScaleInY` | [![](https://camo.githubusercontent.com/c22ba0106f3fa1dd0657a08a5fb1449faa212ea6/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f63376139306537642d666463332d346437322d623036622d3630663965656363656434642f323031382f6769662f30323165653236322d653061332d343339362d383233322d3737346638313336663133382e676966)](https://camo.githubusercontent.com/c22ba0106f3fa1dd0657a08a5fb1449faa212ea6/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f63376139306537642d666463332d346437322d623036622d3630663965656363656434642f323031382f6769662f30323165653236322d653061332d343339362d383233322d3737346638313336663133382e676966) |  |
| `shapesScaleInXY` | [![](https://camo.githubusercontent.com/686aa2d5072f712fea2f006462c6e6a41edd1fa7/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f63663266363630662d343864322d343665392d623765322d6536623539663033333364662f323031382f6769662f36643038343432652d646638392d343131362d383365392d3861333663323435393634352e676966)](https://camo.githubusercontent.com/686aa2d5072f712fea2f006462c6e6a41edd1fa7/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f63663266363630662d343864322d343665392d623765322d6536623539663033333364662f323031382f6769662f36643038343432652d646638392d343131362d383365392d3861333663323435393634352e676966) |  |
| `fadeIn` | [![](https://camo.githubusercontent.com/d497959df67f91714a58f640f1f3d11e92c238a1/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f31363435653635382d633030372d343364612d396431662d6261613332366263656665662f323031382f6769662f32656133386363662d386437632d343263362d613166622d3762616636343032366464392e676966)](https://camo.githubusercontent.com/d497959df67f91714a58f640f1f3d11e92c238a1/68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f736b796c61726b2f31363435653635382d633030372d343364612d396431662d6261613332366263656665662f323031382f6769662f32656133386363662d386437632d343263362d613166622d3762616636343032366464392e676966) |  |

#### `animation` callback

Animation action can also be a callback.

```javascript
 /**
   * Animation callback
   * @param  {Shape} shape       shape of the animation
   * @param  {Object} animateCfg configuration of the animation, such as easing, duration, etc.
   * @param  {Coord} coord       current coordinate object           
   */
  animation: (shape, animateCfg, coord) {}
```

#### Default `easing`

The default easing functions are: 

* `linear`
* `quadraticIn`
* `quadraticOut` 
* `quadraticInOut`
* `cubicIn`
* `cubicOut`
* `cubicInOut`
* `elasticIn` 
* `elasticOut`
* `elasticInOut`
* `backIn`
* `backOut`
* `backInOut`
* `bounceIn`
* `bounceOut`
* `bounceInOut`

For animation effect of each easing function, see [http://sole.github.io/tween.js/examples/03\_graphs.html](http://sole.github.io/tween.js/examples/03_graphs.html).

#### `easing` callback

`easing` can also be a callback.

```javascript
easing(t) {}
```

Example:

```javascript
easing: (t) => {
  return Math.sqrt(1 - --t * t);
}
```

#### `delay` callback

```javascript
/**
 * return the delay of the animation
 * @param  {Number} index      index of the shape, same as the shape's order of the data record in data set.
 * @param  {String} id         id of current shape
 * @return {Number}            delay of the animation, in millisecond
 */
delay(index, id) {}
```

### `shape.animate()`

We also provide a method called `animate` for Shape instance to act the specific animation. See below for usage:

```javascript
shape.animate()
  .to({
    attrs: {Object}, // the final graph attributes of the shape
    easing: {String} || {Function}, // easing function
    duration: {Number}, // duration of the animation, in millisecond
    delay: {Number} // delay time of the animation, in millisecond
  }) // animation action
  .onStart(function() {
    // callback when animation starts
  })
  .onUpdate(function() {
    // callback during the animation
  })
  .onEnd(function() {
    // callback when animation ends
  })
  .onFrame(function(t) {
    // callback for animation's every frame, `t` ranges from 0 to 1.
  });
```

