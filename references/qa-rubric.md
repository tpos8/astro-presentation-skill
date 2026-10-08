# PPTX 科研报告质量门禁与 QA Rubric

## A. 强制 FAIL（不允许以“设计优秀”抵消）

- [ ] 定量结果无真实数据/可信来源支撑，或引用与研究不匹配。
- [ ] 科学对象、周期、误差、单位、时间系统、频率/轨道频率等关键信息有错误。
- [ ] “candidate / upper limit / plausible / model-dependent”被夸大为 confirmed detection。
- [ ] 对观测拟合值做无披露改动；数据平滑/剪裁/误差删除改写科学含义。
- [ ] 主结论页面图表看不清、被遮挡、越界、被裁断，或源图与标题不相符。
- [ ] 未经过全页渲染就宣称视觉已完整检查（若无能力渲染，必须明确标注未通过此项）。
- [ ] 侵犯图像许可/删除要求完整 credit 的外部资料标注。
- [ ] 主办方明确要求格式或比例，但交付物不满足且没有说明。

## B. 评分：满分 100（建议 ≥ 90 优秀，≥ 80 可用）

| 维度 | 权重 | 主要审查 |
|---|---:|---|
| 科学可信度与文献溯源 | 30 | 数据匹配、误差/条件、ADS/DOI、证据链 |
| 叙事逻辑 | 20 | 问题/方法/证据/意义链条、一页一结论 |
| 图表专业性 | 20 | 坐标、量纲、色标、曲线/残差、可辨认性 |
| 视觉与可访问性 | 15 | 字号、配色对比、留白、对齐、alt text |
| 演讲时长与表演友好度 | 10 | 时间预算、speaker notes、过渡与 backup |
| 交付物兼容性 | 5 | PPTX/PDF、显示及媒体播放、文件链接 |

## C. 自动检查脚本能做什么

`scripts/check_pptx.py` 识别：

- 幻灯片比例与数量；
- 对象（尤其是表框、文本、图像）越界；
- 非封面的空白或几乎空白页面；
- 明确指定的正文过小字号（无法可靠解析继承字号时标为 info）；
- 页内文字过密；
- 纯图像没有 alt text；
- 在没有背景形状叠加时，直接背景/文字的简单对比度；
- 图片和文本过量的启发式提示。

此脚本 **不可能** 检查：画面实际清晰度、科学真实性、轴标签（嵌入图像）、公式正确性、复杂图层遮挡、文本框内部的真实文本溢出、具体会议时间、动画是否合理。必须搭配全页渲染和科研审查。

## D. 视觉逐页核对

- [ ] 小缩略图能看出每页只有一个信息中心。
- [ ] 1080p 全屏、模拟坐后排，轴名/图例/误差/标记清晰。
- [ ] 标题言之有据，引用没有被挤掉。
- [ ] 图中的颜色不是唯一的对比编码。
- [ ] 公式、希腊字母、符号、上下标、负号没有乱码。
- [ ] 光谱、光变、RV、频谱等不同图的单位和标注彼此统一。
- [ ] 图里放大的区间、归一化、offset、binning 被披露。
- [ ] 重要的 slide 不只靠动画某一帧才能理解。
- [ ] 主报告计时不超过时长；backup 不占正式主线时间。

## E. 推荐的 qa-report.md 结构

```markdown
# QA Report
Date:
Venue/assumed format:
Deck length:
Talk time (excluding Q&A):

## Hard-fail
- [ ] No unresolved hard-fail

## Automated checks
- Command:
- Warnings:
- Errors:

## Scientific traceability
- Claim -> slide -> source -> verified? -> limitation

## Visual inspection
- Render method:
- Slides inspected:
- Issues fixed:

## Accessibility
- Contrast, font, reading order and alt-text status

## Unverified / exceptions
- List any restrictions, missing raw data, or rights not verified
```
