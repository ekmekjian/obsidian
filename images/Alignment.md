# Alignment
#programming/notes/webdev/frontend/css/flex
- - - -
# Flex - Alignment
* Flex can be used to arrange containers that have  a specific size
* With justify-content: space-between would distribute containers differently inside a another container
	* This property aligns content along the main axis
* If you wanted the containers to align on the cross axis the align-item: center; is the best option
* Both justify-content and align-items are based on the main and cross axis
	* When flex-direction: column; is used justify-content aligns vertically and align-items aligns horizontally
	* default values are horizontal for justify-content and vertical for align-items

![[00-basic-terminology.svg]]

## The Main Axis

* Defined using flex-direction with properties
	* row
	* row-reverse
	* column
	* column-reverse
* using either row or row-reverse set the main axis in an inline direction

![[basics1.png]]

* column or column-reverse uses a block direction

![[basics2.png]]

## Start and end lines
