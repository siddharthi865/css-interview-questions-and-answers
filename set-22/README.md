# Set 22

| #   | Question                                                                                                                                                                               |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you create a loading spinner using CSS?](#question-1-how-do-you-create-a-loading-spinner-using-css)                                                                            |
| 2   | [How do you create skeleton loaders?](#question-2-how-do-you-create-skeleton-loaders)                                                                                                  |
| 3   | [How do you prevent flickering during CSS transitions?](#question-3-how-do-you-prevent-flickering-during-css-transitions)                                                              |
| 4   | [How do you apply styles conditionally in pure CSS?](#question-4-how-do-you-apply-styles-conditionally-in-pure-css)                                                                    |
| 5   | [How do you create a print-friendly stylesheet?](#question-5-how-do-you-create-a-print-friendly-stylesheet)                                                                            |
| 6   | [How do you build a responsive navbar without media queries?](#question-6-how-do-you-build-a-responsive-navbar-without-media-queries)                                                  |
| 7   | [How do you create a masonry layout without JavaScript?](#question-7-how-do-you-create-a-masonry-layout-without-javascript)                                                            |
| 8   | [How do you build a multi-step progress indicator?](#question-8-how-do-you-build-a-multi-step-progress-indicator)                                                                      |
| 9   | [How do you create a pure CSS tabs component?](#question-9-how-do-you-create-a-pure-css-tabs-component)                                                                                |
| 10  | [How do you create an accessible accordion with CSS only?](#question-10-how-do-you-create-an-accessible-accordion-with-css-only)                                                       |
| 11  | [How do you create a responsive sidebar layout?](#question-11-how-do-you-create-a-responsive-sidebar-layout)                                                                           |
| 12  | [How do you handle safe area insets on iOS?](#question-12-how-do-you-handle-safe-area-insets-on-ios)                                                                                   |
| 13  | [How do you create a glassmorphism effect?](#question-13-how-do-you-create-a-glassmorphism-effect)                                                                                     |
| 14  | [How do you implement neumorphism in CSS?](#question-14-how-do-you-implement-neumorphism-in-css)                                                                                       |
| 15  | [How do you create parallax scrolling using CSS?](#question-15-how-do-you-create-parallax-scrolling-using-css)                                                                         |
| 16  | [How do you prevent z-index conflicts in large projects?](#question-16-how-do-you-prevent-z-index-conflicts-in-large-projects)                                                         |
| 17  | [How do you manage stacking contexts intentionally?](#question-17-how-do-you-manage-stacking-contexts-intentionally)                                                                   |
| 18  | [How do you debug overflow issues in complex layouts?](#question-18-how-do-you-debug-overflow-issues-in-complex-layouts)                                                               |
| 19  | [How do you create a full-screen overlay?](#question-19-how-do-you-create-a-full-screen-overlay)                                                                                       |
| 20  | [How do you center content both horizontally and vertically without Flexbox or Grid?](#question-20-how-do-you-center-content-both-horizontally-and-vertically-without-flexbox-or-grid) |

## Question 1. How do you create a loading spinner using CSS?

# Short answer

A CSS loading spinner is typically created by styling an element with a circular border, making one border side a different color, and continuously rotating it using a CSS `@keyframes` animation.

# Explanation

The most common production approach uses:

1. A square element with equal width and height.
2. `border-radius: 50%` to make it circular.
3. A semi-transparent border around the circle.
4. One border edge (usually `border-top`) with a contrasting color.
5. A continuous rotation animation using `transform: rotate()`.

Why this approach is popular:

- **Simple and lightweight** — no images or SVGs required.
- **GPU-friendly** — animating `transform` is generally performant because it avoids layout and paint work.
- **Themeable** — colors, sizes, and speeds can be controlled with CSS custom properties.
- **Reusable** — easy to wrap in a design system component.

For accessibility:

- A spinner alone does not communicate progress to screen readers.
- Use `aria-busy="true"` on the loading container.
- Optionally include visually hidden text such as "Loading..." for assistive technologies.
- If loading takes significant time, consider showing progress or status updates instead of an indefinite spinner.

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      :root {
        --spinner-size: 2rem;
        --spinner-color: #2563eb;
        --spinner-track: #e5e7eb;
      }

      .spinner {
        width: var(--spinner-size);
        height: var(--spinner-size);
        border: 4px solid var(--spinner-track);
        border-top-color: var(--spinner-color);
        border-radius: 50%;
        animation: spin 0.8s linear infinite;
      }

      @keyframes spin {
        to {
          transform: rotate(360deg);
        }
      }

      /* Screen-reader-only utility */
      .sr-only {
        position: absolute;
        width: 1px;
        height: 1px;
        overflow: hidden;
        clip-path: inset(50%);
      }
    </style>
  </head>
  <body>
    <div aria-busy="true" aria-live="polite">
      <div class="spinner" aria-hidden="true"></div>
      <span class="sr-only">Loading...</span>
    </div>
  </body>
</html>
```

# Pitfalls

- **Animating non-transform properties** (e.g., width, height, box-shadow) can be less performant than animating `transform`.
- **Missing accessibility support** can leave screen-reader users without feedback.
- **Very fast animations** may feel distracting; 0.8–1.2 seconds per rotation is usually reasonable.
- Respect user preferences with `prefers-reduced-motion`:

```css
@media (prefers-reduced-motion: reduce) {
  .spinner {
    animation: none;
  }
}
```

## Question 2. How do you create skeleton loaders?

## Question 3. How do you prevent flickering during CSS transitions?

## Question 4. How do you apply styles conditionally in pure CSS?

## Question 5. How do you create a print-friendly stylesheet?

## Question 6. How do you build a responsive navbar without media queries?

## Question 7. How do you create a masonry layout without JavaScript?

## Question 8. How do you build a multi-step progress indicator?

## Question 9. How do you create a pure CSS tabs component?

## Question 10. How do you create an accessible accordion with CSS only?

## Question 11. How do you create a responsive sidebar layout?

## Question 12. How do you handle safe area insets on iOS?

## Question 13. How do you create a glassmorphism effect?

## Question 14. How do you implement neumorphism in CSS?

## Question 15. How do you create parallax scrolling using CSS?

## Question 16. How do you prevent z-index conflicts in large projects?

## Question 17. How do you manage stacking contexts intentionally?

## Question 18. How do you debug overflow issues in complex layouts?

## Question 19. How do you create a full-screen overlay?

## Question 20. How do you center content both horizontally and vertically without Flexbox or Grid?
