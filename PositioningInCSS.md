# Positioning in HTML & CSS

- Relative position:
  - relative to it's normal flow postion
  - can be used with `left` `right` `top` `bottom` to change it's position
  - won't affect other elements' position


- Absolute position: 
  - to lock it's position relative to it's parent position
  - usually set it's parent position to relative
  - absolute position will take the element out of the normal flow (the element around it will change position), so make sure it has a parent element with relative position.

- Fixed position:
  - usually used on navigation bar, so that it will stick on top even when scrolled
  - position is fiexed ralative to browser window
  - element will be moved out of the normal flow (the elements behind it will shift up)

- Float:
  - take the element out of the normal flow, and relative to it's parent element
  - usually float left or right
  - use with width, elements can at the same level

- Margin:
  - set `margin:auto;` will center the block elements from four sides

### CSS flexbox:

- Use of flexbox
  - usually used with a div or section parent element, and make the parent `display: flex;`
  - this will make every elements inside the parent section has a flexible position
  - default flex-direction is row, but you can set to column, row-reverse, column-reverse.

- `justify-content:` property
  - to position the elements in the flex box, set `justify-content` in parent elements
  - default value is `flex-start`, can set to :`center`, `space-around`, `space-evenly`, `space-between`,`flex-end`
  - to see the difference in positions of these values, go to [w3school](https://www.w3schools.com/cssref/playdemo.asp?filename=playcss_justify-content&preval=space-between)

- `align-items` property
  - used when height of the child elements are not difined, and to align elements cross axis.
  - default value is `stretch`, which means by default the child element will have the same height as the parent.

- `flex-wrap` property
  - By default, a flex container will fit all flex items together. For example, a row will all be on one line, despite of their individual width or height
  
- properties to modify the individual child element
  - `flex-shrink` to shrink the element on the axis
  - `flex-grow` to make element bigger on the axis
  - `flex-basis` to set the initial size of the element
  - `align-self` to set alignment of itself, rather then all elements at once
  - `order` to rearrange each element's order in the parent
  

### CSS Grid:

 - Use of Grid
  - usually used with a div or section parent element, and make the parent `display: grid;`
  
 - Create columns in grid
  - `grid-template-columns: 50% 50%;` : this will create 2 column, each column has a width 50% of the parent elements, all elements in the container/parent will be orderd from top to bottom, left to right.
  - `grid-template-columns: auto 50px 10% 2fr 1fr;` : This snippet creates five columns. The first column is as wide as its content, the second column is 50px, the third column is 10% of its container, and for the last two columns; the remaining space is divided into three sections, two are allocated for the fourth column, and one for the fifth.
  - use `grid-gap:10px;` to set the gap between rows or columns;
  - align all items vertically `justify-items`
  - align all items horizontally `align-items`

- Properties to modify the individual child element
  -  to set the span of the element `grid-column: 1 / 3;`:This will make the item start at the first vertical line of the grid on the left and span to the 3rd line of the grid, consuming two columns.
  -  similary `grid-row`
  -  align individual item hortizontally `justify-self`: default is `stretch`
  -  align individual item vertically `align-self`

- Grid Areas













