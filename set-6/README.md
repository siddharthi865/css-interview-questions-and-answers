# Set 6

| #   | Question                                                                                                                                  |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is a CSS declaration block?](#question-1-what-is-a-css-declaration-block)                                                           |
| 2   | [What is the difference between a property and a value in CSS?](#question-2-what-is-the-difference-between-a-property-and-a-value-in-css) |
| 3   | [What is a shorthand property? Give examples](#question-3-what-is-a-shorthand-property-give-examples)                                     |
| 4   | [What happens if two CSS rules target the same element?](#question-4-what-happens-if-two-css-rules-target-the-same-element)               |
| 5   | [What is the difference between initial, inherit, and unset?](#question-5-what-is-the-difference-between-initial-inherit-and-unset)       |
| 6   | [What does all: unset do?](#question-6-what-does-all-unset-do)                                                                            |
| 7   | [What are vendor prefixes?](#question-7-what-are-vendor-prefixes)                                                                         |
| 8   | [What is the default box-sizing value?](#question-8-what-is-the-default-box-sizing-value)                                                 |
| 9   | [What does overflow: hidden do?](#question-9-what-does-overflow-hidden-do)                                                                |
| 10  | [What is the difference between overflow: auto and scroll?](#question-10-what-is-the-difference-between-overflow-auto-and-scroll)         |
| 11  | [What is background-size?](#question-11-what-is-background-size)                                                                          |
| 12  | [What is the difference between cover and contain?](#question-12-what-is-the-difference-between-cover-and-contain)                        |
| 13  | [What is background-position?](#question-13-what-is-background-position)                                                                  |
| 14  | [What is background-clip?](#question-14-what-is-background-clip)                                                                          |
| 15  | [What is background-origin?](#question-15-what-is-background-origin)                                                                      |
| 16  | [What is border-radius?](#question-16-what-is-border-radius)                                                                              |
| 17  | [How do you create a circular div?](#question-17-how-do-you-create-a-circular-div)                                                        |
| 18  | [What is border-image?](#question-18-what-is-border-image)                                                                                |
| 19  | [What is the difference between outline and border?](#question-19-what-is-the-difference-between-outline-and-border)                      |
| 20  | [What is box-shadow?](#question-20-what-is-box-shadow)                                                                                    |

## Question 1. What is a CSS declaration block?

## Short answer

A **CSS declaration block** is the section inside curly braces `{}` that contains one or more CSS declarations (property–value pairs) applied to a selector.

---

## Explanation

A CSS rule is composed of two main parts:

- **Selector** → targets HTML elements (e.g., `.card`, `h1`, `#header`)
- **Declaration block** → defines _what styles to apply_ to those elements

A declaration block looks like this:

```css
selector {
  property: value;
  property: value;
}
```

Each **declaration** inside the block consists of:

- **Property** (e.g., `color`, `margin`, `display`)
- **Value** (e.g., `red`, `16px`, `flex`)

### Senior-level perspective

The declaration block is not just syntax—it’s the **atomic unit of styling instructions** that the browser parses into computed style rules during the CSS cascade process.

Key things happening inside a declaration block:

- Participates in the **cascade (specificity, origin, importance)**
- Values are resolved into the **computed style tree**
- Can include **fallbacks**, custom properties, and functions (`var()`, `calc()`)
- Is evaluated per element during style recalculation (performance-sensitive in large DOMs)

From a performance standpoint:

- Large or deeply nested rules increase style recalculation cost
- Repeated or redundant declarations increase memory and compute overhead in style resolution

---

## Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .card {
        background-color: white;
        border: 1px solid #ddd;
        padding: 16px;
        border-radius: 8px;
        display: flex;
        gap: 12px;
      }
    </style>
  </head>
  <body>
    <div class="card">
      <p>CSS Declaration Block Example</p>
    </div>
  </body>
</html>
```

In this example:

```css
.card {
  background-color: white;
  border: 1px solid #ddd;
  padding: 16px;
  border-radius: 8px;
  display: flex;
  gap: 12px;
}
```

Everything inside `{ ... }` is the **declaration block**.

---

## Pitfalls

- ❌ Missing semicolons can break parsing in some cases (especially before new declarations or in minified CSS)
- ❌ Invalid property names are ignored silently by the browser
- ❌ Overloading a block with too many properties can reduce maintainability
- ❌ Repeated declarations across rules increase specificity conflicts and debugging complexity
- ❌ Misunderstanding cascade vs declaration block scope (styles can be overridden elsewhere)

## Question 2. What is the difference between a property and a value in CSS?

## Question 3. What is a shorthand property? Give examples

## Question 4. What happens if two CSS rules target the same element?

## Question 5. What is the difference between initial, inherit, and unset?

## Question 6. What does all: unset do?

## Question 7. What are vendor prefixes?

## Question 8. What is the default box-sizing value?

## Question 9. What does overflow: hidden do?

## Question 10. What is the difference between overflow: auto and scroll?

## Question 11. What is background-size?

## Question 12. What is the difference between cover and contain?

## Question 13. What is background-position?

## Question 14. What is background-clip?

## Question 15. What is background-origin?

## Question 16. What is border-radius?

## Question 17. How do you create a circular div?

## Question 18. What is border-image?

## Question 19. What is the difference between outline and border?

## Question 20. What is box-shadow?
