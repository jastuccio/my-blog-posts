https://www.learnenough.com/css-and-layout-tutorial-tutorial

## 1.2 CSS overview and history

### Vendor Prefixing
>To get around the potential confusion that could happen if things work differently from browser to browser, the browser vendors typically add a prefix to the experimental styles, such as -webkit-, -moz-, and -ms- (respectively for WebKit, Mozilla, and Microsoft browsers). This allows the applied style to target specific browsers in case the support differs.

>For instance, the CSS transition declaration (covered in Section 7.4) was implemented in most browsers before it was a part of the official spec, and to use it you would have needed to declare the styling like the following examples with vendor prefixes:

```
  -webkit-transition: all 0.1s linear;
  -moz-transition: all 0.1s linear;
  -ms-transition: all 0.1s linear;
  transition: all 0.1s linear;
```

The first rule here specifically targets browsers that use the WebKit layout engine (which includes Safari and Chrome), while the second targets browsers using Mozilla’s Gecko engine (principally Firefox), and the third targets Microsoft browsers (Internet Explorer and Edge). Finally, the fourth rule is an unprefixed declaration—in this case, just transition by itself—which is included so that when support becomes official we won’t have to go back into our code and add it in. (The transition style is supported by all major browsers today, so if you see the prefixed versions in code that you are working on, you can safely delete them.)

-----

## 2.1 Naming Things

When naming classes and ids:
  * think in terms of how something functions or what its intent is
  *  it’s usually best to be specific
     * a class called "box1" is a bad idea because the name is so generic
     * Better to introduce a class like "bio-box" because it references a specific kind of element on the page
  * avoid is naming classes or ids after how the element looks on the page



>If you get more into front-end development, it might not be a bad idea to look into some of the conventions other developers are using:

1. [Block Element Modifier (BEM)](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
2. [Object Oriented CSS (OOCSS)](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)
3. [Scalable and Modular Architecture for CSS (SMACSS)](https://smacss.com/)

Whether you find these systems useful or not, the most important thing is to strive for some semblance of consistency.

-----
## 2.2 When and Why: ID's vs Classes

>Our view is as follows:
strive to use ids only when you absolutely have to (for example, if you are using JavaScript, and then use them only for JavaScript).
>when you use an id to apply styles, it is nearly impossible to change that styling with another declaration without making your code full of ugly hacks.

*  ids have a higher specificity

-----

 Don't rely on styles targeted at ids.

``` css
#exec-bio.alert {
    background: red;
  }
  ```
 Over time you’ll find yourself adding more and more of these hyper-specific declarations. That isn’t the most effective way to use CSS.

 -----
## 2.3 Priority & Specifity

 in the case of conflicting CSS rules, the final one gets applied.

 ``` css
   .bio-box {
    width: 75%;
  }
  /* The 50% rule would be applied. It comes later in the stylesheet */
  .bio-box {
    width: 50%;
  }
```

  The full list of CSS priority rules appears in Table 1. You don’t need to memorize this table—over time you’ll get a feel for how the priority works. Also, of all these rules, only numbers 3 and 5–8 are priorities that you’ll have to understand, and you should strenuously try and avoid using numbers 1 (Box 8) and 2 (makes for difficult-to-maintain code). Numbers 4 and 9 are out of your control.
```
1	Importance	Adding !important (e.g., "width: 100% !important") to a value overrides all other similar styles (but never use !important (Box 8)
2	Inline	A declaration that is put on an element using style=
3	Media Type	When a style is applied through a media query (more in Chapter 9)
4	User defined	Most browsers have the accessibility feature: a user defined CSS
5	Selector specificity	Styling applied via a class or id overwrites generic styling
6	Rule order	The last style written has priority
7	Parent inheritance	If there is no style specified, then children inherit styles from their parent
8	CSS	CSS rules from a stylesheet or style block that are applied to generic elements.
9	Browser defaults	Lowest priority, these are the default styles that browsers ship with
Table 1: CSS priority rules.
```

``` css
a {
  color: gray;
}
h1 a {
  color: green;
}
```

-----
Table 2 has a more detailed listing of the values that different selectors are assigned by the browser. The styles get more specific as you go down the table, meaning that lower ones would override the styles above.

* Simple HTML selector	em {color: #fff;}	1

* HTML selector targeting element inside another element	h1 em {color: #00ff00;}	2
CSS class name	.alert {color: #ff0000;}	1,0
HTML element with a class name	p.safe {color: #0000ff;}	1,1
CSS id	#thing {color: #823706;}	1,0,0
CSS id with a class name	#thing .property {color: #823706;}	1,1,0
Inline style	style="color: transparent;"	1,0,0,0
Table 2: The confusingly complex rules of specificity.


>Think about !important like this: if you’ve had to use !important, then you’ve failed at styling something.

One way to avoid getting caught in situations where overlapping layers of complexity keep your styles from being applied is to try to keep your selectors as simple as possible (Listing 26), rather than using an ugly and complicated set of selectors (Listing 27).

``` css
/* Listing 26: Good clean CSS. */
.bio-box a {
  color: green;
}
.alert {
  background: red;
}
/* Listing 27: Ugly and complicated CSS. */
body div#exec-bio.bio-box a {
  color: orange;
}
```
Often simplicity is the best solution.

-----

>One good practice is to divide up the styling into two different categories: global styles that will apply in many different places in order to create greater consistency, and individual sections that are self-contained modules of functionality or content.

>it’s a good idea to keep the number of selectors in a declaration under three or less... CSS selectors are read by the browser from right to left

``` css
.bio-box p a {
  color: green;
}
```

### 2.4 How to be a good styling citizen

>Good practice is to divide up the styling into two different categories: global styles that will apply in many different places in order to create greater consistency, and individual sections that are self-contained modules of functionality or content.

-----


### Percentage sizing
  * based on the parent container of the element
     * not by the size of the browser, or the page as a whole.

Percentage heights
  * weird because they require a set height on the parent element
  *  can not assume a height like they assume a width.

### Percentage fonts

>If you use a percentage for a text size, the resulting size of the font is based not on the pixel dimensions of the container but rather on whatever font-size style that container has inherited. So the box itself could be 1000px tall, but if it inherited a font size of 16px, and you set the font size of a child element to 50%, you are going to get only an 8px-tall font (50% of 16px), not a 500px-tall font like you might think.

#### em
  one em is equal to the current font size of the element’s parent container. The default page font size is used if no font size is inherited.

#### rem - "root em"

always refers back to the font size of the html tag

-----
#### vh, vw
 >incredibly useful for responsive (mobile) layouts: the view- port height, vh, and viewport width, vw. These units allow us to size elements
 >Each vh or vw is 1 percent of the corresponding screen dimension, so 3vh would equal 3% of the height of the screen and 100vw would be 100% of the width.

 >If for some reason you care about exact pixel sizes, there is a hack that you can use to combine em with pixel-precision—set a font-size on the body of 62.5%, which makes 1em elsewhere on the page equal 10px (62.5% of 16). In web design circles, this is sometimes known as the "62.5% trick".

 >To sum up our recommendations: use relative units for text, don’t use the 62.5% trick, and simply pick random numbers that set the font sizes somewhat close to what your design calls for (seriously). What matters ultimately is how the end product looks and the relationship between different elements. Trying to achieve pixel-perfection is simply not a reasonable goal on the Web, and pixel sizing is really just an artifact from the bad old days of doing designs in Photoshop where elements heights and widths were set in pixels. Just embrace the imprecision

 ## 4 The box model

 >all the rules that determine how height, width, margin, padding, and borders are applied to elements (Figure 50). Ele- ments of the box model can be quite confusing, with weird interactions between elements, counterintuitive applications of styles, and ways of writing style val- ues that can look strange at first glance.

### Inline vs. block

inline elements:
  * can only have margins and padding applied to the left and right (not top or bottom)
  * won’t accept a width or height set by CSS
  * examples include span or a
  * Floated elements will become block

display:
none prevents the element from displaying on the page.
display: block forces an element to be a block element
display: inline turns a block element into an inline element
inline-block property, which is a hybrid between inline and block, is a useful display setting, as it allows styling that normally works only on block elements—such as width and height, top margins, and padding—to be applied to a particular element. At the same time, it also lets the element as a whole act like an inline element. This means that text will still flow around it, and it will only take up as much horizontal space as it needs to contain the content

especially helpful when making site navigation, or when styling a group of ele- ments so that they are side by side.

margin: auto.
If you have a block element, like a div, p, or a ul, that has a width set by a style, you can make the browser center that element horizontally within its parent container by setting the left and right margin to auto.

You can also make margins negative for elements. This draws the element up and out of the normal place it occupies on the page and overlays it on content that normally it wouldn’t be able to affect.

padding pushes the content inside an element away from the edges of the element.

you might think that vertical-align is something that can position elements in the middle of other elements, but in reality it has an effect only on objects that are inline, or inline block, and it centers them only in relation to the line of text that they appear on.

line height, which defines the space above and below text and other inline elements. Any text on your site that is multi-line should have the line-height increased to make reading easier. An ideal amount would be around 140% to 170%, depending on the font. It works like em in that 1 equals 100%, but there’s no associated unit as with em, px, etc.

-----

Note: Style HTML5 elements with classes
To ensure maximum backwards compatibility, it’s not a good idea to target the newer HTML5 semantic elements like header and nav directly. There are inevitably going to be some users who visit your site on an old browser that doesn’t support them—though luckily there are fewer such cases with each passing year.
When an old browser encounters new HTML tags, it sees them as regular divs, and any styles are ignored. To avoid this situation, it’s better to give such elements classes, and then target your styles at the classes.
For example, we want to avoid styling header directly: ```

``` css
header {
  background: #000;
}
```
Instead, we’ll give the header tag a class "header" (like in Listing 107), and then target that class (note the leading dot):

``` css
/* HTML */
<header class"header">

/* CSS */
.header {
  background: #000;
}
```

This way, our styles will work even in older browsers.

-----

The position style in CSS can be given five different values:

1. **static**
  * the default position of elements in the flow of content.
  * will ignore directional styles like left, right, top, and bottom.

***** Add position static image here  ****

2. **relative**
  * respects content flow
  * directional styles allowed (push the element away from the boundary with other elements.)
  * absolutely positioned items can be contained within, as though the relatively positioned element were a separate canvas. In other words, if an absolutely positioned element is inside a rel- atively positioned element, a style of top: 0 would cause the absolutely positioned element to be drawn at the top of the relative position element rather than at the top of the page.
 * z-index change allowed

3. absolute
– Positions the element at a specific place by taking it out of the document flow, either within a parent wrapper that has a position: value other than static, or (if there is no parent) then a specific place in the browser window. It is still a part of the page content, which means when you scroll the page, it moves with the content.
– Also lets you define a z-index property.
– Because the element is removed from the document flow, the width
or height is determined either by shrinking to the content inside, orby setting dimensions in CSS. It behaves kind of like an element set to inline-block.
– Causes any float that is set on the object to be ignored, so if you have both styles on an element you might as well delete the float.

Fixed:

– Positionstheelementataspecificplacewithinthebrowserwindow totally separate from the page content. When you scroll the page, it won’t move.
– Lets you set z-index.
– Has the same need to have dimensions set as position: absolute; otherwise, it will be the size of the con- tent inside.
– Also causes floats to be ignored.

inherit
– This is not very common so we aren’t going to discuss other than to say it makes the element inherit the position from its parent.

when an element is absolutely positioned, the directional styles don’t add or subtract distance—setting bottom: 50px doesn’t move it toward the bottom, but rather it sets the position 50px from the bottom. So right: 50px puts the element 50px from the right edge. what happens if I set both a top and bottom, or a left and right?” The answer is that, for whatever reasons, the top and left properties will take priority and the bottom and right will be ignored

-----
What is the solution to this exercise?

5.8.2 Exercises
1. Try moving the ul that contains the social links to the bottom left corner of the .full-hero using the positioning rules you’ve learned. What changes are you going to need to make to .full-hero to allow the social links to remain inside?

-----
fixed header
use position: fixed to take the header entirely out of the page content and stick it to the top of the user’s browser.

-----

background-size property to cover means that the image will be resized so that the entire .full-hero container is covered by the im- age, even if that means cutting off parts of the image
