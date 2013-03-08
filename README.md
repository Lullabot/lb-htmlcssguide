# HTML/CSS Styleguide for Lullabot
Welcome to the most stylish document you've ever seen.

## General Formatting Rules

### Indentation
Indent by 2 spaces at a time. Do not use tabs.

**html**
```html
<ul>
  <li>Lullabot</li>
  <li>Is great!</li>
</ul>
```
**css**
```css
.class {
  color: steelblue;
}
```
### Casing
We only use lowercase! Don't be a jerk!

```html
<!-- No dammit! -->
<A HREF="/YOUR-MOM">Your mom</A>
```
```html
<!-- Yeah buddy! -->
<a href="/your-mom">Your mom</a>
```

### Trailing whitespace
Always do your best to remove any trailing whitespace in your code.
Whitespace causes problems with diffs and makes vim nerds angry.

```html
<!-- Nevaaar!!1! -->
<ul>
  <li>Trailing_ </li>
  <li>whitespace </li>
</ul>
```
```html
<!-- Good dog! -->
<ul>
  <li>Sit Ubu,</li>
  <li>sit.</li>
</ul>
```

## Comments
Explain code wherever possible. Not everything you write will be obvious to
everyone who reads it later.

### HTML comments
It is appropriate to comment closing tags for easier navigation like so:

```html
<div>
  <div class="class1">
    <p>Lorem ipsum</p>
    <div class="class2">
      <p>dolor sit amet</p>
    </div><!-- closes .class2 -->
  </div><!-- closes .class1 -->
</div>
```

### CSS comments
Because many of the projects we work on use Drupal, we adhere to those
formatting guidelines, [which you can find here](http://drupal.org/node/1887862).

Some brief highlights include:

#### Multi-line comments
When describing a ruleset or set of rulesets, any comment that requires 2 or
more lines (wrapped to 80 characters) must follow the Doxygen comment style
(also called a “docblock”).

```css
/**
 * Short description using Doxygen-style comment format.
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 */
.example-rule {
}
```

Place the comment on the line immediately above the ruleset (or rulesets) it
describes. Place a blank line before the docblock comment.

#### Single-line comments

When describing a property or ruleset, any comment that can be written inside
the 80 character line length limit can use a simple CSS comment style.

```css
.example {
  /* Override the default margins. */
  margin: 0;
}

/* The example's item styling. */
.example--item {
  display: inline;
}
```

#### Other uses

It's often handy to use a comment to the right of a property's closing `;` to
note the proportional math used to generate percentage and em/rem/other values.
```css
.class {
  width: 45.625%; /* 438px / 960px */
  font-size: 1.4375em; /* 23px / 16px */
}
```

_See [SASS comments](#sass) and [LESS comments](#less)_ for more.

## HTML

### Doctype
HTML5 is preferred for all HTML documents: `<!DOCTYPE html>`.

### Semantics
Use HTML according to its purpose in the W3C spec. _E.g., Use heading elements
for headings, `p` elements for paragraphs, etc..._

Semantic HTML is an excellent way to ensure basic accessibility in your document.

```html
<!-- no, dummy! -->
<div onclick="goToRecommendations();">All recommendations</div>
```
```html
<!-- vaaaray naice! -->
<a href="/recommendations" title="Recommendations">All recommendations</a>
```

### Multimedia fallbacks
Not everyone is awesome, this is sad. It is this fact that causes the global use
of Google Chrome / Chromium to be less than 100%.

For everyone who is not awesome, we must provide fallbacks for media such as
images, videos, `canvas` animations, etc... For images that means using
meaningful alternative text (alt) and for video and audio provide transcripts
and captions, if available.

Providing alternative content is important to our overall accessibility. Blind
folks can't see our images, but their screen readers can read our `alt` text.

```html
<!-- Typically, no. Exception: purely decorative images. -->
<img src="source.jpg">
```
```html
<!-- Yahoooooohooo -->
<img src="source.jpg" alt="Source screenshot.">
```

### Separation of concerns
Keep structure (markup), presentation (styling), and behavior (scripting) apart.
Do your best to keep interaction between these concerns at a minimum.

Link as few stylesheets and scripts as possible within an HTML document, and
never ever ever ever ever ever (ever) use inline styles in your markup.

Think of these concerns in terms of money. Tasty tasty money. It costs more time
to modify structure (and therefore money) than it does to modify styles or scripts.
 * structure: $$$$$
 * styling: $$$
 * scripting: $

```html
<!-- If you do this, I will punch you. -->
<!DOCTYPE XHTMLLAWL>
<title>I am the worst</title>
<link rel="stylesheet" href="unnecessary1.css">
<link rel="stylesheet" href="unnecessary2.css">
<link rel="stylesheet" href="unnecessary3.css">
<link rel="stylesheet" href="unnecessary4.css">
<link rel="stylesheet" href="unnecessary5.css">
<h1 style="font-size: 80px; color: #000000; margin-bottom: 23px; line-height: 10000px;">Hey there, you're dumb.</h1>
<p><span style="background-color: #ff00f0; color: #132132;"><center>FUUUUuuuuuuuuuuuuuu</center></span></p>
```
```html
<!-- I'm pretty great at hugging, this might earn you one. -->
<!DOCTYPE html>
<title>Huzzah!</title>
<link rel="stylesheet" href="aggregated.css">
<h1 class="title">This is so nice, I love you.</h1>
<p>Let's be friends forever.</p>
```

### Optional tags
The [HTML5 specification](http://www.whatwg.org/specs/web-apps/current-work/multipage/syntax.html#syntax-tag-omission) defines what tags can be ommitted.

What do we say to unclosed tags? NOT TODAY!

```html
<!-- No wai!!! -->
<ul>
  <li>list item 1
  <li>list item 2
</ul>
<p>This will hurt your brain!
```
```html
<!-- Keep it familiar. -->
<ul>
  <li>list item 1</li>
  <li>list item 2</li>
</ul>
<p>Yo dawg, I heard you like closing tags.</p>
```

### Type attributes
Leave off `type` attributes for `<link>`s and `<script>`s unless you're using
something that isn't CSS or JavaScript, those are the defaults.

```html
<!-- NOPE! -->
<link rel="stylesheet" href="unnecessary.css" type="text/css">
<script src="nope.js" type="text/javascript"></script>
```
```html
<link rel="stylesheet" href="muy_bueno.css">
<script src="nope.js"></script>
```

#### General format
 * New line for
   * block elements
   * list elements
   * table elements

Indent each child of the above elements. Other elements should be written inline.

```html
<div>
  <p>You look so <em>handsome</em> when you write semantic markup.</p>
</div>
```
```html
<ul>
  <li>Falcon Punch!</li>
  <li>Falcon Kick!</li>
  <li>Show me your moves!</li>
</ul>
```
```html
<table>
  <thead>
    <tr>
      <th>Money</th>
      <th>Problems</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <td>2</td>
      <td>20</td>
    </tr>
  </tbody>
</table>
```

#### Quotation marks
Use double quotes for attribute values.

#### Self closing tags
Don't use them! This. is. HTML5. _(Although it sorta looks like Sparta)_

```html
<!-- Stop hitting yourself -->
<p>This is weak-sauce.</p><br />
<img src="yo-mamma.jpg" alt="Your Mother." />
<hr />
```
```html
<!-- Less to type, less to gripe! -->
<p>This is awesome-sauce.<br>
<img src="yo-mamma.jpg" alt="Your Mother.">
<hr>
```

## CSS

### Formatting a selector and its declarations
* Use a space between a selector and the opening `{`.
* Use a space between properties and values, after the colon.
* Use global indentation rules (two spaces, no tabs!).
* In a multiple selector scenario, break each selector to a new line.

```css
article,
section,
aside {
  color: #ddd;
  display: block;
}
```

### Declaration order
Rather than arbitrarily ordering declarations on a CSS selector, or alphabetizing
them (also arbitrary), group related declarations together, much like you would
group your SASS partials. This grouping order should help make certain properties
easier to find (based on importance) which means we can make changes rapidly.

_This is also part of Drupal's CSS formatting guidelines._

#### Declaration groupings

Group Name  | Properties
----------- | ----------------------------------------------------------------
Positioning | position, float, clear, top, right, bottom, left, direction, z-index
Box Model   | display, [(max|min)-]height, [(max|min)-]width, margin, padding, border, box-sizing, vertical-align
Other       | everything else, I'm not going to type it out for you

Other properties should be grouped with like properties in a way that makes sense.
For example:
```css
.selector {
  font-size: 1em;
  font-weight: normal;
  background-color: #911;
  background-position: top center;
}
```

For more information, see the [Declaration
order](http://drupal.org/node/1887862#declaration-order) section of Drupal's CSS
formatting guidelines.

```css
.selector {
  /* Positioning declarations */
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10;
  /* Box model declarations */
  display: inline-block;
  width: 100px;
  padding: 10px;
  border: 1px solid #333;
  /* Other declarations */
  background: #000;
  color: #fff;
  font-family: sans-serif;
  font-size: 1.1em;
}
```

#### Naming Conventions
Here at Lullabot, we don't need no stinkin' snake_casing. We also don't like
humpCasing for our CSS.

For classes and IDs spanning more than one word, use a hyphen to separate them.

```css
.not_like_this {
  color: blue;
}
.orLikeThis {
  color: black;
}
```
```css
.this-is-good {
  color: white;
}
```

Preferably, use semanticly meaningful or generic ID and class names. Names
should relate to the purpose of the content wherever possible.
Classes/IDs named in this way are less likely to change or be wrongfully
applied to markup.

In cases where a purposeful name is hard to come up with, generic or helper
names can be used.

```css
/* Boooooo presentational! */
.green-button{}
.clear{}

/* Boooooo wtf does this mean?!? */
#arf-4988-yuCky {}
```
```css
/* Awwwww yeeeah (meaningful!) */
.video {}
.author{}
.login-form {}

/* Saweeeet (helpers) */
.alt {}
.alpha {}
```

Brevity in naming should also be considered when writing CSS. This improves
readability / scannability and makes oft re-used classes easier to remember.

```css
/* Meh, not the worst */
.navigation {}
/* Ah, small and awesome like a Japanese girl's cell phone. */
.nav {}
```

#### Selectors
Don't qualify classes or IDs with element selectors unless **absolutely** necessary.

```css
/* Nuuuuuuu!!!1 */
ul#nowai {}
div.error {}
```
```css
/* Yes. This forever. */
.perfection {}
.error {}
```

#### IDs
IDs pose an interesting set of issues and there are many varying viewpoints on
how/if/when they should be used.

* The Problems:
  * IDs introduce immediate specificity.
  * ~~An ID is **255 times** more specific than one class [ref.](http://news.ycombinator.com/item?id=4388649) [ref2.](http://csswizardry.com/2011/09/when-using-ids-can-be-a-pain-in-the-class/)~~ [^1]
  * IDs can only be used once in a page. Ever. Seriously.
* The Benefits:
  * IDs marginally quicker for a browser to reference.

[^1]: This was proven not quite correct somewhere, when we @carwin finds the
article, he'll make sure to update this footnote.

In the face of this evidence, it seem spretty obvious that we should avoid IDs
if we want to avoid problems of specificity (which we do). However, because
Lullabots work so often with Drupal this borders on the impossible.

##### Getting around Drupal's ID madness
[Fences](http://drupal.org/project/fences)

While we cannot completely avoid IDs in our Drupal markup, we _can_ avoid
actually styling based on the ID selectors therein.

The idea here is that classes can be stacked to infinity with barely measurable
performance hits. So rather than add an ID and styling it in a very specific
way, we can instead create styles of re-usable classes and stack those on
elements to get a particular look. This is DRY.

Here is an over-the-top example to illustrate the point:

```html
<!-- Example crappy markup -->
<div id="block-block-1" class="block block-views specific-class">
  <h2 class="block-title">Title</h2>
  <p>We gotta style this, yo!</p>
</div>
```
```css
/* Problematic */
#block-block-1 {
  width: 400%;
  background: #000;
  height: 240%;
  border-radius: 8px;
  border-color: white;
  font-family: Arial, sans-serif;
}
#block-block-1 h2 {
  color: #fff;
  font-size: 1.2em;
  margin-bottom: 20px;
}
#block-block-1 p {
  font-size: 1em;
}
```
```html
<!-- Example better markup (again, just illustrative) -->
<div id="block-block-1" class="block block-views super-big specific-class rounded">
  <h2 class="block-title">Title</h2>
  <p>We gotta style this, yo!</p>
</div>
```
```css
/* Preferable */
.block {
  border-color: white;
  font-family: Arial, sans-serif;
}
.super-big {
  height: 240%;
  width: 400%;
}
.rounded {
  border-radius: 8px;
}
.specific-class {
  background: #000;
  font-size: 1em;
}
.block-title {
  color: #fff;
  font-size: 1.2em;
}
```
Both examples above produce the same styles, however the second example lends
itself to re-use and DRYness much better than the first. `.super-big` could be
applied to any other element that needs the same height and width, `.rounded`
could be applied to any element that needs rounded corners.

#### Shorthand
A _general_ rule of thumb is to "Use shorthand all the time." There will be
exceptions to this rule quite often, which is why it's only a _general_ rule.

#### Units
* 0 units
  * Do not use units after "0" values.

  ```css
  margin: 0;
  box-shadow: 0 0 10px #000;
  ```

* Leading 0s
  * Omit leading "0"s in values.

  ```css
  /* fail! */
  opacity: 0.5;
  /* win! */
  opacity: .5;
  ```

unit     | usage
-------- | -------------------------------------------------------------------
em, rem  | these are good to be used most everywhere you want proportional sizing.
%        | % values make super happy fun time everywhere! use them all day! huzzah!
unitless | * use for `line-height` - is calculated as a multiplier of the font-size.
vw, vh, vmin | Don't use viewport units unless you're specifically targetting a browser that supports them.

#### Colors
Different web browsers support different color declarations. In instances where
CSS-only colors are important to the continuity of the overall design, colors
should be declared in every way for the widest support. This also acts as a
future-proofing mechanism since, as browsers develop and begin to use more
complex color declarations our stylesheets will be serving the most
advanced colors possible.

Colors should be declared in this order (least advanced -> most advanced):
`hex, rgb, hsl, rgba, hsla`

```css
/* Complex Colors Cooperate Cleanly! */
text-shadow: 0 0 3px #000;                /* IE stops here */
text-shadow: 0 0 3px rgb(0, 0, 0);        /* Opera Mini stops here */
text-shadow: 0 0 3px hsl(0, nan%, 0%);    /* Flock stops here */
text-shadow: 0 0 3px rgba(0, 0, 0, .5);   /* Safari 4 stops here */
text-shadow: 0 0 3px hsla(0, nan%, .5%);  /* Chrome stops here */
```

Additionally, whenever possible, use 3 digit Hexadecimal values.
```css
/* no thanks nerd! */
color: #000000;
```
```css
/* booya grandma! */
color: #000;
color: #dfded0;
```
