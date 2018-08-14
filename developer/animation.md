# Animate

If you want a more beautiful animation, you can define your own animation.

### Animation Register

Animation register is used to achieve the goal of reusing animation functions. After register, you can use it everywhere.

```javascript
// require registeration class of animation
const Animate = require('@antv/f2/lib/animation/animate');
/**
 * @param  {String} animationName   Animation name, specified by users
 * @param  {Function} animationFun  define specific animations 
 **/
Animate.registerAnimation('animationName', animationFun); //  register a animation called animationName


// use the registered animation
chart.line().animate({
  appear: {
    animation: 'animationName'  // the registered name of the animation
  }
})
```

### Details on Custom Animation

F2 provides a complete animation customization mechanism. Users can customize animation behavior for any states of graphic element that supports animation. The states here are the four types of animations: appear, enter, leave, update.

The animations in F2 all act on [Shape](../api/g/shape.md). The animation is performed by changing shape's attributes frame by frame, take the movement of the circle as example:

![](https://gw.alipayobjects.com/zos/rmsportal/VsphIrCJSqpILogoZTiS.gif)

The animation is very simple, it moves the circle from point A to point B \(the coordinate is `{x: 230, y: 50}`\). We need only to call `shape.animate()` to specify the final state, i.e. graph attributes, of the shape.

```javascript
// the initial position of circle on canvas is x: 100, y: 100
circle.animate().to({
  attrs: {
    x: 230, // final coordinate of x-axis
    y: 50   // final coordinate of y-axis
  }, // specify the final state of the circle
  easing: 'linear', // easing function
  duration: 1500 // duration of the animation
})
```

See [here](../api/g/shape.md) for graph attributes of various shapes.

Three parameters will be passed to the user-defined animation function, in the order of `shape`, `animateCfg`, `coord`.

```javascript
chart.line().animate({
  appear: {
    animation: (shape, animateCfg, coord) => {}
  }
})
```

**Parameters:**

* `shape`: The shape instance which animation is acted on.

You can get graph attributes `attrs` from shape instance and then customize the animation.

The attributes are provided to help users ease the customization:

| Attributes | Method To Get | Type | Explanation |
| :---: | :---: | :---: | :---: |
| `attrs` | `shape.get('attrs')` | Object | Get all graph attributes of the shape |
| `className` | `shape.get('className')` | String | Get the type name of the shape |
| `origin` | `shape.get('origin')` | Object | Get the drawing data and corresponding original data record of the shape |
| `index` | `shape.get('index')` | Number | Get the index of the shape, i.e. the order of the data record in data set |

In addition, `shape.attr(name)` can also be used to get graph attribute from shape. More methods of shape are listed in [Shape API](../api/g/shape.md#methods).

F2 also provides a `cacheShape` attribute for the shape instance in the update state.This attribute stores the content of the previous state for the shape, so that users can customize the animation for changing. The cacheShape contains the following content:

```javascript
{
  animateCfg: {}, // configuration for animation
  attrs: {}, // graph attrs of previous state
  className: "", // class name of the shape
}
```

* `animateCfg`: Object, configuration for animation

  The following attributes are contained in animateCfg:

  ```javascript
  {
    easing: , // easing function
    duration: , // duration of the animation
    delay: // delay of the animation
  }
  ```

* `coord`: Coordinate object, represents the current coordinate of the chart. The attributes contained in coordinate object are listed in [Coordinate API](../api/coordinate.md).

### Example

The example below shows how to customize the `apear` animation for bar chart, online demo [here](https://antv.alipay.com/zh-cn/f2/3.x/demo/other/animated-column.html): 

![column1.gif](https://gw.alipayobjects.com/zos/skylark/477ede4d-3496-42c9-97a6-f63195765dbd/2018/gif/2e743bec-fefb-46f1-96f3-cc0e965d4234.gif)

```javascript
const { Chart, Animate, Util, G } = F2;
  // register an animation called delayScaleInY
  Animate.registerAnimation('delayScaleInY', function(shape, animateCfg) {
    const box = shape.getBBox(); // get the bounding box of the shape
    const origin = shape.get('origin'); // get the drawing data of the shape
    const points = origin.points; // the points that compose of each column
    const centerX = (box.minX + box.maxX) / 2;
    let centerY;
    if (points[0].y - points[1].y <= 0) { // when the point is below 0
      centerY = box.maxY;
    } else {
      centerY = box.minY;
    }

    shape.transform([
      [ 't', centerX, centerY ],
      [ 's', 1, 0.1 ],
      [ 't', -centerX, -centerY ]
    ]); // use matrix transformation to change the origin state of the shape. scaleY.
    const index = shape.get('index');
    let delay = animateCfg.delay; // get the animation configuration
    if (Util.isFunction(delay)) {
      delay = animateCfg.delay(index); // set delay time according to the index
    }
    const easing = animateCfg.easing; // get the animation configuration

    const matrix = shape.getMatrix(); // get the current matrix
    const endMatrix = G.Matrix.transform(matrix, [
      [ 't', centerX, centerY ],
      [ 's', 1, 10 ],
      [ 't', -centerX, -centerY ]
    ]); // the matrix for the final state of the shape

    shape.animate().to({
      attrs: {
        matrix: endMatrix
      },
      delay,
      easing,
      duration: animateCfg.duration
    }); // do the animation
  });

  const data = [];
  for (let i = 0; i < 50; i++) {
    data.push({
      x: i,
      y: (Math.sin(i / 5) * (i / 5 - 10) + i / 6) * 5
    });
  }
  const chart = new Chart({
    id: 'mountNode',
    width: 375,
    height: 200,
    pixelRatio: window.devicePixelRatio
  });
  chart.axis('x', false);
  chart.legend(false);
  chart.source(data);
  chart.interval()
    .position('x*y')
    .color('y', '#4a657a-#308e92-#b1cfa5-#f5d69f-#f5898b-#ef5055')
    .animate({ // customize animation configuration
      appear: {
        animation: 'delayScaleInY', // use the registered animation name
        easing: 'elasticOut', // easing function
        delay(index) {
          return index * 10;
        } // delay time for each shape according to index
      }
    });
  chart.render();
```

