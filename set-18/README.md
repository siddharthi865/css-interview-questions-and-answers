# Set 18

| #   | Question                                                                                 |
| --- | ---------------------------------------------------------------------------------------- |
| 1   | [What is baseline alignment?](#question-1-what-is-baseline-alignment)                    |
| 2   | [What is alignment fallback behavior?](#question-2-what-is-alignment-fallback-behavior)  |
| 3   | [What is safe vs unsafe alignment?](#question-3-what-is-safe-vs-unsafe-alignment)        |
| 4   | [What is overflow clip margin?](#question-4-what-is-overflow-clip-margin)                |
| 5   | [What is fragmentation break control?](#question-5-what-is-fragmentation-break-control)  |
| 6   | [What is vertical writing mode?](#question-6-what-is-vertical-writing-mode)              |
| 7   | [What is text-combine-upright?](#question-7-what-is-text-combine-upright)                |
| 8   | [What is hanging-punctuation?](#question-8-what-is-hanging-punctuation)                  |
| 9   | [What is line-break property?](#question-9-what-is-line-break-property)                  |
| 10  | [What is word-break vs overflow-wrap?](#question-10-what-is-word-break-vs-overflow-wrap) |
| 11  | [What is hyphens property?](#question-11-what-is-hyphens-property)                       |
| 12  | [What is ruby annotation in CSS?](#question-12-what-is-ruby-annotation-in-css)           |
| 13  | [What is ruby-position?](#question-13-what-is-ruby-position)                             |
| 14  | [What is logical border properties?](#question-14-what-is-logical-border-properties)     |
| 15  | [What is text-align-last?](#question-15-what-is-text-align-last)                         |
| 16  | [What is scroll-linked animation?](#question-16-what-is-scroll-linked-animation)         |
| 17  | [What is animation-timeline?](#question-17-what-is-animation-timeline)                   |
| 18  | [What is view-timeline?](#question-18-what-is-view-timeline)                             |
| 19  | [What is offset-path?](#question-19-what-is-offset-path)                                 |
| 20  | [What is offset-distance?](#question-20-what-is-offset-distance)                         |

## Question 1. What is baseline alignment?

# Short answer

**Baseline alignment** is a CSS alignment behavior that aligns elements based on the **text baseline** of their content rather than their top, center, or bottom edges. It is commonly used in **Flexbox**, **Grid**, table cells, and inline layouts to keep text across different-sized elements visually aligned.

---

# Explanation

A **baseline** is the invisible line on which most text characters sit. For example, in the word "Hello", the letters rest on a common baseline, while letters like **g**, **p**, and **y** extend below it.

When elements contain text with different font sizes, line heights, icons, or form controls, aligning them with `center` often makes the text appear visually uneven. Baseline alignment solves this by aligning the text baselines instead of the boxes themselves.

Common values:

```css
align-items: baseline;
```

in Flexbox or Grid.

### Why it's useful

Consider a heading and a small label placed side-by-side:

- `align-items: center` aligns the boxes.
- `align-items: baseline` aligns the text itself.

This creates more professional typography and is frequently used in:

- Navigation bars
- Forms and labels
- Pricing components
- Design system layouts
- Mixed typography (e.g., title + badge)

### Flexbox behavior

In a flex container:

```css
display: flex;
align-items: baseline;
```

the browser finds the baseline of each flex item and aligns them on the same line.

### Grid behavior

CSS Grid also supports:

```css
align-items: baseline;
```

or

```css
align-self: baseline;
```

for individual grid items.

### Accessibility and maintainability

- Improves visual readability by keeping text aligned consistently.
- Helpful when supporting dynamic content, localization, or user-scaled text.
- Avoids fragile pixel-based positioning hacks.
- Works naturally with responsive typography systems.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .row {
        display: flex;
        align-items: baseline;
        gap: 1rem;
        border: 1px solid #ccc;
        padding: 1rem;
      }

      .price {
        font-size: 3rem;
        font-weight: 700;
      }

      .currency {
        font-size: 1rem;
      }

      .note {
        font-size: 0.875rem;
      }
    </style>
  </head>
  <body>
    <div class="row">
      <span class="currency">$</span>
      <span class="price">99</span>
      <span class="note">per month</span>
    </div>
  </body>
</html>
```

Even though the font sizes differ greatly, the text sits on the same baseline, producing a cleaner pricing layout.

---

# Pitfalls

- **Replaced elements** (images, some form controls) may have unexpected baseline behavior because their baseline is defined differently.
- If an item contains no inline text, browsers may fall back to another alignment behavior.
- Baseline alignment only matters when elements actually have baselines to compare.
- Multi-line content can produce results that differ from what designers expect; test with real content.

## Question 2. What is alignment fallback behavior?

## Question 3. What is safe vs unsafe alignment?

## Question 4. What is overflow clip margin?

## Question 5. What is fragmentation break control?

## Question 6. What is vertical writing mode?

## Question 7. What is text-combine-upright?

## Question 8. What is hanging-punctuation?

## Question 9. What is line-break property?

## Question 10. What is word-break vs overflow-wrap?

## Question 11. What is hyphens property?

## Question 12. What is ruby annotation in CSS?

## Question 13. What is ruby-position?

## Question 14. What is logical border properties?

## Question 15. What is text-align-last?

## Question 16. What is scroll-linked animation?

## Question 17. What is animation-timeline?

## Question 18. What is view-timeline?

## Question 19. What is offset-path?

## Question 20. What is offset-distance?
