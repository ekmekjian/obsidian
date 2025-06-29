# CSS3 Backgrounds
#programming/notes/webdev/frontend/css/background-image
Source URL: [](http://www.w3schools.com/css/css3_backgrounds.asp).
- - - -
[w3schools.com](http://www.w3schools.com/)

* [HTML](http://www.w3schools.com/html/default.asp)
* [CSS](http://www.w3schools.com/css/default.asp)
* [JAVASCRIPT](http://www.w3schools.com/js/default.asp)
* [SQL](http://www.w3schools.com/sql/default.asp)
* [PHP](http://www.w3schools.com/php/default.asp)
* [BOOTSTRAP](http://www.w3schools.com/bootstrap/default.asp)
* [JQUERY](http://www.w3schools.com/jquery/default.asp)
* [ANGULAR](http://www.w3schools.com/angular/default.asp)
* [XML](http://www.w3schools.com/xml/default.asp)

# CSS3 Backgrounds
[❮ Previous](http://www.w3schools.com/css/css3_border_images.asp) [Next ❯](http://www.w3schools.com/css/css3_colors.asp)

- - - -
## CSS3 Backgrounds
CSS3 contains a few new background properties, which allow greater control of the background element.

In this chapter you will learn how to add multiple background images to one element.

You will also learn about the following new CSS3 properties:

* `background-size`
* `background-origin`
* `background-clip`

- - - -
## Browser Support
The numbers in the table specify the first browser version that fully supports the property.

Numbers followed by -webkit-, -moz-, or -o- specify the first version that worked with a prefix.

| Property |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
| background-image(with multiple backgrounds) | 4.0 | 9.0 | 3.6 | 3.1 | 11.5 |
| background-size | 4.01.0 -webkit- | 9.0 | 4.03.6 -moz- | 4.13.0 -webkit- | 10.510.0 -o- |
| background-origin | 1.0 | 9.0 | 4.0 | 3.0 | 10.5 |
| background-clip | 4.0 | 9.0 | 4.0 | 3.0 | 10.5 |

- - - -
## CSS3 Multiple Backgrounds
CSS3 allows you to add multiple background images for an element, through the `background-image` property.

The different background images are separated by commas, and the images are stacked on top of each other, where the first image is closest to the viewer.

The following example has two background images, the first image is a flower (aligned to the bottom and right) and the second image is a paper background (aligned to the top-left corner):

### Example
{ background-image: url(img_flwr.gif), url(paper.gif);
    background-position: right bottom, left top;
    background-repeat: no-repeat, repeat;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background_multiple)

Multiple background images can be specified using either the individual background properties (as above) or the `background` shorthand property.

The following example uses the `background` shorthand property (same result as example above):

### Example
{ background: url(img_flwr.gif) right bottom no-repeat, url(paper.gif) left top repeat;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background_multiple2)

- - - -
## CSS3 Background Size
The CSS3 `background-size` property allows you to specify the size of background images.

Before CSS3, the size of a background image was the actual size of the image. CSS3 allows us to re-use background images in different contexts.

The size can be specified in lengths, percentages, or by using one of the two keywords: contain or cover.

The following example resizes a background image to much smaller than the original image (using pixels):

Original background image:

## Lorem Ipsum Dolor
Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.

Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.

Resized background image:

## Lorem Ipsum Dolor
Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.

Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.

Here is the code:

### Example
{ background: url(img_flower.jpg);
    background-size: 100px 80px;
    background-repeat: no-repeat;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background-size)

The two other possible values for `background-size` are `contain` and `cover`.

The `contain` keyword scales the background image to be as large as possible (but both its width and its height must fit inside the content area). As such, depending on the proportions of the background image and the background positioning area, there may be some areas of the background which are not covered by the background image.

The `cover` keyword scales the background image so that the content area is completely covered by the background image (both its width and height are equal to or exceed the content area). As such, some parts of the background image may not be visible in the background positioning area.

The following example illustrates the use of `contain` and `cover`:

### Example
{ background: url(img_flower.jpg);
    background-size: contain;
    background-repeat: no-repeat;}
{ background: url(img_flower.jpg);
    background-size: cover;
    background-repeat: no-repeat;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background-size_contain)

- - - -
## Define Sizes of Multiple Background Images
The `background-size` property also accepts multiple values for background size (using a comma-separated list), when working with multiple backgrounds.

The following example has three background images specified, with different background-size value for each image:

### Example
{ background: url(img_flwr.gif) left top no-repeat, url(img_flwr.gif) right bottom no-repeat, url(paper.gif) left top repeat;
    background-size: 50px, 130px, auto;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background_multiple3)

- - - -
## Full Size Background Image
Now we want to have a background image on a website that covers the entire browser window at all times.

The requirements are as follows:

* Fill the entire page with the image (no white space)
* Scale image as needed
* Center image on page
* Do not cause scrollbars

The following example shows how to do it; Use the html element (the html element is always at least the height of the browser window). Then set a fixed and centered background on it. Then adjust its size with the background-size property:

### Example
html { background: url(img_flower.jpg) no-repeat center fixed;
    background-size: cover;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background_full)

- - - -
## CSS3 background-origin Property
The CSS3 `background-origin` property specifies where the background image is positioned.

The property takes three different values:

* border-box - the background image starts from the upper left corner of the border
* padding-box - (default) the background image starts from the upper left corner of the padding edge
* content-box - the background image starts from the upper left corner of the content

The following example illustrates the `background-origin` property:

### Example
{ border: 10px solid black;
    padding: 35px;
    background: url(img_flwr.gif);
    background-repeat: no-repeat;
    background-origin: content-box;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background-origin)

- - - -
## CSS3 background-clip Property
The CSS3 `background-clip` property specifies the painting area of the background.

The property takes three different values:

* border-box - (default) the background is painted to the outside edge of the border
* padding-box - the background is painted to the outside edge of the padding
* content-box - the background is painted within the content box

The following example illustrates the `background-clip` property:

### Example
{ border: 10px dotted black;
    padding: 35px;
    background: yellow;
    background-clip: content-box;}
[Try it Yourself »](http://www.w3schools.com/css/tryit.asp?filename=trycss3_background-clip)

- - - -
## Test Yourself with Exercises!
[Exercise 1 »](http://www.w3schools.com/css/exercise.asp?filename=exercise_css3_backgrounds1)  [Exercise 2 »](http://www.w3schools.com/css/exercise.asp?filename=exercise_css3_backgrounds2)  [Exercise 3 »](http://www.w3schools.com/css/exercise.asp?filename=exercise_css3_backgrounds3)  [Exercise 4 »](http://www.w3schools.com/css/exercise.asp?filename=exercise_css3_backgrounds4)  [Exercise 5 »](http://www.w3schools.com/css/exercise.asp?filename=exercise_css3_backgrounds5)

- - - -
## CSS3 Background Properties
| Property | Description |
| --- | --- |
| [background](http://www.w3schools.com/cssref/css3_pr_background.asp) | A shorthand property for setting all the background properties in one declaration |
| [background-clip](http://www.w3schools.com/cssref/css3_pr_background-clip.asp) | Specifies the painting area of the background |
| [background-image](http://www.w3schools.com/cssref/pr_background-image.asp) | Specifies one or more background images for an element |
| [background-origin](http://www.w3schools.com/cssref/css3_pr_background-origin.asp) | Specifies where the background image(s) is/are positioned |
| [background-size](http://www.w3schools.com/cssref/css3_pr_background-size.asp) | Specifies the size of the background image(s) |

[❮ Previous](http://www.w3schools.com/css/css3_border_images.asp) [Next ❯](http://www.w3schools.com/css/css3_colors.asp)

#### [COLOR PICKER](http://www.w3schools.com/colors/colors_picker.asp)
[![[images/_resources/CSS3_Backgrounds.resources/colorpicker.gif]]](http://www.w3schools.com/colors/colors_picker.asp)

#### [LEARN MORE](http://www.w3schools.com/howto/default.asp)
[HTML Cards](http://www.w3schools.com/howto/howto_css_cards.asp)
[Google Maps](http://www.w3schools.com/howto/howto_google_maps.asp)
[Animated Buttons](http://www.w3schools.com/howto/howto_css_animate_buttons.asp)
[Modal Boxes](http://www.w3schools.com/howto/howto_css_modals.asp)
[Modal Images](http://www.w3schools.com/howto/howto_css_modal_images.asp)
[Tooltips](http://www.w3schools.com/howto/howto_css_tooltip.asp)
[Loaders](http://www.w3schools.com/howto/howto_css_loader.asp)
[Filter List](http://www.w3schools.com/howto/howto_js_filter_lists.asp)
[JS Animations](http://www.w3schools.com/howto/howto_js_animate.asp)
[Progress Bars](http://www.w3schools.com/howto/howto_js_progressbar.asp)
[Dropdowns](http://www.w3schools.com/howto/howto_js_dropdown.asp)
[Slideshow](http://www.w3schools.com/howto/howto_js_slideshow.asp)
[Accordions](http://www.w3schools.com/howto/howto_js_accordion.asp)
[Side Navigation](http://www.w3schools.com/howto/howto_js_sidenav.asp)
[Top Navigation](http://www.w3schools.com/howto/howto_js_topnav.asp)
[HTML Includes](http://www.w3schools.com/howto/howto_html_include.asp)
[Tabs](http://www.w3schools.com/howto/howto_js_tabs.asp)

#### SHARE
[](http://www.facebook.com/sharer.php?u=http://www.w3schools.com/css/css3_backgrounds.asp)[](https://twitter.com/home?status=Currently%20reading%20http://www.w3schools.com/css/css3_backgrounds.asp)[](https://plus.google.com/share?url=http://www.w3schools.com/css/css3_backgrounds.asp)
[[Metric prefix scale]]

#### [CERTIFICATES](http://www.w3schools.com/cert/default.asp)
HTML, CSS, JavaScript, PHP, jQuery, Bootstrap and XML.

[Read More »](http://www.w3schools.com/cert/default.asp)

- - - -
- - - -

[[ ERROR]]
[PRINT PAGE](http://www.w3schools.com/css/css3_backgrounds.asp)
[FORUM](http://www.w3schools.com/forum/default.asp)
[ABOUT](http://www.w3schools.com/about/default.asp)

- - - -
#### Top 10 Tutorials
[HTML Tutorial](http://www.w3schools.com/html/default.asp)
[CSS Tutorial](http://www.w3schools.com/css/default.asp)
[JavaScript Tutorial](http://www.w3schools.com/js/default.asp)
[W3.CSS Tutorial](http://www.w3schools.com/w3css/default.asp)
[Bootstrap Tutorial](http://www.w3schools.com/bootstrap/default.asp)
[SQL Tutorial](http://www.w3schools.com/sql/default.asp)
[PHP Tutorial](http://www.w3schools.com/php/default.asp)
[jQuery Tutorial](http://www.w3schools.com/jquery/default.asp)
[Angular Tutorial](http://www.w3schools.com/angular/default.asp)
[XML Tutorial](http://www.w3schools.com/xml/default.asp)

#### Top 10 References
[HTML Reference](http://www.w3schools.com/tags/default.asp)
[CSS Reference](http://www.w3schools.com/cssref/default.asp)
[JavaScript Reference](http://www.w3schools.com/jsref/default.asp)
[W3.CSS Reference](http://www.w3schools.com/w3css/w3css_references.asp)
[Browser Statistics](http://www.w3schools.com/browsers/default.asp)
[PHP Reference](http://www.w3schools.com/php/php_ref_array.asp)
[HTML Colors](http://www.w3schools.com/colors/colors_names.asp)
[HTML Character Sets](http://www.w3schools.com/charsets/default.asp)
[jQuery Reference](http://www.w3schools.com/jquery/jquery_ref_selectors.asp)
[AngularJS Reference](http://www.w3schools.com/angular/angular_ref_directives.asp)

#### Top 10 Examples
[HTML Examples](http://www.w3schools.com/html/html_examples.asp)
[CSS Examples](http://www.w3schools.com/css/css_examples.asp)
[JavaScript Examples](http://www.w3schools.com/js/js_examples.asp)
[W3.CSS Examples](http://www.w3schools.com/w3css/w3css_examples.asp)
[HTML DOM Examples](http://www.w3schools.com/js/js_dom_examples.asp)
[PHP Examples](http://www.w3schools.com/php/php_examples.asp)
[ASP Examples](http://www.w3schools.com/asp/asp_examples.asp)
[jQuery Examples](http://www.w3schools.com/jquery/jquery_examples.asp)
[Angular Examples](http://www.w3schools.com/angular/angular_examples.asp)
[XML Examples](http://www.w3schools.com/xml/xml_examples.asp)

#### Web Certificates
[HTML Certificate](http://www.w3schools.com/cert/default.asp)
[HTML5 Certificate](http://www.w3schools.com/cert/default.asp)
[CSS Certificate](http://www.w3schools.com/cert/default.asp)
[JavaScript Certificate](http://www.w3schools.com/cert/default.asp)
[jQuery Certificate](http://www.w3schools.com/cert/default.asp)
[PHP Certificate](http://www.w3schools.com/cert/default.asp)
[Bootstrap Certificate](http://www.w3schools.com/cert/default.asp)
[XML Certificate](http://www.w3schools.com/cert/default.asp)

- - - -

W3Schools is optimized for learning, testing, and training. Examples might be simplified to improve reading and basic understanding. Tutorials, references, and examples are constantly reviewed to avoid errors, but we cannot warrant full correctness of all content. While using this site, you agree to have read and accepted our [terms of use](http://www.w3schools.com/about/about_copyright.asp), [cookie and privacy policy](http://www.w3schools.com/about/about_privacy.asp). [Copyright 1999-2016](http://www.w3schools.com/about/about_copyright.asp) by Refsnes Data. All Rights Reserved.
[Powered by W3.CSS](http://www.w3schools.com/w3css/).
[![[images/_resources/CSS3_Backgrounds.resources/w3schoolscom_gray.gif]]](http://www.w3schools.com/)
