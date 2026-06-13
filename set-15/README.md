# Set 15

| #   | Question                                                                                                     |
| --- | ------------------------------------------------------------------------------------------------------------ |
| 1   | [How does CSS impact accessibility?](#question-1-how-does-css-impact-accessibility)                          |
| 2   | [How do you ensure sufficient color contrast?](#question-2-how-do-you-ensure-sufficient-color-contrast)      |
| 3   | [How does display: none affect screen readers?](#question-3-how-does-display-none-affect-screen-readers)     |
| 4   | [How does aria-hidden differ from CSS hiding?](#question-4-how-does-aria-hidden-differ-from-css-hiding)      |
| 5   | [What is focus trapping in modals?](#question-5-what-is-focus-trapping-in-modals)                            |
| 6   | [How do you style focus states accessibly?](#question-6-how-do-you-style-focus-states-accessibly)            |
| 7   | [What is prefers-contrast media query?](#question-7-what-is-prefers-contrast-media-query)                    |
| 8   | [What is forced-colors mode?](#question-8-what-is-forced-colors-mode)                                        |
| 9   | [How does CSS affect tab order?](#question-9-how-does-css-affect-tab-order)                                  |
| 10  | [How do you handle reduced motion users?](#question-10-how-do-you-handle-reduced-motion-users)               |
| 11  | [What is PostCSS?](#question-11-what-is-postcss)                                                             |
| 12  | [What is autoprefixer?](#question-12-what-is-autoprefixer)                                                   |
| 13  | [What is CSS bundling?](#question-13-what-is-css-bundling)                                                   |
| 14  | [What is CSS code splitting?](#question-14-what-is-css-code-splitting)                                       |
| 15  | [What is critical rendering path?](#question-15-what-is-critical-rendering-path)                             |
| 16  | [How does Tailwind differ from traditional CSS?](#question-16-how-does-tailwind-differ-from-traditional-css) |
| 17  | [What is utility class collision?](#question-17-what-is-utility-class-collision)                             |
| 18  | [What is purge CSS?](#question-18-what-is-purge-css)                                                         |
| 19  | [How do you debug CSS specificity issues?](#question-19-how-do-you-debug-css-specificity-issues)             |
| 20  | [How would you audit CSS in a legacy project?](#question-20-how-would-you-audit-css-in-a-legacy-project)     |

## Question 1. How does CSS impact accessibility?

# Short answer

CSS has a major impact on accessibility because it controls how content is presented, perceived, navigated, and interacted with. Good CSS improves readability, focus visibility, responsiveness, and usability, while poor CSS can make content difficult or impossible for users with visual, motor, or cognitive disabilities to access.

---

# Explanation

CSS does not provide semantic meaning (HTML does that), but it significantly affects how accessible a website feels and functions.

## 1. Readability and Visual Accessibility

CSS controls:

- Font size
- Line height
- Spacing
- Contrast
- Layout

Example best practices:

```css
body {
  font-size: 1rem;
  line-height: 1.5;
}
```

Poor choices such as tiny fonts, low contrast text, or cramped spacing make content difficult to read.

### Contrast Matters

WCAG recommends:

- 4.5:1 contrast ratio for normal text
- 3:1 for large text

Bad:

```css
color: #aaa;
background: #fff;
```

Better:

```css
color: #222;
background: #fff;
```

---

## 2. Keyboard Accessibility

Many users navigate without a mouse.

CSS should never remove focus indicators without replacing them.

Bad:

```css
button:focus {
  outline: none;
}
```

Better:

```css
button:focus-visible {
  outline: 3px solid royalblue;
  outline-offset: 2px;
}
```

Visible focus states help users know where they are on the page.

---

## 3. Responsive Design and Zoom Support

Users may:

- Zoom pages to 200%+
- Use mobile devices
- Use screen magnifiers

Using relative units helps layouts adapt.

Good:

```css
font-size: 1rem;
width: 100%;
max-width: 60rem;
```

Avoid locking layouts with fixed pixel dimensions.

---

## 4. Respecting User Preferences

Modern CSS can react to accessibility preferences.

### Reduced Motion

Some users experience dizziness or motion sickness.

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none;
    transition: none;
  }
}
```

### Dark/Light Mode

```css
@media (prefers-color-scheme: dark) {
  body {
    background: black;
    color: white;
  }
}
```

This improves comfort and usability.

---

## 5. Content Order vs Visual Order

Flexbox and Grid allow visual reordering.

Example:

```css
.item {
  order: 2;
}
```

The screen reader and keyboard navigation order still follow the HTML source order.

A common accessibility issue is making the visual order differ from the logical document order.

Prefer keeping:

- DOM order
- Visual order
- Tab order

aligned whenever possible.

---

## 6. Hiding Content Correctly

CSS can hide content in different ways.

### Completely Hidden

```css
display: none;
```

or

```css
visibility: hidden;
```

These generally remove content from both visual display and accessibility APIs.

### Visually Hidden but Screen Reader Accessible

```css
.visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  overflow: hidden;
  clip-path: inset(50%);
  white-space: nowrap;
}
```

Useful for:

- Skip links
- Extra descriptive labels
- Screen-reader-only text

---

## 7. Touch Targets and Motor Accessibility

Buttons and links should be easy to activate.

Bad:

```css
button {
  width: 20px;
  height: 20px;
}
```

Better:

```css
button {
  min-width: 44px;
  min-height: 44px;
}
```

Larger targets help users with limited motor control and touch-device users.

---

## Example

```html
<button class="cta">Subscribe</button>

<style>
  :root {
    --focus-color: royalblue;
  }

  .cta {
    padding: 0.75rem 1rem;
    font-size: 1rem;
    border: none;
    border-radius: 0.5rem;
  }

  .cta:focus-visible {
    outline: 3px solid var(--focus-color);
    outline-offset: 3px;
  }

  @media (prefers-reduced-motion: reduce) {
    .cta {
      transition: none;
    }
  }
</style>
```

This example provides:

- Adequate sizing
- Keyboard focus visibility
- Respect for reduced-motion preferences
- Scalable typography

---

# Pitfalls

- Removing focus outlines (`outline: none`) without providing an accessible replacement.
- Using low color contrast that fails WCAG requirements.
- Reordering content visually with Flexbox/Grid while leaving a different DOM order.
- Relying solely on color to communicate meaning (e.g., red text for errors without icons or text labels).

## Question 2. How do you ensure sufficient color contrast?

## Question 3. How does display: none affect screen readers?

## Question 4. How does aria-hidden differ from CSS hiding?

## Question 5. What is focus trapping in modals?

## Question 6. How do you style focus states accessibly?

## Question 7. What is prefers-contrast media query?

## Question 8. What is forced-colors mode?

## Question 9. How does CSS affect tab order?

## Question 10. How do you handle reduced motion users?

## Question 11. What is PostCSS?

## Question 12. What is autoprefixer?

## Question 13. What is CSS bundling?

## Question 14. What is CSS code splitting?

## Question 15. What is critical rendering path?

## Question 16. How does Tailwind differ from traditional CSS?

## Question 17. What is utility class collision?

## Question 18. What is purge CSS?

## Question 19. How do you debug CSS specificity issues?

## Question 20. How would you audit CSS in a legacy project?
