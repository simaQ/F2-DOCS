# API

After requiring F2, The global namespace F2 can be used.

### Constants

```text
F2.version // version
```

### Classes

* [F2.Chart](chart/): Chart.

### Namespaces

* [F2.G](g/): The renderer, based on html5 canvas.
* [F2.Shape](../developer/shape.md): Interface of Shapes in F2, can be used to customize shape for various geometries.
* [F2.Global](global.md): Global configuration of F2, including styles of charts.
* [F2.Util](util.md): Some utility functions.

### Functions

```text
F2.track(true);      // open version usage monitoring
F2.track(false);     // close version usage monitoring
```

This method is used for monitoring F2's version usage in H5 environment. It is opened by default. If you don't want us to know your version usage or this method is bothering you, please use `F2.track(false)` to closed it.

More API：

* [Chart](chart/)
* [Geometry](chart/geometry.md)
* [Scale](chart/scale.md)
* [Coordinate](chart/coordinate.md)
* [Axis](chart/axis.md)
* [Legend](chart/legend.md)
* [Tooltip](chart/tooltip.md)
* [Guide](chart/guide.md)
* [Animation](chart/animation.md)
* [Interaction](chart/interaction/)
* [Global](global.md)
* [Util](util.md)
* [G](g/)
* [Canvas API in F2](canvas-api-in-f2.md)



