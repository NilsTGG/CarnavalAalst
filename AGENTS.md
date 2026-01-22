# AGENTS.md - Carnaval Site Guidelines

This document provides guidelines for agentic coding agents operating in this repository.

## Project Overview

This is a static HTML site for Aalst Carnaval 2026. The project consists of a single `index.html` file containing all HTML, CSS, and JavaScript. No build step is required.

## Build, Lint, and Test Commands

### Build Commands
- **No build required**: This is a static HTML site. Simply open `index.html` in a browser or serve it with any static file server.
- **Serve locally**: Use any static server, e.g., `npx serve` or `python3 -m http.server 8000`

### Lint Commands
- **HTML validation**: Use W3C Validator at https://validator.w3.org/ or `npx html-validate index.html`
- **CSS linting**: Use `npx stylelint "**/*.css"` (no config exists yet)
- **JavaScript linting**: Use `npx eslint "**/*.js"` (no config exists yet)

### Test Commands
- **No automated tests**: This is a static site with no test suite
- **Manual testing**: Test in multiple browsers (Chrome, Firefox, Safari, Edge) and verify:
  - Countdown timer works correctly
  - Video embed loads and autoplays
  - Responsive design works on mobile (≤768px)
  - All text is readable and accessible

### Running a Single Test
- Not applicable - no test suite exists

## Code Style Guidelines

### General Principles
- Keep code simple and readable
- Use semantic HTML5 elements
- Maintain consistency with existing patterns
- Add comments for non-obvious functionality

### HTML Conventions
- Use lowercase for tags and attributes: `<div class="container">` not `<DIV CLASS="container">`
- Use double quotes for attribute values: `href="https://example.com"`
- Self-close void elements: `<meta charset="UTF-8">` not `<meta charset="UTF-8" />`
- Use semantic elements: `<header>`, `<main>`, `<footer>`, `<article>`
- Include `lang` attribute on `<html>`: `<html lang="nl">` for Dutch content
- Use `viewport` meta tag for responsive design
- Accessibility: Include `alt` text for images, `aria-label` where needed

### CSS Conventions
- Use lowercase with kebab-case for class names: `.countdown-section` not `.countdownSection`
- Use 4 spaces for indentation (no tabs)
- Organize properties alphabetically within rules
- Use CSS custom properties (variables) for colors and values
- Use flexbox or grid for layout instead of floats
- Use `rem` for font sizes, `px` only for borders and shadows
- Group related styles with comments: `/* Header styles */`
- Responsive breakpoints: use `@media (max-width: 768px)` for mobile

Example structure:
```css
.selector {
    property: value;
    another-property: value;
}
```

### JavaScript Conventions
- Use `const` by default, `let` only when reassignment is needed
- Use strict equality: `===` and `!==` instead of `==` and `!=`
- Use meaningful variable and function names
- Use 4 spaces for indentation
- Use jQuery consistently if already present (as in this project)
- Wrap jQuery in document ready handler: `$(document).ready(function($) { ... });`
- Use semicolons consistently
- Prefer template literals over string concatenation

Example:
```javascript
const initCountdown = function() {
    $("#DateCountdown").TimeCircles({
        animation: "smooth",
        fg_width: 0.04
    });
};
```

### Naming Conventions
- **CSS classes**: lowercase with hyphens (kebab-case): `.main-header`
- **JavaScript variables/functions**: camelCase: `initCountdown`, `isValid`
- **Constants**: UPPER_SNAKE_CASE for true constants: `DEFAULT_TIMEOUT`
- **IDs**: camelCase for HTML IDs: `<div id="dateCountdown">`

### Error Handling
- Wrap DOM-dependent code in document ready handlers
- Add console logs for debugging (remove before production)
- Validate DOM elements exist before manipulating them
- Use try/catch for any async operations

### File Organization
- Keep all HTML, CSS, and JavaScript in `index.html` (current pattern)
- External libraries via CDN (cdnjs.cloudflare.com)
- If adding new files, create `css/` and `js/` directories
- For multiple pages, use consistent header/footer patterns

### Performance
- Minimize DOM manipulations
- Use CSS animations over JavaScript when possible
- Defer non-critical scripts: `<script defer>`
- Use lazy loading for below-fold content

### Accessibility
- Ensure color contrast ratio ≥ 4.5:1 for normal text
- Use semantic HTML structure
- Include proper `alt` attributes
- Support keyboard navigation
- Test with screen readers

### Git Conventions
- Write clear commit messages: "Add countdown timer functionality"
- Create feature branches for new changes
- Use present tense in commit messages: "Add" not "Added"

## Editor Configuration

Recommended VS Code settings for this project:
```json
{
    "editor.tabSize": 4,
    "editor.insertSpaces": true,
    "html.format.indentInnerHtml": true,
    "css.format.spaceAroundSelectorSeparator": true
}
```

## Current Stack
- HTML5
- CSS3 (embedded)
- JavaScript (jQuery 3.6.0, TimeCircles 1.4.4)
- No build tools required
