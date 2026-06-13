# Set 11

| #   | Question                                                                                                                                        |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the difference between a CSS rule and a CSS declaration?](#question-1-what-is-the-difference-between-a-css-rule-and-a-css-declaration) |
| 2   | [How does the browser apply multiple CSS files?](#question-2-how-does-the-browser-apply-multiple-css-files)                                     |
| 3   | [What happens if a CSS property is invalid?](#question-3-what-happens-if-a-css-property-is-invalid)                                             |
| 4   | [How do comments work in CSS?](#question-4-how-do-comments-work-in-css)                                                                         |
| 5   | [What is the default display behavior of `<div>` and `<span>`?](#question-5-what-is-the-default-display-behavior-of-div-and-span)               |
| 6   | [What is the difference between height: auto and fixed height?](#question-6-what-is-the-difference-between-height-auto-and-fixed-height)        |
| 7   | [What is max-height used for?](#question-7-what-is-max-height-used-for)                                                                         |
| 8   | [How do you center a block element horizontally without Flexbox?](#question-8-how-do-you-center-a-block-element-horizontally-without-flexbox)   |
| 9   | [What happens when margin values overlap?](#question-9-what-happens-when-margin-values-overlap)                                                 |
| 10  | [What is margin collapsing?](#question-10-what-is-margin-collapsing)                                                                            |
| 11  | [What is font-variant?](#question-11-what-is-font-variant)                                                                                      |
| 12  | [What is letter-spacing?](#question-12-what-is-letter-spacing)                                                                                  |
| 13  | [What is word-spacing?](#question-13-what-is-word-spacing)                                                                                      |
| 14  | [What is white-space property?](#question-14-what-is-white-space-property)                                                                      |
| 15  | [What is the difference between pre, nowrap, and pre-wrap?](#question-15-what-is-the-difference-between-pre-nowrap-and-pre-wrap)                |
| 16  | [What is text-transform?](#question-16-what-is-text-transform)                                                                                  |
| 17  | [What is text-decoration-thickness?](#question-17-what-is-text-decoration-thickness)                                                            |
| 18  | [What is text-shadow?](#question-18-what-is-text-shadow)                                                                                        |
| 19  | [What is direction property?](#question-19-what-is-direction-property)                                                                          |
| 20  | [What is unicode-bidi?](#question-20-what-is-unicode-bidi)                                                                                      |

## Question 1. What is the difference between a CSS rule and a CSS declaration?

# Short answer

A **CSS rule** is the complete statement that tells the browser _what elements to target and what styles to apply_.

A **CSS declaration** is a single property-value pair inside a rule that defines one specific style.

Example:

```css
.button {
  color: white;
  background: blue;
}
```

- **CSS rule:** the entire block (`.button { ... }`)
- **Declarations:** `color: white;` and `background: blue;`

---

# Explanation

CSS is structured hierarchically:

1. **Selector** → identifies which elements should be styled.
2. **Declaration block** → contains one or more declarations.
3. **Declaration** → a property and value pair.

Structure:

```css
selector {
  property: value;
  property: value;
}
```

For example:

```css
.card {
  padding: 1rem;
  border-radius: 0.5rem;
  background: white;
}
```

Breaking it down:

- Selector: `.card`
- Rule: the entire `.card { ... }`
- Declaration block:

```css
{
  padding: 1rem;
  border-radius: 0.5rem;
  background: white;
}
```

- Individual declarations:
  - `padding: 1rem;`
  - `border-radius: 0.5rem;`
  - `background: white;`

From a browser-engine perspective, the CSS parser converts rules into objects containing:

- A selector list
- A collection of declarations

The selector determines **matching**, while declarations determine **computed styles**.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* CSS Rule */
      .alert {
        padding: 1rem; /* Declaration */
        color: white; /* Declaration */
        background: crimson; /* Declaration */
      }
    </style>
  </head>
  <body>
    <div class="alert">Payment failed. Please try again.</div>
  </body>
</html>
```

In this example:

```css
.alert {
  padding: 1rem;
  color: white;
  background: crimson;
}
```

- One CSS rule
- Three CSS declarations

---

# Pitfalls

- **Confusing declaration with declaration block**
  - `color: red;` is a declaration.
  - `{ color: red; background: blue; }` is a declaration block.

- **Forgetting semicolons**
  - The last declaration can technically omit a semicolon, but including it improves maintainability and reduces merge errors.

- **Mixing selectors and declarations**
  - Selectors are not declarations; they are part of the rule structure.

- **Invalid declarations**
  - Browsers ignore invalid property-value pairs while still applying valid declarations in the same rule.

## Question 2. How does the browser apply multiple CSS files?

## Question 3. What happens if a CSS property is invalid?

## Question 4. How do comments work in CSS?

## Question 5. What is the default display behavior of `<div>` and `<span>`?

## Question 6. What is the difference between height: auto and fixed height?

## Question 7. What is max-height used for?

## Question 8. How do you center a block element horizontally without Flexbox?

## Question 9. What happens when margin values overlap?

## Question 10. What is margin collapsing?

## Question 11. What is font-variant?

## Question 12. What is letter-spacing?

## Question 13. What is word-spacing?

## Question 14. What is white-space property?

## Question 15. What is the difference between pre, nowrap, and pre-wrap?

## Question 16. What is text-transform?

## Question 17. What is text-decoration-thickness?

## Question 18. What is text-shadow?

## Question 19. What is direction property?

## Question 20. What is unicode-bidi?
