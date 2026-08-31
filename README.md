Geometry and Shapes
1_basic_shapes.html: Tests <rect>, <circle>, <ellipse>, <line>, <polyline>, and <polygon> with standard, zero, and negative dimensions.
2_path_commands.html: Tests all path data (d) commands (M/m, L/l, H/h, V/v, Z/z) using absolute and relative coordinates.
3_path_curves.html: Tests cubic Bezier (C/c, S/s), quadratic Bezier (Q/q, T/t), and elliptical arcs (A/a) including extreme arc flags.Painting and Styling4_stroke_properties.html: Tests stroke-width, stroke-linecap (butt, round, square), stroke-linejoin (miter, round, bevel), stroke-miterlimit, and complex stroke-dasharray patterns.
5_linear_gradients.html: Tests <linearGradient> with varying angles, multiple color stops, opacity stops, and spread methods (pad, reflect, repeat).
6_radial_gradients.html: Tests <radialGradient> focus points (fx, fy), radii (r), and gradient unit coordinate spaces.
_patterns.html: Tests <pattern> tiling, nested shapes inside patterns, and coordinate spaces (userSpaceOnUse vs objectBoundingBox).
8_markers.html: Tests <marker> attaching to path start, middle, and end vertices with auto-rotation.Layout and Coordinates.
9_viewbox_scaling.html: Tests viewBox matching and mismatching with all variations of preserveAspectRatio (e.g., xMinYMin meet, xMaxYMax slice).
10_coordinate_transforms.html: Tests nested <g> elements using cumulative transform functions (translate, scale, rotate, skewX, skewY, matrix).Text Rendering.
11_basic_text.html: Tests <text> and <tspan> positioning, text-anchor (start, middle, end), and custom web-font rendering.
12_text_paths.html: Tests <textPath> wrapping text along linear, curved, and closed paths with varying startOffset values.Compositing and Visual Effects.
13_clipping_paths.html: Tests <clipPath> usage on shapes, groups, and text using paths and overlapping vectors.
14_masking.html: Tests mask-type (luminance vs alpha) with semi-transparent, grayscale, and gradient masks.
15_filter_effects_basic.html: Tests basic filter primitives like <feGaussianBlur>, <feColorMatrix>, <feComponentTransfer>, and <feMerge>.
16_filter_effects_advanced.html: Tests complex filter primitives like <feDisplacementMap>, <feLightingProjectic>, and <feComposite> blending modes.Interactivity and Dynamic Features
17_smil_animations.html: Tests declarative animations using <animate>, <animateTransform>, and <animateMotion> along a path.
18_css_animations.html: Tests external and inline CSS @keyframes, transitions, and pseudo-classes (like :hover) applied to SVG elements.
19_pointer_events.html: Tests pointer-events values (none, visiblePainted, stroke, fill) across transparent, overlapping, and hidden shapes.
20_embedded_content.html: Tests <image> embedding (PNG, JPEG, nested SVGs) and foreign document rendering via <foreignObject>.
