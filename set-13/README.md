# Set 13

| #   | Question                                                                                                                                                    |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the difference between inline formatting and block formatting?](#question-1-what-is-the-difference-between-inline-formatting-and-block-formatting) |
| 2   | [What is fragmentation in CSS?](#question-2-what-is-fragmentation-in-css)                                                                                   |
| 3   | [What is multi-column layout?](#question-3-what-is-multi-column-layout)                                                                                     |
| 4   | [What is column-count?](#question-4-what-is-column-count)                                                                                                   |
| 5   | [What is column-gap?](#question-5-what-is-column-gap)                                                                                                       |
| 6   | [What is :target pseudo-class?](#question-6-what-is-target-pseudo-class)                                                                                    |
| 7   | [What is :empty?](#question-7-what-is-empty)                                                                                                                |
| 8   | [What is :root?](#question-8-what-is-root)                                                                                                                  |
| 9   | [What is :enabled and :disabled?](#question-9-what-is-enabled-and-disabled)                                                                                 |
| 10  | [What is :checked?](#question-10-what-is-checked)                                                                                                           |
| 11  | [What is :indeterminate?](#question-11-what-is-indeterminate)                                                                                               |
| 12  | [What is :placeholder-shown?](#question-12-what-is-placeholder-shown)                                                                                       |
| 13  | [What is :only-child?](#question-13-what-is-only-child)                                                                                                     |
| 14  | [What is :only-of-type?](#question-14-what-is-only-of-type)                                                                                                 |
| 15  | [What is :nth-last-child()?](#question-15-what-is-nth-last-child)                                                                                           |
| 16  | [What is aspect-ratio use case in responsive images?](#question-16-what-is-aspect-ratio-use-case-in-responsive-images)                                      |
| 17  | [What is scroll-margin?](#question-17-what-is-scroll-margin)                                                                                                |
| 18  | [What is scroll-padding?](#question-18-what-is-scroll-padding)                                                                                              |
| 19  | [What is overscroll-behavior?](#question-19-what-is-overscroll-behavior)                                                                                    |
| 20  | [What is scroll-snap-type?](#question-20-what-is-scroll-snap-type)                                                                                          |

## Question 1. What is the difference between inline formatting and block formatting?

# Short answer

**Block formatting** lays out elements vertically as blocks that typically start on a new line and can expand to fill available inline space (e.g., `<div>`, `<section>`, `<p>`).

**Inline formatting** lays out content within a line of text, flowing horizontally and wrapping across lines as needed (e.g., `<span>`, `<a>`, `<strong>`).

The browser uses different formatting contexts and layout rules for block-level and inline-level content.

# Explanation

Understanding block and inline formatting is fundamental because it affects sizing, positioning, spacing, and how elements participate in layout.

## Block Formatting

Block-level elements participate in a **Block Formatting Context (BFC)** by default.

Characteristics:

- Start on a new line.
- Stack vertically.
- By default, stretch to fill the available width of their containing block (`width: auto`).
- Respect width, height, margin, padding, and border properties.
- Create clear visual sections of a page.

Example elements:

```html
<div>
  <p></p>
  <section>
    <article></article>
  </section>
</div>
```

Layout flow:

```text
+----------------------+
| Block Element 1      |
+----------------------+

+----------------------+
| Block Element 2      |
+----------------------+
```

## Inline Formatting

Inline elements participate in an **Inline Formatting Context (IFC)**.

Characteristics:

- Flow within a line of text.
- Do not start on a new line.
- Only occupy the space required by their content.
- Wrap onto the next line when necessary.
- `width` and `height` generally have no effect on non-replaced inline elements.
- Vertical margins don't affect surrounding layout the same way block margins do.

Example elements:

```html
<span>
  <a>
    <strong> <em></em></strong></a
></span>
```

Layout flow:

```text
This is [span] text with [link] and [strong] content.
```

## Why This Matters

As a senior engineer, it's important to know that:

- Layout bugs often come from misunderstanding formatting contexts.
- Modern layout systems (Flexbox and Grid) change how children participate in layout.
- `display` can change an element's formatting behavior regardless of its semantic HTML element.

Example:

```css
span {
  display: block;
}

div {
  display: inline;
}
```

The semantic meaning remains the same, but the layout behavior changes.

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .container {
        border: 2px solid #333;
        padding: 1rem;
        margin-bottom: 1rem;
      }

      .block {
        display: block;
        background: #e3f2fd;
        padding: 0.5rem;
        margin-block: 0.5rem;
      }

      .inline {
        display: inline;
        background: #fff3cd;
        padding: 0.5rem;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="block">Block 1</div>
      <div class="block">Block 2</div>
    </div>

    <div class="container">
      <span class="inline">Inline 1</span>
      <span class="inline">Inline 2</span>
      <span class="inline">Inline 3</span>
    </div>
  </body>
</html>
```

In the first container, elements stack vertically. In the second, elements flow on the same line.

# Pitfalls

- **Width/height on inline elements:** Regular inline elements ignore explicit `width` and `height`.
- **Vertical margins:** Top and bottom margins on inline elements generally don't affect line layout as expected.
- **Mixing formatting contexts:** Floats, positioning, Flexbox, and Grid introduce different layout behaviors that can override normal block/inline flow.
- **Using `display: inline-block`:** Often confused with inline formatting—it flows inline but supports width, height, and vertical margins like a block.

## Question 2. What is fragmentation in CSS?

## Question 3. What is multi-column layout?

## Question 4. What is column-count?

## Question 5. What is column-gap?

## Question 6. What is :target pseudo-class?

## Question 7. What is :empty?

## Question 8. What is :root?

## Question 9. What is :enabled and :disabled?

## Question 10. What is :checked?

## Question 11. What is :indeterminate?

## Question 12. What is :placeholder-shown?

## Question 13. What is :only-child?

## Question 14. What is :only-of-type?

## Question 15. What is :nth-last-child()?

## Question 16. What is aspect-ratio use case in responsive images?

## Question 17. What is scroll-margin?

## Question 18. What is scroll-padding?

## Question 19. What is overscroll-behavior?

## Question 20. What is scroll-snap-type?
