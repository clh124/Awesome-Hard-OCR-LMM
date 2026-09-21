# Awesome-Hard-OCR-LLM

<p align="center">
  <a href="./README.md">English</a> | <strong>简体中文</strong>
</p>

<p align="center">
  <a href="https://awesome.re"><img src="https://awesome.re/badge.svg" alt="Awesome"></a>
  <a href="#"><img src="https://img.shields.io/badge/TOPIC-HARD--OCR-blue.svg" alt="TOPIC"></a>
  <a href="#"><img src="https://img.shields.io/badge/SCOPE-2023%2B%20MLLM%2FVLM-orange.svg" alt="SCOPE"></a>
  <a href="#"><img src="https://img.shields.io/badge/CONTRIBUTIONS-WELCOME-brightgreen.svg" alt="CONTRIBUTIONS"></a>
</p>

<p align="center">
  <img src="./poster_ch.png" alt="大模型困难文本识别总览" width="100%">
</p>

本仓库整理 **大多模态模型（MLLMs）** 与 **视觉语言模型（VLMs）** 时代下，关于 **困难 OCR 识别** 与 **OCR 中心视觉理解** 的近期研究。

不同于通用 OCR、文档智能或宽泛的 MLLM benchmark 列表，本合集关注真正难以读懂图中文字的场景：退化和真实世界图像、密集或小文本、复杂文档结构、多语种和历史文字、手写、隐藏文本，以及合成/对抗视觉文本。本列表主要覆盖 **2023 年以来**的工作，因为这一时期 MLLM/VLM 驱动的 OCR 与富文本视觉理解开始成为一个相对独立的研究方向。

🚀🚀🚀 欢迎贡献。如果你发现遗漏的论文、benchmark 或 challenge，请提交 issue，并附上标题、链接、venue/year，以及简短说明为什么它符合 hard OCR 的范围。

---

<a id="contents"></a>

<!-- UPDATE_LOG_START -->
## 📰 更新日志

- **[2026-09-21]** 新增 98 篇(47 个 benchmark/数据集、51 篇方法论文),覆盖 5 个章节:📊 Benchmarks 与数据集 +47、🌍 退化与真实世界 OCR +12、📄 复杂文档与结构化 OCR +70、✍️ 脚本多样、历史与手写 OCR +29、🧪 合成、隐藏与对抗 Hard OCR +6
- **[2026-09-16]** 新增 24 篇(19 个 benchmark/数据集、5 篇方法论文),覆盖 6 个章节:📊 Benchmarks 与数据集 +5、🌍 退化与真实世界 OCR +2、📄 复杂文档与结构化 OCR +8、✍️ 脚本多样、历史与手写 OCR +5、🧪 合成、隐藏与对抗 Hard OCR +1、🏆 竞赛 +14
- **[2026-09-09]** 新增 10 篇(3 个 benchmark/数据集、7 篇方法论文),覆盖 3 个章节:📊 Benchmarks 与数据集 +3、🌍 退化与真实世界 OCR +3、📄 复杂文档与结构化 OCR +4

*标 🆕 的条目为本次更新新增。*
<!-- UPDATE_LOG_END -->

## 目录

- [介绍](#introduction)
- [Benchmarks 与数据集](#benchmarks-datasets)
- [研究论文](#research-papers)
  - [退化与真实世界 OCR](#degraded-and-in-the-wild-ocr)
  - [复杂文档与结构化 OCR](#complex-document-and-structured-ocr)
  - [脚本多样、历史与手写 OCR](#script-diverse-historical-and-handwritten-ocr)
  - [合成、隐藏与对抗 OCR](#synthetic-hidden-and-adversarial-hard-ocr)
- [竞赛](#competitions)
- [联系我们](#contact-us)

---

<a id="introduction"></a>

## ✨ 介绍

**Hard OCR** 指的是在具有视觉、语言、结构或合成难度条件下的 OCR 识别或 OCR 中心理解任务。本仓库的目标是追踪那些 OCR 不只是预处理步骤，而是多模态感知与推理核心瓶颈的研究工作。

### 🧭 分类体系

所有 **benchmarks 和数据集** 统一放在 **Benchmarks 与数据集** 中。**研究论文** 下的四个子章节只包含模型、方法或系统论文，不包含单独的 benchmark 条目。

| 类别 | 包含 | 不包含 |
|---|---|---|
| Benchmarks 与数据集 | OCR 中心 hard benchmark | 通用 MLLM benchmark |
| 退化与真实世界 OCR | 真实世界视觉难度：模糊、低分辨率、噪声、压缩、弱光、屏幕拍摄、扫描伪影、倾斜、遮挡、缺失文本、小文本或密集文本、复杂场景上下文 | 干净、清晰、容易图像上的普通场景文字识别 |
| 复杂文档与结构化 OCR | 结构性文档难度：版面与阅读顺序、表格、公式、图表、多页上下文、KIE、grounding 或关系抽取，以及忠实的 Markdown/HTML/LaTeX/JSON 风格输出 | 不显式处理结构挑战的普通 clean PDF-to-text OCR |
| 脚本多样、历史与手写 OCR | 脚本、书写风格或历史域偏移：低资源或非拉丁脚本、脚本特定正字法复杂性、历史或古代文档、书法、手写、手写公式、稀有脚本解读 | 高资源脚本中的普通现代印刷体 OCR |
| 合成、隐藏与对抗 Hard OCR | 合成、隐藏、错觉式、对抗或被篡改的视觉文本，其中识别、定位或鲁棒解释文本是核心 | 不显式评估 OCR/文本阅读的通用 VLM 攻击、jailbreak、宽泛 AIGC 风险检测或合成图像生成 |

---

### 🏷️ 交叉标签

一篇论文可能拥有多个标签，因为 hard OCR 的困难因素经常相互重叠。标签按其描述论文的作用进行分组。

| 分组 | 标签 | 含义 |
|---|---|---|
| 核心任务 | `recognition`, `localization` | 直接文本转录、字符/词识别、文本检测、grounding 或区域级 OCR。 |
| OCR 中心理解 | `reasoning`, `text-rich-vqa`, `document-qa`, `translation`, `KIE` | 依赖视觉文本的下游理解任务，包括基于 OCR 线索的推理、富文本图像或文档 VQA、跨语言 OCR/翻译，以及关键信息抽取。 |
| 视觉难度 | `degraded`, `occlusion`, `dense-text`, `high-resolution`, `scene-text`, `in-the-wild` | 困难视觉条件，如模糊、噪声、低分辨率、压缩、扫描伪影、遮挡或不完整文本、小/密集文本、高分辨率输入和真实世界场景文字。 |
| 文档结构 | `layout`, `structured-output`, `table/chart`, `table`, `formula`, `multi-page`, `long-context` | 页面结构和结构化转换，包括阅读顺序、多栏版面、Markdown/HTML/LaTeX/JSON 风格输出、表格、图表、公式、多页文档和长文本上下文。 |
| 语言与脚本 | `multilingual`, `low-resource`, `script-diverse`, `historical`, `handwriting` | 语言、脚本和书写风格偏移，包括多语种 OCR、低资源脚本、稀有脚本、历史文档、旧字体、书法和手写。 |
| 合成或对抗文本 | `synthetic-hard`, `hidden/adversarial` | 合成或 AIGC 创建的 hard OCR 样本、隐藏或错觉文本、对抗视觉文本，以及被篡改的视觉文本伪影。 |

[[⬆️ 返回顶部](#contents)]

---

<a id="benchmarks-datasets"></a>

## 📊 Benchmarks 与数据集

| Benchmark | 论文 | Venue & Year | 亮点 | 标签 | 下载 |
|---|---|---|---|---|---|
| DocAttriBench 🆕 | [DocAttriBench](https://arxiv.org/abs/2609.20574v1) | arXiv 2026 | 文档 VQA 缺少把答案归因到版面要素的细粒度标注。作者提出 MAPPET,通过遮蔽候选要素并度量困惑度上升来归因答案,构建含 237k 文档、296k QA 的 DocAttriBench 基准。评测显示可 grounding 的 MLLM 常答对却定位错,揭示答案与归因间的差距。 | `document-qa`, `text-rich-vqa`, `layout` | N/A |
| Tables Decoded (DELTA/TARQA) 🆕 | [Tables Decoded (DELTA/TARQA)](https://arxiv.org/abs/2609.17458v1) | arXiv 2026 | 现有表格 VLM 将结构与内容耦合,多语言难扩展。DELTA 把物理/逻辑结构与 OCR 解耦,输出紧凑的 OTSL;TARQA 在 OTSL 上微调 LLM 做 TabVQA。发布 SOTA TSR 模型、印地语基准 TORQUE,并在 WTQ/FinTabNetQA 上大幅提升。 | `table`, `structured-output`, `multilingual` | [GitHub](https://github.com/Tihiitborg/Tables-Decoded) |
| SA-DBNet 🆕 | [SA-DBNet](https://arxiv.org/abs/2609.13815v1) | arXiv 2026 | 真实场景退化(模糊、低分辨率、压缩)下文本VQA研究不足。作者构建4013图/7000问答对的退化基准,对比模块化OCR流水线(SA-DBNet检测器)与端到端Qwen2-VL。微调后模块化流水线准确率57.50%对38.00%;CER/WER不能可靠预测VQA效果。 | `recognition`, `degraded`, `text-rich-vqa` | [GitHub](https://github.com/RitaliVatsi/VQA_Project) |
| VectorHarness 🆕 | [VectorHarness](https://arxiv.org/abs/2609.13294v1) | arXiv 2026 | 科学图形难以编辑,已有image-to-code方法只复制像素而未恢复可编辑结构。VectorHarness提出类型化语义授权表示,多智能体恢复文本、公式、图表与表格;发布VectorHarness-Bench,提升可执行编辑与关系保持能力。 | `structured-output`, `table/chart`, `formula` | N/A |
| DocHop 🆕 | [DocHop](https://arxiv.org/abs/2609.02059v1) | arXiv 2026 | 现有基准将图表与文档割裂评测。DocHop 用逻辑优先管线构造 2,074 条样本,由叙述给约束、图表给数值,要求跨六类任务做联合多跳推理。最优 MLLM 仅 62.83%,人类超 90%,差距显著。 | `reasoning`, `table/chart`, `document-qa` | N/A |
| VeriOCRBench 🆕 | [VeriOCRBench](https://arxiv.org/abs/2609.00232v1) | arXiv 2026 | 现有 OCR 评测默认任务均可答,但真实图像常有模糊、遮挡、矛盾证据。VeriOCRBench 形式化 OCR 任务可验性(IP,TP,Q),发布 1800 条人工校验样本,含 8 类陷阱×4 校验维度共 1600 条无效任务及 200 条对照,评测 15 个 MLLM 揭示出普遍盲目顺从、诊断失误与诱导式过度拒绝问题。 | `reasoning`, `document-qa`, `degraded` | [GitHub](https://github.com/zy001122/Beyond-Blind-Compliance) |
| OCR-MetaReasoning 🆕 | [OCR-MetaReasoning](https://arxiv.org/abs/2608.30678v1) | arXiv 2026 | 文本富图像理解常将抽取与推理混淆,且不区分推理方向。OCR-MetaReasoning 发布 1500 条样本的 3×5 平衡基准(演绎/归纳/溯因 × 五类 OCR 对象),用 MRMS 衡量答案正确性、RPCS 衡量推理过程合规性。18 个 MLLM 评测显示远未饱和,最强模型 89.3 MRMS vs 人类 96.0。 | `reasoning`, `text-rich-vqa`, `layout` | [GitHub](https://github.com/gengxuli/OCR-MetaReasoning) |
| DVBench 🆕 | [DVBench](https://arxiv.org/abs/2608.29711v1) | arXiv 2026 | 现有评测割裂图表与视频理解。DVBench 将数据视频理解分解为五个维度,含 300 个视频与 1,000 条人工核验问答。评测九个 MLLM,Gemini-3.1-Pro 总体最优,开源模型不随规模单调提升,叙述能力不等于视觉能力。 | `table/chart`, `reasoning`, `text-rich-vqa` | N/A |
| ClearText-Video 🆕 | [ClearText-Video](https://arxiv.org/abs/2608.28784v1) | arXiv 2026 | MLLM 在真实视频中读字对模糊、低分辨率极敏感,而既有基准忽略质量变化。CTVid 发布 4,639 条富文本第一视角视频、160 万场景文字标注与 22 万中英 QA 对,每条含高质/降质/复原三种版本。评测发现模糊比低分辨率更致命,复原甚至会篡改 MLLM 依赖的文字证据。 | `degraded`, `in-the-wild`, `scene-text` | N/A |
| Synth-JDoc 🆕 | [Synth-JDoc](https://arxiv.org/abs/2608.28248v1) | arXiv 2026 | LVLM 识别竖排日文远逊横排,且复杂版面日文 OCR 数据稀缺。Synth-JDoc 用 HTML/CSS 合成 17,970 张文档图,混合竖横排、多栏、AI 配图,并施加扫描式与 Augraphy 噪声。在其上微调对竖排日文 OCR 提升最大,优于既有合成数据基线。 | `recognition`, `script-diverse`, `multilingual` | [GitHub](https://github.com/llm-jp/synth-jdoc) |
| Ancient-Bench 🆕 | [Ancient-Bench](https://arxiv.org/abs/2608.27169v1) | arXiv 2026 | 中文古器物文字识别缺乏跨年代、跨介质、跨字形的综合基准。Ancient-Bench 发布 2700 图,覆盖 3000 年、9 类器物、7 种古文字,并定义符号/字符/解析三类标注规范。评测 VLM 与 OCR 专用模型显示任务远未解决,最优 F1 仅 57.86%。 | `recognition`, `historical`, `script-diverse` | [GitHub](https://github.com/SCUT-DLVCLab/Ancient_Bench) |
| AraMS-28k 🆕 | [AraMS-28k](https://arxiv.org/abs/2608.26921v1) | arXiv 2026 | 历史阿拉伯文手写 HTR 长期缺大规模行级开放数据。AraMS-28k 发布 28600 行、14 本书、三种脚本传统,首次为边注行标注插入锚点以还原非线性阅读序。RefLAM 流水线以参考转录对齐 MLLM OCR 并全量人工复核;Kraken/HATFormer 基线显示明显的跨脚本泛化梯度。 | `recognition`, `historical`, `handwriting` | [Download](https://doi.org/10.5281/zenodo.22095333) |
| PlanSightRAG 🆕 | [PlanSightRAG](https://arxiv.org/abs/2608.26091v1) | arXiv 2026 | OCR 会丢掉解读土木 2D 标准图所需的几何与版面。PlanSightRAG 直接对图象检索与推理,用 ColNomic-3B 多向量检索与 Planner-Retriever-Auditor-Synthesizer 智能体管线,配 MaxSim 热图留痕。构建 4,056 对五州 DOT 基准,零样本 Recall@5 达 91.47%。 | `layout`, `document-qa`, `structured-output` | N/A |
| RefLAM 🆕 | [RefLAM](https://arxiv.org/abs/2608.25140v1) | arXiv 2026 | 历史阿拉伯文手稿缺少可扩展的行级 HTR 标注。RefLAM 结合页面分割、MLLM 结构化 OCR 与去变音符模糊对齐,提出可证明的 Confidence-100 规则,通量提升 75 倍。发布 AraMS-28k:14 卷、3043 页、27971 行及基线微调结果。 | `recognition`, `historical`, `handwriting` | [Download](https://doi.org/10.5281/zenodo.22095333) |
| WildHandBench 🆕 | [WildHandBench](https://arxiv.org/abs/2608.22959v1) | arXiv 2026 | 印刷文档 OCR 已超 96%,但手写文本仍被忽视。WildHandBench 收集 500 份手写文档,覆盖 4 语言、3 结构(正文/表格/公式)与 9 类真实场景,并提出 PDE 指标。18 个 MLLM 最佳仅 71.85%,人类 77.09%;模型错误 63-91% 为先验驱动。 | `recognition`, `handwriting`, `degraded` | N/A |
| FinixDoc-VL 🆕 | [FinixDoc-VL](https://arxiv.org/abs/2608.22842v1) | arXiv 2026 | 金融文档解析基准与真实部署差距大:模糊拍照、密集表格、超大页。FinixDoc-VL(基于 Qwen3-VL-4B)用同形异义字对比学习+多阶段 GRPO 复合奖励训练,配 Data Factory 流水线;FinixDocBench 覆盖拍照、超大页、内部金融流程,合规审校子集公开。 | `structured-output`, `table`, `recognition` | N/A |
| LëtzCross 🆕 | [LëtzCross](https://arxiv.org/abs/2608.21714v1) | arXiv 2026 | 页面图检索器在跨语言低资源场景研究不足。作者构建卢森堡语 PDF 基准,含 908 页与 579 条英/法/德/卢四语 QA,覆盖文本与视觉落地查询。页图检索器优于 OCR 文本检索,含卢森堡语的多语微调效果最佳。 | `document-qa`, `multilingual`, `low-resource` | [GitHub](https://github.com/OmarElbachyr/letzcross-benchmark) |
| KoViDoRe 🆕 | [KoViDoRe](https://arxiv.org/abs/2608.20840v1) | arXiv 2026 | 韩语视觉文档检索缺乏针对英语外的多页基准。KoViDoRe 提供 57 文档/6,729 页/706 查询,平均每查询相关 2.94 页,覆盖四领域,并配套 31 万对 Ko-VDR Train Public 训练集。微调 colqwen2-v1.0 后将 nDCG@10 从 29.5 提到 52.8,超越 8B 的 Qwen3-VL-Embedding。 | `document-qa`, `multi-page`, `multilingual` | [Download](https://hf.co/datasets/NomaDamas/ko-vdr-train-public) |
| ArmorOCR 🆕 | [ArmorOCR](https://arxiv.org/abs/2608.20122v1) | arXiv 2026 | MLLM 对人类可读的对抗视觉文本仍易出错。作者提出首个 region 级对抗 OCR 基准 AdvSpot(390 图、5 类 13 细类),并给出 ArmorOCR 两阶段训练(特权观察自蒸馏 + 任务奖励 GRPO),在对抗与通用 OCR 上均有提升或保持。 | `recognition`, `localization`, `hidden/adversarial` | N/A |
| OmniHandwritingOCR 🆕 | [OmniHandwritingOCR](https://arxiv.org/abs/2608.18586v1) | arXiv 2026 | MLLM 在真实手写 OCR 上的能力长期缺考,旧基准偏向印刷体或单行。作者整合 7.76 万标注图,覆盖英中文本与单/多行公式并按结构复杂度分层,以五种统一指标评测 13 个系统,揭示多行公式性能骤降与幻觉式纠正等失效模式。 | `recognition`, `handwriting`, `formula` | [GitHub](https://github.com/ECNU-RAIL/OmniHandwritingOCR-CIKM2026) |
| Open-Model Structured Extraction Benchmark 🆕 | [Open-Model Structured Extraction Benchmark](https://arxiv.org/abs/2608.18289v1) | arXiv 2026 | 开源 OCR+LLM 与 VLM 在高风险公文结构化抽取上缺系统评测。作者在 100 份成绩单 PDF 上统一评测 6 个 OCR 引擎、5 个 Qwen3 与 5 个 VLM,35 个零样本配置中仅 4 个 F1>0.5,并指出 OCR 输出的结构保持比模型规模更关键。 | `KIE`, `structured-output`, `document-qa` | N/A |
| CADP-Bench 🆕 | [CADP-Bench](https://arxiv.org/abs/2608.17550v1) | arXiv 2026 | 学术页面的表格、公式、图表、伪代码等结构在 Markdown 中难以保真。作者提出可编译学术文档解析范式,将页面重构为上下文 LaTeX + 可执行 Python,发布 1,630 张专家标注的多结构页面基准与回灌编译评测协议;前沿 MLLM 仍难做高保真可执行重构。 | `structured-output`, `formula`, `table/chart` | [GitHub](https://github.com/AriKing11/CADP-Bench) |
| Chartography 🆕 | [Chartography](https://arxiv.org/abs/2608.10677v1) | ECCV 2026 Workshop (BEAM) | 现有图表基准集中在柱/折线/饼图且趋于饱和。Chartography 收集 100 个来自专业实践的图表任务,问题由从业人员撰写并经三位专家独立验证;30 个前沿模型配置最高仅 45.0% pass@1,暴露模型在细微视觉特征、稀疏坐标轴与 3D 几何上的感知短板。 | `table/chart`, `reasoning`, `document-qa` | N/A |
| DEC / TableParseMap 🆕 | [DEC / TableParseMap](https://arxiv.org/abs/2608.09842v1) | arXiv 2026 | 聚合分数掩盖了真实复杂表格的持续失败。作者构建 TableParseMap(916 表、5 场景、9 失败类型),并提出 DEC:用通用 VLM 作控制器,对冻结 解析器执行分解-增强-纠错,配合视觉一致性门控与排序器。平均 TEDS +1.57,大表格上提升达 5.66。 | `table`, `structured-output`, `layout` | N/A |
| LongChart 🆕 | [LongChart](https://arxiv.org/abs/2608.01328v1) | arXiv 2026 | 现有图表基准偏单图感知,欠缺多图推理。作者提出 LongChart,通过潜在图合成流水线,VQA 集平均含 6.5 张图与 31.2 个问题;评测 10 个 MLLM 显示准确率随复杂度急剧下降,揭示多图推理的缺口。 | `table/chart`, `document-qa`, `reasoning` | N/A |
| Berrutti OCR Hallucination Analysis 🆕 | [Berrutti OCR Hallucination Analysis](https://arxiv.org/abs/2607.24077v3) | arXiv 2026 | 在乌拉圭历史微档案上,VLM OCR 在 CER/WER 上优于传统系统,却隐藏系统化幻觉:拼写规范化、虚构内容与语义替换,流畅却改义,对命名实体伤害最大。作者评测 18 个系统并呼吁评价超越字符级准确率。 | `recognition`, `historical`, `low-resource` | [GitHub](https://github.com/camilomarino/ocr_berrutti_dataset) |
| Khondo 🆕 | [Khondo](https://arxiv.org/abs/2607.21780v1) | arXiv 2026 | 政府多文档拼包在低资源孟加拉语中难切分,而 OCR 不可靠。Khondo 是首个面向孟加拉政务表的视觉原生基准,含 1,950 拼包、14 领域、5 种拼接方案。零样本 MLLM 评测显示聚类尚可,但页序在打乱后崩塌;英文包顺序恢复更佳。 | `multilingual`, `low-resource`, `layout` | [HuggingFace](https://huggingface.co/datasets/Mausul/khondo) |
| Persian Pixel 🆕 | [Persian Pixel](https://arxiv.org/abs/2607.20385v1) | arXiv 2026 | 波斯文连笔、字形上下文相关、标注数据稀缺。作者基于 700 万词语料用 SynthOCR-Gen 渲染 34.3 万图文对,叠加 25 种以上退化模型。开源数据集支持 TrOCR/Donut 在低资源波斯-阿拉伯文上的训练与微调。 | `recognition`, `low-resource`, `script-diverse` | N/A |
| XL-DocBench 🆕 | [XL-DocBench](https://arxiv.org/abs/2608.00036v1) | arXiv 2026 | 专业场景常需从上千页文档中给出可溯源答案。XL-DocBench 收录 1519 道人工审核题、覆盖 6 个专业领域、最长 2303 页;72.6% 需多页证据,36.6% 含表格/图表/图示,并附推理标签、证据页与验证规则。 | `multi-page`, `long-context`, `document-qa` | N/A |
| TestHallVQA 🆕 | [TestHallVQA](https://arxiv.org/abs/2609.13158v1) | arXiv 2026 | 现有平面 VQA 基准在长文档检索与清晰单图推理间割裂。TestHallVQA 构建考试文档多图 VQA 基准(10,242 QA、7,155 图),可注入多级冗余上下文,并提出 F1-R2 指标联合度量冗余下的推理与检索鲁棒性;在约 20 个 LVLM 上揭示性能骤降且规模化无法缓解视觉污染。 | `text-rich-vqa`, `long-context`, `multi-page` | [GitHub](https://github.com/yqyu2317/TestHallVQA-benchmark) |
| From Pixels to Pairs 🆕 | [From Pixels to Pairs](https://arxiv.org/abs/2609.17538v1) | arXiv 2026 | LLM 在真实 OCR 噪声下的键值抽取行为缺乏系统研究。该工作在 FUNSD/CORD/SROIE 上用统一协议评测多款 LLM,搭配 Gold 文本与 PaddleOCR/EasyOCR/Tesseract 输出,揭示 OCR 噪声导致显著退化、模型差距随噪声收敛,并归纳键值错位、数字损坏等典型失败模式。 | `KIE`, `structured-output`, `degraded` | N/A |
| GDP.pdf 🆕 | [GDP.pdf](https://arxiv.org/abs/2607.11192v3) | CVPR 2026 Workshop | 现有文档 AI 基准孤立评测能力,难以反映真实专业 PDF 问题。GDP.pdf 由 10 个领域从业者在实际工作流中作者 100 道题,仅保留至少两个前沿多模态模型出错的条目,配备原子评分细则并按 11 项能力打标;十七个前沿模型评测中最好仅通过 30.7%,常在表格、图表、脚注、空间推理上失败。 | `document-qa`, `structured-output`, `table/chart` | [HuggingFace](https://huggingface.co/datasets/surgeai/GDP.pdf) |
| SynthDocBench 🆕 | [SynthDocBench](https://arxiv.org/abs/2607.10400v1) | arXiv 2026 | 真实文档中长度、版面、模态、难度相互混杂,难以归因 VLM 失败。SynthDocBench 是完全合成的长上下文基准(平均 51.1 页,六种版式,双层图表生成,1,788 题),独立变化各因子;在七个前沿 VLM 上揭示长度退化、中段位置敏感与长文档下图表理解崩塌三类失败模式。 | `synthetic-hard`, `long-context`, `layout` | [HuggingFace](https://huggingface.co/datasets/ServiceNow-AI/SynthDocBench) |
| HIPE-OCRepair-2026 🆕 | [HIPE-OCRepair-2026](https://arxiv.org/abs/2607.08143v1) | ICDAR 2026 Competition | 历史报纸与印刷品遗留 OCR 噪声多、再数字化不可行。ICDAR 2026 HIPE-OCRepair 赛发布多语言(英/法/德,17-20 世纪)和谐化基准,设可控噪声层级与检索导向 cMER 评分,评估四支队伍从零样本到持续预训练的 LLM 后纠错系统。微调系统(BnF-Mistral)包揽八项第一,但低噪声过度纠正仍是普遍难题。 | `recognition`, `historical`, `multilingual` | [GitHub](https://github.com/hipe-eval/HIPE-OCRepair-2026-data) |
| Infinity-Parser2 🆕 | [Infinity-Parser2](https://arxiv.org/abs/2607.07836v3) | arXiv 2026 | 文档解析受限于表格/公式/图表/阅读顺序的高质量标注稀缺。Infinity-Parser2 将可控渲染+迭代精修合成引擎与可验证多任务 RLVR 结合,联合训练八项目标(解析、版面、表格、数学、图表、化学式、文档 VQA、通用多模态理解),开源中英双语 500 万样本 Infinity-Doc2-5M。Pro 版在 olmOCR-Bench 达 87.6%、ParseBench 74.3%,超越 DeepSeek-OCR-2 等。 | `recognition`, `layout`, `structured-output` | [HuggingFace](https://huggingface.co/datasets/infly/Infinity-Doc2-5M) |
| HunyuanOCR-1.5 🆕 | [HunyuanOCR-1.5](https://arxiv.org/abs/2607.04884v3) | arXiv 2026 | 轻量 OCR VLM 在密集文档上面临延迟-能力权衡。HunyuanOCR-1.5 将 DFlash 草稿式解码适配到 OCR 实现 6.37×/2.14× 加速,并引入 Agentic Data Flow 自动构建弱点导向训练数据。模型在 OmniDocBench v1.6 上达到顶级水平,并扩展到古文字与 331 种语言。 | `recognition`, `structured-output`, `multilingual` | [GitHub](https://github.com/Tencent-Hunyuan/HunyuanOCR) |
| Interpres 🆕 | [Interpres](https://arxiv.org/abs/2607.03836v1) | arXiv 2026 | 中世纪拉丁手稿因抄写员缩写与羊皮纸退化使通用 VLM 失效。作者评测 OCR→VLM 翻译流水线并发布 Interpres Parallel Corpus(1,383 条对齐手稿行、转录与译文),发现专用 OCR 接 VLM 的最简流水线胜过所有多组件变体,印证专精化差距与复杂度悖论。 | `historical`, `translation`, `low-resource` | N/A |
| ClinOCR-Bench 🆕 | [ClinOCR-Bench](https://arxiv.org/abs/2607.03650v1) | arXiv 2026 | 临床扫描文档(化验单、表单)是 OCR 长期痛点,既有研究多使用私有数据。作者发布 ClinOCR-Bench,含 384 张扫描图像、六类子集(正常/手写/低质/旋转/表格/混合伪影),并对主流开源与商业 VLM 给出基线评测。 | `recognition`, `degraded`, `handwriting` | [GitHub](https://github.com/ClinOCR-Bench/ClinOCR-Bench) |
| MORE 🆕 | [MORE](https://arxiv.org/abs/2607.02956v1) | arXiv 2026 | 现有文档解析基准偏重英文与中文,长尾语言成为评测盲区。作者发布 MORE:覆盖 149 种语言、1,288 页真实文档,带文本/公式/表格/代码/目录/阅读顺序结构标注。对主流 VLM 与专用 OCR 模型的基线评测揭示长尾语言与结构化解析的薄弱环节。 | `multilingual`, `low-resource`, `script-diverse` | [GitHub](https://github.com/zimoqingfeng/MORE) |
| LV-ROVER-MLT 🆕 | [LV-ROVER-MLT](https://arxiv.org/abs/2607.00250v5) | DocEng 2026 | 马耳他语段落级 OCR 训练数据稀缺。LV-ROVER-MLT 合成微调 Tesseract 5,融合五路识别流并做词典门控词级仲裁,适配马耳他语变音符;获 DocEng 2026 冠军(CER 0.0074),并发布 36.8K 对马耳他语 OCR 语料。 | `recognition`, `low-resource`, `multilingual` | N/A |
| sinhala-ocr-lk-acts-1010 🆕 | [sinhala-ocr-lk-acts-1010](https://arxiv.org/abs/2606.29378v1) | MERCon 2026 | 僧伽罗语页面级 OCR 此前无真实数据集。作者发布 sinhala-ocr-lk-acts-1010(1010 页,跨 1981-2019),用 QLoRA 微调 DeepSeek-OCR、LightOnOCR-2-1B;LightOnOCR-2-1B 达 CER 1.05%,优于 Surya、Tesseract v5 与 Google Document AI。 | `recognition`, `low-resource`, `multilingual` | N/A |
| Devanagari OCR-VLM Bench 🆕 | [Devanagari OCR-VLM Bench](https://arxiv.org/abs/2606.29213v1) | arXiv 2026 | OCR-VLM 在印度系文字上的表现缺乏刻画。作者对 10 个系统(经典、开放 VLM、专用 OCR-VLM、前沿闭源)在印地语四种退化与 300 张真实扫描上做基准,并做 ByT5 后校正;真实扫描拉开 76 点差距,英文 OCR 强不代表印地语强。 | `recognition`, `script-diverse`, `degraded` | N/A |
| DLVQA 🆕 | [DLVQA](https://arxiv.org/abs/2606.28780v1) | arXiv 2026 | 受限于上下文窗口且现有 KG-RAG 只处理文本,MLLM 难做整篇文档 VQA。作者从视觉丰富文档构建多模态知识图谱用于图 RAG,并发布 DLVQA 基准(含参考摘要与支持事实),在多跳 QA/VQA 上优于 MMRAG 与 KG 基线。 | `document-qa`, `layout`, `multi-page` | N/A |
| OCR-Robust 🆕 | [OCR-Robust](https://arxiv.org/abs/2606.26041v1) | arXiv 2026 | VLM 在 OCR 上表现强但视觉扰动下的鲁棒性尚乏研究。作者构建 OCR-Robust,812 样本覆盖文档、场景文本、手写、数学、图表与表格,设 5 种扰动×3 级严重度,提出 RCR/WCR/CRI 指标。18 个模型评测显示净度准确率不等于鲁棒性,图表最易崩。 | `recognition`, `degraded`, `reasoning` | N/A |
| WATERec 🆕 | [WATERec](https://arxiv.org/abs/2606.24484v1) | arXiv 2026 | WordArt(艺术字)识别因定制字体、纹理、排版远难于普通场景文本。作者发布 200 万合成数据 WATER-S,并提出支持任意形状输入与自回归解码的 WATERec;在 WordArt-Bench 上达 90.40%,大幅超越通用与 OCR 专用视觉语言模型。 | `recognition`, `synthetic-hard`, `scene-text` | [GitHub](https://github.com/YesianRohn/WATER) |
| Koshur Pixel 🆕 | [Koshur Pixel](https://arxiv.org/abs/2606.23144v1) | arXiv 2026 | 克什米尔文采用波斯-阿拉伯 Nastaliq 脚本,字形上下文变化与连笔复杂,OCR 缺数据。作者用 SynthOCR-Gen 合成 61.3 万图-文对,覆盖词到整页并施加 25+ 退化,成为首个大规模克什米尔文合成 OCR 数据集。 | `recognition`, `low-resource`, `script-diverse` | N/A |
| SemVink 🆕 | [SemVink](https://arxiv.org/abs/2506.02803) | arXiv 2025 | VLM 难以察觉视错觉与 AI 图中的隐藏内容,显式提示下准确率仍仅 0-5.36%。作者发布 HC-Bench(112 张含隐藏文字/物体的图),并提出 SemVink:将图降采样到 32-128 像素,剔除冗余视觉噪声后准确率超 99%。 | `hidden/adversarial`, `synthetic-hard`, `recognition` | N/A |
| AtomCite | [AtomCite](https://arxiv.org/abs/2609.05802v1) | arXiv 2026 | 多页文档问答中模型给出的页级引用常出错,但此前没有基准核验文档图像上已提供的引用。AtomCite 将答案拆为原子声明,用并行文本与图像子代理逐条对照所引页面,再按确定性策略执行修正。DocCite 基准显示图像感知验证在三族模型上全面优于 OCR-only 与提示式基线。 | `multi-page`, `document-qa`, `reasoning` | N/A |
| KhatianDoc | [KhatianDoc](https://arxiv.org/abs/2609.03597v1) | arXiv 2026 | 孟加拉手写地契 RS Khatian 使用 Ana-Ganda 十六进制分数系统,字体与分词器均无支持,任何 OCR 管线与多模态大模型都无法识别。KhatianDoc 基于 107 份律师校验的真实记录构建四任务基准(符号识别、十六进制算术、字段抽取、问答),零样本评测六个多模态大模型,揭示能力缺失而非性能差距,并发布脱敏数据与代码。 | `recognition`, `low-resource`, `handwriting` | [HuggingFace](https://huggingface.co/datasets/RaiyanKhaan/KhatianDoc) |
| OCR-EDR | [OCR-EDR](https://arxiv.org/abs/2609.03445v1) | arXiv 2026 | OCR 在公式与结构化文本上仍常错,聚合指标掩盖 case 级错误。OCR-EDR 把诊断-编辑-重渲染建成闭环;DocEDR (Qwen3.5-9B) 经 verifier SFT、课程式修复与 GRPO 三阶段训练。作者发布 OCRErrBench(900 例,含精确与渲染等价正例及真错误),并在外部公式基准上获得可验证增益。 | `recognition`, `formula`, `structured-output` | N/A |
| LeakageBench | [LeakageBench](https://arxiv.org/abs/2609.02207v1) | arXiv 2026 | 文档图像 PII 脱敏在 OCR 出错或版面干扰时会泄露标识符。LeakageBench 提供 500 张文档图像与 11,954 条 GDPR 对齐的 PII 标注,覆盖直接、链路与上下文三类标识符。即使最强的 OCR 流水线与 OCR-free VLM,关键页级泄漏率仍居高不下。 | `localization`, `KIE`, `recognition` | N/A |
| LongDocBench | [LongDocBench](https://arxiv.org/abs/2608.15064v1) | arXiv 2026 | 长文档 TOC 层级与上下文关系恢复基准;85 篇文档 2,582 页,含 3,937 标题节点与 3,258 关系。 | `long-context`, `multi-page`, `layout` | N/A |
| BanglaWild | [BanglaWild](https://arxiv.org/abs/2608.03884v1) | arXiv 2026 | 提出 BanglaWild,2535 张真实场景孟加拉语文字基准;评测 15 个 VLM 与 3 个 OCR 系统,给出 15 类错误分类。 | `recognition`, `scene-text`, `in-the-wild` | N/A |
| ConfBench | [ConfBench](https://arxiv.org/abs/2608.01792v1) | arXiv 2026 | 首个面向 KIE 的校准基准;20 条受控退化管线,1346 变体,70K+ 实体评测。 | `KIE`, `degraded`, `dense-text` | N/A |
| AdvOCR | [VACoT: Rethinking Visual Data Augmentation with VLMs](https://arxiv.org/abs/2512.02361) | arXiv 2025 | 对抗 OCR benchmark，配合推理时视觉增强方法。 | `recognition`, `hidden/adversarial`, `synthetic-hard` | [HuggingFace](https://huggingface.co/datasets/SincereX/AdvOCR) |
| AncientDoc | [Benchmarking Vision-Language Models on Chinese Ancient Documents: From OCR to Knowledge Reasoning](https://arxiv.org/abs/2509.09731) | arXiv 2025 | 中文古籍文档 benchmark，覆盖页面级 OCR、翻译、知识 QA 和推理 QA。 | `recognition`, `historical`, `script-diverse`, `reasoning`, `translation` | [HuggingFace](https://huggingface.co/datasets/ByteDance/AncientDoc) |
| BABMLLM | [BABMLLM: Benchmarking the Ancient Books Capability of MLLMs](https://www.nature.com/articles/s40494-025-01897-3) | npj Heritage Science 2025 | 评估 MLLM 对印刷和手写古籍的多模态处理能力。 | `recognition`, `historical`, `handwriting`, `reasoning` | N/A |
| CC-OCR V2 | [CC-OCR V2: Benchmarking Large Multimodal Models for Literacy in Real-world Document Processing](https://arxiv.org/abs/2605.03903) | arXiv 2026 | 面向企业真实文档处理的 OCR benchmark，覆盖解析、grounding 和 QA 中的 hard/corner cases。 | `recognition`, `layout`, `KIE`, `document-qa` | [HuggingFace](https://huggingface.co/datasets/Eioss/CC-OCR-V2) |
| CC-OCR | [CC-OCR: A Comprehensive and Challenging OCR Benchmark for Evaluating Large Multimodal Models in Literacy](https://arxiv.org/abs/2412.02210) | ICCV 2025 | 四个赛道覆盖多场景阅读、多语种阅读、文档解析和 KIE。 | `recognition`, `multilingual`, `layout`, `KIE` | [HuggingFace](https://huggingface.co/datasets/wulipc/CC-OCR) |
| Chronicles-OCR | [Chronicles-OCR: A Cross-Temporal Perception Benchmark for the Evolutionary Trajectory of Chinese Characters](https://arxiv.org/abs/2605.11960) | arXiv 2026 | 覆盖七类汉字形态演化的跨时间 benchmark，评估 spotting、古文字识别、解析和脚本分类。 | `recognition`, `historical`, `script-diverse`, `localization` | [GitHub](https://github.com/VirtualLUOUCAS/Chronicles-OCR) |
| GlotOCR Bench | [GlotOCR Bench: OCR Models Still Struggle Beyond a Handful of Unicode Scripts](https://arxiv.org/abs/2604.12978) | arXiv 2026 | 跨 100+ Unicode 脚本的 OCR 泛化 benchmark，包含干净和退化渲染文本。 | `recognition`, `multilingual`, `script-diverse`, `degraded` | [HuggingFace](https://huggingface.co/datasets/cis-lmu/glotocr-bench) |
| HC-Bench | [SemVink: Advancing VLMs' Semantic Understanding of Optical Illusions via Visual Global Thinking](https://aclanthology.org/2025.emnlp-main.1381/) | EMNLP 2025 | 面向隐藏文本、隐藏物体和视觉错觉的 benchmark，测试 VLM 近乎失败的隐藏内容感知。 | `recognition`, `hidden/adversarial`, `synthetic-hard` | [HuggingFace](https://huggingface.co/datasets/JohnnyZeppelin/HC-Bench) |
| IndicVisionBench | [IndicVisionBench: Benchmarking Cultural and Multilingual Understanding in VLMs](https://arxiv.org/abs/2511.04727) | ICLR 2026 | 面向印度语言的 Indic 脚本 OCR、多模态翻译和 VQA。 | `recognition`, `multilingual`, `translation`, `document-qa` | [HuggingFace](https://huggingface.co/datasets/krutrim-ai-labs/IndicVisionBench) |
| KITAB-Bench | [KITAB-Bench: A Comprehensive Multi-Domain Benchmark for Arabic OCR and Document Understanding](https://arxiv.org/abs/2502.14949) | ACL Findings 2025 | 阿拉伯语 OCR/文档 benchmark，覆盖版面、行识别、表格、图表和 PDF-to-Markdown。 | `recognition`, `multilingual`, `layout`, `structured-output`, `table/chart` | [HuggingFace](https://huggingface.co/kitab-bench) |
| KazakhOCR | [KazakhOCR: A Synthetic Benchmark for Evaluating Multimodal Models in Low-Resource Kazakh Script OCR](https://huggingface.co/papers/2603.13238) | ACL AbjadNLP 2026 | 合成哈萨克文字 OCR，覆盖字体、颜色、噪声、模糊和旋转变化。 | `recognition`, `multilingual`, `low-resource`, `synthetic-hard`, `degraded` | [HuggingFace](https://huggingface.co/datasets/henrygagnier/kazakh-ocr) |
| OBI-Bench | [OBI-Bench: Can LMMs Aid in Study of Ancient Script on Oracle Bones?](https://arxiv.org/abs/2412.01175) | ICLR 2025 | 综合性甲骨文 benchmark，覆盖识别、缀合、分类、检索和释读。 | `recognition`, `historical`, `script-diverse`, `reasoning` | [GitHub](https://github.com/zijianchen98/OBI-Bench) |
| OCR-Reasoning | [Reasoning-OCR: Can Large Multimodal Models Solve Complex Logical Reasoning Problems from OCR Cues?](https://arxiv.org/abs/2505.12766) | arXiv 2025 | 测试富文本图像上的逻辑推理能力，其中 OCR 线索必要但不充分。 | `reasoning`, `text-rich-vqa` | [HuggingFace](https://huggingface.co/datasets/mx262/OCR-Reasoning) |
| OCRBench v2 | [OCRBench v2: An Improved Benchmark for Evaluating Large Multimodal Models on Visual Text Localization and Reasoning](https://arxiv.org/abs/2501.00321) | NeurIPS D&B 2025 | 双语 benchmark，包含 31 个场景，评估识别、定位、版面感知和 OCR 推理。 | `recognition`, `localization`, `layout`, `reasoning` | [GitHub](https://github.com/Yuliang-Liu/MultimodalOCR/blob/main/OCRBench_v2/README.md) |
| OCRBench | [OCRBench: On the Hidden Mystery of OCR in Large Multimodal Models](https://arxiv.org/abs/2305.07895) | arXiv 2023 | 面向 MLLM 的 OCR 评测，覆盖场景文本、文档 VQA、KIE 和手写数学。 | `recognition`, `document-qa`, `KIE`, `formula`, `handwriting` | [GitHub](https://github.com/Yuliang-Liu/MultimodalOCR/blob/main/OCRBench/README.md) |
| PictOBI-20k | [PictOBI-20k: Unveiling Large Multimodal Models in Visual Decipherment for Pictographic Oracle Bone Characters](https://arxiv.org/abs/2509.05773) | arXiv 2025 | 基于甲骨文字形与真实物体图像配对的象形甲骨文释读 benchmark。 | `recognition`, `historical`, `script-diverse`, `reasoning` | [GitHub](https://github.com/OBI-Future/PictOBI-20k) |
| PsOCR | [PsOCR: Benchmarking Large Multimodal Models for Optical Character Recognition in Low-resource Pashto Language](https://arxiv.org/abs/2505.10055) | arXiv 2025 | 面向低资源普什图语、波斯-阿拉伯文字识别的合成 OCR 数据集与 benchmark。 | `recognition`, `multilingual`, `low-resource`, `script-diverse` | [HuggingFace](https://huggingface.co/datasets/zirak-ai/PashtoOCR) |
| RIO-Bench | [Read or Ignore? A Unified Benchmark for Typographic-Attack Robustness and Text Recognition in Vision-Language Models](https://arxiv.org/abs/2512.11899) | arXiv 2025 | 同场景反事实样本，要求模型判断图中文字何时应被读取或忽略。 | `recognition`, `hidden/adversarial`, `reasoning` | [HuggingFace](https://huggingface.co/datasets/turing-motors/RIO-Bench) |
| SCAM | [SCAM: A Real-World Typographic Robustness Evaluation for Multimodal Foundation Models](https://arxiv.org/abs/2504.04893) | arXiv 2025 / DMLR 2026 | 真实世界 typographic attack 图像，覆盖物体类别和攻击词。 | `hidden/adversarial`, `scene-text`, `reasoning` | [HuggingFace](https://huggingface.co/datasets/BLISS-e-V/SCAM) |
| ThaiOCRBench | [ThaiOCRBench: A Task-Diverse Benchmark for Vision-Language Understanding in Thai](https://arxiv.org/abs/2511.04479) | IJCNLP-AACL 2025 | 泰语富文本 VLM benchmark，包含细粒度识别和手写内容抽取。 | `recognition`, `multilingual`, `handwriting`, `text-rich-vqa` | [HuggingFace](https://huggingface.co/datasets/typhoon-ai/ThaiOCRBench) |
| VCR-Wiki | [VCR: Visual Caption Restoration](https://arxiv.org/abs/2406.06462) | ICLR 2025 | 利用像素级提示和视觉上下文恢复部分遮挡的 caption。 | `recognition`, `occlusion`, `reasoning` | [GitHub](https://github.com/tianyu-z/VCR) |

[[⬆️ 返回顶部](#contents)]

---

<a id="research-papers"></a>

## 🚀 研究论文

<a id="degraded-and-in-the-wild-ocr"></a>

### 🌍 退化与真实世界 OCR

*本节将 hard OCR 定义为真实世界视觉困难条件下的文本识别或 OCR 中心理解。收录论文应至少处理一种视觉瓶颈：模糊、低分辨率、噪声、压缩、弱光、屏幕拍摄、扫描伪影、倾斜、遮挡、缺失文本、小文本或密集文本、复杂场景上下文。干净、清晰、容易图像上的普通场景文字识别不在本节范围内。*

| 方法/系统 | 论文 | Venue & Year | 亮点 | 标签 | 代码 |
|---|---|---|---|---|---|
| SA-DBNet 🆕 | [SA-DBNet](https://arxiv.org/abs/2609.13815v1) | arXiv 2026 | 真实场景退化(模糊、低分辨率、压缩)下文本VQA研究不足。作者构建4013图/7000问答对的退化基准,对比模块化OCR流水线(SA-DBNet检测器)与端到端Qwen2-VL。微调后模块化流水线准确率57.50%对38.00%;CER/WER不能可靠预测VQA效果。 | `recognition`, `degraded`, `text-rich-vqa` | [GitHub](https://github.com/RitaliVatsi/VQA_Project) |
| DocIntent 🆕 | [DocIntent](https://arxiv.org/abs/2608.29037v1) | arXiv 2026 | 真实退化(模糊、阴影、摩尔纹)损害文档 VQA,盲目修复反会引入伪影。DocIntent 是无需训练的智能体框架:先评估可答性,选择性调用修复工具,并用对比回滚撤销有害步骤。在 WildDoc 上稳定提升多个开源与闭源 MLLM。 | `degraded`, `document-qa`, `in-the-wild` | - |
| ClearText-Video 🆕 | [ClearText-Video](https://arxiv.org/abs/2608.28784v1) | arXiv 2026 | MLLM 在真实视频中读字对模糊、低分辨率极敏感,而既有基准忽略质量变化。CTVid 发布 4,639 条富文本第一视角视频、160 万场景文字标注与 22 万中英 QA 对,每条含高质/降质/复原三种版本。评测发现模糊比低分辨率更致命,复原甚至会篡改 MLLM 依赖的文字证据。 | `degraded`, `in-the-wild`, `scene-text` | - |
| WildHandBench 🆕 | [WildHandBench](https://arxiv.org/abs/2608.22959v1) | arXiv 2026 | 印刷文档 OCR 已超 96%,但手写文本仍被忽视。WildHandBench 收集 500 份手写文档,覆盖 4 语言、3 结构(正文/表格/公式)与 9 类真实场景,并提出 PDE 指标。18 个 MLLM 最佳仅 71.85%,人类 77.09%;模型错误 63-91% 为先验驱动。 | `recognition`, `handwriting`, `degraded` | - |
| Arabic VLM-OCR Study 🆕 | [Arabic VLM-OCR Study](https://arxiv.org/abs/2608.22366v1) | arXiv 2026 | VLM 在阿拉伯/伊斯兰手稿 OCR 上的作用长期研究不足。本文在 8 个阿拉伯语数据集(手稿、旧印本、净印本、多域、手写)上比较 Tesseract、通用与阿拉伯专用 VLM 及 OCR 条件化 VLM 校正,提出 OCR 先验可恢复性原则,并给出失败模式诊断。 | `recognition`, `historical`, `handwriting` | - |
| SPaTS 🆕 | [SPaTS](https://arxiv.org/abs/2607.27902v2) | arXiv 2026 | 多 patch 视觉 token grounding 在密集/小文本场景引入噪声与定位歧义。SPaTS 用单锚点视觉 token 路由每个文本实例,配合 RL 优化的 token 选择、方向嵌入对齐与 patch 增强解码,超越前沿闭源与 OCR MLLM。 | `localization`, `recognition`, `scene-text` | [GitHub](https://github.com/eeNickTang/SPaTS) |
| Berrutti OCR Hallucination Analysis 🆕 | [Berrutti OCR Hallucination Analysis](https://arxiv.org/abs/2607.24077v3) | arXiv 2026 | 在乌拉圭历史微档案上,VLM OCR 在 CER/WER 上优于传统系统,却隐藏系统化幻觉:拼写规范化、虚构内容与语义替换,流畅却改义,对命名实体伤害最大。作者评测 18 个系统并呼吁评价超越字符级准确率。 | `recognition`, `historical`, `low-resource` | [GitHub](https://github.com/camilomarino/ocr_berrutti_dataset) |
| ClinOCR-Bench 🆕 | [ClinOCR-Bench](https://arxiv.org/abs/2607.03650v1) | arXiv 2026 | 临床扫描文档(化验单、表单)是 OCR 长期痛点,既有研究多使用私有数据。作者发布 ClinOCR-Bench,含 384 张扫描图像、六类子集(正常/手写/低质/旋转/表格/混合伪影),并对主流开源与商业 VLM 给出基线评测。 | `recognition`, `degraded`, `handwriting` | [GitHub](https://github.com/ClinOCR-Bench/ClinOCR-Bench) |
| sinhala-ocr-lk-acts-1010 🆕 | [sinhala-ocr-lk-acts-1010](https://arxiv.org/abs/2606.29378v1) | MERCon 2026 | 僧伽罗语页面级 OCR 此前无真实数据集。作者发布 sinhala-ocr-lk-acts-1010(1010 页,跨 1981-2019),用 QLoRA 微调 DeepSeek-OCR、LightOnOCR-2-1B;LightOnOCR-2-1B 达 CER 1.05%,优于 Surya、Tesseract v5 与 Google Document AI。 | `recognition`, `low-resource`, `multilingual` | - |
| Devanagari OCR-VLM Bench 🆕 | [Devanagari OCR-VLM Bench](https://arxiv.org/abs/2606.29213v1) | arXiv 2026 | OCR-VLM 在印度系文字上的表现缺乏刻画。作者对 10 个系统(经典、开放 VLM、专用 OCR-VLM、前沿闭源)在印地语四种退化与 300 张真实扫描上做基准,并做 ByT5 后校正;真实扫描拉开 76 点差距,英文 OCR 强不代表印地语强。 | `recognition`, `script-diverse`, `degraded` | - |
| OCR-Robust 🆕 | [OCR-Robust](https://arxiv.org/abs/2606.26041v1) | arXiv 2026 | VLM 在 OCR 上表现强但视觉扰动下的鲁棒性尚乏研究。作者构建 OCR-Robust,812 样本覆盖文档、场景文本、手写、数学、图表与表格,设 5 种扰动×3 级严重度,提出 RCR/WCR/CRI 指标。18 个模型评测显示净度准确率不等于鲁棒性,图表最易崩。 | `recognition`, `degraded`, `reasoning` | - |
| UniTranslator 🆕 | [UniTranslator](https://arxiv.org/abs/2606.24333v1) | arXiv 2026 | 图内机器翻译需将图中场景文字翻译并原位重绘,统一多模态模型存在理解-生成冲突与空间错位。UniTranslator 用理解-生成对齐模块桥接表征差异,辅以像素监督的空间掩码解码器,在多语言方向与复杂版面上取得 SOTA。 | `translation`, `recognition`, `scene-text` | [GitHub](https://github.com/SeerRay-Lab/Unitranslator) |
| Jina-OCR-v1 | [Jina-OCR-v1](https://arxiv.org/abs/2609.03181v1) | arXiv 2026 | 端到端文档解析 VLM 在低端 GPU 上推理代价高,公式与表格结构奖励覆盖不足。Jina-OCR-v1 在 DeepSeek-OCR 压缩视觉编码器与 3B MoE 解码器上加入复用的 FastMTP 投机解码头,并结合 SFT 与基于公式/表格稠密可验证奖励的 GRPO 后训练。模型在主流解析榜单匹敌更大系统,同时在低端 GPU 保持高吞吐。 | `recognition`, `structured-output`, `table` | - |
| DADC-DocVLM | [DADC-DocVLM](https://arxiv.org/abs/2609.01575v1) | arXiv 2026 | 受监管行业面临文档 VLM 的成本-质量鸿沟:PII 禁用云端模型,小模型达不到质量门槛,大模型又不划算。我们在单卡 H100 上部署 MoE VLM(总 35B、激活 3B),以难度感知数据筛选流水线在 30 万 CC PDF 上微调;性能超越大一个量级的可部署基线,相较人工标注降本逾 80%。 | `KIE`, `structured-output`, `layout` | - |
| NaviDC-OCR | [NaviDC-OCR](https://arxiv.org/abs/2608.12898v1) | arXiv 2026 | 针对数字与拍摄文档的统一解析框架;OmniDocBench 96.87、Wild-OmniDocBench 88.53、PureDocBench 78.41 达 SOTA。 | `structured-output`, `layout`, `table` | [GitHub](https://github.com/caipeng328/NaviDC-OCR) |
| VTS / Prompt-Region Grounding | [VTS / Prompt-Region Grounding](https://arxiv.org/abs/2608.04726v1) | arXiv 2026 | VTS 干预将问题移入像素;prompt-region grounding 无需 OCR 即恢复 8.3 分准确率。 | `reasoning`, `text-rich-vqa`, `localization` | - |
| BanglaWild | [BanglaWild](https://arxiv.org/abs/2608.03884v1) | arXiv 2026 | 提出 BanglaWild,2535 张真实场景孟加拉语文字基准;评测 15 个 VLM 与 3 个 OCR 系统,给出 15 类错误分类。 | `recognition`, `scene-text`, `in-the-wild` | - |
| ConfBench | [ConfBench](https://arxiv.org/abs/2608.01792v1) | arXiv 2026 | 首个面向 KIE 的校准基准;20 条受控退化管线,1346 变体,70K+ 实体评测。 | `KIE`, `degraded`, `dense-text` | - |
| FAU ImageCLEF 2026 | [FAU ImageCLEF 2026](https://arxiv.org/abs/2608.01664v1) | arXiv 2026 | ImageCLEF 2026 多模态推理系统;Visual MCQ 第三、Visual OpenQA 第一。 | `text-rich-vqa`, `multilingual`, `table` | - |
| CLIP4STR | [CLIP4STR: A Simple Baseline for Scene Text Recognition with Pre-trained Vision-Language Model](https://arxiv.org/abs/2305.14014) | arXiv 2023 / IEEE TIP 2024 | 将 CLIP 转化为场景文本识别器，结合视觉与跨模态分支以及 predict-and-refine 解码。 | `recognition`, `degraded`, `occlusion`, `scene-text` | [GitHub](https://github.com/VamosC/CLIP4STR) |
| Lumos | [Lumos: Empowering Multimodal LLMs with Scene Text Recognition](https://arxiv.org/abs/2402.08017) | KDD 2024 | 将场景文本识别集成到 MM-LLM 中，用于第一人称图像 QA。 | `recognition`, `scene-text`, `in-the-wild`, `text-rich-vqa` | N/A |
| Monkey | [Monkey: Image Resolution and Text Label Are Important Things for Large Multi-modal Models](https://arxiv.org/abs/2311.06607) | CVPR 2024 | 通过 patch 处理和多层次文本/物体描述支持更高分辨率的 MLLM 输入。 | `dense-text`, `high-resolution`, `document-qa`, `scene-text` | [GitHub](https://github.com/Yuliang-Liu/Monkey) |
| Ocean-OCR | [Ocean-OCR: Towards General OCR Application via a Vision-Language Model](https://arxiv.org/abs/2501.15558) | arXiv 2025 | 采用 Native Resolution ViT 的 3B MLLM，面向文档、场景文本和手写识别。 | `recognition`, `degraded`, `scene-text`, `handwriting` | [GitHub](https://github.com/guoxy25/Ocean-OCR) |
| VLENet | [VLENet: A Duet of Perception and Reasoning for Scene Text Recognition](https://www.sciencedirect.com/science/article/pii/S092523122502908X) | Neurocomputing 2026 | 使用 CLIP 视觉表征和 LLM，为模糊场景文本生成可能候选并进行推理。 | `recognition`, `degraded`, `scene-text`, `reasoning` | N/A |

[[⬆️ 返回顶部](#contents)]

<a id="complex-document-and-structured-ocr"></a>

### 📄 复杂文档与结构化 OCR

*本节将 hard OCR 定义为文档解析或文档理解。收录论文应至少处理一种结构性瓶颈：版面与阅读顺序、表格、公式、图表、多页上下文、KIE、grounding 或关系抽取，或忠实的 Markdown/HTML/LaTeX/JSON 风格输出。不显式针对这些结构挑战的普通 clean PDF-to-text OCR 不在本节范围内。*

| 方法/系统 | 论文 | Venue & Year | 亮点 | 标签 | 代码 |
|---|---|---|---|---|---|
| DocAttriBench 🆕 | [DocAttriBench](https://arxiv.org/abs/2609.20574v1) | arXiv 2026 | 文档 VQA 缺少把答案归因到版面要素的细粒度标注。作者提出 MAPPET,通过遮蔽候选要素并度量困惑度上升来归因答案,构建含 237k 文档、296k QA 的 DocAttriBench 基准。评测显示可 grounding 的 MLLM 常答对却定位错,揭示答案与归因间的差距。 | `document-qa`, `text-rich-vqa`, `layout` | - |
| WeVisDoc 🆕 | [WeVisDoc](https://arxiv.org/abs/2609.20423v1) | arXiv 2026 | 端到端文档解析受限于训练语料偏向清洁常见文档,且单纯扩覆盖不解决残存弱点。WeVisDoc 两阶段:data-centric 扩语义/结构/外观覆盖并合成退化,再用留出探针诊断残差并重分配 token 预算。4B 模型在 OmniDocBench v1.6 与 PureDocBench 三赛道均居首,退化赛道增益最大。 | `structured-output`, `layout`, `degraded` | - |
| Tables Decoded (DELTA/TARQA) 🆕 | [Tables Decoded (DELTA/TARQA)](https://arxiv.org/abs/2609.17458v1) | arXiv 2026 | 现有表格 VLM 将结构与内容耦合,多语言难扩展。DELTA 把物理/逻辑结构与 OCR 解耦,输出紧凑的 OTSL;TARQA 在 OTSL 上微调 LLM 做 TabVQA。发布 SOTA TSR 模型、印地语基准 TORQUE,并在 WTQ/FinTabNetQA 上大幅提升。 | `table`, `structured-output`, `multilingual` | [GitHub](https://github.com/Tihiitborg/Tables-Decoded) |
| TemplatedDocExtraction 🆕 | [TemplatedDocExtraction](https://arxiv.org/abs/2609.15706v1) | arXiv 2026 | VLM 文档抽取评测多报干净准确率,缺乏对实践者的选型指导。作者在 750 张合成支票上评测 11 套系统(商用、推理、开源 VLM、OCR-正则基线),并提出按任务画像最小化总成本的选择框架。3K 样本微调使开源 VLM 的 F1 超过 0.98。 | `KIE`, `structured-output`, `recognition` | - |
| VectorHarness 🆕 | [VectorHarness](https://arxiv.org/abs/2609.13294v1) | arXiv 2026 | 科学图形难以编辑,已有image-to-code方法只复制像素而未恢复可编辑结构。VectorHarness提出类型化语义授权表示,多智能体恢复文本、公式、图表与表格;发布VectorHarness-Bench,提升可执行编辑与关系保持能力。 | `structured-output`, `table/chart`, `formula` | - |
| CAVR-VET 🆕 | [CAVR-VET](https://arxiv.org/abs/2609.13268v1) | arXiv 2026 | 财报与信息图 PDF 中文本/表格/图表混排,扁平 top-k 视觉 RAG 一律同等处理性能差。系统在冻结 Qwen2.5-VL-7B 与 ColPali/VisRAG 之上插入能力路由 CAVR、弱到强页选择 WSPS(7B 可答性教师蒸馏到 3B 选择头)、以及按版面锚点串联≤3 条证据路径的 VET。在 DocVQA/ChartQA/InfoVQA 与多页 MMLongBench-Doc 上显著提升,多页 F1 由 19.2→22.6。 | `document-qa`, `table/chart`, `multi-page` | - |
| STEER 🆕 | [STEER](https://arxiv.org/abs/2609.13267v1) | arXiv 2026 | VLM 把科学图表当自然照片,自由 CoT 会读出图中没有的数字。STEER 在冻结 Llama-3.2-Vision 上插入图表结构图编码器 CSGE(绑定量轴/图例/数据标记)、证据锚定步骤推理 EASR(每步算术须引用图节点)、以及弱解析器-强推理对齐 WPSR。在 ChartQA 达 82.70、CharXiv reasoning 达 33.60,在 OCR 捷径消失的 ChartQAPro CoT 优势更明显。 | `reasoning`, `table/chart`, `document-qa` | - |
| DocHop 🆕 | [DocHop](https://arxiv.org/abs/2609.02059v1) | arXiv 2026 | 现有基准将图表与文档割裂评测。DocHop 用逻辑优先管线构造 2,074 条样本,由叙述给约束、图表给数值,要求跨六类任务做联合多跳推理。最优 MLLM 仅 62.83%,人类超 90%,差距显著。 | `reasoning`, `table/chart`, `document-qa` | - |
| MIDR 🆕 | [MIDR](https://arxiv.org/abs/2609.01316v1) | arXiv 2026 | 视觉富文档中的表格/图表/版面常被普通 OCR 线性化破坏。MIDR 是免训练的索引增强框架,在入库阶段用 MLLM 做抽取-校验-精炼得到文本字段,再用 BM25F+稠密混合检索服务查询。在 ViDoRe V3 上精度与 ColQwen2.5 持平,索引仅 1/9、延迟约 1/2,并将法语文档检索从 0.15 提升到 0.54 nDCG。 | `document-qa`, `structured-output`, `table/chart` | - |
| VeriOCRBench 🆕 | [VeriOCRBench](https://arxiv.org/abs/2609.00232v1) | arXiv 2026 | 现有 OCR 评测默认任务均可答,但真实图像常有模糊、遮挡、矛盾证据。VeriOCRBench 形式化 OCR 任务可验性(IP,TP,Q),发布 1800 条人工校验样本,含 8 类陷阱×4 校验维度共 1600 条无效任务及 200 条对照,评测 15 个 MLLM 揭示出普遍盲目顺从、诊断失误与诱导式过度拒绝问题。 | `reasoning`, `document-qa`, `degraded` | [GitHub](https://github.com/zy001122/Beyond-Blind-Compliance) |
| OCR-MetaReasoning 🆕 | [OCR-MetaReasoning](https://arxiv.org/abs/2608.30678v1) | arXiv 2026 | 文本富图像理解常将抽取与推理混淆,且不区分推理方向。OCR-MetaReasoning 发布 1500 条样本的 3×5 平衡基准(演绎/归纳/溯因 × 五类 OCR 对象),用 MRMS 衡量答案正确性、RPCS 衡量推理过程合规性。18 个 MLLM 评测显示远未饱和,最强模型 89.3 MRMS vs 人类 96.0。 | `reasoning`, `text-rich-vqa`, `layout` | [GitHub](https://github.com/gengxuli/OCR-MetaReasoning) |
| CENTURIA 🆕 | [CENTURIA](https://arxiv.org/abs/2608.30616v1) | arXiv 2026 | 考古陶器手绘档案上的手写元数据需人工转录,难以计算分析。CENTURIA 发布 Carnuntum 罗马遗址 507 条专家校验样本,含转录、框、7 类结构化字段,并评测 5 个 OCR 模型。零样本 15-32% 的转录误差在仅 57 样 LoRA 微调后降至 1.5% 以下,字段级准确率超 87%。 | `handwriting`, `historical`, `KIE` | [GitHub](https://github.com/gissuvalentina/CENTURIA) |
| DVBench 🆕 | [DVBench](https://arxiv.org/abs/2608.29711v1) | arXiv 2026 | 现有评测割裂图表与视频理解。DVBench 将数据视频理解分解为五个维度,含 300 个视频与 1,000 条人工核验问答。评测九个 MLLM,Gemini-3.1-Pro 总体最优,开源模型不随规模单调提升,叙述能力不等于视觉能力。 | `table/chart`, `reasoning`, `text-rich-vqa` | - |
| DocIntent 🆕 | [DocIntent](https://arxiv.org/abs/2608.29037v1) | arXiv 2026 | 真实退化(模糊、阴影、摩尔纹)损害文档 VQA,盲目修复反会引入伪影。DocIntent 是无需训练的智能体框架:先评估可答性,选择性调用修复工具,并用对比回滚撤销有害步骤。在 WildDoc 上稳定提升多个开源与闭源 MLLM。 | `degraded`, `document-qa`, `in-the-wild` | - |
| Synth-JDoc 🆕 | [Synth-JDoc](https://arxiv.org/abs/2608.28248v1) | arXiv 2026 | LVLM 识别竖排日文远逊横排,且复杂版面日文 OCR 数据稀缺。Synth-JDoc 用 HTML/CSS 合成 17,970 张文档图,混合竖横排、多栏、AI 配图,并施加扫描式与 Augraphy 噪声。在其上微调对竖排日文 OCR 提升最大,优于既有合成数据基线。 | `recognition`, `script-diverse`, `multilingual` | [GitHub](https://github.com/llm-jp/synth-jdoc) |
| MASON 🆕 | [MASON](https://arxiv.org/abs/2608.26716v1) | arXiv 2026 | VLM 能处理原子版面却难处理复合多层设计。作者提出该新任务,发布 CoDeLayout(约 2 万真实多层版面)与方法 MASON,通过多模态对齐与结构感知双阶段后训练缓解语义漂移与结构歧义。Qwen2.5-VL 7B + MASON 达 91.66%,超 GPT-o3 的 79.68%。 | `layout`, `document-qa`, `structured-output` | - |
| SCVER 🆕 | [SCVER](https://arxiv.org/abs/2608.28698v1) | arXiv 2026 | 文档解析需细粒度感知,而全局压缩视觉 token 每步都全量重读。SCVER 将感知建模为状态条件视觉证据检索:粗表征负责结构,按当前 token 动态检索高分辨率区域;SGLO 损失稳定隐式检索过程,计算量降 70% 以上而精度几乎无损。 | `structured-output`, `layout`, `high-resolution` | - |
| PlanSightRAG 🆕 | [PlanSightRAG](https://arxiv.org/abs/2608.26091v1) | arXiv 2026 | OCR 会丢掉解读土木 2D 标准图所需的几何与版面。PlanSightRAG 直接对图象检索与推理,用 ColNomic-3B 多向量检索与 Planner-Retriever-Auditor-Synthesizer 智能体管线,配 MaxSim 热图留痕。构建 4,056 对五州 DOT 基准,零样本 Recall@5 达 91.47%。 | `layout`, `document-qa`, `structured-output` | - |
| AWM 🆕 | [AWM](https://arxiv.org/abs/2608.25618v1) | arXiv 2026 | 长文档 VQA 智能体只检验最终答案正确性,忽视工作记忆能否独立支撑回答。AWM 将 memory-only answerability 作为 GRPO 奖励(AWM-GRPO),偏好答案正确且记忆可答的轨迹;在 MMLongBench-Doc/LongDocURL 上较 RAG 提升 8.1/11.9 点。 | `document-qa`, `long-context`, `multi-page` | [GitHub](https://github.com/DongzhuoranZhou/AWM) |
| RefLAM 🆕 | [RefLAM](https://arxiv.org/abs/2608.25140v1) | arXiv 2026 | 历史阿拉伯文手稿缺少可扩展的行级 HTR 标注。RefLAM 结合页面分割、MLLM 结构化 OCR 与去变音符模糊对齐,提出可证明的 Confidence-100 规则,通量提升 75 倍。发布 AraMS-28k:14 卷、3043 页、27971 行及基线微调结果。 | `recognition`, `historical`, `handwriting` | [GitHub](https://github.com/ArchaText/Reflam-pipeline) |
| WildHandBench 🆕 | [WildHandBench](https://arxiv.org/abs/2608.22959v1) | arXiv 2026 | 印刷文档 OCR 已超 96%,但手写文本仍被忽视。WildHandBench 收集 500 份手写文档,覆盖 4 语言、3 结构(正文/表格/公式)与 9 类真实场景,并提出 PDE 指标。18 个 MLLM 最佳仅 71.85%,人类 77.09%;模型错误 63-91% 为先验驱动。 | `recognition`, `handwriting`, `degraded` | - |
| FinixDoc-VL 🆕 | [FinixDoc-VL](https://arxiv.org/abs/2608.22842v1) | arXiv 2026 | 金融文档解析基准与真实部署差距大:模糊拍照、密集表格、超大页。FinixDoc-VL(基于 Qwen3-VL-4B)用同形异义字对比学习+多阶段 GRPO 复合奖励训练,配 Data Factory 流水线;FinixDocBench 覆盖拍照、超大页、内部金融流程,合规审校子集公开。 | `structured-output`, `table`, `recognition` | - |
| TwSG 🆕 | [TwSG](https://arxiv.org/abs/2608.22429v1) | arXiv 2026 | 图表与视觉表格存在空间-结构鸿沟,通用 MLLM 不借助裁剪工具会误读密集文本。TwSG 将多步区域感知蒸馏为单次前向(SFT 冷启动+TL-GRPO,标签级重要度采样与多维奖励),在降低延迟同时提升图表问答准确率。 | `reasoning`, `table/chart`, `recognition` | - |
| GapSight 🆕 | [GapSight](https://arxiv.org/abs/2608.21762v2) | arXiv 2026 | VLM 将图像压成低分辨率全局图时丢失细节答案。GapSight 用目标模型自身的损失差信号训练自由裁剪路由器,决定何时、何处重新聚焦。在 InternVL2.5-8B 上将六个 OCR/文档/图表/信息图基准的平均分从 52.25 提升到 64.29。 | `high-resolution`, `dense-text`, `document-qa` | - |
| LëtzCross 🆕 | [LëtzCross](https://arxiv.org/abs/2608.21714v1) | arXiv 2026 | 页面图检索器在跨语言低资源场景研究不足。作者构建卢森堡语 PDF 基准,含 908 页与 579 条英/法/德/卢四语 QA,覆盖文本与视觉落地查询。页图检索器优于 OCR 文本检索,含卢森堡语的多语微调效果最佳。 | `document-qa`, `multilingual`, `low-resource` | [GitHub](https://github.com/OmarElbachyr/letzcross-benchmark) |
| SmolDocling-KV 🆕 | [SmolDocling-KV](https://arxiv.org/abs/2608.20868v1) | arXiv 2026 | OCR 与下游抽取级联会逐级传播误差。作者微调 256M 的 SmolDocling VLM,一次性端到端完成键值抽取(识别、定位、关联),无需 OCR 前处理,扩展 DocTags 以支持多对多键值关系。结合合成表单与图裁剪增强,在 FUNSD/XFUND 上以 27 倍小模型超越零样本 Qwen2.5-VL (7B)。 | `KIE`, `structured-output`, `layout` | - |
| KoViDoRe 🆕 | [KoViDoRe](https://arxiv.org/abs/2608.20840v1) | arXiv 2026 | 韩语视觉文档检索缺乏针对英语外的多页基准。KoViDoRe 提供 57 文档/6,729 页/706 查询,平均每查询相关 2.94 页,覆盖四领域,并配套 31 万对 Ko-VDR Train Public 训练集。微调 colqwen2-v1.0 后将 nDCG@10 从 29.5 提到 52.8,超越 8B 的 Qwen3-VL-Embedding。 | `document-qa`, `multi-page`, `multilingual` | [GitHub](https://github.com/whybe-choi/kovidore-benchmark) |
| Q-Guide 🆕 | [Q-Guide](https://arxiv.org/abs/2608.19739v2) | arXiv 2026 | 文档 VQA 单次编码常看不清小字、表格与拓扑结构。Q-Guide 是阅读问题、判断缺什么证据、再调用读/放大/定位工具迭代数轮的小 agent;在 DocVQA2026、Manga109 与三款 Claude 上均胜过直出与多 agent 方案。 | `text-rich-vqa`, `document-qa`, `reasoning` | - |
| Institutional Newspapers Pipeline 🆕 | [Institutional Newspapers Pipeline](https://arxiv.org/abs/2608.18972v1) | arXiv 2026 | 历史报纸版式密集且不规则,难以计算访问。作者与波士顿公共图书馆共建模块化、低算力流水线(切版、按块 OCR、阅读序、NER、分类、语言检测、嵌入),并发布 1795–1930 年 147 万扫描、8310 万切块、163 亿 token 的开放数据集,同发布流水线与小模型。 | `recognition`, `historical`, `layout` | - |
| Iterative Sanskrit OCR Pipeline 🆕 | [Iterative Sanskrit OCR Pipeline](https://arxiv.org/abs/2608.18696v1) | arXiv 2026 | 复杂历史梵文写本版式异质、字形古旧,通用 OCR 难以胜任。作者提出可在版面层与外观层迭代微调的传统 OCR 流水线,逐页适配以减少专家标注,发布三份梵文写本的细粒度 PAGE-XML 数据集并对主流 MLLM 做基准。 | `recognition`, `historical`, `handwriting` | [GitHub](https://github.com/flame-cai/gnn-synthetic-layout-historical/) |
| DocClaw 🆕 | [DocClaw](https://arxiv.org/abs/2608.18685v1) | arXiv 2026 | OCR、DocQA、KIE 同需感知、取证与渐进细化,常被各自建模。DocClaw 将其统一为 agent—文档交互:依据文档技能迭代识别所需信息、调用工具并在共享的结构化文档状态中累积、回访与精修;在多个 IDP 基准上单框架即与通用 VLM 及专职方法相当。 | `document-qa`, `KIE`, `recognition` | - |
| OmniHandwritingOCR 🆕 | [OmniHandwritingOCR](https://arxiv.org/abs/2608.18586v1) | arXiv 2026 | MLLM 在真实手写 OCR 上的能力长期缺考,旧基准偏向印刷体或单行。作者整合 7.76 万标注图,覆盖英中文本与单/多行公式并按结构复杂度分层,以五种统一指标评测 13 个系统,揭示多行公式性能骤降与幻觉式纠正等失效模式。 | `recognition`, `handwriting`, `formula` | [GitHub](https://github.com/ECNU-RAIL/OmniHandwritingOCR-CIKM2026) |
| Open-Model Structured Extraction Benchmark 🆕 | [Open-Model Structured Extraction Benchmark](https://arxiv.org/abs/2608.18289v1) | arXiv 2026 | 开源 OCR+LLM 与 VLM 在高风险公文结构化抽取上缺系统评测。作者在 100 份成绩单 PDF 上统一评测 6 个 OCR 引擎、5 个 Qwen3 与 5 个 VLM,35 个零样本配置中仅 4 个 F1>0.5,并指出 OCR 输出的结构保持比模型规模更关键。 | `KIE`, `structured-output`, `document-qa` | - |
| CADP-Bench 🆕 | [CADP-Bench](https://arxiv.org/abs/2608.17550v1) | arXiv 2026 | 学术页面的表格、公式、图表、伪代码等结构在 Markdown 中难以保真。作者提出可编译学术文档解析范式,将页面重构为上下文 LaTeX + 可执行 Python,发布 1,630 张专家标注的多结构页面基准与回灌编译评测协议;前沿 MLLM 仍难做高保真可执行重构。 | `structured-output`, `formula`, `table/chart` | [GitHub](https://github.com/AriKing11/CADP-Bench) |
| MoCA 🆕 | [MoCA](https://arxiv.org/abs/2608.15510v1) | arXiv 2026 | 图表转代码需先读图再写码。MoCA 将视觉与代码能力解耦为双分支,引入轻量仲裁器按 token 与层动态分配权重,先以自蒸馏推理轨迹做 SFT,再用多维奖励 RL 微调。 | `table/chart`, `structured-output`, `reasoning` | - |
| Trident 🆕 | [Trident](https://arxiv.org/abs/2608.14841v1) | arXiv 2026 | 长文档多模态 VQA 的瓶颈在重排选证据:纯文本片段重排会漏掉表格、图表与版面。Trident 把每页标注为语义记录(视觉描述、章节路径、实体、概念命中)做自适应 K 重排,并加多视角生成模块。 | `document-qa`, `multi-page`, `long-context` | - |
| Chartography 🆕 | [Chartography](https://arxiv.org/abs/2608.10677v1) | ECCV 2026 Workshop (BEAM) | 现有图表基准集中在柱/折线/饼图且趋于饱和。Chartography 收集 100 个来自专业实践的图表任务,问题由从业人员撰写并经三位专家独立验证;30 个前沿模型配置最高仅 45.0% pass@1,暴露模型在细微视觉特征、稀疏坐标轴与 3D 几何上的感知短板。 | `table/chart`, `reasoning`, `document-qa` | - |
| InSight-doc 🆕 | [InSight-doc](https://arxiv.org/abs/2608.10628v1) | arXiv 2026 | 长文档视觉问答对所有页高分辨率编码代价高、易上下文退化。InSight-doc 把视觉分辨率当作推理时自适应资源:低分辨率起步,agent 式无检索器地 zoom-in 到高分辨率区域,并用 17.9K zoom-in 轨迹与 19.2K 困难 RL 样本做 SFT+RL 训练;在长文档上将准确率提升 4.3--16.4 点,幻觉降逾 40%,延迟降 41--68%。 | `document-qa`, `long-context`, `multi-page` | [GitHub](https://github.com/m-Just/InSight-doc) |
| DEC / TableParseMap 🆕 | [DEC / TableParseMap](https://arxiv.org/abs/2608.09842v1) | arXiv 2026 | 聚合分数掩盖了真实复杂表格的持续失败。作者构建 TableParseMap(916 表、5 场景、9 失败类型),并提出 DEC:用通用 VLM 作控制器,对冻结 解析器执行分解-增强-纠错,配合视觉一致性门控与排序器。平均 TEDS +1.57,大表格上提升达 5.66。 | `table`, `structured-output`, `layout` | - |
| JapanDocReader 🆕 | [JapanDocReader](https://arxiv.org/abs/2608.06758v1) | arXiv 2026 | 向推理型多模态模型注入日语结构化文档解析能力会引发 VQA 遗忘。JapanDocReader 采用混合 SFT 加 DAPO 解析强化学习,以 JSON 校验门控奖励与方差过滤 prompt,在保留文档问答的同时取得结构化解析 SOTA(Overall 87.67)。 | `recognition`, `structured-output`, `layout` | - |
| BICR 🆕 | [BICR](https://arxiv.org/abs/2608.06532v1) | arXiv 2026 | 金融 LVLM 在图表与文档上常有自信却错误,部署瓶颈在可信度而非准确率。作者在五个开源 LVLM 与四项金融 VQA 条件下评估七种置信度估计器,提出接地感知探针 BICR,唯一能在模型未看图作答时主动降低置信度。 | `text-rich-vqa`, `table/chart`, `document-qa` | - |
| PaDoc 🆕 | [PaDoc](https://arxiv.org/abs/2608.06146v1) | arXiv 2026 | 端到端文档解析把版式与内容串行化,延迟随总内容增长。PaDoc 将预测版式作为共享页编码上的分支结构,经 ancestor attention 与共享前缀 KV 复用实现区域并行解码,在 OmniDocBench 上达顶级质量,吞吐提升 67-118%。 | `recognition`, `layout`, `structured-output` | [GitHub](https://github.com/Longin-Yu/Padoc) |
| MinerU-Chem 🆕 | [MinerU-Chem](https://arxiv.org/abs/2608.03525v3) | arXiv 2026 | 化学论文的分子结构以图像呈现,通用解析器无法读取。MinerU-Chem 在 MinerU 之上新增五个化学专用模块并使用 CARBON 表示,实现分子结构识别与反应方案解析,在 MolRecBench-Wild 上 SMILES 精确匹配达 93.02%,领先 GPT-5.6-Sol 18.15 个百分点。 | `formula`, `structured-output`, `recognition` | - |
| DocTrace 🆕 | [DocTrace](https://arxiv.org/abs/2608.03292v1) | arXiv 2026 | 长文档 VQA 缺乏显式机制追踪多页证据的形成。DocTrace 将其建模为分层证据图推理,带节点级来源,通过 SFT 与 GRPO 两阶段训练;在 MMLongBench-Doc、LongDocURL、SlideVQA 上较 Qwen3-VL-8B 提升 14.4/11.3/11.7 分。 | `document-qa`, `reasoning`, `multi-page` | - |
| CURV 🆕 | [CURV](https://arxiv.org/abs/2608.02833v1) | arXiv 2026 | MLLM 在图表问答上缺乏内蕴视觉 grounding 推理。CURV 将 CQA 重构为多步视觉 grounding 推理配合动态空间注意力,以三级课程数据集 CCQA 训练;较基线最高提升 20.5%,并泛化到真实与跨域多模态基准。 | `table/chart`, `reasoning`, `document-qa` | - |
| LongChart 🆕 | [LongChart](https://arxiv.org/abs/2608.01328v1) | arXiv 2026 | 现有图表基准偏单图感知,欠缺多图推理。作者提出 LongChart,通过潜在图合成流水线,VQA 集平均含 6.5 张图与 31.2 个问题;评测 10 个 MLLM 显示准确率随复杂度急剧下降,揭示多图推理的缺口。 | `table/chart`, `document-qa`, `reasoning` | - |
| DeCoRAG 🆕 | [DeCoRAG](https://arxiv.org/abs/2607.24554v1) | arXiv 2026 | 多模态 Graph RAG 在密集版面上因“视觉注意力汇聚”丢失语义。DeCoRAG 以语义锚点、RAP-Crop 区域裁剪与锚点引导抽取三段解耦构建图谱,最高提升 12.5pp 语义通过率,离线提示 token 减少 40.8%。 | `reasoning`, `document-qa`, `layout` | - |
| LayoutLite 🆕 | [LayoutLite](https://arxiv.org/abs/2607.22200v1) | arXiv 2026 | VLM 文档 OCR 大量视觉 token 耗在空白区,通用压缩又易损文字细节。LayoutLite 在视觉编码器与解码器之间做 token 级隐式版面打分,以 GRPO 与 OCR 一致性奖励剪枝低信息 token;50% 压缩下精度几乎不变,prefill、FLOPs 与 KV 缓存节省逾 40%。 | `recognition`, `layout`, `structured-output` | [GitHub](https://github.com/dpxudong/LayoutLite/) |
| Khondo 🆕 | [Khondo](https://arxiv.org/abs/2607.21780v1) | arXiv 2026 | 政府多文档拼包在低资源孟加拉语中难切分,而 OCR 不可靠。Khondo 是首个面向孟加拉政务表的视觉原生基准,含 1,950 拼包、14 领域、5 种拼接方案。零样本 MLLM 评测显示聚类尚可,但页序在打乱后崩塌;英文包顺序恢复更佳。 | `multilingual`, `low-resource`, `layout` | - |
| Multi-VIE 🆕 | [Multi-VIE](https://arxiv.org/abs/2607.22723v1) | Sci. Rep. 2026 | 视觉富文档 VIE 受版面多变与真实退化困扰。框架将文档类型分类与内容抽取解耦,基于 Qwen2.5-VL-7B 用 ICL 动态提示做零样本推理,在 16 类证书上 F1 超监督基线 18.35 点;领域微调可达 93.65% F1。 | `KIE`, `structured-output`, `layout` | [GitHub](https://github.com/FairmeHIT/Multi-VIE) |
| DocAtlas 🆕 | [DocAtlas](https://arxiv.org/abs/2608.07527v1) | arXiv 2026 | 长文档问答需要跨页证据整合。DocAtlas 提供可变文档外壳,在固定上下文预算下暴露搜索、阅读、笔记与审阅工具。GPT-5.4 在 MMLongBench-Doc 上达 71.4%;在该环境中用 RL 训练的 4B VLM 达 63.7%。 | `document-qa`, `multi-page`, `long-context` | - |
| XL-DocBench 🆕 | [XL-DocBench](https://arxiv.org/abs/2608.00036v1) | arXiv 2026 | 专业场景常需从上千页文档中给出可溯源答案。XL-DocBench 收录 1519 道人工审核题、覆盖 6 个专业领域、最长 2303 页;72.6% 需多页证据,36.6% 含表格/图表/图示,并附推理标签、证据页与验证规则。 | `multi-page`, `long-context`, `document-qa` | - |
| HPD-Parsing 🆕 | [HPD-Parsing](https://arxiv.org/abs/2607.18839v1) | arXiv 2026 | 统一 VLM 文档解析受自回归串行瓶颈所限。HPD-Parsing 改用分层并行解码:主版面分支调度并发块分支,渐进多 token 预测进一步减少步数。吞吐达 4752 tok/s,是最快方法的 2.62 倍,且保持有竞争力的精度。 | `structured-output`, `layout`, `recognition` | - |
| OvisOCR2 🆕 | [OvisOCR2](https://arxiv.org/abs/2607.13639v1) | arXiv 2026 | 端到端文档解析需按阅读序输出覆盖正文、公式、表格的 Markdown。OvisOCR2(0.8B)用 SFT、4B 分支多分量奖励 RL、在策略蒸馏与模型融合训练,在 OmniDocBench 以 96.58 登顶,PureDocBench Avg3 达 75.06,展示端到端解析可超越流水线方法。 | `recognition`, `structured-output`, `layout` | - |
| TestHallVQA 🆕 | [TestHallVQA](https://arxiv.org/abs/2609.13158v1) | arXiv 2026 | 现有平面 VQA 基准在长文档检索与清晰单图推理间割裂。TestHallVQA 构建考试文档多图 VQA 基准(10,242 QA、7,155 图),可注入多级冗余上下文,并提出 F1-R2 指标联合度量冗余下的推理与检索鲁棒性;在约 20 个 LVLM 上揭示性能骤降且规模化无法缓解视觉污染。 | `text-rich-vqa`, `long-context`, `multi-page` | [GitHub](https://github.com/yqyu2317/TestHallVQA-benchmark) |
| From Pixels to Pairs 🆕 | [From Pixels to Pairs](https://arxiv.org/abs/2609.17538v1) | arXiv 2026 | LLM 在真实 OCR 噪声下的键值抽取行为缺乏系统研究。该工作在 FUNSD/CORD/SROIE 上用统一协议评测多款 LLM,搭配 Gold 文本与 PaddleOCR/EasyOCR/Tesseract 输出,揭示 OCR 噪声导致显著退化、模型差距随噪声收敛,并归纳键值错位、数字损坏等典型失败模式。 | `KIE`, `structured-output`, `degraded` | - |
| MonkeyOCRv2 🆕 | [MonkeyOCRv2](https://arxiv.org/abs/2607.11562v1) | arXiv 2026 | 自然图像预训练编码器对密集文本与细粒度笔画的文档迁移效果差。MonkeyOCRv2 在 1.13 亿图、17 语言的 MonkeyDoc v2 上联合学习图生文与像素级重建,保留字形笔画与版面;作为冻结视觉编码器在 MDPBench 上以 0.7B 模型超越 3B dots.mocr 2.8%,并在五项文档分析任务上稳定增益。 | `recognition`, `formula`, `structured-output` | [GitHub](https://github.com/Yuliang-Liu/MonkeyOCRv2) |
| GDP.pdf 🆕 | [GDP.pdf](https://arxiv.org/abs/2607.11192v3) | CVPR 2026 Workshop | 现有文档 AI 基准孤立评测能力,难以反映真实专业 PDF 问题。GDP.pdf 由 10 个领域从业者在实际工作流中作者 100 道题,仅保留至少两个前沿多模态模型出错的条目,配备原子评分细则并按 11 项能力打标;十七个前沿模型评测中最好仅通过 30.7%,常在表格、图表、脚注、空间推理上失败。 | `document-qa`, `structured-output`, `table/chart` | [GitHub](https://github.com/surge-ai/gdp-pdf) |
| SynthDocBench 🆕 | [SynthDocBench](https://arxiv.org/abs/2607.10400v1) | arXiv 2026 | 真实文档中长度、版面、模态、难度相互混杂,难以归因 VLM 失败。SynthDocBench 是完全合成的长上下文基准(平均 51.1 页,六种版式,双层图表生成,1,788 题),独立变化各因子;在七个前沿 VLM 上揭示长度退化、中段位置敏感与长文档下图表理解崩塌三类失败模式。 | `synthetic-hard`, `long-context`, `layout` | [GitHub](https://github.com/ServiceNow/SynthDocBench) |
| Infinity-Parser2 🆕 | [Infinity-Parser2](https://arxiv.org/abs/2607.07836v3) | arXiv 2026 | 文档解析受限于表格/公式/图表/阅读顺序的高质量标注稀缺。Infinity-Parser2 将可控渲染+迭代精修合成引擎与可验证多任务 RLVR 结合,联合训练八项目标(解析、版面、表格、数学、图表、化学式、文档 VQA、通用多模态理解),开源中英双语 500 万样本 Infinity-Doc2-5M。Pro 版在 olmOCR-Bench 达 87.6%、ParseBench 74.3%,超越 DeepSeek-OCR-2 等。 | `recognition`, `layout`, `structured-output` | [GitHub](https://github.com/infly-ai/INF-MLLM) |
| HunyuanOCR-1.5 🆕 | [HunyuanOCR-1.5](https://arxiv.org/abs/2607.04884v3) | arXiv 2026 | 轻量 OCR VLM 在密集文档上面临延迟-能力权衡。HunyuanOCR-1.5 将 DFlash 草稿式解码适配到 OCR 实现 6.37×/2.14× 加速,并引入 Agentic Data Flow 自动构建弱点导向训练数据。模型在 OmniDocBench v1.6 上达到顶级水平,并扩展到古文字与 331 种语言。 | `recognition`, `structured-output`, `multilingual` | [GitHub](https://github.com/Tencent-Hunyuan/HunyuanOCR) |
| ClinOCR-Bench 🆕 | [ClinOCR-Bench](https://arxiv.org/abs/2607.03650v1) | arXiv 2026 | 临床扫描文档(化验单、表单)是 OCR 长期痛点,既有研究多使用私有数据。作者发布 ClinOCR-Bench,含 384 张扫描图像、六类子集(正常/手写/低质/旋转/表格/混合伪影),并对主流开源与商业 VLM 给出基线评测。 | `recognition`, `degraded`, `handwriting` | [GitHub](https://github.com/ClinOCR-Bench/ClinOCR-Bench) |
| MORE 🆕 | [MORE](https://arxiv.org/abs/2607.02956v1) | arXiv 2026 | 现有文档解析基准偏重英文与中文,长尾语言成为评测盲区。作者发布 MORE:覆盖 149 种语言、1,288 页真实文档,带文本/公式/表格/代码/目录/阅读顺序结构标注。对主流 VLM 与专用 OCR 模型的基线评测揭示长尾语言与结构化解析的薄弱环节。 | `multilingual`, `low-resource`, `script-diverse` | [GitHub](https://github.com/zimoqingfeng/MORE) |
| Max-Regret Reading Order 🆕 | [Max-Regret Reading Order](https://arxiv.org/abs/2607.01018v1) | arXiv 2026 | 《格罗萨》等手稿中心文字被注释以非矩形方式环绕,阅读顺序难定。作者在 OCR 文本行上构造图,以 CLM 与 BERT-NSP 评分,再用 max-regret 路径覆盖规则恢复阅读顺序。Glossa 上达成 95% 后继准确率,OmniDocBench 多栏页面 88%,优于 XY-cut 与 LayoutReader。 | `layout`, `structured-output`, `multi-page` | - |
| Hybrid Armenian RO 🆕 | [Hybrid Armenian RO](https://arxiv.org/abs/2607.00596v1) | arXiv 2026 | 历史亚美尼亚报纸版面复杂、语言资源稀缺。作者标注 66 页,对比几何启发式、YOLO、ECLAIR 与语义分区检测+生成式 LLM 的混合方法。混合方法将排序错误降低最高 76%,在 OCR 噪声下稳健,并发布针对历史亚美尼亚印刷的 Tesseract 模型。 | `historical`, `low-resource`, `script-diverse` | - |
| DLVQA 🆕 | [DLVQA](https://arxiv.org/abs/2606.28780v1) | arXiv 2026 | 受限于上下文窗口且现有 KG-RAG 只处理文本,MLLM 难做整篇文档 VQA。作者从视觉丰富文档构建多模态知识图谱用于图 RAG,并发布 DLVQA 基准(含参考摘要与支持事实),在多跳 QA/VQA 上优于 MMRAG 与 KG 基线。 | `document-qa`, `layout`, `multi-page` | - |
| P-MTP 🆕 | [P-MTP](https://arxiv.org/abs/2606.24447v1) | arXiv 2026 | VLM 文档解析在密集文本页上受推理延迟制约,而多 token 预测加深时优化不稳。P-MTP 引入渐进式课程损失与置信度门控动态起草,扩展前瞻深度,以可忽略精度损失换取最高 5 倍加速,首次验证文档解析中的深度前瞻 MTP。 | `structured-output`, `dense-text`, `long-context` | - |
| ExtractConf 🆕 | [ExtractConf](https://arxiv.org/abs/2606.24420v1) | arXiv 2026 | LLM 文档字段抽取的核心瓶颈在于可靠的置信度估计。ExtractConf 融合两次非对称读取(模式引导的 Hunter 与全文扫描的 Mapper)与 LLM 不确定度、OCR、图像质量、版面特征。在 DocILE 上 ROC AUC 达 0.928,选择风险降 70%,并零样本迁移到 CORD 票据。 | `KIE`, `structured-output`, `reasoning` | - |
| PreciseDoc 🆕 | [PreciseDoc](https://arxiv.org/abs/2606.24118v2) | arXiv 2026 | 现有大模型在富文本文档图上的元素定位精度差,影响推理可靠性。PreciseDoc 合成带相机效应的填写文档以提供细粒度坐标监督,并用强化学习联合训练定位与推理,提升文档空间定位与 VQA 表现。 | `localization`, `document-qa`, `dense-text` | - |
| Unlimited OCR 🆕 | [Unlimited OCR](https://arxiv.org/abs/2606.23050v1) | arXiv 2026 | 以 LLM 为解码器的 OCR 随输出变长 KV 缓存膨胀而变慢,与人类长抄写形成对比。Unlimited OCR 用参考滑动窗注意力替换解码器注意力,保持 KV 缓存恒定,32K 单次前向可转录数十页;R-SWA 亦可迁移至 ASR、翻译。 | `recognition`, `multi-page`, `long-context` | [GitHub](http://github.com/baidu/Unlimited-OCR) |
| AtomCite | [AtomCite](https://arxiv.org/abs/2609.05802v1) | arXiv 2026 | 多页文档问答中模型给出的页级引用常出错,但此前没有基准核验文档图像上已提供的引用。AtomCite 将答案拆为原子声明,用并行文本与图像子代理逐条对照所引页面,再按确定性策略执行修正。DocCite 基准显示图像感知验证在三族模型上全面优于 OCR-only 与提示式基线。 | `multi-page`, `document-qa`, `reasoning` | - |
| KhatianDoc | [KhatianDoc](https://arxiv.org/abs/2609.03597v1) | arXiv 2026 | 孟加拉手写地契 RS Khatian 使用 Ana-Ganda 十六进制分数系统,字体与分词器均无支持,任何 OCR 管线与多模态大模型都无法识别。KhatianDoc 基于 107 份律师校验的真实记录构建四任务基准(符号识别、十六进制算术、字段抽取、问答),零样本评测六个多模态大模型,揭示能力缺失而非性能差距,并发布脱敏数据与代码。 | `recognition`, `low-resource`, `handwriting` | - |
| OCR-EDR | [OCR-EDR](https://arxiv.org/abs/2609.03445v1) | arXiv 2026 | OCR 在公式与结构化文本上仍常错,聚合指标掩盖 case 级错误。OCR-EDR 把诊断-编辑-重渲染建成闭环;DocEDR (Qwen3.5-9B) 经 verifier SFT、课程式修复与 GRPO 三阶段训练。作者发布 OCRErrBench(900 例,含精确与渲染等价正例及真错误),并在外部公式基准上获得可验证增益。 | `recognition`, `formula`, `structured-output` | - |
| Jina-OCR-v1 | [Jina-OCR-v1](https://arxiv.org/abs/2609.03181v1) | arXiv 2026 | 端到端文档解析 VLM 在低端 GPU 上推理代价高,公式与表格结构奖励覆盖不足。Jina-OCR-v1 在 DeepSeek-OCR 压缩视觉编码器与 3B MoE 解码器上加入复用的 FastMTP 投机解码头,并结合 SFT 与基于公式/表格稠密可验证奖励的 GRPO 后训练。模型在主流解析榜单匹敌更大系统,同时在低端 GPU 保持高吞吐。 | `recognition`, `structured-output`, `table` | - |
| LeakageBench | [LeakageBench](https://arxiv.org/abs/2609.02207v1) | arXiv 2026 | 文档图像 PII 脱敏在 OCR 出错或版面干扰时会泄露标识符。LeakageBench 提供 500 张文档图像与 11,954 条 GDPR 对齐的 PII 标注,覆盖直接、链路与上下文三类标识符。即使最强的 OCR 流水线与 OCR-free VLM,关键页级泄漏率仍居高不下。 | `localization`, `KIE`, `recognition` | - |
| DADC-DocVLM | [DADC-DocVLM](https://arxiv.org/abs/2609.01575v1) | arXiv 2026 | 受监管行业面临文档 VLM 的成本-质量鸿沟:PII 禁用云端模型,小模型达不到质量门槛,大模型又不划算。我们在单卡 H100 上部署 MoE VLM(总 35B、激活 3B),以难度感知数据筛选流水线在 30 万 CC PDF 上微调;性能超越大一个量级的可部署基线,相较人工标注降本逾 80%。 | `KIE`, `structured-output`, `layout` | - |
| LongDocBench | [LongDocBench](https://arxiv.org/abs/2608.15064v1) | arXiv 2026 | 长文档 TOC 层级与上下文关系恢复基准;85 篇文档 2,582 页,含 3,937 标题节点与 3,258 关系。 | `long-context`, `multi-page`, `layout` | - |
| NaviDC-OCR | [NaviDC-OCR](https://arxiv.org/abs/2608.12898v1) | arXiv 2026 | 针对数字与拍摄文档的统一解析框架;OmniDocBench 96.87、Wild-OmniDocBench 88.53、PureDocBench 78.41 达 SOTA。 | `structured-output`, `layout`, `table` | [GitHub](https://github.com/caipeng328/NaviDC-OCR) |
| TongGuOCR | [TongGuOCR](https://arxiv.org/abs/2608.07917v2) | arXiv 2026 | 面向中文历史文档的版面感知 OCR MLLM;M5HisDoc AR 93.76,显著降低 NED/RO-ED。 | `recognition`, `historical`, `layout` | [GitHub](https://github.com/jzzh2004/TongGuOCR) |
| Q-CueGraph | [Q-CueGraph](https://arxiv.org/abs/2608.04452v1) | arXiv 2026 | 查询条件视觉证据图,复用 OCR/版面图;V*Bench 0.833,仅用 19% 图像区域。 | `text-rich-vqa`, `layout`, `localization` | - |
| ConfBench | [ConfBench](https://arxiv.org/abs/2608.01792v1) | arXiv 2026 | 首个面向 KIE 的校准基准;20 条受控退化管线,1346 变体,70K+ 实体评测。 | `KIE`, `degraded`, `dense-text` | - |
| FAU ImageCLEF 2026 | [FAU ImageCLEF 2026](https://arxiv.org/abs/2608.01664v1) | arXiv 2026 | ImageCLEF 2026 多模态推理系统;Visual MCQ 第三、Visual OpenQA 第一。 | `text-rich-vqa`, `multilingual`, `table` | - |
| DocPO | [DocPO](https://arxiv.org/abs/2608.00536v3) | arXiv 2026 | 文档策略优化框架,步感知退火奖励覆盖文本/表格/公式;在 OmniDocBench 与 DocElemHard 提升 GRPO。 | `structured-output`, `table`, `formula` | - |
| HierDoc | [HierDoc](https://arxiv.org/abs/2607.29638v1) | arXiv 2026 | 分层页到区证据路由框架,两阶段集合预测配 GRPO;LongDocURL 相对提升 16.87%。 | `multi-page`, `long-context`, `document-qa` | - |
| DeepSeek-OCR | [DeepSeek-OCR: Contexts Optical Compression](https://arxiv.org/abs/2510.18234) | arXiv 2025 | 面向长文本上下文的光学二维映射与视觉压缩。 | `recognition`, `dense-text`, `long-context` | [GitHub](https://github.com/deepseek-ai/DeepSeek-OCR) |
| GLM-OCR | [GLM-OCR Technical Report](https://arxiv.org/abs/2603.10910) | arXiv 2026 | 采用两阶段 layout-to-recognition pipeline 的紧凑多模态 OCR 模型。 | `recognition`, `layout`, `formula`, `KIE` | [GitHub](https://github.com/zai-org/GLM-OCR) |
| GOT-OCR2.0 | [GOT-OCR2.0: General OCR Theory](https://arxiv.org/abs/2409.01704) | arXiv 2024 | 统一端到端 OCR-2.0 模型，处理文本、公式、表格、图表、乐谱和几何图形。 | `recognition`, `structured-output`, `formula`, `table/chart` | [GitHub](https://github.com/Ucas-HaoranWei/GOT-OCR2.0) |
| KOSMOS-2.5 | [KOSMOS-2.5: A Multimodal Literate Model](https://arxiv.org/abs/2309.11419) | arXiv 2023 | 面向文本密集图像、空间文本块和结构化文本输出的 literate VLM。 | `recognition`, `dense-text`, `structured-output` | [GitHub](https://github.com/microsoft/unilm/tree/master/kosmos-2.5) |
| MonkeyOCR v1.5 | [MonkeyOCR v1.5: Unlocking Robust Document Parsing for Complex Patterns](https://arxiv.org/abs/2511.10390) | arXiv 2025 | 面向复杂模式的两阶段 VLM 文档解析框架。 | `recognition`, `layout`, `structured-output` | [GitHub](https://github.com/Yuliang-Liu/MonkeyOCR) |
| MonkeyOCR | [MonkeyOCR: Document Parsing with a Structure-Recognition-Relation Triplet Paradigm](https://arxiv.org/abs/2506.05218) | arXiv 2025 | 基于结构-识别-关系三元范式的文档解析器。 | `recognition`, `layout`, `structured-output` | [GitHub](https://github.com/Yuliang-Liu/MonkeyOCR) |
| PaddleOCR-VL | [PaddleOCR-VL: Boosting Multilingual Document Parsing via a 0.9B Ultra-Compact Vision-Language Model](https://arxiv.org/abs/2510.14528) | arXiv 2025 | 面向多语种文档解析和元素识别的紧凑型 VLM。 | `recognition`, `multilingual`, `table/chart`, `formula` | [GitHub](https://github.com/PaddlePaddle/PaddleOCR) |
| PaddleOCR-VL-1.5 | [PaddleOCR-VL-1.5: Towards a Multi-Task 0.9B VLM for Robust In-the-Wild Document Parsing](https://arxiv.org/abs/2601.21957) | arXiv 2026 | 面向真实世界鲁棒文档解析的多任务紧凑型 VLM。 | `recognition`, `layout`, `table/chart`, `formula` | [GitHub](https://github.com/PaddlePaddle/PaddleOCR) |
| Qianfan-OCR | [Qianfan-OCR: A Unified End-to-End Model for Document Intelligence](https://arxiv.org/abs/2603.13398) | arXiv 2026 | 4B VLM，使用 Layout-as-Thought 在最终输出前进行显式版面推理。 | `layout`, `structured-output`, `reasoning`, `KIE` | [GitHub](https://github.com/baidubce/Qianfan-VL) |
| TextMonkey | [TextMonkey: An OCR-Free Large Multimodal Model for Understanding Document](https://huggingface.co/papers/2403.04473) | arXiv 2024 / TPAMI 2026 | 面向高分辨率文档、截图、spotting 和 grounding 的文本中心 MLLM。 | `recognition`, `localization`, `dense-text` | [GitHub](https://github.com/Yuliang-Liu/Monkey) |
| UReader | [UReader: Universal OCR-free Visually-situated Language Understanding with Multimodal Large Language Model](https://arxiv.org/abs/2310.05126) | EMNLP Findings 2023 | OCR-free MLLM，面向文档、表格、图表、自然图像和网页截图。 | `recognition`, `dense-text`, `document-qa`, `structured-output` | [GitHub](https://github.com/LukeForeverYoung/UReader) |
| dots.ocr | [dots.ocr: Multilingual Document Layout Parsing in a Single Vision-Language Model](https://arxiv.org/abs/2512.02498) | arXiv 2025 | 单一 VLM 同时进行多语种版面检测、文本识别和关系理解。 | `recognition`, `layout`, `multilingual` | [GitHub](https://github.com/rednote-hilab/dots.ocr) |
| mPLUG-DocOwl2 | [mPLUG-DocOwl2: High-resolution Compressing for OCR-free Multi-page Document Understanding](https://aclanthology.org/2025.acl-long.291/) | ACL 2025 | 基于高分辨率压缩的 OCR-free 多页文档理解。 | `layout`, `multi-page`, `document-qa` | [GitHub](https://github.com/X-PLUG/mPLUG-DocOwl) |
| olmOCR 2 | [olmOCR 2: Unit Test Rewards for Document OCR](https://huggingface.co/papers/2510.19817) | arXiv 2025 | 通过可验证单元测试奖励进行结构化文档 OCR 强化学习。 | `structured-output`, `formula`, `table`, `layout` | [GitHub](https://github.com/allenai/olmocr) |

[[⬆️ 返回顶部](#contents)]

<a id="script-diverse-historical-and-handwritten-ocr"></a>

### ✍️ 脚本多样、历史与手写 OCR

*本节将 hard OCR 定义为脚本、书写风格或历史域偏移下的识别或 OCR 中心理解。收录论文应至少处理以下挑战之一：低资源或非拉丁脚本、脚本特定正字法复杂性、历史或古代文档、书法、手写、手写公式，或稀有脚本的视觉释读。高资源脚本中的普通现代印刷体 OCR 不在本节范围内，除非论文明确针对上述挑战之一。*

| 方法/系统 | 论文 | Venue & Year | 亮点 | 标签 | 代码 |
|---|---|---|---|---|---|
| ExpertHTR 🆕 | [ExpertHTR](https://arxiv.org/abs/2609.12705v1) | arXiv 2026 | 手写数据集在语言、脚本与格式上差异大,联合训练困难。ExpertHTR用统一Page-Region-Line表示构造四个互补任务,并引入共享专家稀疏MoE解码器(Sparsegen路由)。在七个异质基准上超越通用OCR/VLM,并在IAM段落级上达到SOTA。 | `recognition`, `handwriting`, `multilingual` | [GitHub](https://github.com/DAIR-Group/ExpertHTR) |
| CENTURIA 🆕 | [CENTURIA](https://arxiv.org/abs/2608.30616v1) | arXiv 2026 | 考古陶器手绘档案上的手写元数据需人工转录,难以计算分析。CENTURIA 发布 Carnuntum 罗马遗址 507 条专家校验样本,含转录、框、7 类结构化字段,并评测 5 个 OCR 模型。零样本 15-32% 的转录误差在仅 57 样 LoRA 微调后降至 1.5% 以下,字段级准确率超 87%。 | `handwriting`, `historical`, `KIE` | [GitHub](https://github.com/gissuvalentina/CENTURIA) |
| KTRWS 🆕 | [KTRWS](https://arxiv.org/abs/2608.30213v1) | arXiv 2026 | 高棉文无词间分隔符,传统流水线需独立分词模型,延迟与误差叠加。作者提出统一 CTC 模型,通过二值边界标志在同模型内联完成识别与分词。还发布首份带词边界标注的高棉文文本行数据集,在文档、场景、手写三类模态上 CTR 表现具竞争力。 | `recognition`, `low-resource`, `script-diverse` | - |
| Synth-JDoc 🆕 | [Synth-JDoc](https://arxiv.org/abs/2608.28248v1) | arXiv 2026 | LVLM 识别竖排日文远逊横排,且复杂版面日文 OCR 数据稀缺。Synth-JDoc 用 HTML/CSS 合成 17,970 张文档图,混合竖横排、多栏、AI 配图,并施加扫描式与 Augraphy 噪声。在其上微调对竖排日文 OCR 提升最大,优于既有合成数据基线。 | `recognition`, `script-diverse`, `multilingual` | [GitHub](https://github.com/llm-jp/synth-jdoc) |
| UniLipi 🆕 | [UniLipi](https://arxiv.org/abs/2608.28195v1) | arXiv 2026 | 印度 Manuscript OCR 多为一脚本一模型,定制重、难扩展。UniLipi 用单一 hybrid CNN-Transformer 联合训练 13 种印度脚本,统一输出 Roman-WX,并通过脚本感知合成数据(每脚本约 250 万行)支撑超低资源训练;还预测脚本身份与字符数,可迁移到藏文、中文等。 | `recognition`, `script-diverse`, `historical` | - |
| PSMC 🆕 | [PSMC](https://arxiv.org/abs/2608.27753v1) | arXiv 2026 | 低资源脚本缺数据,VLM OCR 难以扩展。PSMC 利用跨脚本迁移:先从高资源锚模型派生语言专家,再用任务算术融合并共训合并骨干。在 10 种印度脚本上 WRR 较单脚本专家平均提升约 2%,且不增加参数。 | `recognition`, `multilingual`, `low-resource` | - |
| Ancient-Bench 🆕 | [Ancient-Bench](https://arxiv.org/abs/2608.27169v1) | arXiv 2026 | 中文古器物文字识别缺乏跨年代、跨介质、跨字形的综合基准。Ancient-Bench 发布 2700 图,覆盖 3000 年、9 类器物、7 种古文字,并定义符号/字符/解析三类标注规范。评测 VLM 与 OCR 专用模型显示任务远未解决,最优 F1 仅 57.86%。 | `recognition`, `historical`, `script-diverse` | [GitHub](https://github.com/SCUT-DLVCLab/Ancient_Bench) |
| AraMS-28k 🆕 | [AraMS-28k](https://arxiv.org/abs/2608.26921v1) | arXiv 2026 | 历史阿拉伯文手写 HTR 长期缺大规模行级开放数据。AraMS-28k 发布 28600 行、14 本书、三种脚本传统,首次为边注行标注插入锚点以还原非线性阅读序。RefLAM 流水线以参考转录对齐 MLLM OCR 并全量人工复核;Kraken/HATFormer 基线显示明显的跨脚本泛化梯度。 | `recognition`, `historical`, `handwriting` | - |
| RefLAM 🆕 | [RefLAM](https://arxiv.org/abs/2608.25140v1) | arXiv 2026 | 历史阿拉伯文手稿缺少可扩展的行级 HTR 标注。RefLAM 结合页面分割、MLLM 结构化 OCR 与去变音符模糊对齐,提出可证明的 Confidence-100 规则,通量提升 75 倍。发布 AraMS-28k:14 卷、3043 页、27971 行及基线微调结果。 | `recognition`, `historical`, `handwriting` | [GitHub](https://github.com/ArchaText/Reflam-pipeline) |
| WildHandBench 🆕 | [WildHandBench](https://arxiv.org/abs/2608.22959v1) | arXiv 2026 | 印刷文档 OCR 已超 96%,但手写文本仍被忽视。WildHandBench 收集 500 份手写文档,覆盖 4 语言、3 结构(正文/表格/公式)与 9 类真实场景,并提出 PDE 指标。18 个 MLLM 最佳仅 71.85%,人类 77.09%;模型错误 63-91% 为先验驱动。 | `recognition`, `handwriting`, `degraded` | - |
| Arabic VLM-OCR Study 🆕 | [Arabic VLM-OCR Study](https://arxiv.org/abs/2608.22366v1) | arXiv 2026 | VLM 在阿拉伯/伊斯兰手稿 OCR 上的作用长期研究不足。本文在 8 个阿拉伯语数据集(手稿、旧印本、净印本、多域、手写)上比较 Tesseract、通用与阿拉伯专用 VLM 及 OCR 条件化 VLM 校正,提出 OCR 先验可恢复性原则,并给出失败模式诊断。 | `recognition`, `historical`, `handwriting` | - |
| Institutional Newspapers Pipeline 🆕 | [Institutional Newspapers Pipeline](https://arxiv.org/abs/2608.18972v1) | arXiv 2026 | 历史报纸版式密集且不规则,难以计算访问。作者与波士顿公共图书馆共建模块化、低算力流水线(切版、按块 OCR、阅读序、NER、分类、语言检测、嵌入),并发布 1795–1930 年 147 万扫描、8310 万切块、163 亿 token 的开放数据集,同发布流水线与小模型。 | `recognition`, `historical`, `layout` | - |
| Iterative Sanskrit OCR Pipeline 🆕 | [Iterative Sanskrit OCR Pipeline](https://arxiv.org/abs/2608.18696v1) | arXiv 2026 | 复杂历史梵文写本版式异质、字形古旧,通用 OCR 难以胜任。作者提出可在版面层与外观层迭代微调的传统 OCR 流水线,逐页适配以减少专家标注,发布三份梵文写本的细粒度 PAGE-XML 数据集并对主流 MLLM 做基准。 | `recognition`, `historical`, `handwriting` | [GitHub](https://github.com/flame-cai/gnn-synthetic-layout-historical/) |
| OmniHandwritingOCR 🆕 | [OmniHandwritingOCR](https://arxiv.org/abs/2608.18586v1) | arXiv 2026 | MLLM 在真实手写 OCR 上的能力长期缺考,旧基准偏向印刷体或单行。作者整合 7.76 万标注图,覆盖英中文本与单/多行公式并按结构复杂度分层,以五种统一指标评测 13 个系统,揭示多行公式性能骤降与幻觉式纠正等失效模式。 | `recognition`, `handwriting`, `formula` | [GitHub](https://github.com/ECNU-RAIL/OmniHandwritingOCR-CIKM2026) |
| Khmer DocVQA Pilot 🆕 | [Khmer DocVQA Pilot](https://arxiv.org/abs/2608.28635v1) | arXiv 2026 | MLLM 在低资源非拉丁高棉文表单上的可靠性尚少研究。作者基于 KH-FUNSD 构建高棉-英文评测子集,涵盖发票、收据、报价单,对比 Qwen-VL 直读、解析器辅助与外部 OCR 配置。直读 Qwen3-VL-8B 准确率 51.9%,外部 OCR 最高 61.9%,高棉文原生回答仍是难点。 | `recognition`, `low-resource`, `script-diverse` | - |
| JapanDocReader 🆕 | [JapanDocReader](https://arxiv.org/abs/2608.06758v1) | arXiv 2026 | 向推理型多模态模型注入日语结构化文档解析能力会引发 VQA 遗忘。JapanDocReader 采用混合 SFT 加 DAPO 解析强化学习,以 JSON 校验门控奖励与方差过滤 prompt,在保留文档问答的同时取得结构化解析 SOTA(Overall 87.67)。 | `recognition`, `structured-output`, `layout` | - |
| Berrutti OCR Hallucination Analysis 🆕 | [Berrutti OCR Hallucination Analysis](https://arxiv.org/abs/2607.24077v3) | arXiv 2026 | 在乌拉圭历史微档案上,VLM OCR 在 CER/WER 上优于传统系统,却隐藏系统化幻觉:拼写规范化、虚构内容与语义替换,流畅却改义,对命名实体伤害最大。作者评测 18 个系统并呼吁评价超越字符级准确率。 | `recognition`, `historical`, `low-resource` | [GitHub](https://github.com/camilomarino/ocr_berrutti_dataset) |
| Khondo 🆕 | [Khondo](https://arxiv.org/abs/2607.21780v1) | arXiv 2026 | 政府多文档拼包在低资源孟加拉语中难切分,而 OCR 不可靠。Khondo 是首个面向孟加拉政务表的视觉原生基准,含 1,950 拼包、14 领域、5 种拼接方案。零样本 MLLM 评测显示聚类尚可,但页序在打乱后崩塌;英文包顺序恢复更佳。 | `multilingual`, `low-resource`, `layout` | - |
| Persian Pixel 🆕 | [Persian Pixel](https://arxiv.org/abs/2607.20385v1) | arXiv 2026 | 波斯文连笔、字形上下文相关、标注数据稀缺。作者基于 700 万词语料用 SynthOCR-Gen 渲染 34.3 万图文对,叠加 25 种以上退化模型。开源数据集支持 TrOCR/Donut 在低资源波斯-阿拉伯文上的训练与微调。 | `recognition`, `low-resource`, `script-diverse` | - |
| HIPE-OCRepair-2026 🆕 | [HIPE-OCRepair-2026](https://arxiv.org/abs/2607.08143v1) | ICDAR 2026 Competition | 历史报纸与印刷品遗留 OCR 噪声多、再数字化不可行。ICDAR 2026 HIPE-OCRepair 赛发布多语言(英/法/德,17-20 世纪)和谐化基准,设可控噪声层级与检索导向 cMER 评分,评估四支队伍从零样本到持续预训练的 LLM 后纠错系统。微调系统(BnF-Mistral)包揽八项第一,但低噪声过度纠正仍是普遍难题。 | `recognition`, `historical`, `multilingual` | [GitHub](https://github.com/hipe-eval/HIPE-OCRepair-scorer) |
| HunyuanOCR-1.5 🆕 | [HunyuanOCR-1.5](https://arxiv.org/abs/2607.04884v3) | arXiv 2026 | 轻量 OCR VLM 在密集文档上面临延迟-能力权衡。HunyuanOCR-1.5 将 DFlash 草稿式解码适配到 OCR 实现 6.37×/2.14× 加速,并引入 Agentic Data Flow 自动构建弱点导向训练数据。模型在 OmniDocBench v1.6 上达到顶级水平,并扩展到古文字与 331 种语言。 | `recognition`, `structured-output`, `multilingual` | [GitHub](https://github.com/Tencent-Hunyuan/HunyuanOCR) |
| Interpres 🆕 | [Interpres](https://arxiv.org/abs/2607.03836v1) | arXiv 2026 | 中世纪拉丁手稿因抄写员缩写与羊皮纸退化使通用 VLM 失效。作者评测 OCR→VLM 翻译流水线并发布 Interpres Parallel Corpus(1,383 条对齐手稿行、转录与译文),发现专用 OCR 接 VLM 的最简流水线胜过所有多组件变体,印证专精化差距与复杂度悖论。 | `historical`, `translation`, `low-resource` | - |
| Diffusion Stroke Recovery 🆕 | [Diffusion Stroke Recovery](https://arxiv.org/abs/2607.03422v1) | arXiv 2026 | 手写笔画恢复从离线图像重建笔尖轨迹,旧方法在多笔画字符上表现不佳。作者将其转为图像条件扩散:从高斯噪声采样与墨迹一致的轨迹。在 CASIA-OLHWDB 上时序相似性与形状保真度均超过 PEN-Net 与 Cross-VAE,并可跨脚本迁移。 | `handwriting`, `recognition`, `script-diverse` | - |
| MORE 🆕 | [MORE](https://arxiv.org/abs/2607.02956v1) | arXiv 2026 | 现有文档解析基准偏重英文与中文,长尾语言成为评测盲区。作者发布 MORE:覆盖 149 种语言、1,288 页真实文档,带文本/公式/表格/代码/目录/阅读顺序结构标注。对主流 VLM 与专用 OCR 模型的基线评测揭示长尾语言与结构化解析的薄弱环节。 | `multilingual`, `low-resource`, `script-diverse` | [GitHub](https://github.com/zimoqingfeng/MORE) |
| Hybrid Armenian RO 🆕 | [Hybrid Armenian RO](https://arxiv.org/abs/2607.00596v1) | arXiv 2026 | 历史亚美尼亚报纸版面复杂、语言资源稀缺。作者标注 66 页,对比几何启发式、YOLO、ECLAIR 与语义分区检测+生成式 LLM 的混合方法。混合方法将排序错误降低最高 76%,在 OCR 噪声下稳健,并发布针对历史亚美尼亚印刷的 Tesseract 模型。 | `historical`, `low-resource`, `script-diverse` | - |
| LV-ROVER-MLT 🆕 | [LV-ROVER-MLT](https://arxiv.org/abs/2607.00250v5) | DocEng 2026 | 马耳他语段落级 OCR 训练数据稀缺。LV-ROVER-MLT 合成微调 Tesseract 5,融合五路识别流并做词典门控词级仲裁,适配马耳他语变音符;获 DocEng 2026 冠军(CER 0.0074),并发布 36.8K 对马耳他语 OCR 语料。 | `recognition`, `low-resource`, `multilingual` | - |
| sinhala-ocr-lk-acts-1010 🆕 | [sinhala-ocr-lk-acts-1010](https://arxiv.org/abs/2606.29378v1) | MERCon 2026 | 僧伽罗语页面级 OCR 此前无真实数据集。作者发布 sinhala-ocr-lk-acts-1010(1010 页,跨 1981-2019),用 QLoRA 微调 DeepSeek-OCR、LightOnOCR-2-1B;LightOnOCR-2-1B 达 CER 1.05%,优于 Surya、Tesseract v5 与 Google Document AI。 | `recognition`, `low-resource`, `multilingual` | - |
| Devanagari OCR-VLM Bench 🆕 | [Devanagari OCR-VLM Bench](https://arxiv.org/abs/2606.29213v1) | arXiv 2026 | OCR-VLM 在印度系文字上的表现缺乏刻画。作者对 10 个系统(经典、开放 VLM、专用 OCR-VLM、前沿闭源)在印地语四种退化与 300 张真实扫描上做基准,并做 ByT5 后校正;真实扫描拉开 76 点差距,英文 OCR 强不代表印地语强。 | `recognition`, `script-diverse`, `degraded` | - |
| Koshur Pixel 🆕 | [Koshur Pixel](https://arxiv.org/abs/2606.23144v1) | arXiv 2026 | 克什米尔文采用波斯-阿拉伯 Nastaliq 脚本,字形上下文变化与连笔复杂,OCR 缺数据。作者用 SynthOCR-Gen 合成 61.3 万图-文对,覆盖词到整页并施加 25+ 退化,成为首个大规模克什米尔文合成 OCR 数据集。 | `recognition`, `low-resource`, `script-diverse` | - |
| Manchu Synth-Real OCR | [Manchu Synth-Real OCR](https://arxiv.org/abs/2609.11495v1) | arXiv 2026 | 仅在合成满文词图上训练的 VLM 在真实清代档案上精度受限。作者比较三种 VLM 与一个紧凑 CRNN 在四种合成-真实训练策略下的表现。真实历史图像显著提升档案识别精度,紧凑 CRNN 不逊于大型 VLM,而基于 18 世纪满文字典的投票纠错无需再训练即带来增益。 | `recognition`, `historical`, `low-resource` | - |
| KhatianDoc | [KhatianDoc](https://arxiv.org/abs/2609.03597v1) | arXiv 2026 | 孟加拉手写地契 RS Khatian 使用 Ana-Ganda 十六进制分数系统,字体与分词器均无支持,任何 OCR 管线与多模态大模型都无法识别。KhatianDoc 基于 107 份律师校验的真实记录构建四任务基准(符号识别、十六进制算术、字段抽取、问答),零样本评测六个多模态大模型,揭示能力缺失而非性能差距,并发布脱敏数据与代码。 | `recognition`, `low-resource`, `handwriting` | - |
| Wayu-Paxa-OCR-Zero | [Wayu-Paxa-OCR-Zero](https://arxiv.org/abs/2609.03595v1) | arXiv 2026 | 泰文 OCR 因非拉丁脚本与真实标签稀缺而受限。作者构建受控合成数据重建流水线,解耦源域、字体多样性、二维版面与字形差异以研究合成→真实迁移规律。Wayu-Paxa-OCR-Zero 仅用合成页微调 0.9B PaddleOCR-VL,即可媲美或超越更大参数量的泰文 OCR。 | `recognition`, `synthetic-hard`, `low-resource` | - |
| TongGuOCR | [TongGuOCR](https://arxiv.org/abs/2608.07917v2) | arXiv 2026 | 面向中文历史文档的版面感知 OCR MLLM;M5HisDoc AR 93.76,显著降低 NED/RO-ED。 | `recognition`, `historical`, `layout` | [GitHub](https://github.com/jzzh2004/TongGuOCR) |
| BanglaWild | [BanglaWild](https://arxiv.org/abs/2608.03884v1) | arXiv 2026 | 提出 BanglaWild,2535 张真实场景孟加拉语文字基准;评测 15 个 VLM 与 3 个 OCR 系统,给出 15 类错误分类。 | `recognition`, `scene-text`, `in-the-wild` | - |
| Baseer | [Baseer: An Arabic Vision-Language Model for Document-to-Markdown OCR](https://arxiv.org/abs/2509.18174) | arXiv 2025 | 阿拉伯语 document-to-Markdown OCR VLM，使用合成和真实阿拉伯文档微调。 | `recognition`, `multilingual`, `structured-output`, `layout` | N/A |
| CHURRO | [CHURRO: Making History Readable with an Open-Weight Large Vision-Language Model for High-Accuracy, Low-Cost Historical Text Recognition](https://arxiv.org/abs/2509.19768) | EMNLP 2025 | 高精度、低成本的开源权重历史文本识别 VLM。 | `recognition`, `historical`, `handwriting`, `multilingual` | [GitHub](https://github.com/stanford-oval/Churro) |
| CalliReader | [CalliReader: Contextualizing Chinese Calligraphy via Embedding-Aligned Vision-Language Model](https://arxiv.org/abs/2503.06472) | ICCV 2025 | 基于 embedding alignment 的 VLM，用于整页中文书法识别与解释。 | `recognition`, `historical`, `script-diverse`, `reasoning` | [GitHub](https://github.com/LoYuXr/CalliReader) |
| CalligraphicOCR | [CalligraphicOCR: Towards End-to-End Chinese Calligraphy Recognition with Large Multimodal Model](https://aclanthology.org/2025.emnlp-main.245/) | EMNLP 2025 | 结合图像增强和 action-based corrector 的中文书法识别方法。 | `recognition`, `historical`, `script-diverse` | [GitHub](https://github.com/HoraceXIaoyiBao/COCR-EMNLP2025) |
| Historical mLLM OCR | [Multimodal LLMs for OCR, OCR Post-Correction, and Named Entity Recognition in Historical Documents](https://arxiv.org/abs/2504.00414) | arXiv 2025 | 研究 mLLM 在历史文档转录、OCR 后纠错和命名实体识别中的作用。 | `recognition`, `historical`, `degraded` | N/A |
| Nayana OCR | [Nayana OCR: A Scalable Framework for Document OCR in Low-Resource Languages](https://openreview.net/forum?id=uaQR3BgHrV) | ICCVW 2025 | 针对十种 Indic 语言，结合 layout-aware 合成数据和 LoRA 进行 VLM 适配。 | `recognition`, `multilingual`, `low-resource` | N/A |
| OracleAgent | [OracleAgent: A Multimodal Reasoning Agent for Oracle Bone Script Research](https://www.researchgate.net/publication/397087875_OracleAgent_A_Multimodal_Reasoning_Agent_for_Oracle_Bone_Script_Research) | arXiv 2026 | 面向甲骨文研究的多模态 agent，编排工具和知识库完成检索与推理。 | `historical`, `script-diverse`, `reasoning` | [GitHub](https://github.com/lcs0215/OralceAgent) |
| QARI-OCR | [QARI-OCR: High-Fidelity Arabic Text Recognition with Multimodal Large Language Model Adaptation](https://arxiv.org/abs/2506.02295) | arXiv 2025 | 基于 Qwen2-VL 的阿拉伯语 OCR 模型，覆盖印刷体、带音标文本、低分辨率和手写阿拉伯语。 | `recognition`, `multilingual`, `low-resource`, `handwriting` | N/A |
| Uni-MuMER | [Uni-MuMER: Unified Multi-Task Fine-Tuning of Vision-Language Model for Handwritten Mathematical Expression Recognition](https://huggingface.co/papers/2505.23566) | arXiv 2025 | 面向手写数学表达式识别的统一多任务 VLM 微调。 | `handwriting`, `formula`, `structured-output` | [GitHub](https://github.com/bflameswift/uni-mumer) |
| V-Oracle | [V-Oracle: A Progressive Reasoning Framework for Oracle Bone Script Deciphering](https://aclanthology.org/2025.acl-long.986/) | ACL 2025 | 结合视觉和语言证据的甲骨文释读渐进式推理框架。 | `recognition`, `historical`, `script-diverse`, `reasoning` | N/A |

[[⬆️ 返回顶部](#contents)]

<a id="synthetic-hidden-and-adversarial-hard-ocr"></a>

### 🧪 合成、隐藏与对抗 Hard OCR

*本节将 hard OCR 定义为对合成、隐藏、错觉式、对抗或被篡改视觉文本的识别、定位或鲁棒解释。收录论文应将 OCR 或视觉文本阅读作为核心任务。不显式评估 OCR/文本阅读的通用 VLM 攻击、jailbreak、宽泛 AIGC 风险检测或合成图像生成不在本节范围内。*

| 方法/系统 | 论文 | Venue & Year | 亮点 | 标签 | 代码 |
|---|---|---|---|---|---|
| SupGRPO 🆕 | [SupGRPO](https://arxiv.org/abs/2609.07081v1) | arXiv 2026 | MLLM 识别强但定位弱,SFT 利检测、GRPO 利识别,二者各有缺陷。SupGRPO 用仅作用于坐标 token 的匹配式在线 SFT 联合训练,配四项规则奖励,同时缓解 GRPO 奖励稀疏与 SFT 实例顺序依赖。作者发布艺术字 spotting 基准 ATS,检测 88.8、识别 92.4 F1,超越专用模型与 MLLM 基线。 | `recognition`, `localization`, `scene-text` | [GitHub](https://github.com/Psycho-9/SupGRPO) |
| ArmorOCR 🆕 | [ArmorOCR](https://arxiv.org/abs/2608.20122v1) | arXiv 2026 | MLLM 对人类可读的对抗视觉文本仍易出错。作者提出首个 region 级对抗 OCR 基准 AdvSpot(390 图、5 类 13 细类),并给出 ArmorOCR 两阶段训练(特权观察自蒸馏 + 任务奖励 GRPO),在对抗与通用 OCR 上均有提升或保持。 | `recognition`, `localization`, `hidden/adversarial` | - |
| SamplingTAR 🆕 | [SamplingTAR](https://arxiv.org/abs/2607.02494v1) | ECCV 2026 | 排版攻击让 CLIP 视觉编码器偏向字面而非视觉语义,损害 LVLM。作者通过电路挖掘找出编码字面信息的 ViT 注意力头,施加无需训练的注意力干预。方法优于有监督与无训练防御,并在 RIO-Bench 上提升多款 LVLM 的 VQA 准确率。 | `hidden/adversarial`, `recognition`, `text-rich-vqa` | [GitHub](https://github.com/Liu-524/SamplingTAR) |
| WATERec 🆕 | [WATERec](https://arxiv.org/abs/2606.24484v1) | arXiv 2026 | WordArt(艺术字)识别因定制字体、纹理、排版远难于普通场景文本。作者发布 200 万合成数据 WATER-S,并提出支持任意形状输入与自回归解码的 WATERec;在 WordArt-Bench 上达 90.40%,大幅超越通用与 OCR 专用视觉语言模型。 | `recognition`, `synthetic-hard`, `scene-text` | [GitHub](https://github.com/YesianRohn/WATER) |
| SmuggleBench 🆕 | [SmuggleBench](https://arxiv.org/abs/2604.06950) | arXiv 2026 | MLLM 内容审核可被人可读但 AI 不可读的视觉格式规避。作者形式化对抗走私攻击(破坏文字识别的感知失明、抑制语义理解的推理封锁),构建含 1700 实例的 SmuggleBench,暴露 90%+ 攻击成功率并指出 OCR 鲁棒性缺口是根因之一。 | `hidden/adversarial`, `recognition`, `reasoning` | [GitHub](https://github.com/zhihengli-casia/smugglebench) |
| SemVink 🆕 | [SemVink](https://arxiv.org/abs/2506.02803) | arXiv 2025 | VLM 难以察觉视错觉与 AI 图中的隐藏内容,显式提示下准确率仍仅 0-5.36%。作者发布 HC-Bench(112 张含隐藏文字/物体的图),并提出 SemVink:将图降采样到 32-128 像素,剔除冗余视觉噪声后准确率超 99%。 | `hidden/adversarial`, `synthetic-hard`, `recognition` | - |
| Wayu-Paxa-OCR-Zero | [Wayu-Paxa-OCR-Zero](https://arxiv.org/abs/2609.03595v1) | arXiv 2026 | 泰文 OCR 因非拉丁脚本与真实标签稀缺而受限。作者构建受控合成数据重建流水线,解耦源域、字体多样性、二维版面与字形差异以研究合成→真实迁移规律。Wayu-Paxa-OCR-Zero 仅用合成页微调 0.9B PaddleOCR-VL,即可媲美或超越更大参数量的泰文 OCR。 | `recognition`, `synthetic-hard`, `low-resource` | - |
| SemVink | [SemVink: Advancing VLMs' Semantic Understanding of Optical Illusions via Visual Global Thinking](https://aclanthology.org/2025.emnlp-main.1381/) | EMNLP 2025 | 使用视觉全局思考策略，如低分辨率缩放，提升隐藏/错觉内容感知。 | `hidden/adversarial`, `recognition` | [GitHub](https://github.com/johnnyZeppelin/vlm-semvink) |
| VACoT | [VACoT: Rethinking Visual Data Augmentation with VLMs](https://arxiv.org/abs/2512.02361) | arXiv 2025 | 推理时 VLM 视觉增强方法，包含 crop、denoise、enhance 和工具选择，用于困难感知和对抗 OCR。 | `hidden/adversarial`, `synthetic-hard`, `recognition` | N/A |
| AIGuard | [AIGuard: A Benchmark and Lightweight Detection for E-commerce AIGC Risks](https://aclanthology.org/2025.findings-acl.643/) | ACL Findings 2025 | 检测电商图像中的 AIGC 风险内容，包括隐藏或问题视觉文本相关场景。 | `synthetic-hard`, `hidden/adversarial`, `in-the-wild` | [GitHub](https://github.com/wenh-zhang/aiguard-dataset) |

[[⬆️ 返回顶部](#contents)]

---

<a id="competitions"></a>

## 🏆 竞赛

| 竞赛 | Venue / Platform & Year | 亮点 | 链接 |
|---|---|---|---|
| Vignette OCR | Kaggle 2025 | 药房药品贴纸(vignette)承载小而密的安全关键文本。赛事设双重挑战:先定位并识别贴纸文字,再逐字段抽取直至有效期。提供数据集与榜单,覆盖从定位到信息检索的完整链路。 | [Kaggle](https://www.kaggle.com/competitions/vignette-ocr) |
| VRD-IU 2025 | AAAI 2025 Competition | 视觉富文档(VRD)的智能理解是 Document AI 的核心目标。AAAI-25 榜单赛聚焦 VRD 版面分析与结构解析。提供持续性榜单基准,用于评测文档结构理解方法。 | [Kaggle](https://www.kaggle.com/competitions/aaai-25-visually-rich-document-vrd-iu-leaderboard) |
| CMMHWR26 | ICDAR 2026 Competition | ICDAR 2026 赛事评测中世纪手稿的九语种多语言手写文本识别,设三档递进任务:多语言识别、同语系未见语言泛化、跨语系泛化。采用屏蔽测试集评分,产出榜单对比各 HTR 系统在语言泛化轴上的表现。 | [Competition Website](https://cmmhwr26.inria.fr) |
| TROGS-26 | ICDAR 2026 Competition | 古希腊铭文 OCR 通常通过纸拓拓本采集,面临光照变化与罕被现代系统覆盖的历史脚本。TROGS-26 发布 224 份带标注拓本,在两种正交光照下采集共 448 张图像(PageXML 标注),以转录字符错误率排名,产出历史希腊文 OCR 基准数据集与公开榜单。 | [Competition Website](https://www.science.smith.edu/~nhowe/contest/trogs26.html) |
| DocVQA 2026 | ICDAR 2026 Competition | DocVQA 2026 延续文档视觉问答竞赛,在 8 个领域以超越简单抽取的题型评测多模态推理:空间理解(地图、工程图、版面)、时间理解(漫画故事)、以及结合文本、表格与图的多跳答案。评测服务器接收提交并据此对系统排名。 | [Competition Website](https://www.docvqa.org/challenges/2026) |
| HIPE-OCRepair 2026 | ICDAR 2026 Competition | ICDAR 2026 赛事聚焦多语言多领域历史文档的 LLM 辅助 OCR 纠错。参赛者在固定评测阶段对屏蔽测试集进行 OCR 结果纠错,结果于维也纳 ICDAR 2026 公布,对比各 LLM 纠错方案在历史文本上的效果。 | [Competition Website](https://hipe-eval.github.io/HIPE-OCRepair-2026/) |
| DocVQA 2026 | ICDAR 2026 Competition | DocVQA 系列在 2026 年扩展为覆盖 8 个领域的文档多模态推理赛事。题目超越简单抽取,考察空间与时序理解(地图、漫画)以及跨文本、表格、插图的多跳推理。赛事提供评测数据集与榜单,检验高阶文档理解能力。 | [RRC Page](https://rrc.cvc.uab.es/?ch=34) |
| Seal Title 2023 | ICDAR 2023 Competition | 印章标题文字在公文与金融场景随处可见,却长期被成熟 OCR 技术忽视。任务需在多样印章形状、弯曲文本、背景噪声与文字重叠下读出印章文字。赛事提供专门的基准数据与榜单,推动这一 hard OCR 场景的研究。 | [RRC Page](https://rrc.cvc.uab.es/?ch=20) |
| SVRD 2023 | ICDAR 2023 Competition | 视觉富文档的结构化文本抽取是 Document AI 核心方向,但既有基准场景有限、且只评测流水线子模块。SVRD 赛事设两条赛道推进端到端抽取,并提供针对完整方案的基准与榜单。 | [RRC Page](https://rrc.cvc.uab.es/?ch=21) |
| NewsVideoQA 2023 | ICDAR 2023 Competition | 视频中文字的识别与跟踪长期是文档分析社区的难题。NewsVideoQA 首次在新闻视频上开展文本视频问答,系统需跨多帧读取文本并综合作答。赛事提供连接视频文字读取与问答的基准。 | [RRC Page](https://rrc.cvc.uab.es/?ch=24) |
| DataMFM Challenge: Document Parsing + Chart Understanding | CVPR Workshop 2026 | 针对自然文本、表格、公式、版面和图表的结构化文档解析与图表理解 | [Challenge Website](https://datamfm.github.io/challenge.html) |
| Handwritten to Data: Ukrainian OCR | Kaggle 2026 | 乌克兰语手写文本识别，适合追踪低资源手写 OCR | [Kaggle / News](https://nahornyi.ai/ru/news/kaggle-handwritten-to-data-ukr-ocr) |
| HTR: Handwritten Text Recognition and Understanding | ICDAR 2025 | 历史手写文本识别，并包含文档级理解赛道 | [Competition Website](https://prhlt-carabela.prhlt.upv.es/ICDAR25HTRU/) |
| Handwritten Notes Understanding | ICDAR 2025 | 手写笔记理解与 OCR 中心文档解释 | [RRC Page](https://rrc.cvc.uab.es/?ch=33) |
| Indic Handwritten Document Recognition | ICDAR 2025 | 跨多种脚本和版面的 Indic 页面级手写识别 | [Competition Website](https://ilocr.iiit.ac.in/icdar_2025_Indic_HDR/) |
| FEST: Few-shot Text-line Segmentation of Ancient Handwritten Documents | ICDAR 2025 | 面向古代手写文档的低标注文本行分割 | [Competition Website](https://ai4ch.uniud.it/FESTcompICDAR25/) |
| Historical Map Text Detection, Recognition, and Linking | ICDAR 2025 | 旋转、弯曲、低质量历史地图文本，以及词到短语链接 | [RRC Page](https://rrc.cvc.uab.es/?ch=32) |
| Document Image Machine Translation Challenge | ICDAR 2025 | 复杂版面下的 OCR-free/OCR-based 文档图像翻译 | [Competition Website](https://cip-documentai.github.io/) |
| Multi-lingual Roadside Scene Text Recognition | ICDAR 2025 | 路侧场景文本、多语种 OCR 与脚本识别 | [Competition Website](https://ilocr.iiit.ac.in/icdar_2025_MLT-RSTR/) |
| Glyph Detection in 15th-Century European Printed Documents | ICDAR 2025 | 15 世纪欧洲早期印刷文档中的历史字形检测与识别 | [Competition Website](https://lme.tf.fau.de/competitions/icdar-2025-competition-on-glyph-detection-in-15th-century-european-printed-documents/) |
| Recognition and VQA on Handwritten Documents | ICDAR 2024 | 孤立词识别、页面级阅读和手写文档 VQA | [Competition Website](https://ilocr.iiit.ac.in/icdar_2024_hwd/) |
| Reading Documents Through Aria Glasses | ICDAR 2024 | 低分辨率可穿戴相机文档 OCR、阅读顺序和页面阅读 | [Competition Website](https://ilocr.iiit.ac.in/icdar_2024_rdtag/) |
| Historical Map Text Detection, Recognition, and Linking | ICDAR 2024 | 历史地图 OCR 与文本链接 | [RRC Page](https://rrc.cvc.uab.es/?ch=28) |
| Historical Ciphers | ICDAR 2024 | 具有特殊符号的历史手写密码识别 | [RRC Page](https://rrc.cvc.uab.es/?ch=27) |
| CROCS: Recognition of Chemical Structures | ICDAR 2024 | 手写/符号化学结构识别 | [Competition Website](https://crocs-ifly-ustc.github.io/crocs/index.html) |
| Indic Handwriting Text Recognition | ICDAR 2023 | 十种 Indic 语言，覆盖连写字符、手写变化和非结构化书写 | [Competition Website](https://ilocr.iiit.ac.in/ihtr/) |
| VQA on Business Document Images | ICDAR 2023 | 商业文档 OCR、表格、表单和版面密集文档 VQA | [Competition Website](https://ilocr.iiit.ac.in/vqabd/) |
| DUDE: Document Understanding in the Wild | ICDAR 2023 | 多页视觉丰富文档理解和基于 OCR 的 QA | [RRC Page](https://rrc.cvc.uab.es/?ch=23) |
| HierText: Hierarchical Text Detection and Recognition | ICDAR 2023 | 自然图像中的层级文本检测、识别和版面分析 | [Google Research](https://research.google/pubs/icdar-2023-competition-on-hierarchical-text-detection-and-recognition/) |
| CROHME: Handwritten Mathematical Expression Recognition | ICDAR 2023 | 在线/离线/双模态手写数学表达式识别 | [Zenodo](https://zenodo.org/records/8428035) |
| Robust Reading Competition Portal | RRC / CVC Ongoing | 汇集场景文本、文档、视频文本和阅读竞赛的挑战门户，包含多个 ICDAR 相关任务 | [RRC Portal](https://rrc.cvc.uab.es/) |

[[⬆️ 返回顶部](#contents)]

<a id="contact-us"></a>

## 📮 联系我们

如果你有问题、建议，或希望讨论潜在合作，欢迎联系：

- Linhan Cao: `caolinhan@sjtu.edu.cn`
- Siyuan Li: `kongfu.lsy@antgroup.com`
- Jun Lan: `yelan.lj@antgroup.com`
