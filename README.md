# CSS Workshop #2

## Operational instructions
* Fork this repo and create a clone in Cloud9
* Each exercise goes to a different branch, branched from master
* When you complete an exercise create a pull request for it
* Check back often for comments on your pull requests
* When you respond to a pull request comment by making a new commit, @mention the person in a new comment inside the PR

## Technical instructions
* The repo already contains a `css/` directory with a `normalize.css` as well as a `main.css`. You should be spending
most of your time in `main.css`.
* There is an `index.html` file at the root of the repo which links to `normalize.css` and `main.css`. This is where
you would put your HTML code for the exercise. Should you need to add any new CSS files, make sure you respect the
ordering and have your CSS files be the last to be loaded.

## Exercise 1: Navigation menu
* Create an HTML page with a navigation menu of 5 items. You can make the links point to anything, like google.com
  * Home
  * Products
  * Services
  * About us
  * Contact us
* Below the navigation menu, add a dozen of "lorem ipsum" paragraphs. In Cloud9 if you write `lorem` followed by
a **`TAB`**, it will expand into a paragraph of lorem. **PROTIP**: if you type `p(lorem)*12` and then press `TAB`, it
will expand into 12 paragraphs of lorem :)
* Give the navigation menu a 50% opaque black background
* Give the menu elements a white border, white text and a nice padding of `0.5em`
* Notice that even though the padding is the same all around, the list elements seem to have more vertical spacing
* This is because the `line-height` property, which sets the "height of a standard line of text", is larger than
the font size. Set the `line-height` property of the menu elements to `1`, and notice the difference.
* Fix the browser default `padding` and `margin` on your `ul` element by resetting it to `0`
* Make the navigation menu **`fixed`** on top of the page, taking the full width of the page (100%)
* Give the navigation menu a padding of `0.5em`.
* Notice that the navigation menu now goes overboard on the right of the page! What is happening?
* Setting the `width` to `100%` and then adding a `padding` will make the width of the nav go over 100%. This is
because the browser's default box sizing model (`content-box`) adds paddings and borders on top of your defined width/height.
* There is a better box sizing model, `border-box`, that takes your defined `width` as being `width_of_content + width_of_padding + width_of_border`.
* Read more about [box sizing on Paul Irish's blog](http://www.paulirish.com/2012/box-sizing-border-box-ftw/) and copy/paste his fix at the **top** of your `main.css`
* Refesh your page to see that the width is now back to 100% total.
* **IMPORTANT**: You should add this snippet of code to the top of your `main.css` for *all future exercises!* You can either
do it every time, or commit it once to master and branch off of there. Your choice.
* Commit/push and make a pull request
* Your end-result should look somewhat like this:

![exercise 1](https://i.imgur.com/NutCbP6.png)

## Exercise 2: CSS Positioning and Box Model
To complete this exercise, you will need to read about [CSS positioning](http://learnlayout.com/position.html).

* Add the following HTML to the `body` of an empty HTML page:
```html
<aside class="dialog-box">
    <h1 class="dialog-box__title">Hello World</h1>
    <div class="dialog-box__content">
        <p>
            Lorem ipsum dolor sit amet, consectetuer adipiscing elit,
            sed diam nonummy nibh euismod tincidunt ut laoreet dolore
            magna aliquam erat volutpat. Ut wisi enim ad minim veniam,
            quis nostrud exerci tation ullamcorper suscipit lobortis nisl
            ut aliquip ex ea commodo consequat. Duis autem vel eum iriure
            dolor in hendrerit in vulputate velit esse molestie consequat,
            vel illum dolore eu feugiat nulla facilisis at vero eros et
            accumsan et iusto odio dignissim qui blandit praesent luptatum
            zzril delenit augue duis dolore te feugait nulla facilisi.
            Nam liber tempor cum soluta nobis eleifend option congue
            nihil imperdiet doming id quod mazim placerat facer possim
            assum. Typi non habent claritatem insitam; est usus legentis
            in iis qui facit eorum claritatem. Investigationes
            demonstraverunt lectores legere me lius quod ii legunt saepius.
            Claritas est etiam processus dynamicus, qui sequitur mutationem
            consuetudium lectorum. Mirum est notare quam littera gothica,
            quam nunc putamus parum claram, anteposuerit litterarum formas
            humanitatis per seacula quarta decima et quinta decima. Eodem
            modo typi, qui nunc nobis videntur parum clari, fiant sollemnes
            in futurum.
        </p>
    </div>
    <button class="dialog-box__close"></button>
</aside>
```

Using CSS, make the dialog box look like this:

![exercise-2](https://i.imgur.com/xSQLLaB.png)

---

* Here are a few indications to get you started:
  * The style of writing in this HTML is inspired from BEM. [Read about BEM](https://css-tricks.com/bem-101/) on your own
  time for educational purposes. Basically, each stylable element is assigned a class name based on the "component" it is in.
  * Use the following CSS skeleton to get started:
```css
.dialog-box {
    background-color: #d2d2d2;
}
.dialog-box__title {
    
}
.dialog-box__content {
    background-color: #f2f2f2;
}
.dialog-box__close {
    border: 2px solid white;
    background-color: tomato;
    width: 24px;
    height: 24px;
}
```
  * You shouldn't need to add any more selectors, only fill in the provided ones.
  * Make sure the content is spaced away from the borders of its containers.
  * You will need to remove the default margin on the `h1` element

---

## Exercise 3: CSS Layouts and Media Queries
In this exercise we will be creating a responsive image thumbnail gallery.

The result should look like this on desktop:

![exercise-3-desktop](https://i.imgur.com/YAydktA.png)

---

The result should look like this on a tablet:

![exercise-3-tablet](https://i.imgur.com/hCUKDBJ.png)

---

The result should look like this on a mobile:

![exercise-3-mobile](https://i.imgur.com/7gtkfso.png)

* **NOTE**: You will need to add the following line to the `head` of your HTML document:
```html
<meta name="viewport" content="width=device-width">
```

---

## Exercise 4: Responsive, mobile-first layout
One common technique when building web pages or small applications is to go "mobile-first". In terms of styling and UX, this means we would first design the page as it's meant to look on a mobile device, and then work our way up to add artifices for the larger devices (tablets, desktops, maybe TVs!)

In terms of using media queries to achieve this, it means that our regular CSS would be the base CSS across all our devices, and then we would mostly write `min-width` media queries to target larger and larger screen sizes.

One thing we have to do before getting started is choosing our **breakpoints** carefully. Since we're mobile-first, we will start with the mobile phone and work our way up. We will consider a device to be a "mobile phone" or "small screen" if it has a width of less than, say, `400px`. We will consider a device to be a "tablet" or "medium screen" if it has a width of less than -- again this is only an example -- `800px`. Then anything above `800px` would be considered a "desktop computer", or "large screen".

Setting these breakpoints from the beginning means we don't have to do any guess work when writing our styles.

Reproduce the following page with a mobile, tablet and desktop layout.

On desktop:

![desktop](https://i.imgur.com/73r4tul.png)

---

On tablet:

![tablet](http://i.imgur.com/h4ChQlj.png)

---

On mobile:

![mobile-1](https://i.imgur.com/oQv6on0.png)

![mobile-2](https://i.imgur.com/PixTV2W.png)

---

## Exercise 5: that addressbook, again!
Using this markup:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta name="viewport" content="width=device-width">
        <style type="text/css">
            * {
                box-sizing: border-box;
            }
            body {
                font-family: "helvetica neue", helvetica, arial, sans-serif;
            }
            h1,h2,h3,h4,h5,h6 {
                font-weight: 500;
            }
            
            /* write your style rules below this line */
        </style>
    </head>
    <body>
        <h1>Sparta's Address Book</h1>
        
        <section class="entry">
            <header class="entry-header">
                <img class="entry-header__photo" src="http://i.imgur.com/fcdeUO2.jpg">
                <h2 class="entry-header__name">Anton Sokolov</h2>
            </header>
            
            <section class="entry-subsection">
                <h3 class="entry-subsection__heading">
                    Addresses
                </h3>
                <section class="entry-entity">
                    <h4 class="entry-entity__heading">
                        Home:
                    </h4>
                    <p class="entry-entity__content">
                        Fuente del Gallo, 35<br>
                        15151 Dumbría<br>
                        Spain
                    </p>
                </section>
                <section class="entry-entity">
                    <h4 class="entry-entity__heading">
                        Work:
                    </h4>
                    <p class="entry-entity__content">
                        C/ Pablo Iglesias, 94<br>
                        26325 Viniegra de Abajo<br>
                        Spain
                    </p>
                </section>
            </section>
            
            <section class="entry-subsection">
                <h3 class="entry-subsection__heading">
                    Emails
                </h3>
                <section class="entry-entity">
                    <h4 class="entry-entity__heading">
                        Home:
                    </h4>
                    <p class="entry-entity__content">
                        VladlenAnisimov@rhyta.com 
                    </p>
                </section>
                <section class="entry-entity">
                    <h4 class="entry-entity__heading">
                        Other:
                    </h4>
                    <p class="entry-entity__content">
                        VAnisimov@teleworm.us
                    </p>
                </section>
            </section>
            
            <section class="entry-subsection">
                <h3 class="entry-subsection__heading">
                    Phones
                </h3>
                <section class="entry-entity">
                    <h4 class="entry-entity__heading">
                        Home:
                    </h4>
                    <p class="entry-entity__content">
                        +34 656 351 487
                    </p>
                </section>
                <section class="entry-entity">
                    <h4 class="entry-entity__heading">
                        Work:
                    </h4>
                    <p class="entry-entity__content">
                        +34 799 809 163
                    </p>
                </section>
            </section>
        </section>
        
    </body>
</html>
```

reproduce the following layout **without modifying the markup at all**.

Mobile:

![mobile](https://i.imgur.com/kAJz5LJ.png)

---

Tablet:

![tablet](https://i.imgur.com/hR1Rfpl.png)

---

Desktop:

![desktop](https://i.imgur.com/iutw1AA.png)

---

## CHALLENGE: responsive grid!
For this challenging exercise, we will be reproducing a **basic version** of [Foundation's responsive grid](http://foundation.zurb.com/grid.html).

Zurb's Foundation is a CSS framework. Basically, it defines CSS rules for a ton of classes, and lets you use these classes in your HTML to achieve some effects like nice looking buttons, dropdown menus, etc.

One of its popular features is the responsive grid. The grid basically separates the vertical space of your page in 12 equal-width columns, and you can create sections that span any number of these columns.

Why 12? Because 12 is divisible by 1, 2, 3, 4, 6 and 12! This means you can easily create a half/half layout (6 columns + 6 columns), or a third/third/third layout (4 cols, 4 cols, 4 cols) but also a quarter/quarter/quarter/quarter layout (3 cols, 3 cols, 3cols, 3cols) and so on. If we had divided our space in 10 columns, we could pretty much only do half/half because 10 is only divisible by 1, 2, 5 and 10.

For this exercise, we will be re-creating a very basic version of Foundation's grid. Basically we will be adding the following classes to our CSS:

```
small-1: If an element has this class, it will take one column on small and up screen sizes (1/12 of the width)
...
small-6: if an element has this class, it will take 6 columns on small and up screen sizes (basically will take half the width)
small-12: if an element has this class, it will take 100% of the width

medium-1 ... medium-12: same as small, but only if the screen is medium up (meaning tablet or desktop)

large-1 ... large-12: same as small, but only if the screen is large

row: this class should wrap a set of responsive columns
```

Here are some examples to make it clearer:

The following will create two sections that each take half of the screen, on mobile, tablet and desktop:
```html
<div class="row">
  <div class="small-6">hello</div>
  <div class="small-6">world</div>
</div>
```

The following will create two sections that each take half of the screen, **but only on tablets and desktops**:
```html
<div class="row">
  <div class="medium-6">hello</div>
  <div class="medium-6">world</div>
</div>
```

The following will create six sections. On mobile they will be 2 per row, on tablet and desktop they will be 3 per row:
```html
<div class="row">
  <div class="small-6 medium-4">one</div>
  <div class="small-6 medium-4">two</div>
  <div class="small-6 medium-4">three</div>
  <div class="small-6 medium-4">four</div>
  <div class="small-6 medium-4">five</div>
  <div class="small-6 medium-4">six</div>
</div>
```

You can use the examples above to test the CSS you'll be writing :)
