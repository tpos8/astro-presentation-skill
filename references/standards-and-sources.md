# 官方依据与来源索引（校验日：2026-10-08）

> 区分 **官方要求/公开建议**、**网页可访问性参考基准** 和 **本 Skill 自定设计规范**。会议最终规则以 *当届会议* 网站为准。以下页面会变化，使用时如有网络访问，重新核实。

## A. 天文学会议相关

1. AAS Speaker Ready and Audiovisual Information (official): https://aas.org/meetings/av-information
   - AAS 要求报告 16:9；建议在现场 speaker-ready room 试播；支持具体软件依会场列示。
2. AAS Meeting Sessions & Content (official): https://aas.org/meetings/aas-meeting-sessions-content
   - 常规 oral 时间分配 5min talk + 3min Q&A + 2min transition；Dissertation 15+3+2；常规口头报告约 3–5 页 visual aid。**仅代表该 AAS 页面当前描述，不应强推给其他会议**。
3. AAS 248 Session Chairs (2026): https://aas.org/meetings/aas248/session-chairs
   - 2026 AAS 248 同样列出上述 regular / dissertation 时长及 invited 40+10 形式，special session 另定。
4. IAU General Assembly 2024 presenter instructions: https://astronomy2024.org/instructions-for-oral-talk-presenters-and-poster-authors/
   - 该届接受 PPT/PDF，不接受 Keynote；明确强调准时及演讲播放检查。**历史案例，不能当成所有 IAU 会议的普遍规定**。

## B. 图片、无障碍与可读性

5. W3C WAI Accessible Presentations: https://www.w3.org/WAI/teach-advocate/accessible-presentations/
   - 控制每页文字、字体清晰、大型重要视觉、足够对比度、慎用动画。
6. W3C WCAG 2.1 Contrast (Minimum): https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum
   - 网页 AA 对比度：普通文字 4.5:1、大文字 3:1。用于幻灯片为**合理参考目标**，不是“所有 PPT 必须符合 WCAG”的主办方要求。
7. Microsoft PowerPoint Accessibility: https://support.microsoft.com/en-us/accessibility/powerpoint/make-your-powerpoint-presentations-accessible-to-people-with-disabilities
   - 建议 18pt 或更大无衬线字体、图像 alt text、唯一标题、逻辑阅读顺序、对比度检查。

## C. 科学图形与数据忠实度

8. AAS Journals Graphics Guide: https://journals.aas.org/graphics-guide/
   - 字型/线宽一致；形状或线型作为颜色的补充；**其中印刷稿 6pt 下限与 0.5pt 线宽不是投影设计适用阈值**。
9. AAS Manuscript Preparation: https://journals.aas.org/manuscript-preparation/
   - 多 panel、line styles、符号及图例说明清晰。
10. AAS Journal Style Guide: https://journals.aas.org/aas-style-guide/
    - 科学术语、缩写等规范是重要参考，不等同 PPT 的外观强制要求。
11. Crameri, F. et al., Nature Communications (2020), The misuse of colour in science communication, DOI 10.1038/s41467-020-19160-7: https://www.nature.com/articles/s41467-020-19160-7
    - 使用感知均匀色标，避免 `jet` 等误导性彩虹色标。
12. Nature Methods / Nature (accessible science figures): https://www.nature.com/articles/d41586-021-02696-z
    - 红绿不可作为唯一辨别维度，试做灰度检查。

## D. 文献与图片信用

13. NASA ADS Direct Access: https://www.adsabs.harvard.edu/abs_doc/help_pages/linking.html
    - 以 ADS bibcode 链接具体文章；用正式出版元数据核对引文。
14. ADS BibTeX: https://ads.harvard.edu/pubs/bibtex/
    - ADS 引用导出；符合 AASTeX 等天文学期刊生态。
15. NASA Images & Media Guidelines: https://www.nasa.gov/nasa-brand-center/images-and-media/
    - NASA 内容一般可用于教育/信息目的，需遵守其媒体规则；**NASA 徽章与标识受保护**，可能有第三方版权。
16. ESA/Hubble image policy: https://esahubble.org/copyright/
    - 网站图片通常 CC BY 4.0，完整可见的图片 credit 非常重要，受例外限制。
17. ESO copyright: https://www.eso.org/public/copyright/
    - 公共页面媒体通常 CC BY 4.0，使用时保留完整 credit 并检查例外。

## E. Agent Skill 格式

18. Agent Skills specification: https://agentskills.io/specification
19. OpenAI Skills documentation: https://developers.openai.com/api/docs/guides/tools-skills

以上可直接用于科研报告制作技能的溯源；请勿为了权威性杜撰不存在的“IAU PPT 字号标准”“AAS 每页字数规定”。
