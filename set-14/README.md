# Set 14

| #   | Question                                                                                     |
| --- | -------------------------------------------------------------------------------------------- |
| 1   | [What is scroll-snap-align?](#question-1-what-is-scroll-snap-align)                          |
| 2   | [What is @property rule?](#question-2-what-is-property-rule)                                 |
| 3   | [What is counter-reset?](#question-3-what-is-counter-reset)                                  |
| 4   | [What is counter-increment?](#question-4-what-is-counter-increment)                          |
| 5   | [How do CSS counters work?](#question-5-how-do-css-counters-work)                            |
| 6   | [What is translateZ()?](#question-6-what-is-translatez)                                      |
| 7   | [What is backface-visibility?](#question-7-what-is-backface-visibility)                      |
| 8   | [What is transform-style: preserve-3d?](#question-8-what-is-transform-style-preserve-3d)     |
| 9   | [What is rotate3d()?](#question-9-what-is-rotate3d)                                          |
| 10  | [What is matrix() transform?](#question-10-what-is-matrix-transform)                         |
| 11  | [What is formatting context?](#question-11-what-is-formatting-context)                       |
| 12  | [What is inline-block whitespace issue?](#question-12-what-is-inline-block-whitespace-issue) |
| 13  | [How does display: contents work?](#question-13-how-does-display-contents-work)              |
| 14  | [What is layout containment?](#question-14-what-is-layout-containment)                       |
| 15  | [What is paint containment?](#question-15-what-is-paint-containment)                         |
| 16  | [What is size containment?](#question-16-what-is-size-containment)                           |
| 17  | [What is style containment?](#question-17-what-is-style-containment)                         |
| 18  | [What is fragmentation context?](#question-18-what-is-fragmentation-context)                 |
| 19  | [What is writing-mode?](#question-19-what-is-writing-mode)                                   |
| 20  | [What is text-orientation?](#question-20-what-is-text-orientation)                           |

## Question 1. What is scroll-snap-align?

# Short answer

`scroll-snap-align` defines **where an element should snap within a scroll container** when CSS Scroll Snap is enabled. It specifies the alignment point of a snap target relative to the scroll container's snapport (viewport).

Common values:

- `start` – snap the element's start edge to the container's start edge.
- `center` – snap the element to the center.
- `end` – snap the element's end edge to the container's end edge.
- `none` – element is not a snap target.

---

# Explanation

`scroll-snap-align` is used on **child elements** inside a scroll container that has `scroll-snap-type` enabled.

Think of scroll snapping as a carousel or paginated scrolling experience:

1. The parent container declares how snapping should behave using `scroll-snap-type`.
2. Child elements declare **where they want to snap** using `scroll-snap-align`.
3. When the user scrolls, the browser automatically adjusts the final scroll position to align the nearest snap point.

Example relationship:

```css
.container {
  scroll-snap-type: x mandatory;
}

.slide {
  scroll-snap-align: start;
}
```

When scrolling stops, each slide's left edge aligns with the container's left edge.

### Axis-specific alignment

You can provide one or two values:

```css
scroll-snap-align: center;
```

Applies to both axes.

```css
scroll-snap-align: start center;
```

- Block axis: `start`
- Inline axis: `center`

This is useful in two-dimensional scrolling layouts.

### Typical use cases

- Image carousels
- Product galleries
- Full-screen section scrolling
- Horizontal card scrollers
- Mobile onboarding flows

### Why it's useful

Compared to JavaScript-based carousels, CSS Scroll Snap:

- Requires less code
- Uses browser-native scrolling behavior
- Works well with touch devices
- Usually provides better performance and accessibility

---

# Example

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .carousel {
        display: flex;
        gap: 1rem;
        overflow-x: auto;
        scroll-snap-type: x mandatory;

        width: 400px;
        border: 2px solid #ccc;
      }

      .card {
        flex: 0 0 100%;
        height: 200px;

        display: grid;
        place-items: center;

        font-size: 2rem;
        background: #f3f4f6;

        scroll-snap-align: center;
      }
    </style>
  </head>
  <body>
    <div class="carousel">
      <div class="card">1</div>
      <div class="card">2</div>
      <div class="card">3</div>
    </div>
  </body>
</html>
```

Each card snaps to the center of the scrolling viewport when scrolling stops.

---

# Pitfalls

- **`scroll-snap-align` does nothing without `scroll-snap-type`** on an ancestor scroll container.
- `mandatory` snapping can feel restrictive if content is larger than the viewport; consider `proximity` for a softer experience.
- Fixed headers often require `scroll-padding-top` to prevent snapped content from being hidden.
- Older browsers had partial implementations; modern browsers (Chrome, Firefox, Safari, Edge) have solid support.

Example with a sticky header:

```css
.page {
  scroll-snap-type: y mandatory;
  scroll-padding-top: 64px;
}
```

## Question 2. What is @property rule?

## Question 3. What is counter-reset?

## Question 4. What is counter-increment?

## Question 5. How do CSS counters work?

## Question 6. What is translateZ()?

## Question 7. What is backface-visibility?

## Question 8. What is transform-style: preserve-3d?

## Question 9. What is rotate3d()?

## Question 10. What is matrix() transform?

## Question 11. What is formatting context?

## Question 12. What is inline-block whitespace issue?

## Question 13. How does display: contents work?

## Question 14. What is layout containment?

## Question 15. What is paint containment?

## Question 16. What is size containment?

## Question 17. What is style containment?

## Question 18. What is fragmentation context?

## Question 19. What is writing-mode?

## Question 20. What is text-orientation?
