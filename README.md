# css

CSS comprises of set of rules which contains the following,
1. Selectors (eg. div, #id, .class etc)
2. Properties (eg. color, background-color, margin)
3. Values (eg. red, 30%, 10px, block)

## `CSS file read`
The file is read from top to bottom, so any rule which is a duplicate and coming in the bottom part of the file can overwrite the original rule set on top part. (last rule in file always wins)

## `CSS Specificity`

If different styles or rules are defined for same item, there will be conflicts and css will try to resolve the conflict as given below.
The priority is in the given decreasing order (1 means highest priority)
1. `inline` styles
2. `#id` selectors
3. `.class` and `[attribute]` selectors
4. `<tag>` selectors
5. `inherited` styles

## `CSS Combinators`
A combinator is a css feature that allows you to combine two selectors in a dependent way. You can combine multiple tags or ids or classes etc to set a combined rule or style.
eg,
```
#myid h1 {
    color: red;
}
```
the above sets color to red for those h1 tag who is a child or grandchild or greatgrandchild etc of a tag with id=myid. This eg is actually a Descendant combinator. Given below are the types of combinators.

#### 1. `Adjacent Sibling`
````
div + p {

}
````
This rule eg. is applied on p tag that immediately follows a div tag, where both div and p tags are part of same parent.

#### 2. `General Sibling`
````
div ~ p {
    
}
````
This rule eg. is applied on any p tag who appears after a div tag and is a sibling to this div tag (ie, both div and p tag belongs to same parent). The difference from above (1) is, the p tag doesn't have to be an immediate sibling.

#### 3. `Child`
````
div > p {
    
}
````
This rule eg. is applied on the p tags who are only the children of a div tag (not on grand children etc)

#### 4. `Descendant`
````
div p {
    
}
````
This rule eg. is applied on the p tags who are the children, grandchildren etc of a div tag. This is the most commonly used combinator.

Note: sometimes combinators can be less performant.

## `CSS Box Model`

every element is a box in css and every elements consists of the following (ordered from inner box to outer box),
1. element content (most inner)
2. padding
3. border
4. margin (most outer)

#### `Margin Collapsing`
for those elements which are adjacent to each other, their margins will overlap or collapse into a single margin (on their meeting side). And the bigger margin wins.

#### `Block-level HTML Elements`
- A block-level element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can).
- eg, div, p, section, li, hr etc.

#### `Inline HTML Elements`
- An inline element does not start on a new line and it only takes up as much width as necessary.
- eg, span, a, b, br, img etc.
- inline elements doesn't have padding or border or margin.
- also, setting a width or height on an inline element also has no effect.


#### `property width = 100%`
- 100% means, spread the width to 100% of the screen or more accurately 100% of the container element where it is contained.
- this is by default the case for block level html elements, as they take the full width by default
- this is not the case by default for inline html elements.

#### `box-sizing property`
- the width or height property by default is set for content box only. ie, box-sizing defaults to `content-box`.
- however if you want the width and height to also consider the padding and border, you must use `box-sizing: border-box;`
- box-sizing can only go upto border (which also includes padding). So you can never include margin into box sizing.

#### `display property`
- used to change an element from block to inline or vice-versa
- `display: none;` vs `visibility: hidden;``
    - `display: none` means that the element is not visible and it also doesn't "block its position". Other elements can (and will) take its place instead.
    - `visibility: hidden` means the element is not visible, but it will also "block its position" leaving an empty position instead.
    - in both cases, the elements are still part of the dom (even though it is not displayed in the page).

#### `pseudo class`
- represented using `:class-name`
- defines the style of a special state of an element
- eg, a:hover where hover is the pseudo class name applied on anchor tag

#### `pseudo element`
- represented using `::element-name`
- defines the style of a specific part of an element
- eg, p::first-letter where first-letter is the pseudo element

#### `Grouping css rules`
- use the comma for grouping similar rules into a single rule
- eg, #myid, .myclass { color: red; }