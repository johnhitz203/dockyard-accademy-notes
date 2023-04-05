# CSS Grid
## Grid Wrapper
* A parent element that wraps child elements that will be arranged inside the grid.
* {display: grid}` - creates the gird wrapper
## Columns
* {grid-template-columns:} - defines the number of columns with one of the following formats
  * `grid-template-column: 33.3% 33.3% 33.3%;`
  * `grid-template-column: 1fr 1fr 1fr;`
    * (n)fr - creates a column that is n fractions of the total width
  * `grid-template-column: repeat(3, 1fr);` 
    * repeats the fr 3 times
  
  ## Rows and Gaps
  ### Rows
  * Default behavior - The number of rows are automatically determined by the number of child elements and the number of columns (ie 3 columns with 9 items will create 3 rows)
  * Controlling Row Hight
    * `grid-auto-rows: 200px` sets the height of all rows to 200px
      * minmax(200px,auto)- sets the 200 px as minimum height and auto as the maximum
    * `grid-template-rows: 200px 100px 300px` - creates 3 rows with the given heights
    * `grid-template-rows: repeat(3, 200px)` - creates 3 rows each set to 200px
    * `grid-template-rows: repeat(3, minmax(200px, auto)` - as above
### Gap
* Creates space between columns and rows
  * `grid-column-gap: 10px` - sets the gap between columns
  * `grid-row-gap: 10px` - sets the gap between rows
  * `grid-gap: 10px` - set the gap between both columns and rows

## Column Lines (video 4)
* Grid lines are n + 1 where n is the number of columns
* Can create an overlay to show the column lines (video 7 @ 7:00)
  * 


## Span Keyword
* `grid-column: span 3` - creates 3 columns starting at column 1 and ending at column 4, and is is equivalent to 
* `grid-column: 1/4`

## Align and Justify
* Placed on the parent element to control how the children are place with in it's self
  * <ins>align-self & justify-self</ins> - placed on the child element to determine how it places it's self with in the grid container parent

## Grid Areas
* `{grid-template-area}` - Assigns elements to columns by the position of the name in a given row
* `{grid-area: [element_name]}` - Assigns the element to a specific grid-Areas
* Example:
```html
<div id="content>
  <header>Header</header>
  <main>Main</main>
  <aside>Aside</aside>
  <nav>Nav</nav>
  <footer>Footer</footer>
</content>
```
```css
#content{
    display: grid;
    grid-template-colum: repeat(4, fr1);
    grid-template-row: minmax(100px, auto);
    max-width: 960px;
    margin: 0 auto;
    grid-template-areas:
    "header  header  header  header"
    [
      "aside   aside   main    main" |
      "aside   .       main    main"
      ]
    /* . -> leaves an open space in the grid layout */
    "section section section section"
    "section section section section"
    "footer  footer  footer  footer"
}

#content > *{
  background: #3bbced;
  padding: 30px;
}

header { grid-area: header; }
main { grid-area: main; }
aside { grid-area: aside; }
section { grid-area: section; }
footer { grid-area: footer }
