# Set 16

| #   | Question                                                                                                                                                      |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is the difference between author, user, and user-agent stylesheets?](#question-1-what-is-the-difference-between-author-user-and-user-agent-stylesheets) |
| 2   | [How does the cascade order work when origin and importance differ?](#question-2-how-does-the-cascade-order-work-when-origin-and-importance-differ)           |
| 3   | [What is the difference between computed value and used value?](#question-3-what-is-the-difference-between-computed-value-and-used-value)                     |
| 4   | [What is a specified value in CSS?](#question-4-what-is-a-specified-value-in-css)                                                                             |
| 5   | [What does revert keyword do?](#question-5-what-does-revert-keyword-do)                                                                                       |
| 6   | [What does revert-layer do?](#question-6-what-does-revert-layer-do)                                                                                           |
| 7   | [What is the difference between currentColor and a hardcoded color?](#question-7-what-is-the-difference-between-currentcolor-and-a-hardcoded-color)           |
| 8   | [What is the initial containing block?](#question-8-what-is-the-initial-containing-block)                                                                     |
| 9   | [What happens if width exceeds parent container?](#question-9-what-happens-if-width-exceeds-parent-container)                                                 |
| 10  | [What is overflow-x vs overflow-y?](#question-10-what-is-overflow-x-vs-overflow-y)                                                                            |
| 11  | [How does percentage height behave when parent has no defined height?](#question-11-how-does-percentage-height-behave-when-parent-has-no-defined-height)      |
| 12  | [What is the difference between min-height: 100% and 100vh?](#question-12-what-is-the-difference-between-min-height-100-and-100vh)                            |
| 13  | [What is box-decoration-break?](#question-13-what-is-box-decoration-break)                                                                                    |
| 14  | [How does border-spacing work?](#question-14-how-does-border-spacing-work)                                                                                    |
| 15  | [What is outline-offset?](#question-15-what-is-outline-offset)                                                                                                |
| 16  | [What is image-rendering property?](#question-16-what-is-image-rendering-property)                                                                            |
| 17  | [What is object-view-box?](#question-17-what-is-object-view-box)                                                                                              |
| 18  | [What is field-sizing?](#question-18-what-is-field-sizing)                                                                                                    |
| 19  | [What is max-inline-size?](#question-19-what-is-max-inline-size)                                                                                              |
| 20  | [What is min-block-size?](#question-20-what-is-min-block-size)                                                                                                |

## Question 1. What is the difference between author, user, and user-agent stylesheets?

# Short answer

CSS styles can come from three primary origins:

- **User-Agent stylesheets**: Default styles provided by the browser (e.g., `<h1>` is bold, `<ul>` has bullets).
- **Author stylesheets**: Styles written by the website/application developer.
- **User stylesheets**: Styles defined by the end user to customize browsing (often for accessibility needs, such as larger fonts or high contrast).

The CSS cascade determines which origin wins when multiple styles target the same element.

---

# Explanation

The CSS Cascade considers both **origin** and **importance** when deciding which style is applied.

## 1. User-Agent Stylesheet

Every browser ships with a built-in stylesheet that gives HTML elements default styling.

Example defaults:

```css
h1 {
  display: block;
  font-size: 2em;
  font-weight: bold;
}

ul {
  padding-left: 40px;
  list-style-type: disc;
}
```

Without these defaults, a page containing only HTML would appear mostly unstyled.

Typical examples:

- Heading sizes
- List bullets
- Form control appearance
- Default margins on paragraphs and headings

This is why CSS resets or normalizers exist—they reduce inconsistencies between browser defaults.

---

## 2. Author Stylesheet

These are the styles written by developers.

```css
h1 {
  font-size: 3rem;
  color: navy;
}
```

Author styles are what most developers work with daily:

- External CSS files
- `<style>` blocks
- Inline styles
- CSS-in-JS solutions

The author stylesheet usually overrides browser defaults because it appears later in the cascade.

---

## 3. User Stylesheet

Users may provide their own CSS preferences.

Examples:

- Larger text for low vision users
- Custom color schemes
- High-contrast themes
- Browser extensions that inject CSS

Example:

```css
body {
  font-size: 24px !important;
}
```

Historically browsers exposed direct user stylesheet support. Today it's less common, but accessibility tools, browser settings, extensions, and reader modes often achieve similar effects.

---

## Cascade Order

Ignoring layers and specificity for a moment, the simplified cascade precedence is:

| Origin          | Priority         |
| --------------- | ---------------- |
| User-Agent      | Lowest           |
| User            | Middle           |
| Author          | Higher           |
| Important rules | Special handling |

More precisely, for conflicting declarations:

1. User-Agent normal
2. User normal
3. Author normal
4. Author `!important`
5. User `!important`

A user's `!important` rule is intentionally able to override author styles for accessibility reasons.

Example:

```css
/* Browser */
p {
  color: black;
}

/* Author */
p {
  color: blue;
}

/* User */
p {
  color: red !important;
}
```

Final color:

```css
red
```

because user `!important` has the highest priority.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      /* Author stylesheet */
      button {
        background: royalblue;
        color: white;
        padding: 0.75rem 1rem;
        border: none;
      }
    </style>
  </head>
  <body>
    <button>Submit</button>
  </body>
</html>
```

What happens:

1. Browser (user-agent) gives the button default appearance.
2. Author stylesheet overrides it with custom colors.
3. A user accessibility stylesheet could still override those colors if needed.

---

# Pitfalls

- **Assuming browser defaults are identical**: User-agent styles differ slightly across browsers.
- **Overusing CSS resets**: Aggressive resets can remove useful accessibility defaults.
- **Ignoring user preferences**: Hard-coding colors, font sizes, or disabling zoom can conflict with user needs.
- **Misunderstanding `!important`**: User `!important` rules can override author `!important` declarations.

## Question 2. How does the cascade order work when origin and importance differ?

## Question 3. What is the difference between computed value and used value?

## Question 4. What is a specified value in CSS?

## Question 5. What does revert keyword do?

## Question 6. What does revert-layer do?

## Question 7. What is the difference between currentColor and a hardcoded color?

## Question 8. What is the initial containing block?

## Question 9. What happens if width exceeds parent container?

## Question 10. What is overflow-x vs overflow-y?

## Question 11. How does percentage height behave when parent has no defined height?

## Question 12. What is the difference between min-height: 100% and 100vh?

## Question 13. What is box-decoration-break?

## Question 14. How does border-spacing work?

## Question 15. What is outline-offset?

## Question 16. What is image-rendering property?

## Question 17. What is object-view-box?

## Question 18. What is field-sizing?

## Question 19. What is max-inline-size?

## Question 20. What is min-block-size?
