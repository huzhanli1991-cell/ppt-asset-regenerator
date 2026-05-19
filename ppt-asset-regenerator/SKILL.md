---
name: ppt-asset-regenerator
description: "Use this skill when the user provides a PPT page screenshot, slide image, poster, infographic, or AI-generated PPT image and wants Codex to identify visual layers and regenerate high-resolution reusable image assets with imagegen. It decomposes the page into background, main visual, text areas, decorative graphics, icons, shapes, diagrams, charts, and small icon sets; removes text from regenerated assets while preserving blank text space; keeps each asset's original aspect ratio; saves one element per image or a small icon sheet; and prepares assets for masking, cutout, 1:1 re-layout, editable PPT reconstruction, or image-to-PPT workflows."
---

# PPT 素材重绘

## Purpose

Turn a supplied PPT screenshot, slide image, poster, infographic, or AI-generated PPT page into a reusable high-resolution asset pack.

Do not merely crop low-resolution elements from the source. Inspect the page, identify its visual layers, then use image generation to recreate clean, sharper assets that can be reused in PPT, Photoshop, image2ppt, or manual 1:1 re-layout.

Use this skill together with the built-in `imagegen` skill for actual image generation.

## Core Workflow

1. Inspect the source image carefully. If the user provides a local file path and the image is not already visible, load it first.
2. Create an element inventory before generating anything. Classify elements as:
   - background layer
   - main visual / hero object
   - people / character / mascot
   - illustration / decorative image
   - icon / icon set
   - geometric shape / container / card / frame
   - chart / diagram / flow element
   - text-bearing area
   - texture / pattern / light effect
3. Decide which elements should be regenerated. Skip pure text as an asset; text should usually be rebuilt later in PPT.
4. For text-bearing graphics, regenerate the graphic without text and preserve the blank text space.
5. Generate one image per meaningful element. For very small related icons, generate a single 2x2 or 2x3 icon sheet only when the icons share the same style and will be cut out later.
6. Keep each element's original width-height proportion. Only increase resolution, clarity, and edge quality.
7. Choose a background that supports later extraction:
   - default: white background
   - black background: use for white, glowing, glass, neon, smoke, sparkles, or pale line elements
   - same-as-source background: use when the asset must blend back into the original slide
   - chroma-key background: only when the user explicitly asks and the subject colors make keying practical
8. Save outputs into a structured workspace folder with an asset manifest and notes.
9. Report what was generated, what was intentionally left as text, and any ambiguous elements that need manual judgment.

## Output Structure

If the user gives no destination, create an output folder under the current workspace:

```text
04_配图与封面/素材资产包/<source-name>/
  00_source/
  01_background/
  02_main_visual/
  03_decorations/
  04_icons/
  05_shapes_frames/
  06_diagrams_charts/
  manifest.json
  process_notes.md
```

For non-public or temporary experiments, use:

```text
generated_assets/<source-name>/
```

Copy final generated images from the image generation output folder into the project folder. Leave the original generated files in place unless the user explicitly asks to delete them.

## Element Inventory Format

Before generation, prepare a concise inventory like this:

```text
1. Background layer: off-white paper texture, full 16:9 page, no text.
2. Main visual: 3D dashboard device, right center, keep 16:9-ish crop, remove labels.
3. Icon set: six blue line icons under dashboard, generate as 2x3 sheet or individual icons.
4. Text containers: three rounded white cards with orange border, remove all text, preserve empty centers.
5. Decorative lines: thin blue network lines, same background, no readable labels.
```

Use this inventory to decide filenames and prompts.

## Regeneration Rules

- Regenerate assets; do not simply crop source pixels unless the user asks for extraction only.
- Preserve the visible design language: line weight, material, color palette, lighting, perspective, roughness, and composition.
- Preserve the element's aspect ratio. Add generous padding only when it helps cutout or prevents edge clipping.
- Remove all text, numbers, logos, watermarks, and fake glyphs unless the user explicitly asks to keep them.
- If the original graphic contains text, leave a clean blank panel, label area, plaque, banner, or whitespace with matching material and lighting.
- For icons, keep strokes bold enough for later scaling. Do not add labels.
- For chart-like visuals, remove exact data labels unless the user wants a non-editable chart image. Prefer blank axes, abstract bars, or reusable chart frames.
- For people, generate generic figures that match style; do not preserve real identities unless the user explicitly owns or permits the likeness.
- For PPT re-layout, prioritize clean edges, non-overlapping element bounds, and easy background removal over photorealism.

## Prompt Rules

Use precise production prompts. Every prompt should specify:

- source role: reusable PPT asset recreated from reference page
- asset type and element number
- target subject and visible features
- aspect ratio relative to the original element
- background choice
- text removal rule
- style preservation rule
- constraints: no text, no numbers, no watermark, no logo, no extra unrelated objects

Read `references/prompt-templates.md` when drafting generation prompts.

## File Naming

Use stable names:

```text
p01_01_background_clean.png
p01_02_hero_dashboard_no_text.png
p01_03_orange_rounded_card_blank.png
p01_04_icon_set_2x2.png
p01_05_network_lines_same_bg.png
```

If the source has multiple pages, prefix by page number. If the page number is unknown, use `p00`.

## Quality Check

After generating and saving assets, inspect them when possible:

- Does the asset match the original element category and style?
- Is all text removed?
- Is the blank text space preserved if needed?
- Is the aspect ratio close to the source element?
- Is the background suitable for cutout or re-layout?
- Are there no unwanted logos, watermarks, extra text, or fake UI labels?

If a generated asset has incorrect text, wrong proportions, or style drift, regenerate with a narrower prompt.

## Final Response

Report concisely:

- output folder path
- number of generated images
- asset groups included
- text areas intentionally left blank
- known limitations or elements not regenerated
