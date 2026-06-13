# Set 24

| #   | Question                                                                                                                                                               |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [How do you minimize render-blocking CSS?](#question-1-how-do-you-minimize-render-blocking-css)                                                                        |
| 2   | [How do you lazy-load CSS?](#question-2-how-do-you-lazy-load-css)                                                                                                      |
| 3   | [How do you prevent FOUC (Flash of Unstyled Content)?](#question-3-how-do-you-prevent-fouc-flash-of-unstyled-content)                                                  |
| 4   | [How do you handle CSS in SSR frameworks?](#question-4-how-do-you-handle-css-in-ssr-frameworks)                                                                        |
| 5   | [How do you debug CSS hydration mismatches?](#question-5-how-do-you-debug-css-hydration-mismatches)                                                                    |
| 6   | [How do you design CSS for micro-frontend architecture?](#question-6-how-do-you-design-css-for-micro-frontend-architecture)                                            |
| 7   | [How do you manage shared styles across packages in a monorepo?](#question-7-how-do-you-manage-shared-styles-across-packages-in-a-monorepo)                            |
| 8   | [How do you avoid CSS duplication in large apps?](#question-8-how-do-you-avoid-css-duplication-in-large-apps)                                                          |
| 9   | [How do you audit CSS bundle size?](#question-9-how-do-you-audit-css-bundle-size)                                                                                      |
| 10  | [How do you write future-proof CSS?](#question-10-how-do-you-write-future-proof-css)                                                                                   |
| 11  | [How do you decide between utility classes and semantic classes?](#question-11-how-do-you-decide-between-utility-classes-and-semantic-classes)                         |
| 12  | [How do you manage CSS in a component library?](#question-12-how-do-you-manage-css-in-a-component-library)                                                             |
| 13  | [How do you ensure backward compatibility in CSS updates?](#question-13-how-do-you-ensure-backward-compatibility-in-css-updates)                                       |
| 14  | [How do you refactor a 10,000-line legacy CSS file?](#question-14-how-do-you-refactor-a-10000-line-legacy-css-file)                                                    |
| 15  | [How do you handle browser-specific bugs systematically?](#question-15-how-do-you-handle-browser-specific-bugs-systematically)                                         |
| 16  | [How does the browser resolve conflicting shorthand and longhand properties?](#question-16-how-does-the-browser-resolve-conflicting-shorthand-and-longhand-properties) |
| 17  | [How does CSS handle invalid at-rules?](#question-17-how-does-css-handle-invalid-at-rules)                                                                             |
| 18  | [How does cascading work across multiple layers and origins?](#question-18-how-does-cascading-work-across-multiple-layers-and-origins)                                 |
| 19  | [How does specificity interact with cascade layers?](#question-19-how-does-specificity-interact-with-cascade-layers)                                                   |
| 20  | [How does CSS variable fallback resolution work?](#question-20-how-does-css-variable-fallback-resolution-work)                                                         |

## Question 1. How do you minimize render-blocking CSS?

# Short answer

Render-blocking CSS delays the browser from painting the page because CSS must be downloaded and parsed before rendering. To minimize it:

- Inline critical (above-the-fold) CSS.
- Load non-critical CSS asynchronously.
- Remove unused CSS.
- Split CSS by route/component.
- Minify and compress CSS.
- Avoid large CSS frameworks when only a small subset is used.

The goal is to reduce the amount of CSS required before the first render.

---

# Explanation

CSS is render-blocking by design because the browser needs the final CSSOM (CSS Object Model) before it can safely render the page. If the browser painted before CSS was loaded, users would see unstyled content (FOUC).

A senior-level optimization strategy focuses on **critical rendering path reduction**:

### 1. Inline Critical CSS

Critical CSS contains styles needed to render the initial viewport (header, navigation, hero section, typography, layout).

Instead of waiting for an external stylesheet:

```html
<style>
  /* Critical styles */
  body {
    margin: 0;
    font-family: system-ui;
  }

  .hero {
    display: grid;
    place-items: center;
    min-height: 60vh;
  }
</style>
```

The browser can paint immediately.

**Trade-off:** Excessive inlining increases HTML size and reduces cacheability.

---

### 2. Load Non-Critical CSS Asynchronously

Styles required after initial render can be loaded later.

Common pattern:

```html
<link
  rel="preload"
  href="/styles/non-critical.css"
  as="style"
  onload="this.onload=null;this.rel='stylesheet'"
/>

<noscript>
  <link rel="stylesheet" href="/styles/non-critical.css" />
</noscript>
```

This allows rendering to start before downloading less important styles.

---

### 3. Remove Unused CSS

Large applications often ship thousands of unused selectors.

Examples:

- Unused utility classes
- Legacy styles
- Dead component CSS

Tools:

- PurgeCSS
- Lightning CSS
- Tailwind content scanning
- Chrome Coverage panel

Reducing CSS size directly reduces download and parse time.

---

### 4. Code-Split CSS

Modern frameworks support route-level or component-level CSS loading.

Examples:

- React + Vite
- Next.js
- Remix
- Angular
- Vue

Instead of shipping:

```
500 KB CSS
```

Ship:

```
Home page → 40 KB
Dashboard → 60 KB
Settings → 30 KB
```

Users download only what they need.

---

### 5. Minify and Compress

Production CSS should be:

- Minified
- Gzip compressed
- Preferably Brotli compressed

Example:

```css
/* Before */
.button {
  padding: 1rem;
  background: blue;
}

/* After */
.button {
  padding: 1rem;
  background: blue;
}
```

Compression often reduces transfer size by 70–90%.

---

### 6. Optimize CSS Architecture

A maintainable design system helps prevent CSS bloat:

- Design tokens
- Reusable components
- CSS custom properties
- Utility-first approaches when appropriate

Poorly managed stylesheets tend to accumulate render-blocking weight over time.

---

### 7. Use Resource Hints

For important stylesheets:

```html
<link rel="preload" href="/styles/app.css" as="style" />
```

This tells the browser to fetch CSS earlier.

Use carefully—preloading too many resources can compete with more important downloads.

---

# Example

A production-style pattern combining critical CSS and asynchronous loading:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <!-- Critical CSS -->
    <style>
      :root {
        --space: 1rem;
      }

      body {
        margin: 0;
        font-family: system-ui, sans-serif;
      }

      header {
        padding: var(--space);
        background: #111;
        color: white;
      }

      .hero {
        min-height: 50vh;
        display: grid;
        place-items: center;
      }
    </style>

    <!-- Non-critical CSS -->
    <link
      rel="preload"
      href="/css/components.css"
      as="style"
      onload="this.onload=null;this.rel='stylesheet'"
    />

    <noscript>
      <link rel="stylesheet" href="/css/components.css" />
    </noscript>
  </head>
  <body>
    <header>My App</header>

    <main class="hero">
      <h1>Fast First Paint</h1>
    </main>
  </body>
</html>
```

This approach renders core content immediately while deferring less important styles.

---

# Pitfalls

- **Inlining too much CSS** can increase HTML size and hurt caching.
- **Overusing preload** may compete with fonts, images, or JavaScript for bandwidth.
- **Aggressive CSS purging** can accidentally remove dynamically generated classes.
- **Asynchronous stylesheets** may cause flash of unstyled content (FOUC) if critical styles are not properly identified.

## Question 2. How do you lazy-load CSS?

## Question 3. How do you prevent FOUC (Flash of Unstyled Content)?

## Question 4. How do you handle CSS in SSR frameworks?

## Question 5. How do you debug CSS hydration mismatches?

## Question 6. How do you design CSS for micro-frontend architecture?

## Question 7. How do you manage shared styles across packages in a monorepo?

## Question 8. How do you avoid CSS duplication in large apps?

## Question 9. How do you audit CSS bundle size?

## Question 10. How do you write future-proof CSS?

## Question 11. How do you decide between utility classes and semantic classes?

## Question 12. How do you manage CSS in a component library?

## Question 13. How do you ensure backward compatibility in CSS updates?

## Question 14. How do you refactor a 10,000-line legacy CSS file?

## Question 15. How do you handle browser-specific bugs systematically?

## Question 16. How does the browser resolve conflicting shorthand and longhand properties?

## Question 17. How does CSS handle invalid at-rules?

## Question 18. How does cascading work across multiple layers and origins?

## Question 19. How does specificity interact with cascade layers?

## Question 20. How does CSS variable fallback resolution work?
