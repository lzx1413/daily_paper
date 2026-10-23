# 📚 arXiv CS.CV 每日论文报告

**报告日期**: 2026-10-23  
**论文来源**: [arXiv CS.CV Recent](https://arxiv.org/list/cs.CV/recent)  
**关注论文数**: 38篇（每类别Top 10，经质量筛选）

> 注：每类别按大模型评估的相关性和质量排序，仅展示前10篇高质量论文。已自动过滤低质量和小众方向论文。

---

## 📑 目录

- [🎨 AIGC 相关内容](#aigc) (1篇)
- [🖼️ 图像/视频/全模态生成](#image_video_omni_generation) (10篇)
- [🧠 大模型蒸馏与压缩](#distillation) (3篇)
- [⚙️ 训练推理基础设施](#training_inference_infra) (9篇)
- [🧠 Agent 相关内容](#agent) (5篇)
- [🌍 World Model 相关内容](#world_model) (10篇)

---

## 🎨 AIGC 相关内容

### 1. Think-Capture: Active 3D Geometry Acquisition for Spatial Reasoning in Vision-Language Models **⭐⭐⭐** (相关度: 65%, 质量: 0.8)

- **arXiv ID**: [2610.29232](https://arxiv.org/abs/2610.29232)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29232)
- **作者**: Junjie Wang, Zhihao Yuan, Yunhan Tang et al. (10 authors)
**评估**: 本文提出Think-Capture框架，结合3D几何工具和VLM进行主动空间推理，在多个空间推理benchmark上有显著提升（MindCube-Tiny +21.5%，MMSI-Bench +7.9%，ViewSpatial +5.2）。方法有明确创新点：查询条件化的主动几何获取、符号化3D状态抽象、层次化GRPO训练。代码开源，实验充分，具有实际应用价值（部署在Agibot G1机器人上）。该论文涉及VLM多模态能力增强，与AIGC（AI生成内容/多模态AI系统）最为相关，虽然不完全匹配，但VLM能力提升属于广义的AI生成内容系统范畴。非小众方向，空间推理是VLM的核心能力之一。

**核心贡献**:  
Think-Capture提出了一种查询条件化的3D几何获取框架，通过主动识别任务关键对象并按需获取其几何信息，解决了Vision-Language模型在稀疏视角下因空间关系不一致而产生的空间幻觉问题。该方法利用符号3D状态抽象将物体和相机状态压缩为结构化文本表示，并通过分层GRPO训练模型学会何时利用工具证据、何时回退到视觉线索。

**创新点**:  
1) 提出查询条件化的按需几何获取范式，避免全帧稠密几何融合带来的计算开销；2) 设计Symbolic 3D State Abstraction，将3D物体和相机状态压缩为结构化文本，高效注入VLM上下文；3) 采用分层GRPO策略优化，训练模型在几何估计可靠时利用工具证据、不可靠时回退至视觉线索，增强对噪声几何输入的鲁棒性。

**方法**:  
框架包含三个核心模块：(1) 查询条件化的关键对象识别，从用户问题中提取任务相关目标；(2) 3D Toolkit将零样本分割掩码提升至统一坐标系，结合相机位姿恢复3D物体状态；(3) Symbolic 3D State Abstraction将物体位置、朝向及相机参数编码为结构化文本序列。训练阶段使用分层GRPO，在几何估计正确与错误的场景下联合优化策略。

**结果**:  
Think-Capture-4B在MindCube-Tiny上达到54.4%（较基线提升21.5个百分点），在MMSI-Bench位置子集上达到39.1%（+7.9），在ViewSpatial上达到42.8%（+5.2）。模型在坐标和掩码扰动下保持鲁棒性。完整系统可在单块24GB GPU上运行，并作为异步高层推理器部署于Agibot G1机器人平台。

**相关性与影响**:  
该工作为VLM的空间推理能力提供了新的解决思路，通过按需获取3D几何而非稠密融合，有效平衡了计算效率与空间理解精度。其训练策略使模型学会区分可靠与不可靠的几何证据，对减少VLM空间幻觉具有重要意义。该方法可推广至具身智能、机器人导航等需要跨视角空间推理的场景，单GPU部署的轻量化设计使其具有实际应用价值。

---


---

## 🖼️ 图像/视频/全模态生成

### 1. Looking Ahead: Modeling Future Evolution in Autoregressive Video Generation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.29989](https://arxiv.org/abs/2610.29989)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29989)
- **作者**: Ruopeng Gao, Yukun Huang, Jiarui Hu et al. (7 authors)
**评估**: 论文聚焦自回归视频扩散模型的视频生成问题，属于图像/视频生成领域。核心贡献是提出 Future Chunk Prediction (FCP) 辅助训练目标，针对 teacher forcing 下时间冗余导致的'局部连续性捷径'问题，建模场景的长期演化，具有清晰的技术洞察和方法创新。方法设计优雅：无需额外预训练视觉编码器、不改变自回归推理流程、且训练开销更低，同时在物理合理性上取得更优结果，效率与效果兼得。问题动机（视频演化建模、物理合理性、世界模型表征）对生成式视频建模社区有较广的参考价值，不属于小众垂直方向。因此判定为高质量论文。

**核心贡献**:  
论文提出Future Chunk Prediction (FCP)，一种与teacher-forced去噪联合优化的辅助目标，通过预测时间上分离的未来视频片段来增强自回归视频扩散模型对场景演化过程的建模能力，而非仅依赖局部时间冗余产生的表面连续性。该方法无需额外的预训练视觉编码器，且不改变自回归推理流程，以更低的训练计算预算实现了更优的物理合理性。

**创新点**:  
指出了teacher forcing训练下时间冗余导致模型利用局部视觉连续性走捷径、忽视真正视觉演化建模的问题；提出FCP辅助目标，要求模型在不可见中间视觉上下文的条件下预测时间上分离的未来片段，从而迫使模型学习场景演化规律，且监督信号直接来自训练视频本身。

**方法**:  
在自回归视频扩散模型的teacher-forced去噪训练基础上，联合优化FCP辅助目标：从训练视频中抽取时间上分离的片段对，让模型在无中间帧上下文条件下预测未来片段的去噪过程，监督来自原始视频帧，无需额外预训练视觉编码器，推理时与标准自回归生成流程完全一致。

**结果**:  
相比标准teacher-forced自回归训练，FCP以更低的总体训练计算预算实现了更优的物理合理性；可视化分析表明FCP促进了更结构化的表示空间，有助于构建自回归世界模型。

**相关性与影响**:  
该研究揭示了自回归视频生成中teacher forcing训练的关键缺陷（对时间冗余的过度依赖），提出的FCP方法简单有效、成本低且易于集成，对提升视频生成的物理一致性、推动自回归世界模型的发展具有重要参考价值。

---

### 2. CausalAlign: Causal Alignment of Video Generation Models for Consistent Ego-Motion **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.29915](https://arxiv.org/abs/2610.29915)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29915)
- **作者**: Kai Zhu, Yintianrun Zhang, Shuwei Jiang et al. (10 authors)
**评估**: 论文聚焦扩散式视频生成模型（VGM）中相机ego-motion漂移这一具体且重要的问题，属于图像/视频生成领域。方法上具有明确创新：(1) 通过线性探针和因果干预诊断ego-motion在去噪过程中的表示演化规律（rise-and-fall模式）；(2) 提出delta-token空间的因果对齐框架，将VGM中间层表示与3D基础模型对齐，聚焦运动动态而非静态场景。实验在DL3DV、RealEstate10K等公开数据集上进行，报告了几何一致性提升20%+的量化结果，并在RoboCasa365具身操作任务上验证了下游应用价值（WAM成功率提升10个点），实验链条完整、动机清晰。该方向（视频生成的运动一致性/几何一致性）是当前热点，对世界模型和具身智能研究有实际参考价值。扣分点在于增量性——本质是表示对齐方法在VGM上的应用，且主要在一个基座模型（Wan2.2）上验证。

**核心贡献**:  
CausalAlign 提出了一个因果对齐框架，通过诊断扩散式视频生成模型中相机自我运动（ego-motion）的表示、使用和保持机制，并在关键层将表征与3D基础模型通过delta-token空间对齐，从而显著改善长视频生成中的视点漂移问题，在几何一致性上提升超过20%，同时改善了具身智能模型在机器人操作任务中的成功率。

**创新点**:  
1) 通过线性探针和因果干预首次系统诊断了扩散式视频生成模型中自我运动信息在去噪过程中的表征模式（先升后降）；2) 提出利用delta-token空间（编码连续帧间变化）将VGM表征与3D基础模型对齐，使对齐聚焦于自我运动动态而非静态场景内容，从而在不损害视觉质量的前提下增强运动一致性。

**方法**:  
CausalAlign包含两个核心组件：(1) 诊断阶段使用线性探针（linear probes）和因果干预（causal interventions）分析扩散模型中ego-motion在各层及各去噪阶段的表征规律；(2) 对齐阶段在识别出的关键层上，通过delta-token空间将视频生成模型的中间表征与3D基础模型进行对齐，delta-token编码相邻帧间的变化信息以聚焦运动动态。实验使用Wan2.2模型在DL3DV和RealEstate10K数据集上进行微调。

**结果**:  
在Wan2.2基础上：运动精度、几何一致性和时间平滑度大幅提升，几何一致性相比基线模型提升超过20%；视觉质量得以保持。在具身智能应用中：使用微调后的VGM，世界动作模型（WAMs）在RoboCasa365基准的移动操作任务上的成功率提升10个百分点。

**相关性与影响**:  
该论文解决了扩散式视频生成模型在长时间生成中相机视点漂移这一关键问题，对视频生成、3D场景理解、具身智能和世界模型等领域具有重要意义。其因果诊断方法为理解生成模型内部表征提供了新范式，而其对齐框架则为提升视频生成几何一致性和下游机器人任务性能提供了可泛化的技术路径。

---

### 3. Unlocking Spatial Grounding in Flow-Matching Models via SNR Tuning **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.29581](https://arxiv.org/abs/2610.29581)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29581)
- **作者**: Martin Thißen, Elke Hergenröther
**评估**: 论文聚焦图像生成模型中的空间布局控制问题，通过SNR（信噪比）分布分析揭示flow-matching模型中空间定位能力的关键机制，属于text-to-image/图像生成的细粒度控制研究，归入Image_Video_Omni_Generation。质量方面：1) 有明确的技术洞察——发现高噪声阶段是空间grounding的'关键学习阶段'，布局遵循率从25.9%提升至80.8%，逼近VAE的83.6%重构上限；2) 构建了合成几何图元基准，隔离结构机制与纹理复杂度，并提出color-aware布局量化指标，方法论严谨；3) 分析了SNR偏移需求与分辨率、宽高比方差的关系，指出FLUX.1等保守噪声调度的不足，具有普适参考价值；4) 在COCO真实图像上验证迁移性（1.0 vs 57.3 AP），无需架构修改仅通过分布调优即达SOTA布局遵循度，实际应用价值高。整体实验充分、结论可靠，对生成模型训练与布局控制研究有实际指导意义。

**核心贡献**:  
该论文发现信噪比(SNR)分布是流匹配模型中空间定位能力的关键决定因素。通过将训练的SNR分布向高噪声区间偏移，模型的布局遵从性从25.9%提升至80.8%，接近VAE的83.6%重建上限，且无需任何架构修改。该方法在COCO数据集上同样有效，从1.0 AP提升至57.3 AP。

**创新点**:  
首次系统性揭示了流匹配模型中SNR分布与空间定位能力之间的因果关系，发现高噪声阶段是空间信息学习的关键阶段，并提出仅通过调整训练SNR分布即可显著提升布局遵从性，无需辅助适配器或推理时干预。

**方法**:  
构建了一个由几何原语组成的合成基准数据集以隔离结构机制与纹理复杂度；提出了一种考虑颜色的布局度量来量化空间保真度；分析了不同SNR分布(居中式 vs 高噪声偏移式)对空间定位的影响，并在不同分辨率和宽高比方差下进行验证；最后在COCO真实数据集上进行迁移验证。

**结果**:  
居中SNR训练的布局遵从性为25.9%，向高噪声偏移后提升至80.8%（VAE重建上限为83.6%）；SNR偏移的必要性随分辨率和宽高比方差增大而增加；FLUX.1等模型采用的保守噪声调度不足以实现精确的布局遵从；在COCO数据集上，从1.0 AP提升至57.3 AP，仅通过分布调优即达到最先进水平。

**相关性与影响**:  
该研究为生成模型中的细粒度空间控制提供了一种简单而有效的训练策略，无需架构修改或额外辅助模块，具有很高的实用价值。它揭示了噪声调度在空间接地中的核心作用，对流匹配模型的设计与训练具有指导意义，有望推动可控图像合成的发展。

---

### 4. CCG Diffusion: Combinatory Categorial Grammar-Driven Compositional and Syntactically Disambiguated Text-to-Image Generation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.29415](https://arxiv.org/abs/2610.29415)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29415)
- **作者**: Ryosuke Yamaki, Daichi Mochihashi, Nobutaka Shimada et al. (5 authors)
**评估**: 论文提出用组合范畴语法（CCG）对文生图模型进行语法级控制，解决属性绑定、空间关系、计数以及句法歧义（PP attachment）问题。分类理由：核心贡献是改进text-to-image生成的组合性与语义对齐能力，属于图像生成控制方向。质量评估：(1) 创新点明确——首次将CCG引入扩散模型的prompt控制，利用CCG词类自带的组合信息直接读取修饰关系，并通过固定介词类别消解句法歧义，相比基于短语结构/依存语法的方法更简洁；(2) 方法为training-free，实用性强，可在Stable Diffusion与Sana两种异构骨干上验证，泛化性有支撑；(3) 实验覆盖属性绑定、2D空间关系和PP消歧三类任务并与现有syntax-based方法对比，结果有说服力。局限：属于语法控制这一相对细分的子方向，且实验主要在标准benchmark上，实际复杂场景效果与人类偏好对齐仍待验证。整体属于质量较高的工作。

**核心贡献**:  
CCG Diffusion 是一种免训练的文生图生成控制方法，利用组合范畴语法（CCG）为扩散模型提供丰富的句法结构信息。通过统一的提示改写和注意力引导机制，该方法能有效处理属性绑定、空间关系、计数以及句法歧义消解等多个关键挑战。在 Stable Diffusion 和 Sana 两种不同架构的模型上均验证了其优越性能。

**创新点**:  
首次将组合范畴语法（CCG）引入文生图生成控制，利用 CCG 中词范畴自带的丰富句法信息直接读取词语间的修饰关系，并通过固定介词范畴即可简洁地消解介词短语（PP）附着歧义，无需额外的规则或约束。

**方法**:  
提出两个核心机制：(1) 基于 CCG 解析的提示重写（prompt rewriting），根据 CCG parse 中的修饰关系重新组织 prompt；(2) 基于 CCG 的注意力引导（attention guidance），在扩散过程中引导注意力分配以正确绑定属性和空间关系。这两个机制统一用于控制属性绑定、空间关系、计数及 PP 歧义消解。方法完全免训练，可直接应用于现有文生图模型。

**结果**:  
在属性绑定和二维空间关系任务上，CCG Diffusion 在所有对比方法中取得了最高分。在 PP 附着歧义消解任务上，显著优于所有基线方法。实验覆盖了 Stable Diffusion 和 Sana 两种架构不同的骨干网络，验证了方法的泛化能力。

**相关性与影响**:  
该工作为文生图模型中长期存在的属性绑定错误、空间关系和计数不准确、句法歧义等核心问题提供了统一且优雅的解决方案。基于 CCG 的句法控制框架不依赖特定模型架构，具有良好的通用性，对提升文本生成图像的语义准确性和可控性具有重要意义，同时也为 NLP 与视觉生成模型的交叉融合开辟了新方向。

---

### 5. ER-Chord: Spatially Consistent One-Step Image Editing via Equal-Energy Reliability Redistribution **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.29248](https://arxiv.org/abs/2610.29248)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29248)
- **作者**: Peize Li, Hanzhen Zhao, Xingguo Xu et al. (9 authors)
**评估**: 论文属于图像编辑方向（text-guided image editing），研究单步生成模型在图像编辑中的一致性问题，是Image_Video_Omni_Generation的核心范畴（含图像编辑/diffusion编辑）。方法上有明确的技术创新：提出training-free、inversion-free的可靠性引导空间重分配框架，将编辑强度分配建模为等能量优化问题，并证明存在可高效计算的唯一全局解，无需额外denoiser调用，理论动机清晰。实验在PIE-Bench和TEdBench两个基准上验证，且跨多个生成骨干网络展示了稳健增益，源图像保持效果优于SOTA单步编辑基线。属于较主流的扩散模型编辑方向，具有实际参考价值。扣分点：主要为单一任务上的改进型方法，理论与影响力的广度相对有限。

**核心贡献**:  
ER-Chord 提出了一种免训练、免反演的一步图像编辑框架，通过利用相邻噪声水平下编辑场的一致性来估计局部可靠性信号，并将其转化为等能量优化问题来重新分配空间编辑强度。该方法在保持原始编辑方向和总控制能量不变的前提下，实现空间上更一致的编辑效果，显著改善源图像保留能力。

**创新点**:  
提出了一种基于相邻噪声水平编辑场一致性来计算局部可靠性的方法，并将其形式化为等能量优化问题，使得编辑控制能量在空间上根据局部可靠性重新分配。该优化具有唯一全局解，可通过已有场评估结果高效求解，无需额外的去噪器调用，实现了空间一致性的提升。

**方法**:  
核心方法包含三个部分：(1) 利用多噪声水平下编辑场的时间聚合来估计每个空间位置的局部可靠性（通过相邻噪声水平编辑场的分歧程度衡量）；(2) 将空间编辑能量分配建模为等能量约束下的优化问题，使低可靠性区域获得较少编辑能量、高可靠性区域获得更多编辑能量，同时保持总能量和编辑方向不变；(3) 该优化问题具有唯一解析解，可从已有的场评估中直接计算，无需额外计算开销。框架为免训练（training-free）和免反演（inversion-free）设计。

**结果**:  
在 PIE-Bench 和 TEdBench 两个基准上进行实验，与现有一步编辑方法相比实现了更优的源图像保留效果（source preservation），同时在多个生成骨干网络（multiple generative backbones）上均取得一致的性能提升，验证了方法的通用性和有效性。

**相关性与影响**:  
该研究针对一步生成模型在文本引导图像编辑中引入不必要改动的关键问题，提出了无需额外计算开销的空间可靠性重分配方案。其免训练、免反演且不增加去噪器调用的特性使其具有很强的实用价值，可广泛应用于各种一步编辑模型以提升空间一致性，对图像编辑、可控图像生成等方向具有重要意义。

---

### 6. RealMe: Immersive Volumetric Video from Minimal Captures **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2610.30023](https://arxiv.org/abs/2610.30023)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30023)
- **作者**: Chenxu Zhou, Zhiyuan Yu, Yudong Jin et al. (7 authors)
**评估**: 该论文核心是利用高分辨率视频扩散模型（video diffusion model）从稀疏多视角捕获中生成2K、4D一致的视频，本质上属于视频生成/增强领域。关键技术贡献包括：(1) 将因子化时空注意力适配到多视角捕获布局；(2) 提出隐空间频域损失（latent frequency loss）减少生成视频与真实捕获之间的差距；(3) 布局感知的位置编码设计。实验基于公开基准DNA-Rendering和自建数据集，与SOTA方法进行了视觉保真度和4D一致性的对比，实验较充分。该工作解决了稀疏捕获下体积视频重建的实用问题，技术方法有明确创新，对视频生成和体积视频领域具有参考价值。

**核心贡献**:  
RealMe 提出了一个基于高分辨率视频扩散模型的统一框架，能够从稀疏且低分辨率的多视角捕获中生成高质量、时间一致的沉浸式体积视频（2K 分辨率）。该框架通过布局感知的位置编码和因子化时空注意力适应多视角捕获布局，并利用潜空间频率损失缩小生成视频与真实捕获之间的数据差距。

**创新点**:  
提出了将高分辨率视频扩散模型适配到多视角体积视频增强任务的统一框架；设计了布局感知的位置编码和适应多视角布局的因子化时空注意力机制以保证4D一致性；引入潜空间频率损失（latent frequency loss）提供频域监督以缩小生成与真实数据的分布差距；构建了自采样的RealVV数据集用于体积视频捕获评估。

**方法**:  
从捕获视频构建辅助数据并编码为潜变量（latents），同时编码布局感知的位置嵌入；视频扩散模型采用适配多视角布局的因子化时空注意力机制，在多视角和时间维度上去噪潜变量；将去噪后的潜变量解码为增强视频用于优化4D表示；在潜空间中施加频率域损失（频域监督）以提升生成质量与真实捕获的一致性。

**结果**:  
在公开的DNA-Rendering基准和自建RealVV数据集上的大量实验表明，RealMe在视觉保真度和4D一致性方面均优于现有最先进方法。

**相关性与影响**:  
该工作显著降低了沉浸式体积视频的制作门槛，使得仅需稀疏、低分辨率的捕获设备即可获得高质量体积视频内容，在虚拟现实、远程呈现、影视制作和数字人等领域具有重要应用价值。同时，将视频扩散模型适配到多视角4D任务的思路也为其他时空生成任务提供了可借鉴的方法。

---

### 7. JointLight: Human-Centric Video Relighting with Asynchronous RGB-Irradiance Joint Modeling **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2610.29780](https://arxiv.org/abs/2610.29780)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29780)
- **作者**: Henglei Lv, Bailin Deng, Xiaoqiang Liu et al. (7 authors)
**评估**: 论文核心是基于扩散模型的人像/视频重光照（video relighting），涉及光照控制的生成式建模、合成视频数据集构建与生成质量提升，属于图像/视频生成方向（而非蒸馏或基础设施）。方法上有明确创新：提出RGB与地面真值irradiance的异步联合去噪范式（分离timestep调度）、两阶段训练与domain matching策略，以及推理时的异步hijacked生成管线，解决了现有端到端重光照可控性差和irradiance控制信号伪影的问题。同时构建了游戏引擎生成的多光照合成视频数据集并公开代码和数据，实验与先验方法对比充分，泛化到真实场景，工作完整、可复现性好，对重光照与可控视频生成领域具有实际参考价值。

**核心贡献**:  
JointLight 提出了一种异步 RGB-辐照度联合建模的以人为中心的视频重光照方法，通过在训练中让模型以不同时间步调度同时去噪 RGB 帧和真实辐照度帧，实现了细粒度光照控制。论文还构建了一个基于游戏引擎的多光照合成视频数据集，模型仅在该合成数据集上训练即可泛化到真实场景，在光照保真度和生成质量方面超越了现有方法。

**创新点**:  
1) 提出异步联合建模范式（asynchronous joint-modeling），在两阶段训练中分别以不同去噪时间步调度联合去噪 RGB 和真实辐照度帧，利用噪声去除辐照度的高频伪影并保留低频光照传输信息；2) 设计异步劫持生成管线（asynchronous hijacked generation pipeline），在推理时实现灵活的光照控制；3) 提出域匹配策略弥合辐照度线索与真实辐照度图之间的域差距；4) 构建了高质量多光照合成视频数据集并配对辐照度图。

**方法**:  
该方法基于扩散模型框架，核心为异步时间步调度的两阶段训练：第一阶段联合训练 RGB 与辐照度帧的去噪；第二阶段引入域匹配策略，以真实辐照度图为条件引导生成。推理时采用异步劫持管线，用户可提供目标辐照度图实现光照编辑。训练数据由高性能游戏引擎渲染生成多光照条件的合成视频及配对辐照度地图，确保模型在合成数据上获得精确监督后可泛化至真实场景。

**结果**:  
在合成数据集上训练后，模型在真实场景中展现出鲁棒的泛化能力；在光照保真度和生成质量两个维度上均优于先前的重光照方法（prior approaches），包括基于端到端神经网络的隐式方法和基于路径追踪辐照度线索的显式方法。代码与数据集将公开发布。

**相关性与影响**:  
该论文解决了以人为中心视频重光照领域中精准光照控制和高质量数据集稀缺的核心瓶颈，提出的异步联合建模范式为利用显式物理线索引导扩散模型生成提供了新思路。高质量合成数据集的构建为社区提供了重要资源，方法在影视制作、虚拟会议、数字人渲染、游戏引擎等实际应用场景中具有广泛潜力。

---

### 8. Pair-Free Coarse-to-Real Video Generation via Real-to-Coarse Image Supervision **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.7)

- **arXiv ID**: [2610.28954](https://arxiv.org/abs/2610.28954)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.28954)
- **作者**: Gonzalo Gómez-Nogales, Daohan Lu, Peiye Zhuang et al. (5 authors)
**评估**: 论文核心是 coarse-to-real 视频生成（将粗糙/合成渲染视频转为逼真视频），属于 text-to-video / 视频合成 / 风格化视频生成的范畴，应归入 Image_Video_Omni_Generation。方法上提出了一种巧妙的非对称性思路：利用易得的 real-to-coarse 图像对训练 DINO 特征空间转换模型，逐帧合成伪粗糙视频，从而摆脱昂贵的 (coarse, realistic) 视频对，实现 pair-free 训练并可扩展到任意真实视频语料，具有明确的技术创新和实用价值。不足之处在于方法本质是多阶段管线的组合（图像编辑工具 + 逐帧特征迁移 + 视频生成模型），单帧独立处理可能带来时序一致性问题，摘要中未见充分的消融与对比实验说明，且项目页形式更接近 workshop 论文，影响力有待验证，因此质量分给中等偏上。

**核心贡献**:  
论文提出了一种无需(coarse, realistic)视频对的粗视频到真实视频(Coarse-to-Real)生成训练框架：利用易于构建的真实-粗图像对训练一个在DINO特征空间中将真实图像转换为粗图像的模型(DINO-R2C)，并逐帧应用于普通真实视频以合成伪粗视频，再训练C2R#模型学习从伪粗视频重建真实视频。推理时丢弃DINO-R2C，直接由真实的粗动画/仿真视频驱动C2R#，从而摆脱昂贵的配对视频数据依赖。

**创新点**:  
核心创新是利用'视频配对难、图像配对易'的不对称性，通过真实→粗图像的逆向监督(DINO特征空间)生成伪配对视频对，实现pair-free的粗转真实视频训练；训练可随任意真实视频语料扩展，而不再局限于有限的合成域配对数据。

**方法**:  
1) 使用现有图像编辑与3D重建工具构建真实-粗图像配对；2) 训练DINO-R2C模型在DINO特征空间实现真实图像到粗图像的映射(Real-to-Coarse)；3) 将DINO-R2C逐帧作用于真实视频生成伪粗视频，形成(伪粗, 真实)视频对；4) 训练C2R#视频生成模型以伪粗视频为条件重建对应真实视频，保持布局、相机运动与动态一致；5) 推理阶段仅使用C2R#，由真实粗视频(动画/仿真/游戏渲染)直接驱动生成逼真视频。

**结果**:  
实验表明该pair-free训练范式能够在不使用任何粗-真实视频配对的情况下生成保留场景布局、相机运动和动态的逼真视频，且训练规模可随真实视频语料数据量扩展；相较于依赖窄合成域配对数据的先前方法具有更强的泛化能力与数据可扩展性（具体定量指标详见论文正文与项目主页）。

**相关性与影响**:  
该工作显著降低了粗到真实视频生成的数据标注成本，使视频风格转换、仿真到真实(sim-to-real)渲染、游戏/CG视频逼真化等应用可以从海量无配对真实视频中受益，对内容创作、机器人仿真迁移以及视频生成模型的数据效率提升均具有重要推动作用。

---

### 9. JUICE: Unified Multimodal Modeling in Pretrained Representation Spaces **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2610.28801](https://arxiv.org/abs/2610.28801)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.28801)
- **作者**: Jiahan Li, Huangyuan Su, Shengbang Tong et al. (12 authors)
**评估**: 论文提出JUICE，用单一flow matching Transformer在冻结的预训练编码器空间中联合建模图像与文本的联合分布，属于统一多模态生成（图像/文本双模态生成）方向，是当前Unified Multimodal Modeling的主流研究热点。方法有明确创新：(1) 在连续编码器空间而非VAE latent中统一建模；(2) 每个模态独立噪声水平，通过确定哪些模态干净/生成来灵活切换任务；(3) 提出coupled sampling实现两模态联合生成（如地图+路径、多解迷宫联合成功率从54.6%提升到93.7%），实验设计包含消融对照（编码器空间 vs VAE vs 像素、联合+条件去噪训练对比），结果指标充分（GenEval 0.88、VQAv2 73.1），2.1B参数从零训练无LM初始化，创新性与实验完整性均较好，对统一多模态生成领域有实际参考价值。

**核心贡献**:  
JUICE提出在冻结的预训练编码器连续表示空间中，用单个流匹配Transformer对图像和文本的联合分布进行统一建模，从而以同一生成过程对称地处理两种模态。通过联合采样，模型可同时生成图文一致的内容，在maze规划等多解任务中联合成功率从54.6%提升至93.7%。

**创新点**:  
1) 在预训练语义编码器空间中直接建模图文联合分布，取代传统'语言模型生成文本+扩散头生成图像'的非对称框架；2) 每个模态拥有独立噪声水平，由哪些模态为干净状态决定任务（图像生成、描述、VQA、联合生成）；3) 联合采样无需固定生成顺序，两个模态可自适应彼此。

**方法**:  
单个流匹配（flow matching）Transformer，作用于冻结的图像与文本编码器表示；训练同时包含联合去噪与条件去噪；无语言模型初始化，从头联合训练；2.1B参数，224×224分辨率；通过受控预训练实验对比连续文本状态、语义编码空间 vs VAE latents/原始像素等设计选择。

**结果**:  
GenEval达0.88（文本连续化不影响图像生成：48.41 vs 47.86）；VQAv2达73.1；maze任务联合成功率54.6%→93.7%（联合采样 vs 独立采样）；视觉空间规划在训练规模上解决99.8%的地图；可边画路线边写出对应走法。代价是描述文本的精确措辞略有损失。

**相关性与影响**:  
为统一多模态建模提供了对称且原则性的替代方案，验证了预训练表示空间作为联合生成目标的有效性；联合采样能力对需要模态间强一致性的规划与推理任务具有重要应用前景，可能影响未来统一多模态模型的架构设计范式。

---

### 10. CineEvolve: An Agentic Self-Evolution Framework for Cinematic Multi-Shot Video Generation **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2610.29590](https://arxiv.org/abs/2610.29590)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29590)
- **作者**: Jingzhe Zhang, Peixuan Zhang, Genying Li et al. (7 authors)
**评估**: 论文核心目标是电影级多镜头视频生成（multi-shot video generation），属于图像/视频生成领域；其中的agentic框架、Director-Critic交替RL训练以及E-GRPO算法都是服务于视频生成质量提升的手段，而非独立的训练基础设施或蒸馏工作，因此归入Image_Video_Omni_Generation。质量方面：针对多镜头叙事一致性和迭代精修提出明确的技术创新（单一VLM策略内的Director-Critic协同进化、带历史锚定与修订保护的E-GRPO以缓解advantage膨胀），并贡献了40K规模的CineTraj创作-批评-修订轨迹数据集，实验显示优于现有方法，具有实际参考价值。不足之处在于该方向相对细分、依赖VLM策略与生成模型耦合的工程细节，且为较新的预印本工作（作者机构信息不明确），故质量分评为中上水平。

**核心贡献**:  
CineEvolve 提出一个用于电影级多镜头视频生成的智能体自进化框架，将“导演（Director）”与“评论家（Critic）”统一在一个视觉-语言策略中，通过交替强化学习实现协同进化。论文引入了 Evolutionary GRPO（E-GRPO）以稳定共进化过程，并构建了包含 40K 条电影轨迹的数据集 CineTraj，实验表明其性能优于现有方法。

**创新点**:  
1) 将导演与评论家统一在同一 VLM 策略内，通过交替 RL（导演暴露缺陷以锐化评论家，更新后的评论家指导导演进行针对性修订）实现自进化；2) 提出 Evolutionary GRPO（E-GRPO），引入历史锚定（historical anchoring）和修订防护（revision safeguarding）来缓解优势值膨胀（advantage inflation），稳定协同进化；3) 构建 CineTraj 数据集：覆盖创作、批评与修订环节的 4 万条电影制作轨迹。

**方法**:  
核心方法为 CineEvolve 框架：(1) 叙事规划与迭代精修一体化——Director 负责多镜头视频的生成与基于反馈的修订，CineTraj 为覆盖创作-批评-修订的 40K 条轨迹；(3) 训练采用交替强化学习策略，在单一 VLM 策略内交替优化 Director 与 Critic 角色，模拟真实电影制作中导演与反馈循环的耦合过程。

**结果**:  
大量实验表明 CineEvolve 在电影级多镜头视频生成任务上优于现有方法（包括缺乏叙事推理的方法以及前馈式无策略更新的方法），在生成质量、叙事连贯性与迭代修订效果上取得领先表现。代码将开源：https://github.com/JingZhe-8/CineEvolve。

**相关性与影响**:  
该工作将智能体化、自我进化的强化学习范式引入视频生成领域，弥合了叙事推理与迭代优化之间的鸿沟，为长视频/多镜头内容创作提供了接近真实电影制作流程的自动化方案；E-GRPO 的稳定化技术和 CineTraj 数据集对多轮生成-评估-修订的 RL 训练研究具有广泛参考价值，对 AIGC 影视创作、智能导演助手等应用场景具有重要推动作用。

---


---

## 🧠 大模型蒸馏与压缩

### 1. TernScope: Model-Hardware Co-Design for Efficient Ternary Endoscopic Segmentation **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.7)

- **arXiv ID**: [2610.29617](https://arxiv.org/abs/2610.29617)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29617)
- **作者**: Zhuoyu Wu, Wenhui Ou, Qiawei Zheng et al. (6 authors)
**评估**: 论文核心贡献在于三值量化感知训练（TPQ）和模型-硬件协同设计，属于模型压缩与量化（Distillation范畴）方向。技术上有明确创新：split-channel大核块、分支融合去除冗余推理路径、从深到浅的渐进三值量化策略，以及硬件侧的乘法器消除设计。实验提供了模型精度、参数量（0.2483M）、计算量（0.0949 GMACs）和45nm工艺下计算阵列面积缩减88.46%等多维度评估。但需注意：应用领域为医疗内窥镜分割，属于垂直小众方向，受众和泛化性受限；论文的通用性创新相对有限，更多是针对特定场景的工程优化。综合评估为质量尚可但非顶级的论文。

**核心贡献**:  
TernScope 通过模型-硬件协同设计，提出了一种面向边缘医疗内窥镜图像分割的紧凑三值化分割网络。其核心贡献包括：以分通道大卷积核模块与分支融合构建轻量网络，并通过三值渐进量化感知训练（TPQ）将全部 25 个卷积层量化为三值权重、8 位激活，从而实现免乘法器的打包存储与高效硬件执行。

**创新点**:  
模型-硬件协同设计框架：(1) 分通道大卷积核块（split-channel large-kernel blocks）在有限计算量下保留空间上下文；(2) 分支融合（branch fusion）消除冗余推理路径；(3) 三值渐进量化感知训练（TPQ），按从深到浅、经解码器、再到输入与预测层的顺序逐步量化网络，使全部卷积均为三值权重+8位激活。

**方法**:  
采用端到端协同设计流程：先设计轻量分割架构（大卷积核、通道分组、分支融合），再用 TPQ 逐层渐进式量化训练适配；三值权重支持打包存储并省去乘法器；硬件侧基于 systolic array 加速器（Gemmini）评估，将 8位×8位 乘法计算阵列替换为适配三值权重的计算结构，在 45 nm 工艺下验证面积收益。

**结果**:  
模型仅含 0.2483 M 参数和 0.0949 GMACs，在域内及外部数据集上仍保持有竞争力的分割精度；在相同 45 nm 工艺下，相较原始 Gemmini（8位×8位乘法器 systolic array 加速器）计算阵列面积减少 88.46%。

**相关性与影响**:  
该工作展示了从轻量医疗分割模型到低比特专用硬件的完整路径，对边缘/嵌入式医疗影像设备、低功耗 AI 加速器设计以及量化感知训练研究具有重要参考价值，有望推动内窥镜等床旁实时分割系统在资源受限场景下的落地部署。

---

### 2. ClunoGS: Compact Language 3D Gaussian Splatting via Unified Optimization **⭐⭐⭐** (相关度: 78%, 质量: 0.7)

- **arXiv ID**: [2610.30013](https://arxiv.org/abs/2610.30013)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30013)
- **作者**: Jian Xu, Yi Li, Ying Huang et al. (7 authors)
**评估**: 论文核心贡献在于对带语言特征的3D Gaussian Splatting进行模型压缩（语义感知的稀疏化 + 向量量化的统一约束优化），属于模型压缩/轻量化部署范畴，因此归入Distillation类别。方法上有明确的技术创新：指出顺序式压缩会因忽略语义贡献而永久丢失语义信息，提出联合目标函数并通过原变量-稀疏化-量化-对偶的交替优化求解，理论框架完整；实验在LERF和ScanNet-10两个公开基准上验证了开放词汇定位与分割任务，并有消融实验支撑，论证较为充分。不足之处是面向语言3DGS压缩这一相对细分的应用方向，受众和影响范围有限，但技术思路对3DGS压缩和语义-几何联合优化方向仍具有参考价值。

**核心贡献**:  
ClunoGS 提出了一种面向语言3D高斯溅射（Language 3DGS）的紧凑化框架，将语义感知的高斯稀疏化与向量量化统一到一个受约束的目标函数中联合优化，从而在激进压缩下同时保持渲染质量、语义精度和模型紧凑性。该方法通过交替进行原始变量、稀疏化、量化和对偶更新来求解统一目标。

**创新点**:  
首次将语义感知的高斯稀疏化与向量量化纳入统一的受约束优化框架，取代传统的顺序压缩流程；在稀疏化阶段引入语义监督，使目标函数同时考虑渲染质量、语义精度与紧凑性，避免仅依据RGB渲染质量剪枝导致的重要语义高斯被误删。

**方法**:  
核心技术包括：1) 语义感知的高斯稀疏化，在剪枝过程中引入语义预测监督，保护对开放词汇语义贡献大的高斯原语；2) 针对语言特征的向量量化（VQ）压缩；3) 统一约束目标函数，联合建模渲染、语义与紧凑性三项目标；4) 交替优化算法，轮流执行原始变量更新、稀疏化步骤、量化步骤和对偶变量更新（拉格朗日乘子法）进行求解。

**结果**:  
在开放词汇定位与分割任务的 LERF 和 ScanNet-10 基准上进行评估；实验表明，在激进压缩率下，统一的语义感知公式相比顺序压缩和语义无关的稀疏化能显著缓解语义表征退化；消融实验进一步证明，联合协调稀疏化与量化比独立执行两者能更好地保持语义精度。

**相关性与影响**:  
该工作弥合了3DGS压缩与开放词汇场景理解之间的空白，为需要兼顾存储效率与语义保真度的边缘部署、大规模场景理解、具身智能和机器人导航等应用提供了重要技术支撑，并为后续多目标联合优化的3D表征压缩研究提供了新的范式。

---

### 3. GeoMem-VLA: Internalizing 3D Scene Understanding into Temporal Memory for Vision-Language-Action Models **⭐⭐** (相关度: 55%, 质量: 0.8)

- **arXiv ID**: [2610.29866](https://arxiv.org/abs/2610.29866)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29866)
- **作者**: Qinfan Zhang, Yifan Luo, Haoyuan Shi et al. (9 authors)
**评估**: 论文核心是机器人操作的Vision-Language-Action（VLA）模型，严格来说不属于四个给定类别中的任何一个。归入Distillation是基于其方法机制：使用冻结的几何基础模型（geometry foundation model）作为教师，通过geometric flow-matching目标将3D场景理解监督信号蒸馏到可学习的GeoPlan tokens中，属于teacher-student式知识迁移，只是蒸馏目标从VLM视觉嵌入转向了专用几何token与时序记忆。质量方面：创新点明确（将显式3D监督内化为可累积的时序几何记忆，推理时无需3D教师或显式重建），实验较充分（LIBERO 98.9%、RoboTwin 91.10%/91.24%、5项真实任务78.0%），且与VLA/机器人操作这一活跃主流领域相关，非小众垂直方向。扣分点：与所给分类体系匹配度较低，真实任务数量有限，属于跨领域工作。

**核心贡献**:  
GeoMem-VLA 提出了一种将显式3D几何理解内化到视觉-语言-动作（VLA）模型时序记忆中的框架，使机器人操作策略能够在不进行显式3D重建的情况下积累并利用几何信息。该方法通过冻结的几何基础模型对可学习的 GeoPlan tokens 进行几何流匹配（flow-matching）监督，再将其与观测表征的记忆系统集成，实现跨时间步的几何知识持续更新。在 LIBERO、RoboTwin 基准及真实世界任务中取得了优秀的成功率。

**创新点**:  
首次将3D几何理解通过几何流匹配目标内化到VLA模型的时序记忆tokens中，而非将VLM的原生视觉嵌入与教师特征空间直接对齐；在推理阶段无需调用3D教师模型或显式重建场景，仅通过记忆检索与自适应融合即可生成动作。

**方法**:  
训练阶段使用冻结的几何基础模型作为教师，对可学习的 GeoPlan tokens 施加几何流匹配监督（基于当前场景点图与未来末端执行器轨迹）；将几何tokens与观测表征记忆系统集成，包含历史信息检索、与当前观测的自适应融合、以及事件帧的巩固机制；推理阶段检索历史表征并与当前工作表征融合后直接预测动作，无需3D重建。经过基准特定的下游适配后部署。

**结果**:  
LIBERO基准：98.9%平均成功率；RoboTwin基准：clean设定91.10%，randomized设定91.24%；五项真实世界任务：78.0%平均成功率。

**相关性与影响**:  
该工作表明将3D场景理解内化并记忆到VLA模型中是机器人控制的可行且有效的途径，为弥合VLA模型中几何感知与动作生成之间的鸿沟提供了新思路；其无需显式3D重建即可利用几何信息的范式具有较高的效率优势，对提升机器人操作策略的3D理解与跨任务泛化能力有重要参考价值。

---


---

## ⚙️ 训练推理基础设施

### 1. BlazeVGGT: 13x Faster VGGT at 2,000 Frames via Camera Token without Training **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2610.29454](https://arxiv.org/abs/2610.29454)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29454)
- **作者**: Shujun Yao, Junhui Lin, Congying Han et al. (6 authors)
**评估**: 本文提出BlazeVGGT，通过camera token引导的稀疏化结构(KV sparsification + 贪心DPP选择)对VGGT的全局注意力进行推理加速，属于训练无关(training-free)的推理加速/效率优化工作，核心贡献在基础设施层面的推理加速，而非模型压缩或蒸馏(无teacher-student训练)，故归为Training_Inference_Infra。论文质量较高：(1)有明确的技术洞察——发现camera token的'拓扑优先、几何滞后'演化规律，并据此设计非对称注意力；(2)方法设计合理且创新(DPP多样性选择保留互补视角)；(3)实验充分，2000帧下13x加速且精度不降反升(Chamfer Distance 0.41→0.32)，并验证了与FastVGGT/LiteVGGT的兼容性和向StreamVGGT/PAGE-4D的迁移性；(4)代码开源，实用价值高，对VGGT系列长序列重建的部署有直接参考意义。

**核心贡献**:  
BlazeVGGT is a training-free framework that accelerates VGGT's multi-view reconstruction by exploiting structure-aware sparsification of key-value pairs in global attention blocks. By analyzing the topology-first, geometry-later evolution of camera tokens across layers, it selects complementary views via determinantal point process inference for asymmetric attention. At 2,000 frames, it achieves approximately 13× faster inference than VGGT while simultaneously reducing Chamfer Distance from 0.41 to 0.32.

**创新点**:  
The paper reveals that VGGT camera tokens evolve from encoding local view neighborhoods in shallow layers to globally organized inter-view geometry in deeper layers, enabling a training-free, plug-and-play asymmetric attention design. It constructs a view-level similarity kernel from camera-token relations and employs greedy DPP inference to select a compact, mutually complementary set of views as key-value context, eliminating redundant cross-view computation without any parameter updates.

**方法**:  
BlazeVGGT operates as a structure-aware frame-level key-value sparsification module integrated into pretrained VGGT. At each global-attention block, it (1) extracts camera tokens to build a view-level similarity kernel, (2) applies greedy determinantal point process (DPP) inference to select a diverse subset of complementary views, (3) uses selected views as key-value pairs while retaining all input frames as queries in an asymmetric attention design. This preserves dense per-frame predictions while removing redundant computation. The method is parameter-free and works as a drop-in module, compatible with other VGGT accelerators (FastVGGT, LiteVGGT) and transferable to VGGT-based models (StreamVGGT, PAGE-4D).

**结果**:  
At 2,000 input frames, BlazeVGGT achieves approximately 13× faster inference speed compared to VGGT. Surprisingly, it also improves reconstruction quality, reducing Chamfer Distance from 0.41 to 0.32. Experiments demonstrate favorable accuracy-efficiency trade-offs in both point-cloud reconstruction and camera-pose estimation. The method is compatible with existing accelerators (FastVGGT, LiteVGGT) and transfers effectively to downstream VGGT-based architectures (StreamVGGT, PAGE-4D).

**相关性与影响**:  
This work addresses the critical quadratic scaling bottleneck in feed-forward visual geometry models, making dense multi-view attention practical for very long video sequences (up to 2,000 frames) without any retraining. The training-free, plug-and-play nature ensures broad applicability and easy integration into existing pipelines. The finding that structured sparsification can simultaneously improve both efficiency and accuracy is significant for scalable 3D reconstruction from video, with implications for robotics, AR/VR, autonomous driving, and large-scale structure-from-motion applications.

---

### 2. Sparsity Should Be ALLOTted by Output: Training-Free Allocation of Block-Sparse Attention for Video Diffusion Transformers **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2610.29441](https://arxiv.org/abs/2610.29441)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29441)
- **作者**: Tianze Xia, Xiaoling Zhou, Ruya Lan et al. (6 authors)
**评估**: 论文提出ALLOT方法，通过块稀疏注意力（block-sparse attention）在视频Diffusion Transformer中优化稀疏分配，核心贡献是训练无关的稀疏注意力分配策略，以降低注意力计算成本、加速推理。这属于推理加速与显存/计算优化范畴，归入Training_Inference_Infra。论文有清晰的技术创新（cell probing与trajectory calibration），实验覆盖多个视频生成管线（Wan2.1、Wan2.2、HunyuanVideo），共九个设置均达到或超过默认效果，并报告11.8 dB PSNR增益，实验较充分、结论可靠，对视频扩散模型的高效推理有实际参考价值。

**核心贡献**:  
本文提出了一种训练免费的块稀疏注意力分配方法ALLOT，用于视频扩散Transformer，核心发现是不同层和去噪步骤的注意力稀疏化对最终视频保真度的影响差异巨大，但最敏感的层-步组合在不同输入间几乎不变。ALLOT通过单元探测和轨迹校准估计每个层-步单元对最终误差的贡献，在延迟预算下联合优化稀疏度分配，仅替换现有方法的分配组件即可显著提升性能。

**创新点**:  
1) 发现并利用了层-步敏感性的输入不变性——最敏感的层-步组合跨输入几乎保持不变，为无需训练的稀疏分配提供了理论依据；2) 提出ALLOT框架，通过cell probing和trajectory calibration两阶段机制量化每个层-步对单元对最终视频误差的贡献；3) 在延迟预算下联合优化所有单元的稀疏度分配，与现有选择策略和kernel完全兼容，可即插即用。

**方法**:  
将每个层-步组合视为一个cell，ALLOT通过两步估计贡献：(i) Cell Probing——在少量采样输入上探测各cell的稀疏化对输出的影响；(ii) Trajectory Calibration——校准探测估计沿扩散轨迹的累积误差效应。基于估计的贡献值，将稀疏度分配建模为带实测延迟约束的联合优化问题，求解各cell的最优注意力密度。方法无需额外训练，保留现有的块选择策略和稀疏注意力kernel，仅替换分配模块。

**结果**:  
在XAttention基线上，ALLOT在HunyuanVideo上以相同或更短的墙钟时间实现了11.8 dB的PSNR增益。在Wan2.1、Wan2.2和HunyuanVideo三个基座模型的四个已发布pipeline共九个设置上，ALLOT在全部设置中优于或持平默认分配策略，展示了跨模型和跨pipeline的强泛化能力。

**相关性与影响**:  
该工作解决了视频扩散Transformer中块稀疏注意力的关键瓶颈——稀疏度如何分配的问题，通过输出驱动的自动化分配取代启发式规则，显著提升了稀疏化后的生成质量。其训练免费、即插即用的特性使其可直接应用于现有视频生成系统，对降低视频生成的计算成本同时保持高质量具有重要的实用价值，推动了高效视频扩散模型的实际部署。

---

### 3. No Frames, Just Frequencies: Bandwidth-Efficient Deployment-Time Adaptation for Smart Glasses **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2610.29607](https://arxiv.org/abs/2610.29607)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29607)
- **作者**: Francesco Corti, Moritz Becker, Olga Saukh
**评估**: 论文提出了一种面向智能眼镜部署场景的带宽高效自适应框架，核心创新在于用紧凑的频率描述子替代原始帧传输，结合主机端的分布偏移数据合成与模型自适应。该工作属于部署时推理优化/基础设施范畴。实验涵盖多种架构（ConvNeXtV2、DeiT、TinyViT）和多个任务（图像分类、人员检测、目标检测），结果量化清晰（93-95% oracle恢复率，213-784x带宽压缩）。但研究场景聚焦于智能眼镜，属于相对细分的应用领域，虽然频率描述子方法论具有一定的通用性，整体影响力受限于场景窄度，因此质量中等偏上。

**核心贡献**:  
论文提出了一个名为 No Frames, Just Frequencies 的带宽高效、源端辅助的部署时适应框架，使智能眼镜等边缘设备在隐私和通信受限条件下适应数据分布漂移。设备端仅计算并传输紧凑的频率描述符而非原始图像帧，宿主端模型副本据此合成 OOD 数据并执行适应，从而在大幅节省带宽的同时恢复绝大部分有监督适应增益。

**创新点**:  
以低维频率描述符（而非原始图像帧）作为分布漂移的紧凑表征，通过宿主端将描述符映射为分布偏移算子并合成 OOD 数据来驱动模型副本的适应；描述符分辨率可灵活降采样，实现 213×–784× 的带宽压缩，同时保持适应质量的优雅退化（graceful degradation）。

**方法**:  
1) 设备端在眼镜上对输入图像计算紧凑频率描述符并传输至宿主设备；2) 宿主端持有模型副本，将接收到的频率描述符映射为分布偏移算子（distribution shift operator），合成类 ImageNet-C 的 OOD 扰动数据；3) 采用预定义的适应协议在宿主端更新模型副本；4) 在混合 ImageNet-C 损坏上评测卷积（ConvNeXtV2-Femto）、自注意力（DeiT-Tiny）和混合（TinyViT-5M）三类架构，并在人分类（Visual Wake Words）与目标检测（MS-COCO）任务上验证。

**结果**:  
仅基于传输描述符的适应可恢复监督 Oracle 适应增益的 93–95%（三种架构）、82%（Visual Wake Words 人分类）和 94–98%（MS-COCO 目标检测）；描述符分辨率从 224 降至 28 像素时适应质量在各架构上一致地优雅退化，带宽压缩可达 213×–784×。

**相关性与影响**:  
该工作为隐私敏感、带宽受限的边缘 AI 部署（智能眼镜、可穿戴设备）提供了无需上传原始图像的适应范式，平衡了隐私保护、通信效率与模型适应性能；其频率域表征思路对边缘持续学习、联邦/源端辅助适应和资源受限下的域适应研究具有重要参考价值，并展示了跨架构的通用性。

---

### 4. Generalized CycleGRPO for Fine-Grained Multimodal Understanding and Grounding **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2610.29552](https://arxiv.org/abs/2610.29552)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29552)
- **作者**: Xin Zhang, Haochen Wang, Beibei Lin et al. (7 authors)
**评估**: 该论文提出CycleGRPO，一种基于区域-文本循环一致性的统一强化学习训练框架，用于多模态细粒度理解与定位。核心贡献在于：(1) 首个将区域理解和定位耦合在空间、时间以及时空域中的统一RL训练框架，无需外部语言模型裁判或参考标注；(2) 利用重构重叠度作为可验证奖励信号，设计GRPO训练范式；(3) 提出DOVE基准用于评估视频中事件区分能力。实验结果显著，gIoU从57.5%提升至68.2%（GroundingSuite），从71.2%提升至78.7%（GRES），temporal任务上也有明显提升。该方法本质是一种RL训练方法论创新，属于训练基础设施范畴，对多模态模型训练有实际参考价值。整体创新性和实验充分度较好，代码和模型均已开源。

**核心贡献**:  
论文提出了Generalized CycleGRPO，这是首个将区域理解与定位耦合在统一强化学习框架中的方法，覆盖空间、时间以及时空多个领域。该框架通过区域-文本循环一致性（先生成描述再将描述定位回原区域）构建可验证的奖励信号，无需参考描述或外部语言模型评判。作者同时引入了DOVE基准测试用于评估视频中事件级别的描述区分能力。

**创新点**:  
1) 首个统一的强化学习框架（CycleGRPO），将细粒度区域理解与定位通过循环一致性耦合，覆盖图像掩码/框、视频时间区间和时空证据等多种模态；2) 提出无需参考描述或外部语言模型评判的自验证奖励机制——利用重建重叠度作为描述质量的可验证奖励，同时用定位奖励提升逆映射能力；3) 构建DOVE（Distinctive Occurrence-level Video-caption Evaluation）基准，用于衡量视频描述区分相似重复事件的能力。

**方法**:  
核心方法为区域-文本循环一致性策略：给定一个区域，多模态大语言模型生成候选描述，然后将每条描述定位回原区域以重构输入区域。重构重叠度提供可验证的描述奖励，单条定位奖励提升逆映射精度。通过统一的区域空间公式化方法，将该循环从图像域扩展到视频域，使得描述能够区分目标事件与相似重复事件。训练过程基于GRPO（Group Relative Policy Optimization）框架，以SAMTok/Qwen3-VL等模型为初始化。

**结果**:  
在GroundingSuite上将SAMTok的整体gIoU从57.5%提升至68.2%；在GRES上平均gIoU从71.2%提升至78.7%；在Charades时间定位任务上达到51.9% tIoU（对比Qwen3-VL初始化的45.6%）；在DOVE基准上Temporal Evidence Coverage达到33.3%（对比Qwen3-VL的14.8%），展示了显著的性能提升。

**相关性与影响**:  
该论文确立了区域-文本循环一致性作为多模态理解与定位的通用自评估原则，具有重要影响：1) 统一了空间和时间域的细粒度多模态任务，减少了对任务特定标注的依赖；2) 提供了一种不依赖外部标注或LLM评判器的自监督强化学习信号获取方式，降低了训练成本；3) DOVE基准填补了视频描述中时间区分性评估的空白，对视频理解、时序定位和多模态对话等下游任务具有广泛的应用价值。

---

### 5. Scaling in Games: Continued Pre-Training For Embodied Agents In Diverse Virtual Worlds **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2610.28698](https://arxiv.org/abs/2610.28698)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.28698)
- **作者**: Kuan Zhang, Yukun Chen, Zhihao Yang et al. (11 authors)
**评估**: 论文核心贡献是对虚拟游戏世界中具身智能体的continued pre-training进行系统性scaling law研究。实验规模庞大（120个训练配置、4种模型尺寸0.8B-27B、6种数据预算、5种数据混合方案），设计严谨，属于受控的scaling law实证研究。发现三个重要现象：数据量提升in-corpus性能、多样性提升相关世界迁移、早期interface phase与后期world phase的区分，并拟合了经验scaling law。论文虽然以游戏世界为实验场景，但其核心是训练策略和scaling law的系统研究，涉及数据效率、模型容量、迁移泛化等训练基础设施层面的问题，归类为Training_Inference_Infra最为合适。相比Agent类别，该论文的重点不在智能体架构设计，而在训练方法论和scaling行为分析。质量方面，实验充分、结论可靠、对embodied learning的scaling特性有重要参考价值，但受限于纯imitation learning范式，作者也诚实地指出其局限性。

**核心贡献**:  
该论文通过在虚拟世界（涵盖不同视觉风格、动力学与控制机制）中对具身智能体进行继续预训练（CPT）的受控研究，系统探讨了数据量、数据多样性与模型规模三个维度对学习与泛化的影响，并拟合出经验性缩放定律。研究发现继续预训练存在'早期接口阶段'（跨世界广泛受益）与'后期世界阶段'（收益局限于语料内及相关世界）两个阶段，并指出仅靠模仿式继续预训练难以构建通用具身智能体。

**创新点**:  
大规模受控实验设计：120个训练配置，跨4种模型规模（0.8B–27B）、6档数据预算（50–1600小时）与5种数据混合策略（从Minecraft单世界到多世界语料）；提出三层验证损失与从语料内到未见世界的分级游戏基准评估泛化能力；发现并刻画了'接口阶段—世界阶段'两阶段现象，并拟合了关联验证损失与数据量、多样性、模型规模的缩放定律。

**方法**:  
以Minecraft及其他多个虚拟世界环境为基础，采用继续预训练（Continued Pre-Training, CPT）范式对具身智能体进行训练；通过控制变量法在数据量、数据多样性（单一世界到多世界混合）和模型参数规模三个轴上系统扫参；评估采用三级验证损失以及从语料内世界、相关世界到遥远（未见）世界的游戏行为基准测试，并对缩放行为进行经验拟合建模。

**结果**:  
（1）更多数据提升语料内性能；多样性提升向相关世界的迁移，但对遥远世界收益有限；模型规模提升数据效率，但在单世界训练下对遥远世界的泛化反而更差；（2）观察到早期接口阶段（跨世界广泛受益）与后期世界阶段（收益收窄），并拟合出验证损失关于数据量、多样性与模型规模的经验缩放定律；（3）所训模型在Minecraft上与专用模型及前沿大模型具有竞争力，在3D世界中表现优异，并在实时设置下表现最佳；但对遥远世界存在持续性差距。

**相关性与影响**:  
该研究为虚拟世界中具身智能体的数据与模型缩放提供了首个系统性的实证规律，对Scaling Law在具身学习与虚拟环境中的适用性给出量化刻画，为训练通用具身智能体的数据配比与模型选型提供指导；同时其揭示的模仿学习局限性指明了超越继续预训练的后续研究方向（如更丰富的训练阶段、世界模型或交互式学习），对游戏AI、仿真到现实迁移及通用具身智能研究具有重要参考价值。

---

### 6. Cache Locally, Recompute Selectively for Streaming Video Understanding **⭐⭐⭐** (相关度: 72%, 质量: 0.8)

- **arXiv ID**: [2610.29229](https://arxiv.org/abs/2610.29229)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29229)
- **作者**: Junhyeok Lee, Sangyoon Lee, Jaeho Lee
**评估**: 分类理由：论文核心贡献是针对流式视频理解(video-LLM)的推理阶段KV缓存管理优化——通过选择性KV重计算(query-time selective re-prefill)来缓解idle-time预填充时的上下文不匹配问题，从而降低每帧预填充FLOPs(>20%)和总处理时间(14-59%)。这本质上属于推理效率优化与KV cache基础设施改进（免训练、即插即用），而非视频内容生成，因此归入Training_Inference_Infra。质量评估：问题定义清晰（上下文不匹配这一矛盾分析到位），方法简洁可解释且免训练、可跨框架移植；实验覆盖3个SVU框架和5个流式/离线基准，同时报告精度(最高+3.9pp)与效率(FLOPs、端到端耗时)双维度增益，指标较为充分。局限在于贡献属于工程性启发式改进，理论深度有限，且流式视频理解相对属于较细分方向，故质量分评为0.78而非更高。

**核心贡献**:  
论文提出了FrameBlend，一种即插即用的免训练方法，通过在查询时选择性地使用查询相关上下文重新预填充部分视频token的KV缓存，解决流式视频理解中预填充阶段受限上下文导致的上下文不匹配问题。该方法允许在空闲时间使用更短的注意力窗口进行预填充，从而在降低预填充计算成本的同时提升视频理解准确率。

**创新点**:  
识别并解决流式视频理解中预填充阶段的上下文不匹配问题（受限上下文可能遗漏查询所需信息，同时包含与查询无关的冗余信息），通过查询时选择性KV重计算将上下文化在空闲时间和查询时间之间进行更合理的分配，无需任何额外训练。

**方法**:  
FrameBlend在查询时选择部分视频token，使用查询相关的上下文对其进行重新预填充（re-prefill），并用重计算的KV替换缓存中的原始KV。这使得空闲时间的预填充可以使用更短的注意力窗口，显著降低每帧的预填充FLOPs，同时重计算弥补了短上下文预填充带来的信息损失，提升下游查询精度。该方法作为即插即用模块适用于多种SVU框架。

**结果**:  
在三个SVU框架和五个流式及离线基准测试上，FrameBlend带来了最高3.9个百分点的准确率提升。在RVS-Ego基准上，每帧预填充FLOPs降低超过20%，总处理时间（包括查询时重计算开销）降低14-59%（针对基于检索的框架）。实验表明该方法在准确率和效率之间实现了更优的权衡。

**相关性与影响**:  
该论文针对流式视频理解中无限视频流场景下的核心效率-准确率权衡问题，提出了一种简单而有效的解决方案。FrameBlend的即插即用特性和免训练优势使其易于集成到现有SVU系统中，为实时视频理解系统（如智能助手、自动驾驶、监控等场景）在资源受限条件下的部署提供了实用的优化路径。

---

### 7. Stochastic Nonlinearities Improve Uncertainty Estimation **⭐⭐** (相关度: 45%, 质量: 0.7)

- **arXiv ID**: [2610.29875](https://arxiv.org/abs/2610.29875)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29875)
- **作者**: Mohammad Sarhangzadeh, Amirreza M. Shebly, Doruk Oner
**评估**: 论文提出用随机激活函数切换实现轻量化的不确定性估计，核心卖点是单一模型即可获得预测多样性、避免集成训练成本，属于推理侧效率与部署相关的基础设施工作，因此归入 Training_Inference_Infra，但该主题与四个预设类别的匹配度都较低（uncertainty estimation 本质是视觉识别中的可靠性分析方向，非 AIGC/生成/蒸馏），分类置信度不高。质量方面：方法思想清晰、有一定新意（将随机非线性重构为信息保持的预测多样性来源），在分类、语义分割和 OOD 检测上、CNN 与 Transformer 架构上做了较全面的实验验证，结论可信；但方法本身相对简单、属于对已有随机激活机制的重新利用，理论深度和影响范围有限，综合评为中等偏上质量。

**核心贡献**:  
This paper proposes using stochastic activation switching—randomly sampling between different nonlinear activation functions during forward passes—as a lightweight mechanism for uncertainty estimation in visual recognition tasks. Unlike existing uncertainty methods that suppress intermediate features or require expensive ensembles, this approach induces predictive diversity while keeping all intermediate feature pathways active. It achieves improved uncertainty quality across classification, semantic segmentation, and out-of-distribution detection with a single trained model and no architectural modifications.

**创新点**:  
Reframing stochastic activation functions—previously used for optimization and output diversity—as an information-preserving, lightweight uncertainty estimation method. The key insight is that sampling between nonlinearities during inference induces predictive variation without suppressing intermediate features (as in MC Dropout) or requiring ensemble training, task-specific uncertainty heads, or architectural redesign.

**方法**:  
During each forward pass, network units randomly select among multiple nonlinear activation functions (e.g., various nonlinearities instead of fixed ReLU). This stochastic switching creates an ensemble-like effect over multiple forward passes on a single model, enabling uncertainty estimation via the diversity of predictions. The method is evaluated across convolutional (CNN) and transformer-based architectures on multiple datasets for three tasks: image classification, semantic segmentation, and out-of-distribution (OOD) detection.

**结果**:  
The method improves uncertainty quality metrics (e.g., calibration, AUROC for OOD detection) across all evaluated tasks—classification, semantic segmentation, and OOD detection—while maintaining competitive primary-task performance compared to deterministic baselines. It demonstrates consistent improvements across diverse datasets and both CNN and transformer architectures, showing robustness and generalizability without any additional training cost.

**相关性与影响**:  
This work provides a simple, training-free, and computationally efficient alternative to MC Dropout, deep ensembles, and dedicated uncertainty estimation methods. By leveraging a mechanism already present in neural networks (activation functions), it lowers the barrier for deploying reliable uncertainty estimates in safety-critical vision applications such as autonomous driving, medical imaging, and robotics. The approach is architecturally agnostic and applicable to modern vision transformers, making it highly relevant for real-world deployment where computational budgets are constrained.

---

### 8. Hyperspherical Simplex Representations for Backward-Compatible Retrieval **⭐⭐** (相关度: 45%, 质量: 0.7)

- **arXiv ID**: [2610.29550](https://arxiv.org/abs/2610.29550)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29550)
- **作者**: Simone Ricci, Niccolò Biondi, Federico Pernici et al. (4 authors)
**评估**: 该论文解决模型更新后部署检索系统需要重新索引的问题，通过超球单纯形表示实现向后兼容检索，属于模型更新与部署基础设施优化方向，与Training_Inference_Infra中的部署基础设施最相关。但论文主题更偏向表征学习与检索，并非典型的训练/推理加速或分布式基础设施，分类置信度较低。质量方面：具有明确的理论分析（基于von Mises-Fisher分布的向后兼容性条件）、提出确定性线性变换对齐类原型、无需兼容性专用损失或模型依赖，在标准基准上取得有竞争力的结果，实验涵盖扩展类别、更复杂架构和独立训练模型，属于扎实的中等偏上质量工作。

**核心贡献**:  
本文提出了一种用于向后兼容检索的超球单纯形表示方法（Hyperspherical Simplex Representations），通过利用softmax输出和logits的几何结构，在独立训练的模型更新之间实现直接的表示兼容性，从而避免大规模检索系统中昂贵的重索引过程。该方法不需要兼容性特定的训练损失、学习映射函数或架构修改，仅依赖模型共享的单纯形几何结构即可实现兼容。

**创新点**:  
利用softmax交叉熵训练和one-hot标签所诱导的单纯形几何结构作为跨模型更新的公共几何参考，构建超球单纯形表示；当类集扩展导致单纯形维度变化时，推导出确定性的线性变换来恢复类原型的对齐；并给出在von Mises-Fisher类分布假设下满足向后兼容性形式化定义的两个几何条件的理论分析。

**方法**:  
1) 从模型的softmax输出和logits中提取超球单纯形表示，利用one-hot标签在单纯形中定义的固定类原型作为跨模型的公共参考；2) 对于新增类集导致的单纯形扩展问题，推导确定性线性变换重新对齐已有类的原型；3) 在von Mises-Fisher分布和浓度参数随模型更新递增的假设下，证明对齐的正则单纯形表示满足向后兼容性不等式的两个几何条件。

**结果**:  
在标准兼容性基准测试上取得了有竞争力的结果，验证范围涵盖：扩展类集场景、更具表达力的网络架构、以及从公开仓库独立训练的模型。无需任何兼容性特定的损失函数、映射网络或架构改动，表明该方法具有实用性和普适性。

**相关性与影响**:  
该研究解决了大规模检索系统中模型更新导致重索引开销巨大的实际问题，为向后兼容性提供了一种无需额外训练成本的简洁方案。理论分析揭示了向后兼容的几何本质，为后续研究提供了理论基础。方法不依赖前代模型或特殊训练流程，具有良好的可扩展性和实际部署潜力。

---

### 9. Progressive Permutation Alignment with Temperature-Controlled Spectral Sharpening **⭐⭐** (相关度: 45%, 质量: 0.7)

- **arXiv ID**: [2610.29396](https://arxiv.org/abs/2610.29396)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29396)
- **作者**: Yuta Horioka, Naoya Chiba, Yuki Uranishi
**评估**: 论文核心是神经元置换对齐（weight-space/permutation alignment），用于独立训练模型在权重空间的线性插值与模型合并，属于模型权重操作与训练/部署效率相关的基础技术，与蒸馏压缩无直接关系，与生成任务无关，四个类别中最接近 Training_Inference_Infra（模型权重空间操作、支撑模型合并与高效部署），但匹配度一般，故置信度较低。质量方面：方法有一定技术含量——逐层渐进对齐 + 匈牙利离散锚点 + 温度控制谱退火避免连续松弛的内层梯度优化，定位了现有方法（过早离散化陷入局部最优、梯度优化代价高）的明确痛点；实验覆盖 MLP、CNN、NeRF 多种架构并以 loss barrier 等指标验证，具备一定说服力。不足：置换对齐/weight matching 是相对小众的细分方向（模型合并的一个子问题），创新为工程化改进而非范式突破，若无更强的大规模或下游应用验证，影响面有限，故质量分仅中等偏上。

**核心贡献**:  
该论文提出了一种渐进式排列对齐方法，通过逐层推进的策略和温度控制的谱锐化技术，解决神经网络权重空间中的排列对称性问题。在每个层级，方法通过匈牙利算法获取离散锚点，并结合温度退火逐步将相关性矩阵锐化为排列矩阵，最终通过逐层权重匹配进行精炼优化，从而在独立训练的模型间实现稳定的神经元对应关系恢复。

**创新点**:  
提出温度控制的谱退火机制与渐进式逐层对齐策略的结合：在每一层先用匈牙利算法获得确定性离散锚点，再通过温度退火将相关性矩阵逐步锐化为排列矩阵，避免了连续松弛方法中昂贵的内环梯度优化和离散方法容易陷入不一致局部最优的问题。

**方法**:  
方法采用逐层推进的对齐流程：(1) 沿网络从输入到输出逐层处理，利用层间依赖关系指导对齐；(2) 在每层估计神经元间的相关性矩阵，并通过匈牙利算法与离散锚点对齐；(3) 采用温度控制的谱退火，通过逐步降低温度将相关性矩阵平滑锐化为排列矩阵，该过程是确定性且轻量化的；(4) 最终阶段从对齐解出发，通过逐层权重匹配进行精炼优化，进一步提升对齐质量。

**结果**:  
在MLP、CNN和NeRF上的实验表明，该方法能可靠地恢复神经元对应关系，跨架构实现稳定对齐。特别是在独立训练的NeRF模型对齐实验中，该方法相比现有方法显著降低了权重插值下的损失屏障（loss barrier），验证了其在隐式神经表示中的实用性和有效性。

**相关性与影响**:  
该方法对隐式神经表示（INR）和NeRF等模型的权重空间操作具有重要意义，解决了排列对称性导致的模型合并、插值和分析困难。通过提供一种确定性、轻量化的替代方案，该方法为模型融合、知识蒸馏、模型编辑等下游任务提供了更可靠的神经元对齐基础，尤其在NeRF等计算密集型场景中具有实际应用价值。

---


---

## 🧠 Agent 相关内容

### 1. Multimodal Embodied Agents: A Unified Capability-centric Perspective from Computer-Use to Robot-Use **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.30108](https://arxiv.org/abs/2610.30108)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30108)
- **作者**: Yanzhe Chen, Ziyi Yang, Jifeng Zhu et al. (17 authors)
**评估**: 论文提出PAPAV统一能力框架（Perceive-Anticipate-Plan-Act-Verify），系统性地比较了多模态智能体、计算机使用智能体与机器人系统的异同，并对64个基准进行了能力维度的实证梳理，揭示了Anticipate与Verify能力评估严重缺失的研究空白。作为一篇视角/综述类论文，其分类体系清晰、覆盖面广、对智能体领域具有实际参考价值，属于较高质量工作。扣分点在于以概念性框架和调研统计为主，缺少方法层面的技术创新与实验验证，影响力依赖于后续社区采纳。

**核心贡献**:  
本文提出PAPAV，一个以能力为中心的统一框架，将计算机使用代理（CUIs）和机器人系统（RSs）整合到多模态具身代理（MMEAs）的视角下进行分析。通过定义五个反复出现的核心能力——感知(Perceive)、预判(Anticipate)、规划(Plan)、行动(Act)和验证(Verify)，论文系统比较了三类代理的共性与差异，并揭示了从计算机使用转向机器人使用时面临的五大物理约束。论文还对64个基准进行了全面审计，发现现有评估严重偏向行动能力，而预判和验证能力几乎未被显式衡量。

**创新点**:  
提出PAPAV能力中心框架，以功能而非架构定义五个核心能力（Perceive-Anticipate-Plan-Act-Verify），为多模态具身代理、计算机使用代理和机器人系统提供统一的分析和比较基础；识别出五大约束（从部分可观测到不可验证结果），阐明物理环境对代理决策选择空间的压缩效应。

**方法**:  
采用框架综述与基准审计方法：(1) 定义MMEA概念并建立PAPAV五能力分类体系；(2) 将计算机使用代理、机器人系统和多模态具身代理置于同一能力空间进行横向比较；(3) 对64个现有基准进行系统性评估分析，量化各能力的评估覆盖度；(4) 基于物理约束分析框架识别开放挑战。

**结果**:  
64个基准的审计结果显示：显式评估集中在Act能力上，仅有5个基准评估Anticipate能力，仅3个评估Verify能力，两项关键能力在现有评测中基本处于隐藏状态，被任务成功率所掩盖。五大物理约束（部分可观测、不可预测效果、有限可行路径、物理执行误差、不可验证结果）导致机器人使用场景中预先固定的选择更少、错误回溯空间更小。

**相关性与影响**:  
该工作为具身AI和多模态代理领域提供了重要的分析框架和评估视角，揭示了当前基准体系的系统性盲区（预判和验证能力评估严重不足），推动社区超越任务成功率单一指标、从五能力全面衡量代理进展。PAPAV框架可指导可靠的物理代理设计，统一了计算机视觉、机器人学和多模态学习领域对具身代理的理解，对未来构建能安全可靠执行物理任务的智能代理具有重要指导意义。

---

### 2. ProactEgoMem: Benchmarking Proactive Memory in Streaming Egocentric Video **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2610.30089](https://arxiv.org/abs/2610.30089)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30089)
- **作者**: Ruotong Liao, Meikel Kokowski, Xiaoxiao Sun et al. (9 authors)
**评估**: 该论文提出了一个面向流式第一人称视频的主动记忆基准（ProactEgoMem），核心关注可穿戴多模态助手/视频智能体如何在用户活动中自主地捕获、追踪和维护记忆（Information Capture / State Tracking / Location Tracking），并定义了Notification与Intervention两级主动性协议以及主动start-to-stop的工具调用生命周期。这本质上属于交互式、长时程的视频智能体（Video Agent）评测，而非图像/视频生成、模型蒸馏或训练推理基础设施，因此归为Agent类别。质量方面：动机清晰（减轻长时记忆认知负担、面向真实可穿戴场景），评测协议设计严谨（双层级主动性、Daily/Sci双赛道、QA质量评估），覆盖商业闭源、开源、视频-语言和流式多类基线并给出系统性失败分析，数据规模合理（300/100个片段、1000/500个问题），对主动式多模态助手和视频智能体研究有明确参考价值。扣分点在于其贡献主要是基准与协议本身，缺少方法层面的创新，且部分评测偏垂直应用（如Sci赛道），整体仍属较高质量的benchmark工作。

**核心贡献**:  
本文提出了ProactEgoMem，一个用于评测流式第一人称视频中主动记忆维护能力的基准。该基准定义了信息捕获、状态跟踪和位置跟踪三项核心任务，并在通知级别和干预级别两个层次上评估模型的主动性。实验表明，即使是最强的模型也无法同时做到及时且准确地捕获记忆，凸显了该领域的巨大挑战。

**创新点**:  
提出首个针对流式第一人称视频中主动记忆维护的基准，定义了两个主动级别（Notification Level和Intervention Level）的评测协议，涵盖信息捕获（IC）、状态跟踪（ST）和位置跟踪（LT）三项任务，并包含Daily和Sci两个平行赛道以及配套的QA评测集。

**方法**:  
设计了一个基于流式第一人称视频的标准化评测框架，包含ProactEgoMem-Daily（300个片段）和ProactEgoMem-Sci（100个片段）两个数据集，配以ProactEgoMem-QA（1000/500个问题）进行记忆质量评估。评测涵盖专有模型、开源模型、视频语言模型和流式模型等多种基线方法，在通知级别和干预级别（涉及主动的工具启动-停止生命周期管理）两个层面进行测试。

**结果**:  
跨专有、开源、视频语言和流式基线模型的评测表明，即使是表现最强的模型也无法同时做到及时且准确地捕获记忆，说明当前多模态助手在流式环境中的主动记忆能力仍存在显著不足。

**相关性与影响**:  
该基准为可穿戴主动多模态助手的发展提供了严格的评测基础，推动了能够与用户共存的视频智能体研究。它揭示了现有模型在长期记忆维护和实时场景理解方面的关键短板，对人机交互、边缘AI辅助系统和终身学习AI的发展具有重要意义。

---

### 3. AtomicRL: Atomic Reinforcement Learning for Long-Horizon Robotic Manipulation **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2610.30097](https://arxiv.org/abs/2610.30097)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30097)
- **作者**: Likui Zhang, Zhe Zhu, Zhihao Zhan et al. (10 authors)
**评估**: 论文提出AtomicRL，针对VLA（视觉-语言-动作）模型的强化学习后训练，包含SAPO语义感知信用分配和BATE瓶颈自适应探索两个具体方法创新，并构建了Real2Sim2Real部署流程。实验在LIBERO-LONG、CALVIN ABC-D等主流机器人操作基准上进行，对比PPO有明显提升（最高9.5%），且包含真实机器人实验验证（平均提升21.3%），实验充分、结果可信。属于智能体（Agent）/机器人操作策略学习方向，对VLA与RL结合的研究有实际参考价值，不属于小众垂直领域。

**核心贡献**:  
AtomicRL 是一种针对长时程机器人操作任务的强化学习后训练框架，通过将长时程任务分解为原子子任务结构，解决现有VLA-RL方法中信用分配延迟偏差和子任务掌握不均衡的问题。该方法结合语义感知策略优化和瓶颈自适应目标探索，并配备Real2Sim2Real管线实现仿真到真实机器人的迁移部署。

**创新点**:  
1) 提出语义感知策略优化(SAPO)，利用语义感知门控机制阻止失败原子子任务的TD残差跨任务边界传播，缓解信用污染同时保持子任务内信用分配和价值自举；2) 提出瓶颈自适应目标探索(BATE)，根据各原子子任务的掌握程度动态协调任务采样和局部探索激励，将学习导向剩余瓶颈子任务；3) 设计Real2Sim2Real管线，桥接仿真中的在线RL与真实世界部署，实现向物理机器人的实用迁移。

**方法**:  
将长时程操作任务分解为原子子任务结构作为信用分配的基本单元。SAPO模块通过语义感知门控机制过滤跨子任务的TD残差传播，防止失败子任务对其他子任务价值估计的污染。BATE模块监测各子任务的掌握程度，动态调整任务采样分布和探索激励策略，聚焦未充分掌握的瓶颈子任务。最后通过Real2Sim2Real管线将仿真中训练的RL策略迁移到真实机器人系统。

**结果**:  
在LIBERO-LONG基准上，AtomicRL在两种VLA架构上分别比PPO提升3.6%和4.0%的绝对性能。在CALVIN ABC-D基准上，全任务性能比PPO提升高达9.5%。结合Real2Sim2Real管线后，真实世界任务性能平均提升21.3%。

**相关性与影响**:  
该论文针对VLA模型在长时程操作任务中的关键瓶颈，提出了基于原子任务结构的信用分配和自适应探索机制，有效提升了VLA策略的RL后训练效率。Real2Sim2Real管线为仿真中RL训练向真实机器人部署提供了实用的迁移路径，对机器人操作领域的策略学习和实际部署具有重要的参考价值，推动了VLA模型从仿真走向真实世界应用的进程。

---

### 4. LocalAgent: Collaborative Agentic Verification for Fine-Grained Instance-Level Consistency **⭐⭐⭐** (相关度: 78%, 质量: 0.7)

- **arXiv ID**: [2610.29174](https://arxiv.org/abs/2610.29174)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29174)
- **作者**: Jiachen Guo, Xinshan Zhu, Boyun Wang et al. (7 authors)
**评估**: 论文提出LocalAgent协作式智能体验证框架，核心创新在于：(1) MLLM全局推理与轻量级局部验证工具（LAC/LGC）的协同机制，体现典型的Agent工具调用范式；(2) auxiliary-capped RFT策略，让答案正确性主导辅助工具使用信号，使模型学会何时需要调用验证器；(3) 实验表明4.9%的准确率提升，且仅在12.13%的样本上调用验证器，证明了方法的效率。开源仓库已发布。该任务（细粒度实例级一致性验证）虽有一定特定性，但属于视觉理解的基础能力，对多模态智能体系统构建有参考价值。类别归属于Agent，因为核心贡献是LLM智能体与工具协作的验证框架设计及相应的强化学习训练策略。

**核心贡献**:  
LocalAgent is a collaborative agentic framework that combines a generalist multimodal large language model (MLLM) with lightweight specialist verifiers to solve fine-grained instance-level consistency verification—determining whether two images depict the same physical object under varying conditions. The MLLM reasons globally to identify suspicious local regions and delegates fine-grained matching to a Local Evidence Verifier (LEV) toolkit, achieving a 4.9% mean accuracy improvement over the strongest CoT-RFT baseline while invoking verifiers on only 12.13% of samples.

**创新点**:  
1) A collaborative agentic paradigm that couples global reasoning of an MLLM with localized specialist evidence extractors (LAC for appearance and LGC for geometric matching), returning structured scalar evidence for MLLM integration. 2) An auxiliary-capped reinforcement fine-tuning (RFT) strategy that prioritizes answer correctness over auxiliary tool-use and format signals, enabling the policy to learn when verification is necessary and maintaining general multimodal capabilities.

**方法**:  
The framework operates in a two-stage pipeline: (1) the MLLM performs global reasoning over image pairs to identify suspicious local regions, and (2) a Local Evidence Verifier (LEV) toolkit processes these regions via two specialist components—Local Appearance Consistency (LAC), which estimates appearance similarity robust to illumination and color changes, and Local Geometric Correspondence (LGC), which estimates spatial correspondence robust to viewpoint changes. LEV returns structured scalar evidence that the MLLM integrates for the final consistency decision. The underlying MLLM is trained with an auxiliary-capped RFT strategy that weights answer correctness above auxiliary tool-use and format rewards.

**结果**:  
LocalAgent achieves a 4.9% improvement in mean accuracy over the strongest CoT-RFT baseline on fine-grained instance-level consistency verification benchmarks, while invoking the verifier on only 12.13% of test samples, demonstrating efficient selective use of specialist tools. The approach preserves the general multimodal capabilities of the underlying MLLM. Code is available at https://github.com/Firefly-zoo/LocalAgent-main.

**相关性与影响**:  
This work addresses a critical limitation of current MLLMs in fine-grained visual verification, which is essential for real-world applications such as object re-identification, forensic analysis, autonomous driving, and embodied AI. The collaborative agentic design demonstrates a generalizable paradigm for combining large foundation models with lightweight specialist tools in a resource-efficient manner, offering insights into scalable multi-agent reasoning for vision-language tasks. The selective verification strategy (using tools on only ~12% of cases) provides a practical blueprint for balancing accuracy and computational cost in agentic systems.

---

### 5. DONIC: Generalist Dexterous Bimanual Tracking Control from Human Demonstrations **⭐⭐⭐** (相关度: 70%, 质量: 0.8)

- **arXiv ID**: [2610.29997](https://arxiv.org/abs/2610.29997)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29997)
- **作者**: Mingze Sun, Ziang Cao, Yuan Fei et al. (11 authors)
**评估**: 论文提出通用双手灵巧操作跟踪控制器DONIC及配套BiHOI数据集，属于机器人智能体（Agent）/具身智能策略学习方向，涉及PPO与行为克隆结合的强化学习方法、奖励设计（object-centered per-hand reward）和算法改进（Clip-Centered Advantages）。创新点明确：首个跨任务类别、跨动作来源的通用双手跟踪器，配合1575条序列、229个物体的新数据集；实验充分，无需微调即在未见轨迹和未见物体上分别达到86.79%和57.32%成功率，显著超越SOTA基线（+77.36/+45.73个百分点）。虽然灵巧手操作属于相对专门的机器人子领域，但其通用跟踪框架和数据集对具身智能社区具有较高参考价值，整体质量良好。注意：在给定四个候选类别中均不完全匹配，最接近Agent（智能体/具身策略）。

**核心贡献**:  
DONIC 是首个在多种操作类别和人类运动来源上联合训练的通用灵巧双手追踪控制器，同时提出了 BiHOI 数据集——包含 1,575 段多视角序列、229 个物体，专门强调持续性双手交互。该方法通过 PPO 与行为克隆的反馈循环，以及物体中心的逐手奖励和片段中心化优势估计，实现了在无需微调的情况下对未见轨迹和物体的高效追踪。

**创新点**:  
1) 首个通用灵巧双手追踪策略（DONIC），可跨异构参考运动和操作类别进行协调控制；2) BiHOI 数据集，专注接触密集的持续性双手操作；3) 将 PPO 与行为克隆结合的反馈循环机制，将验证成功的执行回收入训练数据；4) 物体中心逐手奖励设计，根据每只手的参考接触角色进行监督；5) Clip-Centered Advantages（片段中心化优势），消除参考相关的偏移同时保留轨迹内差异。

**方法**:  
DONIC 采用 PPO 与行为克隆（BC）相结合的训练框架：PPO 通过探索获得成功轨迹，BC 利用人类演示和回收的成功执行进行训练，二者形成反馈闭环。奖励设计采用物体中心的逐手奖励函数，跟踪物体运动并根据参考接触角色监督每只手。Clip-Centered Advantages 对参考相关的 advantage 偏移进行片段级中心化处理，保留轨迹内的相对差异，从而支持单一策略学习跨异构参考的协调操作。

**结果**:  
在无需微调的条件下，单一策略在训练物体的未见轨迹上达到 86.79% 的成功率，在保留物体上达到 57.32% 的成功率，分别超越现有最强双手追踪基线 77.36 和 45.73 个百分点。

**相关性与影响**:  
该工作填补了灵巧双手操控追踪领域的空白，将单手追踪扩展至现实生活中更为常见的双手操作场景。通用策略的跨物体、跨轨迹泛化能力对机器人辅助装配、家务服务和工业双臂协作等应用具有重要意义。BiHOI 数据集的发布也有助于推动接触密集型双手操作研究的发展。

---


---

## 🌍 World Model 相关内容

### 1. PhysiCalWorld: In-Context Physics Calibration for World Models **⭐⭐⭐⭐** (相关度: 93%, 质量: 0.8)

- **arXiv ID**: [2610.30125](https://arxiv.org/abs/2610.30125)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30125)
- **作者**: Yunhao Luo, Wentao He, Yinpei Dai et al. (8 authors)
**评估**: 论文核心是改进 action-conditioned world models 的物理动力学建模，属于世界模型方向。创新点明确：通过 in-context prompting 编码探索性交互片段为物理描述符 token，在不微调、不依赖物理标签的情况下校准实例级物理参数（质量分布、阻尼、摩擦等），缓解了世界模型在新场景中的预测漂移问题。方法设计有技术含量（端到端潜空间预测训练、描述符 token 一次提取可复用、开销可忽略），实验覆盖四个不同物理变化的环境，评估包含 rollout 预测精度与视觉规划成功率两个维度，且展示了描述符潜空间的物理结构化和对训练范围外物理参数的泛化能力。整体上对世界模型的物理一致性研究有实际参考价值，属于高质量论文；不足是主要在仿真环境验证，真实世界泛化性尚未展示。

**核心贡献**:  
PhysiCalWorld 提出了一种通过上下文提示对动作条件世界模型进行物理校准的方法，无需微调或解析物理建模，即可使模型适应实例特定的动态特性。该方法将测试场景中采集的探索性交互片段编码为紧凑的物理描述符令牌，从而指导后续预测在场景真实物理行为的约束下进行。实验表明该方法显著提升了轨迹预测精度和视觉规划成功率。

**创新点**:  
提出通过在上下文中提供探索性交互片段作为提示，将隐含的物理参数（如质量分布、关节阻尼、表面摩擦）编码为物理描述符令牌，实现世界模型的无需微调物理校准；描述符通过仅使用潜在预测损失端到端训练，无需物理标签；推理时仅需提取一次描述符即可在多次推演中复用，计算开销极小；学习到的描述符构成具有物理结构化的潜在空间，能够泛化到训练时未见过的物理范围。

**方法**:  
核心方法是：(1) 在测试场景中收集一段探索性交互片段（exploratory interaction clip）；(2) 使用编码器将该片段编码为紧凑的物理描述符令牌（physics descriptor token）；(3) 将该描述符令牌作为上下文提示注入动作条件世界模型中，引导后续视觉帧预测和动态推理；(4) 端到端训练仅使用潜在预测损失（latent prediction loss），不依赖任何物理参数标签；(5) 推理时描述符令牌一次性提取，跨多次rollout复用，开销可忽略。

**结果**:  
在四个涵盖多样物理变化的环境中进行了评估：(1) 大幅提升了rollout预测精度，减少了在新颖测试场景中的预测漂移；(2) 显著提高了视觉规划成功率；(3) 学习到的物理描述符形成具有物理语义结构的潜在空间；(4) 描述符对训练期间未见过的物理参数范围展现出良好的泛化能力。

**相关性与影响**:  
该论文对世界模型和具身智能领域具有重要意义：通过上下文学习而非参数微调来校准物理动力学，为世界模型在新场景中的部署提供了一种高效且通用的解决方案；物理描述符的结构化潜在空间为理解和操控隐含物理属性提供了新途径；该方法在机器人操控、导航等需要准确物理推理的任务中具有广泛的应用前景，同时其无需物理标签的自监督训练范式降低了对标注数据的依赖。

---

### 2. ALPS: Visual State Encoders for World Models **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.30120](https://arxiv.org/abs/2610.30120)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30120)
- **作者**: Yanqing Liu, Letian Zhang, Chengzhi Liu et al. (8 authors)
**评估**: 论文提出ALPS视觉状态编码器，旨在为世界模型提供统一的视觉基础表征（融合语言对齐、像素重建与空间对应三大能力），核心贡献明确属于世界模型的视觉编码基础研究。实验充分：在15个公开编码器上进行统一评估，LIBERO state-probe误差最低，下游策略成功率85.5%达到SOTA水平，并在PushT、Wall、Granular等多个世界模型规划任务上验证泛化能力。跨视角自蒸馏为独立技术亮点。属高质量工作。

**核心贡献**:  
ALPS 提出了一个统一的预训练视觉状态编码器（ViT-B/16），将物理状态信息、语言对齐能力和像素重建能力整合到同一组 patch tokens 中，以同时支持世界模型的预测、指令理解与可视化检查。仅使用静止图像和文本，通过语言、重建和空间对应目标从零预训练，并经跨视角自蒸馏进一步精炼。在十五个公开编码器的统一评测中，ALPS 取得 ViT-B 级别模型中最低的 LIBERO 状态探测误差，匹配规模大 3.5 倍的 V-JEPA 2-L，同时保持强语言对齐与精确像素重建。

**创新点**:  
首次将物理状态感知、语言对齐与像素重建三种能力统一到单一视觉编码器的同一组 patch tokens 中；提出基于静止图像的多目标预训练（语言对齐 + 重建 + 空间对应）与跨视角自蒸馏精炼流程；使预测出的未来 token 可直接解码为像素，实现可视化检查；配套提出原生文本塔以最大化策略性能。

**方法**:  
从零预训练一个 ViT-B/16 视觉编码器，使用仅含静止图像与文本的数据，联合优化三类目标：语言对齐目标（vision-language alignment）、像素重建目标（reconstruction）与空间对应目标（spatial correspondence）。随后通过跨视角自蒸馏（cross-view self-distillation）对编码器进行精炼，以增强对物理状态的表征能力。下游应用中，冻结的 ALPS tokens 与原生文本塔（native text tower）组合，用于 LIBERO 机器人策略学习、世界模型规划（PushT、Wall、Granular）以及未来 token 的像素解码可视化。

**结果**:  
在十五个公开视觉编码器的统一评测中：ALPS 取得 ViT-B 模型中最低的聚合 LIBERO 状态探测误差，匹配大 3.5 倍的 V-JEPA 2-L；同时保持强语言对齐性能和高精度像素重建。冻结 ALPS tokens 配合原生文本塔在 LIBERO 上达到最高平均策略成功率 85.5%；在 PushT、Wall 和 Granular 的世界模型规划任务上匹配或超越主流编码器；预测的未来 token 可直接解码为像素用于视觉检查。

**相关性与影响**:  
该工作明确了世界模型视觉基础模型应兼具状态感知、语言对齐与像素重建三重能力的设计原则，推动视觉预训练成为世界模型中理解、预测与行动共享的基础。ALPS 以较小模型规模达到与更大模型（V-JEPA 2-L）相当的状态表征质量，展示了统一表征在提升样本效率、可解释性（像素级检查）与跨任务泛化方面的潜力，对机器人学习、具身智能与视频预测等方向具有重要参考价值。

---

### 3. LiveAct: Towards Real-Time Multi-Agent World Models with Heterogeneous Action Interfaces **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2610.29408](https://arxiv.org/abs/2610.29408)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29408)
- **作者**: Xinyu Wang, Huafeng Shi, Yue Ma et al. (12 authors)
**评估**: 论文聚焦交互式视频世界模型（interactive video world models），研究多智能体联合未来预测与异构动作接口，属于典型的World_Model方向。核心贡献明确：(1) 提出Heterogeneous Action Interface (HAI)，通过Agent-Aware Spatial Modulation实现各动作流对视觉实体的独立控制，通过Schema-Guided Action Adaptation处理异构控制语义；(2) 将接口迁移到blockwise causal生成器，结合teacher forcing与rollout-aware分布匹配实现流式实时生成（17.7 FPS @ 512x448）；(3) 任务设定新颖，是首个系统研究多智能体+异构动作接口的世界模型工作，实验覆盖游戏与多机器人操作六个数据源，评估指标包括视觉质量、动作跟随、agent归属准确率（0.898/0.942）和延迟，实验较为充分。虽非图像/视频生成主线（生成是被评估的工具，核心是可控性与世界建模），但与Training_Inference_Infra或Distillation无关，故归入World_Model。局限：主要在相对受限的游戏与机器人场景验证，通用性尚待考察，故质量分未给到顶尖水平。

**核心贡献**:  
LiveAct introduces a multi-agent video world model that generates joint visual futures for multiple controlled agents while interpreting heterogeneous action interfaces ranging from discrete game buttons to continuous robot commands. The core contribution is the Heterogeneous Action Interface (HAI), which independently binds each agent's action stream to its intended visual entity and adapts the semantics of control variables across different tasks through language-guided modulation. The framework is further transferred to an efficient blockwise causal generator suitable for real-time streaming generation.

**创新点**:  
提出 Heterogeneous Action Interface (HAI)，包含两个核心组件：(1) Agent-Aware Spatial Modulation，通过语言驱动的空间门控和智能体特定注意力机制，将每个动作流独立绑定到其对应的视觉实体；(2) Schema-Guided Action Adaptation，用语言描述每个控制变量并将其语义 token 与同步数值调制结合，使同一模型能理解游戏中攻击按钮、转向命令、机器人指令等异构控制接口的语义。

**方法**:  
方法包括三个层次：(1) Agent-Aware Spatial Modulation 使用语言描述生成空间注意力掩码，结合 agent-specific self-attention 确保每个动作流独立控制对应视觉智能体；(2) Schema-Guided Action Adaptation 将每个控制维度用自然语言 schema 描述，语义 token 与数值编码融合后注入条件；(3) 通过 teacher forcing 和 rollout-aware distribution matching 将完整接口迁移到块状因果视频生成器，实现流式生成并保持智能体级别的控制与动作语义。

**结果**:  
在涵盖游戏和多机器人操作的六个多智能体数据集上评估：在无需智能体位置或身份裁剪的条件下，游戏场景和机器人操作场景的智能体归属准确率分别达到 0.898 和 0.942；因果生成器在 512×448 分辨率下达到 17.70 FPS 的实时推理速度，同时保持良好的视觉质量、动作跟随能力和低延迟特性。

**相关性与影响**:  
该论文将视频世界模型从单智能体单任务扩展到多智能体、异构控制的新范式，对交互式游戏模拟、多机器人协同控制、具身智能体训练等方向具有重要意义。其 HAI 接口设计为解决动作语义对齐和多实体独立控制问题提供了可推广的框架，因果生成器的实时性能使实际部署成为可能。

---

### 4. Rethinking Video Autoencoders for Interactive World Models **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2610.30129](https://arxiv.org/abs/2610.30129)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30129)
- **作者**: Adrien Ramanana Rahary, Yutong Bai, Nicolas Dufour et al. (5 authors)
**评估**: 该论文以视频世界模型（video world models）的自动编码器设计为核心，探讨了世界模型在潜空间中压缩的最优策略。论文贡献明确：(1) 构建了CADRE——开源的因果扩散表示自编码器家族，支持多种时空压缩率；(2) 冻结特征上仅用小瓶颈模块实现不同压缩，扩散解码器自蒸馏至1-2步；(3) 在机械臂操作和导航两个领域、共四个环境中进行系统性对比实验；(4) 提出四个有价值的发现（强压缩下扩散解码器优于感知回归、操作任务中时间压缩更有效、操作与导航需要相反的压缩策略、空间token粗糙度对运动的影响远大于图像质量等）。论文来自知名团队Kytai，发布了代码、模型和在线演示，实验系统充分，对世界模型和具身智能社区具有较高参考价值。

**核心贡献**:  
The paper rethinks how video autoencoders for interactive world models should compress spatio-temporally, arguing that autoencoders borrowed from text-to-video generators are suboptimal for world models where action latency matters. The authors introduce CADRE, an open family of causal diffusion representation autoencoders at multiple compression levels, and conduct a systematic study across manipulation and navigation domains to map the latency-quality trade-off.

**创新点**:  
CADRE: an open, unified family of causal diffusion representation autoencoders that vary only by a small bottleneck on frozen features and share a diffusion decoder self-distilled to one or a few steps, enabling controlled study of how, where, and how much a world model should compress.

**方法**:  
Builds causal diffusion autoencoders spanning multiple spatio-temporal compressions by adding a small bottleneck on frozen encoder features and training a shared one/few-step self-distilled diffusion decoder. Trains identical world model architectures on each autoencoder across two task domains (manipulation and navigation) with two environments each, systematically evaluating the latency–quality frontier.

**结果**:  
CADRE forms most of the latency–quality frontier, especially with a moving camera. At strong compression, the diffusion decoder produces sharper outputs than perceptual regression. For robot manipulation, temporal compression is more effective in the autoencoders than in the world model. Manipulation and navigation favor opposite compression strategies: temporal compression is cheap with a still camera while spatial compression is preferred when the camera moves. With a still camera, coarser spatial tokens hurt motion quality far more than image quality.

**相关性与影响**:  
The work provides actionable guidance for designing world-model autoencoders, showing that compression choices should depend on task domain and camera dynamics. By releasing CADRE models, code, and a live demo, it lowers the barrier to training and evaluating interactive world models and influences how the community co-designs world models and their representation bottlenecks.

---

### 5. WorldStream: Streaming Interactive 3D Worlds with Hierarchical Planning and Persistent State **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2610.28827](https://arxiv.org/abs/2610.28827)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.28827)
- **作者**: Xiaoxiao Ma, Weiyang Jin, Yanwen Ma et al. (14 authors)
**评估**: 论文提出WorldStream，一个开放式的可交互3D世界模型，核心贡献包括：(1) 层次化规划器（Macro/Micro两级）+类型化决策模型，将语言指令结构化编译为地形、道路、聚落、生态等世界内容；(2) 流式生成机制——沿预测走廊超前规划、按需编译、释放用户身后的几何，在有界预算下实现无限扩展；(3) 单一持久世界记录（world record）维护规划、种子、对象身份、可变状态与用户编辑，支撑跨区域一致性与编辑回归。这些属于世界模型（World Model）方向的实质性技术设计，具有明确的系统性创新，面向开放世界游戏、具身交互、生成式仿真等高价值场景，符合当前世界模型研究热点（与Genie、GameGen等方向相关）。不足之处：摘要未呈现充分的定量实验与基线对比，方法偏系统/工程化，确定性局部代码编译（而非神经生成）可能限制泛化性；结合方向热度与创新性，质量评为中上，判定为高质量但非顶级。

**核心贡献**:  
WorldStream 提出了一个开放式、可流式生成的交互式 3D 世界模型，具备三项同步能力：生成超出预设地图的可探索地形、对运行中的世界执行开放语言指令的交互操作、并在重访时恢复已访问区域及其修改。核心在于层次化规划器（Macro/Macro 决策层 + Micro 细化层）与确定性局部代码编译器的解耦，配合单一持久世界记录实现有界预算下的持续扩展与状态保持。

**创新点**:  
1) 层次化规划：Macro 层在 tile 分组尺度上确定聚落、生态、交通与水文结构，Micro 层在实测地形与相邻 tile 承诺约束下细化为单 tile 语义；2) 决策与执行解耦：确定性本地代码将已接受的规划编译为地形、道路、聚落、植被和实体，保证跨独立规划 tile 的连通性；3) 流式执行调度：规划沿预测走廊提前运行，仅在即将被访问处编译，用户身后的几何体释放以控制预算；4) 单一持久世界记录保存规划、种子、物体身份与可变状态、边界承诺及属性级编辑，使区域可重编译并支撑实体级交互与 NPC 状态更新。

**方法**:  
整体采用『类型化决策模型 + 层次化规划器 + 确定性编译器 + 流式调度 + 单一持久状态记录』的系统架构：(a) 类型化决策模型输出结构化决策状态；(b) Macro/Micro 两层规划通过邻居承诺（neighbor commitments）机制保证跨 tile 一致性；(c) 确定性局部代码将计划编译为具体几何与实体；(d) 流式模块按预测移动走廊管理规划、编译与几何释放的范围；(e) 中央世界记录以属性级方式维护可变状态与用户编辑，并在重访时驱动重新编译；(f) 交互层支持对现有实体操作（含状态化 NPC）、编辑当前区域、以及向未规划区域附加意图。

**结果**:  
论文为系统/模型论文，主要以定性与系统性演示为主：展示世界在有界资源预算下持续扩展、跨独立规划 tile 保持连通、被访问区域可按编辑状态精确恢复，以及开放语言指令驱动的实体级与区域级交互（包括随时间更新的 NPC）。arXiv ID 为 2610.28827。

**相关性与影响**:  
该工作面向开放世界生成、交互式世界模型与游戏/仿真自动化方向，将程序化生成（PCG）与学习式规划结合，缓解了扩散式世界模型在长时程一致性、可编辑性和持久状态上的瓶颈。其层次化规划与确定性编译解耦的范式可推广至机器人仿真、数字孪生、交互式叙事与具身智能训练环境构建，对需要长时序一致、可交互、可回滚的 3D 内容生产具有重要参考价值。

---

### 6. DepState-JEPA: Learning Depth-Grounded State Representation for Visual Perception and Manipulation **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2610.29246](https://arxiv.org/abs/2610.29246)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29246)
- **作者**: Xiujian Liang, Liuyuan Na, Zehao Du et al. (9 authors)
**评估**: 论文提出 DepState-JEPA，一种基于 V-JEPA 2.1 的 RGB-Depth 双流联合嵌入预测架构，通过共享潜在状态进行动作条件化的状态转移预测，属于典型的预测式世界模型（world model）范式，用于机器人操作中的感知与状态表征学习，因此归入 World_Model。质量方面：(1) 有明确的技术创新——将深度流引入 JEPA 框架，以度量 3D 空间接地两种模态，并设计 ray-conditioned readout、动作条件化转移、FK 正则化等机制；(2) 实验较充分，包含编码器迁移、特征补全、视觉预测、操作成功率等多维度对比以及 Within-model 消融；(3) 面向机器人操作这一活跃研究方向，具有一定参考价值。不足之处：方法建立在已有 V-JEPA 2.1 之上，增量式扩展的原创性有限；核心应用场景聚焦机器人操作，受众相对专门，但仍在具身智能主流范畴内，不属于小众垂直领域。综合评估为中高质量论文。

**核心贡献**:  
本文提出 DepState-JEPA，一种双流 RGB-Depth 联合嵌入预测架构（基于 V-JEPA 2.1），通过共享隐状态 DepState 将场景几何理解与动作条件下的状态变化预测连接起来。深度信息既作为互补观测流，也用于将两种模态锚定在度量 3D 空间中，从而在机器人操作任务中实现更强的视觉预测与操作成功率。

**创新点**:  
1) 提出以深度接地（depth-grounded）的共享状态表示 DepState，把 RGB 与深度模态的共享信息聚合到度量 3D 空间；2) 设计双流联合嵌入预测框架，区分模态共享特征与模态私有特征，并通过固定初始私有特征 + 预测状态解码未来 RGB/深度特征；3) 引入 ray-conditioned readout 无需目标深度即可预测局部特征，并结合物体轨迹监督与校准的正向运动学（FK）一致性约束（joint-TCP 一致性）来塑形状态学习。

**方法**:  
基于 V-JEPA 2.1 构建双流 RGB-Depth 编码器，输出模态共享特征与模态私有特征；共享特征聚合为 DepState，并用深度带来的度量 3D 坐标（如 ray/点云坐标）进行空间接地。使用 ray-conditioned readout 从状态读出局部特征；经过动作条件化的状态转移模块后，用相同的解码器预测未来 RGB 与深度特征（配合固定的初始私有特征）。机器人本体感受（robot-state）读出提供递归输入；监督信号包括物体轨迹目标以及校准正向运动学带来的 joint-TCP 一致性正则。消融实验分析深度内容、度量坐标、未来状态匹配和 FK 正则各自的贡献。

**结果**:  
对比实验表明：(1) 经 RGB-D 适配后 RGB 编码器迁移能力更强；(2) 在特征补全（feature completion）任务上表现更优；(3) 条件化视觉预测（conditioned visual forecasting）质量更高；(4) 机器人操作成功率显著提升。消融显示深度内容、度量 3D 坐标和未来状态匹配均带来增益，FK 正则进一步提供额外控制性能提升。

**相关性与影响**:  
该工作将深度几何 grounding 引入 JEPA 类预测表征学习，弥合了视频自监督表征与机器人操作中 3D 状态预测之间的鸿沟。它对机器人操作中的视觉表征学习、世界模型（world model）、RGB-D 多模态预训练以及 sim-to-real 迁移具有重要参考价值，并展示了以几何为基础的预测状态在真实操作任务中的实用价值。

---

### 7. OccJEPA: Occlusion as Masking for Amodal Video Segmentation **⭐⭐⭐⭐** (相关度: 80%, 质量: 0.8)

- **arXiv ID**: [2610.29061](https://arxiv.org/abs/2610.29061)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29061)
- **作者**: Genpei Zhang
**评估**: 论文核心是利用自监督视频世界模型（V-JEPA 2.1 JEPA家族）的预测器，将遮挡视为掩码补全任务来实现amodal视频分割，最相关的类别是World_Model。技术上有清晰的创新点：将occlusion形式化为masking、用预训练世界模型预测器填充被遮挡时空区域、轻量解码头解码，且实验证明性能提升来自预训练权重而非模型容量（87M到1.85B参数的对照实验）。实验充分：在SAIL-VOS、TAO-Amodal（含held-out测试集+4.00 AP50）、Kubric等多个基准上验证，相比扩散式SOTA提速33.5倍且更准确，代码开源，方法论分析扎实，对视频理解与世界模型落地有实际参考价值。

**核心贡献**:  
OccJEPA 提出将非模态视频分割中的遮挡问题重新表述为空间-时间掩码补全：直接复用预训练的自监督视频世界模型 V-JEPA 2.1 的预测器，对被物体可见掩码之外（即被遮挡）的 token 进行填充，再由轻量解码头将观测特征与预测特征解码为完整的非模态掩码。该方法是确定性的，相比基于视频扩散模型的最先进方法快 33.5 倍，同时在 SAIL-VOS、TAO-Amodal（含留出测试集与 SAM2 跟踪的可见掩码）以及 Kubric 数据集上精度更高。

**创新点**:  
首次提出“遮挡即掩码”（Occlusion-as-Masking）的思想，将非模态视频分割这一密集感知任务映射到 JEPA 家族世界模型所训练的时空掩码预测任务上，从而零改动地复用预训练视频世界模型的能力，用确定性前向推理替代多步去噪的视频扩散模型，无需额外深度网络。

**方法**:  
1) 输入非模态视频，利用物体可见掩码将未被覆盖的时空 token 丢弃（等价于掩码）；2) 使用预训练 V-JEPA 2.1 predictor 根据可见部分预测被遮挡区域的表征；3) 一个轻量解码头将观测到的特征与预测特征联合解码为逐帧完整（含遮挡部分）的非模态分割掩码。此外通过覆盖 87M 至 1.85B 参数规模的世界模型进行受控消融实验，区分预训练权重与模型容量的贡献。

**结果**:  
1) 推理速度比扩散式 SOTA 快 33.5 倍，且输出确定性可复现；2) 在 SAIL-VOS、TAO-Amodal（含留出测试集）和 Kubric 上均取得更优精度，其中留出测试集上 AP50 提升 +4.00；3) 在使用 SAM2 跟踪的可见掩码作为输入时同样有效；4) 消融实验表明性能提升来源于 predictor 的预训练权重而非其容量大小，在 87M 到 1.85B 参数范围内均成立。代码已开源：https://github.com/zgp110/occjepa。

**相关性与影响**:  
该工作为密集感知任务与视频世界模型之间架起了桥梁，验证了预训练时空表征可直接迁移到下游几何/遮挡推理任务，推动了世界模型从以运动生成/评估为主的用途向实际计算机视觉应用的转变。其确定性、无需深度网络、低计算开销的特性使非模态分割更易于在真实场景（机器人感知、自动驾驶、视频编辑）中部署，并为后续研究如何将 JEPA 类模型作为通用视觉骨干提供了实证依据。

---

### 8. How Representational Priors Shape Generalization in World Action Models **⭐⭐⭐** (相关度: 75%, 质量: 0.7)

- **arXiv ID**: [2610.29168](https://arxiv.org/abs/2610.29168)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29168)
- **作者**: Junha Chun, Youngjoon Jeong, Taesup Kim
**评估**: 论文聚焦于世界动作模型（World Action Models, WAMs），研究不同生成骨干网络的表示先验如何通过表示几何（nuisance orthogonality）影响策略泛化能力，并提出可前瞻性预测世界模型鲁棒性的几何度量，属于典型的世界模型理论分析工作。研究具有明确的科学假设和量化指标，在多种图像/视频骨干上验证，对世界模型的骨干选型与泛化机理有参考价值。不足之处在于其偏分析性、方法论贡献相对有限，实验规模与实际系统级影响未在摘要中充分体现，故质量评分中等偏上。

**核心贡献**:  
该论文研究了世界-动作模型(WAMs)泛化能力的差异如何源于其生成骨干网络的表示先验。论文提出用干扰正交性(nuisance orthogonality)量化表示先验的质量，即特征在经验分布内流形之外的视觉变化干扰下与分布内流形的正交程度，发现正交性越高，策略训练后的鲁棒性越强。论文还揭示了鲁棒WAMs中的干扰抑制(nuisance suppression)现象。

**创新点**:  
提出了'干扰正交性'(nuisance orthogonality)作为度量生成骨干表示先验质量的几何指标，能够前瞻性地预测WAM策略训练后的泛化鲁棒性；并发现了'干扰抑制'(nuisance suppression)这一鲁棒WAMs的几何特征。

**方法**:  
跨多种图像和视频生成骨干网络进行实验，通过分析表示几何中分布内流形与干扰变化的正交性来量化表示先验的质量；在策略训练后分析特征位移的相对抑制和动作生成的鲁棒性。

**结果**:  
表明更高的干扰正交性与WAM训练后更强的视觉变化鲁棒性相关联，策略的泛化能力可提前从表示先验中预测；鲁棒的WAMs表现出干扰抑制现象，即对分布外视觉变化引起的特征位移的相对抑制以及鲁棒的动作生成。

**相关性与影响**:  
为世界模型和策略学习的泛化能力提供了几何视角的理论框架，有助于解释不同生成骨干网络在下游任务中表现差异的根本原因，为选择和设计更鲁棒的WAM骨干网络提供了前瞻性的评估指标。

---

### 9. VoxProg: 3D Spatial Reasoning through Voxel Programming **⭐⭐⭐** (相关度: 72%, 质量: 0.8)

- **arXiv ID**: [2610.30127](https://arxiv.org/abs/2610.30127)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.30127)
- **作者**: Zhichao Zhai, Menglei Zhao, Guikun Chen et al. (7 authors)
**评估**: 该论文提出VoxProg方法，将3D空间推理问题形式化为体素编程，利用语言模型生成可执行程序来解决3D物体放置任务。论文核心贡献包括：(1) 提出基于规则网格体素视图的空间推理新范式，能够显式处理表面几何和邻域关系；(2) 构建了包含71个任务的VoxProg-Bench基准和配套评估套件（Intent Alignment和3D Physical Validity）；(3) 通过视觉和数值反馈实现迭代式程序修正。论文在关系型、关键点型和网格型多种基线上表现出一致优势，实验充分，方法有创新性，属于3D空间理解和推理（World_Model）范畴。虽然场景聚焦于物体放置，但其体素编程的思路对3D空间推理领域有较好的参考价值。

**核心贡献**:  
VoxProg将3D物体放置任务形式化为体素编程：语言模型把任务解析为可在场景表面局部体素视图上执行的程序，先生成证据程序定位任务相关区域与边界，再生成位姿程序计算SE(3)目标位姿，并借助视觉与数值反馈迭代修正代码。作者同时提出了包含71个开放性放置任务的VoxProg-Bench基准，以及意图对齐（Intent Alignment）和3D物理有效性（3D Physical Validity）评测套件。

**创新点**:  
1) 提出体素编程范式，将语言模型生成的程序作用于规则网格化的体素视图，使几何引用从隐式变为显式坐标与邻域关系；2) 将3D放置分解为证据程序（区域/边界筛选）与位姿程序（几何量测与SE(3)求解）两阶段可执行流程；3) 引入基于执行反馈（视觉+数值）的迭代式代码修订机制；4) 构建VoxProg-Bench基准与配套的感知/物理评测指标。

**方法**:  
以场景表面网格构建局部体素视图作为程序操作空间；语言模型解析任务并生成可执行的证据程序，从网格中直接分离任务相关区域与边界；下游位姿程序测量所得几何并计算目标SE(3)位姿；执行过程中获取视觉与数值反馈，供模型检查中间选择与候选放置结果，循环迭代地修改代码直至满足约束。

**结果**:  
在VoxProg-Bench（71个覆盖功能用途、几何契合与上下文布局的任务）及外部基准上，VoxProg在意图对齐与3D物理有效性等指标上持续优于基于关系（relation-based）、关键点（keypoint-based）和网格（mesh-based）的基线方法。

**相关性与影响**:  
该工作为3D空间推理与具身操作中的物体放置提供了可解释、可验证的程序化解决方案，弥合了语言模型任务理解与显式几何计算之间的鸿沟；其基准与评测协议有助于推动3D空间推理研究的标准化，并对机器人操作、3D场景理解与人机交互等方向具有应用价值。

---

### 10. PhyMo: Learning Physical Dynamics with Accurate and Continuous Motion from Multi-View Videos **⭐⭐⭐** (相关度: 72%, 质量: 0.8)

- **arXiv ID**: [2610.29107](https://arxiv.org/abs/2610.29107)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2610.29107)
- **作者**: Shangjia Liu, Jinxi Li, Siyuan Zhou et al. (5 authors)
**评估**: 论文提出PhyMo框架，从多视角视频中恢复动态三维场景的几何、外观与物理运动状态，并进行未来运动外推，核心在于学习场景演化的物理动力学（位移、速度、加速度的连续演化与双向运动学连续性约束），这与World_Model（世界模型：建模环境状态转移与未来预测）的范畴最为契合，而非单纯的内容生成。技术上有明确的创新点（Motion-Aware Trajectory Representation解决外观捷径问题、Continuous Motion Evolution模块），在四个动态场景基准上报告了SOTA结果，实验较为充分，对动态3D重建与可预测世界模型研究有参考价值。扣分点：缺乏作者机构信息佐证，方法基于神经渲染/变形场体系，创新幅度属于渐进式改进。

**核心贡献**:  
PhyMo提出了一种从多视角视频中学习动态场景物理运动的框架，通过运动感知轨迹表示和具有双向运动学连续性约束的连续运动演化模块，解决了外观监督下模型可能利用颜色/不透明度捷径掩盖不准确形变的问题。该方法实现了几何忠实的插值和连续的运动外推，在四个动态场景基准上达到了最先进性能。

**创新点**:  
1) Motion-Aware Trajectory Representation（运动感知轨迹表示）：迫使模型从形变中恢复真实运动，而非依赖外观捷径来解释观测运动；2) Continuous Motion Evolution模块，结合双向运动学连续性约束（bidirectional kinematic continuity constraint），促进位移、速度和加速度在时间上的一致演化，从而实现可靠的未来预测与插值。

**方法**:  
基于多视角动态视频的神经渲染框架，引入运动感知轨迹表示来解耦几何运动与外观建模，防止渲染监督下的外观捷径；在此基础上构建连续运动演化模块，对位移、速度、加速度施加双向运动学连续性约束，保证运动的时间一致性，实现几何忠实的插值与连续外推。

**结果**:  
在四个动态场景基准上进行了实验，展示了state-of-the-art性能，实现了几何上忠实的插值和连续的运动外推。

**相关性与影响**:  
该工作对动态3D场景重建、物理运动恢复和神经渲染领域具有重要意义，解决了动态NeRF类方法中外观与形变退化的关键问题，可推动视频预测、物理仿真驱动的场景理解以及机器人/自动驾驶中的动态环境感知等应用。

---


---

## 📊 统计信息

| 类别 | 论文数量 | 占比 |
|------|----------|------|
| 🎨 AIGC 相关内容 | 1 | 0.9% |
| 🖼️ 图像/视频/全模态生成 | 10 | 9.4% |
| 🧠 大模型蒸馏与压缩 | 3 | 2.8% |
| ⚙️ 训练推理基础设施 | 9 | 8.5% |
| 🧠 Agent 相关内容 | 5 | 4.7% |
| 🌍 World Model 相关内容 | 10 | 9.4% |
| 其他 | 68 | 64.2% |
| **总计** | **106** | **100%** |
