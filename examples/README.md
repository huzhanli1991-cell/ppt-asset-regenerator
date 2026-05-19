# Examples

## Example Request

```text
用 ppt-asset-regenerator 提取这张 PPT 图片中的元素。
请先识别背景层、主视觉、文字区域、装饰元素、图标、图表和卡片框。
然后把值得复用的元素重绘成高清素材。
素材中的文字去掉，保留文字空间。
一张图尽量只放一个元素，小图标可以做成 2x2 或 2x3 图标 sheet。
```

## Expected Asset Groups

```text
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

## Good Source Images

- PPT 页面截图
- 图片版 PPT
- AI 生成的 PPT 单页
- 海报或信息图
- 有明显背景、卡片、图标、图表、主视觉元素的页面

## Less Suitable Inputs

- 纯文字页面
- 分辨率过低且无法判断元素关系的截图
- 需要精确保留真实人物肖像的商业图片
- 需要保留原始品牌 logo 的素材图
