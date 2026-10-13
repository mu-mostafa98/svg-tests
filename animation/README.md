# SVG Animation Test Pages

One page per SVG animation *mechanism*, so each can be validated in isolation
against Servo's `servo-svg` engine.

## How to run

```
./mach build --features servo-svg -d                       # build once (dev + SVG engine)
./mach run -d file:///D:/Projects/svg-tests/animation/01_set_attribute.html
```

`--features servo-svg` is a build-time flag — it goes on `mach build`, not
`mach run`.

## Support status (as of 2026-10-09)

| File | Mechanism | Status | How it reaches the renderer |
|---|---|---|---|
| `01_set_attribute.html` | JS `setAttribute()` | ✅ Supported | attribute mutation → `NodeDamage::Other` → reflow → rebuild `SvgTree` |
| `02_css_keyframes.html` | CSS `@keyframes` | ✅ Supported | animation tick → `NodeDamage::Style` → `Repaint` upgraded to box damage → reflow |
| `03_css_transition.html` | CSS `transition` | ✅ Supported | style change → same `Repaint`-upgrade path as keyframes |
| `04_inline_style.html` | JS `el.style.* = …` | ✅ Supported | inline style change → same `Repaint`-upgrade path |
| `05_waapi.html` | WAAPI `element.animate()` | ⚠️ Partial | DOM surface exists, drives the same animation machinery; SVG-specific property mapping may have gaps |
| `06_smil.html` | SMIL `<animate>`/`<animateTransform>`/`<animateMotion>` | ❌ Not supported | parsed but ignored — SMIL elements are treated as non-rendering |

### Important caveat: "supported" ≠ "no reflow"

The four ✅ mechanisms all work today, but they do so by triggering a **reflow**
that re-runs `build_svg_tree` (incrementally via the `SvgSubtreeCache`). There is
no compositor-side (`PropertyBinding`) animation for SVG paint yet, so this is
"correct but not sub-frame-cheap". See the note in the engine for the
damage-upgrade path: `components/layout/traversal.rs` (the `servo-svg` block that
turns paint-only damage into box damage).
