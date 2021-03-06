Slippy - HTML Slides
====================

Demo
----

See the example slide deck live on [slides.seld.be](http://slides.seld.be/?file=2010-05-30+Example.html)

How to: Navigate slide decks
----------------------------

Navigate, double click anywhere, press space or use the left/up and right/down arrow keys

Go to a slide directly, press number keys and then enter

Get an overview, press escape or delete then click on a slide to go straight to it

How to: Make your own slide deck
--------------------------------

At the core, slide decks are simple HTML files. Every slide can be any html element,
but is typically a div or section. You initialize slippy by calling `slippy()` on a
jQuery selection, for example, if you add the `slide` class to all your slide divs,
use: `$(".slide").slippy({})`. Using the `slide` class is recommended because that's
what the default CSS file is using, but you're free to do what you want.

To get quickly started, you can use the `2010-05-30 Example.html` file which is an
example slide deck, and edit it, however if you prefer to do it all by hand, here are
the parts you need to add to your HTML file:

    <!-- jQuery + history plugin -->
    <script type="text/javascript" src="jquery.min.js"></script>
    <script type="text/javascript" src="jquery.history.js"></script>

    <!-- Slippy core js file -->
    <script type="text/javascript" src="slippy.js"></script>

    <!-- Slippy structural styles -->
    <link type="text/css" rel="stylesheet" href="slippy.css"/>

    <!-- Slippy theme (feel free to change it) -->
    <link type="text/css" rel="stylesheet" href="slippy-pure.css"/>

In addition, if you want syntax highlighting, you should add the following files.
Using it is simple, just create a `<pre>` tag with a `class="brush: js"` to highlight
javascript code for example. You can read more on the
[SyntaxHighlighter](http://alexgorbatchev.com/SyntaxHighlighter/) website itself.

    <!-- Syntax highlighting core file  -->
    <script type="text/javascript" src="highlighter/shCore.js"></script>

    <!-- Syntax highlighting brushes, this one is only for javascript -->
    <script type="text/javascript" src="highlighter/shBrushJScript.js"></script>

    <!-- Syntax highlighting core CSS and a theme -->
    <link type="text/css" rel="stylesheet" href="highlighter/shCore.css"/>
    <link type="text/css" rel="stylesheet" href="highlighter/shThemeEclipse.css"/>

Finally you should initialize Slippy and the syntax highlighter:

    <script type="text/javascript">
        $(function() {
            $(".slide").slippy({});
            SyntaxHighlighter.all();
        });
    </script>

The slippy() call takes an option object, which accepts the following keys:

- animLen, duration for default animations (0 = disabled)
- animInForward, receives a slide and animates it
- animInRewind, receives a slide and animates it
- animOutForward, receives a slide and animates it
- animOutRewind, receives a slide and animates it
- baseWidth, defines the base for img resizing, if you don't want only
  full-width images, specify this as the pixel width of a slide so that
  images are scaled properly (default is 620px wide)
- ratio, defines the width/height ratio of the slides, defaults to 1.3 (620x476)
- margin, the fraction of screen to use as slide margin, defaults to 0.15

Exporting PDFs
--------------

To upload your presentation on SlideShare, or to share it with others, it can be convenient to
export it to a PDF. Slippy comes with a CLI utility that does just that.

The only requirement is that you download [PhantomJS](http://code.google.com/p/phantomjs/downloads/list) (1.3+)
and [pdftk](http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/) and place the executables in the bin/phantomjs
and bin/pdftk dirs or make them accessible via your PATH environment variable. If you're on linux you can
probably install pdftk with your distro's package manager.

Once that is done, you can call the script using `bin/slippy-pdf.sh <path to your html presentation> <path to the pdf file to generate>`.

It'll take a while and then should output a 4:3 PDF file. If you don't like the aspect ratio or size,
you can change the viewport size in the `bin/phantom-slippy-to-pdf.js` file. If you have rendering issues (missing
images or such), try increasing the delay, or rendering again, sometimes PhantomJS just fails without apparent reason.

Author
------

Jordi Boggiano - <j.boggiano@seld.be>
<http://seld.be/> - <http://twitter.com/seldaek>

See also the list of [contributors](https://github.com/Seldaek/slippy/contributors) which participated in this project.

Contribute
----------

<a href="http://flattr.com/thing/14125/Slippy-HTML-Presentations" target="_blank"><img src="http://api.flattr.com/button/button-static-50x60.png" title="Flattr this" border="0" /></a> If you like this piece of software, please consider giving back with Flattr.

Code contributions, bug reports and ideas are obviously also much welcome.

Changelog
---------

- 1.0.0
  - Switched license to BSD
  - Slide decks files are now standalone html files that don't need php
    - However it is recommended if you have code blocks since it will convert html special chars automatically
    - Note that this breaks compatibility with previous slide decks, since the js/css files have to be included by hand in it now
  - Added layout functionality, see the slide on layouts in the example deck for docs
  - Added parameters to the main slippy js command that enable users to easily tweak/override things, see example file
  - Added swipe/double-tap support on touch devices
  - Added PDF export functionality using PhantomJS
  - Splitted css in structural/theme stylesheets for easy customization
  - Improved the default theme for better readability on projectors
  - Auto-sizing to the browser dimensions
  - Added page up, page down support for prev/next slide, and home/end to go to the begining or end of presentaiton
  - Animations are going the right way now when using overview/direct input and going backwards
  - Added a template to render the slide repository page
  - Added a packager that embeds everything for easy distribution of slides as one html file
  - Added incremental slides functionality (use the incremental class on any elements to make them appear one by one)
  - JS Alerts are now cleared when changing slide, but stay visible longer
  - Fixed bug preventing "0" to be used to switch to slides

- 0.9.0
  - Initial Public Release

License
-------

Slippy is licensed under the New BSD License, which means you can do pretty much anything you want with it - However, I encourage you to share your slides and stylesheets if you make some, but there is no obligation whatsoever.

New BSD License - see the src/LICENSE file for details

Compatibility
-------------

It should work with all browsers, except for the overview function that does not work in IE8 and below.
