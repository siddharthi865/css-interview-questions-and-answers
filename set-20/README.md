# Set 20

| #   | Question                                                                                                                         |
| --- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How would you design a token-based design system?](#question-1-how-would-you-design-a-token-based-design-system)                |
| 2   | [How do you prevent global leakage in CSS?](#question-2-how-do-you-prevent-global-leakage-in-css)                                |
| 3   | [How do you handle CSS in micro-frontends?](#question-3-how-do-you-handle-css-in-micro-frontends)                                |
| 4   | [How do you manage CSS across multiple teams?](#question-4-how-do-you-manage-css-across-multiple-teams)                          |
| 5   | [How do you version CSS safely?](#question-5-how-do-you-version-css-safely)                                                      |
| 6   | [What are CSS anti-patterns in large projects?](#question-6-what-are-css-anti-patterns-in-large-projects)                        |
| 7   | [How do you refactor legacy CSS safely?](#question-7-how-do-you-refactor-legacy-css-safely)                                      |
| 8   | [What is CSS dead code detection?](#question-8-what-is-css-dead-code-detection)                                                  |
| 9   | [How do you enforce CSS conventions in CI/CD?](#question-9-how-do-you-enforce-css-conventions-in-cicd)                           |
| 10  | [How do you test CSS visually?](#question-10-how-do-you-test-css-visually)                                                       |
| 11  | [What is quirks mode vs standards mode?](#question-11-what-is-quirks-mode-vs-standards-mode)                                     |
| 12  | [How does DOCTYPE impact CSS?](#question-12-how-does-doctype-impact-css)                                                         |
| 13  | [What is viewport unit bug on mobile browsers?](#question-13-what-is-viewport-unit-bug-on-mobile-browsers)                       |
| 14  | [What is dynamic viewport height (dvh)?](#question-14-what-is-dynamic-viewport-height-dvh)                                       |
| 15  | [What is small viewport height (svh)?](#question-15-what-is-small-viewport-height-svh)                                           |
| 16  | [What is large viewport height (lvh)?](#question-16-what-is-large-viewport-height-lvh)                                           |
| 17  | [What is scroll anchoring?](#question-17-what-is-scroll-anchoring)                                                               |
| 18  | [What is font-display property?](#question-18-what-is-font-display-property)                                                     |
| 19  | [How do web fonts affect CLS?](#question-19-how-do-web-fonts-affect-cls)                                                         |
| 20  | [How would you debug a layout that breaks only in Safari?](#question-20-how-would-you-debug-a-layout-that-breaks-only-in-safari) |

## Question 1. How would you design a token-based design system?

# Short answer

A token-based design system starts with **design tokens as the single source of truth** for visual decisions (colors, spacing, typography, motion, shadows, radii, etc.). Tokens are defined in semantic layers, distributed to platforms (CSS, React Native, iOS, Android), and consumed by components rather than hard-coded values. The architecture typically follows:

**Core/Foundation Tokens → Semantic Tokens → Component Tokens → Components**

This approach improves consistency, theming, accessibility, scalability, and maintainability.

---

# Explanation

## 1. Design token hierarchy

A mature token system usually has multiple layers.

### Foundation (Primitive) Tokens

Raw values that represent the visual language.

```json
{
  "color": {
    "blue-500": "#2563eb",
    "gray-100": "#f3f4f6"
  },
  "spacing": {
    "4": "1rem",
    "8": "2rem"
  }
}
```

These values should rarely be used directly in components.

---

### Semantic Tokens

Map primitives to meaning.

```json
{
  "color": {
    "text-primary": "{color.gray-900}",
    "surface-primary": "{color.white}",
    "action-primary": "{color.blue-500}"
  }
}
```

Benefits:

- Easier theming
- Better accessibility reviews
- Easier redesigns

Instead of changing 500 components, update one token.

---

### Component Tokens

Component-specific mappings.

```json
{
  "button": {
    "primary": {
      "background": "{color.action-primary}",
      "text": "{color.text-on-primary}"
    }
  }
}
```

This allows a Button to evolve independently from global semantics.

---

## 2. Token categories

A complete design system usually includes:

### Color

```json
{
  "color": {
    "text-primary": "#111827",
    "text-secondary": "#6b7280",
    "surface-default": "#ffffff",
    "border-default": "#d1d5db"
  }
}
```

### Typography

```json
{
  "font-size": {
    "sm": "0.875rem",
    "md": "1rem",
    "lg": "1.125rem"
  }
}
```

### Spacing

```json
{
  "space": {
    "xs": "0.25rem",
    "sm": "0.5rem",
    "md": "1rem"
  }
}
```

### Border Radius

```json
{
  "radius": {
    "sm": "4px",
    "md": "8px",
    "lg": "16px"
  }
}
```

### Motion

```json
{
  "duration": {
    "fast": "150ms",
    "normal": "300ms"
  }
}
```

### Shadows

```json
{
  "shadow": {
    "sm": "0 1px 2px rgba(0,0,0,.08)"
  }
}
```

---

## 3. CSS implementation

Modern systems commonly expose tokens as CSS custom properties.

```css
:root {
  --color-text-primary: #111827;
  --color-surface-primary: #ffffff;

  --space-sm: 0.5rem;
  --space-md: 1rem;

  --radius-md: 8px;

  --duration-fast: 150ms;
}
```

Components consume tokens:

```css
.card {
  padding: var(--space-md);
  background: var(--color-surface-primary);
  border-radius: var(--radius-md);
}
```

Components never use:

```css
padding: 16px;
background: #fff;
```

directly.

---

## 4. Theming strategy

Tokens enable themes by changing semantic mappings.

### Light Theme

```css
:root {
  --color-surface-primary: white;
  --color-text-primary: black;
}
```

### Dark Theme

```css
[data-theme="dark"] {
  --color-surface-primary: #111827;
  --color-text-primary: #f9fafb;
}
```

Components remain unchanged.

```css
.card {
  color: var(--color-text-primary);
  background: var(--color-surface-primary);
}
```

This is one of the biggest advantages of semantic tokens.

---

## 5. Accessibility considerations

A senior-level design system should embed accessibility into token creation.

Examples:

### Contrast-safe color pairs

Instead of:

```css
--button-blue: #2563eb;
```

Define:

```css
--button-primary-bg: #2563eb;
--button-primary-text: #ffffff;
```

and validate contrast centrally.

### Motion preferences

```css
:root {
  --motion-duration-fast: 150ms;
}

@media (prefers-reduced-motion: reduce) {
  :root {
    --motion-duration-fast: 0ms;
  }
}
```

### Focus tokens

```css
:root {
  --focus-ring-color: #2563eb;
  --focus-ring-width: 2px;
}
```

Every component shares a consistent focus treatment.

---

## 6. Scaling across platforms

Large organizations often use:

```text
Figma
   ↓
Token Source (JSON)
   ↓
Style Dictionary / Token Pipeline
   ↓
CSS Variables
React Native Tokens
Android XML
iOS Swift
```

The token repository becomes the single source of truth.

Popular tooling:

- Style Dictionary
- Tokens Studio
- Specify
- Figma Variables

---

# Example

A production-style token architecture:

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      :root {
        /* Semantic tokens */
        --color-text-primary: #111827;
        --color-surface-primary: #ffffff;
        --color-action-primary: #2563eb;

        --space-md: 1rem;
        --space-lg: 1.5rem;

        --radius-md: 0.5rem;
      }

      [data-theme="dark"] {
        --color-text-primary: #f9fafb;
        --color-surface-primary: #111827;
        --color-action-primary: #60a5fa;
      }

      .card {
        background: var(--color-surface-primary);
        color: var(--color-text-primary);
        padding: var(--space-lg);
        border-radius: var(--radius-md);
      }

      .button {
        background: var(--color-action-primary);
        color: white;
        border: 0;
        padding: var(--space-md);
        border-radius: var(--radius-md);
      }
    </style>
  </head>
  <body data-theme="dark">
    <div class="card">
      <h2>Token-based card</h2>
      <button class="button">Save</button>
    </div>
  </body>
</html>
```

---

# Pitfalls

- **Skipping semantic tokens** and letting components use primitives directly creates tight coupling and makes theming difficult.
- **Too many tokens** can become unmanageable. Every token should represent a real design decision.
- **Token naming based on appearance** (`blue-500-button`) instead of purpose (`action-primary`) limits future redesigns.
- **Ignoring accessibility validation** can spread contrast failures across the entire product.
- **Using fixed pixel values everywhere** reduces scalability for responsive and user-adjustable interfaces.
- **Not versioning tokens** can cause breaking visual changes across applications.

## Question 2. How do you prevent global leakage in CSS?

## Question 3. How do you handle CSS in micro-frontends?

## Question 4. How do you manage CSS across multiple teams?

## Question 5. How do you version CSS safely?

## Question 6. What are CSS anti-patterns in large projects?

## Question 7. How do you refactor legacy CSS safely?

## Question 8. What is CSS dead code detection?

## Question 9. How do you enforce CSS conventions in CI/CD?

## Question 10. How do you test CSS visually?

## Question 11. What is quirks mode vs standards mode?

## Question 12. How does DOCTYPE impact CSS?

## Question 13. What is viewport unit bug on mobile browsers?

## Question 14. What is dynamic viewport height (dvh)?

## Question 15. What is small viewport height (svh)?

## Question 16. What is large viewport height (lvh)?

## Question 17. What is scroll anchoring?

## Question 18. What is font-display property?

## Question 19. How do web fonts affect CLS?

## Question 20. How would you debug a layout that breaks only in Safari?
