# Set 8

| #   | Question                                                                                                                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is clear property?](#question-1-what-is-clear-property)                                                                 |
| 2   | [What is clearfix hack?](#question-2-what-is-clearfix-hack)                                                                   |
| 3   | [What is overflow used for clearing floats?](#question-3-what-is-overflow-used-for-clearing-floats)                           |
| 4   | [What is the difference between min-width and max-width?](#question-4-what-is-the-difference-between-min-width-and-max-width) |
| 5   | [What is intrinsic sizing?](#question-5-what-is-intrinsic-sizing)                                                             |
| 6   | [What is ch unit?](#question-6-what-is-ch-unit)                                                                               |
| 7   | [What is ex unit?](#question-7-what-is-ex-unit)                                                                               |
| 8   | [What is vmin and vmax?](#question-8-what-is-vmin-and-vmax)                                                                   |
| 9   | [What is env() function?](#question-9-what-is-env-function)                                                                   |
| 10  | [What is var() fallback value?](#question-10-what-is-var-fallback-value)                                                      |
| 11  | [What is fit-content()?](#question-11-what-is-fit-content)                                                                    |
| 12  | [What is max-content and min-content?](#question-12-what-is-max-content-and-min-content)                                      |
| 13  | [What is object-fit?](#question-13-what-is-object-fit)                                                                        |
| 14  | [What is object-position?](#question-14-what-is-object-position)                                                              |
| 15  | [What is backdrop-filter?](#question-15-what-is-backdrop-filter)                                                              |
| 16  | [What is animation-fill-mode?](#question-16-what-is-animation-fill-mode)                                                      |
| 17  | [What is animation-direction?](#question-17-what-is-animation-direction)                                                      |
| 18  | [What is animation-play-state?](#question-18-what-is-animation-play-state)                                                    |
| 19  | [What is perspective in CSS?](#question-19-what-is-perspective-in-css)                                                        |
| 20  | [What is transform-origin?](#question-20-what-is-transform-origin)                                                            |

## Question 1. What is clear property?

## Short answer

The `clear` property controls whether an element can be positioned next to floated elements or must be moved below them.

---

## Explanation

`clear` is primarily used in float-based layouts to prevent an element from wrapping around floated elements (`float: left/right`).

When an element has a float applied to siblings, normal document flow allows inline content to wrap around it. The `clear` property forces the element to move below floated elements on the specified side(s).

### Values:

- `none` (default): allows wrapping around floats
- `left`: moves below left-floated elements
- `right`: moves below right-floated elements
- `both`: moves below both left and right floats
- `inline-start` / `inline-end`: logical properties (modern, writing-mode aware)

### Modern perspective (important for interviews)

- `clear` is largely a **legacy layout tool** from the float era.
- In modern CSS, it's often replaced by:
  - Flexbox (`display: flex`)
  - Grid (`display: grid`)
  - Block formatting context creation (`display: flow-root`)

- Still relevant for:
  - legacy codebases
  - text wrapping around images in articles
  - email templates

### How it works internally

`clear` influences layout by pushing the element down until it no longer intersects the margin box of floated elements in the specified direction.

---

## Example

### Float layout with `clear: both`

```html
<div class="container">
  <img src="https://via.placeholder.com/120" class="float-left" />
  <p>This text wraps around the image.</p>

  <div class="footer">I must appear below the float.</div>
</div>
```

```css
.float-left {
  float: left;
  margin-right: 12px;
}

.footer {
  clear: both;
  background: #f3f3f3;
  padding: 8px;
  margin-top: 8px;
}
```

### Modern alternative (preferred)

```css
.container {
  display: flow-root; /* creates BFC, contains floats */
}
```

---

## Pitfalls

- ❌ Overuse of floats + clear leads to fragile layouts
- ❌ Can cause unexpected vertical gaps due to float clearing behavior
- ❌ Harder debugging compared to Flex/Grid
- ❌ `clear` does not work with Flex/Grid children in the same way (floats are removed from layout flow there)
- ⚠️ Requires clearfix hacks in older patterns (`::after { clear: both; }`)
- ⚠️ Browser support for logical values (`inline-start/end`) is modern but not relevant in legacy email clients

## Question 2. What is clearfix hack?

## Question 3. What is overflow used for clearing floats?

## Question 4. What is the difference between min-width and max-width?

## Question 5. What is intrinsic sizing?

## Question 6. What is ch unit?

## Question 7. What is ex unit?

## Question 8. What is vmin and vmax?

## Question 9. What is env() function?

## Question 10. What is var() fallback value?

## Question 11. What is fit-content()?

## Question 12. What is max-content and min-content?

## Question 13. What is object-fit?

## Question 14. What is object-position?

## Question 15. What is backdrop-filter?

## Question 16. What is animation-fill-mode?

## Question 17. What is animation-direction?

## Question 18. What is animation-play-state?

## Question 19. What is perspective in CSS?

## Question 20. What is transform-origin?
