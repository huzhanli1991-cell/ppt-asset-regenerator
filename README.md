# PPT Asset Regenerator

`ppt-asset-regenerator` 是一个 Codex skill，用于从 PPT 截图、页面图、海报、信息图或 AI 生成的 PPT 图片中识别视觉元素，并重新生成高清可复用素材。

它适合这些场景：

- 把一张图片版 PPT 拆成可复用视觉资产
- 从低清截图中重绘高清背景、主视觉、图标和装饰元素
- 去掉图片素材里的文字，保留空白文字区域
- 为后续 1:1 复排、图片转可编辑 PPT、PSD 分层或手工排版准备素材包

## What It Does

- 识别背景层、主视觉、人物、装饰图、图标、卡片、图形、图表和文字区
- 不直接裁切低清原图，而是使用图像生成能力重绘高清素材
- 文字、数字、图例、标签默认去掉，后续用 PPT 文本框重建
- 一张图尽量只放一个元素，小图标可以生成 2x2 或 2x3 图标 sheet
- 输出结构化素材包，并附带 `manifest.json` 和 `process_notes.md`

## Repository Structure

```text
ppt-asset-regenerator-github/
  README.md
  LICENSE
  .gitignore
  ppt-asset-regenerator/
    SKILL.md
    agents/
      openai.yaml
    references/
      prompt-templates.md
  examples/
    README.md
```

真正需要安装的是 `ppt-asset-regenerator/` 这个子文件夹。

## Install

下载或克隆本仓库后，把 `ppt-asset-regenerator` 文件夹复制到你的 Codex skills 目录。

Windows:

```text
C:\Users\<你的用户名>\.codex\skills\ppt-asset-regenerator
```

macOS / Linux:

```text
~/.codex/skills/ppt-asset-regenerator
```

最终应该能看到：

```text
~/.codex/skills/ppt-asset-regenerator/SKILL.md
```

安装后，重启 Codex 或开启新会话。

## Usage

在 Codex 中上传一张 PPT 截图或页面图，然后输入：

```text
用 ppt-asset-regenerator 提取这张图片中的元素
```

也可以写得更明确：

```text
用 ppt-asset-regenerator 把这张 PPT 图片拆成高清可复用素材。文字不要保留，留出文字空间，方便后面在 PPT 里重新排版。
```

## Output

默认输出类似：

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
<img width="564" height="763" alt="20260519132901" src="https://github.com/user-attachments/assets/4fd7bde3-b38b-47be-b58c-e3245db968bb" />
<img width="1672" height="941" alt="p00_09_icon_marks_sheet" src="https://github.com/user-attachments/assets/bdea702b-ec56-4921-ba7d-159de1150cfe" />
<img width="1672" height="941" alt="p00_02_brush_marks_labels_tapes" src="https://github.com/user-attachments/assets/fa9f5371-39f2-41a9-95d9-f540e478be04" />

## Notes

- 这个 skill 依赖 Codex 的图像理解和图像生成能力。
- 它不是 OCR 转 PPT 工具，也不是直接裁切工具。
- 最佳用法是把图片里的视觉元素重绘成资产，再用 PPT 文本框和形状重建文字、图表和结构。
- 如果要生成完全可编辑 PPT，可以和 image2ppt 类 skill 或手工复排流程结合使用。

## License

MIT
