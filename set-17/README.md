# Set 17

| #   | Question                                                                                                 |
| --- | -------------------------------------------------------------------------------------------------------- |
| 1   | [What is multiple background layering?](#question-1-what-is-multiple-background-layering)                |
| 2   | [How does background-blend-mode work?](#question-2-how-does-background-blend-mode-work)                  |
| 3   | [What is background-attachment: local?](#question-3-what-is-background-attachment-local)                 |
| 4   | [What is conic-gradient?](#question-4-what-is-conic-gradient)                                            |
| 5   | [What is repeating-linear-gradient?](#question-5-what-is-repeating-linear-gradient)                      |
| 6   | [What is repeating-radial-gradient?](#question-6-what-is-repeating-radial-gradient)                      |
| 7   | [What is mask-composite?](#question-7-what-is-mask-composite)                                            |
| 8   | [What is mask-mode?](#question-8-what-is-mask-mode)                                                      |
| 9   | [What is clip-rule?](#question-9-what-is-clip-rule)                                                      |
| 10  | [What is fill-rule?](#question-10-what-is-fill-rule)                                                     |
| 11  | [What is user-select?](#question-11-what-is-user-select)                                                 |
| 12  | [What is touch-action?](#question-12-what-is-touch-action)                                               |
| 13  | [What is scrollbar-gutter?](#question-13-what-is-scrollbar-gutter)                                       |
| 14  | [What is inset shorthand?](#question-14-what-is-inset-shorthand)                                         |
| 15  | [What is caret-shape?](#question-15-what-is-caret-shape)                                                 |
| 16  | [How does flexbox resolve flexible lengths?](#question-16-how-does-flexbox-resolve-flexible-lengths)     |
| 17  | [What is flex shrink algorithm?](#question-17-what-is-flex-shrink-algorithm)                             |
| 18  | [How does grid auto-placement algorithm work?](#question-18-how-does-grid-auto-placement-algorithm-work) |
| 19  | [What is implicit track sizing?](#question-19-what-is-implicit-track-sizing)                             |
| 20  | [What is grid dense packing?](#question-20-what-is-grid-dense-packing)                                   |

## Question 1. What is multiple background layering?

# Short answer

**Multiple background layering** is a CSS feature that allows you to apply **multiple background images, gradients, or both** to a single element by separating them with commas in the `background` or `background-image` property. The first background listed is painted on top, and the last one is painted closest to the element's background color.

---

# Explanation

Before multiple backgrounds were introduced, developers often needed extra wrapper elements or pseudo-elements to achieve layered visual effects. With multiple background layering, a single element can have:

- Decorative patterns
- Gradient overlays
- Watermarks
- Texture layers
- Hero image overlays

All stacked together without additional markup.

### How layering works

```css
background-image: layer1, layer2, layer3;
```

Rendering order:

1. `layer1` → topmost
2. `layer2`
3. `layer3` → bottommost

The background color (if specified) sits beneath all background layers.

### Per-layer properties

Properties such as:

- `background-size`
- `background-position`
- `background-repeat`
- `background-attachment`
- `background-origin`
- `background-clip`

can also accept comma-separated values, allowing each layer to have different behavior.

Example:

```css
background-image:
  url(pattern.svg), linear-gradient(to bottom, transparent, rgba(0, 0, 0, 0.6)),
  url(hero.jpg);

background-size:
  100px 100px,
  cover,
  cover;
```

### Common production use cases

#### Gradient overlay on hero images

Improves text readability without extra DOM elements.

```css
background-image:
  linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url(hero.jpg);
```

#### Texture + image

```css
background-image: url(noise.png), url(photo.jpg);
```

#### Design system decorations

Layer subtle patterns or brand gradients over a base image while keeping markup clean.

### Why senior engineers use it

- Reduces unnecessary wrapper elements.
- Keeps decorative styling in CSS.
- Improves maintainability.
- Works well with design systems and theming.
- Avoids extra pseudo-elements when only visual layering is needed.

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .hero {
        min-height: 300px;
        display: grid;
        place-items: center;

        color: white;
        font-size: 2rem;

        background-image:
          linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
          url("https://images.unsplash.com/photo-1500530855697-b586d89ba3ee");

        background-size: cover, cover;
        background-position: center, center;
        background-repeat: no-repeat, no-repeat;
      }
    </style>
  </head>
  <body>
    <section class="hero">Accessible Hero Banner</section>
  </body>
</html>
```

This creates a dark overlay on top of the image, improving text contrast and readability.

---

# Pitfalls

- **Order matters.** The first background is painted on top, which is the opposite of how some developers initially expect it.
- **Large image layers increase memory usage** and can affect rendering performance, especially on mobile devices.
- **Decorative backgrounds are not accessible content.** Important information should not be embedded in background images because screen readers cannot access it.
- When specifying multiple backgrounds, ensure related properties (`background-size`, `background-position`, etc.) have matching comma-separated values or understand how CSS value repetition works.

## Question 2. How does background-blend-mode work?

## Question 3. What is background-attachment: local?

## Question 4. What is conic-gradient?

## Question 5. What is repeating-linear-gradient?

## Question 6. What is repeating-radial-gradient?

## Question 7. What is mask-composite?

## Question 8. What is mask-mode?

## Question 9. What is clip-rule?

## Question 10. What is fill-rule?

## Question 11. What is user-select?

## Question 12. What is touch-action?

## Question 13. What is scrollbar-gutter?

## Question 14. What is inset shorthand?

## Question 15. What is caret-shape?

## Question 16. How does flexbox resolve flexible lengths?

## Question 17. What is flex shrink algorithm?

## Question 18. How does grid auto-placement algorithm work?

## Question 19. What is implicit track sizing?

## Question 20. What is grid dense packing?
