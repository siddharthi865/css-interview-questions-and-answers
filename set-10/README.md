# Set 10

| #   | Question                                                                                                                                                                                     |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How does browser rendering pipeline work?](#question-1-how-does-browser-rendering-pipeline-work)                                                                                            |
| 2   | [What triggers layout vs paint vs composite?](#question-2-what-triggers-layout-vs-paint-vs-composite)                                                                                        |
| 3   | [What is GPU acceleration in CSS?](#question-3-what-is-gpu-acceleration-in-css)                                                                                                              |
| 4   | [Why are transforms more performant than top/left?](#question-4-why-are-transforms-more-performant-than-topleft)                                                                             |
| 5   | [What is layout thrashing?](#question-5-what-is-layout-thrashing)                                                                                                                            |
| 6   | [What is content-visibility?](#question-6-what-is-content-visibility)                                                                                                                        |
| 7   | [What is contain property?](#question-7-what-is-contain-property)                                                                                                                            |
| 8   | [What is will-change used for?](#question-8-what-is-will-change-used-for)                                                                                                                    |
| 9   | [What are compositing layers?](#question-9-what-are-compositing-layers)                                                                                                                      |
| 10  | [How does CSSOM differ from DOM?](#question-10-how-does-cssom-differ-from-dom)                                                                                                               |
| 11  | [What is subpixel rendering?](#question-11-what-is-subpixel-rendering)                                                                                                                       |
| 12  | [What is the difference between opacity: 0 and visibility: hidden in accessibility?](#question-12-what-is-the-difference-between-opacity-0-and-visibility-hidden-in-accessibility)           |
| 13  | [What is forced reflow?](#question-13-what-is-forced-reflow)                                                                                                                                 |
| 14  | [What is the difference between inline formatting context and block formatting context?](#question-14-what-is-the-difference-between-inline-formatting-context-and-block-formatting-context) |
| 15  | [What is BFC (Block Formatting Context)?](#question-15-what-is-bfc-block-formatting-context)                                                                                                 |
| 16  | [What is :focus-visible?](#question-16-what-is-focus-visible)                                                                                                                                |
| 17  | [What is container query units?](#question-17-what-is-container-query-units)                                                                                                                 |
| 18  | [What is scroll snap?](#question-18-what-is-scroll-snap)                                                                                                                                     |
| 19  | [What is anchor positioning in CSS?](#question-19-what-is-anchor-positioning-in-css)                                                                                                         |
| 20  | [What future CSS features are you most excited about and why?](#question-20-what-future-css-features-are-you-most-excited-about-and-why)                                                     |

## Question 1. How does browser rendering pipeline work?

# Short answer

The browser rendering pipeline is the sequence of steps a browser follows to convert HTML, CSS, and JavaScript into pixels on the screen:

**Parse HTML → Build DOM → Parse CSS → Build CSSOM → Create Render Tree → Layout (Reflow) → Paint → Composite**

JavaScript can interrupt or trigger parts of this pipeline by modifying the DOM, CSS, or layout-related properties.

---

# Explanation

Understanding the rendering pipeline is important because most frontend performance issues come from forcing the browser to repeat expensive stages like **layout** and **paint**.

## 1. HTML Parsing → DOM Construction

The browser downloads HTML and converts it into a **DOM (Document Object Model)** tree.

```html
<body>
  <h1>Hello</h1>
  <p>World</p>
</body>
```

Becomes:

```text
body
 ├─ h1
 └─ p
```

The DOM represents the document structure and can be modified by JavaScript.

---

## 2. CSS Parsing → CSSOM Construction

The browser parses CSS and creates the **CSS Object Model (CSSOM)**.

```css
h1 {
  color: blue;
}
```

Becomes an internal tree of CSS rules.

Unlike HTML, CSS is render-blocking because the browser needs styles before it can determine how elements should appear.

---

## 3. Render Tree Creation

The browser combines the **DOM** and **CSSOM** to build a **Render Tree**.

The Render Tree contains only visible elements.

Example:

```html
<div>Hello</div>
<div style="display:none">Hidden</div>
```

The second element exists in the DOM but is excluded from the Render Tree because it is not rendered.

```text
Render Tree
 └─ div ("Hello")
```

---

## 4. Layout (Reflow)

The browser calculates:

- Element size
- Position
- Margins
- Padding
- Available space

This process is called:

- **Layout** (modern term)
- **Reflow** (older term)

Example:

```css
.container {
  width: 500px;
}
```

The browser computes exact pixel values for every visible element.

Layout is relatively expensive because changing one element can affect many others.

---

## 5. Paint

The browser converts visual information into pixels.

It paints:

- Text
- Colors
- Borders
- Shadows
- Images

Example:

```css
.box {
  background: red;
  border: 1px solid black;
}
```

The browser determines what pixels should appear on the screen.

---

## 6. Compositing

Modern browsers use layers.

The compositor combines painted layers and sends them to the GPU for display.

Properties like:

```css
transform
opacity
filter
```

can often be updated in the compositor stage without triggering layout.

This is why animations using `transform` and `opacity` are generally much smoother.

---

## How JavaScript Affects the Pipeline

JavaScript can trigger different stages depending on what changes.

### DOM Change

```javascript
element.appendChild(newDiv);
```

May require:

```text
DOM → Render Tree → Layout → Paint → Composite
```

---

### Style Change

```javascript
element.style.color = "red";
```

Usually triggers:

```text
Style Recalculation → Paint → Composite
```

No layout needed because size doesn't change.

---

### Layout Change

```javascript
element.style.width = "300px";
```

Triggers:

```text
Style Recalculation → Layout → Paint → Composite
```

Because dimensions changed.

---

### Transform Change

```javascript
element.style.transform = "translateX(100px)";
```

Often only triggers:

```text
Composite
```

Which is much cheaper.

---

## Rendering Pipeline Visualization

```text
HTML
  │
  ▼
DOM
  │
  ├──────────┐
  │          │
CSS      CSSOM
  │          │
  └────┬─────┘
       ▼
  Render Tree
       ▼
     Layout
       ▼
      Paint
       ▼
   Composite
       ▼
     Screen
```

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .card {
        width: 200px;
        height: 100px;
        background: steelblue;
        transition: transform 300ms ease;
      }

      .card:hover {
        transform: translateY(-10px);
      }
    </style>
  </head>
  <body>
    <div class="card"></div>
  </body>
</html>
```

Why this is performant:

- `transform` avoids layout recalculation.
- No element dimensions change.
- Browser can often handle animation in the compositor layer.
- Produces smoother 60fps animations.

---

# Pitfalls

- **Layout Thrashing:** Reading layout values (`offsetWidth`) immediately after writing styles can force synchronous layout calculations.
- **Animating layout properties:** Animating `width`, `height`, `top`, or `left` often causes repeated layout and paint operations.
- **Large paint areas:** Heavy shadows, filters, and large gradients can increase paint cost.
- **Excessive DOM size:** Large DOM trees increase style calculation and layout time.

## Question 2. What triggers layout vs paint vs composite?

## Question 3. What is GPU acceleration in CSS?

## Question 4. Why are transforms more performant than top/left?

## Question 5. What is layout thrashing?

## Question 6. What is content-visibility?

## Question 7. What is contain property?

## Question 8. What is will-change used for?

## Question 9. What are compositing layers?

## Question 10. How does CSSOM differ from DOM?

## Question 11. What is subpixel rendering?

## Question 12. What is the difference between opacity: 0 and visibility: hidden in accessibility?

## Question 13. What is forced reflow?

## Question 14. What is the difference between inline formatting context and block formatting context?

## Question 15. What is BFC (Block Formatting Context)?

## Question 16. What is :focus-visible?

## Question 17. What is container query units?

## Question 18. What is scroll snap?

## Question 19. What is anchor positioning in CSS?

## Question 20. What future CSS features are you most excited about and why?
