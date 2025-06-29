[source](https://nakedsecurity.sophos.com/2016/05/26/why-you-cant-trust-things-you-cut-and-paste-from-web-pages/)
#javascript #hacking #vulnerability
# Why you can’t trust things you copy and paste from web pages


# Why you can’t trust things you copy and paste from web pages

26 May 2016
		25
		[Vulnerability](https://nakedsecurity.sophos.com/category/security-threats/vulnerability/), [Web Browsers](https://nakedsecurity.sophos.com/category/technologies/web-browsers/)

### Get the latest security news in your inbox.

![[glue.jpg]]

by[Mark Stockley](https://nakedsecurity.sophos.com/author/mark-stockley/)


Put away your wget and curl, your SOAP clients and WSDLs, WebDAV servers, REST APIs and JSON callbacks; when it comes to moving data off websites and on to your computer the sticky stuff that greases the wheels is _copy and paste_.

This side of haptic gloves, Ctrl+C and Ctrl+V is as close as we can get to reaching out and grabbing something off the web. It’s the cyber-grab you cyber-learn in your cyber-infancy and never cyber-forget because you endlessly cyber-repeat it.

Repetition teaches us that what goes in to our hand when we Ctrl+C (grab something) comes out of our hand when we Ctrl+V (let it go).

But what if it didn’t?

What if you reached out to grab one apple but when you opened your hand you had a pear? Or a piranha?

## Pastejacking with Javascript

Javascript is a programming language that can be embedded into HTML web pages and, perhaps more than any other technology, it’s what turned the web from a collection of documents you could read into a collection of applications you can use.

It can’t break out from your browser and put things on your computer, but within the sandboxed confines of a web page it can access all sorts of powerful functionality that makes possible everything from [Nyan Cat](http://www.nyan.cat/) to Gmail (and, when you’re all nyaned-out, [Chrome Experiments](https://www.chromeexperiments.com/).)

With your permission it can trigger push notifications and geolocation, and without your permission Javascript can store megabytes of data in your browser’s cache, open windows, move things around the page, draw things on virtual canvases, log your keystrokes and track your mouse.

And, thanks to a function called execCommand('copy') it can paste cyber-pirhanas to your clipboard too.

An excellent [demonstration of how to do this and why it’s a bad idea](https://github.com/dxa4481/Pastejacking) has been put together by hacker Dylan Ayrey on Github and his personal site [security.love](https://security.love/).

In the demo, users are invited to copy the text echo "not evil" and witness with horror as what they actually paste is the cruelly different echo "evil"\\n.

The execCommand('copy') command that performs this magic has to have a trigger, known as an ‘event’ to run, so Ayrey’s code uses the keydown event which happens to be triggered when you use the keyboard shortcut for Ctrl+C. The code then waits 0.8 seconds and switches out the text from your clipboard.

The snippets of text in the example aren’t just words, they’re valid computer commands that can be run inside a terminal window (that mysterious, featureless black window with white text that ‘power users’ never see and real geeks use to get work done).

The \\n on the end of echo "evil"\\n is a newline and if you type a newline into a terminal window it will run the preceding command immediately.

In other words Ayrey has offered you something that won’t run until you tell it to and then replaced it behind your back with something else that will run as soon as you paste it.

Luckily for anyone using Ayrey’s example it’s a benign command that ends up getting run, but of course it doesn’t have to be; an attacker could just as easily make you think you’re copying something safe and replace it with a command that deletes your home directory and steals your password file.

## Pastejacking with CSS

If you switch off Javascript altogether or use a browser add-on like NoScript that allows you to choose when to run javascript you can render yourself invulnerable to Ayrey’s pastejacking technique, but there’s another way to smuggle commands in to your clipboard that doesn’t rely on Javascript.

HTML is the language the web pages are written in but it’s CSS (Cascading Style Sheets) that determines how they look.

It’s CSS that rearranges pages to work in everything from phones to cinema screens, sizes text, adds columns, adds colour, rounds edges, positions logos, and supplies the white space that designers love to add and clients love to ask designers to remove.

It can also be used to position things on the page or, more usefully for malicious pastejackers, off the page where you can’t see it.

Hacker Jann Horn has [a demo that shows just this technique](http://thejh.net/misc/website-terminal-copy-paste) on his website [thejh.net](http://thejh.net/).

In Horn’s example, what appears to be a command to copy a git source repository:

```
git clone git://git.kernel.org/pub/scm/utils/kup/kup.git
```
…is in fact a much longer command that still copies a git source repository but not before it’s written out a personalised warning alongside the first line of your password file.

```
git clone /dev/null; clear; echo -n "Hello ";whoami|tr -d '\n';echo -e '!\nThat was a bad idea. Don'"'"'t copy code from websites you don'"'"'t trust!
Here'"'"'s the first line of your /etc/passwd: ';head -n1 /etc/passwd
git clone git://git.kernel.org/pub/scm/utils/kup/kup.git
```
Under the hood, in the page’s code, all the text is there as you see it above but Horn has used CSS to display the nasty bit in the middle 100 pixels above and to the left of the page where you can’t see it.

## Don’t trust cut and paste from web pages

For programmers, developers, admins, hackers and geeks of all flavours the web is the most useful learning tool imaginable. Examples of code are everywhere on the web ready to be deciphered, discussed, questioned, picked over, picked apart and, above all copied, pasted and run.

Unfortunately, thanks to CSS, you don’t necessarily know what you’re copying and, thanks to Javascript, you don’t necessarily know what’s in your clipboard.

There are terminals that will warn you if you’re pasting something that ends in a newline character, and there are browsers, say Lynx or Mosaic, that can insulate you from the modernity of CSS and Javascript. The best defence, however, is one that anyone with the knowledge and inclination to copy and paste commands into a terminal should know by heart already: you can’t trust user input.

I suggest that you don’t rely on third party tools to save you – just assume that everything is hostile until you’ve sanitised it or proved it’s OK.

The simplest way to do that is to paste anything you copy from a web page into something that can’t run commands, like NOTEPAD or TextEdit and examine it first.

Then copy it again and paste it where you really want it.

[Follow @MarkStockley](https://twitter.com/intent/follow?original_referer=https%3A%2F%2Fnakedsecurity.sophos.com%2F2016%2F05%2F26%2Fwhy-you-cant-trust-things-you-cut-and-paste-from-web-pages%2F&ref_src=twsrc%5Etfw&region=follow_link&screen_name=MarkStockley&tw_p=followbutton)
		[788 followers](https://twitter.com/intent/user?original_referer=https%3A%2F%2Fnakedsecurity.sophos.com%2F2016%2F05%2F26%2Fwhy-you-cant-trust-things-you-cut-and-paste-from-web-pages%2F&ref_src=twsrc%5Etfw&region=count_link&screen_name=MarkStockley&tw_p=followbutton)

[Follow @NakedSecurity](https://twitter.com/intent/follow?original_referer=https%3A%2F%2Fnakedsecurity.sophos.com%2F2016%2F05%2F26%2Fwhy-you-cant-trust-things-you-cut-and-paste-from-web-pages%2F&ref_src=twsrc%5Etfw&region=follow_link&screen_name=NakedSecurity&tw_p=followbutton)
		[56.7K followers](https://twitter.com/intent/user?original_referer=https%3A%2F%2Fnakedsecurity.sophos.com%2F2016%2F05%2F26%2Fwhy-you-cant-trust-things-you-cut-and-paste-from-web-pages%2F&ref_src=twsrc%5Etfw&region=count_link&screen_name=NakedSecurity&tw_p=followbutton)

