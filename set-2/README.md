# Set 2

| #   | Question                                                                                                                                       |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What are different ways to define colors in CSS?](#question-1-what-are-different-ways-to-define-colors-in-css)                                |
| 2   | [What is the difference between px, em, and rem?](#question-2-what-is-the-difference-between-px-em-and-rem)                                    |
| 3   | [What is the difference between % and vw/vh?](#question-3-what-is-the-difference-between-and-vwvh)                                             |
| 4   | [What are relative and absolute units?](#question-4-what-are-relative-and-absolute-units)                                                      |
| 5   | [What is calc() in CSS?](#question-5-what-is-calc-in-css)                                                                                      |
| 6   | [How do you apply custom fonts in CSS?](#question-6-how-do-you-apply-custom-fonts-in-css)                                                      |
| 7   | [What is the difference between font-weight values?](#question-7-what-is-the-difference-between-font-weight-values)                            |
| 8   | [What is line-height?](#question-8-what-is-line-height)                                                                                        |
| 9   | [What is the difference between text-align and vertical-align?](#question-9-what-is-the-difference-between-text-align-and-vertical-align)      |
| 10  | [How do you truncate text with ellipsis?](#question-10-how-do-you-truncate-text-with-ellipsis)                                                 |
| 11  | [What are different values of the display property?](#question-11-what-are-different-values-of-the-display-property)                           |
| 12  | [What is the difference between block, inline, and inline-block?](#question-12-what-is-the-difference-between-block-inline-and-inline-block)   |
| 13  | [What is position: relative?](#question-13-what-is-position-relative)                                                                          |
| 14  | [What is position: absolute?](#question-14-what-is-position-absolute)                                                                          |
| 15  | [What is the difference between absolute and fixed positioning?](#question-15-what-is-the-difference-between-absolute-and-fixed-positioning)   |
| 16  | [What is Flexbox?](#question-16-what-is-flexbox)                                                                                               |
| 17  | [What is the difference between justify-content and align-items?](#question-17-what-is-the-difference-between-justify-content-and-align-items) |
| 18  | [What does flex: 1 mean?](#question-18-what-does-flex-1-mean)                                                                                  |
| 19  | [What is the difference between align-items and align-content?](#question-19-what-is-the-difference-between-align-items-and-align-content)     |
| 20  | [How does flex-wrap work?](#question-20-how-does-flex-wrap-work)                                                                               |

## Question 1. What are different ways to define colors in CSS?

## Short answer

CSS colors can be defined using named colors, HEX, RGB/RGBA, HSL/HSLA, modern functional notations like `lab()`, `lch()`, `oklch()`, and special keywords like `transparent`, `currentColor`.

---

## Explanation

CSS supports multiple color formats, each with different strengths depending on readability, precision, and design system needs.

### 1. Named colors

Predefined keywords like:

```css
color: red;
color: rebeccapurple;
```

- Easy to use
- Limited palette and not suitable for design systems

---

### 2. Hexadecimal (`#RRGGBB`, `#RGB`, `#RRGGBBAA`)

```css
color: #ff0000;
color: #f00;
color: #ff000080; /* alpha */
```

- Compact and widely used
- Good for static design tokens
- Harder to reason about perceptually (brightness/hue not intuitive)

---

### 3. RGB / RGBA

```css
color: rgb(255, 0, 0);
color: rgba(255, 0, 0, 0.5);
```

- Intuitive for programmatic generation
- Still not perceptually uniform

---

### 4. HSL / HSLA (Hue, Saturation, Lightness)

```css
color: hsl(0 100% 50%);
color: hsla(0 100% 50% / 0.5);
```

- More intuitive for designers (adjust hue/lightness)
- Useful for theming (light/dark variants)
- Still not perceptually uniform in all cases

---

### 5. Modern perceptual color spaces (recommended for design systems)

#### `lab()`

```css
color: lab(62% 80 70);
```

#### `lch()`

```css
color: lch(62% 100 30);
```

#### `oklch()` (modern best practice for UI systems)

```css
color: oklch(70% 0.15 250);
```

- Perceptually uniform (changes in value feel consistent to human vision)
- Excellent for design tokens, theming, gradients
- Better contrast control for accessibility

---

### 6. Special keywords

#### `currentColor`

```css
border: 2px solid currentColor;
color: blue;
```

- Inherits the current text color
- Great for icon systems and reusable components

#### `transparent`

```css
background: transparent;
```

- Equivalent to `rgba(0,0,0,0)`

---

## Example

```html
<div class="card">
  Button variants
  <button class="hex">Hex</button>
  <button class="rgb">RGB</button>
  <button class="hsl">HSL</button>
  <button class="oklch">OKLCH</button>
</div>
```

```css
.card {
  font-family: system-ui;
  padding: 16px;
}

button {
  padding: 8px 12px;
  border: 2px solid currentColor;
  margin-right: 8px;
  cursor: pointer;
}

/* Different color models */
.hex {
  color: #3b82f6;
}

.rgb {
  color: rgb(59, 130, 246);
}

.hsl {
  color: hsl(217 91% 60%);
}

.oklch {
  color: oklch(62% 0.18 250);
}
```

---

## Pitfalls

- **Inconsistent perception in RGB/HSL**: equal numeric changes don’t feel visually equal.
- **Legacy browser support for modern spaces**: `oklch()`, `lab()`, `lch()` may not be fully supported in older browsers.
- **Overusing named colors**: not scalable for design systems.
- **Alpha transparency surprises**: `#RRGGBBAA` vs `rgba()` differences in tooling and debugging.
- **Color contrast accessibility**: some combinations in HSL/RGB may fail WCAG even if they “look fine.”

## Question 2. What is the difference between px, em, and rem?

## Question 3. What is the difference between % and vw/vh?

## Question 4. What are relative and absolute units?

## Question 5. What is calc() in CSS?

## Question 6. How do you apply custom fonts in CSS?

## Question 7. What is the difference between font-weight values?

## Question 8. What is line-height?

## Question 9. What is the difference between text-align and vertical-align?

## Question 10. How do you truncate text with ellipsis?

## Question 11. What are different values of the display property?

## Question 12. What is the difference between block, inline, and inline-block?

## Question 13. What is position: relative?

## Question 14. What is position: absolute?

## Question 15. What is the difference between absolute and fixed positioning?

## Question 16. What is Flexbox?

## Question 17. What is the difference between justify-content and align-items?

## Question 18. What does flex: 1 mean?

## Question 19. What is the difference between align-items and align-content?

## Question 20. How does flex-wrap work?
