# Web Performance

## Image Optimization

- Choose the right formats
  - MP4 instead of GIFs
  - SVG for icons and illustrations
- Prefer lossy optimizers
  - check lossy vs losless
- npm imagemin
- JPNG.svg instead of PNG

## Font Loading

- font subset on fontsquirel

## Animation Performance

- Layout, Paint, Composite
  - Do not animate Layout properties
  - https://csstriggers.com/
- Animate using opacity and transform
- Use will-change: transform
- Monitor CPU memory

## Critical Rendering

- webpack-plugin-critical
  - Addy Osmany critial library

## Script Loading

- use Async for small scripts to be executed quickly (e.g. analytics)
- use Defer for everything else

## Code Minification

- Minify css and js files
- Check gziping on the server

## Lazy Loading

- use IntersectionObserver to load images on scroll

## Loading Indicators

- Quick page load; Skeleton Screen
- < 2s use a spinner
- \> 2s use a progress bar
- \> 6s use a progress bar with explanation
