<div align="center">
  <img
    src="Order summary - desktop.png"
    alt="Order summary card for an annual audio plan subscription."
    height="300px">
</div>

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

This is a solution to the [Order summary card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/order-summary-component-QlPmajDUj).

### The challenge

Users should be able to:

- See hover states for interactive elements

<div align="center">
  <img
    src="ordersum-desktop-design.jpg"
    alt="Order summary card for an annual audio plan subscription."
    height="300px">
  <img
    src="Order summary - hover.jpg"
    alt="Order summary card for an annual audio plan subscription showing hover states when a user interacts with the purchase button and links."
    height="300px">
  <p><em>Desktop static and hover state designs</em></p>
</div>

### Links

- Solution URL: [Order summary card](https://rileydevdzn.github.io/order-summary-card/)

## My process

### Built with

- Semantic HTML5 markup
- Fluid typography with viewport units and the CSS `clamp()` function
- CSS variables
- Flexbox
- Responsive design
- Realistic workflow, building from professional Figma design files (design-to-code) 

### What I learned

To make the font sizes responsive, I used the CSS `clamp()` function and viewport units.

The min and max values were straightforward. For that pesky middle variable (preferred value), I used a delta (amount of change) and a base (starting) value formula instead of a single numerical value. 

There are cases where a single numerical value would be preferred, I wanted to explore the formula approach for this project.

First, I was interested in figuring out the delta, how many pixels should the font size change by for every pixel of change in viewport width? I calculated this using the min and max font sizes and selected min and max viewport widths. For the `<h1>` heading in this design, for example, the minimum font size in the design was 22px at a viewport width of 375px, and the maximum font size was 28px at a viewport width of 1440px. 

So the delta calculation looked like:
```
delta = (fontMax - fontMin) / (viewportMax - viewportMin)

delta = (28px - 22px) / (1440px - 375px)

delta = 0.00563
```

I kept the delta value at 5 decimal places (0.00563 for the `<h1>` example) for my calculations, or three decimals (0.563) in viewport units (0.00563 * 100).

Next, I needed to figure out the base or starting value to apply this change to. Now that I had the delta, I could compare the resulting font size with this change applied at the maximum viewport width to the maximum desired font size; the difference would be my starting value.

My starting value calculation looked like this:
```
starting value = fontMax - (viewportMax * delta) 

starting value = 28px - (1440px * 0.00563)

starting value = 19.89px
```

So the preferred value formula (middle variable in my clamp function) for my `<h1>` element would look like:
```
19.89px + 0.563vw
```

After some testing and playing around with the values at various viewport widths to achieve a consistent visual, I refined my formula a bit:
```
20px + 0.555vw
```

So my `clamp()` function looked like this for the `<h1>` element:
```
font-size: clamp(22px, 20px + 0.555vw, 28px);
```

### Continued development

I applied CSS `clamp()` to individual elements in this project. In a future project I'd like to experiment with "t-shirt sizing" fonts, declaring global variables on the root using `clamp()` to set a font scale.

### Useful resources

- [CSS Tricks: Simplified fluid typography](https://css-tricks.com/simplified-fluid-typography/) - Introduction to fluid typography using CSS calc function. When I was researching typography methods, this inspired me to look into viewport units and fluid typography in the first place.
- [CSS Tricks: Fluid typography](https://css-tricks.com/snippets/css/fluid-typography/) - Slightly older article than the first one, but there's more links for further reading at the bottom to explore.
- [Utopia: Fluid responsive design](https://utopia.fyi/) - Diving further into the possibilities of fluid design with typography, spacing, and fluid grids. Tools include visualizations of how the code implements which I found helpful.
   
## Author

- Frontend Mentor - [@rileydevdzn](https://www.frontendmentor.io/profile/rileydevdzn)