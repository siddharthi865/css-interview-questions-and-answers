# Set 12

| #   | Question                                                                                                                         |
| --- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is opacity?](#question-1-what-is-opacity)                                                                                  |
| 2   | [How is rgba() different from opacity?](#question-2-how-is-rgba-different-from-opacity)                                          |
| 3   | [What is cursor property?](#question-3-what-is-cursor-property)                                                                  |
| 4   | [What is caret-color?](#question-4-what-is-caret-color)                                                                          |
| 5   | [What is resize property?](#question-5-what-is-resize-property)                                                                  |
| 6   | [What is pointer-events?](#question-6-what-is-pointer-events)                                                                    |
| 7   | [What is visibility: collapse?](#question-7-what-is-visibility-collapse)                                                         |
| 8   | [What is isolation property?](#question-8-what-is-isolation-property)                                                            |
| 9   | [What is accent-color?](#question-9-what-is-accent-color)                                                                        |
| 10  | [What is scrollbar-width?](#question-10-what-is-scrollbar-width)                                                                 |
| 11  | [What is content property used for?](#question-11-what-is-content-property-used-for)                                             |
| 12  | [How do you insert icons using CSS?](#question-12-how-do-you-insert-icons-using-css)                                             |
| 13  | [What is ::selection?](#question-13-what-is-selection)                                                                           |
| 14  | [What is ::marker?](#question-14-what-is-marker)                                                                                 |
| 15  | [What is ::file-selector-button?](#question-15-what-is-file-selector-button)                                                     |
| 16  | [How do you vertically center using absolute positioning?](#question-16-how-do-you-vertically-center-using-absolute-positioning) |
| 17  | [What happens when both left and right are defined?](#question-17-what-happens-when-both-left-and-right-are-defined)             |
| 18  | [What is shrink-to-fit behavior?](#question-18-what-is-shrink-to-fit-behavior)                                                   |
| 19  | [What is containing block?](#question-19-what-is-containing-block)                                                               |
| 20  | [What is replaced element?](#question-20-what-is-replaced-element)                                                               |

## Question 1. What is opacity?

# Short answer

`opacity` is a CSS property that controls the transparency of an entire element, including its content and descendants. It accepts values from `0` (fully transparent) to `1` (fully opaque).

```css
.element {
  opacity: 0.5;
}
```

---

# Explanation

The `opacity` property determines how visible an element is when the browser paints it.

- `opacity: 1` → fully visible (default)
- `opacity: 0` → completely transparent but still exists in the document flow
- Values between `0` and `1` create varying levels of transparency

Example:

```css
.card {
  opacity: 0.7;
}
```

The entire card—including text, images, icons, borders, and child elements—will be rendered at 70% opacity.

### Important distinction: `opacity` vs `rgba()` / `hsl()` alpha

Using `opacity` affects the entire element tree:

```css
.modal {
  opacity: 0.5;
}
```

Everything inside the modal becomes semi-transparent.

If you only want the background to be transparent while keeping text fully visible, use an alpha color:

```css
.modal {
  background: rgb(0 0 0 / 50%);
}
```

This is generally preferred for overlays and UI components.

### Rendering and interaction behavior

An element with:

```css
opacity: 0;
```

- Is invisible
- Still occupies layout space
- Still receives pointer events by default
- Can still receive keyboard focus

For truly hiding an element, consider:

```css
display: none;
```

or

```css
visibility: hidden;
```

depending on the use case.

### Animations

`opacity` is commonly animated because it creates smooth fade effects and is generally efficient for browsers to render.

```css
.toast {
  transition: opacity 200ms ease;
}
```

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .card {
        inline-size: 250px;
        padding: 1rem;
        border: 1px solid #ccc;
        border-radius: 8px;
        transition: opacity 200ms ease;
      }

      .card:hover {
        opacity: 0.7;
      }
    </style>
  </head>
  <body>
    <div class="card">
      <h3>Notification</h3>
      <p>Hover over this card to reduce its opacity.</p>
    </div>
  </body>
</html>
```

This creates a simple fade effect on hover.

---

# Pitfalls

- **Affects all children:** Text, icons, and images become transparent too.
- **Invisible ≠ removed:** `opacity: 0` elements can still be clicked and focused.
- **Accessibility concerns:** Lowering opacity too much can reduce text contrast and readability.
- **Stacking context:** Any element with `opacity` less than `1` creates a new stacking context, which can affect z-index behavior.

## Question 2. How is rgba() different from opacity?

## Question 3. What is cursor property?

## Question 4. What is caret-color?

## Question 5. What is resize property?

## Question 6. What is pointer-events?

## Question 7. What is visibility: collapse?

## Question 8. What is isolation property?

## Question 9. What is accent-color?

## Question 10. What is scrollbar-width?

## Question 11. What is content property used for?

## Question 12. How do you insert icons using CSS?

## Question 13. What is ::selection?

## Question 14. What is ::marker?

## Question 15. What is ::file-selector-button?

## Question 16. How do you vertically center using absolute positioning?

## Question 17. What happens when both left and right are defined?

## Question 18. What is shrink-to-fit behavior?

## Question 19. What is containing block?

## Question 20. What is replaced element?
