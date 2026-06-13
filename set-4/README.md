# Set 4

| #   | Question                                                                                                                               |
| --- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is viewport meta tag?](#question-1-what-is-viewport-meta-tag)                                                                    |
| 2   | [What is clamp() in CSS?](#question-2-what-is-clamp-in-css)                                                                            |
| 3   | [What is aspect-ratio property?](#question-3-what-is-aspect-ratio-property)                                                            |
| 4   | [How do you hide elements on mobile only?](#question-4-how-do-you-hide-elements-on-mobile-only)                                        |
| 5   | [How do you create fluid typography?](#question-5-how-do-you-create-fluid-typography)                                                  |
| 6   | [What is the difference between transition and animation?](#question-6-what-is-the-difference-between-transition-and-animation)        |
| 7   | [What is @keyframes?](#question-7-what-is-keyframes)                                                                                   |
| 8   | [What are animation timing functions?](#question-8-what-are-animation-timing-functions)                                                |
| 9   | [What is transform property?](#question-9-what-is-transform-property)                                                                  |
| 10  | [What is the difference between translate, scale, and rotate?](#question-10-what-is-the-difference-between-translate-scale-and-rotate) |
| 11  | [What is CSS specificity hierarchy?](#question-11-what-is-css-specificity-hierarchy)                                                   |
| 12  | [What is !important and why should it be avoided?](#question-12-what-is-important-and-why-should-it-be-avoided)                        |
| 13  | [How do inline styles compare in specificity?](#question-13-how-do-inline-styles-compare-in-specificity)                               |
| 14  | [What is cascade in CSS?](#question-14-what-is-cascade-in-css)                                                                         |
| 15  | [What is inheritance in CSS?](#question-15-what-is-inheritance-in-css)                                                                 |
| 16  | [What are CSS logical properties?](#question-16-what-are-css-logical-properties)                                                       |
| 17  | [What is :has() selector?](#question-17-what-is-has-selector)                                                                          |
| 18  | [What is the difference between :is() and :where()?](#question-18-what-is-the-difference-between-is-and-where)                         |
| 19  | [What are custom properties (CSS variables)?](#question-19-what-are-custom-properties-css-variables)                                   |
| 20  | [How does variable scoping work in CSS?](#question-20-how-does-variable-scoping-work-in-css)                                           |

## Question 1. What is viewport meta tag?

## Short answer

The **viewport meta tag** is an HTML `<meta>` element used to control how a webpage is displayed on mobile devices by defining the layout viewport’s width and scaling behavior.

---

## Explanation

On mobile browsers, the “viewport” is the visible area of a webpage. Without explicit instructions, browsers typically render pages at a **desktop layout width (often ~980px)** and then scale them down to fit the screen. This leads to tiny, unreadable UI.

The viewport meta tag allows developers to:

- Set the **layout width** to match the device width
- Control **initial zoom level**
- Restrict or allow **user scaling**
- Improve **responsive design behavior**

### Why it matters (senior-level perspective)

- It is foundational for **responsive design**—without it, media queries behave unexpectedly on mobile.
- It ensures your **CSS breakpoints map to real device widths**, not a virtual desktop canvas.
- It directly impacts **UX accessibility** (zooming, readability).
- It’s part of the browser’s rendering pipeline decision before CSS layout even runs.

### Common configuration

Most modern sites use:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

This tells the browser:

- `width=device-width` → match screen width in CSS pixels
- `initial-scale=1.0` → no initial zoom

You can also control scaling:

- `maximum-scale`
- `minimum-scale`
- `user-scalable=no` (generally discouraged for accessibility)

---

## Example

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <!-- Viewport meta tag -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Responsive Page</title>

    <style>
      body {
        margin: 0;
        font-family: system-ui;
      }

      .container {
        padding: 16px;
        max-width: 768px;
        margin: 0 auto;
      }

      @media (max-width: 600px) {
        .container {
          background: #f5f5f5;
        }
      }
    </style>
  </head>

  <body>
    <div class="container">
      <h1>Viewport Example</h1>
      <p>
        This layout responds correctly on mobile because of the viewport meta
        tag.
      </p>
    </div>
  </body>
</html>
```

---

## Pitfalls

- ❌ **Missing viewport tag** → mobile browsers render scaled-down desktop layout
- ❌ Using `user-scalable=no` → harms accessibility (prevents zooming)
- ❌ Incorrect scaling settings → breaks responsive design assumptions
- ❌ Forgetting it in SSR/templating systems → inconsistent mobile rendering
- ⚠️ Some legacy browsers partially ignore advanced parameters, but `width=device-width` is widely supported

## Question 2. What is clamp() in CSS?

## Question 3. What is aspect-ratio property?

## Question 4. How do you hide elements on mobile only?

## Question 5. How do you create fluid typography?

## Question 6. What is the difference between transition and animation?

## Question 7. What is @keyframes?

## Question 8. What are animation timing functions?

## Question 9. What is transform property?

## Question 10. What is the difference between translate, scale, and rotate?

## Question 11. What is CSS specificity hierarchy?

## Question 12. What is !important and why should it be avoided?

## Question 13. How do inline styles compare in specificity?

## Question 14. What is cascade in CSS?

## Question 15. What is inheritance in CSS?

## Question 16. What are CSS logical properties?

## Question 17. What is :has() selector?

## Question 18. What is the difference between :is() and :where()?

## Question 19. What are custom properties (CSS variables)?

## Question 20. How does variable scoping work in CSS?
