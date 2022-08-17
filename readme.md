# Making analog clock as a single SVG file with JavaScript

## 0. Basic shapes in center oriented SVG file

- [00-svg-shapes.svg](00-svg-shapes.svg)

1. Create a SVG file with center coord is (0, 0).
2. Draw `<rect>`, `<circle>`, and centering `<text>` in the SVG .

## 1. Transform basic

- [01-transform.svg](01-transform.svg)

1. Rotate `<rect>` with `transform` attribute with `rotate(angle,cx=0,cy=0)` value.
2. Rotate non tilt `<text>` with 1. `rotate(-a)`, 2. `translate(dx,dy)`, 3. `angle(a)` (NOTE: right-side first in SVG `transform`).

## 2. JavaScript enabled SVG

- [02-javascript.svg](02-javascript.svg)
- [02-embed.html](02-embed.html)

1. Use JavaScript `CDATA` section with `<script>`  tag in SVG.
2. Use `requestAnimationFrame` to animation
3. Use `<object data="url.svg"></object>` for embedding JavaScript enabled SVG (not `<img>`).
4. Export JavaScript API for the SVG with members of `globalThis` == `contentWindow`.
5. Access inside SVG with `objectElement.contentWindow` from HTML.

## 3. Basic analog clock

- [03-basic-analog-clock.svg](03-basic-analog-clock.svg)

1. Put 3 hands of `<rect>`with `id`
2. Set `rotate()` transform of hands in JavaScript SVG API
3. Use `Date` object for get current Hours/Minutes/Seconds.
4. Compoute and set angle of each hands.

## 4. Decorated frame of the clock

- [04-deco-frame-clock.svg](04-deco-frame-clock.svg)

1. Put several types of notches for each minutes.

## 5. Round of 12-hours digits

- [05-12digits-clock.svg](05-12digits-clock.svg)

1. Add 12 digits for hours.

## 6. Shadow of hands

- [06-shadow-hands-clock.svg](06-shadow-hands-clock.svg)

1. Add drop shadow of each hand with cross platform ways (use `<feDropShadow>`).

## 7. Round alignment logo 

- [07-logo-clock.svg](07-logo-clock.svg)

1. Add a logo `<text>` with `<textPath>` on arc.

## 8. Digital panel

- [08-digital-panel-clock.svg](08-digital-panel-clock.svg)

1. Add a digital area `<rect>` and placeholder `<text>`s.
2. Update digital texts in JavaScript.

## 9. Decorated texts with Web font

- [09-webfont-clock.svg](09-webfont-clock.svg)

1. Choose Web font css by [Google Fonts](https://fonts.google.com/).
2. Load web fonts with `@import` style in `<style>` in SVG .
3. Apply webfonts at each `font-family`.

## 10. Inset shadow of digital panel

- [10-inset-shadow-clock.svg](10-inset-shadow-clock.svg)

1. Make tricky `<filter>` for inset shadow with several steps.
2. Insert a frame `<rect>` for generating inset shadow.

## 11. Tick sound

- [11-tick-sound-clock.svg](11-tick-sound-clock.svg)

1. Play sounds with [Web Audio API](https://www.w3.org/TR/webaudio/).
2. Make `AudioContext` object after some user inputs (in "click" event).
3. Create tick sound with [`GainNode`](https://www.w3.org/TR/webaudio/#gainnode) and [BiquadFilterNode](https://www.w3.org/TR/webaudio/#biquadfilternode) tricks.
4. Play tick sounds within `requestAnimationFrame` loop.

# 12. Controllable Clock from HTML

- [12-controllable-clock.svg](12-controllable-clock.svg)
- [12-control-clock.html](12-control-clock.html)

1. Export several features via adding object into `globalThis`.
2. Make some example UI with HTML.

## 99. SVG Analog Clock as SPA app

- [99-clock.svg](99-clock.svg)
- [99-spa-clock.html](99-spa-clock.html)
- [99-manifest.json](99-manifest.json)

1. Create fullscreen style HTML with `<object>` tag.
2. Create webmanifest `manifest.json` for the HTML.
3. Add `<link rel="manifest" href="...">` in the HTML.