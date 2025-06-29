---
_Source URL: [](https://ihatetomatoes.net/create-custom-preloading-screen/)._

tags: 
- '#fab #linux #hacking #custom-preloading-screen #web'

---

# How To Create A Custom Preloading Screen | CSS3 Tutorial


 [![[images/_resources/How_To_Create_A_Custom_Preloading_Screen___CSS3_Tutorial.resources/unknown_filename.1.png]]](https://ihatetomatoes.net/create-custom-preloading-screen/) 

# How To Create A Custom Preloading Screen

Are you building a one page parallax scrolling website and getting concerned about your page load time?

**Lets be honest, the one page websites can get quite bulky very quickly even when you optimize everything.**

## Related Screencast

One option to reduce the frustration of your users is to add a nice custom preloader screen.

[View Demo →](https://ihatetomatoes.net/demos/css3-preloader-transition/)[Download Files ↓](https://ihatetomatoes.net/demos/css3-preloader-transition-1125.zip)

In this tutorial we will add a CSS3 transitions to our already created [CSS3 preloader](https://ihatetomatoes.net/create-css3-spinning-preloader/).

Once the content of the page is loaded, we’ll animate the preloading screen away from the viewport with a nice transition.

**What you will learn**

*   how to use `CSS3 transitions`
*   how to `animate out` a full-screen preloader
*   how to combine `CSS3` with `JavaScript` for this technique

Open the starting files and follow the steps below.

## 1\. Add HTML and CSS for loading overlay

![[images/_resources/How_To_Create_A_Custom_Preloading_Screen___CSS3_Tutorial.resources/unknown_filename.png]]

In our `index.html` is an existing CSS3 preloader `#loader` on a white background, but we want to create a high contrast between preload screen and the content.

Lets add two parts of the preloading screen inside of `#loader-wrapper`.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06<br>07 | `<``div` `id``=``"loader-wrapper"``>`<br> `<``div` `id``=``"loader"``></``div``>`<br><br> `<``div` `class``=``"loader-section section-left"``></``div``>`<br> `<``div` `class``=``"loader-section section-right"``></``div``>`<br><br>`</``div``>` |

Now we’ll add some CSS into the `css/main.css`, just after the `@keyframes spin` declaration.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06<br>07<br>08<br>09<br>10<br>11<br>12<br>13<br>14<br>15<br>16 | `#loader-wrapper .loader-section {`<br> `position``:` `fixed``;`<br> `top``:` `0``;`<br> `width``:` `51%``;`<br> `height``:` `100%``;`<br> `background``:` `#222222``;`<br> `z-index``:` `1000``;`<br>`}`<br><br>`#loader-wrapper .loader-section.section-``left` `{`<br> `left``:` `0``;`<br>`}`<br><br>`#loader-wrapper .loader-section.section-``right` `{`<br> `right``:` `0``;`<br>`}` |

This creates a full screen dark overlay, but unfortunately it also covers our rotating `#loader` and makes the page title hard to read.

### CSS Tweaks

We will need to tweak the `z-index` of `#loader` to bring it above our dark overlay and change the color of our heading to light grey.

Find `#loader` in the stylesheet (line 43) and add the following style, also include the `h1` style just below our default `p` styles (line 34).

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06 | `#loader {`<br> `z-index``:` `1001``;` `/* anything higher than z-index: 1000 of .loader-section */`<br>`}`<br>`h``1` `{`<br> `color``:` `#EEEEEE``;`<br>`}` |

Cool, this is looking much better.

## 2\. Add and style our default content

Now lets add some default content to the page so we have something to **reveal**.

Include a new div `#content` just below the closing `#loader-wrapper` tag.

**HTML**

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04 | `<``div` `id``=``"content"``>`<br> `<``h2``>This is our page title</``h2``>`<br> `<``p``>Lorem ipsum dolor sit amet.</``p``>`<br>`</``div``>` |

As you can see this content is hidden behind our preloader screen so lets comment out the `#loader-wrapper .loader-section` for a while and style our content.

Add the following into the `main.css`.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06 | `#content {`<br> `margin``:` `0` `auto``;`<br> `padding-bottom``:` `50px``;`<br> `width``:` `80%``;`<br> `max-width``:` `978px``;`<br>`}` |

We are simply centering our content container and setting a `width` and `padding-bottom`.

And now to the fun part of animating the two preloading screen sections out of the view.

## 3\. Add preloader transition

We will move both parts out of the view using **CSS3 transforms**. When the body gets a class `.loaded`.

Add the following code to `main.css`.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06<br>07<br>08<br>09<br>10<br>11<br>12 | `/* Loaded */`<br>`.loaded #loader-wrapper .loader-section.section-``left` `{`<br> `-webkit-transform: translateX(``-100%``);` `/* Chrome, Opera 15+, Safari 3.1+ */`<br> `-ms-transform: translateX(``-100%``);` `/* IE 9 */`<br> `transform: translateX(``-100%``);` `/* Firefox 16+, IE 10+, Opera */`<br>`}`<br><br>`.loaded #loader-wrapper .loader-section.section-``right` `{`<br> `-webkit-transform: translateX(``100%``);` `/* Chrome, Opera 15+, Safari 3.1+ */`<br> `-ms-transform: translateX(``100%``);` `/* IE 9 */`<br> `transform: translateX(``100%``);` `/* Firefox 16+, IE 10+, Opera */`<br>`}` |

We’ll also fade the preloader out at the same time, lets add this to our stylesheet.

|     |     |
| --- | --- |
| 01<br>02<br>03 | `.loaded #loader {`<br> `opacity:` `0``;`<br>`}` |

Changing the `#loader` opacity to 0 seems to be working but that will make our `#content` not accessible, because the `#loader` container is still sitting on top of our content.

We need to add `visibility: hidden;` to `#loader-wrapper`.

|     |     |
| --- | --- |
| 01<br>02<br>03 | `.loaded #loader-wrapper {`<br> `visibility``:` `hidden``;`<br>`}` |

To **preview our styles** we will need to manually add the `.loaded` class to the `body` element.

[![[images/_resources/How_To_Create_A_Custom_Preloading_Screen___CSS3_Tutorial.resources/unknown_filename.2.png]]](https://ihatetomatoes.net/wp-content/uploads/2014/07/img_css3-preloader-bodyclass.png)

In Google Chrome **right click** anywhere on the page and click on **inspect element**, this will bring up the developer tools.

**Right click** on the body element and add a new attribute `class="loaded"`.

Hit enter and you’ll see our preloader screen disappear.

Great, but hang on, where are the promised **CSS3 transitions**?

Lets do them in the next step.

## 4\. Order of the animations

Firstly lets get the theory of our transition right.

**The order of our animations should be:**

1.  fade `#preloader` out
2.  animate both left and right side of the overlay out of the view
3.  animate the whole `#loader-wrapper` out of the view

We will fade out the preloader first, by adding **CSS3 transitions** to `#loader`.

**Tip:** you can get the necessary CSS3 code snippet with all the required vendor prefixes from [css3please.com](http://css3please.com/).

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05 | `.loaded #loader {`<br> `opacity:` `0``;`<br> `-webkit-transition:` `all` `0.3``s ease-out;` <br> `transition:` `all` `0.3``s ease-out;`<br>`}` |

Then we will animate both sides out of a view with a slight **0.3s delay**.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06 | `.loaded #loader-wrapper .loader-section.section-``right``,`<br>`.loaded #loader-wrapper .loader-section.section-``left` `{`<br><br> `-webkit-transition:` `all` `0.3``s` `0.3``s ease-out;` <br> `transition:` `all` `0.3``s` `0.3``s ease-out;`<br>`}` |

The first `0.3s` defines **animation duration** and the second `0.3s` defines the **animations delay**.

And lastly we will animate the whole `#loader-wrapper` out of the view using `transform: translateY(-100%)`.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06<br>07<br>08 | `.loaded #loader-wrapper {`<br> `-webkit-transform: translateY(``-100%``);`<br> `-ms-transform: translateY(``-100%``);`<br> `transform: translateY(``-100%``);`<br><br> `-webkit-transition:` `all` `0.3``s` `0.6``s ease-out;` <br> `transition:` `all` `0.3``s` `0.6``s ease-out;`<br>`}` |

As you can see, here we are setting the delay to `0.6s` which is the total duration of our **first two animations** (`0.3 + 0.3 = 0.6`).

[![[images/_resources/How_To_Create_A_Custom_Preloading_Screen___CSS3_Tutorial.resources/unknown_filename.4.png]]](https://ihatetomatoes.net/wp-content/uploads/2014/07/img_css3-preloader-bodyclass02.png)

Another way to quickly preview the body class `.loaded` is to run this line of `jQuery` code in the web developer console.

|     |     |
| --- | --- |
| 01  | `$(``'body'``).toggleClass(``'loaded'``);` |

This will toggle between our content and the preloader screen animating out.

**Pretty cool, huh?**

## 5\. Fine tuning

![[images/_resources/How_To_Create_A_Custom_Preloading_Screen___CSS3_Tutorial.resources/unknown_filename.3.png]]

To get even slicker animation for the left and right overlay we can change the easing from `ease-out` to `cubic-bezier` and adjust the timing to 0.7s.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06 | `.loaded #loader-wrapper .loader-section.section-``right``,`<br>`.loaded #loader-wrapper .loader-section.section-``left` `{`<br><br> `-webkit-transition:` `all` `0.7``s` `0.3``s cubic-bezier(``0.645``,` `0.045``,` `0.355``,` `1.000``);` <br> `transition:` `all` `0.7``s` `0.3``s cubic-bezier(``0.645``,` `0.045``,` `0.355``,` `1.000``);`<br>`}` |

Changing the duration of left and right section transition also means that we have to adjust the delay on `.loaded #loader-wrapper` animation to 1s.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06<br>07<br>08 | `.loaded #loader-wrapper {`<br> `-webkit-transform: translateY(``-100%``);`<br> `-ms-transform: translateY(``-100%``);`<br> `transform: translateY(``-100%``);`<br><br> `-webkit-transition:` `all` `0.3``s` `1``s ease-out;` <br> `transition:` `all` `0.3``s` `1``s ease-out;`<br>`}` |

## 6\. Fake it till you make it

Because we don’t have enough **“heavy”** content on our page, we will be faking the loading of the content with a simple jQuery.

You can use [imagesloaded](https://github.com/desandro/imagesloaded) by [David DeSandro](http://desandro.com/) or [PxLoader](https://github.com/thinkpixellab/PxLoader) by [Pixel Lab](http://thinkpixellab.com/) on your own projects, but we will have to fake it this time.

Include this code snippet in the `js/main.js`.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06<br>07<br>08 | `$(document).ready(``function``() {`<br><br> `setTimeout(``function``(){`<br> `$(``'body'``).addClass(``'loaded'``);`<br> `$(``'h1'``).css(``'color'``,``'#222222'``);`<br> `}, 3000);`<br><br>`});` |

That will set the body class to `.loaded` after **3 seconds** and also change the color of our `h1` to dark grey.

If you want to **learn how to implement imagesLoaded** into your project, check out the [Simple One Page Template With A Preloading Screen](https://ihatetomatoes.net/a-simple-one-page-template-with-a-preloading-screen/) tutorial.

## 7\. No JavaScript, no worries

To ensure that our content is **still accessible even without JavaScript** being turned on, we can also include the `.no-js` fallback.

|     |     |
| --- | --- |
| 01<br>02<br>03<br>04<br>05<br>06 | `.no-js #loader-wrapper {`<br> `display``:` `none``;`<br>`}`<br>`.no-js h``1` `{`<br> `color``:` `#222222``;`<br>`}` |

**And that’s it, you’ve made it!**

You’ve created a nice animated preloading screen using CSS3 animations and transitions.

Well done!

**Disclaimer**

This and [all my other tutorials](https://ihatetomatoes.net/tags/tutorial/) were created purely for educational purposes.

Please understand that if you decide to use any of the files or techniques on your own projects, you will still need to do your own cross browser testing, debugging and implementing.

**Thank you for your understanding.**

[View Demo →](https://ihatetomatoes.net/demos/css3-preloader-transition/)[Download Files ↓](https://ihatetomatoes.net/demos/css3-preloader-transition-1125.zip)

## Conclusion

What do you think about this simple preloading transition?

Have you seen a cool preloading animation sequence on other sites? Let me know in the comments.

### Other preloading tutorials

*   [A Simple One Page Template With A Preloading Screen](https://ihatetomatoes.net/a-simple-one-page-template-with-a-preloading-screen/)

Like What You're Reading?

Sign up to receive my future tutorials and demos straight to your inbox.

No spam, Unsubscribe at any time.

[![[unknown_filename.5.png]]](https://ihatetomatoes.net/get-greensock-combo/?utm_source=GC&utm_medium=banner&utm_campaign=post%20banner%20bottom)

![[d52ca462351d7ba2bc25ae6293d780d4.jpg]]

## About Petr Tichy

Petr Tichy = Ihatetomatoes. Petr is a front-end web developer with a passion for pixel-perfect code, innovative digital products and state-of-the-art websites. [Get the best of Petr's content and learn heaps.](https://ihatetomatoes.net/the-best-of/)

