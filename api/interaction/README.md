# Interaction

F2 provides an interaction mechanism to achieve the encapsulation and reuse of common interaction behavior. Based on this mechanism, we provide the following four common interactions:

| Interaction | **Demo** |
| :--- | :--- |
| Selection for pie chart | ![](https://cdn-pri.nlark.com/yuque/0/2018/gif/98090/1534071471935-fb8f4e2f-64f6-4c37-ad2c-7d92866248c3.gif) |
| Selection for bar chart | ![](https://cdn-pri.nlark.com/yuque/0/2018/gif/98090/1534071477620-8f15e3d7-203a-471e-b9d2-0c01a2c5de20.gif) |
| Pan | ![](https://cdn-pri.nlark.com/yuque/0/2018/gif/98090/1534071482215-803a5cb9-ad77-4392-92e5-60b889dfe702.gif) |
| Pinch | ![](https://cdn-pri.nlark.com/yuque/0/2018/gif/98090/1534071488312-ee45dbcb-13b2-43c8-955f-153ea232b1eb.gif) |

For developers, they can encapsulate their own interaction behavior based on this mechanism. For details, see the Custom Interaction Behavior\(todo\).

### Usage

For better package size, interaction mode is not packaged by default into @antv/f2. So we should require it.

```javascript
// import F2
const F2 = require('@antv/f2/lib/index');

// import all interations we provide
require('@antv/f2/lib/interaction/');

// If you just want to use one

// import pie chart selection interaction
require('@antv/f2/lib/interaction/pie-select');

// import bar chart selection interaction
require('@antv/f2/lib/interaction/interval-select');

// import pan interaction
require('@antv/f2/lib/interaction/pan');

// import pinch interaction
require('@antv/f2/lib/interaction/pinch');
```





