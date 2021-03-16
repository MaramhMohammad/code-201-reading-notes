# CSS Transforms, Transitions, and Animations
 
> The transform property comes in two different settings, two-dimensional and three-dimensional.
> Each of these come with their own individual properties and values.
**Transform Syntax***

> The actual syntax for the transform property is quite simple, including the transform property followed by the value. 
> The value specifies the transform type followed by a specific amount inside parentheses.
*Example*

***Rotate, skew, and scale three different `<div>` elements:***

``` ruby
div {
  -webkit-transform: scale(1.5);
     -moz-transform: scale(1.5);
       -o-transform: scale(1.5);
          transform: scale(1.5);
}
```
# Transforms

**One of the new properties in CSS3 is `transform` property.  
This new property allows for new ways to position, size, and change elements.**

**The `transform` property can either be :**

- **two dimensional**
**or**

- **three dimensional**

**Because the browser support for the `transform` property is still not great, _vendor prefixes_ are used for best support.**

**Syntax:**

```
-vendor_prefix-transform: transform_type(amount);
transform: transform_type(amount);
```

the un-prefixed declaration comes last to overwrite the prefixed versions

## 2D Transforms

**define the length and width of the element to be distorted or transformed on the xy-plane.**

- **2D Rotate**
    - to rotate an element from 0 to 360 degrees
    - +ve value : rotate cw
    - -ve value : rotate ccw

```
transform: rotate(amount);
```
- **2D Scale**
   - to change the appearant size of an element
   - the default value is 1 , which represents the element's original size

```
transform: scale(amount);
```

## 3D Transforms

**define the length, width, and height of the element to be distorted or transformed on the xyz-space.**


# Transitions & Animations

**Another new CSS3 properties are the `transition` and `aniamation` which allow to write the behaviors for transitions and animations without using JS.**




> With scaling functions, we can increase or decrease the rendered size of an element in the X-dimension (scaleX), Y-dimension (scaleY), or both (scale). Scaling is illustrated below, where the border illustrates the original boundaries of the box, and the + marks its center point.

# 3D transform functions

![](https://gutenberghub.com/wp-content/uploads/2020/01/Screen-Recording-2020-01-18-at-01.38-PM.gif)

> As a web designer, you’re probably well acquainted with working in two dimensions, `X `and `Y`, positioning items horizontally and vertically.
> With a 3D space initialized with perspective, we can now transform elements in three spatial dimensions with the third Z dimension.
***3D transforms use the same transform property used for 2D transforms. If you’re familiar with 2D transforms, you’ll find the basic 3D transform functions similar.***

- `rotateX( angle )`
- `rotateY( angle )`
- `rotateZ( angle )`
- `translateZ( tz )`
- `scaleZ( sz )`

# Perspective
The `perspective` of an element can be set in two different ways. One way includes using the `perspective` value within the `transform` property on individual elements, while the other includes using the `perspective` property on the parent element residing over child elements being transformed.

# Animations
> When multiple transitions are required, the transition property becomes obsolete and the animation property becomes the focus. To set multiple points at which an element should transition, we use the` @keyframes` rule, which includes the animation name, any animation breakpoints, and the properties intended to be animated.
``` ruby
@keyframes slide {
  0% {
    left: 0;
    top: 0;
  }
  50% {
    left: 244px;
    top: 100px;
  }
  100% {
    left: 488px;
    top: 0;
  }
}
```
