# Source Notes

这份参考只保留对当前 skill 真正有用的外部项目与结论。

## Related Projects

1. `wuyoscar/gpt_image_2_skill`
   - GitHub: https://github.com/wuyoscar/gpt_image_2_skill
   - 价值：把图像提示词做成可检索的分类图库，尤其适合 infographics、wayfinding map、technical illustration。

2. OpenAI Cookbook image prompting guidance
   - 文档入口：https://cookbook.openai.com/
   - 价值：强调结构化提示、复杂图文场景使用高质量输出、把“什么要变/什么不能变”写清楚。

3. OpenAI skills repository
   - GitHub: https://github.com/openai/skills
   - 价值：提供 skill 的基本组织方式，适合把本地提示词能力沉淀成可重复调用的模块。

## Practical Takeaways

### For map infographics

- 把“地图”当成一个布局系统，不只是插画。
- 明确道路、河流、公园、图例、地标、编号点位。
- 中文文字多时使用短词标签，不要写说明段落。

### For exploded product posters

- 先规定分层顺序，再写材质与灯光。
- 标注数控制在 6 到 10 个，过多会降低稳定性。
- 用左右两侧 callout 分栏，减少标注线互相穿插。
- 写明 `clean high-tech 3D render`, `orthographic feel`, `precise spacing`, `industrial design board` 能明显提升结构服从度。

## Local Reference Hints

你的本地仓库里已经有强相关示例：

- `gpt_image_2_skill/skills/gpt-image/references/gallery-events-and-experience.md`
  - 含导览地图、景区地图
- `gpt_image_2_skill/skills/gpt-image/references/gallery-technical-illustration.md`
  - 含手表、键盘、手机爆炸图
- `gpt_image_2_skill/skills/gpt-image/references/craft.md`
  - 强调 fixed-region schemas 和复杂信息图的布局合同写法
