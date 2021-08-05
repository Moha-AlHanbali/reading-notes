[Home](README.md)

<br>

# Docs for the HTML canvas Element & Chart.js

<br>

## Readings from [EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

<br>

### Charts

<br>

#### Setting up Charts for JS

- First, you need to do is download [Chart.js.](https://github.com/nnnick/Chart.js).
- Copy the Chart.min.js out of the unzipped folder and into the directory you’ll be working in.
- Create a new html page and import the script.

```

<script src='Chart.min.js'></script>.

```

<br>

#### Drawing Line Chart

- First thing we need to do is create a canvas element in our HTML in which Chart.js can draw our chart.
- Next, we need to write a script that will retrieve the context of the canvas, so add this to the foot of your body element: 

```

<script>
    var buyers = document.getElementById('buyers').getContext('2d');
    new Chart(buyers).Line(buyerData);
</script>

```

- Inside the same script tags create your data, in this instance it’s an object that contains labels for the base of our chart and datasets to describe the values on the chart.

```

var variable = {
	labels : ["item","item","item","item","item","item"],
	datasets : [
		{
			fillColor : "rgba(xx ,xx ,xx)",
			strokeColor : "#xxxxxx",
			pointColor : "#xxx",
			pointStrokeColor : "#xxxxxx",
			data : [data,data,data,data,data,data]
		}
	]
}

```

<br>

#### Drawing a Pie Chart

- First, create the canvas element.
- Get the context and to instantiate the chart.
- Create the data. This data is a little different to the line chart because the pie chart is simpler, you just need to supply a value and a color for each section.

<br>

#### Drawing a Bar Chart

- Add  a bar chart to your page.
- Retrieve the element and create the graph.
- Add in the bar chart’s data.

<br>

## Readings from [Basic usage of canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage)

<br>

### The canvas Element

<br>

#### canvas Tag

- canvas element has only two attributes, width and height. These are both optional and can also be set using DOM properties.

- The canvas element can be styled just like any normal image (margin, border, background…).

- Providing fallback content is very straightforward, just insert the alternate content inside the canvas element.

- As a consequence of the way fallback is provided, unlike the `<img>` element, the canvas element requires the closing tag `</canvas>`.

- The canvas element creates a fixed-size drawing surface that exposes one or more rendering contexts, which are used to create and manipulate the content shown.

- Use `draw()` function to execut once the page finishes loading; this is done by listening for the load event.

<br>

## Readings from [Drawing shapes with canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes)

<br>

### The canvas Environment

<br>

#### The grid

- In the canvas grid or coordinate space, normally 1 unit in the grid corresponds to 1 pixel on the canvas. The origin of this grid is positioned in the top left corner at coordinate (0,0).

- All elements are placed relative to this origin. So the position of the top left corner of the blue square becomes x pixels from the left and y pixels from the top.

<br>

#### Drawing rectangles

- canvas only supports two primitive shapes: rectangles and paths (lists of points connected by lines). All other shapes must be created by combining one or more paths. 

- There three functions draw rectangles on the canvas:
  - `fillRect(x, y, width, height)`, draws a filled rectangle.
  - `strokeRect(x, y, width, height)`, draws a rectangular outline.
  - `clearRect(x, y, width, height)`, clears the specified rectangular area, making it fully transparent.
  - `rect(x, y, width, height)`, draws a rectangle whose top-left corner is specified by (x, y) with the specified width and height.
<br>

#### Drawing paths

- A path is a list of points, connected by segments of lines that can be of different shapes, curved or not, of different width and of different color. A path, or even a subpath, can be closed.

1. First, you create the path.
2. Then you use drawing commands to draw into the path.
3. Once the path has been created, you can stroke or fill the path to render it.


<br>

- The functions used to perform these steps:
  - `beginPath()`, creates a new path. Once created, future drawing commands are directed into the path and used to build the path up.
  - `Path methods`, methods to set different paths for objects.
  - `closePath()`, adds a straight line to the path, going to the start of the current sub-path.
  - `stroke()`, draws the shape by stroking its outline.
  - `fill()`, draws a solid shape by filling the path's content area.

<br>

> When you call fill(), any open shapes are closed automatically, so you don't have to call closePath(). This is not the case when you call stroke().

<br>

- A very useful function, which doesn't actually draw anything but becomes part of the path list described above, is the `moveTo()` function, it moves the pen to the coordinates specified by x and y.

<br>

#### Lines

- For drawing straight lines, use the `lineTo()` method.

<br>

#### Arcs
 
- `arc(x, y, radius, startAngle, endAngle, counterclockwise)`, draws an arc which is centered at (x, y) position with radius r starting at startAngle and ending at endAngle going in the given direction indicated by counterclockwise (defaulting to clockwise).

- `arcTo(x1, y1, x2, y2, radius)`, draws an arc with the given control points and radius, connected to the previous point by a straight line.

> Angles in the arc function are measured in radians, not degrees. To convert degrees to radians you can use the following JavaScript expression: radians = (Math.PI/180)*degrees.

<br>

#### Bezier and quadratic curves

- `quadraticCurveTo(cp1x, cp1y, x, y)`, draws a quadratic Bézier curve from the current pen position to the end point specified by x and y, using the control point specified by cp1x and cp1y.

- `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)`, draws a cubic Bézier curve from the current pen position to the end point specified by x and y, using the control points specified by (cp1x, cp1y) and (cp2x, cp2y).

<br>

#### Path2D objects

- `Path2D()`, the Path2D() constructor returns a newly instantiated Path2D object, optionally with another path as an argument (creates a copy), or optionally with a string consisting of SVG path data.

<br>

## Readings from [Applying styles and colors](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)

<br>

### The canvas Styles

<br>

#### Colors

- `fillStyle = color value`, sets the style used when filling shapes.

- `strokeStyle = color value`, Sets the style for shapes' outlines.

<br>

#### Transparency

- `globalAlpha = transparencyValue`, Applies the specified transparency value to all future shapes drawn on the canvas. The value must be between 0.0 (fully transparent) to 1.0 (fully opaque). This value is 1.0 (fully opaque) by default.

> You can do this also by assigning a semi-transparent color to the stroke and/or fill style.

<br>

#### Line styles

- `lineWidth = value`, sets the width of lines drawn in the future.
- `lineCap = type`, sets the appearance of the ends of lines.
- `lineJoin = type`, sets the appearance of the "corners" where lines meet.
- `miterLimit = value`, establishes a limit on the miter when two lines join at a sharp angle, to let you control how thick the junction becomes.
- `getLineDash()` returns the current line dash pattern array containing an even number of non-negative numbers.
- `setLineDash(segments)`, sets the current line dash pattern.
- `lineDashOffset = value`, specifies where to start a dash array on a line.

<br>

#### Gradients

- `createLinearGradient(x1, y1, x2, y2)`, creates a linear gradient object with a starting point of (x1, y1) and an end point of (x2, y2).
- `createRadialGradient(x1, y1, r1, x2, y2, r2)`, creates a radial gradient. The parameters represent two circles, one with its center at (x1, y1) and a radius of r1, and the other with its center at (x2, y2) with a radius of r2.
- `createConicGradient(angle, x, y)`, creates a conic gradient object with a starting angle of angle in radians, at the position (x, y).

<br>

#### Patterns

- `createPattern(image, type)`, creates and returns a new canvas pattern object.
  - `repeat` tiles the image in both vertical and horizontal directions.
  - `repeat-x`, tiles the image horizontally but not vertically.
  - `repeat-y`, tiles the image vertically but not horizontally.
  - `no-repeat`, Doesn't tile the image. It's used only once.

<br>

#### Shadows

- `shadowOffsetX = float`, indicates the horizontal distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
- `shadowOffsetY = float` , Indicates the vertical distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
- `shadowBlur = float`, indicates the size of the blurring effect; this value doesn't correspond to a number of pixels and is not affected by the current transformation matrix. The default value is 0.
- `shadowColor = color`, A standard CSS color value indicating the color of the shadow effect; by default, it is fully-transparent black.

<br>

#### canvas fill rules

- When using fill (or clip and isPointInPath) you can optionally provide a fill rule algorithm by which to determine if a point is inside or outside a path and thus if it gets filled or not.
  - `nonzero` rule.
  - `evenodd` rule.

<br>

## Readings from [Drawing text](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text)

<br>

### canvas Text

<br>

#### Drawing Text

- `fillText(text, x, y [, maxWidth])`, fills a given text at the given (x,y) position. Optionally with a maximum width to draw.
- `strokeText(text, x, y [, maxWidth])`, strokes a given text at the given (x,y) position. Optionally with a maximum width to draw.

<br>

#### Styling text

- `font = value`, the current text style being used when drawing text. This string uses the same syntax as the CSS font property. The default font is 10px sans-serif.
- `textAlign = value` text alignment setting. Possible values: start, end, left, right or center. The default value is start.
- `textBaseline = value`, baseline alignment setting. Possible values: top, hanging, middle, alphabetic, ideographic, bottom. The default value is alphabetic.
- `direction = value`, directionality. Possible values: ltr, rtl, inherit. The default value is inherit.

<br>

#### Advanced text measurements

- `measureText()`, returns a TextMetrics object containing the width, in pixels, that the specified text will be when drawn in the current text style.
