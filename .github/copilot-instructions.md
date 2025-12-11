# Copilot Instructions - Creative Writing Club Website

## 🚫 Critical Rules

1. **NEVER edit `css/framework.css`** - This is a read-only framework file. All customizations go in `css/custom.css`.
2. **Always search existing CSS classes before creating new ones** - Reuse framework and custom classes to maintain consistency.
3. **Use the existing grid system** - All layouts use `.grid` class with responsive column spans.
4. **Ask for user preferences** - Don't make assumptions about design choices.

## Architecture Overview

This is a static HTML website for a creative writing club built with a custom responsive CSS framework. The site consists of 7 HTML pages (index, about, activities, showcase, resources, faq, contacts) sharing consistent navigation and styling patterns.

### File Structure
- **HTML Pages**: All pages share the same header/footer structure with mobile and desktop navigation
- **CSS Architecture**: 
  - `css/framework.css` - Core grid system and utilities (READ ONLY)
  - `css/custom.css` - All project-specific styles and overrides
- **Assets**: Images in `img/` directory, Font Awesome for icons

## Responsive Grid System

The framework uses a 12-column grid with three breakpoints:

```html
<!-- Responsive column classes -->
<div class="grid">
  <div class="mobi1 tab2 desk4">...</div>  <!-- Full width mobile, half on tablet, third on desktop -->
</div>
```

**Grid Classes:**
- **Mobile** (< 800px): `.mobi0` (hidden), `.mobi1` (12 cols), `.mobi2` (6 cols), `.mobi3` (4 cols), `.mobi4`, `.mobi6`, `.mobi12`
- **Tablet** (800px-1279px): `.tab0` (hidden), `.tab1`, `.tab2`, `.tab3`, `.tab4`, `.tab6`, `.tab8`, `.tab12`  
- **Desktop** (≥ 1280px): `.desk0` (hidden), `.desk1`, `.desk2`, `.desk3`, `.desk4`, `.desk6`, `.desk8`, `.desk12`

## Key CSS Patterns

### Color System
Use CSS variables defined in `css/custom.css`:
```css
var(--primary-100)   /* #2B2D42 */
var(--colour-1)      /* #2B2D42 - Dark blue */
var(--colour-2)      /* #1F473C - Dark green */
var(--colour-3)      /* #F4F4EC - Off-white */
var(--colour-4)      /* #97F2E9 - Cyan */
var(--colour-5)      /* #FDFF8A - Yellow */
var(--colour-6)      /* #414046 - Dark grey */
var(--colour-7)      /* #000000 - Black */
```

### Typography
- Body font: `"DM Sans"`, sans-serif
- Mono font: `"DM Mono"`, monospace
- Font Awesome loaded via CDN for icons

### Common Layout Patterns

**Hero Sections** - Full-height with background image:
```html
<section class="full-height hero-activities" id="hero-image"></section>
```
Background images set via modifier classes: `.hero-about`, `.hero-activities`, `.hero-resources`

**Dual Layout** - Image and text alternating pattern:
```html
<div class="dual-full-width">
  <div class="image" style="background: url('img/example.jpg') center center/cover no-repeat;"></div>
  <div class="text activities-pad-right">
    <h3>Title</h3>
    <h6>Description</h6>
  </div>
</div>
```

**Showcase Grid** - Card-based content display:
```html
<section class="showcase-grid showcase-grid-multi">
  <article class="showcase-card">...</article>
</section>
```

## Navigation System

**Dual Navigation**: Mobile hamburger menu + desktop horizontal nav

- Mobile nav controlled by checkbox: `#mobile-nav-toggle`
- Desktop nav uses `.desktop-nav` class
- Both support dropdown menus for "About" and "Activities" sections
- Active page indicated with `.active` class (adds bottom border)

## HTML Section Organization

Pages use clear comment-based section markers:
```html
<!-- * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
    3.1  Activities Hero Section   -->
```

Sections are numbered (e.g., 3.1, 3.2) for easy reference.

## Common Tasks

**Adding a new section**: Use `.grid` class with responsive columns:
```html
<section class="grid">
  <div class="mobi1 tab2 desk4">Content</div>
</section>
```

**Styling with existing patterns**: Check `css/custom.css` for classes like:
- `.activities-pad-right`, `.activities-pad-left` - Content padding
- `.activities-colour-3` - Color variants
- `.dark-bg-wrapper` - Dark background sections
- `.check-out-banner`, `.check-out-wrapper` - Call-to-action sections

**Adding colors or spacing**: Use CSS variables in `css/custom.css`:
```css
color: var(--colour-5);
padding: var(--spacing8x3);
```

## Development Workflow

No build process - pure HTML/CSS. Simply edit files and refresh browser to see changes. All pages reference the same three CSS files in order:
1. `css/framework.css`
2. `css/custom.css` (referenced but file not found - create if needed)
3. `css/custom.css`
