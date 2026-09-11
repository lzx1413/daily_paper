# 📚 arXiv CS.CV 每日论文报告

**报告日期**: 2026-09-11  
**论文来源**: [arXiv CS.CV Recent](https://arxiv.org/list/cs.CV/recent)  
**关注论文数**: 30篇（每类别Top 10，经质量筛选）

> 注：每类别按大模型评估的相关性和质量排序，仅展示前10篇高质量论文。已自动过滤低质量和小众方向论文。

---

## 📑 目录

- [🎨 AIGC 相关内容](#aigc) (0篇)
- [🖼️ 图像/视频/全模态生成](#image_video_omni_generation) (10篇)
- [🧠 大模型蒸馏与压缩](#distillation) (6篇)
- [⚙️ 训练推理基础设施](#training_inference_infra) (5篇)
- [🧠 Agent 相关内容](#agent) (4篇)
- [🌍 World Model 相关内容](#world_model) (5篇)

---

## 🖼️ 图像/视频/全模态生成

### 1. Interpreting Object-Dependent Concept Brittleness in Text-to-Image Diffusion Models **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.09909](https://arxiv.org/abs/2609.09909)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09909)
- **作者**: Yifan Yuan, Xiangyu Liu, Hongming Shan et al. (8 authors)
**评估**: 该论文研究文本到图像扩散模型中的对象依赖概念脆弱性，属于图像生成领域。论文提出了一种基于稀疏自编码器的可解释性框架，用于审计和修正生成失败，方法具有创新性，实验覆盖多个扩散骨干网络并取得显著改进，且代码开源。不属于小众方向，质量较高。

**核心贡献**:  
论文识别出文本到图像扩散模型中一种此前未被充分探索的失败模式，即object-dependent concept brittleness：仅目标对象不同的一小组提示在相同生成设置下持续无法实现同一目标概念。作者提出一个面向可解释性的审计与最小修正框架，通过分析去噪轨迹中的稀疏自编码器（SAE）空间来定位概念证据缺失、减弱或延迟的问题，并验证推理时修正策略的有效性。

**创新点**:  
首次系统性地提出并定义object-dependent concept brittleness现象，将其归因于模型内部系统性盲区而非随机采样噪声；提出在逐步SAE空间中审计去噪轨迹，并构建类级概念原型以进行轻量级推理时特征插值修正。

**方法**:  
在step-wise稀疏自编码器（SAE）空间中分析扩散模型的去噪轨迹，使抽象风格和属性概念比原始去噪表示更可分离；通过比较成功与失败生成，识别证据缺失、减弱或时间延迟的概念维度；从可靠的类一致样本构建类级概念原型；在推理时将去噪特征向对应原型插值，以验证诊断出的概念缺陷并进行最小修正。

**结果**:  
在多个扩散骨干网络上的风格和属性失败案例中，该方法在概念一致性、文本保真度和修复成功率方面均取得显著提升；进一步分析表明，更深的去噪表示提供更清晰的概念结构，而早期阶段干预具有最强的修正效果。

**相关性与影响**:  
该工作为文本到图像扩散模型的可解释性与失败诊断提供了新视角和实用工具，有助于理解概念级生成脆性、提升提示鲁棒性，并为无需任务特定重训练的推理时修正提供参考。

---

### 2. StreetDiff: Multi-view Street Scenes Generation via Cross-view Consistent Multi-view Stable Diffusion with Structure Prompts **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.09890](https://arxiv.org/abs/2609.09890)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09890)
- **作者**: Qi Zhang, Yanyifan Wang, Weiyuan Zhang et al. (4 authors)
**评估**: 该论文聚焦多视角街景生成（multi-view diffusion），属于图像/视频/全模态生成范畴，与text-to-image、diffusion models、场景生成等方向高度相关。方法上提出了Panorama–Perspective Synergy设计与Panorama Alignment Module（PAM），通过球面投影注意力约束实现跨视角一致性，无需修改扩散骨干网络，具有一定的技术创新性；同时构建了Street360大规模HDR多视角城市全景数据集，实验充分且验证了结构一致性与视觉保真度的提升。整体方法明确、贡献实质、实验支撑较强，属于高质量工作。虽应用场景偏街景，但涉及通用多视角扩散生成与自动驾驶等广泛下游任务，参考价值较好。

**核心贡献**:  
StreetDiff 是一种面向复杂城市街景的多视角扩散生成框架，旨在解决现有方法在相机旋转下跨视角一致性不足的问题。它通过全景-透视协同设计和全景对齐模块，在去噪过程中显式注入基于球面投影的跨视角对齐约束。论文还构建了大规模 HDR 多视角城市全景数据集 Street360，并在结构一致性和视觉保真度上显著优于已有方法。

**创新点**:  
提出在不修改扩散主干的前提下，将跨视角结构对齐约束注入多视角扩散去噪过程；设计 Panorama-Perspective Synergy 解耦全局布局推理与局部细节合成；引入 Panorama Alignment Module (PAM)，通过球面投影注意力约束实现跨视角一致性；构建 Street360 大规模 HDR 多视角城市全景数据集。

**方法**:  
StreetDiff 采用多视角 Stable Diffusion 框架，结合结构提示与全景-透视协同设计：先进行全局布局推理，再进行局部细节合成；通过 Panorama Alignment Module (PAM) 建立基于球面投影的跨视角注意力约束，在去噪过程中强制多视角对齐；该方法无需修改扩散骨干网络即可提升城市街景生成中的跨视角连贯性。

**结果**:  
大量实验表明，StreetDiff 在复杂城市街景生成任务中显著提升了结构一致性和视觉保真度，相比现有多视角扩散生成方法具有更强的跨视角一致性，并能有效缓解物体重复、结构扭曲和布局不一致等问题。

**相关性与影响**:  
该工作针对多视角扩散模型在复杂城市环境中的跨视角一致性瓶颈，对全景/多视角场景生成、自动驾驶仿真、虚拟现实与城市建模等方向具有重要意义；同时 Street360 数据集可为多视角城市全景生成提供大规模 HDR 基准，推动相关领域在结构一致性和真实感生成方面的研究。

---

### 3. Guiding Image-to-3D Generation with Test-Time Partial Observations **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.10531](https://arxiv.org/abs/2609.10531)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10531)
- **作者**: Jerred Chen, Simon Weber, Ronald Clark
**评估**: 该论文研究图像到3D生成（image-to-3D generation），通过测试时的部分几何观测引导预训练的生成模型，属于3D生成方向，明确契合 Image_Video_Omni_Generation 类别（该类别描述中已包含3D生成）。方法上提出了无需训练/微调的框架，基于占用表示的射线一致观测似然，结合表面占用与自由空间证据，并将其应用于SAM 3D及多视图扩展，具有一定的技术创新性。实验显示在几何保真度和视觉质量上均有提升，实验支撑较为充分。非小众垂直领域（如医疗/遥感），也非简单水文，具有一定的实际参考价值，但训练无关的测试时引导思路相对增量，且依赖已有生成模型，创新度中等偏高，因此质量评分约为0.75。

**核心贡献**:  
本文提出了一种免训练（training-free）的框架，能够在测试阶段将部分几何观测（如局部点云或深度信息）注入到预训练的图像到3D生成模型中，通过显式的测试时引导提升生成资产的几何保真度。该方法无需重新训练或微调模型，在SAM 3D及其多视角扩展上均显著改善了不同可观测度下的几何精度与视觉质量。

**创新点**:  
首次提出在测试阶段利用部分几何观测引导预训练图像到3D生成模型，无需修改模型参数或进行再训练；核心是定义在模型占据表示（occupancy representation）上的、具有射线一致性的观测似然，将表面占据证据与自由空间证据统一结合，从而实现与生成先验互补的显式几何约束。

**方法**:  
方法基于一个免训练的测试时引导框架：给定预训练的图像到3D生成模型（其内部使用占据场表示），将测试时获得的部分几何观测编码为射线一致的似然函数，该似然同时建模表面占据（surface occupancy）与自由空间（free-space）两类证据；在采样/生成过程中以该似然作为引导信号（guidance）对生成轨迹进行修正，并将其扩展到多视角设定（multi-view extension）以适配SAM 3D。整个过程不更新模型权重。

**结果**:  
在SAM 3D及其多视角扩展上的实验表明，该方法在不同可观测性水平下均大幅提升了生成结果的几何保真度，同时改善了视觉质量；结果证明预训练图像到3D模型可以有效整合部分几何观测，并与已学到的生成先验形成互补。

**相关性与影响**:  
该工作为图像到3D生成的实际应用（如需要几何精度的场景）提供了低成本的增强途径，揭示了预训练生成模型在测试时可通过显式观测似然进行几何校正的潜力；对未来无需重训练的生成模型适配、多模态条件引导以及几何一致性研究具有启发意义。

---

### 4. SceneHI: High-Resolution 3D-Consistent Scene Texturing with Controllable Illumination **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.10363](https://arxiv.org/abs/2609.10363)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10363)
- **作者**: Athanasios Tragakis, Marco Aversa, Daniela Ivanova et al. (7 authors)
**评估**: 该论文属于图像/3D生成方向，核心是利用2D扩散模型的高分辨率、光照感知先验进行3D纹理合成。技术贡献明确：提出精确的像素-纹素解析映射以对齐多视角扩散轨迹、设计高分辨率潜在纹理(HRLT)作为持续画布、以及光照感知生成pass嵌入几何一致的阴影。方法创新性强，能同时保证3D一致性、高分辨率保真度和物理合理的烘焙阴影，并在生成时间上比现有场景级方法减少80%，实验与结论有说服力。应用于3D资产纹理合成与生产工作流，具有实际参考价值，非垂直小众方向，故评为高质量。

**核心贡献**:  
SceneHI is a framework for high-resolution, illumination-aware 3D texture synthesis that transfers priors from 2D diffusion models directly onto 3D objects without fine-tuning or optimization. It uniquely combines 3D-consistency, high-resolution fidelity, and physically plausible baked shadows for complex multi-object scenes. The method achieves high visual fidelity while reducing generation time by 80% compared to existing scene-level approaches.

**创新点**:  
The first demonstration that high-resolution textures, previously limited to 2D synthesis, can be generated directly on 3D objects without model fine-tuning or optimization. SceneHI integrates 3D-consistency, high-resolution texture fidelity, and controllable illumination with baked shadows in a single generative pipeline.

**方法**:  
SceneHI uses High-Resolution Latent Textures (HRLTs) as a persistent canvas for gradually denoised textures, with camera views performing denoising steps in latent pixel space. An exact analytical pixel-to-texel mapping aligns diffusion trajectories across multiple viewpoints to enforce geometric coherence. A final light-aware generative pass embeds realistic geometry-consistent shadows directly into the texture atlases.

**结果**:  
The framework produces high visual fidelity textures with strong multi-view consistency and realistic baked shadows. It reduces generation time by 80% compared to existing scene-level methods, while enabling high-resolution 3D texture synthesis without per-object optimization or fine-tuning.

**相关性与影响**:  
SceneHI bridges 2D diffusion-based texture generation and 3D content creation, offering a practical path to production-ready 3D texturing with controllable illumination. Its ability to maintain 3D consistency at high resolution while being significantly faster could impact 3D asset creation, virtual environments, games, and VFX workflows.

---

### 5. AnimalLift: Reconstructing Animatable 3D Animals from a Single Image by Learning Canonical Shape, Texture, and Fur Maps **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.09513](https://arxiv.org/abs/2609.09513)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09513)
- **作者**: Chunyi Sun, Ruyi Zha, Weijian Deng et al. (6 authors)
**评估**: 该论文提出从单张图像重建可动画的3D动物资产，本质上是单图到3D的生成/重建任务，属于图像/视频/全模态生成中的3D生成范畴。方法具有明确技术创新：统一的规范空间（canonical space）、跨数据集一致的拓扑与UV参数化、UV对齐的毛发图（fur map）编码发丝几何，以及程序化数据生成管线提供大规模监督。结构化的表示还支持动画、姿态迁移、毛发编辑和仿真渲染等下游应用，实验在合成与真实数据集上验证了重建质量与泛化能力。整体方法新颖、实验较充分、应用价值明确，属于高质量工作；虽聚焦动物类别，但面向通用3D生成与可动画资产重建，不属于过度细分的垂直领域。

**核心贡献**:  
AnimalLift 提出一个从单张图像重建可动画 3D 动物资产的框架，通过共享规范空间和统一拓扑/UV 参数化，联合预测规范几何、纹理和毛发。其核心是 UV 对齐的毛发图，可在表面规范域中编码毛干几何，使显式毛发重建兼容网格变形和毛发模拟。方法还引入程序化数据生成管线，提供大规模且几何、纹理、毛发对齐的监督数据，并支持动画、姿态迁移、毛发编辑和仿真渲染等下游应用。

**创新点**:  
提出结构化、动画兼容的 3D 动物表示：跨数据集共享规范空间、一致拓扑和 UV 参数化；设计 UV 对齐毛发图，将毛干几何编码到表面规范域，实现显式毛发重建并与变形/模拟兼容；在统一前馈架构中联合预测规范几何、纹理和毛发；通过程序化数据生成管线提供多物种、多外观且对齐的大规模监督。

**方法**:  
将输入图像提升到共享 canonical space，在一致拓扑和 UV 参数化下进行建模；采用统一 feed-forward 架构联合预测 canonical geometry、texture 和 fur；使用 UV-aligned fur map 在 surface-aligned canonical domain 中编码 strand geometry；通过 procedural data generation pipeline 生成具有对齐几何、纹理和毛发的大规模训练数据。

**结果**:  
在合成和真实世界数据集上的实验表明，该方法具有较高的重建质量和跨动物类别的泛化能力。论文未在摘要中给出具体数值指标，但强调其结构化表示可直接支持动画、姿态迁移、毛发编辑和仿真兼容渲染等下游应用。

**相关性与影响**:  
该工作对单图可动画 3D 动物重建、结构化可编辑资产以及毛发建模与仿真具有重要意义。它针对现有隐式/松散结构化表示难以绑定和编辑、参数化动物模型难以捕捉纹理与毛发外观的问题，为动画、游戏、VR/AR 和数字内容创作等领域的可动画动物资产生成提供了新思路。

---

### 6. GLOSS: Geometric Local Self-Similarity Learning for Faithful Reference-Guided Texture Fill **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2608.25461](https://arxiv.org/abs/2608.25461)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2608.25461)
- **作者**: Chenyue Cai, Anita Hu, James Lucas et al. (5 authors)
**评估**: 该论文专注于3D形状的纹理生成与填充，属于图像/全模态生成范畴。方法利用几何自相似性和几何-纹理相关性，训练形状特定的局部纹理生成模型，并支持艺术家交互控制，具有明确的技术创新。实验对比了强基线，并通过Blender插件获得了专业纹理艺术家的积极反馈，表明其实用性和质量。该方向在计算机图形学中具有重要价值，非小众或低质量工作。

**核心贡献**:  
论文提出 GLOSS，一种面向三维纹理填充的几何局部自相似学习方法，通过从单一三维形状和已有图像模型先验中学习形状特定的局部纹理生成与补全模型，实现参考引导的纹理迁移与填充。该方法不依赖大规模三维纹理数据集，而是利用几何自相似性和几何-纹理相关性，将任意参考图像逐块迁移到目标物体表面。作者还展示了该模型在艺术家可控性、PBR 材质泛化以及 Blender 插件实用反馈方面的优势。

**创新点**:  
核心创新在于提出局部、形状特定的纹理生成与补全范式：不同于依赖大规模三维数据与全局引导的方法，GLOSS 利用几何自相似性和几何-纹理相关性，通过几何感知的参考块注意力机制，实现显式艺术家控制下的参考引导纹理填充与局部修复。

**方法**:  
方法从已有图像生成模型先验和单个三维形状中训练形状特定的局部纹理生成与补全网络；该网络以一组几何感知的参考图像块为引导，通过注意力机制学习几何与纹理之间的对应关系，并以逐块 inpainting 方式将任意新参考纹理迁移到完整目标物体纹理上。模型还支持局部几何条件纹理修复，并泛化到 PBR 材质和未见网格。

**结果**:  
在纹理生成质量上，GLOSS 相比强图像条件纹理生成基线取得更优或相当的效果；能够将任意新参考迁移到完整目标物体纹理，支持艺术家选择参考引导的局部纹理修复，并泛化到 PBR 材质和未见网格。作为 Blender 插件进行试用时，多位三维纹理专业人员在可控性、实用性和创作辅助方面给出了积极反馈。

**相关性与影响**:  
该工作表明局部纹理生成是一种有前景的研究方向，可减少对大规模三维纹理数据集的依赖，并为艺术家提供更灵活、交互式和可控的纹理创作流程。其方法对参考引导纹理填充、三维内容创作、材质迁移以及实际 DCC 工具集成具有潜在影响。

---

### 7. Albedo Estimation via Latent Bridge Matching **⭐⭐⭐⭐** (相关度: 85%, 质量: 0.8)

- **arXiv ID**: [2609.09884](https://arxiv.org/abs/2609.09884)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09884)
- **作者**: Carme Corbi, David Serrano-Lozano, Javier Vazquez-Corral et al. (4 authors)
**评估**: 该论文研究基于Latent Bridge Matching的固有图像分解与反照率估计，属于生成模型在图像分解/图像生成领域的应用，最接近Image_Video_Omni_Generation类别。论文提出新的LBM架构，通过像素重建损失增强物理一致性，利用LBM高效推理，并引入阴影条件提升泛化性；扩展版本进一步对阴影估计器进行反照率条件化，在五个真实和合成数据集上与SOTA方法对比。方法有明确创新，实验较充分，具有较高参考价值。

**核心贡献**:  
本文提出基于潜空间桥匹配（Latent Bridge Matching, LBM）的白化（albedo）估计方法，旨在解决本征图像分解中物理一致性不足、推理计算成本高和泛化能力有限三大问题。该方法通过像素重建损失增强物理一致性，利用LBM的低成本推理提升效率，并引入阴影条件（shading conditioning）改善跨数据集泛化。扩展版本进一步将阴影估计器条件化于预测白化，从而提升重建保真度，并在五个真实与合成数据集上与当前最优IID方法进行了对比。

**创新点**:  
首次将潜空间桥匹配（LBM）用于白化估计，构建了兼顾物理一致性、低成本推理与跨数据集泛化的新型架构；同时提出对阴影估计器进行白化条件化，以进一步改善重建质量。

**方法**:  
采用LBM-based架构进行白化估计；通过像素重建损失强制物理一致性；利用LBM固有的低推理成本提升效率；引入阴影条件提升泛化；在扩展版本中，将阴影估计器本身条件化于预测白化，形成相互促进的重建流程。

**结果**:  
在五个真实和合成数据集上将最佳模型与当前最优IID方法进行基准比较；实验表明LBM能有效缓解物理一致性、推理效率和泛化性问题，且阴影估计器条件化于预测白化可进一步提升重建保真度。摘要未提供具体数值指标。

**相关性与影响**:  
该工作为基于生成模型的本征图像分解和白化估计提供了新的高效、物理一致且泛化更强的技术路线，对图像编辑、重光照、风格迁移、逆渲染等相关领域具有潜在推动作用。

---

### 8. FlowCPO: A Unified Divergence View of Preference Alignment for Flow Models **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.09905](https://arxiv.org/abs/2609.09905)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09905)
- **作者**: Yansen Han, Shengyi Liao, Peng Sun et al. (7 authors)
**评估**: 该论文研究流模型（flow models）和扩散模型的偏好对齐，属于生成模型的训练与优化方向，核心应用是图像/视频生成（如GenEval、OCR评测），因此最契合 Image_Video_Omni_Generation 类别。虽有DPO/knowledge distillation相关概念，但本质是对生成模型的偏好优化，而非通用大模型蒸馏或训练基础设施。质量方面：论文提出了基于散度的统一框架和FlowCPO离线前向KL目标，具有理论贡献（证明前向KL被对比流匹配损失上界、非负性等），并在GenEval/OCR上取得优于FlowDPO的结果（0.84/0.87 vs 0.81/0.74），方法有创新性且实验较充分。不足在于域外结果混合、部分指标不如RFT，泛化性有待验证，故质量评分为0.75，属于较高质量工作。

**核心贡献**:  
论文从散度视角统一了流模型与扩散模型偏好对齐中的在线强化学习和离线偏好优化方法，并提出离线前向KL目标FlowCPO，无需在线采样即可同时利用偏好与非偏好样本。理论证明在线性插值与正则条件下，前向KL目标可由对比式流匹配损失上界，从而得到固定数据上的可处理代理目标。实验表明FlowCPO在域内设置下优于FlowDPO等基线，但域外设置下结果混合。

**创新点**:  
提出统一的散度框架来组织Flow/Diffusion模型的偏好对齐方法；提出FlowCPO这一离线前向KL目标，避免在线rollout并同时使用正负偏好样本；证明其目标可由对比式流匹配损失上界，且损失非负，而简化FlowDPO的有符号回归损失可能无下界。

**方法**:  
通过散度视角分析在线RL与离线偏好优化的关系；针对流模型设计离线前向KL目标FlowCPO；在线性插值假设和显式正则条件下，将前向KL目标转化为对比式流匹配损失的可行代理，从而在固定偏好数据上优化，无需从当前模型重新采样。

**结果**:  
在域内设置中，FlowCPO在CFG 3.0下取得平均GenEval 0.84和OCR 0.87，高于FlowDPO的0.81和0.74；在域外设置中结果混合，取得最佳GenEval，但在若干指标上奖励分数低于RFT。

**相关性与影响**:  
该工作为流模型和扩散模型的偏好对齐提供了统一的理论视角，阐明了在线与离线方法之间的联系，并给出无需在线采样的高效离线对齐方案。其理论分析与实验结果表明FlowCPO在生成模型偏好优化中具有潜在价值，尤其对文本到图像等需要偏好对齐的生成任务有参考意义。

---

### 9. View-Structured Conformal Prediction for 3D Gaussian Splatting **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2609.10307](https://arxiv.org/abs/2609.10307)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10307)
- **作者**: Junzheng Chu, Bin Pan, Zhenwei Shi
**评估**: 该论文研究3D Gaussian Splatting（3DGS）新视角合成的结构化不确定性量化，属于3D/图像生成范畴，最契合Image_Video_Omni_Generation类别。方法上提出View-Structured Conformal Prediction，将预校准尺度分解为空间形状与视图难度因子，并提供有限样本有效性保证，具有明确技术创新。实验充分：在13个真实场景与Mip-NeRF 360上验证，相比像素池化校准（61.4%）提升视图事件覆盖率至91.7-92.0%，宽度相比常数尺度降低22.1%，单模型接近十模型集成效果，含统计显著性检验（p=0.0225），并测试不同骨干与FPS（216-280 FPS），结论可靠。属于3DGS不确定性认证的细分方向，受众相对专业但应用价值明确，非水文，质量较高。

**核心贡献**:  
3D Gaussian Splatting (3DGS) renders novel views in real time, but an uncertainty heatmap does not certify that a rendered view meets a certain prediction coverage. We treat novel-view synthesis as st...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 10. DensePol: Dense-Angle Polarization Dataset for Learning-Based Polarimetric Vision **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.09359](https://arxiv.org/abs/2609.09359)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09359)
- **作者**: Param Sangani, Ahmad Moori, Erik Blasch et al. (5 authors)
**评估**: 该论文的核心贡献是构建高角度冗余的RGB-偏振数据集（DensePol，180个偏振方向、2018对图像），并提出基于确定性扩散模型的RGB到偏振生成框架（含循环AoLP表示和局部DoLP精修），本质上是图像到图像/物理属性图的生成任务，因此归为Image_Video_Omni_Generation最相关。质量方面：数据集构建有实质创新（DoT采集替代DoFP，角度稳定性显著提升，AoLP偏差从13.36°降至2.21°），方法结合扩散生成与针对偏振特性的表示设计，并有下游表面法线估计实验支撑，属于中等偏上质量工作。但偏振视觉属于相对细分的视觉子领域，受众和应用面较窄，且缺乏与主流生成任务的广泛对比，因此质量评分适中。

**核心贡献**:  
该论文提出了 DensePol，一个基于 Division-of-Time 采集的高冗余 RGB-偏振数据集，包含 180 个 1° 间隔的全分辨率分析器方向以及 2,018 对 RGB-偏振图像。论文还提出了一个确定性的基于扩散的 RGB 到偏振预测框架，结合循环 AoLP 表示和局部 DoLP 细化器，用于提升偏振预测与下游表面法线估计。实验表明，密集角度采样显著提高了偏振稳定性，并将 AoLP 偏差从 13.36° 降低到 2.21°。

**创新点**:  
构建了高角度冗余的 DoT RGB-偏振数据集 DensePol，提供 180 个全分辨率分析器方向、1° 间隔采样以及保留的角度测量和拟合残差；同时提出了结合循环 AoLP 表示与局部 DoLP 细化器的确定性扩散式 RGB-to-polarization 学习框架。

**方法**:  
采用 Division-of-Time 采集方式，在 180 个分析器方向上以 1° 间隔获取全分辨率偏振图像，形成 2,018 对 RGB-偏振数据，并保留角度测量与拟合残差。在方法上，使用确定性扩散框架从 RGB 预测偏振，引入循环 AoLP 表示处理角度周期性，并使用局部 DoLP 细化器提升偏振参数估计质量。

**结果**:  
DensePol 的密集角度采样将 AoLP 偏差从 13.36° 降低到 2.21°。实验显示，该数据集与所提方法在偏振预测和下游表面法线估计任务上均取得改进。

**相关性与影响**:  
该工作为学习型偏振视觉提供了更高保真度的监督数据，缓解了传统 DoFP 数据集角度冗余有限及插值和瞬时视场误差问题，有望推动基于 RGB 的偏振预测、材质与反射分析以及表面法线估计等相关研究。

---


---

## 🧠 大模型蒸馏与压缩

### 1. One Loop, Two Gains: Can Active Learning win the Lottery for Free? **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.10311](https://arxiv.org/abs/2609.10311)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10311)
- **作者**: Benedikt Tscheschner, Eduardo Veas, Marc Masana
**评估**: 该论文将迭代幅度剪枝（彩票假设）与深度主动学习结合，提出I&P方法，在主动学习重训练循环中几乎零成本地获得稀疏模型。这属于模型压缩/剪枝范畴，明确符合Distillation类别。论文方法新颖，跨多种采集函数、架构和数据集进行了充分实验，且解决了主动学习的计算瓶颈，具有实际参考价值。

**核心贡献**:  
论文提出 Improve & Prune (I&P)，将迭代幅度剪枝嵌入深度主动学习的每轮重训练循环中，几乎不增加额外成本。它研究了在主动学习非稳态数据机制下能否免费获得彩票中奖票，并证明可在高达95%稀疏度下保持与稠密模型相当的精度。该方法还能缓解每轮重训练和对未标注池进行采集打分两个计算瓶颈。

**创新点**:  
发现并利用池式主动学习的迭代重训练循环与迭代幅度剪枝的计算结构同构，将剪枝整合进主动学习每轮重训练中，从而把中奖票的发现作为主动学习流程的副产品。

**方法**:  
在每轮主动学习采集新标签并重训练模型时，同步执行幅度剪枝，形成 Improve & Prune (I&P)；跨多种采集函数、架构族和图像分类数据集验证，并包含主动微调场景。

**结果**:  
I&P 在每个主动学习迭代产生稀疏可部署模型；在稀疏度高达95%时，其精度与稠密对应模型相当，即获得中奖票；同时缓解每轮模型重训练和未标注池采集打分两大计算瓶颈。

**相关性与影响**:  
连接彩票票假设与深度主动学习两个此前独立研究的范式，为大规模模型和大未标注池场景下降低主动学习计算成本、提升实用性提供新思路。

---

### 2. Video-MOPD: Multi-Teacher On-Policy Distillation for Video Understanding **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.09300](https://arxiv.org/abs/2609.09300)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09300)
- **作者**: Zhenxin Qin, Peng Shi, Cong Han et al. (6 authors)
**评估**: 该论文核心贡献是 Multi-Teacher On-Policy Distillation (MOPD)，通过多教师在线策略蒸馏整合视频理解领域（时序定位、通用理解、STEM推理）的互补能力，并辅以 Reliability-Aware Informative Sampling 采样策略，属于典型的知识蒸馏/大模型压缩范畴。方法具有明确创新点（多教师路由反馈监督学生轨迹、可靠性感知采样），实验覆盖多种视频理解基准并开源模型权重，作者具备相关研究背景，实验较充分，参考价值较高。虽应用落点在视频理解方向，但技术路线聚焦蒸馏，非小众垂直领域，故判定为较高质量论文。

**核心贡献**:  
论文提出 Video-MOPD-8B，一个面向视频理解的开源权重模型，通过针对视频时序定位、通用视频理解和视频 STEM 推理三个核心领域进行强化学习优化，并利用多教师在线策略蒸馏统一互补能力。模型在多个视频理解基准上取得同规模模型中的 SOTA 表现。

**创新点**:  
提出多教师在线策略蒸馏（MOPD），通过路由教师反馈监督学生模型在线生成的轨迹，从而整合不同领域专家知识；同时引入可靠性感知信息采样（RAIS），优先选择教师监督一致可靠且师生性能差距大的样本，提升蒸馏效率与效果。

**方法**:  
首先针对视频时序定位（VTG）、通用视频理解和视频 STEM 推理三个核心领域分别进行强化学习优化，获得具备互补能力的教师模型；然后采用 MOPD 对学生模型在线生成的轨迹进行多教师路由监督与蒸馏；最后结合 RAIS 采样策略筛选高质量、高信息量的训练样本，训练得到 Video-MOPD-8B。

**结果**:  
在覆盖通用视频理解、时序定位、视频推理和视频 STEM 任务的综合基准上，Video-MOPD-8B 在同等规模现有模型中达到 state-of-the-art 性能，并实现多任务协调且全面的能力提升。模型权重已在 Hugging Face 开源。

**相关性与影响**:  
该工作为视频理解中多能力联合优化困难的问题提供了可扩展的多教师在线蒸馏与可靠性采样方案，对强化学习、知识蒸馏、视频多模态理解及开源视频大模型的发展具有重要参考价值和潜在影响。

---

### 3. Beyond One-Size-Fits-All: Sample-Adaptive Strategy Routing for Vision Token Pruning in MLLMs **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.10346](https://arxiv.org/abs/2609.10346)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10346)
- **作者**: Haiji Liang, Pengfei Zhou, Zhenglin Wan et al. (6 authors)
**评估**: 该论文研究多模态大模型中的视觉token剪枝，并提出轻量级路由策略自适应选择剪枝方案以降低推理成本，属于大模型压缩/剪枝与轻量化部署方向，因此归为Distillation最合适。方法具有明确创新点：揭示样本级剪枝策略互补性，并设计plug-and-play的VIP-Router，不修改原剪枝算法或模型权重，仅引入极少可训练参数。实验覆盖剪枝敏感基准，报告了显著的相对提升，并验证了跨backbone与未见基准的泛化性，整体实验较充分、贡献清晰，质量较高。

**核心贡献**:  
该论文指出，现有视觉 token 剪枝方法通常对所有输入采用统一的固定剪枝策略，忽略了不同样本之间可能存在的最优策略互补性。为此，作者提出 VIP-Router，一种轻量级视觉剪枝路由器，能够根据每个输入自适应选择最适合的剪枝策略，并允许在剪枝不利时回退到全 token 推理。实验表明，该方法在剪枝敏感的视觉感知基准上持续优于最佳固定策略，并具有即插即用和跨模型泛化能力。

**创新点**:  
核心创新在于将视觉 token 剪枝从“一刀切”的固定策略转变为样本自适应策略路由：通过低成本视觉与文本特征预测每个输入在指定剪枝率下最合适的候选剪枝策略，同时保留全 token 推理选项，且不修改底层剪枝算法或模型权重。

**方法**:  
VIP-Router 是一种轻量级 VIsion Pruning Router，以低成本的视觉和文本特征为条件，为每个输入在给定剪枝水平下选择预测最优的剪枝策略；当预测剪枝不利时，可选择全 token 推理。该方法即插即用，仅引入约 0.017% 主干参数量的可训练参数。

**结果**:  
在专门构建的剪枝敏感视觉感知基准 VTC-Bench Group A 上，VIP-Router 在所有压缩率下均优于最佳固定策略基线，平均准确率相对提升 26.9%，考虑实际 token 成本后的平均效用相对提升 22.0%。此外，该方法在不同 MLLM 主干上有效，并在未见基准上取得一致增益。

**相关性与影响**:  
该工作揭示了固定剪枝策略评估中平均准确率掩盖的样本级策略互补性，为 MLLM 视觉 token 剪枝提供了新的样本自适应路由范式，有望降低多模态大模型推理成本，同时提升剪枝敏感任务上的性能和跨模型泛化能力。

---

### 4. LinearMask-GS: Stable-Mask Importance Pruning for Compact 3D Gaussian Splatting **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.10095](https://arxiv.org/abs/2609.10095)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10095)
- **作者**: Donghun Ryu, Minhyeok Lee
**评估**: 该论文面向3D Gaussian Splatting的冗余基元剪枝与紧凑化，核心是模型压缩/剪枝方法，属于Distillation（大模型蒸馏与压缩）范畴，而非生成方法本身。论文指出了现有learned-mask剪枝中Gumbel-Sigmoid激活导致掩码分布双峰化的问题，并提出LinearMask-GS以线性增量激活保持稳定的单峰掩码分布，从而更可靠地进行重要性排序与剪枝。方法有明确的问题动机和技术改进，在Mip-NeRF 360上给出了压缩比与渲染质量结果，实验相对充分，整体质量较好。

**核心贡献**:  
本文针对3D高斯泼溅（3DGS）中因自适应致密化产生大量冗余高斯基元而导致存储开销过大的问题，指出已有学习掩码剪枝方法LP-3DGS使用Gumbel-Sigmoid激活时，掩码值会在重要性排序稳定前迅速两极分化，形成不可靠的双峰分布。作者提出LinearMask-GS，用线性增量激活替代Gumbel-Sigmoid，使掩码训练过程中保持中等置信度并形成稳定的单峰分布，从而更可靠地剪枝冗余高斯。

**创新点**:  
识别出LP-3DGS等学习掩码剪枝范式中Gumbel-Sigmoid激活导致掩码过早双峰化、重要性排序不可靠的关键局限，并提出LinearMask-GS：以线性增量激活替代Gumbel-Sigmoid，使掩码值在训练期间维持中间置信区域，产生稳定且与重要性一致的单峰掩码分布，实现更紧凑的3DGS表示。

**方法**:  
在3DGS的每个高斯上引入可学习掩码以标识并剪除冗余基元。不同于LP-3DGS使用陡峭的Gumbel-Sigmoid激活将掩码快速推向0或1，LinearMask-GS采用线性增量激活，在掩码训练窗口内让掩码值保持在中置信度区间，避免过早二值化，从而稳定重要性排序并据此剪枝。

**结果**:  
在Mip-NeRF 360数据集上，相比3DGS和LP-3DGS分别实现3.6倍和1.6倍的高斯数量压缩，同时保持或提升渲染质量。户外场景中，高斯数量从2.18M降至1.36M，实现1.6倍压缩，PSNR提升0.38 dB，SSIM提升0.025，LPIPS降低0.029。

**相关性与影响**:  
该工作为3DGS的紧凑化与剪枝提供了新的掩码激活设计思路，能显著降低存储与渲染开销，同时维持或改善新视角合成质量，对实时神经渲染、3D场景压缩和高效3D高斯表示等方向具有重要参考价值。

---

### 5. Low-Rank Prompt Learning for Vision-Language Models with Fixed-Token Bases **⭐⭐⭐** (相关度: 72%, 质量: 0.8)

- **arXiv ID**: [2609.09462](https://arxiv.org/abs/2609.09462)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09462)
- **作者**: Tanvir Muntakim Tonoy, Sajjad Ghiasvand, Mahnoosh Alizadeh et al. (4 authors)
**评估**: 该论文研究视觉-语言模型（CLIP）的提示学习，通过低秩分解将提示矩阵 P=BA 参数化，将可训练参数从 md 降至 r(m+d) 甚至 rd，核心目标是参数高效微调与轻量化适配，与 Distillation 类别中的模型压缩、轻量化部署方向最相关（而非生成内容或训练推理基础设施）。论文创新点明确：发现 token 侧基矩阵 B 无需学习，固定的高斯基/正交基/随机基即可与全可训练分解持平，并给出提示因子非对称性与更新空间维度分析、收敛性保证。实验覆盖七个 few-shot 基准与两个 CLIP 主干，结论有支撑。方法虽属参数高效微调范畴，理论分析有一定深度，但整体创新偏向对已有低秩/PET 思路的验证性扩展，影响力有限，故质量评分为中等偏上。

**核心贡献**:  
This paper studies whether the dense prompt matrix learned by CoOp for CLIP adaptation is over-parameterized. It factorizes the prompt matrix as a low-rank product P = BA, reducing trainable parameters from md to r(m+d), and further to rd when the token-side factor B is fixed. Experiments show that low-rank prompts match or improve dense CoOp across few-shot benchmarks, and that fixing B to Gaussian, orthogonal, SVD-derived, or even random bases while training only A performs on par with fully trainable factorization.

**创新点**:  
The main innovation is a low-rank prompt-learning framework for vision-language models that fixes the token-side prompt basis rather than learning it. The paper identifies a prompt-factor asymmetry and a local update-space dimension gap to explain why fixing B is much less restrictive than fixing A, and provides a smoothness-only convergence guarantee for optimizing A over a fixed B. It further shows that a source-trained B is no better than a random one in this setting.

**方法**:  
The method replaces the dense CoOp prompt matrix P with a factorized form P = BA, where B is the token-side factor and A is the embedding-side factor. It trains the low-rank factors instead of the full matrix, optionally fixing B to Gaussian, orthogonal, SVD-derived, or random bases and learning only A. The authors evaluate this approach on seven few-shot benchmarks with two CLIP backbones, and provide theoretical analysis of prompt-factor asymmetry, local update-space dimension, and convergence for optimizing A with fixed B.

**结果**:  
Across seven few-shot benchmarks and two CLIP backbones, low-rank prompts match or improve dense CoOp while using far fewer trainable parameters. The clearest gains appear on low-shot base-to-new generalization. Fixing the token-side factor B to a Gaussian, orthogonal, SVD-derived, or random basis stays on par with the fully trainable factorization, and a source-trained B offers no advantage over a random one. The abstract reports no specific numerical performance values.

**相关性与影响**:  
The work matters for efficient adaptation of large vision-language models because it shows that prompt learning can be drastically parameter-reduced without sacrificing performance. It suggests that the embedding-side coefficients carry the adaptation while the token basis can simply be fixed, simplifying prompt design and training. The theoretical insights into prompt-factor asymmetry and convergence also provide guidance for future parameter-efficient fine-tuning methods.

---

### 6. RouteBridge: Reliability-Routed Bidirectional Distillation Between Neural Radiance Fields and 3D Gaussian Splatting **⭐⭐⭐** (相关度: 68%, 质量: 0.7)

- **arXiv ID**: [2609.09606](https://arxiv.org/abs/2609.09606)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09606)
- **作者**: YuanHang Wang, Xin Cao
**评估**: 该论文的核心贡献是 NeRF 与 3DGS 之间的双向知识蒸馏框架（teacher-student 式监督迁移），提出基于可靠性的逐射线路由机制来动态选择教学方向，属于典型的跨表示知识蒸馏/监督迁移范畴，因此最贴合 Distillation 类别。虽然涉及 3DGS/NeRF 的 3D 表示，但其方法本质是蒸馏方向的选择与监督信号传递，而非 3D 生成本身。质量方面：方法有明确创新点（可靠性估计器、renderer-independent 接口、动态路由），在 mip-NeRF 360 与 DTU 上给出定量结果（28.56/28.77 dB，LPIPS 0.207），并提供了消融实验验证自适应路由与几何射线目标的贡献，实验相对充分，对 3D 表示蒸馏方向有参考价值；但评测场景偏单一（静态场景、少量视图）、提升幅度有限，属中等质量工作。

**核心贡献**:  
RouteBridge is a bidirectional distillation framework between NeRF and 3DGS that selects the teaching direction per ray rather than fixing one representation as the global teacher. A reliability estimator combines photometric residuals with representation-specific geometric evidence to route supervision from NeRF to 3DGS, from 3DGS to NeRF, or to abstain, using a renderer-independent interface for color, opacity, and normalized depth transfer.

**创新点**:  
Per-ray adaptive bidirectional routing with an abstention option, powered by a reliability estimator that integrates photometric residuals and representation-specific geometric evidence, avoiding error propagation from a globally fixed teacher and enabling renderer-independent knowledge transfer without shared features or point correspondence.

**方法**:  
The method estimates per-ray reliability by combining photometric residuals with geometric cues specific to NeRF and 3DGS, then routes supervision accordingly: NeRF-to-3DGS, 3DGS-to-NeRF, or no supervision. A renderer-independent interface transfers color, opacity, and normalized depth between representations without requiring shared features or point correspondences.

**结果**:  
On mip-NeRF 360, RouteBridge achieves 28.56 dB for the NeRF export and 28.77 dB for the 3DGS export. The 3DGS export improves over 3DGS by 1.56 dB and over NeRF-GS by 0.45 dB while reducing LPIPS to 0.207. On static three-view DTU, it obtains 21.12 dB. Ablations show that both adaptive routing and geometric ray targets contribute to the improvement.

**相关性与影响**:  
The work addresses a key limitation of cross-representation distillation by avoiding globally fixed teacher supervision, which can propagate local reconstruction errors. Its adaptive bidirectional routing and renderer-independent transfer have potential impact on novel view synthesis, 3D reconstruction, and hybrid NeRF-3DGS pipelines, offering more robust distillation across complementary representations.

---


---

## ⚙️ 训练推理基础设施

### 1. Why Is Video Still So Expensive? A Survey of Inference-Efficiency Mechanisms in Video and Audiovisual LLMs **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.10355](https://arxiv.org/abs/2609.10355)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10355)
- **作者**: Killian Steunou, Yannis Tevissen, Mounîm A. El Yacoubi
**评估**: 这是一篇关于视频与音视频大语言模型推理效率机制的系统综述，重点分析帧采样、模态编码、token 压缩、LLM 预填充与解码等推理瓶颈和加速方法，并整理精度-成本对比。主题直接属于训练/推理基础设施中的推理加速、显存优化和部署效率，而非生成模型本身或蒸馏压缩。作为综述，它提供了较系统的文献梳理、统一比较视角和开源仓库，对相关领域有参考价值。

**核心贡献**:  
该综述系统梳理了视频与音视频大语言模型（VideoLLMs）中的推理效率机制，旨在降低随帧数和上下文长度增长的计算与内存开销。论文按流水线阶段组织方法，覆盖帧采样、模态编码、连接器级 token 压缩以及 LLM 预填充与解码，并汇总了在统一宿主模型和输入协议下的准确率-成本对比。作者还指出了音视频效率与标准化评估方面的研究空白，并维护了相关资源库。

**创新点**:  
首次以推理效率为核心，对视频及音视频 LLM 的效率优化机制进行端到端、按流水线阶段分类的系统综述；强调将文献报告的准确率-成本结果与异构跨论文证据区分开，并识别音视频效率与标准化评估的空白。

**方法**:  
采用文献综述与 taxonomy 构建方法，分析帧采样、模态编码、连接器级 token 缩减、LLM 预填充和解码等瓶颈；按方法作用的流水线阶段组织，涵盖 2022 年末以来的 VideoLLMs 以及仍被当前流水线使用的早期帧采样和视觉编码器机制；在共享宿主模型和输入协议下汇总准确率-成本比较。

**结果**:  
作为综述，论文未报告单一模型的实验数值，而是综合了在参数数量、每输入 FLOPs、延迟、内存以及视觉和音频 token 数量上取得具体降低的方法；在可用情况下汇总了统一宿主模型和输入协议下的准确率-成本对比，并区分了异构跨论文证据。

**相关性与影响**:  
该工作有助于理解和选择面向实时、移动和资源受限场景的视频/音视频 LLM 推理加速方案，为后续研究提供分类框架、效率-精度权衡视角和评估标准化方向，并推动音视频效率这一相对空白领域的发展。

---

### 2. TRACE: Trajectory-robust Admission with Evidence Ordering for Efficient GUI Agents **⭐⭐⭐⭐** (相关度: 85%, 质量: 0.8)

- **arXiv ID**: [2609.10297](https://arxiv.org/abs/2609.10297)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10297)
- **作者**: Yuhao Wang, Mu Qiao, Xindong Zhang et al. (6 authors)
**评估**: 该论文针对GUI智能体在推理过程中因累积高分辨率截图而导致的延迟和内存问题，提出了一种无需训练的视觉token剪枝框架。核心贡献包括轨迹鲁棒准入、覆盖感知证据排序、嵌套token顺序以及单调KV收缩，属于推理加速和显存优化范畴，因此最符合Training_Inference_Infra类别。论文方法具有明确的技术创新（不可逆剪枝决策、嵌套排序、增量KV收缩），实验覆盖六个GUI基准和多种模型，验证充分，作者虽未明确但工作扎实，质量较高。GUI智能体是当前热门方向，不属于小众领域。

**核心贡献**:  
该论文提出TRACE，一种面向GUI智能体的免训练视觉令牌剪枝框架，用于在轨迹推进过程中降低高分辨率截图带来的推理延迟和内存开销。TRACE将剪枝视为不可逆的准入决策，通过排序与保留原生视觉令牌来兼顾未来可用性、多样性和空间覆盖，并支持预算变化下的单调收缩与轨迹内复用。

**创新点**:  
核心创新在于提出轨迹鲁棒的准入与覆盖感知证据排序机制：结合与查询无关的布局交互先验、指令相关性和特征新颖性对视觉证据排序，同时预留部分预算给屏幕分布的原生视觉令牌以修复空间覆盖；由此形成嵌套令牌顺序，使保留证据可随预算单调收缩，并通过单调KV收缩将退役帧逐步压缩为紧凑会话状态，避免重复视觉编码或剪枝。

**方法**:  
TRACE是一种免训练框架。它首先利用布局导出的、与查询无关的交互先验，联合指令相关性和特征新颖性对视觉令牌进行排序，以评估潜在未来效用和多样性；然后保留一定比例的原生视觉令牌以维持全屏可操作区域覆盖；最终生成嵌套令牌顺序，使不同预算下的保留集合具有包含关系。配合单调KV收缩，已退役帧被增量式压缩为会话状态，从而在整个GUI轨迹中复用视觉证据并减少重复计算。

**结果**:  
论文在六个GUI基准和多种模型上进行了大量实验，验证了TRACE在紧预算条件下的有效性。摘要未给出具体数值指标，但强调其能够在降低推理延迟和内存使用的同时保持对未知未来目标的可用性。

**相关性与影响**:  
该工作对GUI智能体、多模态大模型推理加速和视觉令牌剪枝具有重要意义。它将缓存复用下的剪枝不可逆性问题形式化，并提出可随预算单调收缩且轨迹内可复用的证据排序与KV收缩方案，为高分辨率、长轨迹GUI任务中的高效推理提供了新思路。

---

### 3. PACE: Perceived-Latency-Aware Cascading Service Routing and Filler Control for QoE-Efficient Retrieval-Augmented Dialogue Serving **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2609.10372](https://arxiv.org/abs/2609.10372)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10372)
- **作者**: Lin Huang, Yujuan Tan, Weisheng Li et al. (6 authors)
**评估**: 该论文聚焦于检索增强对话服务的推理部署优化，核心是降低感知首响应延迟（PTFR）、级联路由、语义缓存准入与填充控制，属于推理加速/服务基础设施范畴，因此归为 Training_Inference_Infra。方法上有联合路径-填充控制器、波动感知缓存准入等机制创新，并在真实人形机器人销售服务上部署，75k 请求的实测数据（P95 延迟、调用量下降 94%、陈旧回答 86%→0%）提供了较充分的实证支撑，且首次量化了填充-回答冲突风险，具备一定工程参考价值。但该方法偏向特定服务系统与工程优化，理论通用性和适用范围相对有限，创新点属于系统层面的组合优化而非突破性方法，因此质量评分中等偏好（0.68）。

**核心贡献**:  
本文提出PACE框架，面向检索增强对话服务，将感知首响时间（PTFR）形式化为QoE目标，并在质量与成本约束下最小化该指标。与现有级联路由、语义缓存或自适应检索工作不同，PACE联合控制回答来源选择与等待窗口填充内容。该系统已部署于人形机器人销售服务中，并验证了其在真实负载下的QoE优化效果。

**创新点**:  
首次将感知首响时间PTFR作为检索增强对话服务的QoE优化目标，并联合设计级联路由、路径填充控制和缓存准入机制；同时首次在部署服务中量化填充答案与真实答案之间的冲突风险。

**方法**:  
PACE结合三种机制：负载自适应级联路由器，用于动态选择回答来源；联合路径-填充控制器，在等待窗口内控制填充内容以减少调用与冲突；波动感知缓存准入，用于降低过期答案。还引入门控规则，保证控制器性能不劣于基线，并将暴露风险限制在一个保持周期内。

**结果**:  
在75k CarQA请求上，级联路由在P95将纯LLM的PTFR减半（c16下0.29s vs 0.53s）；自适应控制器达到0.41s P95，在高负载下以同等质量优于RAG 2.4倍；填充控制器减少94%调用且零冲突；波动感知准入将过期答案从86%降至0%。

**相关性与影响**:  
该工作对检索增强生成、对话系统服务化、QoE优化和边缘/机器人部署具有重要参考价值，为在质量、成本和延迟约束下提升实际服务体验提供了可落地的路由、填充与缓存协同控制方案。

---

### 4. Elastoformer: Enabling Dynamic Adaptivity via Elastic Model Transformation **⭐⭐⭐** (相关度: 78%, 质量: 0.7)

- **arXiv ID**: [2609.10018](https://arxiv.org/abs/2609.10018)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10018)
- **作者**: Sudaksh Kalra, Dolly Sapra
**评估**: 该论文提出 Elastoformer 框架，将常规神经网络转换为可运行时动态伸缩的弹性网络（Elastic NN），用于边缘设备上根据动态的计算预算、延迟、功耗和内存约束进行弹性推理，属于推理加速、部署基础设施与运行时自适应的范畴。相比 bag-of-models 需要维护多个独立模型，其单模型多模式切换方案对边缘部署有实际工程价值。实验显示计算 FLOPs 降低最高 85%、延迟降低 50%、内存降低 76%，并具备跨 ViT 与 CNN 的架构无关性，且开源了代码，实验支撑较为充分。方法思路（弹性/可切换子网络）在思想上有一定工程贡献，但核心概念（类似 slimmable/elastic network）并非全新，理论创新有限，故质量评为中上水平。综合判断属于高效推理与部署基础设施方向，予以保留。

**核心贡献**:  
该论文提出 Elastoformer，一个将常规神经网络转换为弹性神经网络（Elastic NN）的框架，以支持边缘设备上的实时弹性推理。它通过单一模块化模型在运行时动态切换多种工作模式，从而适应变化计算预算，避免维护多个独立模型的“模型集合”开销。

**创新点**:  
核心创新在于用单个可弹性变换的模型替代传统 bag-of-models 方案，实现运行时动态自适应推理，并且架构无关，可同时适用于 Vision Transformers 和 CNNs。

**方法**:  
通过弹性模型变换将常规神经网络转换为 Elastic NN，使其在运行时根据延迟、功耗、内存等约束动态切换不同操作模式；采用模块化设计，在不管理多个独立模型的情况下适应边缘设备的动态计算预算。

**结果**:  
实验表明，该框架可实现最高 85% 的计算 FLOPs 降低、50% 的延迟降低和 76% 的内存开销降低，并在 Vision Transformers 与 CNNs 上验证了架构无关性。

**相关性与影响**:  
该工作对边缘 AI 和动态自适应视觉模型部署具有重要意义，为在资源波动环境下高效运行 DNN 提供了统一、可扩展的解决方案，有望推动实时计算机视觉在边缘设备上的实用化。

---

### 5. Isotropic Embedding Perturbations for Robust Vision Language Encoders **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.10292](https://arxiv.org/abs/2609.10292)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10292)
- **作者**: Hyesong Choi, Daeun Kim, Song Park et al. (8 authors)
**评估**: 该论文提出 Aether——一种在嵌入空间进行扩散式随机扰动（alpha-mixing）的数据增强方法，用于提升视觉语言编码器的鲁棒性与多模态对齐。它属于训练方法/训练流程优化范畴（数据增强作为训练正则化手段），因此最贴近 Training_Inference_Infra。方法具有一定创新点（从输入空间增强转向嵌入空间各向同性正则化），动机清晰，并在多种架构与识别任务上给出一致增益，实验相对充分，有实际参考价值。不足之处在于方法本身较为简单（plug-in 式改造），且更偏向通用训练技巧而非基础设施层面的系统创新，故质量评为中等偏上。

**核心贡献**:  
论文提出 Aether，一种在嵌入空间中施加各向同性随机扰动的简单插件式数据增强方法，旨在突破传统像素级增强组合的性能饱和问题。该方法通过受控的 alpha-mixing 进行扩散式扰动，在保持语义一致性的同时平滑表征，从而提升视觉语言编码器的鲁棒性。实验表明，Aether 在多种架构和识别任务上均优于 CutMix、Mixup、DropPath 和 RandAug 等先进增强组合，并在多模态对齐中表现突出。

**创新点**:  
将数据增强从输入空间转移到嵌入空间，提出 Aether：一种基于受控 alpha-mixing 的扩散式嵌入扰动，能够提供各向同性正则化且保持语义一致性，避免激进像素操作破坏跨模态对齐。

**方法**:  
Aether 是一种即插即用方法，在嵌入空间中对特征施加扩散风格的随机扰动，通过受控 alpha-mixing 实现温和而有效的扰动。其灵感来自语言模型中的特征空间扰动和生成式预训练中的图像退化，目标是在不破坏细粒度结构信息的前提下平滑表征。

**结果**:  
在多种架构和多个识别任务上，Aether 相比结合 CutMix、Mixup、DropPath 和 RandAug 的先进配方取得一致提升，这种改进幅度在现代增强替代方案中较为罕见。尤其在多模态对齐方面，Aether 明显优于传统像素空间增强方法。

**相关性与影响**:  
该工作为视觉语言编码器提供了一种新的嵌入空间增强轴，有助于解决像素级增强组合饱和与跨模态对齐脆弱的问题。其即插即用特性与稳定各向同性正则化信号对鲁棒多模态表征学习及相关领域具有潜在重要影响。

---


---

## 🧠 Agent 相关内容

### 1. Show-Harness: Just a VLM Agent Can Play Robots **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.10522](https://arxiv.org/abs/2609.10522)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10522)
- **作者**: Yanzhe Chen, Zechen Bai, Zhijun Cao et al. (10 authors)
**评估**: 该论文聚焦于利用视觉语言模型（VLM）作为具身智能体来控制机器人，核心贡献是 Show-Harness——一个将VLM的语义理解与机器人动作连接的紧凑语义接口，属于典型的Agent方向（具身智能体、机器人控制）。工作具有明确的技术创新：提出离散语义动作单元与具身特定解释器分离的设计，使闭源前沿VLM实现零样本机器人控制，并支持小规模开源VLM低成本微调；同时提出GUMI实现基于GUI的跨具身演示采集。实验涵盖跨任务、跨具身、跨环境的泛化验证，与代表性agentic及VLA范式对比，论证充分。该方向并非小众垂直领域，具有较高的通用性和实际参考价值，方法新颖且实验扎实，因此判定为高质量论文。

**核心贡献**:  
论文提出 Show-Harness，一种 Embodied Harness，通过紧凑的语义接口将 VLM 的意图映射为机器人动作，使 VLM 能够直接“玩”机器人。它既支持闭源前沿 VLM 的零样本机器人控制，也支持小规模开源 VLM 仅用少量 GPU 小时微调后低成本部署。作者还提出 GUMI，将同一语义动作空间扩展到基于 GUI 的示范采集，从而无需专用遥操作硬件即可跨本体采集数据。

**创新点**:  
核心创新是 Show-Harness 语义动作接口：向 VLM 暴露离散语义动作单元，并由本体特定解释器确定性地落地为局部机器人动作，同时让 VLM 直接负责细粒度物理决策。该接口统一支持零样本闭源 VLM 控制、低成本开源 VLM 适配以及 GUMI 的 GUI 示范采集，实现跨任务、跨本体、跨环境的泛化。

**方法**:  
方法上，Show-Harness 将机器人控制抽象为 VLM 可自然推理的离散语义动作空间，并用 embodiment-specific interpreters 将这些语义动作确定性地转换为具体机器人的本地动作。GUMI 则把相同语义动作空间扩展到 GUI 操作示范采集，使人类或智能体可以通过 GUI 而非专用遥操作硬件来“玩”机器人并收集数据。

**结果**:  
大量实验表明，配备 Show-Harness 的 VLM 智能体在任务、本体和环境之间具有稳健泛化能力，并优于代表性的 agentic 和 VLA 范式。结果还显示，无需增加模型容量或进行昂贵的本体特定预训练，即可从基础 VLM 中释放出显著的具身能力。

**相关性与影响**:  
该工作对具身智能和机器人学习领域具有重要意义，提供了一种不依赖额外模型容量或昂贵本体预训练即可复用基础 VLM 的通用接口范式。它有望降低机器人控制与示范采集的门槛，推动跨本体泛化、零样本控制和低成本部署的研究与应用。

---

### 2. VLX-VR: An Agentic-Aware Video Reasoning Model **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2609.09985](https://arxiv.org/abs/2609.09985)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09985)
- **作者**: Sheng Li, Peng Liu, Qianqian Zhang et al. (4 authors)
**评估**: 该论文提出 VLX-VR，一个具备 agentic 能力的视频推理模型，核心是 Think–Memory–Observation 循环：模型在每一步自主决定所需证据、调用 read_memory/write_memory、整合 Observation 并判断是否终止输出。其关键创新在于将智能体式的自适应证据获取、记忆读写与终止决策引入视频推理，并通过强化学习训练，这与 Agent 类别（自主决策、工具/记忆调用、多步推理）高度契合，而非单纯的生成或蒸馏。质量方面：在 MINERVA 基准上取得 78.79% 的 SOTA 准确率，跨时长准确率方差仅 2.97 pp²，并给出推理轨迹一致性（96.20%）与答案-证据双重满足率（75.80%）等细粒度分析，实验较充分、结论可信，作者具备多模态推理研究背景。不足之处在于尚未开源、缺乏与其他主流基线的大规模对比，且计数、状态变化、因果与空间感知等仍是短板，故质量评分中等偏上，属高质量但非顶尖工作。

**核心贡献**:  
本文提出 VLX-VR，一种具备智能体感知能力的视频推理模型，旨在通过 Think–Memory–Observation 循环实现自适应的多模态证据获取与推理。该模型在每一步判断所需证据、调用记忆读写操作、整合观察结果，并决定继续推理或输出答案。在 MINERVA 基准上，VLX-VR 取得了 78.79% 的准确率，并展现出跨视频时长的稳定表现。

**创新点**:  
将视频理解建模为智能体式的 Think–Memory–Observation 推理循环，使模型能够主动获取、写入和利用记忆中的多模态证据，而非依赖固定视频上下文和单次前向推理；并通过强化学习训练证据获取、记忆使用和终止决策。

**方法**:  
VLX-VR 在视频推理框架中逐步运行：判断所需证据，调用 read_memory 或 write_memory，纳入返回的 Observation，并决定继续推理或生成任务输出。模型使用包括视频和智能体轨迹在内的多模态数据进行训练，并采用强化学习学习证据获取、记忆使用和推理终止策略。

**结果**:  
在 MINERVA 上，VLX-VR 在所比较模型中达到最优性能，准确率为 78.79%；在原始三个时长分组上的准确率分别为 76.70%、78.73% 和 80.92%，跨时长准确率方差为 2.97 pp²。在正确回答的样本中，96.20% 的推理轨迹与 MINERVA 参考推理轨迹及其描述的证据一致；在所有评估样本中，约 75.80% 同时满足答案正确和证据 grounded 轨迹标准。计数、状态变化、因果推理和空间感知仍是挑战。

**相关性与影响**:  
该工作推动了视频理解从静态上下文、单次推理向智能体式多模态证据获取与记忆推理转变，对视频推理、多模态大模型、强化学习驱动的工具/记忆调用以及可解释推理轨迹评估具有重要参考价值，并展示了跨时长稳定推理的潜力。

---

### 3. No Free Checker: A Survey of Verifiers for Robot Policies **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.09250](https://arxiv.org/abs/2609.09250)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09250)
- **作者**: Yang Wan, Xihang Yue, Zhirui Liu et al. (10 authors)
**评估**: 该论文综述了机器人策略（vision-language-action policies）的验证器（verifiers），涵盖成功检测器、奖励模型、运行时监控、安全过滤器和时序逻辑规范等。这本质上属于智能体（Agent）领域，涉及agent的评估、奖励建模与训练，与Agent的决策、验证、安全等核心主题高度相关，因此归入Agent类别。论文提出了'可用性（Availability）vs 可信性（Credibility）'的对比框架，覆盖约150个验证器并总结九项可检验指标，具备一定的概念贡献和参考价值，故判定为较高但非顶级质量。需要说明的是，机器人策略验证属于相对垂直的应用方向，受众相对有限，且作为综述缺乏原创方法创新，因此质量评分处于中等偏上水平。

**核心贡献**:  
该论文系统综述了约150个机器人策略验证器，涵盖成功检测器、奖励模型、运行时监控器、安全过滤器和时序逻辑规范等。作者提出可用性（Availability）与可信性（Credibility）两个核心维度，按判断来源将验证器分为人类、规则与形式化、学习与预训练、模型内在四类，并揭示二者之间的普遍权衡：可用性越高，可信性通常越低。论文进一步梳理了验证器自身的验证方式，并提出九项使验证器主张可检验的指标。

**创新点**:  
首次以“可用性—可信性”双轴统一审视机器人策略验证器，提出“没有免费检查器（No Free Checker）”的核心论点；建立按判断提供者划分的四类验证器分类体系；总结验证器自身有效性的三类证据，并提出九项可检验指标及未来验证器构建方向。

**方法**:  
文献综述方法，调研约150个验证器；从成本、判定到达早晚、判定密度衡量可用性，从可博弈性、自利性和任务指示性衡量可信性；按人类验证器、规则与形式化验证器、学习与预训练验证器、模型内在验证器四类进行比较分析；梳理验证器验证手段，包括与人类标签一致性、所训练策略性能、奖励黑客下的行为表现。

**结果**:  
该论文为综述，未报告新的实验性能指标。核心发现是跨四类验证器普遍存在可用性与可信性权衡：判定越便宜、越早、越密集，其高分对任务成功的指示性通常越弱，且越容易被博弈或自利利用。论文提出九项可检验指标，并指出验证器研究仍需填补的方向。

**相关性与影响**:  
对视觉-语言-动作策略评估与训练、机器人安全、奖励建模、运行时监控、形式化方法和强化学习等方向具有重要参考价值。该工作提供统一分析框架，帮助研究者选择和设计验证器，并强调验证器本身必须被验证，从而推动机器人策略验证研究向更可检验、可复现和可信的方向发展。

---

### 4. Strangers to Themselves: What Language Models Say About Themselves Is Generic **⭐⭐⭐** (相关度: 60%, 质量: 0.8)

- **arXiv ID**: [2609.09899](https://arxiv.org/abs/2609.09899)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09899)
- **作者**: Phil Blandfort, Urja Pawar
**评估**: 该论文研究语言模型对自身行为（如是否屈服于反驳、误用工具或在压力下撒谎）的预测能力，通过九项行为评估构建预测检验，并设置对照组剥离“自我”因素。核心发现是模型的自我报告主要反映对'AI助手'的一般性理论加上自利偏差，而非真正的自我知识。这与Agent行为评测和自我认知方向相关，因此归入Agent类别。质量方面：方法设计严谨（预测检验+对照组+多模型交叉对比），实验充分（九项行为评估、规模化前沿模型测试、微调实验），结论有明确实践意义，创新性较强，属于高质量工作。虽然严格来说更接近可解释性/安全分析，但可用类别中最贴近Agent行为评测。

**核心贡献**:  
本文把语言模型的“自我认知”转化为一个可量化的预测任务：在九项行为评估中测量模型在不同条件下的实际行为率，要求模型预测这些比率，并与去除“自我”指向的对照问题进行比较。结果表明，模型的直接自我报告几乎不具备预测力（r = +0.04），其预测能力主要来自对“一般AI助手会如何行为”的通用理论以及一种偏向美化的第一人称偏差，而非对自身特权的了解。

**创新点**:  
将“模型自我知识”从主观问答改造为行为预测的实证检验，并设计了三类关键对照：（1）把问题中的“你”替换为“一般有能力的AI智能体”；（2）用其他模型对自身的回答来预测目标模型；（3）对模型自身行为记录做微调。由此首次系统区分了“真正的自我知识”与“关于AI助手的通用理论 + 自我美化偏差”，并检验了模型规模与第一人称框架各自的独立效应。

**方法**:  
对九个行为评估维度，先在多种条件（如是否受到反驳、是否被施压等）下测量目标模型的真实行为发生率，再让模型预测这些比率，并设置去除自我指向的对照提问。比较对象包括：直接自我报告、展示具体题项后的自我预测、关于“一般AI智能体”的同题项提问、其他模型的自我回答，以及经过自身行为记录微调的模型。此外分析模型规模（前沿规模）与第一人称措辞对预测精度和报告方向的影响。

**结果**:  
（i）直接自我报告预测力很弱（r = +0.04），即使向其展示具体题项也仅提升至 +0.24；而关于“一般有能力AI智能体”的同题项提问达到 +0.28，且其他模型对自身的回答对目标模型的预测力不亚于其自我回答。（ii）前沿规模并未显著改变这一模式，预测增益并非自我特异，更像是更准确的“AI助手行为理论”。（iii）第一人称框架有一个稳定效应：使报告朝美化方向偏移，相对通用智能体提问更低估有害行为。（iv）基于自身行为记录的微调可教会狭窄的自我预测，但同时改变了被预测的行为本身，且收益无法广泛迁移。

**相关性与影响**:  
该研究对AI对齐、模型评估与可解释性具有重要警示意义：依赖模型自述来评估其安全行为（如是否会屈从压力、滥用工具或撒谎）是不可靠的，因为自述主要反映通用刻板印象与自我美化偏差。它为构建更可信的模型行为评估方法、理解自我报告偏差的机制，以及设计不依赖模型自省的监控手段提供了实证基础和明确的实践建议。

---


---

## 🌍 World Model 相关内容

### 1. Programmable World Model **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.9)

- **arXiv ID**: [2609.10540](https://arxiv.org/abs/2609.10540)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10540)
- **作者**: Zheng-Hui Huang, Guixu Lin, Jiacheng Lin et al. (11 authors)
**评估**: 该论文聚焦于可编程世界模型，将世界状态演化与视觉观测生成解耦，通过自然语言指令生成可执行程序来维护持久化全局世界状态，并利用状态增强的3D OBB作为中间表示驱动预训练视频模型渲染。工作属于世界模型方向，而非单纯的图像/视频生成或基础设施优化。论文提出明确的方法框架、可玩游戏交互能力、长时程一致性生成，并构建了CombatStateBench基准，取得94% Count Accuracy和98% State Accuracy，实验支撑较充分，创新性和参考价值较高，不属于低质量、小众或水文论文。

**核心贡献**:  
本文提出 Programmable World Model，将世界状态演化与视觉观测生成解耦，使视频世界模型能够维护持久状态并执行可编程规则。该方法通过自然语言到可执行程序的转换，控制实体状态与状态转移，并以轻量引擎维护显式全局世界状态。结合状态增强的 3D OBB 中间表示与预训练视频生成模型，支持可玩游戏、实体级控制和长时程一致生成。

**创新点**:  
核心创新在于将世界状态演化与视觉渲染分离：用可执行程序显式定义实体状态和转移规则，由轻量引擎维护包含离屏实体和非视觉属性的持久全局状态；并引入状态增强 3D 定向包围盒（OBB）作为中间表示，与目标相机轨迹一起确定性地编译为像素对齐的时空条件信号，驱动预训练视频模型作为生成渲染器。

**方法**:  
方法包括：1）智能体将自然语言指令翻译为可执行程序，指定实体状态和状态转移规则；2）轻量引擎执行程序，更新并维护显式的持久全局世界状态；3）用状态增强 3D OBB 表示实体及其属性，并结合目标相机轨迹，确定性地编译为像素对齐的时空条件信号；4）预训练视频模型作为生成渲染器，根据条件信号生成视觉观测，从而连接显式状态与视觉生成。

**结果**:  
在作者提出的 CombatStateBench 基准上，该方法达到 94% Count Accuracy 和 98% State Accuracy，显著优于现有交互式视频世界模型，并支持连贯的长时程生成，验证了将显式状态演化与生成式渲染分离的有效性。

**相关性与影响**:  
该工作对交互式视频世界模型、可编程世界模拟和游戏生成具有重要意义。它通过分离状态维护与视觉渲染，提升了长时程一致性、实体级可控性和规则可编程性，并为评估可编程世界模型提供了 CombatStateBench 基准，有望推动持久、可交互、可编程的世界模型发展。

---

### 2. DUET-DINO: Simultaneous Cross-View World Modeling for Latent Planning in Robot Manipulation **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.10506](https://arxiv.org/abs/2609.10506)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10506)
- **作者**: Nisarga Nilavadi, Ralf Römer, Moritz Reuss et al. (8 authors)
**评估**: 该论文聚焦于机器人操作中的动作条件潜在世界模型，提出同时跨视角的世界建模方法用于7-DoF末端执行器控制与潜在规划，属于World_Model类别。方法具有明确创新：跨视图条件建模、结合侧视与腕部相机信息、支持完整7-DoF动作空间规划。实验覆盖reach、angled-reach、lift等任务，并在DROID和RoboArena数据集上训练，报告了具体成功率并验证了视觉分布偏移下的泛化能力。论文还比较了V-JEPA 2与DINOv3的预测表现，分析较充分。代码和模型将开源，对机器人世界模型与规划方向有实际参考价值，因此评为高质量。

**核心贡献**:  
Action-conditioned latent world models predict future visual representations, enabling zero-shot goal-conditioned robot planning and control. However, their predictions for fine-grained spatial and ro...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 3. Semigroup-JEPA: Latent Dynamics Consistency for Zero-Shot Physics Generalization **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.10464](https://arxiv.org/abs/2609.10464)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.10464)
- **作者**: Andy Zeyi Liu, Haoran Sun, Lucas Baker et al. (5 authors)
**评估**: 该论文明确属于世界模型（World Model）方向。论文提出 SemiGroup-JEPA，基于 JEPA（Joint-Embedding Predictive Architecture）世界模型框架，研究潜在动力学表示、物理规律泛化、预测与规划能力。核心贡献包括：通过 action-conditioning 将物理参数注入时序模型，联合训练编码器与预测器；设计不同引力场下的动力学任务评估分布外泛化；相比 DINO-WM 在开环预测误差降低2倍、3D机器人控制成功率提升2.5倍；并提出线性特征模型分离局部误差与递归放大误差，揭示了增益主要来自编码器学习到更好的特征。方法创新明确、实验设计合理（含2D数据集与3D机器人任务并训练独立扩散策略）、有理论分析支撑，作者提供了项目主页。属于世界模型领域有价值的工作，质量较高。

**核心贡献**:  
本文提出了 Semigroup-JEPA（SG-JEPA），通过将控制物理规律的参数以动作条件方式注入时间模型，并联合训练编码器与预测器进行自回归潜在滚动，从而提升世界模型的零样本物理泛化能力。作者设计不同引力场下的动力学任务评估分布外泛化，并发现关键增益主要来自编码器学习到更适合多步预测的动态特征，而非预测器本身。

**创新点**:  
将物理参数通过动作条件引入 JEPA 类世界模型，并利用多步自回归潜在滚动损失反向传播到编码器，使表征学习保留可供预测器向前传播且真正决定动力学的特征。

**方法**:  
在 LeWorldModel 框架上扩展为 SG-JEPA：向时间模型提供控制物理的参数，联合训练编码器和预测器，通过自回归 latent rollout 优化多步预测。设计不同引力场下的二维/三维动力学任务进行 OOD 评估，并训练独立 diffusion policies 用于三维机器人控制。此外提出线性特征模型分析局部 law-conditioned 误差与 rollout 递归放大。

**结果**:  
相比 DINO-WM，SG-JEPA 在二维数据集上将开环预测误差最多降低 2 倍，在三维机器人数据集上将控制成功率最多提升 2.5 倍。分析表明，大部分性能增益来自编码器学习到更好的特征，而非预测器学习到更好的动力学。

**相关性与影响**:  
该工作为 JEPA 世界模型学习物理规律和零样本泛化提供了系统评估与改进方法，强调了联合表征学习在多步潜在动力学预测中的核心作用，对基于世界模型的规划、控制和物理推理具有重要潜在影响。

---

### 4. Identifying Habit, Physics, and Nuisance in Robot World Models **⭐⭐⭐⭐** (相关度: 93%, 质量: 0.9)

- **arXiv ID**: [2609.09210](https://arxiv.org/abs/2609.09210)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09210)
- **作者**: Jinting Hang, Zhenhui Cai
**评估**: 论文研究机器人世界模型中的因果因子分解，提出结构因果模型与干预方法来区分操作者习惯、共享物理和观测噪声，并在 StackCube、DROID、RH20T 上验证低样本迁移与鲁棒性。该工作属于机器人世界模型/具身智能方向，有明确的方法创新和实验支撑，不属于图像视频生成、蒸馏或训练推理基础设施，也不是小众垂直应用。

**核心贡献**:  
Teleoperated demonstrations are often multimodal even when the underlying dynamics are nearly deterministic given the executed action. We argue that this multimodality typically mixes three factors--o...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 5. MotionBlind: Probing the Illusion of Motion Understanding in Video-LLMs **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.09528](https://arxiv.org/abs/2609.09528)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.09528)
- **作者**: Dhairya Bhatia, Bishoy Galoaa, Oliver Fritsche et al. (10 authors)
**评估**: 该论文研究 Video-LLM 对物理运动（速度、幅度、方向）的理解能力，并将其明确定位为 world model 的感知前端（'perceptual front end of world models'），直接对应世界模型必须预测的核心变量，因此最相关类别为 World_Model。论文虽非生成类工作，但围绕世界模型所需运动感知能力的评估展开，与 World_Model 主题高度契合。质量方面：提出了对比式基准 MotionBlind（自录视频、四问题配对、6.25% 随机下限），并对 8 个模型（6 开源 + 2 前沿）做了受控实验，系统控制视频有无、时序打乱、采样帧数（1–24 帧）与四种采样策略，实验设计严谨、结论有据（开源模型接近随机下限、打乱帧即崩溃、仅 Gemini3.1 Pro 通过），对世界模型监督/奖励/评估的可信度有实际参考价值。属较扎实的评测类工作，但方法为基准评测而非全新算法，创新性中等，故质量评分 0.72。

**核心贡献**:  
论文提出 MotionBlind，一个用于检验 Video-LLM 是否真正理解物理运动（速度、幅度、方向）的对比式基准，每个实例由两条仅在运动上不同的近似相同视频组成，并配以四个互补的 yes/no 问题，只有全部答对才算通过（随机基线为 6.25% IAcc）。作者对 6 个开源和 2 个前沿 Video-LLM 进行受控实验，发现开源模型几乎停留在随机水平且规模无益，去掉视频或打乱帧序会使性能归零或跌至随机，说明任务确实依赖有序视频，但模型仍无法读取运动。

**创新点**:  
首次系统性地揭示 Video-LLM 存在“运动盲”（MotionBlind）现象：模型能够识别场景中的物体与外观，却无法分辨同一动作的快慢、幅度与方向；同时提出了一个自录制、对比式、物理落地的运动理解基准，并设计了严格的四题全对评分（IAcc）与 6.25% 随机下限，可有效排除单帧、外观和纯语言等捷径，与 TimeBlind 基准形成互补。

**方法**:  
构建 MotionBlind 对比基准：每个实例为两条近乎相同、仅在运动（速度、幅度、方向）上存在差异的自录视频，每条视频配两道互补的 yes/no 问题，共四题，全部答对才计分，指标为 Instance Accuracy（IAcc，随机基线 6.25%）。在此基础上开展受控消融研究，系统变化是否提供视频、帧是否按正确时间顺序展示、以及帧采样方式（1 至 24 帧、四种选择策略），测试 6 个开源模型与 2 个前沿 Video-LLM。

**结果**:  
开源模型 IAcc 接近 6.25% 的随机下限，且模型规模增大并不能改善；移除视频输入后所有模型 IAcc 降为 0，打乱帧序后 IAcc 塌缩至随机水平，证明任务确实需要按序视频。增加帧数或采用更聪明的帧选择策略均无法缩小差距，因为它们只改变“看到哪些帧”，而不改变模型是否真正读取运动。总体仅 Gemini 3.1 Pro 通过基准，但即便它在速度维度上仍然失败。

**相关性与影响**:  
该工作对以 Video-LLM 作为世界模型感知前端的研究提出了重要警示：无法区分同一动作两种速度的模型，不足以作为世界模型的监督、奖励或评估来源，从而对视频理解评测、具身智能、机器人规划与多模态世界模型的可信度评估具有直接的推动与纠偏意义。

---


---

## 📊 统计信息

| 类别 | 论文数量 | 占比 |
|------|----------|------|
| 🎨 AIGC 相关内容 | 0 | 0.0% |
| 🖼️ 图像/视频/全模态生成 | 10 | 9.9% |
| 🧠 大模型蒸馏与压缩 | 6 | 5.9% |
| ⚙️ 训练推理基础设施 | 5 | 5.0% |
| 🧠 Agent 相关内容 | 4 | 4.0% |
| 🌍 World Model 相关内容 | 5 | 5.0% |
| 其他 | 71 | 70.3% |
| **总计** | **101** | **100%** |
