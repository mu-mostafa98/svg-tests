# Incremental-update test pages

One page per incremental-update scenario, each minimal enough to show just the
idea. Every page has a button that performs the change **in-document** so the
persistent `SvgSubtreeCache` is exercised across a reflow.

## How to run

```
./mach build --features servo-svg -d                                  # build once (dev + SVG engine)
RUST_LOG=svg=debug ./mach run -d <file>.html                          # sh / bash
$env:RUST_LOG = "svg=debug"; ./mach run -d <file>.html                # PowerShell
```

`-d` (dev build) is required — `debug!` is compiled out of release builds.
`--features servo-svg` is a build-time flag: it compiles the SVG engine in, so it
goes on `mach build`, not `mach run`. Point at a specific file, e.g.
`file:///D:/Projects/svg-tests/incremental/01_noop_reflow.html`.

Each cacheable element emits one line per rebuild:

```
svg: reuse <rect#a>          <- served from the cache unchanged
svg: build <rect#box> [SubtreeDirty]   <- rebuilt, with the miss reason
```

## Important caveats

- **Click the button, do not reload.** A full page reload rebuilds the DOM and
  starts the cache cold (all `[NoEntry]`). The cache is keyed by DOM node
  addresses, which change on reload.
- **Ignore the first-load `[NoEntry]` lines.** On initial load every node logs
  `build [NoEntry]`. The interesting `reuse` / `build [Reason]` lines begin on
  the first button click.
- The root `<svg>` never logs (it is returned by value, never cached).

## Scenarios

| File | Scenario | Key signal |
|---|---|---|
| `01_noop_reflow.html` | Harmless root-attribute mutation | all subtrees `reuse`, no `build` |
| `02_leaf_attribute.html` | One shape's own attribute changes | `build <rect#box> [SubtreeDirty]`, sibling `reuse` |
| `03_inherited_style.html` | Ancestor `<g fill>` changes | descendants `build [ComputedStyle]`, unrelated sibling `reuse` |
| `04_stylesheet_change.html` | Non-class CSS rule restyles one element | `build <rect#tinted> [ComputedStyle]`, other `reuse` |
| `05_cross_reference.html` | Two `<use>`s; mutate one referenced `<path>` | mutated path `[SubtreeDirty]`, untouched path `reuse`; `<use>` of mutated target `[ReferencedTarget]`, `<use>` of untouched target `reuse` |
| `06_viewport_change.html` | Nested `<svg>` `viewBox` changes its child's `vw`/`vh` | mutated `<svg>` `[SubtreeDirty]`, its child `[Viewport]`; untouched subtree `reuse` |
| `07_currentcolor_change.html` | Inherited `color` changes | child `build [CurrentColor]` |
| `08_child_mutation.html` | Child changes under an unchanged `<g>` | the `<g>` rebuilds `[SubtreeDirty]` (child bumped its version) |

The cache's decision logic is also covered by unit tests in
`servo/components/layout/svg/mod.rs` (`#[cfg(test)] mod tests`).
