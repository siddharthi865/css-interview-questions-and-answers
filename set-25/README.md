# Set 25

| #   | Question                                                                                                                                      |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How are percentages resolved in absolutely positioned elements?](#question-1-how-are-percentages-resolved-in-absolutely-positioned-elements) |
| 2   | [How are percentage paddings calculated?](#question-2-how-are-percentage-paddings-calculated)                                                 |
| 3   | [How does min-content sizing affect flex items?](#question-3-how-does-min-content-sizing-affect-flex-items)                                   |
| 4   | [How does aspect ratio interact with width and height?](#question-4-how-does-aspect-ratio-interact-with-width-and-height)                     |
| 5   | [How does overflow interact with border-radius?](#question-5-how-does-overflow-interact-with-border-radius)                                   |
| 6   | [How does transform affect stacking context?](#question-6-how-does-transform-affect-stacking-context)                                         |
| 7   | [How does position sticky interact with overflow?](#question-7-how-does-position-sticky-interact-with-overflow)                               |
| 8   | [How does z-index behave inside flex and grid items?](#question-8-how-does-z-index-behave-inside-flex-and-grid-items)                         |
| 9   | [How does CSS handle fractional pixels?](#question-9-how-does-css-handle-fractional-pixels)                                                   |
| 10  | [How does device pixel ratio affect layout?](#question-10-how-does-device-pixel-ratio-affect-layout)                                          |
| 11  | [How does CSS adapt to high DPI screens?](#question-11-how-does-css-adapt-to-high-dpi-screens)                                                |
| 12  | [How do media queries evaluate in nested browsing contexts?](#question-12-how-do-media-queries-evaluate-in-nested-browsing-contexts)          |
| 13  | [How does CSS behave in iframes?](#question-13-how-does-css-behave-in-iframes)                                                                |
| 14  | [How does shadow DOM encapsulation affect CSS cascade?](#question-14-how-does-shadow-dom-encapsulation-affect-css-cascade)                    |
| 15  | [How does CSS inheritance behave inside shadow roots?](#question-15-how-does-css-inheritance-behave-inside-shadow-roots)                      |
| 16  | [How do custom properties cross shadow boundaries?](#question-16-how-do-custom-properties-cross-shadow-boundaries)                            |
| 17  | [How do container queries evaluate nested containers?](#question-17-how-do-container-queries-evaluate-nested-containers)                      |
| 18  | [How does scroll snapping behave with dynamic content?](#question-18-how-does-scroll-snapping-behave-with-dynamic-content)                    |
| 19  | [How does CSS interact with Web Components?](#question-19-how-does-css-interact-with-web-components)                                          |
| 20  | [How do you stay updated with evolving CSS specifications?](#question-20-how-do-you-stay-updated-with-evolving-css-specifications)            |

## Question 1. How are percentages resolved in absolutely positioned elements?

# Short answer

For **absolutely positioned elements**, percentage values are usually resolved against the **containing block** (typically the nearest positioned ancestor).

Common rules:

- `width: 50%` → 50% of the containing block's width.
- `left: 10%`, `right: 10%` → percentage of the containing block's width.
- `top: 10%`, `bottom: 10%` → percentage of the containing block's height.
- `padding` and `margin` percentages are traditionally resolved against the containing block's width.
- If the containing block's size is indefinite in a given axis, percentage resolution can become more complex and may behave as `auto` in certain layout calculations.

---

# Explanation

Absolute positioning removes an element from normal document flow and positions it relative to its **containing block**.

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
}
```

Here, `.parent` becomes the containing block for `.child`.

## Width and height percentages

```css
.child {
  width: 50%;
  height: 50%;
}
```

Resolution:

- Width percentage → containing block width.
- Height percentage → containing block height.

Example:

```css
.parent {
  width: 800px;
  height: 400px;
}
```

Results:

```text
width: 50%  → 400px
height: 50% → 200px
```

---

## Offset percentages

For absolutely positioned elements:

```css
.child {
  position: absolute;
  left: 25%;
  top: 10%;
}
```

Resolution:

- `left`/`right` percentages use containing block width.
- `top`/`bottom` percentages use containing block height.

Given:

```css
.parent {
  width: 1000px;
  height: 500px;
}
```

Results:

```text
left: 25% → 250px
top: 10%  → 50px
```

---

## Percentage margins

```css
.child {
  position: absolute;
  margin-top: 10%;
  margin-left: 10%;
}
```

A common interview point:

Historically, percentage margins are calculated from the **containing block's width**, even for vertical margins.

```css
.parent {
  width: 800px;
}
```

Results:

```text
margin-top: 10%  → 80px
margin-left: 10% → 80px
```

This behavior often surprises developers.

---

## Percentage padding

Likewise:

```css
.child {
  padding-top: 10%;
}
```

Traditionally resolves against the containing block width.

```css
.parent {
  width: 1000px;
}
```

Result:

```text
padding-top: 10% → 100px
```

This behavior enabled classic intrinsic-ratio techniques before `aspect-ratio` existed.

---

## When percentages become tricky

A percentage only resolves if the browser knows the relevant dimension.

Example:

```css
.parent {
  position: relative;
  width: 600px;
  /* no explicit height */
}

.child {
  position: absolute;
  height: 50%;
}
```

The containing block's height may be indefinite, so `height: 50%` cannot always be resolved as expected.

This is one reason why percentage heights are often more problematic than percentage widths.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .card {
        position: relative;
        width: 600px;
        height: 300px;
        border: 2px solid #333;
      }

      .badge {
        position: absolute;
        top: 10%;
        left: 5%;
        width: 30%;
        height: 20%;
        background: coral;
        color: white;
        display: grid;
        place-items: center;
      }
    </style>
  </head>
  <body>
    <div class="card">
      <div class="badge">Badge</div>
    </div>
  </body>
</html>
```

Computed values:

```text
top    = 30px
left   = 30px
width  = 180px
height = 60px
```

All percentages are resolved against the `.card` containing block.

---

# Pitfalls

- **Percentage heights require a definite containing block height.** Without one, results may be unexpected or behave like `auto`.
- **Vertical margin and padding percentages are based on width**, not height, which frequently surprises developers.
- Absolute positioning ignores normal document flow, so percentage-based positioning can overlap content if layouts change.
- Different writing modes and logical inset properties (`inset-block-start`, `inset-inline-start`) can affect how developers reason about axes.

## Question 2. How are percentage paddings calculated?

## Question 3. How does min-content sizing affect flex items?

## Question 4. How does aspect ratio interact with width and height?

## Question 5. How does overflow interact with border-radius?

## Question 6. How does transform affect stacking context?

## Question 7. How does position sticky interact with overflow?

## Question 8. How does z-index behave inside flex and grid items?

## Question 9. How does CSS handle fractional pixels?

## Question 10. How does device pixel ratio affect layout?

## Question 11. How does CSS adapt to high DPI screens?

## Question 12. How do media queries evaluate in nested browsing contexts?

## Question 13. How does CSS behave in iframes?

## Question 14. How does shadow DOM encapsulation affect CSS cascade?

## Question 15. How does CSS inheritance behave inside shadow roots?

## Question 16. How do custom properties cross shadow boundaries?

## Question 17. How do container queries evaluate nested containers?

## Question 18. How does scroll snapping behave with dynamic content?

## Question 19. How does CSS interact with Web Components?

## Question 20. How do you stay updated with evolving CSS specifications?
