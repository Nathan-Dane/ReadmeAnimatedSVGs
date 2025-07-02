# Work In Progress

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/title.svg">
    <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/title-light.svg" style="max-width: 95%; width: 740px">
</picture>

&nbsp;&nbsp;&nbsp;&nbsp; **Add _flair_ to your Readmes with some CSS.**

This is a tutorial and exploration for adding elements to GitHub Readmes (and some other _md documents_) that allow for much more variety and ✨fanciness✨.

The standard **Markdown** feature set allows for very little variety, being little more than some left-aligned text, images, and tables.

GitHub flavour markdown adds a handful of **HTML** abilities, like `Align` and `div` layouting. One other addition is `SVG` elements, which as it turns out, opens a door to many opportunities!

> Basic **HTML** and **CSS** knowledge is assumed for this tutorial. Get an introduction [here](https://www.w3schools.com/html/html_css.asp)

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-animating.svg">
    <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-animating-light.svg" style="height: 40px">
</picture>

The secret is *that SVGs can contain CSS!*

While we can't use CSS in its full power as discussed later in **Limitations**, we can still use `animations` and even more fancy stuff like `filters`:

<div align="center">
  <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/Fade.svg">
      <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/Fade-light.svg" style="height: 35px">
  </picture>
</div>

</br>

For this case, we can define two types of SVG:
* `Raw SVG`: A simple SVG, just with added CSS.
* `HTML Embed`: Essentially an injected HTML document (which may still include `<svg>` and `<path>` elements)

<table align="center">
  <thead>
    <tr>
      <th style="text-align: center;">Raw SVG</th>
      <th style="text-align: center;">HTML Embed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <picture>
            <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/WelcomeSVG.svg">
            <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/WelcomeSVG-light.svg" width="130px" height="130px">
        </picture>
      </td>
      <td align="center">
        <picture>
            <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/WelcomeRectangle.svg">
            <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/WelcomeRectangle-light.svg">
        </picture>
      </td>
    </tr>
  </tbody>
</table>

> Code for all examples can be found in the `Examples` folder of this repository.

As a `Raw SVG` has native CSS support, this is much simpler to implement.



### Raw SVG

The standard simple SVG format looks like this:

```html
<?xml version="1.0" encoding="UTF-8"?>
<svg id="a" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 x y">
  <!-- SVG elements -->
</svg>
```

It has `viewBox` dimensions, and a list of childeren, which may contain `<path>`, `<rect>`, `<polygon>`,`<circle>`, and `<g>`.

Styling this with CSS is very straightforward, as you can simply add a `<style>` element before the children:

```html
<?xml version="1.0" encoding="UTF-8"?>
<svg id="a" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 x y">
  <style>
    .myClass {
      /* Your CSS */
    }
  </style>
  <!-- Example element: -->
  <path class="myClass" d="...">
</svg>
```

> If you are unfamiliar with SVGs, notice that I can add _classes_, _IDs_, and _styles_ to the child elements in the same way as usual HTML ones.

From here, it's the same as usual. You can define `@keyframes`, set `animation` on elements, and other CSS properties.

You can then add the SVG to the readme file as like any other image using HTML:\
`<img class="image" src="path/my-image.svg" width="...px">`

or using regular markdown:\
`![My image](/path/my-image.svg)`

Below is an example. The static SVG is the unedited output from Illustrator, and the animated one is an example of how to implement simple keyframe animations with CSS.

<table align="center">
  <thead>
    <tr>
      <th style="text-align: center;">Static</th>
      <th style="text-align: center;">Animated</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <a href="https://github.com/Nathan-Dane/ReadmeAnimatedSVGs/blob/main/Examples/Rocket.svg" target="_blank">
          <img class="image" src="Examples/Rocket.svg" width="100px">
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/Nathan-Dane/ReadmeAnimatedSVGs/blob/main/Examples/RocketAnimated.svg" target="_blank">
          <img class="image" src="Examples/RocketAnimated.svg" width="100px">
        </a>
      </td>
    </tr>
  </tbody>
</table>

Again, raw code for all examples can be seen in the `Examples` folder in this repository. _(Click to see source)_

---

### HTML Embed

How to do it...

Pretty much allows full HTML documents, including SVG elements

Can be injected using a `<foreignObject>` element.

Below is a template you can always use to make stuff:

```html
<?xml version='1.0' encoding='UTF-8'?>
<svg fill="none" viewBox="0 0 x y" width="x" height="y" xmlns="http://www.w3.org/2000/svg">
    <foreignObject width="100%" height="100%">
        <div xmlns="http://www.w3.org/1999/xhtml">
            <style>
              /* Your CSS Here */
            </style>
            <!-- HTML Elements Here -->
        </div>
    </foreignObject>
</svg>
```

both x's and y's must be equal (I'll explain why later)

Here is an example from my profile:
</br>
</br>
<div align="center">
  <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/WingBox.svg">
      <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/WingBox-light.svg" style="max-width:80%; width: 500px;" align="center">
  </picture>
</div>

</br>
</br>


<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-responsive.svg">
    <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-responsive-light.svg" style="height: 40px">
</picture>

They react to system and site light/dark themes

<table align="center">
  <thead>
    <tr>
      <th style="text-align: center;">Light</th>
      <th style="text-align: center;">Dark</th>
      <th style="text-align: center;">Responsive</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <img class="image" src="Examples/ResponsiveLight.svg">
      </td>
      <td align="center">
        <img class="image" src="Examples/ResponsiveDark.svg">
      </td>
      <td align="center">
        <picture>
            <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/ResponsiveDark.svg">
            <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/ResponsiveLight.svg">
        </picture>
      </td>
    </tr>
  </tbody>
</table>

Very good for curating the experience so it is always good.


Many possible methods (But `@media` is bad because webkit)

This is the good one:
```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="Link to dark-mode version">
  <img class="image" src="Link to light-mode version" width="--px" height="--px">
</picture>
```

Requires two individual files (one light, one dark).

Should be `raw.githubusercontent.com` links because reasons. There used to be issues with updating the images when they were relative links, so it is safer to use raw GitHub links.

Using links means the repo must be public, unless you use links containing a token.

Refer to the table below to ever see if there are issues:

<table align="center">
  <thead>
    <tr>
      <th style="text-align: center;">GitHub Links</th>
      <th style="text-align: center;">Relative Paths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <picture>
            <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/ResponsiveDark.svg">
            <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Examples/ResponsiveLight.svg">
        </picture>
      </td>
      <td align="center">
        <picture>
            <source media="(prefers-color-scheme: dark)" srcset="Examples/ResponsiveDark.svg">
            <img class="image" src="Examples/ResponsiveLight.svg">
        </picture>
      </td>
    </tr>
  </tbody>
</table>

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-limitations.svg">
    <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-limitations-light.svg" style="height: 40px">
</picture>

Certain things are not possible, largely due to Webkit (Safari).

Events are not passed (Pointer, hover, click, etc.)

External requests are blocked (Style sheets, fonts, packages, online images etc.)

JavaScript is not run

Webkit does not pass `vw`, `vh`, `@media` queries

Webkit freaks out when viewbox ≠ width and height

Difference in browser display. Defaults vary in many ways, the main ones I had issues with:
- Animations (Safari bruh)
- Line height (Firefox bruh)
- Masking
- Fonts (Chrmium ,Firefox, Safari all have different defaults, and they vary in width)
- `ch` units (Safari bruh)