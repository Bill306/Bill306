# Anki Card Skills · 什么样的卡片值得留下？

[English](README.md) · **简体中文** · [返回 Bill 的主页](../../README.zh-CN.md) · [项目仓库](https://github.com/Bill306/anki-card-skills)

读完一份资料，是当下的事情。一个月之后还能记住，需要多花一点心思。

## 查看作品效果

1. **[浏览来源 PDF](https://github.com/Bill306/anki-card-skills/blob/main/examples/lumabox/lumabox-test.pdf)。** 仓库中的 LumaBox 教学示例共有四页，包含一页扫描页。资料中的教学对象为虚构内容，原文已有标注。
2. **[阅读卡片与对应证据](https://github.com/Bill306/anki-card-skills/blob/main/examples/lumabox/output/review.md)。** 每个问题都保留答案、PDF 物理页码和支持文字。末尾的知识点覆盖记录列出已包含、重复和资料无法回答的内容。
3. **[下载示例 Anki 牌组](https://github.com/Bill306/anki-card-skills/raw/refs/heads/main/examples/lumabox/output/deck.apkg)。** 下载 `.apkg` 后，通过 Anki「文件 → 导入」打开。示例包含 12 张卡片：10 张 Basic、2 张 Cloze，以及一张证据图片。

前面两项可以直接在 GitHub 查看。导入牌组需要 Anki；使用自己的 PDF 制卡，需要由 Agent 加载[已安装的 Skill](https://github.com/Bill306/anki-card-skills/blob/main/README.zh-CN.md#安装与调用)。

![通过仓库现有示例生成的卡片审阅页面](https://raw.githubusercontent.com/Bill306/anki-card-skills/main/docs/images/preview.png)

## 设计选择：让答案与证据保持在一起

**用户的问题。** 答案写得流畅，核对时仍然需要找到原文。修改复习材料时，学习者需要知道一张卡片依据哪一段资料。

**产品设计。** 每个答案保留来源文档、物理页码和证据。简短答案与补充解释分别展示。交付牌组时，同时保留可编辑的 `cards.json` 和审阅文档。

**带来的影响。** 用户在导入之前有明确的审阅步骤，修订卡片时也能够返回来源。审阅需要投入注意力，因此产品把核对所需的信息放在手边。

**怎样查看。** 打开示例中的任意卡片，再按照页码在来源 PDF 中核对内容。

## 设计选择：让资料缺口能够被看见

示例资料提供了一次写入速率测量，并明确说明最大吞吐量数值尚未提供。覆盖记录把这个缺失数值标记为 `blocked`，另外保留一张卡片说明测量结果与最大吞吐量之间的区别。导出记录使用 `PARTIAL_SOURCE_COVERAGE`，使资料缺口能够继续被看见。

完成一份牌组，也需要说明还有哪些问题等待补充来源。可以在[覆盖记录](https://github.com/Bill306/anki-card-skills/blob/main/examples/lumabox/output/audit.json)中查看这一条。

## 设计选择：修订牌组时保留卡片身份

稳定的 deck ID 与 card ID，使重新导出的 note 保持 GUID，帮助 Anki 在导入修订内容时匹配原有记录。验证文档记录了重复导入和答案更新；实际更新方式也受 Anki 导入设置与本地修改影响。

## 依据与当前范围

仓库中日期为 2026-10-20 的[验证记录](https://github.com/Bill306/anki-card-skills/blob/main/docs/verification.md)，记录了使用 Anki 官方后端进行的实际导入、12 个 notes/cards、媒体检查、重复导入和答案更新。这些结果支持现有示例的打包与导入行为。学习效果和独立学习者评估仍有待研究。

当前导出器支持 Basic、单空 Cloze 和图片辅助卡片。原生 Image Occlusion 尚未实现；扫描页阅读依赖执行 Agent 的能力。

[项目与安装说明](https://github.com/Bill306/anki-card-skills/blob/main/README.zh-CN.md) · [继续浏览其他作品](../../README.zh-CN.md#最近制作的东西)
