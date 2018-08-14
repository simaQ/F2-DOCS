# Plugin

Plugins are the most efficient way to customize or change the default behavior of a chart. 

### How to use plugins

1. Global registeration for plugins

   ```javascript
   const plugin1 = { /* plugin implementation */ };
   const plugin2 = { /* plugin implementation */ };
   // Global registeration, plugin will be registered to all the chart plugins
   Chart.plugins.register(plugin1); 
   // Global registeration for multiple plug-in
   Chart.plugins.register([ plugin1, plugin2 ]);
   ```

2. Register for a chart instance

   ```javascript
   const plugin1 = { /* plugin implementation */ };
   const plugin2 = { /* plugin implementation */ };

   // chart1 use "plugin1"
   const chart1 = new Chart({
     plugins: plugin1
   );
   // chart2 use "plugin2"
   const chart2 = new Chart({
     plugins: plugin2
   );
   // chart3 doesn't use "plugin"
   const chart3 = new Chart({});
   ```

### Unregister plugins

Use `Chart.plugins.unregister(plugins)` to unregister a plug-in.

### Clear plugins

Use `Chart.plugins.clear()` to clear all the plugins.

### Get registered plugins

Use `Chart.plugins.getAll()` to get all successfully registered plug-ins.

### How to define plugin

The implementation of a plugin is very simple, all you need to do is define the behaviors of the plugin during the life circle of the chart. 

```javascript
const plugin = {
    init(chart) {
       // do something when initialize the chart 
    }
};
```

### Available hooks

* `init`: After initialization of the chart
* `beforeGeomDraw`: Before drawing the geometry
* `afterGeomDraw`: After drawing the geometry
* `beforeCanvasDraw`: before drawing the canvas
* `clear`: Clear the chart, remove geometry
* `clearInner`: Clear the layers
* `repaint`: Redraw

