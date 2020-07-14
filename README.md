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
