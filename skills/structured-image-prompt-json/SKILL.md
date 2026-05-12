---
name: structured-image-prompt-json
description: |
  为图像生成模型编写高质量、结构化、可参数化的 JSON 提示词。适用于 illustrated map infographic、travel/food map、field guide、technical illustration、exploded view product diagram、产品分解海报、多模块信息图和需要精确版式约束的视觉任务。
  当用户要求“写成 json 提示词”“结构化提示词”“地图信息图提示词”“爆炸图提示词”“技术示意图提示词”“把提示词内化成 skill”时使用。
---

# Structured Image Prompt JSON

这个 skill 的目标不是把自然语言简单包成 JSON，而是把复杂视觉任务改写成“模型更容易执行的布局合同”。

## 适用场景

- 插画地图、旅游地图、美食地图、路线图、景区导览图
- 产品爆炸图、拆解海报、技术结构图、工业设计说明板
- 多模块信息图、字段较多的海报、需要稳定文字区域的版式

## 核心原则

1. 先定义 `type` 和画面用途，不要一上来堆细节。
2. 把提示词拆成固定区域：标题、主体、模块、图例、页脚。
3. 对每个区域同时约束“内容”与“布局关系”。
4. 文字多时优先短标签，不要大段正文。
5. 明确哪些元素必须出现，哪些只作风格装饰。
6. 对地图类写清道路/河流/绿地/图例系统；对爆炸图写清层数、层序、间距、标注数量。
7. 增加 `negative_prompt`，明确禁止杂乱小字、假 logo、额外 UI、透视混乱、结构错位。

## 推荐 JSON 骨架

```json
{
  "type": "artifact category",
  "goal": "what this image is for",
  "style": "visual direction",
  "canvas": {
    "aspect_ratio": "3:4",
    "orientation": "vertical",
    "resolution_hint": "high"
  },
  "header": {},
  "layout": {
    "centerpiece": "",
    "sections": []
  },
  "text_rules": [],
  "negative_prompt": "",
  "quality_notes": []
}
```

## 地图信息图写法

- `type` 明确写 `illustrated map infographic`
- `style` 同时写媒介和材质，例如 `watercolor and ink hand-drawn illustration on vintage parchment`
- `layout.background` 要写地图底图语言：道路、河流、绿地、底纸
- `sections` 至少分成地标、美食点、图例三层
- 地图的 `labels` 要短，尽量 2 到 10 字
- `centerpiece` 给一个强记忆点角色或城市吉祥物
- `bottom_right_extras` 常放指南针、免责声明、路线说明

## 爆炸图海报写法

- `type` 明确写 `exploded view product diagram poster`
- `subject` 写具体产品
- `layout.centerpiece` 必须写层数、分层方向、关键部件
- `callout_labels` 分左右两栏，减少交叉引线
- `footer` 放一句结论性品牌文案，不要再塞新信息
- 如要更稳定，写明 `orthographic product visualization`, `precise spacing`, `clean leader lines`

## 输出要求

输出时优先给用户：

1. 最终 JSON
2. 一个更强的 `negative_prompt`
3. 如果适用，再给一个“极简版 JSON”

## 参考文件

- 需要外部项目与方法论时，读 `references/source-notes.md`
- 需要直接套模板时，读：
  - `templates/illustrated-map-infographic.json`
  - `templates/exploded-vr-headset-poster.json`
