# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Google Glass — Site Responsivo** is an educational project from the [Curso em Vídeo](https://www.cursoemvideo.com/) by Gustavo Guanabara. It's a static HTML5/CSS3 website with added responsive design (mobile, tablet, desktop) and minimal JavaScript interactivity.

- **Tech Stack**: HTML5 (semantic markup), CSS3 (Flexbox, media queries), JavaScript (DOM event handlers)
- **Deployment**: GitHub Pages (see `.github/workflows/pages.yml`)
- **Root Directory**: Content in `curso/` folder

## Getting Started

### Running Locally

```bash
# Simple HTTP server (Python)
cd curso
python3 -m http.server 8000
# Visit http://localhost:8000

# OR using Node.js serve
npx serve .
```

### Viewing Changes

Since this is static HTML, simply refresh the browser after edits. No build process required.

## Project Structure

```
curso/
├── *.html              # Page files (index, specs, fotos, multimidia, fale-conosco)
├── _css/               # Stylesheets (modular by page)
├── _javascript/        # Minimal JS (funcoes.js has icon-swap handlers)
├── _imagens/           # Images and assets
├── _fonts/             # Custom fonts
├── _media/             # Audio/video files
├── _textos/            # Text content files
└── testes/             # Test images
```

## CSS Architecture

The CSS strategy preserves the original course structure while adding modern responsiveness:

- **`estilo.css`** — Base styles (desktop-first, 900px+ layout)
- **`responsivo.css`** — Media queries for tablet (≤900px) and mobile (≤600px)
  - This file is loaded **last** to override desktop styles
  - Do NOT modify original `*.css` files; add breakpoints here
- **Page-specific files** — `form.css`, `fotos.css`, `specs.css`, `media.css` (loaded per page)

### Responsive Breakpoints

- **Desktop (default)**: ≥901px — original layout with absolute positioning
- **Tablet (≤900px)**: Header/nav reflow, content stacks, adjusted spacing
- **Mobile (≤600px)**: Vertical menu, smaller fonts, tables adapted

### Adding Responsive Rules

If you need to adjust layout at breakpoints:

```css
/* In _css/responsivo.css */
@media screen and (max-width: 900px) {
  /* Tablet rules */
}

@media screen and (max-width: 600px) {
  /* Mobile rules */
}
```

## JavaScript Patterns

The project uses **inline event handlers** in HTML (not modern, but matches course style):

```html
<li
  onmouseover="mudaFoto('_imagens/home.png')"
  onmouseout="mudaFoto('_imagens/glass-oculos-preto-peq.png')"
>
  <a href="index.html">Home</a>
</li>
```

The handler is defined in `_javascript/funcoes.js`:

```javascript
function mudaFoto(foto) {
  document.getElementById("icone").src = foto;
}
```

**Follow this pattern** if adding interactivity to stay consistent with the course material.

## Pages and Content

| File                | Purpose        | Key Feature                                |
| ------------------- | -------------- | ------------------------------------------ |
| `index.html`        | Home page      | Hero section with article                  |
| `specs.html`        | Specifications | Image map (clickable areas)                |
| `fotos.html`        | Photo gallery  | Gallery grid with CSS hover zoom           |
| `multimidia.html`   | Media player   | HTML5 audio/video tags                     |
| `fale-conosco.html` | Contact form   | HTML5 form inputs (email, tel, date, etc.) |

## HTML Conventions

- **Semantic markup** — Use `<header>`, `<nav>`, `<section>`, `<article>`, `<aside>`, `<footer>`
- **Lang attribute**: All files use `lang="pt-br"` (Portuguese Brazil)
- **Charset**: UTF-8
- **Viewport meta tag**: Already set for responsive design

## Deployment

GitHub Pages is configured to auto-deploy on `main` branch push:

```yaml
# .github/workflows/pages.yml
- Builds from ./curso directory
- Triggers on push to main or manual workflow_dispatch
```

## Common Tasks

### Add a new HTML page

1. Create `curso/new-page.html` with semantic structure
2. Include `_css/estilo.css` and `_css/responsivo.css`
3. Add navigation link in header menu
4. Use existing pages as template for structure

### Add a new CSS file (page-specific)

1. Create file in `_css/` named after the page (e.g., `new-page.css`)
2. Link in the HTML `<head>`: `<link rel="stylesheet" href="_css/new-page.css"/>`
3. Load **before** responsivo.css so media queries in responsivo.css override

### Fix responsiveness issues

1. Check the breakpoint (900px or 600px) where issue occurs
2. Add rule to `_css/responsivo.css` in the appropriate `@media` block
3. Test in browser at that viewport size

### Add interactivity

1. Create handler function in `_javascript/funcoes.js`
2. Add inline `onmouseover`, `onclick`, etc. to the HTML element
3. Keep JavaScript minimal — this is a course project, not a production app

## Notes for Future Work

- **Course Integrity**: Preserve the original course structure; responsive CSS is an _addition_, not a refactor
- **Browser Support**: Flexbox and modern CSS are supported in all modern browsers
- **Accessibility**: Consider adding ARIA labels if expanding form functionality
- **Image Optimization**: Images are sourced from course; resize/optimize if adding new images
