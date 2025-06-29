# Bootstrap Animations - Material Design for Bootstrap
#programming/notes/webdev/frontend/css
*Source URL: [](http://mdbootstrap.com/css/animations/).*
- - - -
# Bootstrap Animations - Material Design for Bootstrap

## Showcase
Bunch of cool, fun, and cross-browser animations for you to use in your projects. Great for emphasis, home pages, sliders, and general just-add-water-awesomeness.

![[2f07fd8d29dc79f508e64850de1f49f6.png]]

- - - -
### Select an animation

- - - -
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼
* ▼

## Basic usage
Using our animation is simple.

**Step 1:** Add the class `.animated` to the element you want to animate.

**Step 2:** Add one of the following classes:

1. `.bounce`
2. `.flash`
3. `.pulse`
4. `.rubberBand`
5. `.shake`
6. `.headShake`
7. `.swing`
8. `.tada`
9. `.wobble`
10. `.jello`
11. `.bounceIn`
12. `.bounceInDown`
13. `.bounceInLeft`
14. `.bounceInRight`
15. `.bounceInUp`
16. `.bounceOut`
17. `.bounceOutDown`
18. `.bounceOutLeft`
19. `.bounceOutRight`
20. `.bounceOutUp`
21. `.fadeIn`
22. `.fadeInDown`
23. `.fadeInDownBig`
24. `.fadeInLeft`
25. `.fadeInLeftBig`
26. `.fadeInRight`
27. `.fadeInRightBig`
28. `.fadeInUp`
29. `.fadeInUpBig`
30. `.fadeOut`
31. `.fadeOutDown`
32. `.fadeOutDownBig`
33. `.fadeOutLeft`
34. `.fadeOutLeftBig`
35. `.fadeOutRight`
36. `.fadeOutRightBig`
37. `.fadeOutUp`
38. `.fadeOutUpBig`
39. `.flipInX`
40. `.flipInY`
41. `.flipOutX`
42. `.flipOutY`
43. `.lightSpeedIn`
44. `.lightSpeedOut`
45. `.rotateIn`
46. `.rotateInDownLeft`
47. `.rotateInDownRight`
48. `.rotateInUpLeft`
49. `.rotateInUpRight`
50. `.rotateOut`
51. `.rotateOutDownLeft`
52. `.rotateOutDownRight`
53. `.rotateOutUpLeft`
54. `.rotateOutUpRight`
55. `.hinge`
56. `.rollIn`
57. `.rollOut`
58. `.zoomIn`
59. `.zoomInDown`
60. `.zoomInLeft`
61. `.zoomInRight`
62. `.zoomInUp`
63. `.zoomOut`
64. `.zoomOutDown`
65. `.zoomOutLeft`
66. `.zoomOutRight`
67. `.zoomOutUp`
68. `.slideInDown`
69. `.slideInLeft`
70. `.slideInRight`
71. `.slideInUp`
72. `.slideOutDown`
73. `.slideOutLeft`
74. `.slideOutRight`
75. `.slideOutUp`

**Step 3 (additionally):** You may also want to include the class infinite for an infinite loop.

![[2f07fd8d29dc79f508e64850de1f49f6.png]]

```
<img class="animated bounce infinite" src="http://mdbootstrap.com/images/mdb-logo.png">
```

## Advanced usage
You can do a whole bunch of other stuff with animations when you combine it with jQuery or add your own CSS rules.

- - - -

Dynamically add animations using jQuery with ease:

```
$('#yourElement').addClass('animated bounceOutLeft');
```

You can also detect when an animation ends:

```
$('#yourElement').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', doSomething);
```

**Note:** `jQuery.one()` is used when you want to execute the event handler at most *once*. More information [here](http://api.jquery.com/one/).

You can also extend jQuery to add a function that does it all for you:

```
#yourElement {
  -vendor-animation-duration: 3s;
  -vendor-animation-delay: 2s;
  -vendor-animation-iteration-count: infinite;
}
```

**Note:** be sure to replace "vendor" in the CSS with the applicable vendor prefixes (webkit, moz, etc)

## Reveal Animations When Scrolling
![[cbf49f255b1324d9eed02f72ef363ff0.jpg]]
![[474ebbc21196aa01f14f435efc0a43d1.jpg]]

![[63f0b0b6d8dba2b415bd34922339aa7c.jpg]]
![[d188f80cc3b74f602598a3e178835d28.jpg]]

![[7b0dbbd840dbed8167c8dd73aa4046a2.jpg]]
![[c3535acdecbf39c88234c978ea1f1def.jpg]]

- - - -
#### Basic usage
**Step 1:** Initialize script for animations on scroll.

```
new WOW().init();
```

**Step 2:** Add the CSS class .wow to a HTML element: it will be invisible until the user scrolls to reveal it.

```
<img src="..." class="wow">
```

**Step 3:** Pick an animation style from the [list of animations](http://mdbootstrap.com/css/animations/#animations-classes) , then add the CSS class to the HTML element.

```
<img src="..." class="wow fadeInUp">
```

> Adding multiple animations via jQueryIf you want to use the same animation trough the entire page, you can use jQuery `addClass()` to make it at once.  

```
$( ".wow" ).addClass( "fadeInUp" );
```

## Options
Use one of the custom atributes below to change the behavior of the animations on scroll.

1. 
`data-wow-duration`: Change the animation duration

2. 
`data-wow-delay`: Delay before the animation starts

3. 
`data-wow-offset`: Distance to start the animation (related to the browser bottom)

4. 
`data-wow-iteration`: Number of times the animation is repeated


```
<img src="..." class="wow fadeInUp" data-wow-delay="0.6s">
```

#### Customize Settings

1. 
`boxClass`: Class name that reveals the hidden box when user scrolls

2. 
`animateClass`: Class name that triggers the CSS animations

3. 
`offset`: Define the distance between the bottom of browser viewport and the top of hidden box. When the user scrolls and reach this distance the hidden box is revealed.

4. 
`mobile`: Turn on/off animations on mobile devices.

5. 
`live`: consatantly check for new animated elements on the page


```
wow = new WOW({
    boxClass: 'wow', // default
    animateClass: 'animated', // default
    offset: 0, // default
    mobile: true, // default
    live: true // default
})
wow.init();
```
