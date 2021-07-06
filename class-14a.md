[Home](README.md)

<br>

# CSS Transforms, Transitions, and Animations

<br>

## Readings from [CSS Transforms](https://learn.shayhowe.com/advanced-html-css/css-transforms/)

<br>

### 2D Transforms

<br>

#### Transform Syntax

> The actual syntax for the `transform` property is quite simple, including the `transform` property followed by the value.

```

div {

  -webkit-transform: scale(x);
     -moz-transform: scale(x);
       -o-transform: scale(x);
          transform: scale(x);

}

```

<br>

- Two-dimensional `transforms` work on the x and y axes, known as horizontal and vertical axes. 
- Three-dimensional `transforms` work on both the x and y axes, as well as the z axis. 
- The `transform` property accepts a handful of different values. 
  - The `rotate` value provides the ability to rotate an element from 0 to 360 degrees.
  - The default point of rotation is the center of the element, 50% 50%, both horizontally and vertically. 
- To change this default origin position the `transform-origin` property may be used.
- The `perspective` of an element can be set in two different ways.
  - One way includes using the `perspective` value within the `transform` property on individual elements,.
  - The other includes using the `perspective` property on the parent element residing over child elements being transformed.-
  - The `perspective` value can be set as none or a length measurement. 
  - You can also set a `perspective-origin`.
  
<br>

#### 2D Scale

- Using the `scale` value within the `transform` property allows you to change the appeared size of an element.
- The default scale value is 1, therefore any value between .99 and .01.
- It is possible to scale only the height or width of an element using the `scaleX` and `scaleY` values.

<br>

#### 2D Translate

- The `translate` value works a bit like that of relative positioning, pushing and pulling an element in different directions without interrupting the normal flow of the document.
- sing the `translateX` value will change the position of an element on the horizontal axis while using the `translateY` value will change the position of an element on the vertical axis.

<br>

#### 2D Skew

- `skew`, is used to distort elements on the horizontal axis, vertical axis, or both. 
- Using the `skewX` value distorts an element on the horizontal axis while the `skewY` value distorts an element on the vertical axis. 

<br>

### 3D Transforms

<br>

#### 3D Rotate

- We use three new transform values, including `rotateX`, `rotateY`, and `rotateZ`.

<br>

#### 3D Scale

- Using the `scaleZ` three-dimensional transform elements may be scaled on the z axis.

<br>

#### 3D Translate

- Elements may also be translated on the z axis using the `translateZ` value. A negative value here will push an element further away on the z axis.

<br>

#### 3D Skew

- `Skew` is the one two-dimensional transform that cannot be transformed on a three-dimensional scale.

<br>

#### Transform Style

- On occasion three-dimensional transforms will be applied on an element that is nested within a parent element which is also being transformed.
- The nested, transformed elements will not appear in their own three-dimensional space.
- To allow nested elements to transform in their own three-dimensional plane use the `transform-style` property with the preserve-3d value.
- The `preserve-3d` value allows the transformed children elements to appear in their own three-dimensional plane while the flat value forces the transformed children elements to lie flat on the two-dimensional plane.

<br>

#### Backface Visibility

- When working with three-dimensional transforms, elements will occasionally be transformed in a way that causes them to face away from the screen. This may be caused by setting the `rotateY`(180deg) value for example. 
- Setting the `backface-visibility` property to hidden, and you will hide the element whenever it is facing away from the screen.

<br>

<br>

## Readings from [CSS Transitions & Animations](https://learn.shayhowe.com/advanced-html-css/transitions-animations/)

<br>

### Transitions

<br>

#### Transition Syntax

- For a transition to take place, an element must have a change in state, and different styles must be identified for each state. The easiest way for determining styles for different states is by using the `:hover`, `:focus`, `:active`, and `:target` pseudo-classes.
- There are four transition related properties in total, including `transition-property`, `transition-duration`, `transition-timing-function`, and `transition-delay`. 

<br>

#### Transitional Property

- The `transition-property` property determines exactly what properties will be altered in conjunction with the other transitional properties.
- By default, all of the properties within an element’s different states will be altered upon change. 

<br>

#### Transition Duration

- The duration in which a transition takes place is set using the `transition-duration` property. 
- The value of this property can be set using general timing values, including `seconds (s)` and `milliseconds (ms)`.

<br>

#### Transition Timing

- The `transition-timing-function` property is used to set the speed in which a transition will move.
-  Knowing the duration from the transition-duration property a transition can have multiple speeds within a single duration. A few of the more popular keyword values for the `transition-timing-function` property include `linear`, `ease-in`, `ease-out`, and `ease-in-out`.
  - The `linear` keyword value identifies a transition moving in a constant speed from one state to another.
  - The `ease-in` value identifies a transition that starts slowly and speeds up throughout the transition.
  - The `ease-out` value identifies a transition that starts quickly and slows down throughout the transition. 
  - The `ease-in-out` value identifies a transition that starts slowly, speeds up in the middle, then slows down again before ending.

  <br>

#### Transition Delay

- On top of declaring the `transition property`, `duration`, and` timing function`, you can also set a delay with the `transition-delay` property.
-  The delay sets a time value, `seconds` or `milliseconds`, that determines how long a transition should be stalled before executing.

<br>

### Animations

<br>

#### Animations Keyframes

- To set multiple points at which an element should undergo a transition, use the `@keyframes` rule.

<br>

#### Vendor Prefixing the Keyframe Rule

- The `@keyframes` rule must be vendor prefixed, just like all of the other transition and animation properties. The vendor prefixes for the `@keyframes` rule look like the following:
  - `@-moz-keyframes`
  - `@-webkit-keyframes`
  - `@-o-keyframes`

<br>

#### Animation Name

- Once the keyframes for an animation have been declared they need to be assigned to an element.
- Tthe `animation-name` property is used with the animation name, identified from the `@keyframes` rule, as the property value. 

<br>

#### Animation Duration, Timing Function, & Delay

- Once you have declared the `animation-name` property on an element, animations behave similarly to transitions.
- The `animation-duration` property. As with transitions, the duration may be set in `seconds` or `milliseconds`.
- A timing function and delay can be declared using the `animation-timing`-function and `animation-delay` properties respectively. 

<br>

#### Animation Iteration

- To have an animation repeat itself numerous times the `animation-iteration-count` property may be used.
- Values for the `animation-iteration-count` property include either an `integer` or the `infinite` keyword.

<br>

#### Animation Direction

- You may also declare the direction an animation completes using the `animation-direction` property. Values for the `animation-direction` property include `normal`, `reverse`, `alternate`, and `alternate-reverse`.

<br>

#### Animation Play State

- The `animation-play-state` property allows an animation to be played or paused using the `running` and `paused` keyword values respectively.

<br>

#### Animation Fill Mode

- The `animation-fill-mode` property identifies how an element should be styled either before, after, or before and after an animation is run. The `animation-fill-mode` property accepts four keyword values, including `none`, `forwards`, `backwards`, and `both`.

<br>

## Readings from [8 SIMPLE CSS3 TRANSITIONS THAT WILL WOW YOUR USERS](https://www.webdesignerdepot.com/2014/05/8-simple-css3-transitions-that-will-wow-your-users)

<br>

### CSS Transitions Examples

<br>

#### Fade in

- `Fade` in effects are coded in two steps:
  - First, you set the initial state.
  - Next, you set the change, for example on `hover:`.

<br>

#### Change Color

- Just set the div’s class to `color` and specify the color we want in our CSS.

<br>

#### Grow and Shrink

- Set your div’s class to `grow`/`shrink` and then add this code to your style `block:`

```

.grow:hover
{
        -webkit-transform: scale(x);
        -ms-transform: scale(x);
        transform: scale(x);
}

```
<br>

#### Rotate Element

-  Give your div the class `rotate` and add the following:

```

.rotate:hover
{
        -webkit-transform: rotateZ(xdeg);
        -ms-transform: rotateZ(xdeg);
        transform: rotateZ(xdeg);
}

```

<br>

#### Square to Circle

- Give your div the class `circle` and add this:

```

.circle:hover
{
        border-radius:x%;
}

```

<br>

#### 3D shadow

- This effect is achieved by adding a box shadow, and then moving the element on the x axis using the transform and translate properties so that it appears to grow out of the screen.

```

.threed:hover
{
        box-shadow:
                1px 1px #xxxxxx,
                2px 2px #xxxxxx,
                3px 3px #xxxxxx;
        -webkit-transform: translateX(xpx);
        transform: translateX(xpx);
}

```

<br>

#### Swing

- We can also create highly complex animations using `@keyframes`, `animation` and `animation-iteration`.

```
@-webkit-keyframes swing
{
    15%
    {
        -webkit-transform: translateX(5px);
        transform: translateX(5px);
    }
    30%
    {
        -webkit-transform: translateX(-5px);
       transform: translateX(-5px);
    } 
    50%
    {
        -webkit-transform: translateX(3px);
        transform: translateX(3px);
    }
    65%
    {
        -webkit-transform: translateX(-3px);
        transform: translateX(-3px);
    }
    80%
    {
        -webkit-transform: translateX(2px);
        transform: translateX(2px);
    }
    100%
    {
        -webkit-transform: translateX(0);
        transform: translateX(0);
    }
}

```

- This animation simply moves the element left and righ using :

```
.swing:hover
{
        -webkit-animation: swing 1s ease;
        animation: swing 1s ease;
        -webkit-animation-iteration-count: 1;
        animation-iteration-count: 1;
}
```

<br>

#### Inset border

- Give your div the class “border” and add the following CSS to your styles:

```
.border:hover
{
        box-shadow: inset 0 0 0 25px #53a7ea;
}
```
<br>
