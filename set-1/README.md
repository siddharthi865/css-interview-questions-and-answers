# Set 1

| #   | Question                                                                                                                                               |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | [What is CSS and why is it used?](#question-1-what-is-css-and-why-is-it-used)                                                                          |
| 2   | [What are the different ways to apply CSS to an HTML document?](#question-2-what-are-the-different-ways-to-apply-css-to-an-html-document)              |
| 3   | [What is the difference between inline, internal, and external CSS?](#question-3-what-is-the-difference-between-inline-internal-and-external-css)      |
| 4   | [What is the CSS box model?](#question-4-what-is-the-css-box-model)                                                                                    |
| 5   | [What is the difference between margin and padding?](#question-5-what-is-the-difference-between-margin-and-padding)                                    |
| 6   | [What is the default value of position in CSS?](#question-6-what-is-the-default-value-of-position-in-css)                                              |
| 7   | [What are CSS selectors?](#question-7-what-are-css-selectors)                                                                                          |
| 8   | [What is the difference between class and id selectors?](#question-8-what-is-the-difference-between-class-and-id-selectors)                            |
| 9   | [What is the universal selector?](#question-9-what-is-the-universal-selector)                                                                          |
| 10  | [What is the difference between display: none and visibility: hidden?](#question-10-what-is-the-difference-between-display-none-and-visibility-hidden) |
| 11  | [What are element selectors?](#question-11-what-are-element-selectors)                                                                                 |
| 12  | [What are attribute selectors?](#question-12-what-are-attribute-selectors)                                                                             |
| 13  | [What is the difference between > and space in selectors?](#question-13-what-is-the-difference-between--and-space-in-selectors)                        |
| 14  | [What is the difference between + and ~ combinators?](#question-14-what-is-the-difference-between--and--combinators)                                   |
| 15  | [What are pseudo-classes?](#question-15-what-are-pseudo-classes)                                                                                       |
| 16  | [What are pseudo-elements?](#question-16-what-are-pseudo-elements)                                                                                     |
| 17  | [What is the difference between :nth-child() and :nth-of-type()?](#question-17-what-is-the-difference-between-nth-child-and-nth-of-type)               |
| 18  | [What does :not() do?](#question-18-what-does-not-do)                                                                                                  |
| 19  | [What is the difference between :first-child and :first-of-type?](#question-19-what-is-the-difference-between-first-child-and-first-of-type)           |
| 20  | [How does CSS specificity work?](#question-20-how-does-css-specificity-work)                                                                           |

## Question 1. What is CSS and why is it used?

Got it — I’ll answer in a senior-level CSS interview format.

---

# Short answer

CSS (Cascading Style Sheets) is a stylesheet language used to describe the presentation of HTML content, including layout, colors, spacing, typography, and responsiveness.

It is used to separate content (HTML) from design, enabling scalable, maintainable, and reusable UI styling across web applications.

---

# Explanation

CSS is a fundamental layer of the web stack alongside HTML and JavaScript:

- **HTML** defines structure (what is on the page)
- **CSS** defines presentation (how it looks)
- **JavaScript** defines behavior (how it interacts)

## Why CSS exists

Before CSS, styling was embedded directly in HTML (`<font>`, inline styles), which led to:

- Poor maintainability
- Repeated code
- Difficult global updates
- No separation of concerns

CSS solves this by introducing a **declarative styling system** that applies rules to elements via selectors.

## Key reasons CSS is used in production systems

### 1. Separation of concerns

UI structure and styling are decoupled, allowing designers and engineers to work independently.

### 2. Reusability & scalability

A single class can style multiple components:

- Promotes design systems
- Enables tokens and theming
- Reduces duplication

### 3. Cascade & specificity model

CSS applies styles based on:

- Importance
- Specificity
- Source order

This allows layered styling (base → theme → component overrides).

### 4. Responsive design

CSS enables layout adaptation via:

- Media queries
- Flexbox
- Grid
- Container queries (modern)

### 5. Performance optimization

CSS is render-blocking but highly optimized by browsers:

- Styles are cached
- Selectors are efficiently matched
- Avoids JS-driven layout calculations

### 6. Accessibility & user preferences

CSS supports:

- `prefers-reduced-motion`
- `prefers-color-scheme`
- High contrast modes

## Modern CSS evolution

Modern CSS is no longer just “styling”:

- Layout systems: Flexbox, Grid
- Dynamic styling: `:has()`, variables (`--tokens`)
- Component-based architecture support
- Design systems integration

---

# Example

A simple semantic layout styled with modern CSS:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CSS Example</title>
    <style>
      :root {
        --primary: #2563eb;
        --spacing: 16px;
        --radius: 8px;
      }

      body {
        margin: 0;
        font-family: system-ui, sans-serif;
        line-height: 1.5;
        background: #f9fafb;
      }

      .card {
        max-width: 400px;
        margin: 40px auto;
        padding: var(--spacing);
        background: white;
        border-radius: var(--radius);
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
      }

      .button {
        background: var(--primary);
        color: white;
        padding: 10px 14px;
        border: none;
        border-radius: var(--radius);
        cursor: pointer;
      }

      .button:hover {
        opacity: 0.9;
      }
    </style>
  </head>
  <body>
    <div class="card">
      <h2>CSS Example</h2>
      <p>CSS controls layout, spacing, and visual design.</p>
      <button class="button">Click me</button>
    </div>
  </body>
</html>
```

---

# Pitfalls

- Overusing specificity leads to “specificity wars” and brittle CSS
- Global scope can cause unintended style leakage without architecture (BEM, CSS Modules, etc.)
- Large CSS files can increase initial render cost if not split or optimized
- Inconsistent naming conventions reduce maintainability in large teams
- Misunderstanding cascade leads to debugging complexity

## Question 2. What are the different ways to apply CSS to an HTML document?

## Question 3. What is the difference between inline, internal, and external CSS?

## Question 4. What is the CSS box model?

## Question 5. What is the difference between margin and padding?

## Question 6. What is the default value of position in CSS?

## Question 7. What are CSS selectors?

## Question 8. What is the difference between class and id selectors?

## Question 9. What is the universal selector?

## Question 10. What is the difference between display: none and visibility: hidden?

## Question 11. What are element selectors?

## Question 12. What are attribute selectors?

## Question 13. What is the difference between > and space in selectors?

## Question 14. What is the difference between + and ~ combinators?

## Question 15. What are pseudo-classes?

## Question 16. What are pseudo-elements?

## Question 17. What is the difference between :nth-child() and :nth-of-type()?

## Question 18. What does :not() do?

## Question 19. What is the difference between :first-child and :first-of-type?

## Question 20. How does CSS specificity work?
