# Flex
#programming/notes/webdev/frontend/css/flex
- - - -
* The main idea behind flex is to be able to alter items width/height/order to fill the available space in a container
* flex is for flex-grow , flex-shrink, and flex-bases
* When only one value is used for flex, for instance flex:1; , that value defaults to flex-grow
* A flex container’s direction can be changed from row (which is by default) to column with flex-direction

### flex-grow

* default property for flex
* when 1 is applied every element is being told to grow the same amount
* when 2 is applied to a div it is being told to grow 2x the size of the others

### flex-shrink

* sets the shrink factor of an element
* Only applies if the size of all flex items is larger than it’s parent container
	* if three divs each had a width of 100px and the parent div’s container was smaller than 300px the other divs would shrink to fit
* default flex-shrink is 1 which means all things shrink evenly
* flex-shrink 0 specifically says not to shrink evenly
* higher numbers can make containers shrink at higher rates

![[images/_resources/Flex.resources/Untitled.png]]

### flex-basis

* Sets initial size of container
* any grow or shrinking starts from the point flex-basis sets
* 0 would ignore item width and shrink evenly
* auto checks width
* flex:1 implies flex:1 1 0
	* to avoid even shrinking use flex-grow directly
* Giving an element the flexdisplay turns the box outer display to a block
* If flex and inlineare needed display:inline-flex can be used
* common practice is to allow even shrinking by default and only apply flex-shrink: 0 for specific items

### Flex axes

* No matter the direction flex containers can be looked at for having two axis, main and cross.
	* Axis direction changes with the container

### [[Flex - Alignment|Flex - Alignment]]
