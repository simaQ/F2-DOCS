# Global

## F2.Global

`F2.Global` is the global configuration in F2, it contains following attributes:  
~~~~We can get the default value of an attribute by `console.log(F2.Global)`.

| Name | Type | Description |
| :--- | :--- | :--- |
| `padding` | Array / Number | the spacing between the chart plot area and the canvas border. See [here](https://antv.gitbook.io/f2/api/chart#padding). Default value is 'auto'. |
| `appendPadding` | Array / Number | The reserved spacing on the four sides of the chart canvas area. See [here](https://antv.gitbook.io/f2/api/chart#appendpadding). |
| `axis` | Object | The default configuration for different types of axes. |
| `colors` | Array | The default color series. |
| `defaultColor` | String | The default color. |
| `fontFamily` | String | The default font family. |
| `guide` | Object | The default configuration for different types of guides. |
| `legend` | Object | The default configuration for different type of legends. |
| `lineDash` | Array | The default setting for `lineDash`. |
| `pixelRatio` | Number | The default pixel ratio. |
| `shape` | Object | The default style configuration for different shapes. |
| `sizes` | Array | The default size range for size mapping. |
| `tooltip` | Object | The default tooltip configuration for tooltip. |
| `version` | String | The current version of F2.  |
| `widthRatio` | Object | ratio of width for different shapes. |

**Methods**

### `Global.setTheme(config)`

Configure F2's charts style. For users to define their own style.

**Parameters**:

| Name | Type | Description |
| :--- | :--- | :--- |
| `config` | Object | theme configuration |

Example: 

```javascript
F2.Global.setTheme({
  colors: [ '#F04864', '#D66BCA', '#8543E0', '#8E77ED', '#3436C7', '#737EE6', '#223273', '#7EA2E6' ],
  pixelRatio: 2,
  guide: {
    line: {
      stroke: '#F04864',
      lineWidth: 2
    }
  }
});
```

