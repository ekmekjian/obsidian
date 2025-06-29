Basic CSS

# Basic Syntax

 CSS uses a particular style rule for it’s declarations. It uses a selector as the block to hold the style declarations which are semicolon separated and each declaration is made of property:value

![[Pasted image 20220317095516.png]]
 Refers to the HTML element that you want to apply style too.
--- 
### Universal Selector

 Universal selector applies styles to all elements

```CSS​​
* {
  color: purple;
}
```

Type Selectors

 Selects all elements of the given type

```CSS
div {
  color: white;
}
```

Class Selectors

 Selects all elements with the given class name
 Syntax for class selectors require a period before the class name
-
