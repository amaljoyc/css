# css

CSS comprises of set of rules which contains the following,
1. Selectors (eg. div, #id, .class etc)
2. Properties (eg. color, background-color, margin)
3. Values (eg. red, 30%, 10px, block)

### CSS file read
The file is read from top to bottom, so any rule which is a duplicate and coming in the bottom part of the file can overwrite the original rule set on top part. (last rule in file always wins)

### CSS Specificity

If different styles or rules are defined for same item, there will be conflicts and css will try to resolve the conflict as given below.
The priority is in the given decreasing order (1 means highest priority)
1. `inline` styles
2. `#id` selectors
3. `.class` and `[attribute]` selectors
4. `<tag>` selectors
5. `inherited` styles

### CSS Combinators
A combinator is a css feature that allows you to combine two selectors in a dependent way. You can combine multiple tags or ids or classes etc to set a combined rule or style.
eg,
```
#myid h1 {
    color: red;
}
```
the above sets color to red for those h1 tag who is a child or grandchild or greatgrandchild etc of a tag with id=myid. This eg is actually a Descendant combinator. Given below are the types of combinators.

#### 1. Adjacent Sibling
````
div + p {

}
````
This rule eg. is applied on p tag that immediately follows a div tag, where both div and p tags are part of same parent.

#### 2. General Sibling
````
div ~ p {
    
}
````
This rule eg. is applied on any p tag who appears after a div tag and is a sibling to this div tag (ie, both div and p tag belongs to same parent). The difference from above (1) is, the p tag doesn't have to be an immediate sibling.

#### 3. Child
````
div > p {
    
}
````
This rule eg. is applied on the p tags who are only the children of a div tag (not on grand children etc)

#### 4. Descendant
````
div p {
    
}
````
This rule eg. is applied on the p tags who are the children, grandchildren etc of a div tag. This is the most commonly used combinator.

Note: sometimes combinators can be less performant.

## CSS Box Model

every element is a box in css and every elements consists of the following (ordered from inner box to outer box),
1. element content (most inner)
2. padding
3. border
4. margin (most outer)

#### Margin Collapsing
for those elements which are adjacent to each other, their margins will overlap or collapse into a single margin (on their meeting side). And the bigger margin wins.

#### Block-level HTML Elements
- A block-level element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can).
- eg, div, p, section, li, hr etc.

#### Inline HTML Elements
- An inline element does not start on a new line and it only takes up as much width as necessary.
- eg, span, a, b, br, img etc.
- inline elements doesn't have padding or border or margin.
- also, setting a width or height on an inline element also has no effect.


#### property width = 100%
- 100% means, spread the width to 100% of the screen or more accurately 100% of the container element where it is contained.
- this is by default the case for block level html elements, as they take the full width by default
- this is not the case by default for inline html elements.

#### box-sizing property
- the width or height property by default is set for content box only. ie, box-sizing defaults to `content-box`.
- however if you want the width and height to also consider the padding and border, you must use `box-sizing: border-box;`
- box-sizing can only go upto border (which also includes padding). So you can never include margin into box sizing.

#### display property
- used to change an element from block to inline or vice-versa
- `display: none;` vs `visibility: hidden;``
    - `display: none` means that the element is not visible and it also doesn't "block its position". Other elements can (and will) take its place instead.
    - `visibility: hidden` means the element is not visible, but it will also "block its position" leaving an empty position instead.
    - in both cases, the elements are still part of the dom (even though it is not displayed in the page).

#### pseudo class
- represented using `:class-name`
- defines the style of a special state of an element
- eg, a:hover where hover is the pseudo class name applied on anchor tag

#### pseudo element
- represented using `::element-name`
- defines the style of a specific part of an element
- eg, p::first-letter where first-letter is the pseudo element

#### Grouping css rules
- use the comma for grouping similar rules into a single rule
- eg, #myid, .myclass { color: red; }

### Main and Important CSS Properties

- color -> to change text color
- background-color
- display -> to change the way an element is positioned (block or inline or none)
- padding -> distance between content and border
- border
- margin -> to add some spacing around a box (outside the border of a box)
- width
- height

### Addtional Info on CSS selectors

we already saw how you can combine classes and or ids with CSS combinators above. Those combinators are used to target elements which are either siblings and children. However, we could also combine them in another way as shown below,

```
<a href="" class="active"></a>

a.active {

}
```

here `a.active` means, select those anchor tag which has a class `active`.

#### `id vs class selectors`
- it is recommended to use class selectors over id selectors. The reason is because, class selectors are only used for css styling purposes, whereas ids are also used for html linking purposes
- so even if you have only 1 element to style, use it as a class selector rather than an id selector.
- use id selector for styling only if you already need to use that element as an id for linking purpose.

#### !important
```
div {
    color: red !important;
}
```
- `!important` will overwrite specificity and all other selectors
- in general don't use this (in 99% cases).

#### box-shadow property
eg,
```
box-shadow: 2px 2px 2px 2px rgba(0, 0, 0, 0.5)
```

#### to build a circle
- use `border-radius: 50%` -> will convert square to circle
- and then give appropriate same height and width values.

#### to center an element horizontally
- for text we can use, `text-align: center`
- for other elements like eg, `div`, we can center then using margin auto as given below (auto below will make sure equal space is used for left and right)
```
margin: 0 auto;
```
- `margin: auto` will keep equal space to left, right, top, bottom.

#### using float for positioning
- float is now not recommended anymore, as it brings lot of issues.
- you can do the same with flex box a lot more easier and simpler.
- float can basically be used to position an element to left or right
- it is important to clear the float just below its use, so that the elements after it is not affected with floating

```
float: right; -> will float to right
```

in order to clear the flow for next element, we do,
```
clear: both; -> will clear all left and right floats from above
```

#### using margin auto to center a div or other block element
- `margin: auto;` will center an element horizontally
- By assigning auto to the left and right margins of an element, they take up the available horizontal space in the element’s container equally – and thus the element gets centered.
- `auto` in both top and bottom margins is always computed to 0px, so it cannot be used for centering elements vertically
- `auto` will not work in floated, inline and absolute elements

### Positioning elements in CSS
- Default position property applied automatically in an html document is `position: static`
- Other position property values are
    - absolute
    - relative
    - fixed
    - sticky (new value, so not much browser support)
- The position property is often used together with the following additional properties,
    - top
    - bottom
    - left
    - right
- `top: 0;` or `bottom: 0;` when used together with `position: fixed;` can be used to fix a nav bar to top or footer to bottom respectively.