# Prompt Templates For PPT 素材重绘

## Single Element

```text
Create a high-resolution reusable PPT asset recreated from a reference slide image.
Asset type: <background / hero object / decoration / frame / icon / diagram>.
Element: <short description>.
Preserve the original element's aspect ratio: <wide / tall / square / exact ratio if known>.
Style to preserve: <line art / hand-drawn / glassmorphism / 3D / flat vector / paper texture / business illustration>.
Color palette: <main colors>.
Background: <pure white / pure black / same warm off-white slide background>.
Text rule: remove all words, numbers, labels, logos, and fake glyphs. If the original element had text, keep a clean blank area in the same position with matching material and lighting.
Composition: center the single element with generous padding; no cropping; clean edges for later cutout.
Constraints: no text, no watermark, no logo, no extra unrelated objects, no new decorative elements that were not in the reference.
```

## Text-Bearing Container

```text
Create a high-resolution reusable blank container asset from a PPT reference image.
Recreate the container/frame/card/banner only; remove all text inside it.
Preserve the blank text area, border radius, stroke color, shadow, material, and original aspect ratio.
Background: pure white unless the container is white; if white-on-white becomes hard to cut out, use light gray or black.
No words, no numbers, no logo, no watermark.
```

## Small Icon Sheet

```text
Create a high-resolution 2x2 or 2x3 sheet of small reusable icons matching the same style from a PPT reference image.
Icons to include: <icon 1>, <icon 2>, <icon 3>, <icon 4>.
Each icon must be isolated in its own quadrant/cell with generous spacing and consistent stroke weight.
Background: pure white or pure black for easy cutout.
Remove all labels and numbers. No extra icons, no text, no watermark.
```

## Background Layer

```text
Create a clean high-resolution PPT background layer recreated from a reference slide.
Include only the background texture, gradients, abstract light effects, lines, and decorative atmosphere.
Remove all foreground subjects, text, icons, charts, labels, logos, and UI cards.
Preserve the original slide aspect ratio and visual mood.
Background should be directly reusable for 1:1 PPT re-layout.
No text, no numbers, no watermark, no logo.
```

## Diagram Or Chart Component

```text
Create a high-resolution reusable PPT diagram/chart component from a reference slide image.
Recreate the visual structure only: <bars / line / arrows / nodes / funnel / timeline / flow>.
Remove all data labels, legends, axis labels, percentages, numbers, and text.
Preserve the blank chart frame, visual hierarchy, color palette, and original aspect ratio.
Background: pure white unless the component is pale; use black or same source background when needed for extraction.
No text, no numbers, no watermark, no logo.
```
