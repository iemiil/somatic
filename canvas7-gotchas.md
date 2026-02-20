# Canvas 7 Template - Gotchas & Lessons Learned

## 1. Never build from scratch
Canvas 7 is NOT a simple CSS framework. JS and CSS are tightly coupled.
**Always start from a working .html file** (like `index-classic.html`) and modify it incrementally.

## 2. `one-page-menu` class is broken
The class `one-page-menu` on `<ul class="menu-container">` triggers a JS module that prevents
the menu from rendering. Even the original `index-onepage.html` doesn't show menu items.
**Solution**: Use `<ul class="menu-container">` (without `one-page-menu`) and add `data-scrollto`
attributes on individual `<a>` links for smooth scrolling.

## 3. Spans inside `.menu-link` are hidden
Canvas CSS rule: `.menu-link span { display: var(--cnvs-primary-menu-submenu-subtitle-display); }`
which resolves to `display: none`. This hides ALL `<span>` elements inside menu links.
**Solution**: Use `<em class="not-italic">` instead of `<span>` for bilingual text in nav.

## 4. Transparent header requires Swiper structure
The transparent header (`transparent-header` class) only works correctly when combined with
the full Canvas Swiper slider structure:
```
section.slider-element.slider-parallax.swiper_wrapper.include-header
  > .slider-inner > .swiper.swiper-parent > .swiper-wrapper > .swiper-slide.dark
```
Custom hero sections without this structure won't trigger the correct JS behavior.

## 5. Menu visibility depends on `is-expanded-menu` body class
Canvas JS adds `is-expanded-menu` to `<body>` when viewport >= 992px.
`.menu-container` has `display: none` by default and only shows with this class.
The class is added by `Base.menuBreakpoint()` in `functions.bundle.js`.

## 6. White menu text on transparent header (desktop only)
To make menu links white on the dark hero overlay:
```css
.is-expanded-menu #header.transparent-header:not(.sticky-header) {
    --cnvs-primary-menu-color: #fff;
}
```
Must use `.is-expanded-menu` prefix - otherwise mobile dropdown (white bg) gets white text too.

## 7. Logo text instead of image
Use Canvas's `logo-default` / `logo-dark` classes on spans inside `#logo a`:
```html
<span class="logo-default logo-text">TEXT</span>
<span class="logo-dark logo-text-dark">TEXT</span>
```
Canvas JS toggles these based on header state (transparent vs sticky).

## 8. Local development requires HTTP server
Canvas JS may not fully initialize when opened via `file://` protocol.
Use `python -m http.server 8080` from the project directory.
