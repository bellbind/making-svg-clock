# Making analog clock as a single SVG file with JavaScript

Step-by-step guide to make and use a analog clock app as a [SVG](https://www.w3.org/TR/SVG11/) with embeded JavaScript.

<object data="99-clock.svg"></object>

- repository: [@bellbind/making-svg-clock](https://github.com/bellbind/making-svg-clock)

-----

## 0. Basic shapes in center oriented SVG file

- [00-svg-shapes.svg](00-svg-shapes.svg)

1. Create a SVG file with center coord is (0, 0) as [`viewBox="-halfwidth -halfheight wwidth height"`](https://www.w3.org/TR/SVG11/single-page.html#coords-ViewBoxAttribute).
2. Draw [`<rect>`](https://www.w3.org/TR/SVG11/single-page.html#shapes-RectElement), [`<circle>`](https://www.w3.org/TR/SVG11/single-page.html#shapes-CircleElement), and centering [`<text>`](https://www.w3.org/TR/SVG11/single-page.html#text-TextElement) in the SVG .

<object data="00-svg-shapes.svg"></object>

-----

## 1. Transform basic

- [01-transform.svg](01-transform.svg)

1. Rotate `<rect>` with [`transform`](https://www.w3.org/TR/SVG11/single-page.html#coords-TransformAttribute) attribute with `rotate(angle,cx=0,cy=0)` value.
2. Rotate non tilt `<text>` as 1. `rotate(-a)`, 2. `translate(dx,dy)`, 3. `rotate(a)` (NOTE: right-side first in each SVG `transform` list).

<object data="01-transform.svg"></object>

-----

## 2. JavaScript enabled SVG

- [02-javascript.svg](02-javascript.svg)
- [02-embed.html](02-embed.html)

1. Use JavaScript [`CDATA` section](https://en.wikipedia.org/wiki/CDATA) with [`<script>`](https://www.w3.org/TR/SVG11/single-page.html#script-ScriptElement) tag in SVG.
2. Use [`requestAnimationFrame`](https://html.spec.whatwg.org/multipage/imagebitmap-and-animations.html#dom-animationframeprovider-requestanimationframe) to animation
3. Use [`<object data="url.svg"></object>`](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-object-element) for embedding JavaScript enabled SVG (not `<img>`).
4. Export JavaScript API for the SVG with members of [`globalThis`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/globalThis) == `contentWindow`.
5. Access inside SVG with `objectElement.contentWindow` from HTML.

<object data="02-javascript.svg"></object>

-----

## 3. Basic analog clock

- [03-basic-analog-clock.svg](03-basic-analog-clock.svg)

1. Put 3 hands of `<rect>`with `id` for pickup with [`document.getElementById(id)`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById).
2. Set `rotate()` transform of hands in JavaScript SVG API ([`svgElement.createSVGTransform()`](https://www.w3.org/TR/SVG11/single-page.html#struct-__svg__SVGSVGElement__createSVGTransform) ).
3. Use [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) object for get current Hours/Minutes/Seconds.
4. Compoute and set angle of each hands.

<object data="03-basic-analog-clock.svg"></object>

-----

## 4. Decorated frame of the clock

- [04-deco-frame-clock.svg](04-deco-frame-clock.svg)

1. Put several types of notches for each minutes.

<object data="04-deco-frame-clock.svg"></object>

-----

## 5. Round of 12-hours digits

- [05-12digits-clock.svg](05-12digits-clock.svg)

1. Add 12 digits for hours.

<object data="05-12digits-clock.svg"></object>

-----

## 6. Shadow of hands

- [06-shadow-hands-clock.svg](06-shadow-hands-clock.svg)

1. Add drop shadow of each hand with cross platform ways (use [`<feDropShadow>`](https://drafts.fxtf.org/filter-effects/#feDropShadowElement) instead of [`filter: drop-shadow()`](https://drafts.fxtf.org/filter-effects/#funcdef-filter-drop-shadow) function).

<object data="06-shadow-hands-clock.svg"></object>

-----

## 7. Round alignment logo 

- [07-logo-clock.svg](07-logo-clock.svg)

1. Add a logo `<text>` with [`<textPath>`](https://www.w3.org/TR/SVG11/single-page.html#text-TextPathElement) on invisible arc [`<path>`](https://www.w3.org/TR/SVG11/single-page.html#paths-PathElement).

<object data="07-logo-clock.svg"></object>

-----

## 8. Digital panel

- [08-digital-panel-clock.svg](08-digital-panel-clock.svg)

1. Add a digital area `<rect>` and placeholder `<text>`s.
2. Update digital texts in JavaScript.

<object data="08-digital-panel-clock.svg"></object>

-----

## 9. Decorated texts with Web font

- [09-webfont-clock.svg](09-webfont-clock.svg)

1. Choose [Web font css](https://drafts.csswg.org/css-fonts/#font-face-rule) by [Google Fonts](https://fonts.google.com/).
2. Load web fonts with `@import` style in `<style>` in SVG .
3. Apply webfonts at each `font-family`.

<object data="09-webfont-clock.svg"></object>

-----

## 10. Inset shadow of digital panel

- [10-inset-shadow-clock.svg](10-inset-shadow-clock.svg)

1. Make tricky [`<filter>`](https://www.w3.org/TR/SVG11/single-page.html#filters-FilterElement) for [inset shadow with several steps](http://jsfiddle.net/kkPM4/).
2. Insert a frame `<rect>` for generating inset shadow.

<object data="10-inset-shadow-clock.svg"></object>

-----

## 11. Tick sound

- [11-tick-sound-clock.svg](11-tick-sound-clock.svg)

1. Play sounds with [Web Audio API](https://www.w3.org/TR/webaudio/).
2. Should make a [`AudioContext`](https://www.w3.org/TR/webaudio/#AudioContext) object after some user inputs; e.g. `"click"` event.
3. Create tick sound with [`GainNode`](https://www.w3.org/TR/webaudio/#gainnode) and [BiquadFilterNode](https://www.w3.org/TR/webaudio/#biquadfilternode) tricks.
4. Play tick sounds within `requestAnimationFrame` loop after seconds changed.

<object data="11-tick-sound-clock.svg"></object>

-----

## 12. Controllable Clock from HTML

- [12-controllable-clock.svg](12-controllable-clock.svg)
- [12-control-clock.html](12-control-clock.html)

1. Export several features via adding object with methods into `globalThis`.
2. Make some example UI with HTML.

<object data="12-control-clock.html" width="340" height="400"></object>

-----

## 99. SVG Analog Clock as SPA app

- [99-clock.svg](99-clock.svg)
- [99-spa-clock.html](99-spa-clock.html)
- [99-manifest.json](99-manifest.json)

1. Create fullscreen style HTML with `<object>` tag.
2. Create [web app manifest](https://www.w3.org/TR/appmanifest/) `manifest.json` for the HTML.
3. Add [`<link rel="manifest" href="...">`](https://www.w3.org/TR/appmanifest/#using-a-link-element-to-link-to-a-manifest) in the HTML.

<object data="99-spa-clock.html" width="480" height="640"></object>

-----

## References

- SVG1.1: https://www.w3.org/TR/SVG11/
- Filter Effects Module Level 1: https://drafts.fxtf.org/filter-effects/
- CSS Fonts Module Level 4: https://drafts.csswg.org/css-fonts/
- WHATWG HTML: https://html.spec.whatwg.org/
- Web Audio API: https://www.w3.org/TR/webaudio/
- Web Application Manifest: https://www.w3.org/TR/appmanifest/

