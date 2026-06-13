# Set 19

| #   | Question                                                                                                                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is offset-rotate?](#question-1-what-is-offset-rotate)                                                                   |
| 2   | [What is animation-composition?](#question-2-what-is-animation-composition)                                                   |
| 3   | [What is timeline-scope?](#question-3-what-is-timeline-scope)                                                                 |
| 4   | [What is steps() timing function?](#question-4-what-is-steps-timing-function)                                                 |
| 5   | [What is cubic-bezier curve customization?](#question-5-what-is-cubic-bezier-curve-customization)                             |
| 6   | [How do you detect expensive CSS selectors?](#question-6-how-do-you-detect-expensive-css-selectors)                           |
| 7   | [Why are deep descendant selectors problematic?](#question-7-why-are-deep-descendant-selectors-problematic)                   |
| 8   | [What is style recalculation cost?](#question-8-what-is-style-recalculation-cost)                                             |
| 9   | [How does CSS impact Largest Contentful Paint (LCP)?](#question-9-how-does-css-impact-largest-contentful-paint-lcp)           |
| 10  | [How does unused CSS affect performance?](#question-10-how-does-unused-css-affect-performance)                                |
| 11  | [What is CSS parsing error handling?](#question-11-what-is-css-parsing-error-handling)                                        |
| 12  | [What is at-rule syntax?](#question-12-what-is-at-rule-syntax)                                                                |
| 13  | [What is nesting in modern CSS?](#question-13-what-is-nesting-in-modern-css)                                                  |
| 14  | [How does CSS cascade layering interact with !important?](#question-14-how-does-css-cascade-layering-interact-with-important) |
| 15  | [What is origin precedence in cascade layers?](#question-15-what-is-origin-precedence-in-cascade-layers)                      |
| 16  | [What is selector specificity weight calculation?](#question-16-what-is-selector-specificity-weight-calculation)              |
| 17  | [What is custom media query?](#question-17-what-is-custom-media-query)                                                        |
| 18  | [What is container style query?](#question-18-what-is-container-style-query)                                                  |
| 19  | [What is size query vs inline-size query?](#question-19-what-is-size-query-vs-inline-size-query)                              |
| 20  | [What is style query evaluation order?](#question-20-what-is-style-query-evaluation-order)                                    |

## Question 1. What is offset-rotate?

# Short answer

`offset-rotate` is a CSS Motion Path property that controls how an element rotates while moving along a path defined by `offset-path`. It determines whether the element automatically aligns with the direction of the path, stays fixed, or applies an additional rotation angle.

Common values:

```css
offset-rotate: auto;
offset-rotate: reverse;
offset-rotate: auto 45deg;
offset-rotate: 90deg;
```

---

# Explanation

`offset-rotate` is part of the CSS Motion Path specification and works together with:

- `offset-path` → defines the path
- `offset-distance` → defines how far along the path the element has moved
- `offset-anchor` → defines the alignment point
- `offset-rotate` → controls orientation during movement

Without `offset-rotate`, an object moving along a curved path might not point in the direction it's traveling.

### Values

### `auto`

The element rotates so its forward direction follows the tangent of the path.

```css
offset-rotate: auto;
```

Useful for:

- Cars following roads
- Airplanes following flight paths
- Animated icons moving along curves

### `reverse`

Like `auto`, but rotated 180°.

```css
offset-rotate: reverse;
```

Useful when the graphic faces the opposite direction by default.

### Fixed angle

Keeps the element at a constant rotation regardless of path direction.

```css
offset-rotate: 90deg;
```

### Auto with additional angle

Follows the path and then adds an extra rotation.

```css
offset-rotate: auto 45deg;
```

Useful when the asset's natural orientation doesn't match the path direction.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .scene {
        width: 500px;
        height: 250px;
        border: 1px solid #ccc;
        position: relative;
      }

      .car {
        width: 40px;
        height: 20px;
        background: tomato;
        border-radius: 4px;

        offset-path: path("M20,200 C120,20 380,20 480,200");
        offset-rotate: auto;

        animation: drive 5s linear infinite;
      }

      @keyframes drive {
        to {
          offset-distance: 100%;
        }
      }
    </style>
  </head>
  <body>
    <div class="scene">
      <div class="car"></div>
    </div>
  </body>
</html>
```

The rectangle automatically rotates as it moves along the curve, making it appear to "drive" naturally.

---

# Pitfalls

- **Asset orientation matters:** `auto` assumes the element's forward direction points to the right. If your SVG or image faces another direction, use `auto 90deg`, `auto -90deg`, etc.
- **Browser support:** Motion Path properties are supported in modern Chrome, Edge, Safari, and Firefox, but verify support requirements for your target browsers.
- **Performance:** Motion path animations are generally efficient, but very complex SVG paths can increase rendering costs.
- **Accessibility:** Motion-heavy UI can be distracting. Respect user preferences with `prefers-reduced-motion`.

```css
@media (prefers-reduced-motion: reduce) {
  .car {
    animation: none;
  }
}
```

## Question 2. What is animation-composition?

## Question 3. What is timeline-scope?

## Question 4. What is steps() timing function?

## Question 5. What is cubic-bezier curve customization?

## Question 6. How do you detect expensive CSS selectors?

## Question 7. Why are deep descendant selectors problematic?

## Question 8. What is style recalculation cost?

## Question 9. How does CSS impact Largest Contentful Paint (LCP)?

## Question 10. How does unused CSS affect performance?

## Question 11. What is CSS parsing error handling?

## Question 12. What is at-rule syntax?

## Question 13. What is nesting in modern CSS?

## Question 14. How does CSS cascade layering interact with !important?

## Question 15. What is origin precedence in cascade layers?

## Question 16. What is selector specificity weight calculation?

## Question 17. What is custom media query?

## Question 18. What is container style query?

## Question 19. What is size query vs inline-size query?

## Question 20. What is style query evaluation order?
