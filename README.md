# Work In Progress

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/title.svg">
    <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/title-light.svg" style="max-width: 95%; width: 740px">
</picture>


Very cool and very useful. Add _Spice_.

Covers animation and theme responsiveness.

Assumes basic HTML and CSS knowledge.



<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-animating.svg">
    <img class="image" src="https://raw.githubusercontent.com/Nathan-Dane/ReadmeAnimatedSVGs/refs/heads/main/Resources/heading-animating-light.svg" style="height: 40px">
</picture>

Two types: `Raw SVG` and `HTML Embed`

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

They are implemented differently (Raw SVG has simplifications)



### Raw SVG

Uses regular SVG format:
```html
<?xml version="1.0" encoding="UTF-8"?>
<svg id="a" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 x y">
  <!-- SVG elements -->
</svg>
```

Can simply add style element:
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

From here, same as usual. Define `@keyframes` and set `animation` on elements.

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
        <img class="image" src="Examples/Rocket.svg" width="100px">
      </td>
      <td align="center">
        <img class="image" src="Examples/RocketAnimated.svg" width="100px">
      </td>
    </tr>
  </tbody>
</table>

Again, raw code for all examples can be seen in the `Examples` folder in this repository.

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

JavaScript is not run

Webkit does not pass `vw`, `vh`, `@media` queries

Webkit freaks out when viewbox ≠ width and height

Difference in browser display. Defaults vary in many ways, the main ones I had issues with:
- Animations (Safari bruh)
- Line height (Firefox bruh)
- Masking
- Fonts (Chrmium ,Firefox, Safari all have different defaults, and they vary in width)
- `ch` units (Safari bruh)