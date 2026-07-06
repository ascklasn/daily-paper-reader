---
title: "MCD Stitcher: An open-source tool for whole-slide stitching and conversion of Imaging Mass Cytometry data"
title_zh: MCD Stitcher：用于全切片拼接和成像质谱流式数据转换的开源工具
authors: "Chaurasia, P."
date: 2026-07-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.26.732348v1.full.pdf"
tags: ["query:spatialprot"]
score: 9.0
evidence: 用于成像质谱流式全切片拼接的开源工具
tldr: 成像质谱流式(IMC)单次采集区域有限，大片组织需多ROI拼接，但.mcd专有格式阻碍分析流程。MCD Stitcher作为开源Python包，可将.mcd文件转换为OME-TIFF并自动拼接全切片。它支持矩形/多边形ROI、变像素尺寸、内存感知分块读取大数集，输出保留空间、通道和元数据。该工具提供了可重复的工作流，摆脱厂商软件依赖，便于在QuPath等工具中进行全切片空间分析。
source: biorxiv
selection_source: fresh_fetch
motivation: 解决IMC数据因.mcd专有格式和多ROI拼接困难，难以整合到标准生物图像分析流程的问题。
method: 开发MCD Stitcher Python包，分块读取.mcd文件，自动拼接矩形/多边形ROI并生成OME-TIFF格式，支持变像素尺寸和内存优化。
result: 输出包含完整元数据的OME-TIFF图像，可直接用于QuPath、napari等工具，实现全切片空间分析。
conclusion: MCD Stitcher提供了可重复的原始IMC数据转换工作流，无需厂商软件即可进行全切片空间分析。
---

## 摘要
成像质谱流式技术（IMC）将金属标记抗体与激光消融质谱结合，生成组织切片的高多重空间图像。然而，单个感兴趣区域（ROI）内可采集的面积受硬件和软件限制，因此需要将大组织成像为多个拼接的ROI。将这些ROI重建为全切片图像需要额外的处理，而专有的.mcd文件格式可能阻碍其与标准生物图像分析工作流程的整合。

在此，我们介绍MCD Stitcher，这是一个开源的Python包，用于将.mcd文件转换为OME-TIFF图像并进行自动全切片拼接。该工具支持矩形和多边形ROI，适应ROI之间不同的像素大小，并在数据摄取时使用内存感知的分块读取，以在标准工作站上处理大型数据集。生成的OME-TIFF输出保留了空间、通道和采集元数据，可用于QuPath、napari和ImageJ/Fiji等工具中的下游分析。

MCD Stitcher提供了一个可重复的工作流程，将原始IMC数据转换为可互操作的图像格式，从而无需依赖供应商特定软件即可实现全切片空间分析。

## Abstract
Imaging Mass Cytometry (IMC) combines metal-tagged antibody labelling with laser ablation mass spectrometry to generate highly multiplexed spatial images of tissue sections. However, the area that can be acquired within a single region of interest (ROI) is limited by hardware and software constraints, requiring large tissues to be imaged as multiple tiled ROIs. Reconstructing these ROIs into whole-slide images requires additional processing, while the proprietary .mcd file format can hinder integration with standard bioimage analysis workflows.

Here, we present MCD Stitcher, an open-source Python package for converting .mcd files into OME-TIFF images with automated whole-slide stitching. The tool supports rectangular and polygonal ROIs, accommodates variable pixel sizes between ROIs, and uses memory-aware chunked reading during data ingestion to process large datasets on standard workstations. The generated OME-TIFF outputs preserve spatial, channel, and acquisition metadata for downstream analysis in tools such as QuPath, napari, and ImageJ/Fiji.

MCD Stitcher provides a reproducible workflow for converting raw IMC data into interoperable image formats, enabling whole-slide spatial analysis without reliance on vendor-specific software.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：成像质谱流式（IMC）技术能够同时检测组织切片上40多种蛋白标志物，但单个感兴趣区域（ROI）的采集面积受硬件（如激光扫描范围、内存、软件稳定性）限制，大组织必须分割为多个相邻或部分重叠的ROI进行采集。由此产生两个障碍：(1) 将多个ROI重建为全切片图像需要额外处理；(2) Standard BioTools 的专有 .mcd 文件格式难以直接整合到标准开源生物图像分析工具（如 QuPath、napari、ImageJ/Fiji）中。现有开源工具（如 imctools、steinbock、readimc）仅支持单个 ROI/采集的格式转换，缺乏全切片自动拼接功能，尤其当 ROI 为多边形或像素尺寸不同时更显不足。
- **整体含义**：为实现 IMG 数据的 FAIR（可发现、可访问、可互操作、可复用）原则和规模化空间分析，需要一种开放、可重复的工具，能从原始 .mcd 文件直接生成兼容标准格式（如 OME-TIFF）的全切片图像，同时保留空间坐标、通道标签、元数据等关键信息。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：开发一个名为 MCD Stitcher 的开源 Python 包，基于 readimc 库读取 .mcd 文件，提供四个命令行工具（或一个综合命令 `mcd_process`）实现：
  - `mcd_stitch`（或 `--stitch`）：全切片拼接，将多个 ROI 合成一幅大的 OME-TIFF 图像。
  - `mcd_convert`（或 `--convert`）：逐个 ROI 转换为独立的 OME-TIFF。
  - 全景图导出与 ROI 映射（`--panorama` 和 `--roi_map`）：将仪器采集的预览全景图导出为 PNG，并在图上绘制 ROI 轮廓，同时生成 ROI 坐标与全景像素坐标的映射文本文件。
  - `tiff_subset`（或 `--filter` 和 `--pyramid`）：通道过滤、压缩、生成金字塔（多分辨率）OME-TIFF。

- **关键技术细节**：
  - **内存感知处理**：数据读取采用分块策略，每块最多 50,000 像素（每个像素包含 X、Y 坐标和各通道强度值），逐块写入采集图像数组后再读取下一块，从而将解析时的峰值内存控制在较低水平。拼接时，每个 ROI 被读取、缩放（若需）、掩膜（多边形 ROI）、合成到全局画布后立即释放，进一步节省内存。
  - **支持多边形 ROI**：通过 ROI 特定掩膜（mask）排除非采集区域外的伪影。
  - **支持可变像素尺寸**：当不同 ROI 的像素大小不同时，采用双线性插值统一缩放到全局公共像素尺寸。
  - **数据验证与恢复**：检查每个采集的存储数据大小是否为每像素记录大小的整数倍；若发现截断或损坏数据，自动进入恢复模式，丢弃不完整像素。
  - **输出格式**：均为 OME-TIFF（16-bit 无符号整数或 32-bit 浮点），可选 LZW 或 zstd 压缩，嵌入 OME-XML 元数据（物理像素尺寸、通道标签、ROI 坐标、采集时间等）。

- **算法流程（文字描述）**：
  1. 输入：一个或多个 .mcd 文件。
  2. 读入文件结构，提取所有 ROI 的坐标、像素大小、时间戳、通道标签等元数据。
  3. 根据选择的操作（拼接/转换等）进行处理。拼接流程：
     - 计算所有选中 ROI 的包围盒（bounding box），确定全局画布大小。
     - 逐 ROI 读入像素数据（分块），若需则双线性插值缩放，应用多边形掩膜，按照记录坐标放置到全局画布相应位置，写入 OME-TIFF。
     - 写入时保留完整 OME-XML 元数据。
  4. 输出：全拼接的 OME-TIFF（或每个 ROI 独立的 OME-TIFF）。

## 3. 实验设计：数据集、场景、基准测试与方法对比

- **数据集**：使用来自 Standard BioTools XTi 系统的代表性 tiled IMC 采集，包含 8 个部分重叠的 ROI，36 个标志物通道，像素尺寸 1 μm。组织为一块组织核心（tissue core）。未提供具体的肿瘤类型或来源（仅提到可向作者索取，受机构数据共享协议约束）。
- **场景**：全切片拼接演示，展示重建后连续组织架构和单细胞级分辨率保持情况（图2）。
- **基准测试（benchmark）**：无。论文未设立量化指标（如拼接精度、速度、内存峰值对比等），也未与其他拼接工具（如基于特征配准的方法）进行正式比较。仅限于功能演示与定性展示。
- **方法对比**：论文指出现有开源工具（imctools, steinbock, readimc, napari-imc）只能处理单个 ROI 的格式转换，无法自动拼接全切片；MCD Stitcher 填补了这一空白。但未进行定量对比实验。

## 4. 资源与算力

- **未明确说明**：论文提及 MCD Stitcher 可在标准工作站上运行，分块读取降低了内存需求，但未说明具体硬件配置（CPU、内存、GPU 等），也未给出运行时间、峰值内存等测量数据。未涉及 GPU 训练（IMC 数据无需模型训练，仅预处理）。

## 5. 实验数量与充分性

- **实验数量**：仅有一个演示数据集（8 个 ROI，36 通道，1 μm 像素）。功能上展示了拼接、通道过滤、金字塔生成等，但未进行多数据集、多种 ROI 数量/形状/像素尺寸的系统性测试。
- **充分性评估**：实验覆盖有限。
  - **优点**：演示了核心功能（拼接后组织连续、单细胞分辨率保持），验证了工具的基本可行性。
  - **不足**：
    - 缺乏定量评价指标（如拼接精度、重叠区域一致性、亮度/对比度差异、内存/时间基准）。
    - 未测试大 ROI 数量（>10）或大组织面积（接近或超过 1 cm²）的场景。
    - 未测试多边形 ROI 的实际表现（仅文字提到支持）。
    - 未与基于图像配准的方法（如 Kim et al., Cell Rep Methods 2023 提到的 IMC-IF 配准）对比。
    - 未进行鲁棒性测试（如损坏的 .mcd 文件自动恢复）。
  - 总体而言，实验偏弱，但作为工具介绍性论文可以接受。若要进行更严格的方法验证，需要补充更多数据集和量化评估。

## 6. 论文的主要结论与发现

- MCD Stitcher 成功实现了从 .mcd 文件到 OME-TIFF 的自动化转换与全切片拼接，支持多边形 ROI 及混合像素尺寸。
- 输出图像可直接在 QuPath、napari、ImageJ/Fiji 等主流生物图像分析平台中打开，保留完整元数据。
- 演示案例中，8 个 ROI 拼接为 5,105 × 7,074 像素（36.1 百万像素）的大图像，组织连续，单细胞分辨率保持良好。
- 该工具可消除对厂商特定软件的依赖，提升 IMC 数据的可重复性和可移植性，尤其适用于需要全切片空间分析的肿瘤微环境研究。

## 7. 优点

- **填补空白**：是第一个专门用于 IMC 多 ROI 全切片拼接的开源工具，解决了一个实际痛点。
- **兼容性强**：输出 OME-TIFF 格式，被广泛支持，嵌入的 OME-XML 保留了丰富的元数据。
- **功能全面**：单个工具集成了格式转换、拼接、全景图映射、通道过滤、金字塔生成，无需多个工具组合。
- **内存优化**：分块读取与流式写入设计使其能在普通工作站上处理较大数据集（虽有大面积限制）。
- **支持异构 ROI**：多边形 ROI 和可变像素尺寸是现有 IMC 工具中独有的功能。
- **开放与可再现**：GPL v3 许可，源代码、文档、示例均在 GitHub 公开，支持 Python 3.9-3.13。

## 8. 不足与局限

- **平台局限**：仅支持 Standard BioTools（Hyperion, Hyperion Plus, XTi）的 .mcd 格式，不支持其他 multiplexed 成像平台（如 CODEX, Xenium, CosMx）。
- **拼接假设**：假设所有 ROI 位于同一组织坐标空间，不执行跨切片配准。
- **内存限制**：虽然读取时分块，但拼接时整个画布仍需驻留在内存中。对于超过约 1 cm × 1 cm 的大面积（多于单一 ROI 名义上限）可能内存不足，论文建议采用逐个 ROI 转换或分割重建。
- **缺乏智能拼接优化**：未实现重叠区域自动检测、接缝融合、强度归一化。若相邻 ROI 因激光功率漂移或染色不均存在强度差异，接缝可能可见。
- **实验验证不足**：如前所述，缺乏量化基准和更多数据集测试。
- **代码版本**：论文声称描述的是版本 2.3.0，但未详细说明版本历史或与其他版本的区别。
- **算力/性能数据缺失**：没有提供运行时间或内存消耗的典型值，用户难以预估部署需求。

（完）
