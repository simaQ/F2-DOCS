# Canvas API in F2

Since F2 use html5 canvas as its renderer, all charts drawn support the attributes of the canvas. This chapter lists commonly used properties, see [Canvas Attributes](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D) for more details.

### General Properties

| Name | Description |
| :--- | :--- |
| `fill` | the color or style to use inside shapes, can be a color string, a[`CanvasGradient`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasGradient) object \(a linear or radial gradient\) or a [`CanvasPattern`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasPattern) object \(a repetitive image\). |
| `fillStyle` | same as `fill` |
| `stroke` | the color or style to use for the lines around shapes, can be a color string, a [`CanvasGradient`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasGradient) object \(a linear or radial gradient\) or a [`CanvasPattern`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasPattern) object \(a repetitive image\). |
| `strokeStyle` | same as `stroke` |
| `shadowColor` | the color of the shadow. |
| `shadowBlur` | the level of the blurring effect; this value doesn't correspond to a number of pixels and is not affected by the current transformation matrix. The default value is 0. Negative, [`Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) or [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) values are ignored. |
| `shadowOffsetX` | the distance that the shadow will be offset in horizontal distance.The default value is 0. [`Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) or [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) values are ignored. |
| `shadowOffsetY` |  the distance that the shadow will be offset in vertical distance. The default value is 0. [`Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) or [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) values are ignored. |
| `opacity` | the alpha value that is applied to shapes and images before they are drawn onto the canvas. The value is in the range from 0.0 \(fully transparent\) to 1.0 \(fully opaque\).Values outside the range, including [`Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) and [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) will not be set and `globalAlpha` will retain its previous value. |
| `globalOpacity` | same as `opacity`. |
| `globalCompositionOperation` |  sets the type of compositing operation to apply when drawing new shapes, where type is a string identifying which of the compositing or blending mode operations to use. See [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/globalCompositeOperation). |

### Line Style

| Name | Description |
| :--- | :--- |
| `lineCap` | determines how the end points of every line are drawn. There are three possible values for this property and those are: `butt`, `round` and `square`. By default this property is set to `butt`. See [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineCap). |
| `lineJoin` | determines how two connecting segments \(of lines, arcs or curves\) with non-zero lengths in a shape are joined together \(degenerate segments with zero lengths, whose specified endpoints and control points are exactly at the same position, are skipped\). See [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin). |
| `lineWidth` |  sets the thickness of lines in space units. When getting, it returns the current value \(`1.0` by default\). When setting, zero, negative, [`Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) and [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) values are ignored; otherwise the current value is set to the new value. See [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineWidth). |
| `miterLimit` | sets the miter limit ratio in space units. When getting, it returns the current value \(`10.0` by default\). When setting, zero, negative, [`Infinity`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) and [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) values are ignored; otherwise the current value is set to the new value. See [MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/miterLimit). |
| `lineDash` | An [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) of numbers which specify distances to alternately draw a line and a gap \(in coordinate space units\). If the number of elements in the array is odd, the elements of the array get copied and concatenated. For example, `[5, 15, 25]` will become `[5, 15, 25, 5, 15, 25]`. If the array is empty, the line dash list is cleared and line strokes return to being solid. |

### Text Style

| Name | Description |
| :--- | :--- |
| `textAlign` | specifies the horizontal alignment of text in an element. The value can be set same as css property [text-align](https://www.w3schools.com/cssref/pr_text_text-align.asp). |
| `textBaseline` | sets the vertical alignment of an element. The value can be set same as css property [vertical-align](https://www.w3schools.com/cssref/pr_pos_vertical-align.asp). |
| `fontStyle` | specifies the font style for text. The value can be set same as css property [font-style](https://www.w3schools.com/cssref/pr_font_font-style.asp). |
| `fontSize` | specifies the font size of text. The value can be set same as css property [font-size](https://www.w3schools.com/cssref/pr_font_font-size.asp). |
| `fontFamily` | specifies the font family for text.The value can be set same as css property [font-family](https://www.w3schools.com/cssref/pr_font_font-family.asp). |
| `fontWeight` | specifies the weight of a font. The value can be set same as css property [font-weight](https://www.w3schools.com/cssref/pr_font_weight.asp). |
| `fontVariant` | specifies whether or not a text should be displayed in a small-caps font. The value can be set same as css property [font-variant](https://www.w3schools.com/cssref/pr_font_font-variant.asp). |
| `lineHeight` | specifies the height of a line. The value can be set same as css property [line-height](https://www.w3schools.com/cssref/pr_dim_line-height.asp). |
| `roate` | rotation angle for text, should be a radian value. |

