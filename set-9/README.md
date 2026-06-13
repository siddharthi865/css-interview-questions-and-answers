# Set 9

| #   | Question                                                                                                             |
| --- | -------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is filter property?](#question-1-what-is-filter-property)                                                      |
| 2   | [What is clip-path?](#question-2-what-is-clip-path)                                                                  |
| 3   | [What is mask in CSS?](#question-3-what-is-mask-in-css)                                                              |
| 4   | [What is mix-blend-mode?](#question-4-what-is-mix-blend-mode)                                                        |
| 5   | [What is scroll-behavior?](#question-5-what-is-scroll-behavior)                                                      |
| 6   | [What is @supports rule?](#question-6-what-is-supports-rule)                                                         |
| 7   | [What are feature queries?](#question-7-what-are-feature-queries)                                                    |
| 8   | [What is prefers-color-scheme?](#question-8-what-is-prefers-color-scheme)                                            |
| 9   | [What is prefers-reduced-motion?](#question-9-what-is-prefers-reduced-motion)                                        |
| 10  | [What is logical property margin-inline?](#question-10-what-is-logical-property-margin-inline)                       |
| 11  | [What is ITCSS architecture?](#question-11-what-is-itcss-architecture)                                               |
| 12  | [What is OOCSS?](#question-12-what-is-oocss)                                                                         |
| 13  | [What is SMACSS?](#question-13-what-is-smacss)                                                                       |
| 14  | [What is Atomic CSS?](#question-14-what-is-atomic-css)                                                               |
| 15  | [What are utility-first frameworks?](#question-15-what-are-utility-first-frameworks)                                 |
| 16  | [What are design tokens?](#question-16-what-are-design-tokens)                                                       |
| 17  | [How do you implement dark mode with CSS variables?](#question-17-how-do-you-implement-dark-mode-with-css-variables) |
| 18  | [How do you handle theming in large applications?](#question-18-how-do-you-handle-theming-in-large-applications)     |
| 19  | [What is CSS layering (@layer)?](#question-19-what-is-css-layering-layer)                                            |
| 20  | [How does cascade layers affect specificity?](#question-20-how-does-cascade-layers-affect-specificity)               |

## Question 1. What is filter property?

# Short answer

The **`filter`** property applies graphical effects to an element after it has been rendered, similar to image-editing effects. Common filters include `blur()`, `brightness()`, `contrast()`, `grayscale()`, `sepia()`, `invert()`, `drop-shadow()`, and `hue-rotate()`.

Example:

```css
img {
  filter: grayscale(100%) blur(2px);
}
```

---

# Explanation

The `filter` property allows you to modify the visual appearance of an element without changing the underlying content. It works on images, backgrounds, text, videos, and even entire containers.

Unlike traditional CSS properties that change layout or styling directly, filters are applied as a post-processing step during rendering.

Common filter functions:

| Function        | Purpose                      |
| --------------- | ---------------------------- |
| `blur()`        | Blurs the element            |
| `brightness()`  | Adjusts brightness           |
| `contrast()`    | Adjusts contrast             |
| `grayscale()`   | Converts colors to grayscale |
| `sepia()`       | Applies a sepia tone         |
| `invert()`      | Inverts colors               |
| `opacity()`     | Adjusts transparency         |
| `saturate()`    | Changes color intensity      |
| `hue-rotate()`  | Rotates color hues           |
| `drop-shadow()` | Adds a shadow effect         |

Multiple filters can be chained together:

```css
.card {
  filter: brightness(110%) contrast(120%) saturate(130%);
}
```

### Why use filters?

- Image hover effects without editing assets.
- Dark/light theme image adjustments.
- Disabled or inactive UI states.
- Background blur effects (combined with `backdrop-filter` when needed).
- Visual enhancements in dashboards and media applications.

### `filter` vs `backdrop-filter`

- **`filter`** affects the element itself.
- **`backdrop-filter`** affects content behind the element.

```css
.modal {
  backdrop-filter: blur(10px);
}
```

This creates the popular "glassmorphism" effect.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      :root {
        --radius: 12px;
      }

      .gallery {
        display: flex;
        gap: 1rem;
      }

      .gallery img {
        width: 220px;
        border-radius: var(--radius);
        transition: filter 0.3s ease;
        filter: grayscale(100%);
      }

      .gallery img:hover {
        filter: grayscale(0%) brightness(110%);
      }
    </style>
  </head>
  <body>
    <div class="gallery">
      <img src="https://picsum.photos/id/237/300/200" alt="Dog" />
    </div>
  </body>
</html>
```

When the user hovers over the image, it transitions from grayscale to full color with increased brightness.

---

# Pitfalls

- **Performance considerations:** `blur()` can be expensive, especially with large values or large elements because it may trigger GPU-intensive rendering.
- **Stacking multiple filters:** Chaining many filters can impact animation smoothness on lower-end devices.
- **Accessibility:** Avoid excessive blur or low contrast that reduces readability.
- **`drop-shadow()` differs from `box-shadow`:** It follows the actual visible shape (including transparent PNGs), while `box-shadow` follows the element's rectangular box.

## Question 2. What is clip-path?

## Question 3. What is mask in CSS?

## Question 4. What is mix-blend-mode?

## Question 5. What is scroll-behavior?

## Question 6. What is @supports rule?

## Question 7. What are feature queries?

## Question 8. What is prefers-color-scheme?

## Question 9. What is prefers-reduced-motion?

## Question 10. What is logical property margin-inline?

## Question 11. What is ITCSS architecture?

## Question 12. What is OOCSS?

## Question 13. What is SMACSS?

## Question 14. What is Atomic CSS?

## Question 15. What are utility-first frameworks?

## Question 16. What are design tokens?

## Question 17. How do you implement dark mode with CSS variables?

## Question 18. How do you handle theming in large applications?

## Question 19. What is CSS layering (@layer)?

## Question 20. How does cascade layers affect specificity?
