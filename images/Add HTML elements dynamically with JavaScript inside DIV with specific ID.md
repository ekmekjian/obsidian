# Add HTML elements dynamically with JavaScript inside DIV with specific ID
#programming/notes/javascript
*Source URL: [](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id).*
- - - -
# Add HTML elements dynamically with JavaScript inside DIV with specific ID
[http://engine.adzerk.net/r?e=eyJhdiI6NDE0LCJhdCI6NCwiYnQiOjAsImNtIjo0NzE0OTMsImNoIjoxMTc4LCJjayI6e30sImNyIjoxNjI3NzcwLCJkaSI6Ijk0YTIzY2VhODQ4YjRhYmRiMGY2OGM0ZmI4ZTFkNWZjIiwiZG0iOjEsImZjIjoxOTI0NDQ5LCJmbCI6MjE0MjMxMiwiaXAiOiI3MS4xODcuMTU4LjE5MyIsImt3IjoiamF2YXNjcmlwdCIsIm53IjoyMiwicGMiOjAsImVjIjowLCJwciI6MTYwNCwicnQiOjEsInJmIjoiaHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS8iLCJzdCI6ODI3NywidWsiOiJ1ZTEtY2JhYjBhNDdjOGI5NDkyMGFmZTJkOWJhZTUwMjE1OTgiLCJ6biI6NDMsInRzIjoxNDc0NTEwMTc1OTQxLCJiZiI6dHJ1ZSwicG4iOiJhZHplcms3NDYwOTE2MDQiLCJ1ciI6Imh0dHA6Ly9zdGFja292ZXJmbG93LmNvbS9qb2JzL3JlbW90ZT91dG1fc291cmNlPXdlYnNpdGUmdXRtX21lZGl1bT1iYW5uZXImdXRtX2NvbnRlbnQ9bGVhZGVyYm9hcmRfNSZ1dG1fY2FtcGFpZ249aG91c2VfYWRzX1JPU19TTyJ9&s=Z7SLocWb4Cq_eI-VX3fjFuTmp2s](http://engine.adzerk.net/r?e=eyJhdiI6NDE0LCJhdCI6NCwiYnQiOjAsImNtIjo0NzE0OTMsImNoIjoxMTc4LCJjayI6e30sImNyIjoxNjI3NzcwLCJkaSI6Ijk0YTIzY2VhODQ4YjRhYmRiMGY2OGM0ZmI4ZTFkNWZjIiwiZG0iOjEsImZjIjoxOTI0NDQ5LCJmbCI6MjE0MjMxMiwiaXAiOiI3MS4xODcuMTU4LjE5MyIsImt3IjoiamF2YXNjcmlwdCIsIm53IjoyMiwicGMiOjAsImVjIjowLCJwciI6MTYwNCwicnQiOjEsInJmIjoiaHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS8iLCJzdCI6ODI3NywidWsiOiJ1ZTEtY2JhYjBhNDdjOGI5NDkyMGFmZTJkOWJhZTUwMjE1OTgiLCJ6biI6NDMsInRzIjoxNDc0NTEwMTc1OTQxLCJiZiI6dHJ1ZSwicG4iOiJhZHplcms3NDYwOTE2MDQiLCJ1ciI6Imh0dHA6Ly9zdGFja292ZXJmbG93LmNvbS9qb2JzL3JlbW90ZT91dG1fc291cmNlPXdlYnNpdGUmdXRtX21lZGl1bT1iYW5uZXImdXRtX2NvbnRlbnQ9bGVhZGVyYm9hcmRfNSZ1dG1fY2FtcGFpZ249aG91c2VfYWRzX1JPU19TTyJ9&s=Z7SLocWb4Cq_eI-VX3fjFuTmp2s)
12  [favorite](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#)
**1**

Ok, poeple, I need your help. I've found some code here on Stackoverflow (can't find that link) which generate HTML code dynamically via JS. Here is code:

```js
function create(htmlStr) {
    var frag = document.createDocumentFragment(),
        temp = document.createElement('div');
    temp.innerHTML = htmlStr;
    while (temp.firstChild) {
        frag.appendChild(temp.firstChild);
      }
        return frag;
    }

    var fragment = create('<div class="someclass"><a href="www.example.com"><p>some text</p></a></div>'); 

    document.body.insertBefore(fragment, document.body.childNodes[0]);
```

This code work's just fine! But generated code apears on top of page, right below `body` tag. My wish is to generate that code inside empty `div` with specific `id="generate-here"`.

So output will be:

```js
<div id="generate-here">
    <!-- Here is generated content -->
</div>
```

I know that I can't see generated content with "view source". I only need to generate that content just in this particular place with `#generate-here`. I'm Javascript noob, so if anyone can just rearrange this code that will be perfect. Thanks a lot!

P.S. I know how to do this with Jquery, but I need native and pure JavaScript in this case.

[javascript](http://stackoverflow.com/questions/tagged/javascript)

|     |     |
| --- | --- |
| [share](http://stackoverflow.com/q/11805251)|[improve this question](http://stackoverflow.com/posts/11805251/edit) | asked Aug 4 '12 at 1:41![[208ac871c2ee1f944fb786f0959e062e.png]][Miljan Puzović](http://stackoverflow.com/users/1550040/miljan-puzovi%c4%87)**4,583**11127 |

 

|     |     |
| --- | --- |
| 1   |     |

You can view the actual html on the page with firebug: [getfirebug.com](http://getfirebug.com/) – [Gordon Gustafson](http://stackoverflow.com/users/89989/gordon-gustafson) [Aug 4 '12 at 1:45](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15687855_11805251)

|     |     |
| --- | --- |
|     |     |

Thanks, I didn't know that :) But more important is to generate that code on that particular place. – [Miljan Puzović](http://stackoverflow.com/users/1550040/miljan-puzovi%c4%87) [Aug 4 '12 at 1:46](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15687863_11805251)

## 1 Answer
[active](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id?answertab=active#tab-top) [oldest](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id?answertab=oldest#tab-top) [votes](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id?answertab=votes#tab-top)

11  accepted

All you need to do is change the last line. This will add the created element as the **last** child of the div:

```
document.getElementById("generate-here").appendChild(fragment);     
```

This will add the created element as the **first** child of the div:

```
var generateHere = document.getElementById("generate-here");
generateHere.insertBefore(fragment, generateHere.firstChild);
```

You can also use innerHTML to just replace everything with new text (as you do in your `create` function). Obviously this one doesn't require you to keep the `create` function because you need an html string instead of a DOM object.

```
var generateHere = document.getElementById("generate-here");
generateHere.innerHTML = '<div class="someclass"><a href="www.example.com"><p>some text</p></a></div>';
```

|     |     |     |
| --- | --- | --- |
| [share](http://stackoverflow.com/a/11805304)|[improve this answer](http://stackoverflow.com/posts/11805304/edit) | [edited Aug 4 '12 at 2:00](http://stackoverflow.com/posts/11805304/revisions) | answered Aug 4 '12 at 1:51![[8379dc25724c470e36b2f7f659b060ad.jpg]][Gordon Gustafson](http://stackoverflow.com/users/89989/gordon-gustafson)**20.2k**1782138 |

 

|     |     |
| --- | --- |
|     |     |

I don't know why, but that # generate-here is still empty. I've tried both codes, and it doesn't work :/ – [Miljan Puzović](http://stackoverflow.com/users/1550040/miljan-puzovi%c4%87) [Aug 4 '12 at 2:02](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15687969_11805304)

|     |     |
| --- | --- |
|     |     |

@MiljanPuzović did you keep all your other code the same and just change the last line? I edited to clarify. :) – [Gordon Gustafson](http://stackoverflow.com/users/89989/gordon-gustafson) [Aug 4 '12 at 2:04](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15687980_11805304)

|     |     |
| --- | --- |
|     |     |

Yes, i've just changed the last line :) And that didn't work. I'll try now with innerHTML. – [Miljan Puzović](http://stackoverflow.com/users/1550040/miljan-puzovi%c4%87) [Aug 4 '12 at 2:06](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15687989_11805304)

|     |     |
| --- | --- |
|     |     |

Interesting, they all work for me in this example. Just comment out the one you want to try; I listed all three. [jsfiddle.net/XydQ9](http://jsfiddle.net/XydQ9/) – [Gordon Gustafson](http://stackoverflow.com/users/89989/gordon-gustafson) [Aug 4 '12 at 2:13](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15688026_11805304)

|     |     |
| --- | --- |
|     |     |

I don't see even from example that is working :/ See picture [i.imgur.com/mke2H.jpg](http://i.imgur.com/mke2H.jpg) I'm using Chrome, maybe is some bug in Chrome.... No, i've looked also from Firefox, same problem. – [Miljan Puzović](http://stackoverflow.com/users/1550040/miljan-puzovi%c4%87) [Aug 4 '12 at 2:16](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#comment15688046_11805304)

[show **5** more comments](http://stackoverflow.com/questions/11805251/add-html-elements-dynamically-with-javascript-inside-div-with-specific-id#)

## Your Answer

### Sign up or [log in](http://stackoverflow.com/users/login?ssrc=question_page&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f11805251%2fadd-html-elements-dynamically-with-javascript-inside-div-with-specific-id%23new-answer)
Sign up using Google

Sign up using Facebook

Sign up using Email and Password

### Post as a guest
**Name**
**Email**

By posting your answer, you agree to the [privacy policy](http://stackexchange.com/legal/privacy-policy) and [terms of service](http://stackexchange.com/legal/terms-of-service).

## Not the answer you're looking for? Browse other questions tagged [javascript](http://stackoverflow.com/questions/tagged/javascript) or [ask your own question](http://stackoverflow.com/questions/ask).
