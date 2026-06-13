# Set 5

| #   | Question                                                                                                                                                                       |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | [How does CSS affect rendering performance?](#question-1-how-does-css-affect-rendering-performance)                                                                            |
| 2   | [What is critical CSS?](#question-2-what-is-critical-css)                                                                                                                      |
| 3   | [How do you optimize CSS for large applications?](#question-3-how-do-you-optimize-css-for-large-applications)                                                                  |
| 4   | [What is the difference between will-change and transform?](#question-4-what-is-the-difference-between-will-change-and-transform)                                              |
| 5   | [What are repaint and reflow?](#question-5-what-are-repaint-and-reflow)                                                                                                        |
| 6   | [How do you reduce layout shifts?](#question-6-how-do-you-reduce-layout-shifts)                                                                                                |
| 7   | [What is BEM methodology?](#question-7-what-is-bem-methodology)                                                                                                                |
| 8   | [What is CSS-in-JS?](#question-8-what-is-css-in-js)                                                                                                                            |
| 9   | [What is tree shaking in CSS?](#question-9-what-is-tree-shaking-in-css)                                                                                                        |
| 10  | [What are CSS preprocessors?](#question-10-what-are-css-preprocessors)                                                                                                         |
| 11  | [What is the difference between SCSS and SASS?](#question-11-what-is-the-difference-between-scss-and-sass)                                                                     |
| 12  | [What are mixins?](#question-12-what-are-mixins)                                                                                                                               |
| 13  | [What is CSS Modules?](#question-13-what-is-css-modules)                                                                                                                       |
| 14  | [What is shadow DOM styling?](#question-14-what-is-shadow-dom-styling)                                                                                                         |
| 15  | [What is container queries?](#question-15-what-is-container-queries)                                                                                                           |
| 16  | [What is subgrid?](#question-16-what-is-subgrid)                                                                                                                               |
| 17  | [What is the difference between content-box and border-box?](#question-17-what-is-the-difference-between-content-box-and-border-box)                                           |
| 18  | [What is progressive enhancement in CSS?](#question-18-what-is-progressive-enhancement-in-css)                                                                                 |
| 19  | [How does z-index stacking context work?](#question-19-how-does-z-index-stacking-context-work)                                                                                 |
| 20  | [How would you design a scalable CSS architecture for a large React application?](#question-20-how-would-you-design-a-scalable-css-architecture-for-a-large-react-application) |

## Question 1. How does CSS affect rendering performance?

## Short answer

CSS impacts rendering performance by influencing **style calculation, layout (reflow), paint, and compositing stages** of the browser rendering pipeline. Poorly structured CSS (large stylesheets, complex selectors, frequent layout-triggering changes) can significantly slow down page rendering.

---

## Explanation

CSS is processed as part of the **Critical Rendering Path (CRP)**:

1. **CSSOM construction**
   - Browser parses CSS into a CSS Object Model.
   - Large or blocking stylesheets delay first render because CSS is render-blocking.

2. **Style calculation (recalculation)**
   - Browser matches CSS rules to DOM elements.
   - Complex selectors (e.g., deep descendant chains or universal selectors) increase matching cost.

3. **Layout (reflow)**
   - Calculates geometry: size and position of elements.
   - Triggered by changes in layout-affecting properties like `width`, `height`, `display`, `margin`.

4. **Paint**
   - Fills pixels (colors, shadows, borders, text).
   - Expensive when large areas or complex effects (box-shadow, filters) are used.

5. **Compositing**
   - Combines painted layers.
   - Efficient when using properties like `transform` and `opacity` (GPU-accelerated).

### Key performance impacts of CSS

- **Render-blocking CSS**
  - CSS must be downloaded and parsed before rendering (prevents FOUC).

- **Selector complexity**
  - `.a .b .c .d` forces deeper DOM traversal during style matching.

- **Layout thrashing**
  - Repeated reads/writes that force synchronous reflow.

- **Large unused CSS**
  - Increases parse time, memory usage, and network cost.

- **Animations affecting layout vs composite**
  - `top/left/width` → triggers layout + paint
  - `transform/opacity` → only compositing (fast path)

- **Repaint vs Reflow cost**
  - Reflow is significantly more expensive than repaint.

---

## Example

### Expensive vs optimized animation

```html
<div class="box"></div>

<style>
  .box {
    width: 100px;
    height: 100px;
    background: coral;

    /* GOOD: compositor-only animation */
    animation: move 2s infinite alternate;
  }

  @keyframes move {
    from {
      transform: translateX(0);
    }
    to {
      transform: translateX(300px);
    }
  }

  /* BAD (commented): causes layout + paint every frame */
  /*
.box {
  position: relative;
  animation: moveBad 2s infinite alternate;
}

@keyframes moveBad {
  from { left: 0; }
  to { left: 300px; }
}
*/
</style>
```

---

## Pitfalls

- Using layout-triggering properties (`top`, `left`, `width`) for animations instead of `transform`
- Overly complex selectors increasing style recalculation time
- Large monolithic CSS files blocking first paint
- Frequent DOM reads/writes causing **layout thrashing**
- Overuse of expensive effects like `filter`, `box-shadow`, `backdrop-filter`
- Not using `will-change` carefully (can increase memory usage if misused)

## Question 2. What is critical CSS?

## Question 3. How do you optimize CSS for large applications?

## Question 4. What is the difference between will-change and transform?

## Question 5. What are repaint and reflow?

## Question 6. How do you reduce layout shifts?

## Question 7. What is BEM methodology?

## Question 8. What is CSS-in-JS?

## Question 9. What is tree shaking in CSS?

## Question 10. What are CSS preprocessors?

## Question 11. What is the difference between SCSS and SASS?

## Question 12. What are mixins?

## Question 13. What is CSS Modules?

## Question 14. What is shadow DOM styling?

## Question 15. What is container queries?

## Question 16. What is subgrid?

## Question 17. What is the difference between content-box and border-box?

## Question 18. What is progressive enhancement in CSS?

## Question 19. How does z-index stacking context work?

## Question 20. How would you design a scalable CSS architecture for a large React application?
