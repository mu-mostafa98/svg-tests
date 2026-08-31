# SVG Test Suite — Plan & Table of Contents

This repository contains a comprehensive suite of HTML test harnesses designed to systematically validate SVG rendering, layout, styling, filter effects, dynamic features, and edge cases across browsers and SVG rendering engines.

---

## Table of Contents

### 1. Geometry and Basic Shapes
Tests core vector geometry rendering, including standard, zero, and negative dimension handling.

| File Name | Test Scope & Description | Key Tags & Attributes |
| :--- | :--- | :--- |
| **`1_basic_shapes.html`** | Tests basic primitive shapes (`<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, `<polygon>`) with standard dimensions, zero dimensions, negative dimensions, and rounded corners (`rx`, `ry`). | `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, `<polygon>` |
| **`2_path_commands.html`** | Tests fundamental path data commands using absolute (uppercase) and relative (lowercase) coordinates. Covers line, horizontal, vertical, and closepath commands. | `<path d="M/m L/l H/h V/v Z/z">` |
| **`3_path_curves.html`** | Tests complex path commands including cubic Bézier, smooth cubic Bézier, quadratic Bézier, smooth quadratic Bézier, and elliptical arcs with extreme arc flags (`large-arc-flag`, `sweep-flag`). | `<path d="C/c S/s Q/q T/t A/a">` |

---

### 2. Painting, Styling, and Graphics Elements
Tests color fill, stroke rendering, gradients, pattern tiling, and vector markers.

| File Name | Test Scope & Description | Key Tags & Attributes |
| :--- | :--- | :--- |
| **`4_stroke_properties.html`** | Tests stroke styling parameters including `stroke-width`, cap styles (`butt`, `round`, `square`), join styles (`miter`, `round`, `bevel`), `stroke-miterlimit`, and complex dash patterns via `stroke-dasharray` and `stroke-dashoffset`. | `stroke`, `stroke-width`, `stroke-linecap`, `stroke-linejoin`, `stroke-miterlimit`, `stroke-dasharray` |
| **`5_linear_gradients.html`** | Tests linear gradients with varying angles, multiple color stops, opacity stops, stop offsets, and spread methods (`pad`, `reflect`, `repeat`). | `<linearGradient>`, `<stop>`, `x1`, `y1`, `x2`, `y2`, `spreadMethod` |
| **`6_radial_gradients.html`** | Tests radial gradients with focal points (`fx`, `fy`), center points (`cx`, `cy`), radius (`r`), focal radius (`fr`), and coordinate spaces (`userSpaceOnUse` vs `objectBoundingBox`). | `<radialGradient>`, `<stop>`, `cx`, `cy`, `r`, `fx`, `fy`, `gradientUnits` |
| **`7_patterns.html`** | Tests pattern tiling, nested vector shapes within patterns, pattern transformations, and coordinate spaces (`patternUnits`, `patternContentUnits`). | `<pattern>`, `patternUnits`, `patternContentUnits`, `patternTransform` |
| **`8_markers.html`** | Tests line/path ornamentation using markers attached to start, middle, and end vertices (`marker-start`, `marker-mid`, `marker-end`) with auto-rotation (`orient="auto"` / `orient="auto-start-reverse"`). | `<marker>`, `marker-start`, `marker-mid`, `marker-end`, `orient`, `refX`, `refY` |

---

### 3. Layout, Coordinate Systems, and Reusability
Tests coordinate spaces, viewports, transformations, and symbol instantiation.

| File Name | Test Scope & Description | Key Tags & Attributes |
| :--- | :--- | :--- |
| **`9_viewbox_scaling.html`** | Tests SVG viewport matching/mismatching with all variations of `preserveAspectRatio` alignment (`xMin`, `xMid`, `xMax` × `YMin`, `YMid`, `YMax`) and scaling modes (`meet`, `slice`, `none`). | `viewBox`, `preserveAspectRatio`, `width`, `height`, `overflow` |
| **`10_coordinate_transforms.html`** | Tests transformation pipelines on nested elements using cumulative transform functions (`translate`, `scale`, `rotate`, `skewX`, `skewY`, `matrix`) and CSS `transform-origin`. | `transform`, `transform-origin`, `<g>` |
| **`11_symbols_and_use.html`** | Tests element reusability via `<defs>`, `<symbol>`, and `<use>` elements across explicit and implicit shadow DOM roots with style overrides. | `<defs>`, `<symbol>`, `<use>`, `href` / `xlink:href` |

---

### 4. Text Rendering and Typography
Tests plain text layout, multi-line spans, anchor positioning, text along paths, and web fonts.

| File Name | Test Scope & Description | Key Tags & Attributes |
| :--- | :--- | :--- |
| **`12_basic_text.html`** | Tests baseline positioning, `<tspan>` nesting, text alignment via `text-anchor` (`start`, `middle`, `end`), dominant baseline alignment, and custom web-font integration via `@font-face`. | `<text>`, `<tspan>`, `text-anchor`, `dominant-baseline`, `font-family` |
| **`13_text_paths.html`** | Tests wrapping text along open, closed, linear, and curved paths, with varying `startOffset`, `side`, and `method` attributes. | `<textPath>`, `href`, `startOffset`, `side`, `method` |

---

### 5. Compositing, Masking, and Visual Effects
Tests clipping, opacity masking, and SVG filter primitives.

| File Name | Test Scope & Description | Key Tags & Attributes |
| :--- | :--- | :--- |
| **`14_clipping_paths.html`** | Tests non-destructive clipping on shapes, groups, and text using overlapping paths, complex vectors, and `clipPathUnits`. | `<clipPath>`, `clip-path`, `clipPathUnits`, `clip-rule` |
| **`15_masking.html`** | Tests alpha and luminance masking (`mask-type`) using semi-transparent elements, grayscale gradients, and multi-layered mask structures. | `<mask>`, `mask`, `mask-type`, `maskUnits` |
| **`16_filter_effects_basic.html`** | Tests essential filter primitives: Gaussian blur, drop shadow, offset, blend modes, and color matrix transformations. | `<filter>`, `<feGaussianBlur>`, `<feDropShadow>`, `<feOffset>`, `<feBlend>`, `<feColorMatrix>` |
| **`17_filter_effects_advanced.html`** | Tests advanced filter pipelines: turbulence, displacement mapping, specular/diffuse lighting, component transfer, and morphology. | `<feTurbulence>`, `<feDisplacementMap>`, `<feSpecularLighting>`, `<feComponentTransfer>`, `<feMorphology>` |

---

### 6. Interactivity, Dynamic Features, and Embedded Content
Tests declarative animation, CSS integration, hit-testing, dynamic styling, and foreign markup.

| File Name | Test Scope & Description | Key Tags & Attributes |
| :--- | :--- | :--- |
| **`18_smil_animations.html`** | Tests SMIL declarative animations using attribute morphing, CSS property interpolation, and motion along paths. | `<animate>`, `<animateTransform>`, `<animateMotion>`, `<mpath>` |
| **`19_css_animations.html`** | Tests inline and external CSS `@keyframes` animations, transitions, dynamic CSS Variables (`var(--accent)`), and state pseudo-classes (`:hover`, `:active`). | `<style>`, `@keyframes`, `transition`, `var()` |
| **`20_pointer_events.html`** | Tests hit-testing and event capturing across interactive shapes using varying `pointer-events` rules (`none`, `visiblePainted`, `stroke`, `fill`, `all`). | `pointer-events`, `fill-opacity`, `stroke-opacity`, `visibility` |
| **`21_embedded_content.html`** | Tests raster image embedding (PNG, JPEG, WebP), nested inline SVG documents, and HTML embedding within SVG layouts. | `<image>`, `<foreignObject>`, nested `<svg>` |

---

## Test Execution Guidelines

1. **Standard Directory Layout**: Place all `.html` test files in the root or a `/tests` directory.
2. **Harness Layout**: Each file follows a standard CSS Grid flexbox container with consistent card sizing (`200px` × `200px` standard viewBox) for automated visual regression testing.
3. **Automated Verification**: Use visual regression runners like **Playwright**, **Puppeteer**, or **Appium** to compare rendered outputs against reference baseline snapshots across modern engine targets (Chromium, WebKit, Gecko).
