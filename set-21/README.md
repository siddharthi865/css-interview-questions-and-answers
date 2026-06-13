# Set 21

| #   | Question                                                                                                                            |
| --- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you debug a CSS rule that is not being applied?](#question-1-how-do-you-debug-a-css-rule-that-is-not-being-applied)         |
| 2   | [How do you inspect computed styles in browser DevTools?](#question-2-how-do-you-inspect-computed-styles-in-browser-devtools)       |
| 3   | [How do you determine which rule is overriding another?](#question-3-how-do-you-determine-which-rule-is-overriding-another)         |
| 4   | [How do you reset CSS without using a library?](#question-4-how-do-you-reset-css-without-using-a-library)                           |
| 5   | [What are the pros and cons of CSS reset vs normalize?](#question-5-what-are-the-pros-and-cons-of-css-reset-vs-normalize)           |
| 6   | [How do you create a full-height layout without using vh?](#question-6-how-do-you-create-a-full-height-layout-without-using-vh)     |
| 7   | [How do you prevent layout shift when images load?](#question-7-how-do-you-prevent-layout-shift-when-images-load)                   |
| 8   | [How do you make a sticky footer layout?](#question-8-how-do-you-make-a-sticky-footer-layout)                                       |
| 9   | [How do you prevent text from overflowing a flex container?](#question-9-how-do-you-prevent-text-from-overflowing-a-flex-container) |
| 10  | [How do you create equal-height columns without Grid?](#question-10-how-do-you-create-equal-height-columns-without-grid)            |
| 11  | [How do you prevent horizontal scroll issues?](#question-11-how-do-you-prevent-horizontal-scroll-issues)                            |
| 12  | [How do you handle long unbreakable strings?](#question-12-how-do-you-handle-long-unbreakable-strings)                              |
| 13  | [How do you create a responsive iframe?](#question-13-how-do-you-create-a-responsive-iframe)                                        |
| 14  | [How do you lock body scroll when a modal is open?](#question-14-how-do-you-lock-body-scroll-when-a-modal-is-open)                  |
| 15  | [How do you avoid double scrollbars?](#question-15-how-do-you-avoid-double-scrollbars)                                              |
| 16  | [How do you style elements based on data attributes?](#question-16-how-do-you-style-elements-based-on-data-attributes)              |
| 17  | [How do you animate height from 0 to auto?](#question-17-how-do-you-animate-height-from-0-to-auto)                                  |
| 18  | [How do you create a triangle using only CSS?](#question-18-how-do-you-create-a-triangle-using-only-css)                            |
| 19  | [How do you create a tooltip without JavaScript?](#question-19-how-do-you-create-a-tooltip-without-javascript)                      |
| 20  | [How do you create a dropdown purely with CSS?](#question-20-how-do-you-create-a-dropdown-purely-with-css)                          |

## Question 1. How do you debug a CSS rule that is not being applied?

# Short answer

When a CSS rule is not being applied, I systematically check:

1. **Is the selector matching the element?**
2. **Is the rule being overridden by another rule?** (specificity, cascade, layers, source order)
3. **Is the property valid for that element or state?**
4. **Is the stylesheet loaded correctly?**
5. **Is layout context affecting the result?** (Flexbox, Grid, positioning, inheritance)
6. **What do browser DevTools show in the Computed and Styles panels?**

For senior engineers, DevTools is the primary debugging tool—not guessing.

---

# Explanation

A disciplined debugging process saves time and avoids random CSS changes.

## 1. Verify the selector matches

The most common issue is that the selector doesn't match the intended element.

```css
.card-title {
  color: red;
}
```

```html
<h2 class="title">Hello</h2>
```

The selector never matches because the class names differ.

In browser DevTools:

- Inspect the element.
- Check whether your rule appears in the **Styles** panel.
- If it doesn't appear, the selector isn't matching or the stylesheet isn't loaded.

---

## 2. Check the cascade and specificity

Even if a rule matches, another rule may win.

```css
.card-title {
  color: blue;
}

.sidebar .card-title {
  color: red;
}
```

Inside `.sidebar`, the second rule wins because it is more specific.

Also check:

- Cascade layers (`@layer`)
- Source order
- Inline styles
- `!important`

Example:

```css
.card-title {
  color: blue !important;
}
```

This can override otherwise more specific selectors.

---

## 3. Look at the Computed panel

The **Computed** tab is often more useful than the Styles panel.

It shows:

- Final value actually applied
- Which rule provided the value
- Whether the property is inherited

Example:

```css
.card {
  color: red;
}

.card-title {
  color: inherit;
}
```

Computed styles help trace inheritance chains.

---

## 4. Verify the stylesheet is loaded

Sometimes the CSS file never reaches the browser.

Check:

```html
<link rel="stylesheet" href="/styles/main.css" />
```

Common issues:

- Wrong path
- Network error (404)
- Build pipeline problems
- Cache serving an old file

Use the Network tab to verify the file loads successfully.

---

## 5. Validate the property itself

Some properties don't apply in certain contexts.

Example:

```css
span {
  width: 200px;
}
```

A normal inline element ignores `width`.

Fix:

```css
span {
  display: inline-block;
  width: 200px;
}
```

Other common examples:

- `z-index` requires positioning or stacking context awareness.
- `justify-content` only works on flex/grid containers.
- `grid-column` only works on grid items.
- `flex-grow` only works on flex items.

---

## 6. Check layout context

Many CSS issues are actually layout issues.

Example:

```css
.child {
  height: 100%;
}
```

This won't work if the parent doesn't have a defined height.

Similarly:

- Flexbox alignment may override expectations.
- Grid sizing may affect dimensions.
- Positioning may remove elements from normal flow.

Understanding the formatting context is often the real fix.

---

## 7. Check for invalid CSS

Browsers silently ignore invalid declarations.

```css
.button {
  padding: 10;
}
```

Invalid because the unit is missing.

Correct:

```css
.button {
  padding: 10px;
}
```

DevTools usually strikes out invalid declarations.

---

## 8. Consider modern cascade features

In large applications, modern CSS introduces additional debugging points:

```css
@layer reset, components, utilities;
```

A lower-priority layer can lose even with higher specificity.

Also verify:

- CSS Modules
- Shadow DOM
- Scoped styles
- CSS-in-JS generated class names
- Container query conditions
- Feature queries (`@supports`)

---

# Example

A realistic debugging example:

```html
<div class="card">
  <h2 class="title">Product</h2>
</div>

<style>
  .title {
    color: blue;
  }

  .card .title {
    color: red;
  }

  .title {
    color: green;
  }
</style>
```

Result:

- Text is **red**.

Why?

1. All selectors match.
2. `.card .title` has higher specificity.
3. Computed styles show `color: red`.
4. Source order doesn't matter because specificity differs.

This is exactly the type of issue DevTools exposes immediately.

---

# Pitfalls

- **Using `!important` as a debugging tool** often creates larger maintenance problems.
- **Ignoring DevTools Computed styles** can lead to chasing the wrong rule.
- **Forgetting layout context** (Flexbox/Grid/positioning) causes many false CSS assumptions.
- **Not accounting for Shadow DOM, CSS Modules, or CSS-in-JS scoping** can make selectors appear "broken" when they're actually isolated.

## Question 2. How do you inspect computed styles in browser DevTools?

## Question 3. How do you determine which rule is overriding another?

## Question 4. How do you reset CSS without using a library?

## Question 5. What are the pros and cons of CSS reset vs normalize?

## Question 6. How do you create a full-height layout without using vh?

## Question 7. How do you prevent layout shift when images load?

## Question 8. How do you make a sticky footer layout?

## Question 9. How do you prevent text from overflowing a flex container?

## Question 10. How do you create equal-height columns without Grid?

## Question 11. How do you prevent horizontal scroll issues?

## Question 12. How do you handle long unbreakable strings?

## Question 13. How do you create a responsive iframe?

## Question 14. How do you lock body scroll when a modal is open?

## Question 15. How do you avoid double scrollbars?

## Question 16. How do you style elements based on data attributes?

## Question 17. How do you animate height from 0 to auto?

## Question 18. How do you create a triangle using only CSS?

## Question 19. How do you create a tooltip without JavaScript?

## Question 20. How do you create a dropdown purely with CSS?
