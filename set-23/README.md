# Set 23

| #   | Question                                                                                                                                    |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you create fluid spacing using CSS variables?](#question-1-how-do-you-create-fluid-spacing-using-css-variables)                     |
| 2   | [How do you create responsive cards with equal ratios?](#question-2-how-do-you-create-responsive-cards-with-equal-ratios)                   |
| 3   | [How do you animate between grid layouts?](#question-3-how-do-you-animate-between-grid-layouts)                                             |
| 4   | [How do you prevent cumulative layout shift in dynamic content?](#question-4-how-do-you-prevent-cumulative-layout-shift-in-dynamic-content) |
| 5   | [How do you ensure layout stability during font loading?](#question-5-how-do-you-ensure-layout-stability-during-font-loading)               |
| 6   | [How do you create a timeline component?](#question-6-how-do-you-create-a-timeline-component)                                               |
| 7   | [How do you design a responsive dashboard layout?](#question-7-how-do-you-design-a-responsive-dashboard-layout)                             |
| 8   | [How do you prevent CSS from affecting third-party widgets?](#question-8-how-do-you-prevent-css-from-affecting-third-party-widgets)         |
| 9   | [How do you sandbox CSS styles?](#question-9-how-do-you-sandbox-css-styles)                                                                 |
| 10  | [How do you isolate CSS for embeddable components?](#question-10-how-do-you-isolate-css-for-embeddable-components)                          |
| 11  | [How do you architect CSS for a design system?](#question-11-how-do-you-architect-css-for-a-design-system)                                  |
| 12  | [How do you handle theme switching at scale?](#question-12-how-do-you-handle-theme-switching-at-scale)                                      |
| 13  | [How do you manage CSS variables dynamically?](#question-13-how-do-you-manage-css-variables-dynamically)                                    |
| 14  | [How do you design a scalable spacing system?](#question-14-how-do-you-design-a-scalable-spacing-system)                                    |
| 15  | [How do you ensure consistent typography across browsers?](#question-15-how-do-you-ensure-consistent-typography-across-browsers)            |
| 16  | [How do you prevent specificity wars?](#question-16-how-do-you-prevent-specificity-wars)                                                    |
| 17  | [How do you migrate from global CSS to modular CSS?](#question-17-how-do-you-migrate-from-global-css-to-modular-css)                        |
| 18  | [How do you design CSS for white-label applications?](#question-18-how-do-you-design-css-for-white-label-applications)                      |
| 19  | [How do you manage performance budgets for CSS?](#question-19-how-do-you-manage-performance-budgets-for-css)                                |
| 20  | [How do you split CSS by route in large SPAs?](#question-20-how-do-you-split-css-by-route-in-large-spas)                                    |

## Question 1. How do you create fluid spacing using CSS variables?

# Short answer

Fluid spacing can be created by combining **CSS custom properties (variables)** with responsive functions like `clamp()`, `min()`, `max()`, or viewport-relative units (`vw`, `vi`). This allows spacing values to scale smoothly between a minimum and maximum size instead of changing abruptly at breakpoints.

---

# Explanation

In modern design systems, fixed spacing scales (`8px`, `16px`, `24px`) often produce noticeable jumps when layouts switch between breakpoints. Fluid spacing solves this by allowing margins, paddings, and gaps to grow proportionally with the viewport size.

A common approach is to define spacing tokens as CSS variables:

```css
--space-m: clamp(1rem, 0.8rem + 1vw, 2rem);
```

This means:

- **Minimum:** `1rem`
- **Preferred fluid value:** `0.8rem + 1vw`
- **Maximum:** `2rem`

As the viewport grows, the spacing smoothly increases until it reaches the maximum value.

### Why use CSS variables?

Custom properties provide:

- Centralized spacing definitions
- Consistent spacing across components
- Easy theming and design token integration
- Reduced media-query maintenance

### Design-system pattern

Many teams define a fluid spacing scale:

```css
--space-xs
--space-sm
--space-md
--space-lg
--space-xl
```

Components then consume tokens rather than hardcoded values:

```css
.card {
  padding: var(--space-md);
}

.stack {
  gap: var(--space-lg);
}
```

This keeps layouts consistent and easier to maintain.

### Accessibility considerations

Fluid spacing generally improves readability because content gets more breathing room on larger screens. However:

- Avoid tying spacing entirely to viewport units.
- Always provide sensible minimum values with `clamp()`.
- Test zoom levels (200%+) to ensure layouts remain usable.
- Prefer `rem`-based minimums and maximums so spacing respects user font settings.

### Performance

CSS variables are highly efficient. Defining spacing tokens once and reusing them is typically more maintainable than maintaining many breakpoint-specific spacing rules.

---

# Example

A production-style fluid spacing scale:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <style>
      :root {
        /* Fluid spacing tokens */
        --space-xs: clamp(0.5rem, 0.4rem + 0.3vw, 0.75rem);
        --space-sm: clamp(0.75rem, 0.6rem + 0.5vw, 1rem);
        --space-md: clamp(1rem, 0.8rem + 1vw, 2rem);
        --space-lg: clamp(1.5rem, 1rem + 2vw, 3rem);
      }

      body {
        margin: 0;
        font-family: system-ui, sans-serif;
        padding: var(--space-lg);
      }

      .card-list {
        display: grid;
        gap: var(--space-md);
      }

      .card {
        padding: var(--space-md);
        border: 1px solid #ddd;
        border-radius: 0.75rem;
      }

      .card h2 {
        margin-block-end: var(--space-sm);
      }
    </style>
  </head>
  <body>
    <div class="card-list">
      <article class="card">
        <h2>Fluid spacing</h2>
        <p>Padding and gaps scale smoothly with viewport size.</p>
      </article>

      <article class="card">
        <h2>Design tokens</h2>
        <p>Components consume reusable spacing variables.</p>
      </article>
    </div>
  </body>
</html>
```

---

# Pitfalls

- **Using only `vw` units:** Spacing may become too small on mobile or excessively large on ultrawide screens. Use `clamp()` to establish limits.
- **Overly aggressive scaling:** Large viewport coefficients can create inconsistent visual rhythm across screen sizes.
- **Mixing fixed and fluid scales randomly:** Establish a clear token system to avoid unpredictable layouts.
- **Ignoring container-based layouts:** Sometimes spacing should respond to component width rather than viewport width; consider container queries where appropriate.

## Question 2. How do you create responsive cards with equal ratios?

## Question 3. How do you animate between grid layouts?

## Question 4. How do you prevent cumulative layout shift in dynamic content?

## Question 5. How do you ensure layout stability during font loading?

## Question 6. How do you create a timeline component?

## Question 7. How do you design a responsive dashboard layout?

## Question 8. How do you prevent CSS from affecting third-party widgets?

## Question 9. How do you sandbox CSS styles?

## Question 10. How do you isolate CSS for embeddable components?

## Question 11. How do you architect CSS for a design system?

## Question 12. How do you handle theme switching at scale?

## Question 13. How do you manage CSS variables dynamically?

## Question 14. How do you design a scalable spacing system?

## Question 15. How do you ensure consistent typography across browsers?

## Question 16. How do you prevent specificity wars?

## Question 17. How do you migrate from global CSS to modular CSS?

## Question 18. How do you design CSS for white-label applications?

## Question 19. How do you manage performance budgets for CSS?

## Question 20. How do you split CSS by route in large SPAs?
