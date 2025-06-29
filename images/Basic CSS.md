# Basic CSS
#programming/notes/webdev/frontend/css
- - - -
## **Basic Syntax**

* CSS uses a particular style rule for it’s declarations. It uses a selector as the block to hold the style declarations which are semicolon separated and each declaration is made of property:value
![](Basic%20CSS/90KletpecxRRBk00AwkeWijWPezKABIUB27IusD5zbDMlUUB7a.jpeg)

## **Selectors**

* Refers to the HTML element that you want to apply style too.

### **Universal Selector**

* Universal selector applies styles to all elements

```css
* {
 color: purple;
}
```

### **Type Selectors**

* Selects all elements of the given type

```css
div {
 color: white;
}
```

### **Class Selectors**

* Selects all elements with the given class name
* Syntax for class selectors require a period before the class name
* A class name can be used on multiple and different elements
* A single element can have multiple class name. Each separated by a space, but the class name themselves can **NOT** have a space in it's own name which is why multi word class names use a hyphen

```html
<div class="alert-text">
 Please agree to our terms of service.
</div>
```

```css
.alert-text {
 color: red;
}
```

### **ID Selectors**

* same as Class Selectors, ID Selectors add style to elements with an id attribute
* Syntax for id selectors use a hashtag as a preface, similar too class that has a period for the preface

```html
<div id="title">My Awesome 90's Page</div>
```

```css
#title {
 background-color: red;
}
```

### **Grouping Selector**

* If there are multiple selectors that share common CSS you can group common styles with grouping selectors while using class/ID selectors for any unique styles
* Benefits of this is to save as much space as possible

```css
.read,
.unread {
 color: white;
 background-color: black;
}

.read {
 /* several unique declarations */
}

.unread {
 /* several unique declarations */
}
```

### **Chaining Selectors**

* Selectors can be chained for increased organization chaining multiple classes/ids without separation
* Two elements with subsection have another class, header and preview. Chaining allows us to style a specific element based on the
* When chaining selectors you concat the first with the second without any spaces or commas and this says style the element that contain **BOTH** the first and second class
* You can only chain selectors of the same type. So you can't chain a class with and id.

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red;
}
```

### **Descendant Combinator**

* Combines selectors look at the last selector in a block to style. The former being the parent element
* The syntax for this is using a space between the selectors
* In the current example only B and C contents would be styled because the have parent directory indicated (.ancestor)
* There is no limit to how many can be applied .one .two .three .four would be acceptable

```html
<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
    <div class="contents"> <!-- C -->
    </div>
  </div>
</div>
<div class="contents"></div> <!-- D -->
```

```css
.ancestor .contents {
  /* some declarations */
}


```

## **Basic Properties:**

### **color/background-Color**

* color sets text color and background-color sets the background color of an element
* Both properties can accept different type of values (hex, rgb, hsl)

```
p {
  /* hex example: */
  color: #1100ff;
  /* rgb example: */
  color: rgb(100, 0, 127);
  /* hsl example: */
  color: hsl(15, 82%, 56%);
}
```

### **Typography Basics and text-align**

* font-family a single value or comma-separated list that contain fonts for an element
	* The reason to use multiple is so that if a browser doesn't accept the first font it would go down the list till it found one that worked
	* Fonts can be specified using the "font family name" using double quotes due to some font have multiple words "Times New Roman" and "generic family name" sans-serif
	* common practice is to use multiple font names so that there is something to fall back on

font-family: "Times New Roman", sans-serif;

* font-size sets the size of font

font-size: 22px

* font-weight affects the boldness of text
	* Values can be keywords like bold or a number from 1 - 1000
	* Values will be incremented of 100 up to 900 but this can depend on the font

font-weight: bold

* text-align will align text horizontally within an element, and you can use the common keywords you may have come across in word processors as the value for this property

text-align: center

### **Image Height and Width**

* If height and width are not set  uses the images original values
* If you want to adjust and image without losing proportions set height to auto and adjust width value
	* It's good practice to include both properties in and image because the original may cause the site to shift other elements waiting for the picture to load. Setting the size reserves that space for the image

```css
img {
 height: auto;
 width: 500px;
}
```

## **The Cascade of CSS**

* There are many reasons as to why a page is not looking correctly.
	* Default styles by the browser can change the page. If you don't set any CSS for an element the browser may use it's own and may not look right.
	* Cascade determines which rules get applied to HTML using different factors.

### **Specificity**

* CSS declaration that is more specific has it's rules applied over less specific.
* Selectors come in different specificity some are ID, Class, and Type selectors
	* ID selector takes priority of Class selectors, even if there are multiple.
	* Class take priority of Type
	* Type take priority over anything lower.
	* Calculate specificity Start at 0, add 1000 for style attribute, add 100 for each ID, add 10 for each attribute, class or pseudo-class, add 1 for each element name or pseudo-element.
* In example 1 even though both are classes because rule 2 is using a more specific

example 1
```
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}


```

* In example 2 even though rule 2 has two classes rule 1 take priority because ID is more specific

example 2
```
/* rule 1 */
#subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}


```

* In example 3 both rule two and one have classes rule 1 using chaining selector while rule 2 is using a descendant combinator. Combinators such as +, ~, >, and an empty space for selectors do not add to the specificity meaning that both rule 1 and 2 are equal in specificity values

example 3
```
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class .second-class {
  font-size: 24px;
}


```

* In example 4 rule one is using a universal selector while 2 is using a type selector. Even though type has the lowest priority universal has no priority value what's so ever

example 4
```
/* rule 1 */
* {
  color: black;
}

/* rule 2 */
h1 {
  color: orange;
}


```

### **Inheritance**

* Means that when and element receives CSS its nested descendants get those styles as well
* If one of the child elements were specified that style would take priority over the inheritance
* Even though ID has higher priority because that style was meant for the parent and not the child the child style would take priority as being more specific

```
<div id="parent">
  <div class="child"></div>
</div>


```

```
#parent {
  color: red;
}

.child {
  color: blue
}


```

### **Rule Order**

* After all factors have been considered the final say is the order rule
* Simply which ever was last defined is the winner

```
.alert {
  color: red;
}

.warning {
  color: yellow;
}


```

## **Adding CSS to HTML**

### **External CSS**

* Most common where the CSS is in its own file and imported into the HTML through  tags with a self-closing link element
* href is the attribute that points to the location of the CSS file. In this file the style.css is located in the same directory as the HTML
* rel attribute is required and tells the relationship between the HTML and the linked fil

```
<head>
  <link rel="stylesheet" href="styles.css">
</head>


```

### **Internal CSS**

* refers to CSS embbeded within the HTML
* using CSS inside HTML requires  tags which then go inside of  tags
* The benefits of this method is for simple single page sites but the bigger the site the bigger the HTML and things can get cluttered

```
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>...</body>


```

### **Inline CSS**

* makes it possible to add CSS directly into the HTML element
* No selectors necessary because we are directly styling the element.
* the style= attribute with it's value in double quotes
* Great for uniquely styling any specific element
* But can add unnecessary clutter if used much

```
<body>
  <div style="color: white; background-color: black;">...</div>
</body>


```

## **Box Model**

* Everything in a webpage is a rectangular box. Essentially when positioning elements its just nesting and stacking these boxes
* Things get difficult because there are multiple ways to manipulate the space between each box
	* margin - increases the space between boxes
	* padding - increases spaces between edge of the box and the content of the element
	* border - adds space between margin and padding
* The box model when takes multiple spacing attributes calculates them together when sizing
	* A box that receives a padding:10px; height:100px; width:100px; border:20px; would create a size of 180 instead of the defined 100 by height and width because it adds both padding and border from top/bottom/sides and adds them to height
	* to avoid this box-sizing: border-box; property is used to take the padding and border into account when height and width are defined keeping the size set to what ever height and width are set too
	* Common practice is to set box-sizing: border-box; to the universal selector so that all elements keep true to size

![](Programming/Web%20Development/Basic%20CSS/Untitled.png)

## **Block and inline boxes**

* Most used
* Refer to behavior in page flow and relation to other boxes
* Boxes also come with additional types of inner and outer display type

### **Block box for outer display behavior**

* breaks onto new line
* fills space in container inline
* width and height properties respected
* Padding, margin, and border will cause other elements to be pushed away from the box
