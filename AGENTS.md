# ISTQB Certs - Project Rules

## Infographic Study Guide Style

When creating new infographic HTML study guide pages in this project, follow these conventions:

### File Structure
- Place each topic in its own subfolder: `<topic-name>/index.html`
- Reference shared CSS via `../shared-styles.css` (already exists at project root)
- Use template `template.html` (at project root) as the starting skeleton - it already wires up the CSS, TOC sidebar, Home button, and JS
- Use Google Fonts: `Caveat` (headings) + `Patrick Hand` (body) - loaded via `<link>`

### Visual Style
- **Sketch border class**: Always use `.sketch-border` on cards/boxes - light gray border (`1.5px solid #ccc`) with organic hand-drawn border radius
- **Colors**: Use the pastel CSS variables (`--pastel-pink`, `--pastel-blue`, `--pastel-green`, `--pastel-yellow`, `--pastel-purple`, `--pastel-orange`, `--pastel-cyan`, `--pastel-rose`)
- **Background**: `#FDF6EC` (warm off-white)
- **Text**: `#3D3D3D` (dark gray, not black)
- **Fonts**: `Caveat` for all headings, titles, numbers. `Patrick Hand` for body text

### Page Structure (required)
1. **Floating TOC sidebar** - left side, with chapter items + point values, pass pill at bottom
2. **Main content** offset by `margin-left: var(--toc-w)`
3. **Chapter sections** using `.chapter-section` with IDs for anchor navigation
4. **Mobile**: TOC collapses to hamburger toggle button
5. **Back to Home button** - top-right fixed button linking to `../index.html`. Use `.home-btn` class (defined in `shared-styles.css`). For pages with inline styles, add the `.home-btn` CSS inline too.
```html
<a class="home-btn" href="../index.html" style="position:fixed;top:14px;right:14px;z-index:1001;">&#127968; Home</a>
```

### Available Components
Use these CSS classes from `shared-styles.css`:

| Component | Classes | Purpose |
|-----------|---------|---------|
| Chapter banner | `.ch-banner .ch-title .ch-meta .ch-tag` | Top banner per chapter with title + tags |
| Card grid | `.card-grid .cols-2 .cols-3 .cols-4 .info-card` | Responsive card layouts |
| Bullet list | `.bullet-list .bullet-item .bi-icon` | Icon + text bullet points |
| Layer stack | `.layer-stack .layer-box` | Vertical stacked boxes |
| Flow diagram | `.flow-row .flow-node .flow-arrow` | Horizontal pipeline with arrows |
| Bar chart | `.bar-rows .bar-row .bar-label .bar-track .bar-fill` | Horizontal bar charts |
| Tooltips | `.tt .tt-box` | Hover-to-reveal tooltip popups |
| Tip boxes | `.tip-box .warn .info .success` | Colored callout boxes |
| Meters | `.meter-wrap .meter-track .meter-fill` | Progress/meter bars |
| Trap cards | `.trap-card .tc-name .tc-desc` | Exam pitfall warnings |
| Strategy flow | `.strat-flow .strat-step .strat-arrow` | Step-by-step horizontal flow |
| Contract diagram | `.contract-row .contract-box .contract-arrow` | A-B-C relationship diagrams |

### Chapter Banners
```html
<div class="ch-banner sketch-border bg-ch1 anim" data-ch="1">
  <div class="ch-title">Ch.1 - Title</div>
  <div class="ch-meta">
    <span class="ch-tag pts">X pts (XX%)</span>
    <span class="ch-tag diff">Difficulty</span>
    <span class="ch-tag ks">X Questions</span>
  </div>
</div>
```
Use `bg-ch1` through `bg-ch8` for banner background colors.

### Tooltip Pattern
```html
<span class="tt" style="display:inline-block;margin-top:6px;font-size:.85rem">Hover text
  <div class="tt-box">Detail text on hover</div>
</span>
```

### Animation
- Add `.anim` class to elements that should animate in on scroll
- JS observer automatically adds `.vis` class when visible

### Bar Chart Pattern
```html
<div class="bar-row">
  <div class="bar-label">Label</div>
  <div class="bar-track"><div class="bar-fill" data-width="75" style="background:var(--pastel-green)"></div></div>
  <div class="bar-desc">Description</div>
</div>
```
Bar fills animate via `data-width` attribute (percentage) on scroll.

### Content Rules
- **Minimal text** - use icons, tooltips, and visual elements instead of paragraphs
- **All content from source** - nothing should be missing, but condense to key terms
- **Tooltips for details** - hover for expanded explanations
- **No comments in HTML** unless requested
