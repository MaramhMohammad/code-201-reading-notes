# [Chart.js API](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

Charts are far better for displaying data visually than tables. They're easier to look at and convey data quickly, but they're not always easy to create. A great way to get started with charts is with Chart.js, a JavaScript plugin that uses HTML5’s canvas element to draw the graph onto the page.

## Setting up

1. Download [Chart.js](https://github.com/chartjs/Chart.js)
1. Copy the Chart.min.js out of the unzipped folder and into the directory you’ll be working in. 
1. Then create a new html page and import the script:
```
<!DOCTYPE html>
<html lang="en">
<head>
        <meta charset="utf-8" />
        <title>Chart.js demo</title>
        <script src='Chart.min.js'></script>
    </head>
    <body>
    </body>
</html>
```

The following is covered at the link for [Chart.js](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

- Drawing a Line Chart
- Drawing a Pie Chart
- Drawing a Bar Chart 

# Canvas API - [Basic Usage](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage)

## The `<canvas>` element

At first sight a `<canvas>` looks like the `<img>` element, with the only clear difference being that it doesn't have the src and alt attributes. Indeed, the `<canvas>` element has only two attributes, width and height. These are both optional and can also be set using DOM properties. When no width and height attributes are specified, the canvas will initially be 300 pixels wide and 150 pixels high. The element can be sized arbitrarily by CSS, but during rendering the image is scaled to fit its layout size: if the CSS sizing doesn't respect the ratio of the initial canvas, it will appear distorted.

The id attribute isn't specific to the `<canvas>` element but is one of the global HTML attributes which can be applied to any HTML element (like class for instance). It is always a good idea to supply an id because this makes it much easier to identify it in a script.

The `<canvas>` element can be styled just like any normal image (margin, border, background…). These rules, however, don't affect the actual drawing on the canvas.

The `<canvas>` element differs from an `<img>` tag in that, like for `<video>`, `<audio>`, or `<picture>` elements, it is easy to define some fallback content, to be displayed in older browsers not supporting it, like versions of Internet Explorer earlier than version 9 or textual browsers. You should always provide fallback content to be displayed by those browsers.

### Fallback Content

Providing fallback content is very straightforward: just insert the alternate content inside the `<canvas>` element. Browsers that don't support `<canvas>` will ignore the container and render the fallback content inside it. Browsers that do support `<canvas>` will ignore the content inside the container, and just render the canvas normally.

### Required `</canvas>` tag

As a consequence of the way fallback is provided, unlike the `<img>` element, the `<canvas>` element requires the closing tag `(</canvas>)`. If this tag is not present, the rest of the document would be considered the fallback content and wouldn't be displayed.

If fallback content is not needed, a simple `<canvas id="foo" ...></canvas>` is fully compatible with all browsers that support canvas at all.

## The rendering context

The `<canvas>` element creates a fixed-size drawing surface that exposes one or more rendering contexts, which are used to create and manipulate the content shown. In this tutorial, we focus on the 2D rendering context. Other contexts may provide different types of rendering; for example, WebGL uses a 3D context based on OpenGL ES.

The canvas is initially blank. To display something, a script first needs to access the rendering context and draw on it. The `<canvas>` element has a method called getContext(), used to obtain the rendering context and its drawing functions. getContext() takes one parameter, the type of context. For 2D graphics, such as those covered by this tutorial, you specify "2d" to get a CanvasRenderingContext2D.

var canvas = document.getElementById('tutorial');
var ctx = canvas.getContext('2d');

The first line in the script retrieves the node in the DOM representing the `<canvas>` element by calling the document.getElementById() method. Once you have the element node, you can access the drawing context using its getContext() method.

## Checking for support

The fallback content is displayed in browsers which do not support `<canvas>`. Scripts can also check for support programmatically by simply testing for the presence of the getContext() method. Our code snippet from above becomes something like this:
```
var canvas = document.getElementById('tutorial');

if (canvas.getContext) {<br>
  var ctx = canvas.getContext('2d');<br>
  // drawing code here<br>
} else {<br>
  // canvas-unsupported code here<br>
}
```
# Canvas API - [Drawing Shapes With Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes)

## The grid

Before we can start drawing, we need to talk about the canvas grid or coordinate space. Our HTML skeleton from the previous page had a canvas element 150 pixels wide and 150 pixels high.  The origin of this grid is positioned in the top left corner at coordinate (0,0). All elements are placed relative to this origin. So the position of the top left corner of a square becomes x pixels from the left and y pixels from the top, at coordinate (x,y). 

## Drawing rectangles

Unlike SVG, `<canvas>` only supports two primitive shapes: rectangles and paths (lists of points connected by lines). All other shapes must be created by combining one or more paths. Luckily, we have an assortment of path drawing functions which make it possible to compose very complex shapes.

There are three functions that draw rectangles on the canvas:

- fillRect(x, y, width, height)
  - Draws a filled rectangle.
- strokeRect(x, y, width, height)
  - Draws a rectangular outline.
- clearRect(x, y, width, height)
  - Clears the specified rectangular area, making it fully transparent.

Each of these three functions takes the same parameters. x and y specify the position on the canvas (relative to the origin) of the top-left corner of the rectangle. width and height provide the rectangle's size.

Example:

ctx.fillRect(25, 25, 100, 100);<br>
    ctx.clearRect(45, 45, 60, 60);<br>
    ctx.strokeRect(50, 50, 50, 50);

The fillRect() function draws a large black square 100 pixels on each side. The clearRect() function then erases a 60x60 pixel square from the center, and then strokeRect() is called to create a rectangular outline 50x50 pixels within the cleared square.

## Drawing paths

Now let's look at paths. A path is a list of points, connected by segments of lines that can be of different shapes, curved or not, of different width and of different color. A path, or even a subpath, can be closed. To make shapes using paths, we take some extra steps:

1. First, you create the path.
1. Then you use drawing commands to draw into the path.
1. Once the path has been created, you can stroke or fill the path to render it.

Here are the functions used to perform these steps:

- beginPath()
  - Creates a new path. Once created, future drawing commands are directed into the path and used to build the path up.
- Path methods
  - Methods to set different paths for objects.
- closePath()
  - Adds a straight line to the path, going to the start of the current sub-path.
- stroke()
  - Draws the shape by stroking its outline.
- fill()
  - Draws a solid shape by filling the path's content area.

1. he first step to create a path is to call the beginPath(). Internally, paths are stored as a list of sub-paths (lines, arcs, etc) which together form a shape. Every time this method is called, the list is reset and we can start drawing new shapes.
1. The second step is calling the methods that actually specify the paths to be drawn. We'll see these shortly.
1. The third, and an optional step, is to call closePath(). This method tries to close the shape by drawing a straight line from the current point to the start. If the shape has already been closed or there's only one point in the list, this function does nothing.

## Moving the pen to the

One very useful function, which doesn't actually draw anything but becomes part of the path list described above, is the moveTo() function. You can probably best think of this as lifting a pen or pencil from one spot on a piece of paper and placing it on the next.

moveTo(x, y)

Moves the pen to the coordinates specified by x and y.
When the canvas is initialized or beginPath() is called, you typically will want to use the moveTo() function to place the starting point somewhere else. 

## lines

For drawing straight lines, use the lineTo() method.

lineTo(x, y)

Draws a line from the current drawing position to the position specified by x and y.
This method takes two arguments, x and y, which are the coordinates of the line's end point. The starting point is dependent on previously drawn paths, where the end point of the previous path is the starting point for the following, etc. The starting point can also be changed by using the moveTo() method.

## Arcs

To draw arcs or circles, we use the arc() or arcTo() methods.

arc(x, y, radius, startAngle, endAngle, anticlockwise)

Draws an arc which is centered at (x, y) position with radius r starting at startAngle and ending at endAngle going in the given direction indicated by anticlockwise (defaulting to clockwise).

arcTo(x1, y1, x2, y2, radius)

Draws an arc with the given control points and radius, connected to the previous point by a straight line.

Let's have a more detailed look at the arc method, which takes six parameters: x and y are the coordinates of the center of the circle on which the arc should be drawn. radius is self-explanatory. The startAngle and endAngle parameters define the start and end points of the arc in radians, along the curve of the circle. These are measured from the x axis. The anticlockwise parameter is a Boolean value which, when true, draws the arc anticlockwise; otherwise, the arc is drawn clockwise.

**Note: Angles in the arc function are measured in radians, not degrees. To convert degrees to radians you can use the following JavaScript expression: radians = (Math.PI/180)*degrees.**

## Bezier and quadratic curves

The next type of paths available are Bézier curves, available in both cubic and quadratic varieties. These are generally used to draw complex organic shapes.

quadraticCurveTo(cp1x, cp1y, x, y)

Draws a quadratic Bézier curve from the current pen position to the end point specified by x and y, using the control point specified by cp1x and cp1y.

bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)

Draws a cubic Bézier curve from the current pen position to the end point specified by x and y, using the control points 
specified by (cp1x, cp1y) and (cp2x, cp2y).

The difference between these can best be described using the image on the right. A quadratic Bézier curve has a start and an end point (blue dots) and just one control point (indicated by the red dot) while a cubic Bézier curve uses two control points.

The x and y parameters in both of these methods are the coordinates of the end point. cp1x and cp1y are the coordinates of the first control point, and cp2x and cp2y are the coordinates of the second control point.

## Rectangles
In addition to the three methods we saw in Drawing rectangles, which draw rectangular shapes directly to the canvas, there's also the rect() method, which adds a rectangular path to a currently open path.

rect(x, y, width, height)

Draws a rectangle whose top-left corner is specified by (x, y) with the specified width and height.
Before this method is executed, the moveTo() method is automatically called with the parameters (x,y). In other words, the current pen position is automatically reset to the default coordinates.

# Canvas API - [Applying Shapes and Colors](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) 

## Colors

Up until now we have only seen methods of the drawing context. If we want to apply colors to a shape, there are two important properties we can use: fillStyle and strokeStyle.

- fillStyle = color
  - Sets the style used when filling shapes.
- strokeStyle = color
  - Sets the style for shapes' outlines.

Color is a string representing a CSS `<color>`, a gradient object, or a pattern object. We'll look at gradient and pattern objects later. By default, the stroke and fill color are set to black (CSS color value #000000).

**Note: When you set the strokeStyle and/or fillStyle property, the new value becomes the default for all shapes being drawn from then on. For every shape you want in a different color, you will need to reassign the fillStyle or strokeStyle property.**

The valid strings you can enter should, according to the specification, be CSS `<color>` values.

## Transparency

In addition to drawing opaque shapes to the canvas, we can also draw semi-transparent (or translucent) shapes. This is done by either setting the globalAlpha property or by assigning a semi-transparent color to the stroke and/or fill style.

globalAlpha = transparencyValue

Applies the specified transparency value to all future shapes drawn on the canvas. The value must be between 0.0 (fully transparent) to 1.0 (fully opaque). This value is 1.0 (fully opaque) by default.

The globalAlpha property can be useful if you want to draw a lot of shapes on the canvas with similar transparency, but otherwise it's generally more useful to set the transparency on individual shapes when setting their colors.

Because the strokeStyle and fillStyle properties accept CSS rgba color values, we can use the following notation to assign a transparent color to them.

// Assigning transparent colors to stroke and fill style

ctx.strokeStyle = 'rgba(255, 0, 0, 0.5)';<br>
ctx.fillStyle = 'rgba(255, 0, 0, 0.5)';

The rgba() function is similar to the rgb() function but it has one extra parameter. The last parameter sets the transparency value of this particular color. The valid range is again between 0.0 (fully transparent) and 1.0 (fully opaque).

## Line styles

There are several properties which allow us to style lines.

- lineWidth = value
  - Sets the width of lines drawn in the future.
- lineCap = type
  - Sets the appearance of the ends of lines.
- lineJoin = type
  - Sets the appearance of the "corners" where lines meet.
- miterLimit = value
  - Establishes a limit on the miter when two lines join at a sharp angle, to let you control how thick the junction becomes.
- getLineDash()
  - Returns the current line dash pattern array containing an even number of non-negative numbers.
- setLineDash(segments)
  - Sets the current line dash pattern.
- lineDashOffset = value
  - Specifies where to start a dash array on a line.

## Gradients

Just like any normal drawing program, we can fill and stroke shapes using linear and radial gradients. We create a CanvasGradient object by using one of the following methods. We can then assign this object to the fillStyle or strokeStyle properties.

- createLinearGradient(x1, y1, x2, y2)
  - Creates a linear gradient object with a starting point of (x1, y1) and an end point of (x2, y2).
- createRadialGradient(x1, y1, r1, x2, y2, r2)
  - Creates a radial gradient. The parameters represent two circles, one with its center at (x1, y1) and a radius of r1, and the other with its center at (x2, y2) with a radius of r2.

For example:

var lineargradient = ctx.createLinearGradient(0, 0, 150, 150);<br>
var radialgradient = ctx.createRadialGradient(75, 75, 0, 75, 75, 100);

Once we've created a CanvasGradient object we can assign colors to it by using the addColorStop() method.

- gradient.addColorStop(position, color)
  - Creates a new color stop on the gradient object. The position is a number between 0.0 and 1.0 and defines the relative position of the color in the gradient, and the color argument must be a string representing a CSS <color>, indicating the color the gradient should reach at that offset into the transition.

You can add as many color stops to a gradient as you need.

## Patterns

In one of the examples on the previous page, we used a series of loops to create a pattern of images. There is, however, a much simpler method: the createPattern() method.

- createPattern(image, type)
  - Creates and returns a new canvas pattern object. image is a CanvasImageSource (that is, an HTMLImageElement, another canvas, a `<video>` element, or the like. type is a string indicating how to use the image.

The type specifies how to use the image in order to create the pattern, and must be one of the following string values:

- repeat
  - Tiles the image in both vertical and horizontal directions.
- repeat-x
  - Tiles the image horizontally but not vertically.
- repeat-y
  - Tiles the image vertically but not horizontally.
- no-repeat
  - Doesn't tile the image. It's used only once.

We use this method to create a CanvasPattern object which is very similar to the gradient methods we've seen above. Once we've created a pattern, we can assign it to the fillStyle or strokeStyle properties. For example:

var img = new Image();<br>
img.src = 'someimage.png';<br>
var ptrn = ctx.createPattern(img, 'repeat');<br>

**Note: Like with the drawImage() method, you must make sure the image you use is loaded before calling this method or the pattern may be drawn incorrectly.**

## Shadows

Using shadows involves just four properties:

- shadowOffsetX = float
  - Indicates the horizontal distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
- shadowOffsetY = float
  - Indicates the vertical distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
- shadowBlur = float
  - Indicates the size of the blurring effect; this value doesn't correspond to a number of pixels and is not affected by the current transformation matrix. The default value is 0.
- shadowColor = color
  - A standard CSS color value indicating the color of the shadow effect; by default, it is fully-transparent black.

The properties shadowOffsetX and shadowOffsetY indicate how far the shadow should extend from the object in the X and Y directions; these values aren't affected by the current transformation matrix. Use negative values to cause the shadow to extend up or to the left, and positive values to cause the shadow to extend down or to the right. These are both 0 by default.

The shadowBlur property indicates the size of the blurring effect; this value doesn't correspond to a number of pixels and is not affected by the current transformation matrix. The default value is 0.

The shadowColor property is a standard CSS color value indicating the color of the shadow effect; by default, it is fully-transparent black.

**Note: Shadows are only drawn for source-over compositing operations.**

## Canvas fill rules

When using fill (or clip and isPointinPath) you can optionally provide a fill rule algorithm by which to determine if a point is inside or outside a path and thus if it gets filled or not. This is useful when a path intersects itself or is nested.

Two values are possible:

"nonzero": The [non-zero winding rule](https://en.wikipedia.org/wiki/Nonzero-rule), which is the default rule.
"evenodd": [The even-odd winding rule](https://en.wikipedia.org/wiki/Even%E2%80%93odd_rule).

# Canvas API - [Drawing Text](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_text)

## Drawing text

The canvas rendering context provides two methods to render text:

- fillText(text, x, y [, maxWidth])
  - Fills a given text at the given (x,y) position. Optionally with a maximum width to draw.
- strokeText(text, x, y [, maxWidth])
  - Strokes a given text at the given (x,y) position. Optionally with a maximum width to draw.

## Styling text

In the examples above we are already making use of the font property to make the text a bit larger than the default size. There are some more properties which let you adjust the way the text gets displayed on the canvas:

- font = value
  - The current text style being used when drawing text. This string uses the same syntax as the CSS font property. The default font is 10px sans-serif.
- textAlign = value
  - Text alignment setting. Possible values: start, end, left, right or center. The default value is start.
- textBaseline = value
  - Baseline alignment setting. Possible values: top, hanging, middle, alphabetic, ideographic, bottom. The default value is alphabetic.
- direction = value
  - irectionality. Possible values: ltr, rtl, inherit. The default value is inherit.

## Advanced text measurements

In the case you need to obtain more details about the text, the following method allows you to measure it.

- measureText()
  - Returns a TextMetrics object containing the width, in pixels, that the specified text will be when drawn in the current text style.
