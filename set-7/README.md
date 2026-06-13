# Set 7

| #   | Question                                                                                                                   |
| --- | -------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you remove bullets from a list?](#question-1-how-do-you-remove-bullets-from-a-list)                                |
| 2   | [What is list-style-type?](#question-2-what-is-list-style-type)                                                            |
| 3   | [What is list-style-position?](#question-3-what-is-list-style-position)                                                    |
| 4   | [How do you style table rows alternately?](#question-4-how-do-you-style-table-rows-alternately)                            |
| 5   | [What is border-collapse?](#question-5-what-is-border-collapse)                                                            |
| 6   | [What is caption-side?](#question-6-what-is-caption-side)                                                                  |
| 7   | [How do you make a table responsive?](#question-7-how-do-you-make-a-table-responsive)                                      |
| 8   | [What is table-layout: fixed?](#question-8-what-is-table-layout-fixed)                                                     |
| 9   | [What is empty-cells?](#question-9-what-is-empty-cells)                                                                    |
| 10  | [What is vertical-align used for in tables?](#question-10-what-is-vertical-align-used-for-in-tables)                       |
| 11  | [How do you style input placeholders?](#question-11-how-do-you-style-input-placeholders)                                   |
| 12  | [What is :focus pseudo-class?](#question-12-what-is-focus-pseudo-class)                                                    |
| 13  | [How do you remove default browser styles from inputs?](#question-13-how-do-you-remove-default-browser-styles-from-inputs) |
| 14  | [What is appearance: none?](#question-14-what-is-appearance-none)                                                          |
| 15  | [How do you style checkboxes and radio buttons?](#question-15-how-do-you-style-checkboxes-and-radio-buttons)               |
| 16  | [What is stacking context?](#question-16-what-is-stacking-context)                                                         |
| 17  | [What properties create a new stacking context?](#question-17-what-properties-create-a-new-stacking-context)               |
| 18  | [What is position: sticky?](#question-18-what-is-position-sticky)                                                          |
| 19  | [How does z-index work with positioned elements?](#question-19-how-does-z-index-work-with-positioned-elements)             |
| 20  | [What is float and why is it deprecated for layout?](#question-20-what-is-float-and-why-is-it-deprecated-for-layout)       |

## Question 1. How do you remove bullets from a list?

## Short answer

Use `list-style: none;` (or `list-style-type: none;`) on the `<ul>` or `<ol>` element to remove bullets.

---

## Explanation

In CSS, list bullets are controlled by the `list-style` family of properties. By default, browsers render:

- `<ul>` → disc bullets
- `<ol>` → numbers

To remove bullets, you disable the marker rendering:

```css
list-style: none;
```

This is shorthand for:

- `list-style-type: none;`
- `list-style-position`
- `list-style-image`

### Senior-level considerations

Removing bullets is often part of creating:

- Navigation menus
- Custom list components (design systems)
- Card layouts using `<ul>` for semantics but custom visuals

However, removing markers does **not reset default spacing**, so you usually also need:

```css
margin: 0;
padding: 0;
```

This is important because browsers apply default `padding-left` to lists for indentation.

### Accessibility note

Even if bullets are removed visually:

- The list semantics remain intact for screen readers
- That’s good—do not replace lists with non-semantic `<div>`s just for styling

If you replace markers with custom icons, ensure:

- Proper spacing
- Sufficient contrast
- Not relying solely on color or shape

---

## Example

### Semantic list with no bullets (production-ready pattern)

```html
<ul class="nav">
  <li><a href="#">Home</a></li>
  <li><a href="#">About</a></li>
  <li><a href="#">Contact</a></li>
</ul>
```

```css
.nav {
  list-style: none;
  margin: 0;
  padding: 0;

  display: flex;
  gap: 16px;
}

.nav a {
  text-decoration: none;
  color: #333;
}
```

---

## Pitfalls

- Forgetting to remove default `padding-left`, causing unexpected indentation
- Using `display: flex` on `<ul>` but not resetting list styles → inconsistent spacing across browsers
- Overriding list styles globally (e.g., `ul { list-style: none; }`) without considering content lists
- Replacing lists with non-semantic elements, harming accessibility and SEO
- In RTL layouts, manual padding adjustments may be needed if you depend on spacing assumptions

## Question 2. What is list-style-type?

## Question 3. What is list-style-position?

## Question 4. How do you style table rows alternately?

## Question 5. What is border-collapse?

## Question 6. What is caption-side?

## Question 7. How do you make a table responsive?

## Question 8. What is table-layout: fixed?

## Question 9. What is empty-cells?

## Question 10. What is vertical-align used for in tables?

## Question 11. How do you style input placeholders?

## Question 12. What is :focus pseudo-class?

## Question 13. How do you remove default browser styles from inputs?

## Question 14. What is appearance: none?

## Question 15. How do you style checkboxes and radio buttons?

## Question 16. What is stacking context?

## Question 17. What properties create a new stacking context?

## Question 18. What is position: sticky?

## Question 19. How does z-index work with positioned elements?

## Question 20. What is float and why is it deprecated for layout?
