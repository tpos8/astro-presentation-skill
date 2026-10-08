# 天文学科研图表：投影重绘与科学可信度检查

## 通用原则

- 先确定科研含义、数据性质、坐标定义、统计模型、量纲，再绘制任何图像。
- `Axes`: 使用完整物理名称 + 单位，示例 `Time (BJD_TDB − 2457000)`、`Radial velocity (km s⁻¹)`、`Normalized flux`。不要默认各时间标签等价。
- `Data provenance`: 标注 survey/telescope, instrument, filter, sector/epoch, calibration and binning choices。图面过密则置页脚或 notes。
- `Uncertainty`: 使用与结论相关的 1σ、credible interval、上下限或置信区域，并解释定义；如果误差棒小于标记需在 notes 说明。
- 轴尺度不可具有误导性：重新定范围可能是为了突出变化，但不得隐藏零点、残差、峰值或系统误差以改变结果解读。
- 科研可视化主张优先：颜色、空间位置、误差、模型曲线都要有物理或统计定义；不做装饰性无意义映射。
- 真实天文图像可采用非自然色合成，但说明波段、色彩映射与增强方式；不能让公众误认为肉眼颜色。
- 绝不强制将所有数据平滑、去噪、去离群值；任何变换留审计记录。

## 高优先核对：时间系统与相位

- 需要确认：`JD / MJD / HJD / BJD`；`UTC / TDB / TT`；任务自定义 offset（如 BTJD、BKJD）的定义。
- 显示“相位折叠”时明确周期 P 与 T0 的物理定义、时间尺度。基本式 `phase = frac[(t − T0)/P]` 仅在适用常周期模型时使用。
- 如果存在 Pdot、O−C / timing model、apsidal effects，必须使用和分析一致的非线性 ephemeris；不能在图题中暗示常 P 模型。
- 双星光变中注意：光度主频与轨道频率可能相差 2 倍；`Pphot = Porb` 不能自动假定；需要专门确认约定。
- 多 sector 叠加：如有 sector baseline offset / normalization / dilution corrections，必须在 notes 和图注说明；不要把 per-sector nuisance 参数悄悄归入物理模型。

## 各领域推荐主图及检查

| 数据 | 最适合报告的图 | 必须保留的约定或疑点 |
|---|---|---|
| 光变 | raw/normalized light curve + folded curve + model residual | 时间定义、filter、质量清洗、周期、相位零点、binning |
| 周期搜索 | GLS/Lomb–Scargle periodogram | 频率/周期单位、alias/window、FAP 算法与 threshold、P 与 P/2 |
| SB1/SB2 RV | RV orbital phase + Keplerian curve + residual | systemic velocity γ、K、e、ω、T0、测量误差、仪器零点 |
| PHOEBE/ellc | observed-model-residual + geometry schematic | inclination、fill-out/filling factor、limb-darkening、third light、model assumptions |
| SED | flux density νFν or Fλ vs wavelength + band photometry | filter curves、dereddening、distance prior、zero points、upper limits |
| 谱图 | observed spectrum + model + residual | wavelength vacuum/air、rest frame vs observed、λ or ν、R、continuum normalized? |
| 射电干涉图 | synthesized image + beam + colorbar | RA/Dec direction and WCS、beam ellipse、Jy/beam、RMS/contours、dynamic range |
| ALMA spectral cube | channel maps / moment 0,1,2 / PV | Jy/beam km s⁻¹、beam、velocity frame、channel width、mask and clipping |
| 偏振/RM | Stokes Q/U/V / polarization / Faraday spectrum | angle conventions, units and uncertainties、RM sign conventions |
| X/γ-ray | counts/flux and folded model + data/model ratio | background、exposure、response ARF/RMF、binning statistic、energy units |
| 银河/宇宙学 | redshift / distance / parameter contours | cosmology assumed、fiducial priors、posterior credible regions、selection effects |
| 天文图像 | image + scale bar/beam/compass when relevant | instrument/bands、stretches、filter color mapping、north/east/WCS |

## 科学绘图实践

1. **重绘优先**：若有 FITS/CSV，保存绘图参数、清洗记录、代码和环境，原图可复现。
2. **简化不是删减证据**：可以减少次要曲线和多余坐标，但不得删去能推翻主结论的异常点、误差和统计限制。
3. **相位轴**：`Orbital phase`（通常 0–1 或 −0.5–0.5），明确 T0 对应合/凌的哪个事件；倍周期折叠时注明显示两周期的原因。
4. **亮度轴**：magnitudes 传统上更亮朝上（反向 magnitude 坐标），但 flux 应遵守数学直觉的正常方向；任何例外需清楚表明。
5. **多模型对比**：不要只强调 best-fit；还应考虑 residual、置信区间、模型退化和自由度，特别是光度推倾角/质量时。
6. **色标**：连续数据优先感知均匀色标；使用发散色标时零点/参考值应科学上可解释。`jet` 不建议作为无理由默认值。
7. **矢量与清晰度**：散点/线图优先 PDF/SVG 矢量保存；PPTX 兼容性不佳时用高像素透明 PNG。图像裁切前检查 legend、error bars、axes 是否完整。
8. **切勿默默截断**：对不同波段或仪器的数据，单位转换、系统误差、非同时性应在页脚或演讲中明确。
9. **关键定量结论**：显示有效数字与不确定性，例如 `P = (0.28789 ± 0.00002) d`（**数字仅为格式演示，非真实科研结果**）。实际必须读取来源。
10. **统计语言**：`detection`、`candidate`、`consistent with`、`upper limit`、`favored by model` 不可随意交换。双星隐形伴星不要仅凭低倾角解称为黑洞发现。

## 科研图的讲述结构

**图标题/视觉结论**：这张图说明了什么？

**观测证据**：哪些点、峰、误差、分组与趋势最相关？

**解释边界**：是否存在采样偏差、替代模型、退化、系统误差或选择效应？

辅助箭头与高亮只标注现有证据，不要添加没在数据中的“新物理结构”。

## 复现型图文件输出约定

- `figures/src/<name>.py`：生成代码。
- `figures/data/<name>...`：在权限允许时存原始/派生数据或可获取数据引用。
- `figures/vector/<name>.pdf` / `.svg`：可复用高清源。
- `figures/ppt/<name>.png`：透明/白底高分辨率展示图。
- `figures/README.md`：每幅图数据来源、单位、变换、版本及图使用范围。
