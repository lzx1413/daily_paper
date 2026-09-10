# 📚 arXiv CS.CV 每日论文报告

**报告日期**: 2026-09-10  
**论文来源**: [arXiv CS.CV Recent](https://arxiv.org/list/cs.CV/recent)  
**关注论文数**: 45篇（每类别Top 10，经质量筛选）

> 注：每类别按大模型评估的相关性和质量排序，仅展示前10篇高质量论文。已自动过滤低质量和小众方向论文。

---

## 📑 目录

- [🎨 AIGC 相关内容](#aigc) (0篇)
- [🖼️ 图像/视频/全模态生成](#image_video_omni_generation) (10篇)
- [🧠 大模型蒸馏与压缩](#distillation) (5篇)
- [⚙️ 训练推理基础设施](#training_inference_infra) (10篇)
- [🧠 Agent 相关内容](#agent) (10篇)
- [🌍 World Model 相关内容](#world_model) (10篇)

---

## 🖼️ 图像/视频/全模态生成

### 1. Multi-History-Step SDE Inversion for Image Editing with Superior Regional Awareness **⭐⭐⭐⭐** (相关度: 96%, 质量: 0.8)

- **arXiv ID**: [2609.06602](https://arxiv.org/abs/2609.06602)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06602)
- **作者**: Haiyan Wei, Yunlong Wang, Huaibo Huang et al. (5 authors)
**评估**: 该论文聚焦基于扩散SDE反演的无训练图像编辑，提出MIEdit框架，属于图像生成与编辑方向，因此归类为Image_Video_Omni_Generation。方法上引入多历史步预测-校正SDE反演、自动语义角度掩码IASM，并构建EditEval++评测集，具有明确技术创新和较充分实验支撑，不属于低质量或小众垂直应用方向。

**核心贡献**:  
本文提出 MIEdit，一种基于扩散随机微分方程（SDE）反演的无训练图像编辑框架。该方法通过预测-校正多历史步方案，在更少步数下实现更优编辑质量，并提升大编辑下的稳定性与可塑性。同时引入反演时自动语义角度掩码（IASM），无需额外用户输入即可增强区域感知与未编辑区域保持能力。

**创新点**:  
主要创新包括：提出多历史步 SDE 反演与预测-校正方案，以更少采样步数实现高质量编辑；缓解多条件噪声残差与梯度项之间的异质性和冲突，提升大编辑下的稳定性和编辑可塑性；设计 Inversion-Time Automatic Semantic Angle Masking（IASM），利用无分类器引导在反演阶段自动生成语义角度掩码，并在采样全程施加区域约束；构建 EditEval++ 细粒度评估基准。

**方法**:  
MIEdit 基于扩散 SDE 反演进行无训练图像编辑，采用预测-校正的多历史步采样机制。针对多条件噪声残差与梯度项在采样中的异质性和冲突问题，方法对其进行缓解以增强稳定性和大编辑能力。IASM 利用无分类器引导在反演阶段自动生成语义角度掩码，并将其应用于整个采样过程以施加区域约束，无需额外用户输入。

**结果**:  
论文在自建的 EditEval++ 基准上进行全面评估，该基准包含 30 个细粒度任务和 1000 多个图像-文本-掩码三元组。实验表明 MIEdit 优于当前最先进方法，能够以更少步数获得更优编辑质量，并具有更好的区域保持能力。

**相关性与影响**:  
该工作推动了无训练扩散图像编辑的发展，在效率、编辑可塑性和区域感知方面改进了现有 SDE 反演与无反转方法。其自动掩码机制降低了用户交互需求，EditEval++ 也为细粒度图像编辑评估提供了新基准，对图像编辑、扩散模型反演和可控生成等方向具有潜在影响。

---

### 2. VoT: Vision-of-Thought for Unified Multimodal Representation Alignment **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.07815](https://arxiv.org/abs/2609.07815)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07815)
- **作者**: Jingxiang Sun, Chao Liao, Zhengxiong Luo et al. (9 authors)
**评估**: 该论文提出Vision-of-Thought (VoT)框架，在VLM和DiT之间引入离散视觉思考层，用于text-to-image生成，属于图像生成范畴。方法具有创新性，通过闭环目标训练VoT tokenizer，提升了语义对齐和可控生成能力。实验验证了方法的有效性，且不属于小众或水文方向，因此质量较高。

**核心贡献**:  
本文提出 Vision-of-Thought (VoT) 框架，在视觉语言模型（VLM）与扩散 Transformer（DiT）之间引入离散的视觉思维层。该方法不再将 VLM 仅作为文本编码器，而是作为多模态规划器，先生成表示高层视觉计划（如物体和布局）的离散 VoT token，再渲染像素。实验表明 VoT 能提升语义对齐，并为可解释、可控生成提供结构化接口。

**创新点**:  
在 VLM 和 DiT 之间引入离散视觉思维层，用 VoT token 显式桥接高层语言语义与低层视觉信号；将 VLM 重新定位为多模态规划器，并设计专用 VoT tokenizer，使离散 token 既语义可读又保留生成所需视觉信息。

**方法**:  
在 VLM 语义空间中训练专用 VoT tokenizer，采用闭环目标联合优化 VLM 对齐损失、特征重构损失和向量量化损失。VLM 生成代表对象、布局等高层视觉计划的离散 VoT token，随后由 DiT 基于这些 token 渲染像素。

**结果**:  
摘要中报告实验结果表明，VoT 能够提升语义对齐，并为可解释和可控的图像生成提供结构化接口；未给出具体数值指标。

**相关性与影响**:  
该工作为文本到图像生成提供了一种显式、可解释的中间表示范式，有助于统一多模态表示对齐，并推动 VLM 与扩散模型之间更紧密、可控的协同，对多模态生成、可解释性和可控生成研究具有潜在影响。

---

### 3. Better Call CineCrew: Consistent Ultra-Long Narrative-to-Film Generation **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.07720](https://arxiv.org/abs/2609.07720)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07720)
- **作者**: Jiaben Chen, Sixun Dong, Qinhong Zhou et al. (7 authors)
**评估**: 该论文聚焦于长篇叙事到电影的视频生成，属于图像/视频生成领域。其核心贡献是提出结构化编排层和FilmDSL，利用多智能体框架实现镜头级可控性和跨剪辑一致性，并在实验中优于纯文本和仅参考基线。方法有明确创新，实验验证充分，且应用场景（影视生成）具有实际价值，不属于低质量或小众方向。

**核心贡献**:  
该论文针对长篇叙事到影视生成中镜头级可控性与跨片段视觉身份、角色行为一致性的难题，提出了一种介于剧本与现成视频生成模型之间的结构化编排层。该层以面向影视的领域专用语言 FilmDSL 为核心，通过多智能体框架（生成智能体与评论智能体）在规划、生成、批评和修复环节共享结构化规范。实验表明，该方法在电视风格片段生成上相较纯文本和纯参考基线，在可控性与一致性方面均有提升。

**创新点**:  
核心创新在于引入 FilmDSL 作为剧本与视频模型之间的结构化中间表示层，将镜头与摄影机指令、资产与连续性要求、人物角色线索等电影化约束显式化；并以此为基础构建多智能体编排框架，使生成智能体先构建资产包与故事板关键帧以锚定构图，再由评论智能体产出结构化质量信号并触发针对性修复，整个过程无需对基础视频模型进行重训练。

**方法**:  
方法采用多层结构：首先定义 FilmDSL 这一影视导向的领域专用语言，用于显式表达镜头、摄影机、资产、连续性与人物线索等电影化约束；随后构建运行于剧本与现成视频生成器之间的多智能体框架，其中生成智能体负责规划并生成资产包与故事板关键帧，作为片段逐一合成前的构图锚点，评论智能体则生成结构化 QA 信号并在不重训基座模型的前提下触发局部精修。智能体之间通过共享的结构化规范进行协调，从而在剧本信息欠明确的关键电影决策点上提供补充约束。

**结果**:  
论文在电视风格（TV-style）片段上进行了实验，结果显示该方法在可控性与跨片段一致性两方面均优于仅使用文本提示（text-only）和仅使用参考（reference-only）的基线方法。摘要未提供具体量化指标数值。

**相关性与影响**:  
该工作对长视频叙事生成、剧本到视频的自动化影视制作以及多智能体协同生成等方向具有重要价值。其提出的结构化中间层与 FilmDSL 思路，为缓解长时程生成中的一致性与可控性瓶颈提供了可复用的范式，并展示了在不重训练基座模型的情况下通过编排与批评修复提升生成质量的可能性，对后续影视级 AI 生成系统的工程化落地具有潜在影响。

---

### 4. Test-Time Weak-to-Strong Alignment: Transferring Implicit Rewards from Weak to Strong Flow Models **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.05968](https://arxiv.org/abs/2609.05968)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05968)
- **作者**: Xin Xie, Fan Zhang, Dong Gong
**评估**: 论文提出了一种测试时弱到强对齐方法，利用弱模型对提供的隐式奖励信号来引导强模型，无需奖励函数或梯度。在多个图像和视频生成模型（Stable Diffusion 3.5, FLUX, Wan）上验证，实验充分，方法有创新性，属于图像/视频生成领域的高质量工作。

**核心贡献**:  
论文提出 AlignGraft，一种测试时弱到强对齐方法，将弱模型对齐对（源对齐模型与其基座模型）中的隐式奖励信号迁移到更大、冻结且未微调的流模型。该方法在采样时通过加入速度差实现对齐，无需奖励函数、梯度或额外训练，仅用一个标量控制对齐强度。实验表明，该方法可在图像和视频流模型上提升偏好、组合与文本渲染奖励，并保持大模型保真度和较低采样开销。

**创新点**:  
核心创新是改变测试时对齐的监督来源：不再依赖奖励函数、其梯度或单独训练的价值函数，而是让一对弱模型提供逐步、KL 锚定的隐式奖励信号。该信号以采样器自身坐标中的速度差形式表达，可跨模型尺度迁移，并且无需调度，仅用单一标量即可控制甚至外推超过源对齐对的强度。

**方法**:  
将源基座模型与源对齐模型组成源对齐对；在共享噪声核下，二者速度差对应源对齐训练所隐含的奖励信号。对更大、冻结、未微调的目标流模型采样时，在每一步速度中加入该源对齐对的速度差，并用一个标量调节对齐强度。该方法不需要测试时访问奖励或其梯度，也不需要为每个检查点重复对齐训练，仅带来小常数采样开销。

**结果**:  
在 Stable Diffusion 3.5、FLUX 和 Wan 等图像与视频流模型上，AlignGraft 能提升冻结大模型在偏好、组合性和文本渲染奖励上的表现，效果可超过源对齐模型本身，同时保持大模型生成保真度。一次在弱模型上的对齐运行即可产生可复用的监督信号，供整个模型族在测试时使用。

**相关性与影响**:  
该工作为测试时对齐和流匹配生成模型提供了一种低成本、可跨尺度复用的新范式，降低了对齐微调与部署成本，并对 RLHF、偏好优化、个性化生成和模型族知识迁移等相关方向具有潜在影响。

---

### 5. PhysFlow: Physics-Aware Optical Flow for Motion Controllable Video Generation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.08215](https://arxiv.org/abs/2609.08215)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08215)
- **作者**: Cong Wang, Hanxin Zhu, Yonglin Tian et al. (8 authors)
**评估**: 该论文聚焦于视频生成（video generation），提出PhysFlow框架通过物理感知光流提升生成视频的物理合理性，并构建了PhysVideo数据集。核心研究内容属于图像/视频生成范畴，与diffusion/video synthesis方向高度契合，因此归类为Image_Video_Omni_Generation。质量方面，论文提出了明确的创新点（两阶段运动-外观解耦框架、physics-aware attention模块）、构建了大规模物理视频数据集（10K前景物体、50K视频序列），并进行了充分实验验证物理合理性与视觉保真度，技术贡献清晰且具有实际参考价值，非小众垂直领域（如医疗、遥感），故判定为高质量论文。

**核心贡献**:  
本文提出 PhysFlow，一种两阶段物理感知视频生成框架，通过先预测运动光流、再基于运动条件合成表观，提升生成视频的物理合理性与动态可信度。该方法包含物理感知光流生成器 PA-Flow 和光流引导视频生成器 FlowRender，并构建了带运动与材质标注的 PhysVideo 数据集用于显式物理监督训练。实验表明，PhysFlow 在保持高视觉保真度的同时，生成的视频具有更优的物理合理性。

**创新点**:  
将视频生成解耦为运动感知的光流生成与运动条件表观合成两个阶段；提出物理感知注意力模块，分别建模运动属性与材质属性对全局运动和局部形变的影响；构建 PhysVideo 物理视频数据集，为模型训练提供运动与材质属性的显式物理监督。

**方法**:  
PhysFlow 采用两阶段框架：第一阶段 PA-Flow 作为物理感知光流视频生成器，利用物理感知注意力模块生成显式光流视频，表示全局运动与局部形变；第二阶段 FlowRender 以解耦后的运动表示为引导，合成真实纹理与表观，最终生成物理合理的视频。训练数据 PhysVideo 由物理引擎和 3D-GS 渲染生成，包含 10K 前景对象和 50K 真实感视频序列，并带有运动与材质属性标注。

**结果**:  
大量实验表明，与现有方法相比，PhysFlow 生成的视频在物理合理性和视觉保真度上均表现更优；摘要未给出具体定量性能指标。

**相关性与影响**:  
该工作对物理一致性视频生成、运动可控视频生成和物理真实感建模具有重要推动作用，其显式光流解耦与物理监督思路有望应用于仿真、影视内容生成、具身智能和世界模型等方向。

---

### 6. RelightFormer: Feed-forward Generative Transformer for Multiview Object Relighting **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.07414](https://arxiv.org/abs/2609.07414)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07414)
- **作者**: Hejun Wang, Jinxi Li, Junwei Jiang et al. (7 authors)
**评估**: 该论文面向图像重光照任务，属于图像生成与编辑方向，提出基于生成式Transformer的前馈式单/多视角重光照方法，并构建大规模LOD数据集（90K物体、39K光照）。方法包含潜在光照模块、跨注意力注入环境图以及置换不变位置编码，实验显示SOTA视觉质量与零样本泛化能力。分类上最贴近Image_Video_Omni_Generation。论文创新点明确、实验充分、数据集贡献显著，不属于低质量、水文或小众垂直应用方向，因此判定为高质量论文。

**核心贡献**:  
RelightFormer 是一种用于单视图和多视图物体重光照的前馈生成式 Transformer，无需显式估计材质、几何等本征属性，即可直接生成重光照结果。它通过潜在光照模块和置换不变位置编码处理目标环境贴图与无序多视图输入，并构建了大规模 LOD 数据集进行训练。实验表明其在单视图、多视图和新视图重光照任务中均取得最先进的视觉质量与零样本泛化能力。

**创新点**:  
提出完全绕过显式本征属性估计的前馈生成式 Transformer 重光照框架；设计潜在光照模块，通过交叉注意力将目标环境贴图动态注入空间特征；采用置换不变位置编码，无顺序偏差地对称处理无序多视图输入；构建包含 90K 物体和 39K 独特光照的大规模 Laval Objaverse Dataset。

**方法**:  
模型基于视频基础模型改编，输入单视图或多视图图像及目标环境贴图，通过潜在光照模块在空间特征中注入光照信息，利用交叉注意力实现光照条件控制。针对多视图输入，使用置换不变位置编码避免视图顺序带来的序列偏差。训练依赖于新构建的大规模 LOD 数据集，以数据驱动方式学习重光照。

**结果**:  
在单视图、多视图和新视图重光照任务上取得了最先进的视觉质量与照片级真实感重光照效果，并展现出较强的零样本泛化能力。

**相关性与影响**:  
该工作为物体重光照提供了无需复杂逆渲染和显式本征分解的前馈生成范式，降低了多视图重光照对 3D 几何与材质交互建模的依赖。其大规模数据集和 Transformer 架构有望推动生成式重光照、多视图一致性生成以及零样本新视图重光照等方向的发展。

---

### 7. Single Image to Textured 3D Object Generation in Frequency Domain: From Theory to Pipeline **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.07085](https://arxiv.org/abs/2609.07085)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07085)
- **作者**: Qisen Wang, Yifan Zhao, Jia Li
**评估**: 该论文研究单视图图像到带纹理3D对象的生成，属于图像/视频/全模态生成中的3D生成方向。论文从频域角度分析2D与3D扩散先验，提出统一的混合优化框架和Morpheus3D pipeline，用于解决颜色偏差、视角不一致和缺少高频细节等问题，方法具有理论动机和流程创新。实验在公开数据集和自采集复杂纹理数据集上进行，包含定量与定性评估，整体质量较高，不属于低质量、水文或过于小众方向。

**核心贡献**:  
该论文从频率域视角重新审视2D与3D扩散先验的特性，提出一个多扩散先验混合优化的统一理论框架。基于该框架，作者提出Morpheus3D，可从任意单张无位姿野外图像生成带纹理的3D物体。方法利用高通图像提示的2D先验增强3D先验，在提升高频细节的同时抑制视角不一致、低频颜色偏差和高频缺失问题。

**创新点**:  
首次从频率域统一分析并融合2D与3D扩散先验，提出混合优化理论框架；在此基础上设计Morpheus3D，通过高通图像提示的2D先验引导增强3D先验，避免空间域直接互补带来的错误低频2D先验干扰，实现高质量单图到纹理3D物体生成。

**方法**:  
从频率角度分析不同扩散先验的优缺点，构建频率域中多扩散先验混合优化的统一框架。在该框架下，Morpheus3D以3D先验为基础，引入高通图像提示的2D先验作为高频引导，进行混合优化，从而在保持3D一致性的同时恢复高频纹理细节并抑制低频颜色偏差。

**结果**:  
在公开数据集和作者收集的复杂纹理数据集上进行了定量与定性实验，结果表明该方法在生成质量上相比现有方法有显著提升，并能有效缓解视角不一致、低频颜色偏差和高频细节缺失等问题。

**相关性与影响**:  
该工作为单视图3D重建与生成中多先验融合提供了频率域新视角和理论框架，对扩散先验驱动的3D内容生成、纹理细节恢复、颜色一致性与视角一致性研究具有重要参考价值，并推动野外单张无位姿图像生成高质量纹理3D物体的实用化。

---

### 8. Multi-Grid Post-Training for Long-Form Multi-Shot Video Generation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.06373](https://arxiv.org/abs/2609.06373)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06373)
- **作者**: Jiawei Mao, Haoqin Tu, Hardy Chen et al. (11 authors)
**评估**: 该论文提出MovieGrid，一种用于长视频多镜头生成的Multi-Grid Post-Training范式，核心方法是将长视频分解为按时间排序的短片段并排列在空间网格上进行联合建模，属于文本/视频生成与视频合成方向，因此归类为Image_Video_Omni_Generation。质量方面：论文提出明确的技术创新（Multi-Grid训练范式、Noise-Free Random-Grid Training、Grid Embedding、Grid Boundary Loss），并构建了MGLV数据集（54K网格视频），实验充分且与HoloCine、StoryMem等方法进行了定量对比（如镜头内一致性0.9131、镜头间一致性0.5914），token预算下生成镜头数是Temporal Packing的6.05倍，展示了SOTA结果，具有实际参考价值，非小众垂直领域（如医疗/遥感），故判定为高质量论文。

**核心贡献**:  
本文提出 MovieGrid，一种面向长视频多镜头生成的 Multi-Grid Post-Training 范式，将长视频分解为按时间排序的短片段并排列到空间网格上联合建模，从而减少单条时间轴需处理的镜头数并促进跨片段全局信息交换。作者构建了 MGLV 数据集（54K 网格视频与故事提示），并设计 Noise-Free Random-Grid Training、Grid Embedding、角色感知 Story Prompts 与 Grid Boundary Loss。实验表明，在相同 token 预算下 MovieGrid 能生成比 Temporal Packing 多 6.05 倍的镜头，并在多个真实类别基准上取得最优的镜头内与镜头间一致性。

**创新点**:  
主要创新在于提出 Multi-Grid Post-Training 范式：将长视频沿时间轴分解为有序片段，再以空间网格形式联合建模，以缓解单一时间轴难以容纳完整多镜头叙事的问题。配套创新包括 Noise-Free Random-Grid Training、Grid Embedding、角色感知 Story Prompts、Grid Boundary Loss，以及大规模 MGLV 数据集构建流程。

**方法**:  
方法将长视频拆分为较短且时间有序的 chunk，并排列成空间网格进行联合建模，使每个时间轴只需处理更少镜头，同时允许跨 chunk 的全局信息交换。训练时采用 Noise-Free Random-Grid Training，保留随机子集 chunk 作为干净视觉上下文，去噪剩余 chunk。Grid Embedding 编码网格结构，character-aware Story Prompts 关联重复出现的实体，Grid Boundary Loss 稳定网格布局。数据方面，从 1,000 个长视频通过源视频收集、层次化分割、网格视频构建和角色感知故事标注，构建包含 54K 网格视频及故事提示的 MGLV 数据集。

**结果**:  
在相同 token 预算下，MovieGrid 在 1,616 帧视频中生成的镜头数比 Temporal Packing 多 6.05 倍。在覆盖五个真实世界类别的基准上，MovieGrid 取得最先进的镜头内一致性 0.9131（对比 HoloCine 的 0.8086）和镜头间一致性 0.5914（对比 StoryMem 的 0.5384）。此外，MovieGrid 可通过单次或多次生成扩展视频长度，且性能损失较小。

**相关性与影响**:  
该工作对长视频生成、多镜头叙事合成和视频基础模型后训练具有重要意义。它提出以空间网格替代单一时间轴承载长程多镜头内容的思路，为长视频生成中的镜头一致性、角色连贯性和可控叙事提供了新范式，并可能推动视频生成在影视、故事创作和长内容生成等场景中的应用。

---

### 9. PIC: Revisiting INR for Image Coding with Fast Encoding and Sub-Millisecond Decoding **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.09020](https://arxiv.org/abs/2609.09020)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09020)
- **作者**: Xiang Liu, Jinxiang Wang, Bin Chen et al. (8 authors)
**评估**: 标题明确涉及图像编码（Image Coding）和隐式神经表示（INR），属于图像生成/重建/压缩方向，与图像视频生成类别最相关。INR在计算机视觉中用于表示图像，且提及快速编码和亚毫秒解码，属于方法优化，有一定技术贡献。未提供摘要全文，但标题暗示具有编码/解码加速的创新点，质量中上。

**核心贡献**:  


**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 10. CausalChapter: Improving Long-Video Chaptering with Interventional Dependency Modeling **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.08686](https://arxiv.org/abs/2609.08686)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08686)
- **作者**: Xinran Duan, Guozhang Li, Yaoyao Zhong et al. (6 authors)
**评估**: 论文主题为长视频章节切分（chaptering），属于视频理解与生成相关方向，与Image_Video_Omni_Generation类别中的视频处理任务相符。质量评估：标题和摘要未提供，但从题目看涉及因果干预建模来改进长视频章节切分，方法有一定创新性，目标场景具体，可能具有实用价值。因缺少摘要和实验细节，置信度较高但质量评分保守。

**核心贡献**:  


**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---


---

## 🧠 大模型蒸馏与压缩

### 1. Ambient @ EgoLongQA 2026: Distilling Long-Video perception into a Sub-2B Model **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.07154](https://arxiv.org/abs/2609.07154)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07154)
- **作者**: Logesh Kumar Umapathi
**评估**: 论文核心是将长视频问答中的agentic pipeline感知模块蒸馏到2B学生模型，并通过剪枝embedding表满足参数限制，属于知识蒸馏与模型压缩方向。实验在ECCV 2026 Wearable-AI Challenge EgoLongQA的<=2B组取得第一，held-out test达到0.8279，并以1.1%参数达到大流水线89%的精度，结果较充分。虽然偏挑战赛和长视频问答应用，但方法有明确创新和实际参考价值，不属于低质量或水文。

**核心贡献**:  
本文提出了 EgoLongQA 2026 挑战赛 Wearable-AI Challenge 的参赛系统，在 <=2B 参数组别中以 0.8279 的留出测试集成绩获得第一名。该系统是一个单一 2B 视觉语言模型，可在一次贪心前向传播中回答关于十分钟第一人称视频的多选题。其核心是通过蒸馏工具型智能体流水线中的初级感知模块，而非蒸馏整个智能体，将大流水线能力迁移到小模型，并通过嵌入表剪枝使参数量合规。

**创新点**:  
主要创新在于蒸馏工具型智能体流水线中的初级感知模块而非完整智能体，并使用仅保留正确回答的教师轨迹进行训练；同时通过裁剪多语言嵌入表，将 2.2132B 参数模型压缩到 1.9985B，且保留行上的 logits 可证明保持不变。

**方法**:  
系统使用单个 2B 视觉语言模型，对十分钟第一人称视频的多选题进行单次贪心前向推理。训练上采用蒸馏方法，以工具型智能体流水线中的初级感知模块作为教师，并过滤出回答正确的教师轨迹来指导小模型学习。为满足 <=2B 参数限制，将多语言嵌入表从 248,320 行剪枝到 143,469 行，使总参数量降至 1.9985B，并保证保留行上的输出 logits 不变。

**结果**:  
在留出测试集上取得 0.8279，获得 <=2B 参数组别第一名。该系统以约 1.1% 的参数量达到大型智能体流水线 89% 的准确率，并将基础模型在留出问题上的准确率从 27.1% 提升到 81.4%。最终模型参数量为 1.9985B，符合分组限制。

**相关性与影响**:  
该工作对长视频第一人称视频理解、可穿戴 AI 和多模态问答具有重要意义，展示了通过蒸馏智能体子模块而非完整智能体来实现高效小模型部署的潜力。其嵌入表剪枝方法也为在严格参数预算下保持模型输出一致性提供了实用参考。

---

### 2. BEFORE THE FLIP: Measuring Hidden Score Shifts In Quantized Vision Language Models Before The Answer Changes for Visual Question Answering **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.06922](https://arxiv.org/abs/2609.06922)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06922)
- **作者**: Sourajit Saha, Shubhashis Roy Dipta, Shaswati Saha et al. (5 authors)
**评估**: 该论文研究量化视觉语言模型（VLM）在压缩后隐藏的分数变化，属于模型压缩/量化方向，与Distillation类别（涵盖量化、模型压缩、轻量化部署）高度匹配。论文提出了BEFORE THE FLIP方法，系统测量了4-bit与8-bit量化对VQA任务中log概率的影响，并在LLaVA和Qwen上进行了实验，发现压缩会改变底层分数但很少改变最终答案，同时探讨了按问题选择权重组的效果。工作具有明确的方法创新和实验分析，但结论未确立可靠收益，属于分析性贡献，质量中等偏上，非小众或水文。

**核心贡献**:  
论文提出 BEFORE THE FLIP，用于测量量化视觉语言模型在 VQA 答案尚未改变时底层分数（log probabilities）已经发生的隐藏偏移。方法将压缩引起的分数变化与图像 token 替换为固定平均 token 引起的变化进行比较，并逐组提高权重精度以定位额外比特是否有帮助。研究发现 4-bit 压缩会比 8-bit 更明显地把 yes/no 分数差距推向图像 token 替换输出，尽管最终答案很少改变；同时，按问题单独选择权重组并未稳定优于 shuffled controls。

**创新点**:  
提出一种在答案翻转之前检测量化造成隐藏分数偏移的评估框架，通过对比压缩效应与图像 token 替换效应来量化 VLM 内部评分变化，并系统测试逐权重组/逐问题调整精度是否带来可靠收益。

**方法**:  
对量化前后的 VLM 在 VQA 任务上计算 yes/no 等答案的 log probability 分数差；将压缩导致的分数变化与用固定平均图像 token 替换原图像内部表示所导致的分数变化进行比较；随后一次提高一个权重组的精度，识别额外比特在哪些组中有效，并测试为每个问题选择不同权重组是否优于 shuffled controls。

**结果**:  
在 8,277 个图像 token 替换会可测量影响分数的 LLaVA 问题上，4-bit 压缩比 8-bit 更强烈地将 yes/no 分数差距推向替换输出；Qwen 呈现相同趋势但差异较小。然而 9,000 个 LLaVA 答案中仅 265 个在 4-bit 下发生改变。另有 1,024 个校准问题的研究表明，在任何测试存储预算下，逐问题选择权重组均未同时优于两个 shuffled controls。

**相关性与影响**:  
该工作表明量化可能在不改变最终 VQA 答案的情况下改变模型内部置信度和评分结构，提示仅以答案不变评估量化可靠性可能不足。它对视觉语言模型压缩、鲁棒性评估和量化校准策略具有潜在影响，但也指出逐问题动态调整精度目前尚未证明有稳定收益。

---

### 3. Mind the Approximation: Fisher-Weighted SVD Compression for ViTs **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.07155](https://arxiv.org/abs/2609.07155)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07155)
- **作者**: Moritz Thoma, Maximilian Groezinger, Maximilian Forstenhäusler et al. (10 authors)
**评估**: 该论文聚焦于模型压缩，具体是基于SVD（含Fisher加权SVD）的结构化压缩方法，面向Vision Transformers的轻量化部署，属于模型压缩与轻量化部署范畴，因此归入Distillation类别。论文有明确的技术创新：提出FACTS（针对ViT的token-local Fisher近似聚合方法）和快速约束秩搜索（CoRS）用于固定FLOP约束下的逐层秩分配，方法具有原理性和创新性。实验在ViT及混合架构上充分开展，无需微调即可显著提升精度-效率权衡（如Swin-B上较最强SVD基线提升5.8 p.p. Top-1），并提供了开源代码，论证可靠，具有实际参考价值。非小众垂直领域，也非水文，故判定为高质量论文。

**核心贡献**:  
论文研究面向Vision Transformer的SVD压缩，发现提升Fisher近似保真度并不能可靠预测压缩后精度。为此提出FACTS，一种面向Fisher加权SVD压缩ViT的结构化Fisher近似，并引入快速约束秩搜索CoRS，在固定FLOP约束下优化逐层秩分配。大量实验表明，无需微调即可持续改进精度-效率权衡。

**创新点**:  
提出FACTS结构化Fisher近似，强制token局部聚合，同时保留token内激活-梯度依赖；提出快速约束秩搜索CoRS，在固定FLOP预算下优化逐层秩分配。

**方法**:  
基于Fisher加权SVD压缩框架，重新设计适配ViT token结构的Fisher近似，通过token局部聚合和token内激活-梯度依赖建模压缩损失；使用CoRS在FLOP约束下搜索各层秩分配；在ViT和混合架构上验证，无需微调。

**结果**:  
在ViT及混合架构上，FACTS持续改善精度-效率权衡，无需微调；在Swin-B上比最强SVD基线最高提升+5.8个百分点Top-1，结合CoRS搜索可进一步提升。

**相关性与影响**:  
为ViT结构化压缩提供了更可靠的损失感知SVD方法，揭示了Fisher近似保真度与压缩后精度不匹配的问题，对高效Transformer部署和压缩算法设计具有重要参考价值。

---

### 4. CoVeR: Coverage-Based Token Pruning for Multi-View 3D Reasoning in VLMs **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2609.08345](https://arxiv.org/abs/2609.08345)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08345)
- **作者**: Nhat-Tan Bui, Varshini Elangovan, Arun Reddy Anugu et al. (10 authors)
**评估**: 该论文研究视觉token剪枝（visual token pruning），用于降低多视图3D推理中VLM的冗余token开销，属于模型压缩/剪枝/高效推理范畴。虽然其应用场景是3D多视图推理，但核心贡献是一个通用的、training-free的token选择器（CoVeR），可在多个VLM上即插即用，本质上是对大模型推理效率优化的压缩方法，因此归入Distillation（含剪枝、模型压缩、轻量化部署）最为贴切。质量方面：论文清晰指出现有两类token剪枝方法（学习式重要性排序与体素化方法）在多视图3D场景下的固有缺陷，提出基于空间覆盖度、确定性的无训练选择器，方法动机明确且具有创新性；实验在三个3D推理基准上超越SOTA，并在四种VLM上验证泛化性，仅用约8%的token即可保留93.5%的性能，结果充分有力，具有实际参考价值。综合判断为高质量论文。

**核心贡献**:  
CoVeR 提出了一种面向多视角 3D 推理视觉语言模型的基于覆盖度的视觉 token 剪枝方法。它无需训练，仅利用 token 坐标即可确定性选择一组能够覆盖场景各区域的可视 token，在严格预算下减少多视角冗余。实验表明该方法在多个 3D 推理基准和多种 VLM 上优于现有方法，并能以极少 token 保持较高性能。

**创新点**:  
核心创新是提出确定性的、无需训练的覆盖度驱动 token 选择器 CoVeR，仅依赖 token 坐标而不使用学习信号。它同时解决了学习重要性方法偏向显著区域并保留近重复 token 的问题，以及体素化方法无法精确控制预算和因多视角重叠导致覆盖饱和的问题。

**方法**:  
CoVeR 将多视角视觉 token 选择建模为场景空间覆盖问题，通过 token 坐标选择能够集体覆盖整个场景区域的 token 子集，并强制满足每个场景的精确 token 预算。该方法不依赖注意力或编码器特征，可直接作为即插即用模块集成到不同 VLM 中，用于多视角 3D 推理时的视觉 token 剪枝。

**结果**:  
在三个 3D 推理基准和四个 VLM 上，CoVeR 均优于先前 SOTA。仅使用约 8% 的视觉 token 时，它能保留全 token 性能的 93.5%，并在各基准上平均超过 SOTA 3.9 个百分点。

**相关性与影响**:  
该工作揭示了空间覆盖度与多视角 3D 推理性能之间的关联，为 VLM 中视觉 token 冗余问题提供了新的剪枝视角。其无需训练、即插即用且具有精确预算控制的特性，使其对多视角 3D 理解、高效视觉语言模型和实际部署具有重要潜在影响。

---

### 5. CVT-GS: Learning to Simplify 3D Gaussian Splatting with Centroidal Voronoi Tessellation **⭐⭐⭐** (相关度: 65%, 质量: 0.8)

- **arXiv ID**: [2609.08730](https://arxiv.org/abs/2609.08730)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08730)
- **作者**: Bingxian Li, Yilong Li, Jingliang Peng et al. (9 authors)
**评估**: 论文标题表明其目标是简化3D高斯泼溅（3D Gaussian Splatting），通过质心Voronoi图（Centroidal Voronoi Tessellation）减少高斯数量，属于模型压缩/简化范畴，与知识蒸馏、剪枝等概念一致。尽管3DGS不是传统大模型，但该工作实质上是降低场景表示的复杂度以提升效率，最契合Distillation类别。由于缺少摘要，质量评估基于标题显示的技术贡献和创新性，初步认为具有参考价值，但置信度中等。

**核心贡献**:  
由于提供的摘要字段为空，无法获取论文的具体内容，以下内容仅基于标题进行推断：该论文提出 CVT-GS，将质心 Voronoi 剖分（Centroidal Voronoi Tessellation, CVT）引入 3D Gaussian Splatting（3DGS）的表示学习流程，用于对高斯原语进行简化/压缩，在保留渲染质量的同时降低存储与渲染开销。需要说明的是，给出的 arXiv ID（2609.08730）格式上对应 2026 年 9 月，疑似有误，且缺少摘要与实验数据，故除标题所暗示的方向外，其余描述均属推测，未经原文验证。

**创新点**:  
推测的核心创新点是：利用质心 Voronoi 剖分的几何最优划分特性，为 3DGS 的高斯原语提供一种有原理依据的简化（合并/剪枝/重分布）机制，从而替代或改进现有 3DGS 压缩方法中常用的启发式密度控制与剪枝策略。由于缺少摘要与正文，这一判断无法从原文得到证实，仅供参考。

**方法**:  
无法从所给信息中确定。基于标题可推测其技术路线大致为：以 CVT 的能量最小化目标驱动高斯的划分与合并，将一组局部高斯近似为若干 Voronoi 单元对应的代表性高斯，并通过可微渲染进行端到端优化以对齐渲染损失。具体实现细节、损失函数、训练流程与网络结构均未提供，需查阅原文。

**结果**:  
未提供。由于摘要为空，无法获得任何实验数据集、基线对比、渲染质量指标（如 PSNR/SSIM/LPIPS）、高斯数量压缩比、训练与渲染速度或显存占用等性能数据。当前不足以对论文的实验结论做出任何评价。

**相关性与影响**:  
3DGS 的表示冗余与存储开销是该领域公认的瓶颈，简化与压缩是当前研究热点之一。若 CVT-GS 确实建立了 Voronoi 剖分与高斯简化之间的理论联系并能带来实际压缩收益，它可能对三维重建、实时渲染、大规模场景表示及移动端/VR 部署等方向具有参考价值。但在缺少摘要与实验证据的情况下，此判断仍属推测，建议获取论文原文后再做评估。

---


---

## ⚙️ 训练推理基础设施

### 1. ECOKV: Geometry-Aware KV Cache Eviction via Complementary Diversity Metrics **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.06663](https://arxiv.org/abs/2609.06663)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06663)
- **作者**: Chin Ting Hsu, Yu-Syuan Xu, Ling Zou et al. (5 authors)
**评估**: 该论文研究多模态大语言模型中的KV cache eviction，属于推理阶段的显存优化与加速技术，直接对应Training_Inference_Infra类别。论文提出几何感知的复合度量（结合欧氏距离和余弦相似度）和自适应加权策略，并减少观察窗口以优化缓存分配，方法有明确创新。实验表明在多种压缩率下达到SOTA，且能与现有方法无缝集成，分析充分，结论可靠。整体不属小众方向，具有实际参考价值，质量较高。

**核心贡献**:  
论文提出 ECOKV，一种面向多模态大语言模型的几何感知 KV cache 驱逐方法，用于缓解 KV cache 存储带来的内存与计算开销。它通过联合欧氏距离与余弦相似度构建互补的多样性度量，并利用注意力头冗余度自适应平衡多样性与重要性。实验表明 ECOKV 在多种压缩率下达到 SOTA，且可无缝集成现有 KV cache 驱逐方法。

**创新点**:  
严格解构现有基于余弦相似度的多样性度量，指出其归一化丢失幅度信息且因隐藏表示各向异性导致层间相似度普遍偏高；提出几何感知复合度量，从欧氏距离和余弦相似度两个互补视角联合刻画 token 多样性；利用这两种度量估计每个注意力头的冗余水平，在 token 选择时自适应加权多样性与重要性；并证明可大幅缩小用于保留近期 token 的观察窗口，从而将更多 cache 容量分配给信息量高的 token。

**方法**:  
在 KV cache 驱逐框架中，将重要性指标与多样性指标结合来选择保留关键 key-value 对。ECOKV 使用欧氏距离与余弦相似度构成复合多样性度量，以互补方式捕捉 token 多样性；同时基于这两个度量估计每个注意力头的冗余程度，动态调整多样性分数与重要性分数的权重。此外，方法减少常用于保留近期 token 的观察窗口大小，把释放出的 cache 容量用于更有信息量的 token。

**结果**:  
大量实验表明，ECOKV 在各种压缩率下均取得 state-of-the-art 性能，并且可以与现有 KV cache 驱逐方法无缝集成。论文进一步分析了重要性与多样性之间的关系，并考察了不同层和注意力头中的冗余模式。

**相关性与影响**:  
该工作对多模态大语言模型的高效推理与长上下文部署具有重要意义。通过几何感知的多样性建模与自适应重要性-多样性权衡，它为 KV cache 压缩提供了新思路，有助于降低内存和计算开销，并可兼容现有驱逐方法，推动可扩展 MLLM 的实际应用。

---

### 2. CONDUIT: A Unified Residual-Stream Restoration Framework for KV Cache Reuse in Vision-Language Models **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.05821](https://arxiv.org/abs/2609.05821)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05821)
- **作者**: Pengan Chen, Kaisheng Zheng, Liang Hong et al. (13 authors)
**评估**: 该论文聚焦于视觉语言模型（VLM）推理阶段的 KV 缓存复用与加速，属于训练推理基础设施中的推理优化方向。提出的 CONDUIT 方法免训练，统一了单图和多图的缓存刷新策略，通过规范加权注意力和残差流恢复来提升选择质量。实验在三个 VLM 骨干和五个数据集上进行，10% 刷新预算下达到全预填充 97-99.5% 的性能，并在 MMLongBench-Doc 上实现 13.5% FLOPs 和 2.99 倍首 token 时间加速，表明方法创新且实验充分，具有实际部署参考价值。

**核心贡献**:  
Vision-language models (VLMs) often answer new questions about recurring visual content, where reusing the key-value (KV) cache can avoid re-encoding expensive visual prefixes. Exact-prefix reuse, how...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 3. Accelerating Diffusion Transformers with Gaussian Process Rectified Feature Cache **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.05981](https://arxiv.org/abs/2609.05981)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05981)
- **作者**: Zhirong Shen, Rui Huang, Chang Zou et al. (13 authors)
**评估**: 该论文聚焦于加速Diffusion Transformers的推理过程，通过特征缓存校正框架（GP-Refiner）和不确定性自适应计算策略来减少计算负载，属于推理加速的基础设施优化，因此归类为Training_Inference_Infra。质量评估：论文基于统计观察（残差呈零均值高斯分布）提出了一种新颖的即插即用校正框架，方法有理论支撑，实验显示在多种模型上显著提升（计算量减少19.3%，PSNR提升0.9dB，LPIPS从0.46降至0.29），并提供了开源代码，具有较高的技术贡献和实际参考价值。

**核心贡献**:  
论文针对扩散Transformer特征缓存中预测偏差随步数累积的问题，提出GP-Refiner：利用全计算步特征作为参考轨迹的噪声观测，并基于残差局部零均值高斯分布的统计观察，用高斯过程回归进行即插即用校正。该方法结合不确定性自适应计算策略，在需要时触发全计算校准，从而提升缓存加速的精度与效率。

**创新点**:  
发现缓存全计算步与参考全计算轨迹之间的残差局部服从零均值高斯分布，从而将全计算特征视为带噪观测，解决在线回归校正中标签不可得的问题；提出即插即用GP-Refiner，利用GPR校正并由后验方差驱动不确定性自适应全计算校准。

**方法**:  
通过统计观察建模缓存特征与参考特征残差为局部零均值高斯噪声；使用高斯过程回归对预测缓存特征进行在线校正；依据GPR后验方差实时监测不确定性，在必要时触发全计算校准；可与其他预测式特征缓存方法结合。

**结果**:  
与多种SOTA方法结合取得显著提升；与TaylorSeer集成后计算量降低19.3%，PSNR提升0.9 dB，LPIPS从0.46降至0.29。

**相关性与影响**:  
为扩散Transformer实时生成提供通用、即插即用的加速校正框架，缓解特征缓存误差累积，推动高效生成模型在实时场景中的部署，并对不确定性驱动的动态计算策略有借鉴意义。

---

### 4. Conditioned Initialization for Attention **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.07086](https://arxiv.org/abs/2609.07086)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07086)
- **作者**: Hemanth Saratchandran, Simon Lucey
**评估**: 该论文聚焦于 Transformer 注意力层 Q/K/V 权重初始化，通过改善谱性质与降低注意力 Jacobian 条件数来优化训练动态，属于训练优化/训练基础设施方向。虽然摘要提到 teacher model 权重迁移，但核心贡献并非蒸馏或压缩，而是初始化方案对训练稳定性和收敛性的影响。论文有理论分析和跨任务实证验证，方法简洁且易于集成，具有较高参考价值，不属于小众垂直应用或水文。

**核心贡献**:  
本文提出 Conditioned Initialization，一种针对 Transformer 注意力层 Q/K/V 权重的新型初始化方案，旨在通过改善注意力层谱属性来减少初始化带来的优化偏差。理论分析表明该方法可降低注意力 Jacobian 的条件数，从而提升优化稳定性；实验显示其能加速收敛并在多种应用中提升泛化能力。

**创新点**:  
将注意力权重初始化视为影响训练动力学和优化偏差的关键因素，提出以改善注意力层谱条件数为目标的 Conditioned Initialization。与随机初始化、模仿收敛模型的 mimetic initialization 以及从教师模型迁移权重的 weight selection 不同，该方法简单通用，可无缝集成到多种 Transformer 架构中。

**方法**:  
对注意力层的 query、key、value 权重进行条件化初始化，使注意力层具有更优的谱性质。理论上分析初始化与注意力 Jacobian 条件数之间的关系，证明 Conditioned Initialization 可潜在地降低条件数并带来更稳定的优化；随后在多种 Transformer 应用中进行实证验证。

**结果**:  
理论结果表明，Conditioned Initialization 可潜在地降低注意力 Jacobian 的条件数，从而改善优化稳定性。实验结果表明，该方法在不同应用上能够加速收敛并提升泛化性能。摘要未给出具体数据集、基线或数值指标。

**相关性与影响**:  
该工作强调初始化与谱条件化是提升 Transformer 性能中关键但尚未被充分探索的方向，为注意力层初始化提供了新的理论视角和实用方案。该方法易于应用且兼容多种 Transformer 架构，对视觉、语言等依赖注意力机制的领域具有潜在影响，并可能推动更稳定、更高效的 Transformer 训练研究。

---

### 5. Stable-MM-R1: Anchoring Multimodal Reasoning Dynamics via Entropy-Guided Stratification **⭐⭐⭐⭐** (相关度: 85%, 质量: 0.8)

- **arXiv ID**: [2609.07148](https://arxiv.org/abs/2609.07148)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07148)
- **作者**: Yimeng Ye, Shuang Chen, Wenxuan Huang et al. (11 authors)
**评估**: 该论文核心关注强化学习训练过程中的不稳定性、熵崩塌和 rollout 采样效率问题，并提出 PAQM 与 HSR 等数据/批次构造机制来稳定 RL 微调，属于训练基础设施与训练效率优化方向，而非图像/视频生成、蒸馏或 Agent/World Model。方法具有一定创新性，针对 RL 训练中低质量梯度信号和熵崩塌等实际问题，且声称在复杂推理任务上优于强基线。但摘要未提供充分实验细节与消融，质量评估为中等偏上。

**核心贡献**:  
本文提出 Stable-MM-R1，一种以数据为中心的强化学习训练框架，用于缓解多模态/大模型推理训练中的不稳定性和熵坍缩问题。通过潜在感知查询挖掘（PAQM）和混合分层回放（HSR），方法动态筛选高潜力样本并重构优化批次，从而稳定 RL 微调。实验表明该方法在复杂推理任务上优于强基线，并提升了有限算力下的学习信号利用率。

**创新点**:  
提出 PAQM 动态筛选处于“蒸馏区”的高潜力查询，并设计 HSR 基于路径熵与结果奖励对 rollout 进行分层，构造高对比优化组；同时复用当前策略的“稳定性锚点”和“困难负样本”，在每步优化后清空缓冲区，以缓解熵坍缩并提升训练稳定性。

**方法**:  
核心方法包括：1）Potential-Aware Query Mining（PAQM），动态过滤数据，聚焦于有能力激发潜力的样本；2）Hybrid Stratified Replay（HSR），根据 Path Entropy（rollout 级置信度代理）和结果奖励对 rollout 分层，重组批次；3）在每步优化中复用当前策略的 Stability Anchors 与 Hard Negatives 构造高对比优化组，并在下一步前清空缓冲区。

**结果**:  
摘要指出该方法在复杂推理任务上优于强基线，能够缓解熵坍缩，并在有限计算预算下提高学习信号利用率；但未提供具体数值指标。

**相关性与影响**:  
该工作针对 RL 微调大模型推理时常见的训练不稳定和熵坍缩问题，提供了一种原则性的数据筛选与批次重构方案，对稳定、高效的强化学习微调及相关多模态推理研究具有潜在推动意义。

---

### 6. RoLA: Rotary-Positioned Low-Rank Linear Attention for Efficient Diffusion Transformers **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.06712](https://arxiv.org/abs/2609.06712)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06712)
- **作者**: Zekun Zhang, Yixiang Cai, Yuxi Liu et al. (12 authors)
**评估**: 该论文核心贡献在于提升视频 Diffusion Transformer 的推理效率：提出 RoLA（Rotary-Positioned Low-Rank Linear Attention）线性注意力分支，解决在 3D RoPE 与非线性低秩特征图不兼容导致的结构性问题，从而将全局注意力分支降为线性复杂度，并在 90% 稀疏度下保持生成质量、在 Wan2.1-14B 上实现 2.63× 端到端推理加速。虽然应用场景为视频生成，但论文的创新本质是高效的注意力/推理加速机制，属于推理优化与部署基础设施范畴，因此归类为 Training_Inference_Infra 而非 Image_Video_Omni_Generation。质量上，论文针对 RoPE 与低秩线性注意力不交换这一具体结构性难题提出设计（将 RoPE 置于非线性低秩映射之外、复用预训练 rotary schedule 截断子集），具有明确方法创新且无需额外位置参数；实验在开源视频 DiT 上给出稀疏度与端到端加速的量化结果，支撑较充分，作者方向聚焦于高效生成模型推理，具备参考价值。属于高质量工作。

**核心贡献**:  
该论文提出 RoLA，一种面向视频 Diffusion Transformers 的旋转位置低秩线性注意力分支，用于解决 RoPE 与低秩非线性特征映射不兼容的问题。RoLA 在非线性低秩特征映射之外应用 RoPE，并复用预训练旋转调度中的截断子集，从而在保持真实跨 token 全局聚合的同时获得线性复杂度和相对位置行为。实验表明，在 90% 稀疏度下生成质量仍具竞争力，并在 Wan2.1-14B 上实现 2.63 倍端到端推理加速。

**创新点**:  
主要创新在于设计了与 3D RoPE 兼容的低秩线性注意力全局分支：将 RoPE 放在非线性低秩特征映射之外，并复用与低秩瓶颈匹配的预训练旋转调度截断子集。该方法无需额外位置参数，避免了用坐标条件代理或可学习绝对位置模块近似相对位置衰减，同时保留可复用的线性摘要和真实跨 token 全局聚合。

**方法**:  
方法采用稀疏-低秩混合注意力：局部稀疏分支保持固定稀疏度，全局分支使用低秩线性注意力。RoLA 全局分支通过非线性低秩特征映射压缩键值信息，并在其外部施加 RoPE，使旋转与非线性不再冲突；同时截断并复用预训练 RoPE 调度以匹配低秩瓶颈。最终模块实现线性时间复杂度的全局注意力，并具备相对位置行为。

**结果**:  
在开源视频 DiT 上，RoLA 在 90% 稀疏度下生成质量仍具竞争力；在 Wan2.1-14B 上，720p、81 帧、NVIDIA H100 GPU 实测获得 2.63 倍端到端推理加速。

**相关性与影响**:  
该工作对高效视频生成与 Diffusion Transformers 推理优化具有重要意义，缓解了密集时空自注意力的二次复杂度瓶颈，并为 RoPE 与线性/低秩注意力结合提供了新思路。其无需额外位置参数且兼容预训练旋转调度的设计，有望推动长序列视频生成模型的高效部署与进一步研究。

---

### 7. To Adapt or Not to Adapt? Selective Adaptation for Vision-Language Models **⭐⭐⭐** (相关度: 74%, 质量: 0.8)

- **arXiv ID**: [2609.08367](https://arxiv.org/abs/2609.08367)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08367)
- **作者**: Siru Jiang, Yuwei Liang, Jian Liang et al. (5 authors)
**评估**: 该论文研究 Vision-Language Models 的 test-time adaptation（TTA），关注推理阶段是否对测试样本进行适应，属于推理时模型适应与推理效率优化，因此归为 Training_Inference_Infra。论文提出“选择性适应”新问题，并给出 Cross-Augmentation Similarity 基线，能跳过近 85% 的适应过程且保持甚至提升准确率，具有实际参考价值，代码开源。虽摘要未展示大规模实验细节，但方向热门、问题明确，不属于低质量或小众垂直领域。

**核心贡献**:  
本文研究视觉-语言模型在测试时适应（TTA）中的选择性适应问题，通过逐样本分析发现现有TTA方法存在适应无效或有害的失败模式。作者提出跨增强相似度（CAS）基线，仅在增强视图预测相似度较低时执行适应，从而跳过大量无效或有害的适应过程。

**创新点**:  
首次提出“选择性适应”问题，即决定给定测试样本是否应进行适应或跳过；并提出简单有效的基线方法CAS，通过增强视图间预测相似度判断是否执行适应。

**方法**:  
对模型适应前后的逐样本预测进行分析，识别出适应可忽略和适应有害两种失败模式。CAS方法对同一测试样本生成多个增强视图，若这些视图的预测相似度较低则执行适应，否则跳过适应。

**结果**:  
CAS在跳过近85%的适应过程的情况下，不仅保持整体准确率，在某些情况下还能提升整体准确率。

**相关性与影响**:  
为视觉-语言模型的测试时适应提供了新方向，有望提升TTA的可靠性、效率和安全性，并启发后续研究探索更优的选择性适应策略。

---

### 8. SupGRPO: Enhancing GRPO with Matching-based Online SFT for Text Spotting **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.07081](https://arxiv.org/abs/2609.07081)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07081)
- **作者**: Xudong Xie, Yuzhe Li, Jing Shi et al. (6 authors)
**评估**: 该论文的核心贡献是一种大模型微调训练方法——SupGRPO，它创新性地将 SFT 与 GRPO 强化学习联合优化，并设计了基于匹配的在线 SFT 和专门的奖励函数，以缓解 GRPO 的奖励稀疏问题和 SFT 的实例顺序依赖问题。这本质上属于训练策略/微调基础设施范畴，而非生成、蒸馏或智能体方向，故归为 Training_Inference_Infra。质量方面，论文提出了明确的技术创新（联合训练策略与匹配机制），实验覆盖了识别与检测任务并构建了挑战性数据集 ATS，结果显示双向提升，方法有一定参考价值。不足之处在于应用场景较为细分（text spotting / artistic text spotting），属于特定视觉任务上的微调改进，通用性与受众范围有限，因此质量评分中等偏上，未达到广泛高影响力级别。

**核心贡献**:  
论文提出 SupGRPO，一种面向文本检测与识别（text spotting）的联合微调策略，将监督微调（SFT）与基于 Group Relative Policy Optimisation（GRPO）的强化学习结合，以同时提升多模态大模型的识别与定位能力。作者发现 SFT 更利于检测、GRPO 更利于识别，因此通过匹配式在线 SFT 仅优化坐标 token 来互补二者。论文还构建了艺术文本检测数据集 ATS，实验表明 SupGRPO 在识别和检测上均取得更优性能。

**创新点**:  
提出 SupGRPO 联合训练策略，将 SFT 与 GRPO 同时用于模型优化；设计专门奖励函数，并提出仅作用于坐标 token 的 matching-based online SFT，从而缓解 GRPO 的奖励稀疏问题，同时避免 SFT 的实例顺序依赖问题；此外构建了面向困难场景的艺术文本检测数据集 ATS。

**方法**:  
基于多模态大语言模型探索文本 spotter 的微调方法，对比 SFT 与 GRPO 在识别和检测任务上的不同优势。SupGRPO 采用联合训练，同时使用 SFT 和 GRPO 优化模型，并通过匹配式在线 SFT 仅对坐标 token 进行监督，配合定制奖励函数提升定位与识别能力。

**结果**:  
实验表明 SupGRPO 能够同时提升文本识别和文本检测性能，并在具有挑战性的场景中取得优于对比方法的性能；作者还整理了艺术文本检测数据集 ATS 用于评估困难案例。摘要未给出具体数值指标。

**相关性与影响**:  
该工作对文本检测与识别、多模态大模型微调、强化学习与监督学习联合训练等方向具有参考价值，尤其为复杂或艺术文本场景下的定位与识别提供了新思路，并有望推动 text spotting 在困难实际场景中的应用。

---

### 9. VidaForge: Open Research Infrastructure for Video Pretraining Data Recipes **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.06652](https://arxiv.org/abs/2609.06652)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06652)
- **作者**: Yan Ma, Jiadi Su, Zhulin Hu et al. (7 authors)
**评估**: 该论文提出 VidaForge，一个面向视频预训练数据的开放式研究基础设施，将视频数据配方表示为从原始视频到训练数据集的可执行五阶段工作流，并系统比较不同覆盖度与质量的数据配方对 Wan 2.1（生成）和 V-JEPA 2.1（理解）从头预训练的影响。论文的核心贡献是预训练数据管线的可复现基础设施与数据集（VidaForge-3M，314万片段、6475小时），而非模型生成方法本身，因此最贴合 Training_Inference_Infra（预训练/数据管线基础设施）。虽然涉及视频生成模型 Wan 2.1，但重点不在生成算法创新，不归入 Image_Video_Omni_Generation。论文具有明确的工程价值、可复用的开源基础设施和较大规模的数据集发布，实验覆盖两类学习目标，具备一定的实际参考价值；但方法层面创新有限（偏数据配方工程与实证研究），故质量评分中等偏上。

**核心贡献**:  
VidaForge 是一个面向视频预训练数据配方的开放研究基础设施，将数据配方表示为从原始视频到训练数据集的可执行五阶段工作流，使研究者能够系统比较不同数据决策对模型预训练的影响。论文通过对比不同覆盖率和质量的数据配方，在 Wan 2.1 与 V-JEPA 2.1 的早期从头预训练中验证了该基础设施的研究流程，并发布了包含 314 万场景级片段、6475 小时的 VidaForge-3M 数据集。

**创新点**:  
提出开放、可执行、可追溯的视频数据配方研究工作流，使视频预训练数据管道从封闭黑箱变为可检查、可复用、可干预的基础设施；支持通过改变工作流中的决策构建替代数据集，同时保留每个样本的生产来源，从而系统连接数据配方选择与下游模型性能。

**方法**:  
将视频数据配方建模为从原始视频到训练数据集的五阶段可执行工作流，并允许在任意阶段改变决策以构造不同数据集；在此基础上比较不同覆盖率和质量的数据配方，用于 Wan 2.1 和 V-JEPA 2.1 的早期从头预训练；同时发布 VidaForge-3M，包含 314 万场景级片段、6475 小时视频以及细粒度标注和筛选信号。

**结果**:  
在 Wan 2.1 和 V-JEPA 2.1 两种学习目标下，覆盖率更广的数据配方取得最高的下游基准分数，而基于损失的评估则偏好不同的数据配方。研究展示了 VidaForge 能够将数据配方选择与下游模型性能联系起来，并公开提供 VidaForge-3M 数据集用于视频数据配方研究。

**相关性与影响**:  
该工作有助于推动以数据为中心的视觉预训练研究，降低理解和复现视频预训练数据管道的门槛，提升数据配方实验的透明性、可复现性和可复用性；其发布的数据集和研究范式可为视频基础模型的数据筛选、质量评估和下游性能分析提供重要基础设施与参考。

---

### 10. Bigger Text Encoders Can Hurt CLIP Zero-Shot Performance **⭐⭐⭐** (相关度: 72%, 质量: 0.8)

- **arXiv ID**: [2609.05730](https://arxiv.org/abs/2609.05730)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05730)
- **作者**: Samir Char, Carles Domingo-Enrich, Randall Balestriero
**评估**: 该论文研究CLIP模型的编码器容量分配问题，探讨视觉/文本编码器规模如何影响零样本性能，并提出更高效的训练配置（减少55%参数）和模态特定的权重衰减方法。核心内容围绕模型架构缩放规律、训练资源配置和效率优化，属于训练方法与基础设施范畴，因此归为Training_Inference_Infra。文章有明确的技术发现（过度放大的文本编码器导致过拟合）、几何分析解释（embedding均匀性与跨模态对齐的权衡）、以及可操作的训练改进方案（模态特定权重衰减），实验设计较系统，结论对CLIP的可靠高效扩展有实际参考价值。虽然不是纯基础设施（分布式/显存优化），但本质上关注训练效率与缩放策略。质量中等偏上，属于有价值的方法分析类工作。

**核心贡献**:  
本文系统研究CLIP中视觉编码器与文本编码器容量分配对零样本性能的影响，发现对多数视觉编码器而言，文本编码器过大会导致零样本性能下降，即使总参数量增加。作者据此设计高效配置，在参数量最多减少55%的情况下达到标准ViT-B/16的零样本性能。

**创新点**:  
挑战将CLIP总模型规模视为单一变量的传统做法，揭示编码器容量分配中存在最优文本编码器规模；发现性能下降源于文本编码器过拟合，并提出模态特定权重衰减来缓解并提升性能；从几何角度解释嵌入均匀性与跨模态对齐之间的权衡。

**方法**:  
训练不同视觉编码器与文本编码器尺寸组合的CLIP模型，比较零样本性能；分析过拟合现象并使用模态特定权重衰减进行干预；开展嵌入几何分析，考察均匀性与跨模态对齐指标及其对零样本性能的预测能力。

**结果**:  
对多数视觉编码器存在最优文本编码器尺寸，超过后零样本性能随总参数量增加反而下降；高效配置以最多减少55%参数匹配ViT-B/16零样本性能；模态特定权重衰减可在所有退化配置上恢复并提升性能；文本编码器增大会提升嵌入均匀性但损害跨模态对齐，且这些指标可预测零样本性能。

**相关性与影响**:  
为CLIP的缩放规律、架构设计和训练策略提供新视角，表明需关注编码器容量分配而非仅总规模；对高效CLIP训练、多模态表示学习及可靠扩展具有指导意义。

---


---

## 🧠 Agent 相关内容

### 1. Selective Knowledge Control for Continual GUI Agent Learning over Application Streams **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.7)

- **arXiv ID**: [2609.06530](https://arxiv.org/abs/2609.06530)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06530)
- **作者**: Zirui Shang, Xin Shu, Yang Liu et al. (6 authors)
**评估**: 该论文研究持续学习场景下的GUI智能体，核心问题是应用流中的知识保留与适应，属于Agent方向。方法提出基于激活条件的选择性知识控制，通过神经元级梯度裁剪与正交投影缓解灾难性遗忘，具有一定技术创新性。实验在多应用序列基准上验证，但摘要未提供具体基线、指标和消融细节，因此质量评估为中等偏上。

**核心贡献**:  
本文针对GUI智能体在应用流（application streams）场景下的持续学习问题，提出了一种名为“激活条件化选择性知识控制”（activation-conditioned selective knowledge control）的轻量级方法。该方法通过神经元级别的梯度操作实现选择性知识保留：保护历史高激活的MLP神经元，并对新应用训练时的梯度进行实时“手术”，从而在适应新应用的同时避免对旧知识的灾难性遗忘。作者在多应用顺序基准上验证了该方法能有效缓解遗忘并保持对新应用的稳健适应能力。

**创新点**:  
核心创新在于将“新应用与旧应用之间既共享又特异的知识结构”显式建模为神经元级别的两类保护对象，并在前向激活条件下实时执行差异化梯度处理：对承载特异知识的未激活神经元直接截断梯度以防止干扰，对承载共享知识的已激活神经元进行梯度正交投影以在保持稳定性的同时允许适应。此外，方法维护一个紧凑的历史知识状态，并在每个应用阶段结束后将新识别的关键神经元合并进该状态，实现知识的持续累积与复用。

**方法**:  
方法基于MLP神经元的激活状态进行知识控制。首先维护一个紧凑的历史知识状态，记录此前阶段中被判定为关键（高激活、承载旧知识）的神经元。当新应用到来时，依据前向传播的激活情况对受保护神经元分类：1）未激活神经元被视为携带应用特异知识，其梯度被截断（truncated），避免新任务学习对其造成干扰；2）已激活神经元被视为携带跨应用共享知识，其梯度被正交投影（orthogonally projected）到与历史知识子空间正交的方向，从而在保持旧知识稳定性的同时允许必要适配。每个应用阶段结束后，新识别的关键神经元被合并进历史状态，供后续阶段继续保护。

**结果**:  
论文在多应用顺序（multi-app sequential）基准上进行了实证评估，结果表明该方法能够有效缓解对先前应用的灾难性遗忘，同时对新增应用保持稳健的适应性能。摘要中未给出具体的量化指标数值。

**相关性与影响**:  
该工作对GUI智能体的持续学习与跨应用泛化具有重要意义：随着应用生态不断演化，智能体必须在有限资源下持续吸收新应用知识而不遗忘旧技能，而“共享知识与特异知识纠缠”正是该场景的核心难点。所提出的神经元级、激活条件化的梯度操作方案轻量且与模型架构解耦，为持续学习中的稳定性—可塑性权衡提供了一种新思路，也可为其他需要顺序适配的智能体或大模型微调场景提供借鉴。

---

### 2. LLM-Aided Design for Manufacturing: A Multi-Agent System for Intent-Preserving Redesign of CAD for Improved Manufacturability **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.7)

- **arXiv ID**: [2609.05559](https://arxiv.org/abs/2609.05559)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05559)
- **作者**: Kojo Welbeck, Xiangyu Shi, Zahra Sadeghi et al. (5 authors)
**评估**: 该论文提出一个基于多模态LLM的多智能体系统，用于CAD零件的可制造性重设计，核心是DFM Reviewer与CAD Modifier两个智能体子系统，并通过验证循环逐步生成和检查编辑。这最符合Agent类别，即多智能体协作与大模型驱动的自主任务执行。质量方面，论文有明确的方法设计、46个零件的基准评测、与单智能体链式思考方法的对比以及消融实验，显示一定技术贡献和实验支撑；但论文自述为preliminary report，完整评估（可制造性增益、意图保持度量）仍在进行中，因此质量评分为中等偏上而非高置信度。不属于低质量水文或极小众方向。

**核心贡献**:  
本文提出一种自主且保持设计意图的CAD零件面向制造的设计（DFM）重设计方法，能够在给定工程师CAD模型后返回更易制造但不丢失设计意图的变体。方法通过由预训练多模态LLM驱动的两个耦合智能体子系统，将重设计生成为一系列逐一验证的设计转换，而非不可靠的一次性生成。这是一份初步报告，完整重设计循环的评估仍在进行中。

**创新点**:  
核心创新是耦合的DFM Reviewer与CAD Modifier多智能体系统：Reviewer每次提出一个保持意图的可制造性改进建议，Modifier将其执行为CadQuery程序编辑，并通过编译、多视角渲染和视觉检查形成验证闭环，接受或放弃每次编辑。该方法无需微调，通过累积经过验证的编辑来处理超出一次性生成器可靠范围的复杂零件，并在每一步保持原始设计意图。

**方法**:  
给定当前CAD设计，DFM Reviewer检查设计并一次提出一个保持意图的可制造性改进方案；CAD Modifier将该方案转化为对零件CadQuery程序的编辑。每次候选编辑都会经过验证闭环：编译程序、多视角渲染，并与预期修改进行视觉对比，若不满足则重新生成或重新指令，直到编辑被接受或放弃。系统迭代执行评审与已验证修改，将多个转换逐步复合。消融实验分析了视觉审查循环以及在每次编辑前为设计状态生成描述的作用。

**结果**:  
在一个包含46个零件的基准上，以倒角距离（chamfer distance）相对于参考几何进行评分，CAD Modifier平均比使用相同工具的思维链单智能体更准确地复现目标零件。消融实验分离了视觉审查循环和编辑前设计状态描述各自的贡献。一个由32个链式转换构建的离心泵壳体展示了复合验证编辑可达到的复杂度。完整评审-重设计循环的评估，包括可制造性增益和意图保持的操作性度量，仍在进行中。

**相关性与影响**:  
该工作对LLM驱动的CAD生成、面向制造的设计和工程自动化具有重要意义。它展示了多智能体验证与迭代编辑在复杂CAD任务中比单次生成更可靠，并强调在自动化重设计中保持设计意图。潜在影响包括更实用的可制造性优化工具、LLM智能体在工业设计流程中的集成，以及为CAD/CAE中的可靠生成与编辑提供新范式。

---

### 3. One MLLM, One Call: Efficient Zero-Shot Vision-and-Language Navigation via Spatial-Aware Waypoints **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.06476](https://arxiv.org/abs/2609.06476)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06476)
- **作者**: Shiqi Pan, Qi Zheng, Hanqin Sun et al. (6 authors)
**评估**: 该论文研究的是连续环境下的视觉-语言导航（VLN-CE），本质上是一个具身智能体（embodied agent）任务，智能体需根据自然语言指令在未知环境中导航，因此最符合 Agent 类别。核心贡献是提出 O2C-Nav 框架，通过无训练的结构化 waypoint 生成器和将候选 waypoint 投影到 RGB 图像作为视觉标记的抽象表示，使 MLLM 每步只需调用一次即可完成决策，显著降低推理延迟，并结合 FMM 规划器生成无碰撞路径，具有较强的效率优化与具身决策创新。在 R2R-CE 和 RxR-CE 标准基准上超越现有零样本 SOTA 方法，并提供开源代码，实验较为充分，具身导航领域（非小众垂直应用）具备实际参考价值，作者有相关工作背景。综合评为较高质量论文，但相比真正突破性的工作，其方法仍属工程与范式改进性质，故质量分适中。

**核心贡献**:  
本文提出 O2C-Nav，一种高效的零样本连续环境视觉语言导航框架，每个决策步骤仅调用一次多模态大模型（MLLM）。该方法通过免训练结构化路点生成器和空间感知的抽象视觉表示，在降低推理延迟与计算开销的同时提升导航性能。在 R2R-CE 和 RxR-CE 基准上，O2C-Nav 优于当前最先进的零样本方法，展示了实时机器人部署潜力。

**创新点**:  
核心创新在于“一次 MLLM 调用”的零样本导航范式：设计免训练的结构化路点生成器，并将稀疏、历史感知的候选路点作为视觉标记直接投影到 RGB 图像上，为 MLLM 提供具体空间感知与显式记忆；同时支持 MLLM 选择路点或生成回退目标边界框，再由 FMM 规划器转化为无碰撞可执行路径。

**方法**:  
O2C-Nav 每个决策步仅查询一次 MLLM。首先通过免训练结构化路点生成器产生候选路点，并利用历史信息构建稀疏候选表示；随后将候选路点投影到 RGB 图像上作为视觉标记，使 MLLM 能在图像空间中直接选择路点或输出回退目标边界框；最后使用 Fast Marching Method（FMM）低层规划器将选定目标转换为无碰撞路径，从而显著降低视觉处理负担和推理开销。

**结果**:  
在 R2R-CE 和 RxR-CE 基准上的大量评估表明，O2C-Nav 优于当前最先进的零样本 VLN-CE 方法，并具有显著降低的推理延迟与计算开销，适合实时机器人部署。

**相关性与影响**:  
该工作为连续环境视觉语言导航提供了一种高效、无需额外训练的零样本解决方案，缓解了现有方法依赖预训练路点预测器或每步多次查询大模型的问题。其单次 MLLM 调用与空间感知路点表示有望推动 VLN 在真实机器人系统中的实时部署，并对多模态大模型与具身导航的融合研究具有重要参考价值。

---

### 4. From Gaze to Meaning: A Training-Free AI Agent for Unified Grounding and Explanation **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.06208](https://arxiv.org/abs/2609.06208)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06208)
- **作者**: Shayan Nasiriboukani, Sara Atito, Mohammad Nezamipour et al. (4 authors)
**评估**: 该论文提出了一种无需训练的Gaze Target Agent（GTA），利用预训练视觉语言模型、视觉引导提示和基于记忆的检索策略，实现注视目标预测、注意力定位和对象识别等任务的统一推理与解释。核心贡献在于将AI Agent范式应用于注视引导的视觉推理，并在GazeFollow和GazeHOI基准上取得SOTA，同时保持无需额外训练和词汇约束的灵活性。分类为Agent最为相关。质量方面，方法有明确创新点（training-free agent + memory retrieval），实验包含定量指标和定性分析，但整体属于较专门的应用方向，实验规模和创新深度有限，因此质量评分为0.75，属于高质量但非顶尖工作。

**核心贡献**:  
本文提出首个无需训练的注视目标智能体（GTA），用于统一处理注视目标预测、注意力定位和物体识别等注视引导推理任务。该方法利用预训练视觉语言模型，结合视觉引导提示和面向高不确定性样本的基于记忆的检索策略，无需额外训练即可提升性能。在GazeFollow和GazeHOI基准上取得最先进结果，并能给出细粒度语义解释。

**创新点**:  
提出首个无需训练的Gaze Target Agent（GTA），实现注视引导的统一推理；通过视觉引导提示增强预训练视觉语言模型，并引入基于记忆的检索策略处理高不确定性样本，从而在不进行额外训练的情况下提升注视目标预测与解释能力。

**方法**:  
基于预训练视觉语言模型构建无需训练的智能体框架；使用视觉引导提示（visually guided prompts）引导模型关注注视相关线索；对高不确定性样本采用基于记忆的检索策略进行增强；最终统一支持注视目标预测、注意力定位和物体识别等任务。

**结果**:  
在GazeFollow和GazeHOI基准上达到最先进性能；定性结果显示该智能体能提供详细语义预测，在真实标签错误时仍预测正确目标，并且不受固定词汇表约束，具有较强灵活性。

**相关性与影响**:  
该工作表明无需大规模监督训练即可实现可解释的注视引导场景理解，为注视目标预测、人机交互、注意力分析和视觉语言模型推理提供了新思路，并可能推动无需训练智能体在视觉理解任务中的应用。

---

### 5. Beyond the Verdict: Evidence-Aligned Evaluation of Visual Prompt-Injection Guardrails **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.05535](https://arxiv.org/abs/2609.05535)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05535)
- **作者**: Suyoung Lee, Myungsub Choi
**评估**: 该论文研究视觉语言模型（VLM）在网页代理安全护栏中的评估问题，属于AI智能体（Agent）的安全与鲁棒性方向。论文提出了新的基准测试Mind2Web-Injection和评估指标EAD，并设计两种免训练干预方法，实验充分，对代理安全领域有实际参考价值，非小众或水文。

**核心贡献**:  
Verdict-only evaluation does not reveal whether a vision-language model (VLM) used the visual evidence that should support its decision. We study this problem in web-agent guardrails, where a VLM judg...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 6. Eliciting Self-Verification in Multimodal Reasoning Agents with Reinforcement Learning **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2609.08025](https://arxiv.org/abs/2609.08025)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08025)
- **作者**: Vishwas Sathish, Viresh Ranjan, Xinliang Zhu et al. (5 authors)
**评估**: This paper focuses on multimodal reasoning agents that use external tools (web search) and RL-based finetuning (GRPO) to improve tool-use reliability. The core contribution—training agents to self-verify and filter retrieved evidence within their own reasoning traces (SVRL)—is squarely an agent-centric research problem, addressing agentic behavior, tool use, and decision-making (when/what to search). It is not a generative/diffusion paper, nor a compression/distillation or infrastructure paper, so Agent is the most relevant category. Quality is solid: it introduces concrete methodological innovations (search-aware penalty, query-diversity reward), targets a well-defined problem (reliable tool use under sparse supervision), and reports consistent gains on multi-hop VQA benchmarks with a compact 7B model, narrowing the gap to proprietary models at lower cost. Novelty and reproducibility are reasonable, though it is a specialized sub-area (multimodal tool-augmented VQA), so it is not top-tier general impact.

**核心贡献**:  
本文提出了一种名为 SVRL（Self-Verification via Reinforcement Learning）的纯强化学习微调框架，旨在让多模态推理智能体在自身的推理轨迹中主动验证并过滤检索到的证据，从而减少对推理时外部验证器的依赖。作者通过在 5,000 条视觉问答样本上对 Qwen-2.5-VL-7B 进行微调，验证了该方法在多跳 VQA 泛化能力和工具调用效率上的稳定提升。整体上，SVRL 缩小了紧凑型智能体与大型专有模型之间的差距，同时显著降低了训练与推理成本。

**创新点**:  
核心创新在于将“自验证”能力直接内化到多模态智能体的推理轨迹中，通过纯 RL 微调实现证据的自我验证与过滤，无需依赖外部验证器；同时引入搜索感知惩罚（search-aware penalty）以抑制不必要的工具调用，以及查询多样性奖励（query-diversity reward）以鼓励生成多样且形式良好的搜索查询，从而在“何时搜索”和“搜索什么”两个层面提供细粒度反馈。

**方法**:  
采用仅基于强化学习的微调方案（类似 GRPO 的 RL 算法），在只有稀疏的结果级监督、缺乏显式验证信号的条件下训练多模态智能体。模型需在理解文本与图像的同时整合含噪检索证据，并在自身推理链中完成证据验证与筛选。训练数据仅使用 5,000 个视觉问答示例，基座模型为 Qwen-2.5-VL-7B，并在奖励设计中结合搜索感知惩罚与查询多样性奖励。

**结果**:  
在仅使用 5,000 条 VQA 样本微调 Qwen-2.5-VL-7B 的情况下，SVRL 在多个基准上均取得了一致的提升，主要体现在多跳 VQA 的泛化能力以及工具使用效率方面。整体性能缩小了紧凑型智能体与规模大得多的专有模型之间的差距，同时所需的训练与推理成本大幅降低。

**相关性与影响**:  
该工作对多模态推理智能体与工具增强型语言模型领域具有重要意义：它表明无需外部验证器或大量标注，仅靠带定制奖励的强化学习即可让小型多模态模型获得可靠的工具使用与自验证能力。这为降低智能体部署成本、提升检索增强推理的鲁棒性提供了可行路径，也为后续在多模态场景中研究 RL 驱动的自我校验与高效工具调用奠定了基础。

---

### 7. AirAnchor: Bridging Local and Global Spatial Information for Zero-Shot Aerial Vision-and-Language Navigation **⭐⭐⭐⭐** (相关度: 85%, 质量: 0.7)

- **arXiv ID**: [2609.08442](https://arxiv.org/abs/2609.08442)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08442)
- **作者**: Shanwei Fan, Bin Zhang, Zhiwei Xu et al. (7 authors)
**评估**: 该论文聚焦于零样本空中视觉语言导航（Aerial VLN），属于具身智能体在真实环境中的语言指令跟随与导航任务，最符合Agent类别。标题中提出的方法旨在桥接局部与全局空间信息，有一定的方法创新点。虽然摘要信息缺失，无法全面评估实验充分性，但该方向具有明确应用价值，且非小众领域，因此给予中等偏高评价。

**核心贡献**:  
论文提出 AirAnchor 框架，用于零样本空中视觉-语言导航，核心目标是桥接局部观测与全局空间信息以提升导航泛化能力。由于提供的摘要为空，无法确认其具体贡献、实验设置与性能指标。

**创新点**:  
从标题推断，主要创新点可能在于面向零样本空中 VLN 的局部-全局空间信息融合机制，或基于锚点的空间表示与对齐策略；但摘要缺失，无法确认具体创新细节。

**方法**:  
摘要未提供，无法确定具体技术方法。根据标题推测，可能涉及局部视觉观测编码、全局空间布局建模以及二者之间的桥接或锚点式融合，用于零样本指令导航。

**结果**:  
摘要未提供，无法给出实验结果、数据集、评价指标或性能对比。

**相关性与影响**:  
若该方法有效，可推动空中机器人/无人机在零样本视觉-语言导航中的泛化与部署，对具身智能、跨模态导航和空中自主系统具有潜在影响；但需原文验证。

---

### 8. Search-to-World: Evaluation of 3D World Delivery from User Request through Web Search **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2609.07605](https://arxiv.org/abs/2609.07605)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07605)
- **作者**: Zixiao Gu, Yabo Chen, Xunzhi Xiang et al. (8 authors)
**评估**: 本文核心贡献在于构建了一个端到端的智能体（agentic）评估任务 Search-to-World 与配套的 WorldSearcher 智能体框架，涵盖请求理解、网页视觉内容检索、失败恢复控制（recovery controller）以及 3D 世界交付。虽然最终目标是 3D 世界生成/重建，但论文的技术主线与创新点均围绕智能体的检索、工具调用、失败恢复与监督微调（SFT）展开，定位更贴近 Agent 方向（agentic web search 与工具编排），而非单纯的图像/视频/3D 生成方法论文，因此归为 Agent。质量方面：提出了新的任务定义与两组可量化指标（ORR、WDR），构建了可复现的评测 harness，并系统对比了代表性模型与 SFT 训练恢复子智能体的效果，具有一定的实证价值与参考意义；但其方法更多是工程性整合（复用优先、失败则从视频重建）而非深层算法创新，3D 交付质量依赖底层基础模型，因此质量评分为中等偏上（0.72），属于高质量范畴。

**核心贡献**:  
论文提出 Search-to-World，一个面向“用户请求→网络搜索→3D世界交付”的端到端评估任务与基准，用于系统衡量智能体能否将检索到的网页内容转化为可用的3D世界。作者定义 Observed Retrieval Rate (ORR) 和 World Delivery Rate (WDR) 来区分“观察到相关内容”与“成功交付符合请求且感知可接受的世界”，并提出 WorldSearcher 作为可复用优先、失败后重建的评估框架。实验表明，3D世界交付能力依赖于底层智能体模型，且检索到相关内容并不保证最终世界交付成功。

**创新点**:  
首次将基于实时网络搜索的3D世界交付形式化为端到端评估任务，并提出 Search-to-World 基准、ORR/WDR 指标以及 WorldSearcher 评估框架。WorldSearcher 采用“先复用、后重建”的策略，并引入结构化恢复控制器，在失败后修正时间定位、替换源视频或重写查询。

**方法**:  
构建覆盖请求理解、网页视觉内容检索和3D世界交付的端到端流程；使用 ORR 衡量是否检索到相关视觉内容，使用 WDR 衡量是否成功交付与请求对齐且感知可接受的世界。WorldSearcher 连接现有搜索智能体与世界交付模块：优先检索可复用的3D世界，若不可用则从视频重建世界；结构化恢复控制器在失败时执行时间定位修正、源视频替换或查询重写。论文还在基准上评估代表性模型，并对恢复子智能体进行监督微调（SFT）。

**结果**:  
实验显示，最终3D世界交付成功与否取决于底层智能体模型；观察/检索到相关内容并不能保证成功交付世界。联合训练恢复子智能体可以提升交付成功率与动作效率。Search-to-World 使智能体式3D世界交付变得可度量，WorldSearcher 提供了一个具备恢复能力的实用评估工具。

**相关性与影响**:  
该工作填补了智能体系统从实时网络搜索到3D世界生成/交付缺乏系统评估的空白，为3D内容生成、具身智能、检索增强智能体和多模态世界建模提供了可复现的评测基准与恢复式框架。其 ORR/WDR 指标和 WorldSearcher 设计有望推动更可靠的“搜索到世界”应用，并促进对检索、推理、重建与失败恢复联合优化的研究。

---

### 9. NutriBench-Kitchen: Benchmarking Embodied AI for Nutrition Management **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2609.07135](https://arxiv.org/abs/2609.07135)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07135)
- **作者**: Yulin Wei, Xiangchen Wang, Jianhui Pan et al. (8 authors)
**评估**: 该论文构建了面向具身营养管理的基准（NutriBench-Kitchen）并提出诊断性长视频智能体（Nutri-Vgent），核心关注智能体的持续状态跟踪、记忆管理与知识驱动的规划决策能力，属于典型的具身/长视频 Agent 研究，而非单纯的生成或训练基础设施方向，因此归类为 Agent。工作具有明确的贡献：1,500 条人工校验的问答对、五类任务划分、对多种专有/开源 VLM 的系统评测，并揭示了模型与人类之间的显著差距，同时还提出了带有情景/食物状态/食谱记忆的智能体方法，实验与动机较扎实。不足之处在于应用场景（厨房烹饪与营养管理）较为垂直细分，通用性受众相对有限，且方法更多是基准与记忆结构的设计而非重大算法突破，故质量评分处于中等偏上（0.68），未达到极高创新水平但具备实际参考价值。

**核心贡献**:  
该论文形式化了具身营养管理任务，要求智能体在动态厨房中感知营养相关事件、维护持久食物状态，并进行知识驱动的规划。为此提出了 NutriBench-Kitchen 基准，包含来自160个烹饪视频的1500个人工验证问答对，覆盖五类任务。论文还提出诊断型长视频智能体 Nutri-Vgent，验证了显式状态表示与结构化记忆对营养管理的价值。

**创新点**:  
首次形式化具身营养管理能力，并构建专门评估动态厨房中食物状态构建、维护、知识检索与跨时间规划能力的基准 NutriBench-Kitchen；同时提出具有分离式情节记忆、食物状态记忆和食谱记忆的长视频诊断智能体 Nutri-Vgent。

**方法**:  
构建包含1500个人工验证问答对的基准，数据来自160个烹饪视频，覆盖 Ingredient Entry、Memory Management、Recipe Query、Long-Term Planning 和 Short-Term Planning 五类任务。评估专有和开源大型视觉语言模型，并提出 Nutri-Vgent，通过分离 episodic memory、food-state memory 和 recipe memory 进行长视频诊断与推理。

**结果**:  
评估显示专有和开源大型视觉语言模型与人类表现存在显著差距，尤其在定量食材估计、长期状态跟踪和交互约束下的推理方面。Nutri-Vgent 取得一致改进，表明显式状态表示和结构化记忆对营养管理任务有效。

**相关性与影响**:  
该工作为具身AI在动态厨房环境中的持续状态跟踪、知识基础推理和营养管理决策提供了测试平台，有助于推动长视频理解、具身智能体记忆机制以及营养相关应用的研究。

---

### 10. GIFT: Goal-Injected Fine-Tuning for Efficient Manipulation Policy Adaptation **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2609.07006](https://arxiv.org/abs/2609.07006)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07006)
- **作者**: Xiaoyuan Fang, Shuo Feng, Yuxuan Wang et al. (6 authors)
**评估**: 该论文聚焦于 Vision-Language-Action (VLA) 操作策略的微调适配，属于具身智能/机器人操作智能体（Embodied Agent）范畴，核心贡献是将生成的目标图像作为高层视觉引导注入预训练 VLA 模型。虽然包含图像编辑生成目标图像这一生成式组件，但其主要创新在于高效的微调框架（zero-initialized convolution 渐进注入目标信息），而非生成模型本身，因此归为 Agent 最合适。方法上有一定创新（零初始化卷积避免破坏预训练策略），实验覆盖 SIMPLER 和 LIBERO 等主流机器人操作基准，结果有说服力（单 epoch 即有显著提升），属于活跃且应用价值较高的方向，非医疗/遥感等小众垂直领域。整体质量中等偏上，方法创新度相对有限（属于增量式的条件注入与微调），但实验较充分，具备一定参考价值。

**核心贡献**:  
本文提出GIFT（Goal-Injected Fine-Tuning），一种轻量高效的微调框架，可将生成的目标图像无缝集成到多种预训练VLA模型中。通过零初始化卷积将目标图像特征注入观测，并随着训练逐步引入目标信息，在避免破坏预训练策略的同时实现高效目标理解。实验表明，该方法仅需单轮微调即可在多个仿真操控任务上显著超越基线模型。

**创新点**:  
提出零初始化卷积将目标图像特征渐进式注入预训练VLA模型观测中，从零开始增长参数以避免微调初期的有害噪声干扰；同时设计了一种精细图像编辑方法，从初始观测和任务指令生成语义与视觉一致的目标图像。

**方法**:  
首先利用精细图像编辑方法，根据初始观测和语言指令生成语义及视觉一致的目标图像；然后将目标图像特征通过零初始化卷积注入VLA模型的观测输入中，使模型在微调过程中逐步学习目标条件信息，从而以低成本实现目标感知的策略适配。

**结果**:  
仅需单轮微调，GIFT在两个SIMPLER设置上分别比基础模型提升6.0%和13.4%，在LIBERO上提升4.7%，验证了其高效性和有效性。

**相关性与影响**:  
该工作为视觉-语言-动作模型的目标条件微调和高效适配提供了新思路，能够以较低计算成本增强操控策略的鲁棒性和目标理解能力，对机器人操控、具身智能及VLA模型实际部署具有重要潜在影响。

---


---

## 🌍 World Model 相关内容

### 1. ActionSplice: In-Flight Action Editing for Interactive World Models **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.08230](https://arxiv.org/abs/2609.08230)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08230)
- **作者**: Pardis Taghavi, Tingyu Guo, Jonas Lossner et al. (5 authors)
**评估**: 该论文研究交互式视频世界模型中的实时动作编辑问题，提出 ActionSplice 推理框架与 Counterfactual State Transport 方法，使冻结的世界模型和采样器无需回滚即可响应采样过程中新到达的动作。论文主题明确属于 World_Model 类别，而非一般图像/视频生成。方法具有技术创新性，实验覆盖 minWM-Wan Action2V 和 HY-WM1.5，并报告了 LPIPS 降低与像素就绪加速等定量结果，说明其有效性和实用价值。因此判定为高质量论文。

**核心贡献**:  
本文提出 ActionSplice，一种用于交互式视频世界模型的推理时动作编辑框架，解决分块自回归生成中采样过程中新动作无法即时生效的问题。该方法将问题形式化为反事实状态迁移（Counterfactual State Transport, CST），在不重放已完成去噪步骤、不修改冻结的世界模型和采样器的前提下，使新的动作条件能够作用于当前正在生成的块。论文在多个视频世界模型上验证了该方法能显著降低回滚相关误差并提升响应速度。

**创新点**:  
将交互式世界模型中的在线动作编辑建模为反事实状态迁移问题，并通过轻量级校正器在相同求解器步上将被打断的骨干原生表示迁移到由修正动作诱导的匹配状态。提出两种变体：CST_R 重定向整个当前活跃块，CST_T 保留时间前缀并仅更新后缀，从而避免等待下一块或回滚已完成的采样计算。

**方法**:  
ActionSplice 保持世界模型与采样器冻结，在采样过程中检测到新动作后，不重新执行已完成评估，而是利用轻量级校正器将当前被中断的表示向新动作对应的目标状态进行传输。CST_R 更新整个活跃块；CST_T 进行时间拼接，保留已生成的前缀，仅校正受新动作影响的后续部分，从而在推理阶段实现动作条件的即时切换。

**结果**:  
在 minWM-Wan Action2V 和 HY-WM1.5 上，CST_R 相比直接条件替换将回滚相对 LPIPS 分别降低 61.5% 和 75.9%；CST_T 将后缀 LPIPS 分别降低 56.1% 和 77.5%，同时相比等待策略取得 2.73 倍和 1.69 倍的像素就绪加速。在 HY-WorldPlay 协议下，CST_R 相对原始 rollout 达到 PSNR 25.66 dB、SSIM 0.6902 和 LPIPS 0.1337。

**相关性与影响**:  
该工作使交互式视频世界模型能够在生成过程中即时响应动作变化，避免等待、错误条件传播或高成本回滚，对实时交互式仿真、游戏、机器人和视频生成等需要低延迟动作控制的应用具有重要价值。其冻结模型与采样器的推理时校正思路也为世界模型的高效在线编辑提供了通用框架。

---

### 2. CST-WM: A Causally Structured World Model for Embodied Visual Tracking **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.9)

- **arXiv ID**: [2609.06302](https://arxiv.org/abs/2609.06302)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06302)
- **作者**: Junyi Hu, Shuaihang Yuan, Yi Fang
**评估**: 该论文提出 CST-WM，一种因果结构化的世界模型，用于具身视觉跟踪。核心贡献在于识别并缓解 action-conditioned prediction 中的因果幻觉问题，将 latent state 分解为目标证据、机器人、观测三个分支，并阻断动作直接注入目标证据分支，从而提升未来预测与规划一致性。方法具有明确技术创新，实验覆盖 EVT-Bench 和 Habitat 3.0，包含标准跟踪、目标丢失恢复和跨数据集迁移，并给出多步 rollout 保真度、规划价值一致性和 action leakage 等诊断指标，实验较充分。该工作属于世界模型与具身智能交叉方向，对具身视觉跟踪、模型预测控制和因果世界模型有参考价值，不属于低质量或小众垂直应用。因此分类为 World_Model，质量较高。

**核心贡献**:  
该论文提出CST-WM，一种面向具身视觉跟踪的因果结构化世界模型，用于解决动作条件预测中直接由当前动作幻觉目标证据的因果捷径问题。通过将隐状态分解为目标证据、机器人状态和观测分支，并阻断动作到目标证据分支的直接注入，CST-WM结合基于rollout的模型预测控制，统一支持稳定跟踪与目标丢失后的重新捕获。

**创新点**:  
识别并建模具身视觉跟踪中的任务特定因果幻觉：模型易利用机器人控制与目标观测之间的强相关性，错误地从当前动作直接预测目标证据。创新性地将隐状态分解为目标证据、机器人、观测三支，并因子化状态转移，使动作只能经由机器人运动及由此产生的观测变化间接影响目标证据，从而避免跟踪规划中的语义错误捷径。

**方法**:  
CST-WM将世界模型隐状态分解为目标证据、机器人状态和观测三个分支，并设计因果结构化的转移函数：显式阻断动作直接注入目标证据分支，同时保留动作对机器人运动和观测更新的影响。基于该世界模型进行多步rollout，并与模型预测控制结合，用于在线规划，同时支持持续跟随和目标重新获取。

**结果**:  
在EVT-Bench和Habitat 3.0上，覆盖标准跟踪、目标丢失恢复和跨数据集迁移任务，CST-WM在跟随质量、距离范围控制、安全性和重新捕获方面优于反应式基线及世界模型基线。离线诊断表明其具有更好的多步rollout保真度、更强的规划价值一致性，并显著减少直接动作泄漏。

**相关性与影响**:  
该工作表明，在具身视觉跟踪中仅提升未来预测能力并不足够，预测结构本身必须与目标证据进入规划的方式一致。其因果结构化世界模型为具身智能、视觉跟踪和基于模型的规划提供了新思路，有助于提升机器人在遮挡、自我运动和干扰物存在下的鲁棒目标跟踪与重捕获能力。

---

### 3. GE-Act 2.0: Pretraining and Scaling a World-Action Model for Robotic Manipulation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.05588](https://arxiv.org/abs/2609.05588)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.05588)
- **作者**: AgiBot Research Team, Renhang Liu, Wenzhi Zhao et al. (45 authors)
**评估**: 该论文提出GE-Act 2.0世界-动作模型（World-Action Model），核心是通过预测未来状态来指导机器人操作动作，本质上属于世界模型范畴——学习环境的动态演化并用于决策/规划，因此归类为World_Model最为贴切。虽然涉及视觉规划与生成组件，但核心贡献是世界模型的预训练与规模化，而非纯图像/视频生成。质量方面：论文包含明确的技术创新（CoAE控制导向自编码器、单步视觉规划器SVP、逆动力学模型IDM以及KASO知识对齐选择性优化），实验充分（100个任务、20类技能组、held-out场景，数据规模从300到30000小时验证scaling律），并展示了跨本体迁移和zero-shot OOD成功率的相关性分析（Pearson r=0.80）。作者来自Genie Envisioner团队，研究背景扎实。方法完整、结论可靠，具有较高的学术参考价值，判为高质量论文。

**核心贡献**:  
GE-Act 2.0 提出了一种从零开始在机器人操作数据上预训练并扩展的世界-动作模型，而非依赖预训练视频生成器。该模型通过控制导向自编码器、单步视觉规划器和逆动力学模型分别预训练后再联合训练，实现了无需逐任务微调的零样本操作策略。实验表明，随着协同训练数据从300小时扩展到30000小时，模型成功率显著提升，并展现出跨本体迁移能力。

**创新点**:  
首次系统探索世界-动作模型（WAM）的预训练与扩展，所有可训练生成与动作组件均在操作数据上从零初始化；提出控制导向自编码器（CoAE）、单步视觉规划器（SVP）和逆动力学模型（IDM）的组合架构；引入知识对齐选择性优化（KASO），通过筛选与记录动作行为兼容的预测未来来减少监督不匹配。

**方法**:  
GE-Act 2.0 由三部分组成：CoAE 在激进压缩下保留动作与指令相关信息；SVP 在单次可微前向过程中生成完整未来状态；IDM 从预测未来和当前状态推断动作。视觉规划与逆动力学可在互补数据上分别预训练，随后通过 KASO 联合训练。评估时直接使用预训练检查点，不进行逐任务微调。

**结果**:  
在20个操作技能组、100个任务及留出场景/背景/光照/物体实例上评估：协同训练数据从300小时扩展到30000小时，G1-OP成功率从17.1%提升至44.1%，G2-90D从13.4%提升至31.1%；G2-90D虽不足协同训练数据的2%，仍提升17.7个百分点，表明跨本体迁移。增益覆盖19/20和18/20技能组，技能特定覆盖率与零样本OOD成功率强相关（Pearson r=0.80；Spearman rho=0.85）。模型在至少90%试验中正确 grounding 物体、颜色、形状和位置引用，并能遵循与已执行行为或常规场景关联冲突的显式指令。

**相关性与影响**:  
该工作推动了世界-动作模型在机器人操作中的可扩展预训练，证明了从零初始化、跨数据规模扩展和跨本体迁移的可行性，并展示了强零样本OOD泛化与指令遵循能力。其方法有望减少对预训练视频生成器和任务特定微调的依赖，为通用机器人操作基础模型提供重要参考。

---

### 4. CALIPER: Clean Scenes Cannot Rank Physical Inference in Pretrained Visual Representations **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.9)

- **arXiv ID**: [2609.08250](https://arxiv.org/abs/2609.08250)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.08250)
- **作者**: Aman Mehta, Riya Baviskar
**评估**: 该论文研究预训练视觉表示作为世界模型感知前端时的物理推理能力评估，提出CALIPER基准，揭示固定相机清洁场景下物理推断难以被现有线性探针和扰动基准有效排序的问题，并给出基于校准、交换和多样化场景的检验方法。核心贡献属于世界模型与物理推理评估，而非生成、蒸馏或训练推理基础设施。实验覆盖2,000个模拟回合、8种表示，包括V-JEPA 2、随机ViT和原始像素，并展示clean scene与resampled scene下的显著差异，方法严谨、结论有实际参考价值，因此判定为高质量论文。

**核心贡献**:  
How far a pushed object slides depends on its mass and friction, which no single image reveals. Pretrained visual encoders are increasingly used as the perception front end of world models for manipul...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 5. Learning to Use Imagination: Progress-Conditioned Future Utilization for World Action Models **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.06578](https://arxiv.org/abs/2609.06578)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06578)
- **作者**: Yijie Zhu, Zitong Yu, Wei Li et al. (7 authors)
**评估**: 该论文聚焦于 World Action Models (WAMs)，核心是建模并利用'想象的未来'（future visual dynamics / imagination）来辅助动作生成，这属于世界模型（World Model）范畴——即通过预测未来状态/动态来支持决策与规划。虽然应用于 VLA/机器人动作生成场景（邻近 Agent 方向），但其核心贡献在于对想象未来的建模与自适应利用机制（含 inter-progress 与 intra-progress 两层非均匀性建模），因此 World_Model 最为贴切。质量方面：作者明确识别了未来效用的两类非均匀性问题，并提出 SS-DTPE（自监督双时序进度编码器）与 HPIM（分层进度条件想象调制）两个紧密耦合的组件，方法具有一定创新性，且声称在强 VLA/WAM 基线上取得一致增益。方法设计合理、动机清晰，但仅凭摘要无法完全确认实验规模与开源情况，故质量分取中等偏上。

**核心贡献**:  
本文提出 ProWAM，一种以执行进度为条件的世界动作模型，用于自适应地利用想象出的未来视觉动态来生成动作。针对未来效用随执行阶段变化以及同一进度内未来隐变量相关性不均的问题，ProWAM 引入执行进度作为显式中间表示，并联合设计进度编码与想象力调制模块。实验表明其在多个强 VLA 和 WAM 基线上取得一致提升。

**创新点**:  
将执行进度作为显式中间表示，用于条件化未来想象的使用；提出自监督双时序进度编码器 SS-DTPE 与分层进度条件想象力调制 HPIM，分别从进度表示学习和跨进度/进度内两个层面解决未来效用非均匀问题。

**方法**:  
ProWAM 包含两个紧耦合组件：SS-DTPE 通过短期动作-观测交互建模与长期循环进度聚合，捕捉近期执行反馈和累积任务历史，得到可靠的执行进度表示；HPIM 基于该进度表示，在跨进度层面进行全局调制以适配不同执行阶段的未来利用策略，并在进度内层面区分单个未来隐变量的相关性，从而抑制干扰或不可靠的预测线索。

**结果**:  
摘要指出大量实验表明 ProWAM 相较于强 VLA 和 WAM 基线均取得一致性能提升；但未提供具体数值指标或数据集名称。

**相关性与影响**:  
该工作对视觉-语言-动作模型与世界动作模型领域具有重要意义，强调了未来想象不能静态使用，而应随执行进度动态调制。其进度条件化框架有望提升机器人在复杂任务中的动作生成鲁棒性与泛化能力，并为后续研究提供可借鉴的自监督进度表示与分层想象力利用思路。

---

### 6. Diagnosing and Dynamically Filtering Occupancy World Models for Active Mapping **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2609.06820](https://arxiv.org/abs/2609.06820)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.06820)
- **作者**: Jiahui Zhang, Gongbo Liang, Yu Zhang
**评估**: 该论文围绕预训练的occupancy网络作为世界模型（Occupancy World Models）展开，研究其在主动建图（active mapping）中预测几何结构对下游规划的影响。核心对象是'world model'的occupancy表示及其误差诊断，与World_Model类别高度契合。论文通过控制变量（固定planner、仅变化occupancy表示）系统诊断了假阳性/假阴性对规划的影响，揭示了几何精度与下游规划性能之间的差距，具有一定的分析价值和启发意义。但论文主要是一次诊断性研究，提出的动态过滤策略仍处于'preliminary examples'阶段，实验规模和验证深度有限，属于robotics主动建图细分方向，受众相对小众。综合判断为中等质量研究，未达到低质量过滤标准。

**核心贡献**:  
本文系统诊断了主动建图中占用世界模型误差对下游规划的影响，通过固定规划器并替换不同占用表示，发现单独纠正假阳性或假阴性并不能稳定提升最终覆盖率。基于此，作者提出一种动态过滤策略，在保留未探索空间预测的同时，利用在线观测抑制反复未被支持的占用预测。

**创新点**:  
揭示了占用预测精度与主动建图下游规划性能之间的差距，并提出一种面向未探索区域与在线观测的动态过滤策略，以改善视角选择和可达表面探索。

**方法**:  
在固定规划器条件下，对比多种占用表示：无补全、学习到的占用、由真实值 oracle 去除假阳性、由 oracle 恢复假阴性以及真实值占用。进一步提出动态过滤策略：对未探索空间保留预测，对反复缺少观测支持的占用进行在线抑制。

**结果**:  
实验表明，仅纠正假阳性或假阴性不能一致提升最终覆盖率；真实值占用对覆盖效率的提升远大于对终点覆盖率的提升，说明规划和可达性仍是重要瓶颈。初步示例显示，动态过滤可将视角选择重定向到原本可能未被观测到的可达表面。

**相关性与影响**:  
该工作对主动建图、占用世界模型和机器人自主探索具有重要参考价值，强调几何世界模型精度并非唯一瓶颈，规划与可达性同样关键。所提动态过滤思路有望提升未知环境探索效率和视角选择质量。

---

### 7. CASCADE: A Spatio-Temporal-Causal Reasoning Representation and Dataset for Driving **⭐⭐⭐** (相关度: 78%, 质量: 0.9)

- **arXiv ID**: [2609.07094](https://arxiv.org/abs/2609.07094)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07094)
- **作者**: Jenny Schmalfuss, Despoina Paschalidou, Simon Gerstenecker et al. (5 authors)
**评估**: 该论文提出面向自动驾驶场景的时空因果推理表示与大规模人工标注数据集，核心在于显式建模驾驶环境中的动作、时空位置和因果关系，这属于世界模型/场景理解与动力学建模方向。论文来自 NVIDIA，提供 2,066 个驾驶片段和超过 34K 标注元素，支持机器可验证的推理评估，实验与数据贡献较扎实，具有较高参考价值。虽然偏自动驾驶应用，但并非小众垂直领域，且方法、数据和评测设计较完整，因此判定为高质量论文。

**核心贡献**:  
CASCADE 提出了一个用于自动驾驶场景推理的结构化时空因果表示，并基于该表示构建了大规模人工标注数据集。该表示对每个与自车交互的参与者逐帧记录其动作、发生位置以及与他者动作和状态的依赖关系，从而使推理预测可以被机器逐元素验证，而无需依赖（M）LLM 评判。数据集覆盖 PhysicalAI 的 2,066 段驾驶视频片段，包含超过 34K 个标注元素。

**创新点**:  
首次将显式的因果链接引入驾驶场景的时空表示中，弥补了文本推理链缺乏时空基础、时空场景图缺乏因果关系、以及大规模推理标注多为模型生成难以验证的缺口。其核心突破在于让推理预测可被机器逐元素打分验证，为自动生成推理标签的质量检验提供了人工标注的参考基准。

**方法**:  
构建 CASCADE（Causal Spatio-Temporal Analysis of Driving Environments）结构化场景表示：针对每个与自车交互的 actor，在其可见期间逐帧记录所采取的动作、动作发生的空间位置，以及该动作如何依赖于其他 actor 的动作与状态。基于此表示对 PhysicalAI 数据集进行人工标注，涵盖时间戳级的自车与 agent 动作、因果关系与潜在影响，以及 agents、objects、traffic lights 和环境元素的标注，形成可逐元素比对的推理评估结构。

**结果**:  
CASCADE 数据集包含 2,066 段驾驶视频片段的人工标注，共 34K+ 个元素：8.6K 个带时间戳的自车与 agent 动作、3.7K 条因果链接、2.9K 项潜在影响，以及 6.1K 个针对 agents、objects、traffic lights 和环境的标注。该数据集完全由人工标注，可作为评估 Physical AI 模型推理能力、验证自动生成推理标签质量的参照标准（数据集已发布于 Hugging Face: nvidia/cascade）。

**相关性与影响**:  
该工作为自动驾驶中的长尾泛化推理研究提供了可验证的表示与评测基准，使推理质量评估摆脱对 LLM 裁判的依赖，转向客观的逐元素比对。它既可用于基准测试 Physical AI 模型的推理能力，也可用于审核和筛选自动生成的推理标签，对可解释自动驾驶、因果推理、时空场景理解及多模态推理数据标注等方向具有重要推动意义。

---

### 8. "World Knowledge" in the Weights: Reading Concept Circuits of Vision Transformers **⭐⭐⭐** (相关度: 70%, 质量: 0.8)

- **arXiv ID**: [2609.09055](https://arxiv.org/abs/2609.09055)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09055)
- **作者**: Yanlin Chen, Tang Li, Xi Peng
**评估**: 论文标题和摘要提及分析Vision Transformer中的概念电路（concept circuits），并关联'世界知识'，属于模型内部机制与知识表征研究，与WorldModel类别中对世界知识的建模和理解相关。论文聚焦可解释性机制分析，具有技术深度和潜在参考价值，但具体实验细节不完整，质量中上。

**核心贡献**:  


**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 9. MV-STRIDE: Enabling MLLMs to Master Multi-View Spatial Reasoning via Hierarchical Capability Modeling **⭐⭐⭐** (相关度: 62%, 质量: 0.7)

- **arXiv ID**: [2609.07258](https://arxiv.org/abs/2609.07258)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.07258)
- **作者**: Jin Xu, Xiaojian Huang, Zhuodong Luo et al. (9 authors)
**评估**: 该论文聚焦于多视角空间推理与3D一致的场景认知，构建了层次化的多视角空间推理数据集（MV-STRIDE），并配套多阶段训练框架，使MLLM能够建模基础感知—场景理解—上下文推理的依赖关系，本质上是为多模态模型赋予结构化的3D空间认知与世界建模能力，因此最贴近 World_Model 类别。它并非图像/视频生成、蒸馏压缩或训练推理基础设施方向。质量方面：论文提出了明确的层次化能力建模思路、带跨视角依赖约束的QA生成管线以及认知链式思维监督，并在MMSI-Bench等多视角基准上取得SOTA，具有一定方法创新与实验支撑。但作为数据集/基准类工作，技术方法更偏工程管线整合，核心算法创新有限，且属于相对细分的空间推理评测方向，整体质量中等偏上（约0.72），可保留。

**核心贡献**:  
本文提出 MV-STRIDE，一个面向多视图空间推理的分层数据集，旨在通过显式建模基础感知、场景理解与复杂上下文推理之间的依赖关系，为多模态大模型提供符合人类空间认知的学习路径。作者构建了系统化的 QA 生成流水线，并基于分层数据集设计多阶段训练框架，使模型在多视图空间推理基准上取得领先性能。

**创新点**:  
核心创新在于提出具有相互依赖与分解能力的分层多视图空间推理数据集 MV-STRIDE，通过跨视图依赖约束避免单视图可解问题，并为复杂推理提供有认知依据的链式思维监督。

**方法**:  
方法包括：利用多样 3D 场景源构建系统化 QA 生成流水线；显式建模基础感知、场景理解和复杂上下文推理之间的层级依赖； enforced 跨视图依赖约束以确保任务需要多视图信息；针对复杂推理生成 cognitively grounded chain-of-thought 监督；并采用基于该分层数据集的多阶段训练框架提升 MLLM 的多视图空间推理能力。

**结果**:  
大量评估表明，基于该分层数据集的多阶段训练框架在多个空间推理基准上达到 state-of-the-art，尤其是在面向多视图的 MMSI-Bench 上表现突出，并使 MLLM 能在不同视角下保持稳健且 3D 一致的空间推理。

**相关性与影响**:  
该工作对多模态大模型的空间智能研究具有重要意义，弥补了现有数据集缺乏结构化 3D 认知路径的不足，为多视图空间推理提供了可扩展的数据构建与训练范式，有望推动具身智能、机器人导航和 3D 场景理解等应用发展。

---

### 10. Rethinking Learned Occupancy in Autonomous Active Mapping with Observation-Gated Filtering **⭐⭐⭐** (相关度: 60%, 质量: 0.6)

- **arXiv ID**: [2609.09069](https://arxiv.org/abs/2609.09069)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09069)
- **作者**: Jiahui Zhang, Bonian Han, Gongbo Liang et al. (4 authors)
**评估**: 该论文研究自主3D主动建图中的学习式占据补全（learned occupancy completion），其核心是构建面向规划器的空间/世界表示（occupancy map）以支持导航与避障，属于对环境的几何世界建模，因此最贴近 World_Model 类别，而非纯生成、蒸馏或训练基础设施。质量方面：论文采用受控闭环基准，通过固定主动建图系统、仅改变规划器所面对的占据表示（observation-only / learned / oracle / ground-truth）来解耦分析，提出 observation-gated filter 抑制缺乏RGB-D支撑的预测，方法清晰且实验设计有一定严谨性，也坦诚说明了对位姿精度和行星探测条件的局限。但整体属于较窄的机器人主动建图方向，创新偏增量（滤波/门控思想），实验规模有限（25次启动），受众较小，未达到高影响力工作水平。综合评估为中等质量、可保留。

**核心贡献**:  
Autonomous 3D active mapping requires a space robot to choose where to sense while building the geometry needed for navigation. Learned occupancy completion extends spatial context beyond the current ...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---


---

## 📊 统计信息

| 类别 | 论文数量 | 占比 |
|------|----------|------|
| 🎨 AIGC 相关内容 | 0 | 0.0% |
| 🖼️ 图像/视频/全模态生成 | 10 | 3.6% |
| 🧠 大模型蒸馏与压缩 | 5 | 1.8% |
| ⚙️ 训练推理基础设施 | 10 | 3.6% |
| 🧠 Agent 相关内容 | 10 | 3.6% |
| 🌍 World Model 相关内容 | 10 | 3.6% |
| 其他 | 234 | 83.9% |
| **总计** | **279** | **100%** |
