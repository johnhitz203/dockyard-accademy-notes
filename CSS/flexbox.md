# Flexbox

## Flex Grow

## Flex Shrink

## Flexbox Wrap
* Causes the the elements in a container to wrap to the next row
  * Set on the parent element
  * wrap-reverse reverses the behavior and causes the elements to wrap to row above
  * Default is no wrap

## Flex Basis
* Sets the starting width of an element
  * Similar to minimum width except the `min-with` prevents the item form shrinking bellow the value set and `flex-bases` allows the element to shrink as it normally would
  * Can be set directly on individual elements
    * Each element can have its own value
    * Makes the flex-grow rate apply to the width on a given element
  
## Flex Property
* Combines the properties of `flex-grow`, `flex-shrink`, and `flex-basis` into one property
  * Format is `flex: flex-grow_value, flex-shrink_value, flex-basis_value`
  * Often used as `flex: 1` which sets `flex-grow `, `flex-shrink 1`, and `flex-basis 0` 

## Flex Flow and Axis
* Flex flow controls the flow direction of elements in a container element
  * `flex-flow: row` - Default
    * Elements line up in a row
  * `flex-flow: column` - Stacks element one on top of the other
    * Elements line up vertically in a column
  * `column-reverse`
  * `row-reverse`
  * `nowrap`
  * `wrap`
  ### Properties Applied By Axis
  * main axis - defaults to horizontal
    * `justify-content`
      * `center`
      * `flex-end`
      * `flex-start`
      * `space-around`
      * `space-between`
  * cross axis - defaults to vertical
    * `align-items`
      * `flex-start`
      * `flex-end`
      * `center`
      * `stretch`
      * `baseline`

## Grid
* Parent element
  ```css
  {
    display: grid;
    flex-wrap;
    justify-content: space-between;
  }
  ```
* Child Element
  ```css
  {
    flex: 0 1 32%
  }
  ```

## Element Order
 * Sets the order of the elements
   * Default is `{order: 0;}`
   * Lowest number is placed last
