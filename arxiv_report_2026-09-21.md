# 📚 arXiv CS.CV 每日论文报告

**报告日期**: 2026-09-21  
**论文来源**: [arXiv CS.CV Recent](https://arxiv.org/list/cs.CV/recent)  
**关注论文数**: 34篇（每类别Top 10，经质量筛选）

> 注：每类别按大模型评估的相关性和质量排序，仅展示前10篇高质量论文。已自动过滤低质量和小众方向论文。

---

## 📑 目录

- [🎨 AIGC 相关内容](#aigc) (0篇)
- [🖼️ 图像/视频/全模态生成](#image_video_omni_generation) (10篇)
- [🧠 大模型蒸馏与压缩](#distillation) (6篇)
- [⚙️ 训练推理基础设施](#training_inference_infra) (4篇)
- [🧠 Agent 相关内容](#agent) (10篇)
- [🌍 World Model 相关内容](#world_model) (4篇)

---

## 🖼️ 图像/视频/全模态生成

### 1. Paint-Anything: Unified Any-Color Control for Image Generation and Editing **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.20816](https://arxiv.org/abs/2609.20816)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20816)
- **作者**: Ji Xie, Dewei Zhou, Xinyu Huang et al. (5 authors)
**评估**: 该论文聚焦于图像生成与编辑中的统一任意颜色控制（any-color control），核心贡献包括共享的hex-prompt接口、Paint-500K数据构建流程、纯色锚点监督策略，以及新提出的Any Color Benchmark（ACBench-T2I和ACBench-Edit）。这属于图像生成与编辑领域，因此归入Image_Video_Omni_Generation类别。质量上，论文提出了明确的方法创新（hex颜色接口+混合监督训练策略），构建了大规模数据集和新的评测基准，并在FLUX.2-4B上取得了显著提升（T2I +85.3%，Edit +28.3%），实验较为充分，具有实际参考价值。方法新颖且工程完整，非水文或小众垂直方向，质量较高。

**核心贡献**:  
Paint-Anything 提出了一种面向图像生成与编辑的统一任意颜色控制方法，用户可通过 24 位十六进制颜色值指定对象目标颜色。该方法基于对象级颜色监督学习共享的 hex-prompt 接口，并构建了 Paint-500K 数据管线和 ACBench 基准。实验表明，在 FLUX.2-4B 上显著提升了文本到图像生成和图像编辑中的对象级颜色保真度。

**创新点**:  
提出统一的 hex-prompt 接口，将任意 24 位十六进制颜色控制同时用于图像生成和编辑；构建 Paint-500K 对象级颜色监督数据管线；引入纯色锚点仅在高噪声时间步训练以弥补真实图像阴影导致的颜色标签不精确问题；提出 Any Color Benchmark（ACBench-T2I 和 ACBench-Edit）用于评估对象级 hex 颜色保真度。

**方法**:  
通过对象 grounding、感知颜色标注和编辑对合成构建 Paint-500K 数据集；训练模型学习共享的 hex-prompt 颜色控制接口；使用纯色锚点在高噪声时间步提供精确颜色监督，低噪声时间步则使用自然图像训练；在 FLUX.2-4B 上验证方法并设计 ACBench 基准评估生成与编辑任务中的对象级十六进制颜色一致性。

**结果**:  
在 FLUX.2-4B 上，Paint-Anything 相比基础模型将 ACBench-T2I 和 ACBench-Edit 分数分别提升 85.3% 和 28.3%；在对比方法中取得最高平均 CompColor 分数；消融实验支持所提出的训练配方。

**相关性与影响**:  
该工作推动了细粒度、对象级且可直接指定 24 位 hex 颜色的可控图像生成与编辑，统一了生成和编辑中的颜色控制范式；Paint-500K 与 ACBench 为后续任意颜色控制研究提供了数据与评测基础，对设计、内容创作和可控生成领域具有潜在应用价值。

---

### 2. Refinement Is Inherently Editable: Training-Free Prompt-to-Prompt Image Editing with Generative Refinement Network **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.20633](https://arxiv.org/abs/2609.20633)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20633)
- **作者**: Yulong Chen, Ziqian Zhang, Haoyu Zhang et al. (6 authors)
**评估**: 该论文研究text-guided图像编辑（prompt-to-prompt image editing），是典型的图像生成与编辑方向，属于Image_Video_Omni_Generation类别。方法上提出了基于生成式精炼网络（Generative Refinement Network）的免训练编辑框架RefineEdit，核心创新在于通过双分支概率差来定位可编辑位置与比特，并引入自适应空间冻结与有限比特锁定机制来稳定编辑过程，具有明确的方法创新。实验在PIE-Bench的九个编辑类别上评估，在背景保持（PSNR、LPIPS、MSE、SSIM）和CLIP分数上取得最优，实验较为充分。整体属于免训练图像编辑方向的有价值工作，方法清晰、有实际参考意义，但创新点属于已有编辑框架的组合与改进，故质量评分中等偏上。

**核心贡献**:  
论文提出 RefineEdit，一个无需训练的 prompt-to-prompt 图像编辑框架，基于 Generative Refinement Network 实现。其核心思想是通过二值图像码的全局细化，将编辑定位与内容生成耦合，使编辑证据能够随图像演化被重新评估。该方法在保持源图像无关内容的同时引入文本指定的编辑，并在 PIE-Bench 上取得领先的背景保持与 CLIP 对齐性能。

**创新点**:  
将编辑定位视为生成细化过程的内在可编辑部分，通过比较编辑分支与源分支对同一源采样比特的概率差异，动态选择可编辑位置和比特；无需额外训练、外部掩码或注意力控制。

**方法**:  
RefineEdit 从源图像的中间状态初始化编辑分支，复用其正在形成的布局。对同一源采样比特，比较两个分支分配的概率，并利用带符号差异选择可编辑位置与比特。被选中的比特跟随编辑细化，其余比特复制演化中的源状态。为稳定跨细化步骤的编辑，引入自适应空间冻结以限制不必要的掩码扩展，并使用有限比特锁定保持最近选中的比特可编辑。

**结果**:  
在 PIE-Bench 的九类编辑任务中，RefineEdit 在 PSNR、LPIPS、MSE 和 SSIM 上取得最佳背景保持分数，并在所评估方法中获得最高的整图 CLIP 分数和编辑区域 CLIP 分数。

**相关性与影响**:  
该工作为文本引导图像编辑提供了一种无需训练、无需外部掩码的 prompt-to-prompt 新范式，强调生成细化过程本身的可编辑性，有望推动更精确、内容保持更好的扩散/自回归图像编辑方法发展。

---

### 3. FlowSGS: Improving Flow Matching Priors for Inverse Imaging with Stochastic Interpolants **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.20769](https://arxiv.org/abs/2609.20769)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20769)
- **作者**: Tianao Li, Xinhui Qian, Emma Alexander
**评估**: 该论文聚焦于使用flow matching生成模型作为先验来解决计算成像中的逆问题，属于生成模型在图像逆问题中的应用，与图像生成/全模态生成领域高度相关。论文提出了FlowSGS方法，结合Split Gibbs Sampling和Stochastic Interpolants，在多个逆问题上达到SOTA，并首次在非线性逆问题（傅里叶相位恢复）上验证，具有明确的技术创新和充分的实验支撑，质量较高。

**核心贡献**:  
本文提出 FlowSGS，一种基于流匹配先验的后验采样方法，利用 Split Gibbs Sampling 将后验分解为似然步和先验步，以求解计算成像中的逆问题。该方法通过 Langevin 动力学采样似然步，并借助 Stochastic Interpolants 框架将预训练流模型集成到先验步中，避免了对线性前向模型和简化近似的依赖。实验表明，FlowSGS 在多种逆问题上达到最先进性能，并首次在基于流的逆求解器中验证了非线性傅里叶相位恢复问题。

**创新点**:  
主要创新在于将 Split Gibbs Sampling 与 Stochastic Interpolants 结合，构建基于流模型的后验采样框架，适用于非线性和非线性前向模型；提出使用 SI 反向时间 SDE 的先验步形式，并引入反向时间 SDE 的时间步校正技术，利用流先验的直线概率路径减少网络评估次数。

**方法**:  
FlowSGS 将后验分布分解为似然步和先验步：似然步采用 Langevin 动力学采样，先验步利用预训练流模型和 Stochastic Interpolants 的反向时间 SDE 进行采样。通过流先验的直线概率路径和针对反向时间 SDE 的时间步校正，降低先验步中的网络评估次数，并与已有即插即用方法建立联系。

**结果**:  
在多种逆问题上取得最先进性能，且先验步所需的网络评估次数少于即插即用扩散采样器；首次为基于流的逆求解器提供非线性逆问题（傅里叶相位恢复）的实验验证。

**相关性与影响**:  
该工作提升了流匹配先验在计算成像逆问题中的实用性，为非线性逆问题提供了新的后验采样思路，并有望推动高效、通用的即插即用生成先验在相关领域的发展。

---

### 4. CleanVideo: Adaptive Concept Erasure for Text-to-Video Diffusion Models **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.20267](https://arxiv.org/abs/2609.20267)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20267)
- **作者**: Junchi Liao, Hongji Li, Wenrui Zhou et al. (4 authors)
**评估**: 该论文聚焦于文本到视频扩散模型中的概念擦除（concept erasure），属于视频生成与扩散模型的安全/编辑方向，最契合 Image_Video_Omni_Generation 类别。方法上有明确技术创新：提出低维子空间干预结合三模态门控机制（时空视觉特征、时间步信号、文本语义），解决了视频中目标概念随帧和去噪步逐渐演变的难题，并非简单迁移图像方法。实验覆盖三个视频扩散模型，在帧级和视频级评估中优于现有基线，并考虑概念恢复攻击，验证较充分。作者论点清晰、贡献实质，非水文。质量上稍扣分是因属于概念擦除这一相对细分的安全方向，应用受众相对有限，但方法本身对视频生成领域具有参考价值。

**核心贡献**:  
本文提出 CleanVideo，一种面向文本到视频扩散模型的自适应概念擦除框架，能够在保留非目标内容和通用生成能力的同时，选择性去除不需要的视觉语义。该方法通过三模态门控机制进行低维子空间干预，自适应决定在何处、何时以及是否进行擦除，并在可定义时将目标内容引导至自然替代概念。

**创新点**:  
将概念擦除从图像扩展到视频，并针对视频中目标概念逐步出现、跨帧和跨去噪步变化的问题，提出由时空视觉特征、时间步信号和文本语义联合控制的三模态门控自适应低维子空间干预机制。

**方法**:  
CleanVideo 采用选择性擦除框架，在低维子空间中执行干预，并通过三模态门控机制联合处理时空视觉特征、时间步信号和文本语义，以判断干预的位置、时机和必要性。当目标概念存在清晰可定义的自然替代概念时，方法会将待擦除内容引导至这些替代概念，同时尽量保持非目标内容不变，从而减少固定干预带来的模糊、抖动和内容失真。

**结果**:  
在三个视频扩散模型上的实验表明，CleanVideo 能有效擦除目标概念，同时保持视觉保真度和时间一致性。在帧级和视频级评估中，以及在受保护流程保持完整时的概念恢复攻击下，该方法均优于现有基线。

**相关性与影响**:  
该工作对文本到视频生成的内容安全、版权保护和有害语义去除具有重要意义，为视频扩散模型中的可控概念擦除提供了新思路，并有助于推动更可信、更可控的视频生成技术发展。

---

### 5. Recency Forcing: Bridging the Long-Horizon Gap in Autoregressive Video Generation **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.19729](https://arxiv.org/abs/2609.19729)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19729)
- **作者**: Tri Cao, Hung Nguyen, Phong Nguyen et al. (4 authors)
**评估**: 该论文聚焦于自回归视频生成的长时程质量问题，属于图像/视频生成范畴。核心贡献在于识别出一种被忽视的训练-推理差异（KV eviction mismatch），并提出了基于位置响应分析（positional response）的 Recency Forcing 方法及 Biased Attention Reparameterization 重参数化技巧，使方法可零额外开销融入 FlashAttention。技术洞察新颖（perturbation-based sensitivity measure），方法设计有理论动机且兼顾 training-free 与 training-based 两种模式，在 VBench/VBench-Long 上验证了长时程生成质量的提升，实验较为充分。虽然涉及 KV cache 与推理效率，但其根本目标是提升视频生成质量而非基础设施优化，故归类为 Image_Video_Omni_Generation。整体方法清晰、贡献明确，属于高质量工作。

**核心贡献**:  
本文识别出自回归视频生成中长期退化问题的根源——KV eviction mismatch，即训练时所有上下文帧保留在KV cache中而推理时因显存限制被迫驱逐远距离帧所导致的训练-推理不一致。作者提出Recency Forcing方法，通过在注意力logits上施加与时间步相关的非正偏差（TRB）来渐进削弱远距离帧的影响，从而在不改变上下文长度和训练目标的前提下弥合这一差距。该方法支持免训练与基于训练两种模式，在VBench和VBench-Long上实现了无需额外推理开销的最优长时程生成质量。

**创新点**:  
首次提出并形式化'KV eviction mismatch'这一自回归视频生成中长时程退化的训练-推理不一致问题；提出基于扰动敏感度测量（位置响应 R(Δ, t_denoise)）的设计指导；引入Temporal Response Bias（TRB）在softmax前的注意力logits上施加时间步相关偏差，并给出精确重参数化Biased Attention Reparameterization（BAR），将偏差移出softmax从而以零开销复用FlashAttention。

**方法**:  
首先通过扰动分析定义位置响应 R(Δ, t_denoise)，量化上下文影响随时间的衰减规律及去噪步间的系统性变化；然后基于该响应设计Temporal Response Bias（TRB），对pre-softmax注意力logits施加非正、时间步相关的偏置，渐进降低远距离帧权重而非直接截断上下文；进一步提出Biased Attention Reparameterization（BAR）实现精确等价改写，使TRB可封装为标准FlashAttention调用；方法可免训练直接作用于推理，也可结合训练使用。

**结果**:  
在VBench和VBench-Long基准上取得当前最优（state-of-the-art）的长时程生成质量，且不增加额外推理开销。

**相关性与影响**:  
论文揭示了自回归视频生成中KV cache驱逐导致的训练-推理不一致这一被忽视的关键问题，为长视频生成提供了理论分析工具（位置响应）和高效工程方案（TRB+BAR），对长时程视频生成、注意力机制设计以及KV cache压缩/驱逐策略等相关研究具有重要的参考价值和潜在推动作用。

---

### 6. RGS: Reflection-aware Gaussian Splatting via Learning Geometry Continuity for Reflective Objects **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.19421](https://arxiv.org/abs/2609.19421)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19421)
- **作者**: Xiaobiao Du, Yida Wang, Cheng Bi et al. (5 authors)
**评估**: 该论文研究基于3D Gaussian Splatting的反射物体新视角合成，属于图像/视频/3D生成与渲染范畴，与Image_Video_Omni_Generation类别高度相关。技术上提出了基于物理的延迟渲染框架、跨视角形状一致性正则化（借助3D基础模型先验）以及反射感知致密化策略，针对反射区域表面塌陷和几何空洞问题进行了针对性改进，具有一定的技术创新性。实验声称达到state-of-the-art，方法完整。不足之处在于核心贡献是已有组件（基础模型先验、致密化）的组合与迁移，创新深度中等，且未提供绝对指标数据支撑。整体属于较高质量的工作，可作为反射物体神经渲染方向的有价值参考。

**核心贡献**:  
论文提出 RGS，一种基于物理延迟渲染的反射感知高斯泼溅框架，用于解决现有 3DGS 在反射区域表面塌陷、几何质量差和镜面高光渲染不佳的问题。该方法引入 3D 基础模型几何先验与跨视角形状一致性正则，并结合反射感知致密化策略，实现高质量反射物体新视角合成。大量实验表明其持续渲染高质量反射物体并达到当前最优性能。

**创新点**:  
主要创新包括：提出物理基础的延迟渲染框架 RGS 以准确建模镜面区域；利用强 3D 基础模型提供几何先验，并设计跨视角形状一致性正则化来保持反射区域几何连续性、减少表面塌陷与空洞；提出反射感知致密化策略，以捕捉不同视角下的镜面高光变化，从而提升新视角渲染质量。

**方法**:  
方法基于 3D Gaussian Splatting，构建物理基础的延迟渲染框架。首先利用强 3D 基础模型提供 3D 几何先验，并通过跨视角形状一致性正则化约束几何表面，使反射区域表面更平滑并减少几何空洞。然后设计反射感知致密化策略，针对反射区域在不同视角下的镜面变化进行高斯致密化，以更准确建模镜面反射并改善新视角合成结果。

**结果**:  
摘要指出大量实验证明 RGS 能持续渲染高质量反射物体，并在反射物体新视角合成任务上达到 state-of-the-art 性能，同时改善了反射区域的几何质量和镜面高光渲染效果。

**相关性与影响**:  
该工作对反射物体的三维重建与新视角合成具有重要意义，可推动 3DGS 在复杂反射场景下的几何建模和物理渲染能力。其结合 3D 基础模型先验、跨视角几何约束与反射感知致密化的思路，对 AR/VR、数字孪生、机器人感知和高质量内容生成等相关领域具有潜在影响。

---

### 7. GS-PI: An Optimization-Decoupled Appearance Decomposition Approach for Generating PBR Gaussian Assets **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2609.19907](https://arxiv.org/abs/2609.19907)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19907)
- **作者**: Jieting Xu, Rengan Xie, Zijian Huang et al. (6 authors)
**评估**: 该论文聚焦于3D高斯资产的可重光照PBR材质生成，属于3D内容/资产生成方向，与Image_Video_Omni_Generation（含3D生成、扩散模型）最为契合。方法上提出优化解耦框架，将PBR材质生成建模为3D点云上的几何条件扩散过程，并设计多尺度跨视角条件机制（全局语义先验+源锚定光度线索+绝对视角方向条件），在3D域直接操作保证了多视角一致性，避免了2D扩散的像素对应问题。相比既有逆渲染联合优化方法，避免了目标冲突导致的歧义和残余光照伪影，且无需代理网格。技术创新明确、思路清晰，属于高质量工作；但摘要未提供定量实验细节与消融，质量评分略作保守估计（0.78）。不属于医疗、遥感等小众垂直方向，也非水文。

**核心贡献**:  
GS-PI 提出一种优化解耦的外观分解框架，将 PBR 材质生成建模为 3D 点云上的几何条件扩散过程，从而从预训练 Gaussian Splatting 模型中生成可重光照的 PBR-GS 资产。该方法避免了传统联合逆渲染中光照与材质相互纠缠、目标竞争导致的多义性和残留光照伪影，并在 3D 域中操作以保证多视角一致性。

**创新点**:  
核心创新在于将 PBR 材质生成从逐场景联合光照/BRDF 优化中解耦，转而采用基于 3D 点云的几何条件扩散过程；引入多尺度跨视角条件机制，融合全局语义先验、源锚定光度线索和绝对空间学习视角方向条件，有效压缩多视角证据、缓解投影错位并防止高光烘焙进本征颜色。

**方法**:  
方法首先从预训练高斯模型中提取点云，然后通过条件扩散模型预测 PBR 属性，最后利用可微光栅化将预测属性蒸馏回高斯表示，得到完全可重光照的 PBR-GS 资产。其多尺度跨视角条件设计直接在 3D 域中整合全局语义、源视角光度信息和学习到的视角方向空间条件，避免了 2D 扩散方法中的像素对应问题，且不需要代理网格。

**结果**:  
摘要指出 GS-PI 在性能上优于近期逆渲染基线方法，能够生成完全可重光照的 PBR-GS 资产，并且无需代理网格。它用学习到的扩散过程加短时目标驱动蒸馏，替代了逐场景的联合光照/BRDF 优化。摘要未提供具体定量指标。

**相关性与影响**:  
该工作对逆渲染、基于高斯泼溅的 PBR 资产生成以及可重光照三维内容创建具有重要意义。它有助于将 Gaussian Splatting 更好地集成到 PBR 管线中，减少材质与光照分解的歧义和伪影，并为多视角一致的材质预测与重光照编辑提供新思路。

---

### 8. EliGSiR: Continual RGB-D Mapping with Gaussian Splatting under Bounded Compute **⭐⭐⭐** (相关度: 78%, 质量: 0.7)

- **arXiv ID**: [2609.20348](https://arxiv.org/abs/2609.20348)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20348)
- **作者**: Björn Ellensohn, Elmar Rueckert, Christian Rauch
**评估**: 该论文研究基于3D Gaussian Splatting的持续RGB-D建图（continual RGB-D mapping），核心是增量式、在线到达观测下的3D高斯重建，属于3D生成/重建范畴，最接近Image_Video_Omni_Generation类别。论文提出了三个针对性机制（Map-Guided View Scheduling、Load-Adaptive Fidelity、Targeted Geometry Growth）来处理受限算力预算下的建图问题，并在Replica、TUM RGB-D、ScanNet++及真实传感器序列上进行了充分实验，与SplaTAM、CaRtGS等基线对比，报告了量化的重建指标，具备明确的技术贡献和实验支撑，非水文。论文的贡献点（自适应视图调度、监督保真度、几何增长）具有针对性且论证清晰。整体质量尚可，但与前沿通用生成/大模型工作相比，影响面和创新度偏中等，属于较为专门的3D建图方向，故质量评分中等偏上。

**核心贡献**:  
该论文提出了 EliGSiR，一种在有限计算预算下进行持续 RGB-D 建图的 3D 高斯泼溅方法，能够在在线接收新观测的同时保留已重建区域。其核心贡献是通过动态调度优化预算，使建图过程在视图选择、监督分辨率和几何增长方面自适应调整，并在多个数据集和真实传感器序列上验证了效果。

**创新点**:  
提出面向持续 RGB-D 建图的负载自适应增量高斯泼溅框架，将优化预算控制与高斯表示增长解耦，并引入 Map-Guided View Scheduling、Load-Adaptive Fidelity 和 Targeted Geometry Growth 三个机制，使重建在持续采集过程中仍能高效利用有限计算资源。

**方法**:  
基于 3D Gaussian Splatting 构建持续建图系统：Map-Guided View Scheduling 根据当前地图状态过滤冗余新视图并重新考虑保留视图；Load-Adaptive Fidelity 根据当前建图负载动态调整监督分辨率，而非使用固定分辨率计划；Targeted Geometry Growth 将深度监督与高斯创建分离，仅在重复 RGB-D 观测表明存在缺失或错位结构处增加几何容量。方法在 Replica、TUM RGB-D、ScanNet++ 和真实 RGB-D 传感器序列上评估，同时考察最终重建和采集过程中的地图质量。

**结果**:  
在 TUM RGB-D fr3/long_office_household 上，使用与受控基线相同的地面真值建图位姿时，EliGSiR 达到 21.52 dB，而 SplaTAM 为 19.42 dB。在使用实时 ORB-SLAM3 位姿的跟踪位姿比较中，EliGSiR 在 155.5 秒内达到 23.02 dB，优于使用原生跟踪器的 CaRtGS（230.9 秒内 20.10 dB）。实验还表明，其自适应视图调度、监督保真度和几何增长机制能够改善可用建图预算的利用效率。

**相关性与影响**:  
该工作对持续在线 3D 重建、RGB-D SLAM、机器人感知和增强现实等需要有限计算资源的场景具有重要意义。它将 3D Gaussian Splatting 从封闭集观测和长优化调度扩展到持续建图设定，为在真实系统中平衡实时性、存储、计算预算与重建质量提供了新思路。

---

### 9. PACE: Precise AI Cinematic Expression: A Typed Specification for Script-Grounded Previsualization and Geometric Conformance **⭐⭐⭐** (相关度: 78%, 质量: 0.7)

- **arXiv ID**: [2609.19853](https://arxiv.org/abs/2609.19853)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19853)
- **作者**: Bing Duan, Qiang Guo, Linpu Li et al. (9 authors)
**评估**: 该论文提出PACE，一种用于脚本驱动的电影预可视化的类型化表示方法，核心是利用扩散模型生成分镜/画面（panels），并通过编译器将声明式规格转化为prompt和3D场景，再由相机求解器实现几何一致性。这本质上属于text-to-image/diffusion models在图像生成与可控生成方向的应用，因此最贴合Image_Video_Omni_Generation类别。方法上有明确的技术创新：类型化层级继承的规格表示、编译器、相机几何求解，以及对声明与生成结果逐字段的几何符合度量化（而非依赖模型判断）。实验包括11场景剧本和204个外部导演分镜镜头，提供了定量结果（如1.2%画幅宽度误差、头部高度比值等），实验较为充分且有实际参考价值，作者提供了开源代码。虽非颠覆性突破且整体仍属特定应用方向，但创新和方法支撑足够，故评为较高质量。

**核心贡献**:  
Between a screenplay and a film sits a planning problem that is spatial first: who stands where, and what a camera sees from where it stands. An image diffusion model asked for a shot in free text set...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 10. STAR: Structure-aware Test-time Adaptation for diffusion-based light field Reconstruction **⭐⭐⭐** (相关度: 78%, 质量: 0.6)

- **arXiv ID**: [2609.19747](https://arxiv.org/abs/2609.19747)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19747)
- **作者**: Wontae Choi, Ki Ryum Moon, Jae Young Lee et al. (5 authors)
**评估**: 该论文聚焦基于扩散模型的光场(Light Field)重建，利用预训练diffusion prior并针对测试样本拟合轻量适配器进行test-time adaptation，本质上属于扩散模型驱动的图像重建/生成范畴，因此归入Image_Video_Omni_Generation。方法上有一定创新性（首个面向FS→LF重建的测试时适配框架，适配空间-角度结构三要素），并在两/三焦面设置下取得SOTA且推理更快，实验相对充分。但光场重建属于计算成像中较为细分的应用方向，受众较小、通用性有限，整体质量中等偏上，未达到显著高影响力的水平。

**核心贡献**:  
论文提出STAR，一种面向基于扩散模型的光场重建的结构感知测试时自适应框架，用于从有限且含噪的焦栈测量中重建光场。针对每个测试光场，冻结预训练扩散先验，并通过拟合三个轻量适配器分别适应光场的空间-角度结构三要素：视图内空间细节、跨视图角度依赖和视差。该方法在二焦片与三焦片设置下优于现有SOTA，且推理时间短于需要测试时参数更新的方法。

**创新点**:  
首个从焦栈重建光场的测试时自适应框架；将光场空间-角度结构分解为视图内空间细节、跨视图角度依赖和跨视图视差三部分，并用三个轻量适配器在测试时联合适配；无需更新扩散先验，兼顾性能与效率。

**方法**:  
从有限含噪FS重建LF是高度病态逆问题。给定光学装置后，LF-to-FS成像几何固定，但每个场景的空间-角度结构变化，固定预训练先验难以最优捕捉测试LF结构。STAR对每个测试LF冻结预训练扩散先验，利用观测FS拟合三个轻量适配器，分别建模和适应视图内空间细节、跨视图角度依赖及跨视图视差，联合实现结构感知的测试时自适应重建。

**结果**:  
在二焦片和三焦片设置下均优于现有SOTA方法；推理时间短于那些需要测试时参数更新的方法。摘要未给出具体数值指标。

**相关性与影响**:  
该工作对光场重建、计算成像、扩散模型先验以及测试时自适应具有重要意义，可提升有限且含噪测量下的重建质量与效率，并为其他结构随测试样本变化的逆问题提供新思路。

---


---

## 🧠 大模型蒸馏与压缩

### 1. Enhanced Knowledge Distillation for Detection Transformer via Teacher Prediction Refinement **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.19964](https://arxiv.org/abs/2609.19964)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19964)
- **作者**: Yitong Xing, Yuhao Cheng, Yanping Li et al. (4 authors)
**评估**: 该论文聚焦于DETR目标检测模型的知识蒸馏方法，属于模型压缩/蒸馏方向，与Distillation类别高度匹配。论文针对现有DETR蒸馏方法忽视教师监督质量的问题，提出了Teacher Prediction Refinement Distillation (TPRD)即插即用模块，包含Positive Prediction Correction、Negative Prediction Suppression和Maximum Dark Knowledge Preservation三个组件，具有明确的技术创新点。在MS COCO和PASCAL VOC上的充分实验验证了方法的有效性和鲁棒性，并开源了代码。该工作针对边缘设备部署需求，具有实际应用价值。综合来看，方法有创新、实验充分、面向通用目标检测任务（非小众垂直领域），属于高质量论文。

**核心贡献**:  
本文针对DETR类目标检测器在知识蒸馏中忽视教师监督质量的问题，提出了一种即插即用的教师预测精炼蒸馏模块TPRD。该方法利用DETR分阶段预测中的非单调行为，在蒸馏前对教师预测进行精炼，以提供更准确、一致的监督信号。在MS COCO和PASCAL VOC上的实验验证了其有效性和鲁棒性。

**创新点**:  
首次指出DETR教师模型存在分阶段预测退化与负样本过度自信问题，并据此提出在蒸馏前精炼教师预测的TPRD框架；通过正预测校正、负预测抑制和最大暗知识保留三个组件，同时提升监督质量并保留非目标类关系。

**方法**:  
TPRD包含三个核心模块：Positive Prediction Correction (PPC) 从更早阶段恢复更准确的正预测，以校正后期退化的定位和分类信号；Negative Prediction Suppression (NPS) 抑制过度自信的负预测，避免其对学生模型产生误导性监督；Maximum Dark Knowledge Preservation (MDKP) 选择性精炼目标类logits，同时保留非目标类之间的暗知识关系。该模块可直接嵌入现有DETR蒸馏流程。

**结果**:  
在MS COCO和PASCAL VOC数据集上进行了大量实验，结果表明所提方法具有有效性和鲁棒性；摘要未给出具体性能数值，但强调TPRD能提升教师监督质量并改善DETR蒸馏效果。

**相关性与影响**:  
该工作为DETR类检测器的知识蒸馏提供了新视角，即从单纯对齐蒸馏点转向精炼教师监督本身，有助于推动高效目标检测模型在边缘设备上的部署，并对教师-学生蒸馏、DETR优化及暗知识保留等相关研究具有启发意义。

---

### 2. Cross-Architecture Foundation-Model Distillation for Edge Flood Segmentation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.7)

- **arXiv ID**: [2609.20441](https://arxiv.org/abs/2609.20441)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20441)
- **作者**: Fabian Schmalstieg, Karsten Mueller, Wojciech Samek
**评估**: 该论文的核心贡献是将3亿参数的Prithvi-EO-2.0地理空间基础模型蒸馏为0.7M参数的EfficientViT-B0学生模型，并结合量化感知训练与激活替换，最终部署到Jetson Xavier NX边缘设备上。跨架构知识蒸馏、teacher监督扩展无标注数据、INT8量化与边缘推理优化完全属于Distillation（大模型蒸馏与压缩）范畴，而非生成或基础设施方向。方法具有较强的可迁移性（teacher-student训练、量化部署），实验较为充分：包含多数据集(Sen1Floods11/STURM-Flood/WorldFloods-v2)对比、几何匹配对照实验、以及显存/延迟等部署指标。作者亦保持科学诚实，指出固定MNDWI阈值在两个外部基准上可与模型竞争，故将基准解读为泛化测试而非模型优越性证据。扣分点在于：应用领域偏窄（洪水/遥感分割垂直方向），真实性能增益在部分基准上有限，且蒸馏本身缺乏显著的理论创新，主要贡献偏工程集成与实证验证。因此属于中等质量、有一定参考价值的工作。

**核心贡献**:  
Geospatial foundation models can provide strong flood-segmentation performance, but their size limits deployment on memory-constrained edge hardware. We distill a 300-million-parameter Prithvi-EO-2.0 ...

**创新点**:  
待补充

**方法**:  
待补充

**结果**:  
待补充

**相关性与影响**:  
待补充

---

### 3. AI or Real: Detecting Partially Altered Videos Under Resource-Constrained Environments **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.7)

- **arXiv ID**: [2609.20263](https://arxiv.org/abs/2609.20263)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20263)
- **作者**: Tamoghna Chakraborty, Md Nurul Absur, Sourya Saha et al. (4 authors)
**评估**: 该论文的核心贡献是将 DINOv2-Base 教师模型蒸馏到轻量化的 MobileNetV3-Small 学生模型，用于边缘设备上的部分篡改视频检测。方法上采用温度退火软标签迁移、注意力多样性正则、帧级监督和残差特征适配器，属于典型的知识蒸馏与模型压缩/轻量化部署方向，因此归为 Distillation 类别。质量方面：方法有具体的技术组合与创新（针对场景切换误报和阈值失校准两个失败模式的针对性设计），实验在 55,393 样本测试集上进行了多假帧比例的评估，并报告了与教师模型的差距缩小比例、延迟和显存占用等实用指标，实验较为充分，具备边缘部署的参考价值。但 AUC 仅 0.766，绝对性能有限，且切入点（deepfake/篡改视频检测）应用方向相对聚焦，故质量评分为中等偏上。

**核心贡献**:  
本文提出一种面向边缘设备的轻量级全帧检测器，用于检测部分篡改的AI生成视频，无需人脸检测预处理。作者将DINOv2-Base教师模型蒸馏到冻结的MobileNetV3-Small学生模型中，并针对合法场景切换误报和纯真实类阈值校准问题设计专门策略。实验表明该方法在资源受限条件下显著缩小了与大型基础模型检测器的性能差距。

**创新点**:  
主要创新在于面向部分篡改视频检测的轻量级边缘部署方案：通过蒸馏将400M+参数基础模型的能力迁移到MobileNetV3-Small，同时引入针对部分篡改场景特有的两类失败模式的处理机制，即合法场景切换导致的误报和主导纯真实类上的阈值校准偏差。

**方法**:  
方法采用DINOv2-Base作为教师模型，冻结的MobileNetV3-Small作为学生模型，使用温度退火软标签迁移、注意力多样性正则化、帧级监督和残差特征适配器来适配ImageNet特征以检测伪造伪影。针对合法场景切换，使用视频内时序硬负样本；针对纯真实类阈值误校准，使用校准感知采样。检测器为全帧检测，无需人脸检测预处理。

**结果**:  
在包含55,393个样本、伪造帧比例从6.2%到31.2%的拼接测试集上，学生模型缩小了与DINOv2-Base教师模型之间58%的性能差距，AUC达到0.766。在RTX A4000上处理16帧片段的运行时间为3.65 ms，检查点大小为150.4 MB，满足边缘设备的内存和延迟预算。

**相关性与影响**:  
该工作对资源受限环境下的AI生成视频检测具有重要意义，推动了部分篡改视频检测从高资源基础模型向边缘可部署轻量模型的转变。其在准确率、延迟和模型大小之间的权衡，以及针对场景切换和校准问题的处理，对实际视频取证、内容审核和边缘安全应用具有潜在影响。

---

### 4. A Smaller Transformer in Your Transformer **⭐⭐⭐⭐** (相关度: 85%, 质量: 0.8)

- **arXiv ID**: [2609.20100](https://arxiv.org/abs/2609.20100)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20100)
- **作者**: Dhananjay Tomar, Marius Aasan, Andreas Kleppe et al. (4 authors)
**评估**: 论文提出Transformer-Within-Transformer (TWT)方法，通过将冗余层融合为学习代理层来减少参数和推理计算，属于模型压缩与轻量化部署范畴，与Distillation类别高度相关。方法包含形式化统一视角和实际效果验证，在自然图像和组织病理学任务上表现良好，具有一定创新性和实用价值。虽然涉及医疗垂直领域，但核心贡献是通用的Transformer压缩技术，受众较广，质量中上。

**核心贡献**:  
论文提出对视觉Transformer中逐层计算冗余的统一形式化视角，并引入Transformer-Within-Transformer（TWT），一种将连续冗余层融合为单个可学习代理层的后处理方法。TWT在减少参数和推理计算量的同时，在自然图像上以一半深度保持竞争力，并在多个组织病理学下游任务中匹配甚至超越原始基线。

**创新点**:  
统一形式化了块冗余问题，将冗余的几何结构与具体代理干预解耦；提出TWT后处理方法，把连续的冗余层组融合为一个学习得到的代理层，从而在不显著损失表达能力的情况下压缩模型并降低推理计算。

**方法**:  
首先分析Vision Transformers中局部相似的计算阶段，形式化深度方向的块冗余；然后识别连续冗余层组，并用单个可学习代理层替换这些层组，实现后处理式的层融合。该方法同时减少参数数量和推理计算量，并可应用于自然图像和组织病理学等下游任务。

**结果**:  
TWT在自然图像上使用一半深度即可与原模型保持竞争力；在多个组织病理学设置中，TWT匹配甚至优于原始基线；同时有效减少参数数量和推理计算量。

**相关性与影响**:  
该工作为Vision Transformer的深度冗余建模和高效压缩提供了新视角与实用方法，对模型加速、参数削减以及计算资源受限场景下的部署具有重要意义，尤其在组织病理学等专业领域展现出保持或提升性能的潜力。

---

### 5. GAPrompt++: Multi-Granular Geometry-Aware Point Cloud Prompt for 3D Vision Model **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.19716](https://arxiv.org/abs/2609.19716)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19716)
- **作者**: Zixiang Ai, Zhenyu Cui, Yufei Guo et al. (7 authors)
**评估**: 该论文聚焦于参数高效微调（PEFT），提出GAPrompt++方法用于3D点云视觉模型的高效适配，核心目标是在降低计算和存储成本的前提下完成下游任务迁移，这与Distillation类别中'模型压缩、轻量化部署、参数高效适配'的定义高度契合（PEFT常与知识蒸馏/压缩归为同一高效适配范畴）。方法上提出了Point Shift Prompter、Keypoint Prompter和Prompt Propagation三个组件，针对点云几何结构的细粒度与粗粒度特征进行建模，具有一定技术创新性；实验上声称在多个基准上达到SOTA并超越全量微调，仅需不到2%可训练参数，同时构建了基于3D Gaussian Splatting和MVS的两个更具挑战性的新基准，实验贡献较为充分。整体工作有明确的方法创新、可靠实验支撑和实际应用价值，属于高质量论文，故分类为Distillation并给予较高评分。

**核心贡献**:  
本文提出 GAPrompt++，一种面向 3D 视觉模型的多粒度几何感知点云提示方法，用于高效地将预训练点云模型适配到下游任务。该方法通过提取多尺度几何特征、生成点级提示并沿模型层级传播几何线索，弥补了现有提示式参数高效微调方法忽略点云内在几何结构的不足。实验表明，GAPrompt++ 在多个基准上达到提示式 PEFT 方法的最优性能，甚至超过全量微调，且可训练参数少于 2%。

**创新点**:  
主要创新在于将多粒度几何感知引入点云提示式参数高效微调，设计了 Point Shift Prompter、Keypoint Prompter 和 Prompt Propagation 三个模块，分别实现跨尺度几何特征提取、局部显著细节增强以及几何信息在特征提取层级中的有效传播。此外，论文还构建了两个基于 3D Gaussian Splatting 和 Multi-View Stereo 重建的更具挑战性的点云评测基准。

**方法**:  
GAPrompt++ 采用多粒度几何感知提示框架：Point Shift Prompter 在不同尺度上提取多粒度几何特征，实现实例特定的几何调整；Keypoint Prompter 自适应生成点级提示，突出局部几何显著性和细粒度结构细节；Prompt Propagation 机制将多粒度几何线索注入整个特征提取层级，增强模型对关键几何特征的捕获能力。

**结果**:  
大量实验表明，GAPrompt++ 在多种基准上取得了提示式 PEFT 方法中的最先进性能，并且能够超越全量微调，同时仅需少于 2% 的可训练参数。为缓解现有评测数据集饱和问题，论文还基于 3D Gaussian Splatting 和 Multi-View Stereo 重建构建了两个更具挑战性的基准。

**相关性与影响**:  
该工作对点云分析和 3D 视觉模型的高效适配具有重要意义，推动了参数高效微调在三维几何领域的应用。其多粒度几何感知提示与传播机制为后续点云 PEFT 研究提供了新思路，同时新构建的挑战性基准有助于促进更真实、多样场景下的点云理解研究。

---

### 6. QCPruner: Query-Conditioned Population Coverage for Visual Token Pruning **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2609.19990](https://arxiv.org/abs/2609.19990)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19990)
- **作者**: Shengli He, Yongchao Liang, Roumeng He et al. (7 authors)
**评估**: 该论文提出QCPruner，一种面向多模态大模型（MLLM）视觉token的无训练剪枝方法，通过双边效用加权和查询条件化的覆盖选择减少后续层计算。这属于模型压缩/剪枝范畴（training-free pruning, 轻量化部署），因此归入Distillation类别。候选方案同时涉及推理加速，但核心贡献是剪枝压缩算法，故Distillation更贴切。质量方面：方法有清晰的技术创新（将query效用同时作用于视觉目标与候选代表，构造非负facility-location目标，保持单调次模性及(1-1/e)贪心保证），无需训练，实验覆盖LLaVA-1.5、LLaVA-NeXT、LLaVA-Video、Qwen2.5-VL多个主流模型且在各token预算下取得最优结果，证据充分，属于较高质量的效率优化工作。

**核心贡献**:  
论文提出 QCPruner，一种无需训练的视觉 token 剪枝方法，通过查询条件化的双边效用加权同时指导视觉目标与候选代表的选择。该方法在固定 token 预算下保留查询相关证据并减少冗余，适用于多种多模态大语言模型。

**创新点**:  
将视觉目标与候选代表两种角色统一为查询条件化效用，利用关键词匹配的查询锚点融合跨模态线索，并将该效用嵌入基于视觉亲和度的覆盖目标，形成单调且子模的非负设施选址问题，从而保持标准贪心 (1-1/e) 近似保证，且无需模型训练或参数更新。

**方法**:  
QCPruner 使用关键词匹配的查询锚点获取查询相关信息，融合两种跨模态线索得到共享的逐视觉查询效用，并对视觉目标和候选代表进行双边效用加权。随后在视觉亲和度基础上构建覆盖目标，将其转化为非负设施选址问题，利用单调子模性质进行贪心选择，实现免训练、免参数更新的视觉 token 剪枝。

**结果**:  
在 LLaVA-1.5、LLaVA-NeXT、LLaVA-Video 和 Qwen2.5-VL 上，QCPruner 在所有报告的 token 预算下取得评估的完整系统剪枝方法中最高的平均相对性能。在 LLaVA-1.5-7B 上，保留 32/576 个 token 时仍达到未剪枝性能的 96.1%，优于最强评估基线的 93.9%；在 Qwen2.5-VL-7B 上，保留 256/1296 个 token 时相应值为 96.7% 对 92.5%。

**相关性与影响**:  
该工作为多模态大语言模型中的视觉 token 剪枝提供了查询条件化且理论可保证的免训练方案，有助于在固定计算预算下提升推理效率与查询相关证据保留能力，对高效多模态推理、长视频理解和视觉 token 压缩等相关方向具有潜在影响。

---


---

## ⚙️ 训练推理基础设施

### 1. Understanding and Exploiting Diagonal Attention Sparsity in Autoregressive Image Generation **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.19702](https://arxiv.org/abs/2609.19702)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19702)
- **作者**: Daeun Kim, Junwha Hong, Changhun Oh et al. (6 authors)
**评估**: 该论文虽然应用场景是自回归图像生成，但其核心贡献在于推理基础设施的效率优化：系统刻画了注意力稀疏性（KV cache访问瓶颈、prefill-decode不对称、对角稀疏模式），并提出了diagonal-aware sparse attention机制，在GPU服务系统上基于FlexGen、FlashAttention-2和自定义kernel实现，取得最高3.1倍吞吐和1.19倍延迟改进且质量损失<2%。这属于推理加速/服务基础设施优化范畴，因此归为Training_Inference_Infra。论文有明确的系统性分析、原创的稀疏注意力方法、真实系统实现和充分的性能评测，方法创新性和工程价值兼备，质量较高。

**核心贡献**:  
本文首次对自回归图像生成中的注意力稀疏性进行了系统性表征，揭示了预填充-解码不对称、注意力集中于提示词与局部token、以及由视觉token空间局部性导致的独特对角注意力稀疏模式。基于这些发现，作者提出了一种对角感知稀疏注意力机制，在保持图像质量几乎不降的前提下显著提升推理效率。

**创新点**:  
首次系统刻画自回归图像生成（而非文本LLM）的注意力稀疏特性，发现并利用独特的『对角注意力稀疏』模式——即近期窗口内沿对角线方向的KV条目可被选择性跳过；提出对角感知稀疏注意力机制，区别于传统基于阈值或固定模式的稀疏方法。

**方法**:  
跨多种工作负载与代表性开源自回归图像生成模型进行注意力稀疏性的实证分析；据此设计对角稀疏注意力，在最近窗口内沿对角注意力方向选择性跳过KV条目；在GPU服务系统上基于FlexGen、FlashAttention-2及自定义CUDA内核实现。

**结果**:  
相比稠密推理，吞吐量最高提升3.1倍，延迟改善最高1.19倍，而生成质量下降不足2%。

**相关性与影响**:  
该工作填补了稀疏注意力在自回归图像生成领域研究的空白，表明文本LLM的稀疏性假设不能直接迁移到视觉生成场景；其对角稀疏洞察可为多模态生成模型的高效推理、KV缓存优化及服务系统设计提供新方向，兼具学术价值与工程落地意义。

---

### 2. Region-Level Policy Optimization for Fine-grained MLLM Perception **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2609.19745](https://arxiv.org/abs/2609.19745)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19745)
- **作者**: Yuheng Shi, Xiaohuan Pei, Minjing Dong et al. (4 authors)
**评估**: 该论文聚焦于提升 MLLM 细粒度视觉感知的推理效率：通过区域级策略优化（Vision-RL2）在粗视图定位 RoI、将分辨率集中在证据区域，从而显著减少视觉 token 数量并降低视觉编码与语言模型 prefilling 成本。虽然涉及从注意力蒸馏出的轻量 proposal network，但其核心贡献是推理阶段的 token 压缩与效率优化（在固定 token 预算下提升精度、用约 1/4 token 达到更大预算的精度），属于推理加速/显存与 token 优化范畴，因此归为 Training_Inference_Infra。论文方法具有明确创新（区域级强化学习、互补的减法/加法目标、无需区域标注），实验覆盖 6 个细粒度基准和 4 个 MLLM 骨干，结论有据可依，并开源代码，整体质量较高。

**核心贡献**:  
论文提出Vision-RL2，用区域级强化学习优化轻量候选区域网络，实现细粒度MLLM感知中的高效RoI定位与稀疏高分辨率编码。方法在粗视图定位后集中分辨率于关键证据，在六个细粒度基准和四个MLLM骨干上均提升精度，并可用约4倍更少视觉token超过原模型最大预算精度。

**创新点**:  
发现细粒度感知中定位与识别对分辨率需求不同，定位可承受约3-4倍更强token压缩；将RoI选择建模为区域级强化学习动作，用冻结MLLM阅读器对区域移除引起的答案似然变化进行评分，并通过互补的减法与加法目标优化候选区域网络，无需区域标注、响应采样或推理轨迹。

**方法**:  
先通过诊断实验证明定位比识别更能容忍token压缩，因此从粗视图定位、再对选中证据集中分辨率。轻量proposal network由MLLM注意力蒸馏得到；其输出连贯区域作为动作，冻结MLLM reader根据移除该区域后答案似然的变化给出奖励。减法目标抑制干扰候选，加法目标恢复遗漏证据，仅更新预测器。精炼后的proposal进一步支持稀疏编码，放大证据并排除背景token。

**结果**:  
在六个细粒度视觉感知基准和四个MLLM骨干上，Vision-RL2在每个token预算下均优于基础模型；以约4倍更少的视觉token达到并超过基础模型最大token预算下的准确率。

**相关性与影响**:  
该工作为高效细粒度多模态感知提供了新思路，将强化学习用于区域级视觉token选择，兼顾定位精度与计算效率。其无需区域标注和响应采样的设计降低了训练成本，对高分辨率MLLM、视觉token压缩、注意力蒸馏和区域级策略优化等相关方向具有潜在推动作用。

---

### 3. From Models to Systems: A Comprehensive Survey of Efficient Multimodal Learning **⭐⭐⭐** (相关度: 78%, 质量: 0.8)

- **arXiv ID**: [2609.19445](https://arxiv.org/abs/2609.19445)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19445)
- **作者**: Pan Wang, Siwei Song, Hui Ji et al. (15 authors)
**评估**: 该论文是一篇关于高效多模态学习（Efficient Multimodal Learning）的系统性综述，核心关注计算、内存与部署瓶颈，并提出了从模型到系统的三层级分类（model/algorithm/system），重点涉及硬件感知编排、全栈资源编排、执行优化与可扩展部署效率，最契合 Training_Inference_Infra（训练推理基础设施）。虽然内容也触及模型轻量化（接近 Distillation），但其系统级、部署级与硬件协同设计的整体框架更偏向基础设施与效率工程，故归入 Training_Inference_Infra。质量方面：这是一篇涵盖300+篇工作的结构化综述，提出了原创性的分类体系和跨层协同方法论，并含MLLM案例研究与未来方向分析，具有较高参考价值，质量较高。

**核心贡献**:  
This survey systematically organizes the Efficient Multimodal Learning (EML) landscape by introducing the first structured, model-to-system taxonomy, distilling insights from over 300 works across model, algorithm, and system levels. It synthesizes cross-layer co-design and the Efficiency-Utility-Privacy trade-off, and provides an integrative case study on Multimodal Large Language Models (MLLMs) to trace the field's evolution. The paper establishes a structured framework for natively efficient multimodal systems ready for ubiquitous deployment.

**创新点**:  
The first structured, model-to-system taxonomy for EML, covering architectural parsimony, execution refinement, and hardware-aware orchestration. It offers a methodological synthesis of vertical synergies between layers, a holistic view of the Efficiency-Utility-Privacy trade-off, and posits a paradigm shift toward self-regulating intelligence where efficiency is an intrinsic emergent property rather than a post-hoc constraint.

**方法**:  
Systematic literature review and categorization of over 300 seminal works into three hierarchical levels: model (architectural parsimony), algorithm (execution refinement), and system (hardware-aware orchestration). Cross-layer co-design analysis, integrative case study of MLLMs, and application-specific optimization blueprints for diverse domains.

**结果**:  
As a survey, it does not report experimental results; instead, it provides a comprehensive taxonomy, methodological synthesis, application-specific blueprints, and a discussion of open challenges and future directions. It establishes a structured framework for high-performing, generalizable, natively efficient, and deployable multimodal systems.

**相关性与影响**:  
The survey is highly relevant for advancing efficient multimodal learning by bridging model, algorithm, and system perspectives, guiding cross-layer co-design, and addressing deployment bottlenecks. It impacts research on MLLMs, resource-constrained multimodal systems, and the broader goal of ubiquitous, efficient, and privacy-aware multimodal intelligence.

---

### 4. Queries Knew More Than We Thought: Uncovering Latent Knowledge in Segmentation Models **⭐⭐⭐** (相关度: 72%, 质量: 0.9)

- **arXiv ID**: [2609.20283](https://arxiv.org/abs/2609.20283)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20283)
- **作者**: Ignacio M. De la Jara, Cristian Rodriguez-Opazo, Damith Ranasinghe
**评估**: 该论文研究冻结 DETR 系列分割模型在推理阶段的输出选择瓶颈，提出 HYDRA 选择器，无需新增 query、重新生成 mask、重跑 backbone 或更新权重，仅利用缓存输出进行候选路由与校准。这属于推理时模型输出优化与部署基础设施相关方向，因此归为 Training_Inference_Infra。论文问题定义清晰，实验覆盖 Mask2Former、MaskDINO、OneFormer、SAM 3 等多个模型及 ADE20k、COCO 等数据集，并包含消融、LoRA 对照与机制分析，创新性和实证充分性较好，质量较高。

**核心贡献**:  
该论文揭示了冻结的DETR系列分割模型中存在被忽略的'输出选择瓶颈'：模型已经计算出的查询候选中往往包含有用的掩码，但默认的选择规则未能将其暴露。作者提出HYDRA——一个仅基于缓存冻结输出训练的小型选择器，在不新增查询、不生成新掩码、不重跑骨干网络、不更新权重的前提下，将潜在候选重新路由并超越保留基线，从而显著提升多个分割模型在多种数据集与域上的性能。

**创新点**:  
首次系统性地将分割模型的性能损失归因于'输出选择'而非'特征或掩码生成'问题，并用真实标签oracle量化了已计算候选中的隐藏提升空间；提出HYDRA选择器，其核心是引入显式的keep-baseline选项与基于held-out数据校准的决策边际，只在候选明显更优时才进行替换，从而在零额外推理成本下安全地挖掘潜在知识。此外，作者通过配对LoRA对照实验证明轻量权重微调无法消除该瓶颈，并将现象与二分匹配下的查询特化机制联系起来。

**方法**:  
在冻结的DETR家族模型上，先以ground-truth-only oracle评估已计算掩码候选中的隐藏上限；随后训练HYDRA——一个仅使用训练集缓存输出的小型选择器，对缓存候选打分并与keep-baseline选项比较，推理时仅在held-out数据校准的margin表明所选候选足够更优时才采取行动，否则保留原预测。实验覆盖Mask2Former、MaskDINO、OneFormer及SAM 3，并通过配对LoRA微调对照与受控TinyDETR研究验证瓶颈来源与查询特化假设。

**结果**:  
HYDRA将Mask2Former、MaskDINO和OneFormer在ADE20k与COCO上的dataset mIoU最高提升+7.41个点；在SAM 3上跨八个域平均提升+9.4个class-macro prompt-IoU点，且通过校准保留了有用预测。配对LoRA对照显示，权重适应后暴露的预测常常持平或更差，但对适应后候选进行路由仍能恢复精度，说明瓶颈并非权重层面可轻易解决。

**相关性与影响**:  
该工作对DETR系列分割模型及更广泛的候选选择范式具有重要影响：它表明冻结分割器不应仅以其暴露的掩码来评价，还应考量其抑制的有用候选，为免训练/免重算的模型提升提供了新思路。其方法与发现可推广到其他多候选输出的视觉模型与基础模型（如SAM 3），并提示模型评估与部署中应关注输出选择策略这一常被忽视的环节。

---


---

## 🧠 Agent 相关内容

### 1. VideoResearcher: Self-Improving Tool Design for Long-Video Understanding **⭐⭐⭐⭐** (相关度: 95%, 质量: 0.8)

- **arXiv ID**: [2609.19664](https://arxiv.org/abs/2609.19664)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19664)
- **作者**: Dingqiang Ye, Dongdi Zhao, Kaishen Wang et al. (14 authors)
**评估**: 该论文提出了一种用于长视频理解的自改进多智能体框架，核心是自主设计、测试和精炼视频工具，属于智能体（Agent）方向。方法具有创新性（训练无关、双循环工具进化），面向长视频理解这一热门应用，且声称达到自改进智能体的SOTA并接近人类设计上界，实验设计合理，对相关领域有参考价值。虽未提及具体机构，但整体质量较高，不属于低质量或小众方向。

**核心贡献**:  
论文提出 VideoResearcher，一个无需训练的多智能体框架，能够像人类研究者一样自主设计、测试和优化长视频理解工具。它通过 Solving 与 Evolving 双循环分析工具使用轨迹、识别能力缺口，并协调专用智能体开发与验证可执行工具。该方法在自改进智能体上达到最先进性能，并接近人工设计的上界。

**创新点**:  
面向高影响力视频工具的自主自改进设计：无需更新模型参数，通过双循环机制让多智能体协作发现能力缺口、开发并验证新工具，并将进化后的工具复用于后续视频推理中的证据获取。

**方法**:  
提出免训练的多智能体框架 VideoResearcher，包含 Solving 循环和 Evolving 循环。Evolving 循环分析工具使用轨迹以识别能力缺口，协调专门智能体开发并验证可执行视频工具；Solving 循环复用进化后的工具来增强长视频推理中的证据获取。通过迭代式工具优化与验证，在不更新模型参数的情况下逐步提升智能体能力。

**结果**:  
在自改进智能体方法中取得最先进性能，并接近人工设计工具的上界，验证了无需训练即可通过自主工具开发扩展智能体能力的范式。

**相关性与影响**:  
该工作为长视频理解提供了一种降低人工设计成本、可自主进化工具能力的免训练范式，对视频智能体、工具学习与自改进多智能体系统具有重要参考价值。

---

### 2. Coding Agents with an Obstacle-Aware Harness for Safe Robot Manipulation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.20822](https://arxiv.org/abs/2609.20822)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20822)
- **作者**: Bingxin Xu, Yuzhang Shang, Zhen Dong et al. (4 authors)
**评估**: 该论文研究基于编码智能体（coding agents）的机器人操作安全性问题，提出SafeHarness框架，通过障碍感知的路径规划与接触执行两个模块，使语言模型智能体在任务规划中优先考虑安全约束。属于Agent方向，因为核心是LLM智能体在具身任务中的规划与安全约束满足。方法有明确创新点，实验指标显著优于SOTA，问题动机清晰，具有实际参考价值。不属于低质量或小众方向，故判定为高质量论文。

**核心贡献**:  
论文首次评估了编码智能体（coding agent）在安全约束下的机器人操作安全性，发现其虽能感知障碍物且提示已禁止碰撞，却仍因规划阶段未将安全约束作为优先目标而频繁碰撞。为此提出SafeHarness，通过障碍感知的路线规划与接触执行两个harness，使模型在规划中优先考虑安全约束。实验表明该方法在任务成功率和避障率上均显著超越先前SOTA。

**创新点**:  
首次提出并系统研究编码智能体在机器人操作中的安全问题，将失败根源定位到规划阶段：模型缺乏清理路线与重规划的概念，且接触执行未受同一安全约束限制。创新性地提出SafeHarness，用障碍感知的路线规划和障碍感知的接触执行两个harness，将安全约束显式注入规划过程。

**方法**:  
将机器人操作分解为路线阶段与接触密集时刻。障碍感知路线规划：以边界框表示物体，在其上生成候选路线作为路点序列；智能体提前规划路线、验证其可行性、必要时重规划，然后才执行。障碍感知接触执行：选择接触位置时使接触本身避开障碍物，从而在接触阶段也满足安全约束。

**结果**:  
SafeHarness取得71.9%的任务成功率和87.5%的避障率，较先前SOTA分别提升6.5%和27.0%；这两个指标分别是同一智能体不使用harness时的2.3倍和1.5倍。

**相关性与影响**:  
该论文对机器人操作、具身智能及安全关键系统具有重要意义，揭示了编码智能体在安全约束下规划层面的根本缺陷，并证明通过障碍感知harness可有效提升安全性，为编码智能体在真实机器人中的安全部署提供了可行方案。

---

### 3. Navi-Agent: Unlocalized Monocular Navigation Agent **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.8)

- **arXiv ID**: [2609.20388](https://arxiv.org/abs/2609.20388)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20388)
- **作者**: Wenyuan Xie, Mengyang Hong, Yongzhong Wang et al. (12 authors)
**评估**: 该论文提出一种零样本连续环境下的视觉语言导航智能体 Navi-Agent，核心是构建无坐标空间状态与导航拓扑，用于近似自定位、进度验证和基于视觉重访的恢复，属于典型的具身智能体与导航决策方向，因此分类为 Agent。方法针对 VLN-CE 中空间状态维护困难的问题提出新表示与闭环导航框架，实验包含零样本 VLN-CE 基准和真实机器人平台，且声称在几何约束方法中达到 SOTA，整体创新性和实验充分性较好，不属于简单水文或小众垂直应用，质量较高。

**核心贡献**:  
本文提出 Navi-Agent，一种面向连续环境视觉语言导航（VLN-CE）的零样本单目导航智能体。它不依赖深度信息或全局坐标定位，而是从视觉观测与运动历史中构建无坐标空间状态，并组织为导航拓扑图。该表示支持基于观测的近似自定位、任务进度验证与基于视觉重访的恢复，在基准测试和真实机器人平台上取得了几何约束方法中的最优性能。

**创新点**:  
核心创新在于提出无需几何定位和全局坐标的坐标自由空间状态表示，并将其组织为“导航拓扑”：节点表示视觉地点，边表示运动转换。该拓扑使智能体能够仅依靠视觉观测和已执行动作历史完成近似自定位、进度验证和视觉重访恢复，从而在去除深度与全局一致坐标约束的同时维持持久空间感知。

**方法**:  
Navi-Agent 将指令分解为子目标，执行局部视觉导航，并通过构建的导航拓扑验证已访问地点，形成闭环导航。其空间状态由视觉观测与运动历史在线构建，不使用深度或全局坐标；节点对应视觉地点，边对应运动转移。系统利用该表示进行基于观测的近似自定位、任务进度确认以及通过视觉重访实现失败恢复。

**结果**:  
在零样本 VLN-CE 基准和真实机器人平台上进行了实验。结果表明，Navi-Agent 在几何约束方法中达到最先进性能，同时与依赖几何定位的方法相比仍具有竞争力。

**相关性与影响**:  
该工作推动了零样本 VLN-CE 在无深度、无全局定位条件下的发展，为单目具身智能体在未知环境中的长期导航提供了可扩展的空间记忆与闭环决策方案。其无坐标拓扑表示有望促进更实用、低传感器依赖的视觉语言导航系统，并对具身 AI、机器人导航和视觉地点识别等方向产生潜在影响。

---

### 4. VLN on the Fly: An Onboard Vision-Language Navigation Stack for Aerial Robots **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.7)

- **arXiv ID**: [2609.20191](https://arxiv.org/abs/2609.20191)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20191)
- **作者**: Marco S. Tayar, Felipe Tommaselli, Gianluca Capezutto et al. (9 authors)
**评估**: 论文核心是面向空中机器人的视觉语言导航（VLN）系统，将指令 grounding、3D 目标定位、轨迹规划与底层控制组成可检查的 onboard 模块化栈，属于具身智能体/机器人导航 Agent 方向。系统集成了量化 VLM、B-spline 规划器和预训练 RL 控制器，并在真实无人机上完成 onboard 实验，具有一定工程参考价值；但实验规模较小、场景较受控，创新更多体现为系统集成与部署而非全新算法，因此质量评为中等偏上。

**核心贡献**:  
该论文提出 VLN on the Fly，一个完全机载运行的视觉语言导航堆栈，用于空中机器人。它将语言 grounding、规划和飞行控制保持为独立可检查的阶段，在受限计算条件下实现从自然语言指令到四旋翼电机命令的闭环飞行。实验表明该模块化堆栈在室内真实飞行中具有较高的目标到达率与厘米级定位精度。

**创新点**:  
核心创新在于为空中机器人设计了一种模块化、可观测、可安全检查的 onboard VLN 堆栈，避免端到端策略将 grounding、规划和控制融合为单一网络所带来的不可解释性和错误隔离困难。同时，它使用量化 VLM 进行指令 grounding，并结合深度信息、B 样条规划器和预训练强化学习控制器，在单机载计算资源下实现跨四旋翼的实时导航。

**方法**:  
方法分为四个独立阶段：首先用量化视觉语言模型将自然语言指令 grounding 到粗略图像单元；然后利用深度信息将该图像单元提升为 3D 目标；接着通过快速 B 样条规划器生成可行轨迹；最后使用预训练强化学习策略跟踪轨迹并输出电机控制命令，且可适配不同四旋翼平台。整个堆栈在机载计算上运行，并保留模块间的可观测性与安全门控。

**结果**:  
在受控室内环境中，针对三类日常参照物进行了 15 次机载飞行，堆栈在 15 次试验中成功到达目标 13 次，平均目标误差为 5.72 cm，平均 GPU 利用率为 39.3%。额外 6 次杂乱环境试验中，堆栈在机载感知门控下能够跟踪无碰撞轨迹。

**相关性与影响**:  
该工作证明了在有限机载计算条件下实现完整视觉语言导航空中机器人系统的可行性，对空中机器人自主导航、人机交互、具身智能和资源受限平台上的多模块系统集成具有重要参考价值。其模块化设计也提升了飞行安全与可调试性，有望推动 VLN 从仿真或地面平台走向真实空中部署。

---

### 5. VABench: Measuring Embodied Spatial Intelligence through Visual Demonstrations, Active Perception, and Metric Control **⭐⭐⭐⭐** (相关度: 82%, 质量: 0.8)

- **arXiv ID**: [2609.19554](https://arxiv.org/abs/2609.19554)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19554)
- **作者**: Zhongbo Zhang, Jiayi Jin, Yifan Wang et al. (7 authors)
**评估**: 该论文提出VA-Bench，一个评估具身空间智能的基准，考察通用多模态大模型（MLLMs）在'观察-推理-行动-修正'闭环中的能力：从纯RGB演示中学习、主动选择相机视角、发出度量笛卡尔命令并根据执行反馈修正。这属于具身智能体（Embodied Agent）评测方向，与Agent类别高度契合。质量方面，评测设计较为严谨：包含14个基础任务族、7个留出几何/布局变体、长时程五物体组合任务，评估12种模型在3次独立运行下基于20个物理验证种子的结果，并报告终端成功率、9项轨迹级行为诊断和子任务进度，实验充分且有明确发现（如主动相机控制显著提升成功率、几何迁移导致性能下降超30个百分点）。方法有明确贡献，实验设计科学，结论可靠。虽然评审对象是小众的具身空间智能基准，但受众为MLLM/具身智能领域，具有一定参考价值，非水文。综合质量评分0.78。

**核心贡献**:  
论文提出了 VA-Bench，一个用于评估具身空间智能的基准，旨在测试模型在视觉演示、主动感知和度量控制下完成“观察-推理-行动-修正”完整闭环的能力。该基准覆盖14类基础任务、7类留出几何/布局变体以及长时程五物体组合任务，并对12种模型条件进行多次独立评估。实验表明，当前通用多模态大模型在目标定位上表现良好，但整体任务成功率、几何迁移和长时程执行仍存在显著不足。

**创新点**:  
主要创新在于将具身空间智能评估从静态描述扩展到完整的闭环交互：模型仅依赖RGB演示学习程序性上下文，主动选择相机视角，输出度量笛卡尔命令，并根据执行反馈进行修正；同时不提供对象的特权位姿、预言轨迹或预训练动作头，并使用固定的模型无关控制器执行模型指定目标。

**方法**:  
VA-Bench包含14个基础任务族（11个单臂和3个双臂）、7个留出几何/布局变体以及一个五物体长时程组合赛道。每个基础任务在20个物理验证的随机种子上进行三组独立运行，评估12种主要模型条件。模型需从仅RGB演示中学习程序上下文，主动控制相机视角，发出度量笛卡尔命令，并基于执行反馈修正动作。评估指标包括终端成功率、九项轨迹级行为诊断和子任务进度。

**结果**:  
最佳模型在标注运行中目标定位达到100.0%，空间关系达到78.9%，但三运行宏平均任务成功率仅为53.93%±3.17%。主动相机控制相对被动多视角观察显著提升任务成功率，在匹配比较中从27.86%提高到57.50%。留出几何迁移可使任务成功率下降超过30个百分点。没有模型能完成严格的长时程任务，尽管部分进度显著。

**相关性与影响**:  
该基准强调了具身空间智能中主动感知、度量控制和闭环修正的重要性，揭示了当前通用多模态大模型在真实具身行动中的能力边界。其评估框架和诊断指标可为后续研究提供标准化测试平台，推动从被动视觉理解向主动、可执行和可修正的空间智能发展。

---

### 6. AnyviewMeter: Adapting Robotic Reward Models with Camera Geometry and Multi-View Attention **⭐⭐⭐** (相关度: 76%, 质量: 0.8)

- **arXiv ID**: [2609.20106](https://arxiv.org/abs/2609.20106)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20106)
- **作者**: Yuang Tu, Runjia Tan, Yujie Yan et al. (5 authors)
**评估**: 该论文面向机器人奖励模型在视角变化和遮挡下的适应问题，属于具身智能/机器人智能体（Agent）方向。方法结合相机几何条件、Plücker ray 和同步块注意力，并采用低秩参数高效微调，创新点较明确；在模拟与真实操作任务上进行了多视角实验，报告了 MAE 和时序排序改进，实验支撑较充分。虽然主题偏机器人操作与奖励建模，不算极大众，但具有明确的具身智能应用价值，不属于低质量或水文。

**核心贡献**:  
论文提出 AnyviewMeter，一个面向机器人奖励模型的几何条件适配框架，用于在视角和遮挡变化下保持任务进度预测的稳定性。它通过低秩微调、Plucker 射线条件化与同步块注意力，将相机几何和多视角信息融入预训练奖励模型。该方法同时支持单视角奖励预测和多视角联合评估，并在仿真与真实操作任务中显著降低进度预测误差。

**创新点**:  
主要创新在于将相机几何（token 对齐的 Plucker 射线）与多视角同步注意力结合，用于参数高效地适配预训练机器人奖励模型，使奖励预测不再对视角变化和遮挡敏感。

**方法**:  
方法以预训练的 Robometer 奖励模型为基础，采用低秩微调进行参数高效适配；通过 token 对齐的 Plucker 射线将相机几何注入视觉特征以及注意力查询和键中；并利用同步块注意力在预训练解码器内部融合同步多视角信息。框架支持单视角奖励预测和联合多视角评估。

**结果**:  
在 PickCube 上，单视角适配提升了每个相机组的进度预测，并在视野变化下相对 RGB 微调将平均绝对误差降低约 21%。在模拟操作任务中，联合多视角预测相比平均单视角 RGB 预测将进度误差降低 41-69%，并在约 88% 的任务-相机组中改善时间排序。在固定相机和腕部相机的真实任务中，平均绝对误差相对平均 RGB 微调降低约 21%。

**相关性与影响**:  
该工作强调了相机几何与联合视觉证据在任务特定机器人奖励适配中的重要性，为提升机器人奖励模型在真实动态视角和遮挡环境下的鲁棒性提供了有效路径，对机器人学习、视觉奖励建模和多视角感知具有潜在影响。

---

### 7. Beyond Patch Removal: Persistent Adversarial Effects in Vision-Language-Action Policies **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.19669](https://arxiv.org/abs/2609.19669)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19669)
- **作者**: Enhao Wu, Fusen Guo, Yuxin Cao et al. (6 authors)
**评估**: 该论文研究 Vision-Language-Action (VLA) 策略的对抗鲁棒性问题，VLA 策略本质上是具身智能体（embodied agent）的决策模型，因此最符合 Agent 类别。论文并非生成、蒸馏或训练基础设施方向。方法上提出了 state-restoration 协议，通过 clean、random-patch、deviation-matched、fixed-direction 等多种对照来分离对抗效应与遮挡、动作误差幅度、方向持续性等因素，实验设计较为严谨，并在 OpenVLA-OFT 与自回归 OpenVLA 上验证，还训练了 recovery adapter 并分析干预延迟的影响，具有一定的实际参考价值（VLA 安全性与可恢复性）。属于对抗鲁棒性这一相对细分的子方向，受众较小但并非医疗、遥感等垂直应用领域，方法有明确创新点且实验较充分，故评为中等偏上质量。

**核心贡献**:  
论文研究 Vision-Language-Action（VLA）策略中对抗补丁移除后的持续状态效应，强调现有评估多关注连续攻击而未区分即时动作破坏与后续可恢复性。作者提出状态恢复协议，在匹配的动作块边界移除补丁，并测量相同剩余步数预算下的恢复能力。实验表明，对抗补丁的影响会在移除后持续存在，且及时干预对恢复至关重要。

**创新点**:  
提出一种状态恢复协议，在匹配 action-chunk 边界移除对抗补丁，并引入 clean、random-patch、deviation-matched 和 fixed-direction 控制条件，以分离遮挡、动作误差幅度和方向持续性等混杂因素。同时评估在攻击诱导状态上训练的 recovery adapter，并考察受控干预延迟对恢复效果的影响。

**方法**:  
在 OpenVLA-OFT 上使用 EDPA 攻击，并在 LIBERO-Long 任务中于匹配动作块边界移除补丁，测量后续可恢复性；通过多个控制组区分不同非对抗因素。还在自回归 OpenVLA 上验证持续效应，并训练 recovery adapter 在攻击诱导状态上进行恢复，测试不同干预延迟下的恢复表现。

**结果**:  
在 OpenVLA-OFT 与 EDPA 攻击下，LIBERO-Long 中五个动作块后仅 36.2% 的 episode 仍可恢复，而 deviation-matched 和 fixed-direction 控制分别为 89.9% 和 87.0%。自回归 OpenVLA 上也观察到类似的持续效应。recovery adapter 在一个动作块延迟下将恢复率从 7.7% 提升至 47.4%，但随着干预延迟增加，其收益显著下降。

**相关性与影响**:  
该研究表明 VLA 策略中的对抗攻击不仅造成即时动作破坏，还会留下移除补丁后仍持续存在的状态影响，对具身智能与机器人策略的安全性评估具有重要意义。所提出的状态恢复协议和恢复适配器分析为鲁棒性评测、及时干预与恢复机制设计提供了新方向。

---

### 8. Towards Active Cross-View Object Geo-Localization **⭐⭐⭐** (相关度: 72%, 质量: 0.7)

- **arXiv ID**: [2609.19662](https://arxiv.org/abs/2609.19662)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19662)
- **作者**: Shunyu Yao, Xiaohan Zhang, Zhuoran Yang et al. (8 authors)
**评估**: 该论文的核心是让一个智能体主动、序贯地选择新视角并自主决定何时停止观测以提高跨视角目标地理定位的精度，这本质上是智能体的决策/策略学习问题：它使用监督轨迹初始化策略，并采用 GRPO 强化学习配合增益-成本奖励来联合优化定位精度与观测效率。这种‘主动感知-决策’范式与 Agent 方向高度契合，而非生成（Image_Video_Omni_Generation）、蒸馏压缩（Distillation）或训练推理基础设施（Training_Inference_Infra），因此归为 Agent。质量方面：论文提出了新的任务设定 ActiveGeo、三阶段训练框架 ActiveMoPT，并构建了零样本测试集 ActiveGeo-858，方法有明确创新（主动视角选择 + GRPO 策略优化）、实验显示了 SOTA 与零样本泛化优势，具备一定参考价值。但方向相对偏窄（UAV/跨视角地理定位属细分应用），实验规模和机构背景从摘要难以完全确认，故 quality_score 定于 0.72，判定为高质量但非顶尖。

**核心贡献**:  
论文提出主动跨视角物体地理定位（ActiveGeo），让移动智能体主动选择新视角并决定何时停止，以最少观测提升定位性能。为此提出 ActiveMoPT 三阶段训练框架，并构建零样本测试集 ActiveGeo-858。实验表明 ActiveMoPT 在 MoP-UAV 上以平均仅 1.45 个查询视角达到 SOTA，并在 ActiveGeo-858 零样本评测中显著优于现有 CVOGL 方法。

**创新点**:  
将传统固定查询图像的 CVOGL 扩展为主动感知设定；提出多视角提示保持适配、轨迹引导策略初始化、代价感知策略精炼三阶段框架；设计增益-代价奖励联合优化定位精度与观测效率；构建 ActiveGeo-858 零样本基准。

**方法**:  
ActiveMoPT 采用三阶段训练：1）Multi-View Prompt-Preserving Adaptation 聚合多个查询视角并复用初始提示；2）Trajectory-Guided Policy Initialization 使用监督智能体轨迹学习视角选择与初始停止行为；3）Cost-Aware Policy Refinement 使用 GRPO 与 gain-cost reward 联合优化定位精度和观测效率。

**结果**:  
在 MoP-UAV 上达到 SOTA，平均仅使用 1.45 个查询视角；在 ActiveGeo-858（包含 858 个场景和 1716 个目标标注）的零样本评测中大幅超越先前 CVOGL 方法。

**相关性与影响**:  
推动跨视角地理定位从被动固定查询转向主动高效感知，对移动机器人/无人机自主定位、主动视觉与地理定位交叉研究具有潜在影响。

---

### 9. AI Smart Glasses for Wearable Intelligence: From Egocentric Sensing to Agentic Personalization **⭐⭐⭐** (相关度: 62%, 质量: 0.7)

- **arXiv ID**: [2609.19793](https://arxiv.org/abs/2609.19793)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19793)
- **作者**: Xu Yuan, Yi Wang, Zhuohang Jiang et al. (11 authors)
**评估**: 该论文是一篇关于AI智能眼镜的综述，核心围绕可穿戴智能系统，强调从自我中心感知（egocentric sensing）到智能体个性化（agentic personalization）的转变，涉及智能体能力、主动性智能（proactive intelligence）、具身基础模型（embodied foundation models）、多模态交互等。四项组织维度中的'wearable intelligence'和'agentic capabilities'以及提出的研究挑战都指向智能体（Agent）方向，因此归为Agent类别。质量方面：作为综述，它构建了较系统的统一框架，涵盖硬件、穿戴智能、交互设计与应用场景，并提炼了五大跨领域挑战，具有一定的组织价值和参考意义；但内容偏概念框架、缺少具体方法创新与实验验证，且应用场景（医疗、文旅、工业等）较分散，深度受限，因此质量评分为中等偏上（0.65）。虽涉及医疗等垂直应用，但论文主体是通用可穿戴智能体平台而非单一小众领域，故保留分类。

**核心贡献**:  
本文是一篇关于AI智能眼镜的综述，将智能眼镜从自我中心（egocentric）采集与显示设备重新定义为可穿戴智能平台，即AI smart glasses。作者提出一个系统级概念框架，强调自我中心感知、资源感知计算、智能推理、多模态交互与真实应用约束的协同设计，并围绕硬件基础、可穿戴智能、交互设计与应用场景四个维度组织全文。论文还提炼出下一代硬件、可信自我中心智能、终身个性化记忆、主动式智能与具身基础模型五大跨领域挑战。

**创新点**:  
提出并系统化定义'AI smart glasses'这一系统级概念，把它作为连接第一人称感知与实时个性化辅助的可穿戴智能平台，而非单纯的硬件或单一算法问题。构建了以硬件基础—可穿戴智能—交互设计—应用场景为四大支柱的统一综述框架，并首次（在该框架下）整合出五个跨领域开放研究挑战，为领域提供统一的技术与应用组织视角。

**方法**:  
采用系统性综述与框架化分析方法：首先梳理约束感知、计算、反馈传递与持续部署的硬件基础；其次分析如何将自我中心信号转化为感知、情境与智能体（agentic）能力；随后讨论用户在实际活动中请求、接收、纠正与调节辅助的交互设计；最后跨医疗健康、无障碍辅助、情境学习、日常生活辅助、文化旅游与工业支持等场景，分析领域需求如何反向重塑系统设计与评估方式。

**结果**:  
作为综述论文，本文不报告自有的实验数据或性能指标，其主要产出是概念定义、四维组织框架、跨场景设计需求分析以及五项未来研究挑战（next-generation hardware、trustworthy egocentric intelligence、lifelong personalized memory、proactive intelligence、embodied foundation models）。

**相关性与影响**:  
该综述为快速兴起的AI智能眼镜与可穿戴智能领域提供了统一的概念与技术地图，有助于研究者定位自身工作在硬件、感知智能、交互与应用中的位置。其对资源受限条件下的自我中心智能、个性化记忆与主动式辅助等挑战的提炼，可指导未来多模态大模型、具身智能与边缘计算在可穿戴场景中的融合研究，并对医疗、无障碍、教育与工业等实际落地具有参考价值。

---

### 10. WZPlanner: Safe End-to-End Path Planning for Autonomous Driving in Work Zones **⭐⭐⭐** (相关度: 62%, 质量: 0.7)

- **arXiv ID**: [2609.19393](https://arxiv.org/abs/2609.19393)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19393)
- **作者**: Nishad Sahu, Changzhong Qian, Guangzhou Cai et al. (6 authors)
**评估**: 该论文聚焦自动驾驶在施工区（work zone）的端到端路径规划，核心是让自动驾驶智能体感知-决策-规划，属于典型的Agent（自动驾驶智能体决策/规划）范畴。论文贡献较扎实：构建了大规模多模态数据集WorkZonePlan（149K+合成与5K+真实样本、3D标注、228条闭环CARLA评测路线），提出半自动化数据生成流水线WAVE，以及基于Transformer的BoundaryFormer（BF/BF++）联合预测车道边界、施工区边界与驾驶轨迹，并给出消融实验与Bench2Drive格式的量化对比（Driving Score 63.0/64.4 vs SimLingo 59.3、TF++ 26.1），同时模型更小巧。整体方法有创新、实验较充分、结论有支撑，质量属中上。但施工区属于相对垂直且细分的安全场景，受众偏窄，通用性与影响力有限，故质量分不高。无人驾驶规划并非生成/蒸馏/训练推理基础设施方向，最接近的类别为Agent。

**核心贡献**:  
本文面向工作区（Work Zone）中自动驾驶路径规划的安全性与泛化难题，提出了WorkZonePlan数据集、WAVE半自动数据生成流程以及BoundaryFormer/BF++模型。核心思想是联合预测车道边界、工作区边界和驾驶轨迹，从而提升自动驾驶车辆在临时交通控制与车道几何变化场景下的规划安全性。实验表明，BF++以更小模型规模取得了优于SimLingo和TransFuser++的闭环驾驶性能。

**创新点**:  
主要创新包括：1）构建WorkZonePlan数据集，包含149K+合成样本和5K+真实多模态样本，并提供车道边界、工作区边界和驾驶轨迹选项的3D标注；2）提出WAVE半自动虚拟与真实环境数据生成流程，以及76个CARLA闭环场景、3种天气条件下生成的228条Bench2Drive格式评估路线；3）提出BoundaryFormer（BF）与BF++，通过slot attention联合预测车道/工作区边界多项式和驾驶轨迹，并引入独立轨迹解码器、度量地平面编码、类型化查询、长距离点锚、图像空间曲线细化及保守门控LiDAR融合等设计。

**方法**:  
方法上，BF使用基于Transformer的架构，以slot attention进行边界预测，并联合输出车道边界、工作区边界多项式及驾驶轨迹。消融实验发现，使用边界slot特征的独立轨迹解码器相比仅使用slot attention能显著改善轨迹预测。BF++进一步提供Camera与Camera+LiDAR两种变体，加入度量地平面编码、类型化边界/轨迹查询、长距离点锚、图像空间曲线细化以及保守门控LiDAR融合，以提升感知与规划性能。

**结果**:  
在评估冻结时四个模型共有的211条路线上，BF++-Camera和BF++-Camera+LiDAR分别取得63.0和64.4的Driving Score，高于SimLingo的59.3和TransFuser++（TF++）的26.1。BF++模型规模比SimLingo小40倍，比TF++小10倍以上，同时取得更高的Driving Score，验证了联合预测车道边界、工作区边界与驾驶轨迹的有效性。

**相关性与影响**:  
该论文对自动驾驶工作区场景的感知与规划具有重要意义，提供了面向工作区的大规模多模态数据集和闭环评估基准，缓解了公开数据稀缺与结构化几何监督不足的问题。其联合边界预测与轨迹规划的方法及轻量化高效模型，有望推动更安全、更可泛化的端到端自动驾驶系统在实际临时道路场景中的部署。

---


---

## 🌍 World Model 相关内容

### 1. Feeling Terrain Before Crossing: World Models for Off-Road Navigation **⭐⭐⭐⭐** (相关度: 96%, 质量: 0.9)

- **arXiv ID**: [2609.19863](https://arxiv.org/abs/2609.19863)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.19863)
- **作者**: E-In Son, Dong-Wook Kim, Ji-Hoon Hwang et al. (7 authors)
**评估**: 该论文聚焦于机器人导航中的世界模型，提出Feel-WM，通过引入本体感觉预测未来物理状态和失败风险，并与视觉场景预测联合规划。其核心贡献属于World Model范畴，而非单纯的图像/视频生成、蒸馏或训练推理基础设施。论文在真实越野数据和仿真中验证，支持轮式与足式平台，并部署于Husky山地路径，实验充分且具有实际机器人导航价值，作者工作有明确技术创新，因此判定为高质量。

**核心贡献**:  
该论文提出 Feel-WM，这是首个以本体感知为条件、同时预测未来视觉场景与未来物理感受的越野导航世界模型。它能够预测机器人未来的本体感知状态和失败风险，并在规划中结合场景预测与物理风险来评估动作序列。实验表明，Feel-WM 在开环规划和闭环崎岖地形导航中优于仅依赖视觉的导航世界模型。

**创新点**:  
首次将本体感知引入越野导航世界模型，使模型不仅预测相机将看到什么，还能预测机器人将感受到什么，包括打滑、倾斜、震动等机器人-地形交互结果。同时，模型从机器人自身经验中学习未来本体感知状态与失败风险，无需人工标签，并在规划分数中可分离地权衡失败风险与目标相似度。

**方法**:  
Feel-WM 以本体感知作为输入条件，构建越野导航世界模型，预测未来本体感知状态和失败风险，并与未来视觉场景预测联合展开。规划器对候选动作序列进行 rollout，同时评估预测的物理未来和场景未来，通过可分离评分综合失败风险与目标相似度来选择动作。模型训练依赖机器人自身经验，不需要人工标注，并在真实越野数据和仿真中验证。

**结果**:  
在真实越野数据和仿真实验中，Feel-WM 在开环规划与闭环崎岖地形导航任务上均优于仅视觉的导航世界模型，并覆盖轮式和腿式平台。部署在 Husky 机器人于山地小径上时，Feel-WM 可机载规划，提前预测前方崎岖地面并绕行，完成端到端策略失败的路线。

**相关性与影响**:  
该工作强调了越野导航中机器人-地形交互预测的重要性，将本体感知和失败风险纳入世界模型规划，为复杂非结构化环境下的自主导航提供了新思路。其方法有望提升轮式和腿式机器人在崎岖地形中的安全性与鲁棒性，对越野自动驾驶、野外机器人和基于世界模型的机器人规划具有潜在影响。

---

### 2. DexTouch-WM: Learning Action-Conditioned Tactile World Models from Human Touch for Dexterous Robot Manipulation **⭐⭐⭐⭐** (相关度: 92%, 质量: 0.9)

- **arXiv ID**: [2609.20649](https://arxiv.org/abs/2609.20649)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20649)
- **作者**: Yan Qin, Yue Chen, Wenwei Lin et al. (11 authors)
**评估**: 该论文提出 DexTouch-WM，一种动作条件化的触觉世界模型，用于从人类触觉交互中学习机器人灵巧操作预测模型。核心贡献在于跨具身触觉数据迁移、人类到机器人的动作重定向、以及联合预测RGB观测和双侧触觉动力学，属于世界模型/具身智能方向。论文包含真实机器人监督与人类交互数据 scaling 实验，并评估世界模型作为策略评估代理和合成轨迹生成器的用途，方法创新明确、实验较充分。虽然机器人灵巧操作相对专门，但世界模型和跨具身学习具有较高研究价值，不属于低质量或纯小众垂直应用。

**核心贡献**:  
论文提出DexTouch-WM，一种动作条件触觉世界模型，能够从可扩展的人类触觉交互中学习，并联合预测未来RGB观测与双侧触觉动力学。其核心洞察是：当触觉观测和动作空间兼容时，人类与机器人操作共享可迁移的接触动力学。实验表明，在固定5小时真机监督下，增加0到100小时人类交互可显著提升机器人域的视觉、几何和接触预测。

**创新点**:  
主要创新在于将人类触觉交互作为可扩展监督信号来学习灵巧机器人世界模型：在人类手和灵巧机器人手上部署共享传感布局的柔性压阻阵列，并将人类运动重定向到机器人动作空间，使人类交互可监督同一动力学模型。同时，模型耦合预训练视频专家与轻量触觉专家，引入解剖感知触觉token和对齐动作条件。

**方法**:  
方法包括：在人类与机器人手部使用共享布局的柔性压阻触觉阵列；将人类运动重定向到机器人动作空间以实现人机触觉与动作兼容；构建动作条件世界模型，联合预测未来RGB观测和双侧触觉动力学；采用预训练视频专家与轻量触觉专家耦合架构，并使用解剖感知触觉token与对齐动作条件。评估中固定5小时真实机器人监督，逐步增加人类交互数据至100小时，并测试世界模型作为策略评估代理环境及合成轨迹生成器的用途。

**结果**:  
在人到机器人扩展实验中，固定5小时真实机器人监督，将人类交互从0小时增加到100小时，尽管人类与机器人任务集不相交，仍在留出的机器人域视觉、几何和接触预测上取得显著提升。此外，世界模型可作为策略评估的替代环境，并能为真实机器人策略学习生成合成轨迹。

**相关性与影响**:  
该工作为接触丰富的灵巧机器人操作提供了一种利用可扩展人类触觉数据的新范式，有助于缓解真实机器人触觉数据采集成本高、难以规模化以及传感器具身耦合的问题。其潜在影响包括推动触觉世界模型、人机技能与动力学迁移、策略评估代理环境以及合成数据驱动的机器人策略学习等方向。

---

### 3. Astronex-World 1.0: Real-Time Interactive World Model Foundation **⭐⭐⭐⭐** (相关度: 90%, 质量: 0.8)

- **arXiv ID**: [2609.20034](https://arxiv.org/abs/2609.20034)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20034)
- **作者**: Xin Zhou, Cong Miao
**评估**: 该论文提出 'Astronex-World 1.0'，明确定位为实时交互式世界模型基础（World Model Foundation），核心在于基于文本或初始观测预测未来视觉状态，并支持帧对齐相机轨迹、连续动作和具身标识符控制，还能在 rollout 中插入文本事件。这符合世界模型的典型特征（可控、交互、用于具身智能/自动驾驶），因此归为 World_Model 而非单纯视频生成。技术创新明确：PRoPE 注入相机内参/外参、64 维动作流调制每层 Transformer、block-causal attention + cross-block KV caching 实现持久生成，以及五阶段训练路径与 DMD/DMD2 分布匹配蒸馏。实验较充分：在 WBench Navi 达 73.5、WBench Full 达 70.0，5B 模型超越 13.6B LongCat-Video 和 14B Helios，接近 22B LTX-2.3，且实现 832x480@24fps 实时流式生成，仅需两张 NVIDIA L20 48GB。方法新颖、结果可验证、工程价值高，非小众垂直领域，故判定为高质量论文。

**核心贡献**:  
本文提出了 Astronex-World 1.0，一个开放且可控的视频世界模型基础模型。模型可根据文本提示或初始观测，在帧对齐的相机轨迹、连续动作和具身标识条件下预测未来视觉状态，并支持在 rollout 指定位置插入文本事件。该工作同时提供双向全上下文生成模型和基于块因果注意力与跨块 KV 缓存的持久因果生成模型，并在实时交互与基准性能上取得突出表现。

**创新点**:  
主要创新在于将相机内外参、连续动作和具身标识统一注入视频世界模型，实现文本/图像条件下的可控未来预测；同时提出双向模型与块因果模型并存的基础模型家族，并支持在生成过程中插入文本事件。训练上采用五阶段路径，将双向控制能力迁移到块因果生成，并通过少步蒸馏和不对称 DMD/DMD2 分布匹配提升实时生成质量。

**方法**:  
模型基于 Wan2.2-TI2V-5B 先验，包含双向模型和带块因果注意力及跨块 KV 缓存的因果模型。PRoPE 用于注入相机内参和外参，64 维动作流调制每个 Transformer 层。五阶段训练包括：双向相机与动作控制、主干转换为块因果生成、少步学生蒸馏、混合域动态恢复，以及不对称 DMD/DMD2 分布匹配。所有训练阶段在两张 NVIDIA L20 48 GB GPU 上完成，因果模型可在单卡实时流式生成。

**结果**:  
因果模型可生成 832x480、24 fps 的视频，并在单张 NVIDIA L20 48 GB GPU 上实时流式运行。模型在 WBench Navi 上得分 73.5，在 WBench Full 上得分 70.0。在 Full 基准上，该 5B 模型超过 13.6B 的 LongCat-Video 和 14B 的 Helios，与 22B 的 LTX-2.3 差距在 1 分以内，并超过基于同一 5B 先验在 NVIDIA A100 上后训练的 YUME 1.5。

**相关性与影响**:  
该工作推动了可控视频世界模型向实时、交互式和具身智能方向发展，为文本/图像到视频生成、机器人仿真、自动驾驶和 embodied AI 提供了统一基础模型框架。其保留的动作输入输出接口支持后续在具身智能与自动驾驶场景中的后训练，具有较高的应用扩展潜力。

---

### 4. MM-Future: Multi-Mode Joint World-Action Modeling for Autonomous Driving **⭐⭐⭐⭐** (相关度: 88%, 质量: 0.8)

- **arXiv ID**: [2609.20377](https://arxiv.org/abs/2609.20377)
- **PDF**: [📄 Download](https://arxiv.org/pdf/2609.20377)
- **作者**: Shuai Liu, Hechangle Gong, Hao Jiang et al. (8 authors)
**评估**: 该论文提出 MM-Future，一个用于自动驾驶的 world-action model，联合建模决策与场景演化。其核心创新在于多模态（multi-mode）联合世界-动作建模：每个假设由结构化动作先验和独立的未来场景源初始化，通过 modality-aware diffusion Transformer 双向耦合演化，并压缩多视图视频为规划导向的 MM-Tokens，再用 future-conditioned proposal scorer 排序轨迹。这属于典型的 world model（世界模型）范畴——建模环境未来演化并与智能体动作耦合，而非纯内容生成或基础设施优化，因此归类为 World_Model。质量方面：方法具有明确的技术创新（多模态联合世界-动作建模 + 双向耦合扩散 Transformer + 结构化先验），在 NAVSIM navtest 上达到 94.0 PDMS/91.5 EPDMS，并在 HUGSIM 上完成零样本闭环评估（32.3 HD-Score），消融验证了多模态相对单模态和 action-only 变体的优势，实验较充分、结果具有说服力。自动驾驶虽属应用领域，但 world model 是当前学术界热点方向，受众广、参考价值高，不属于小众垂直领域，故判定为高质量论文。

**核心贡献**:  
MM-Future 提出一种面向自动驾驶的多模式联合世界-动作模型，能够在多模态不确定性下生成多个成对的场景-动作假设，并建模每一对内部的双向交互。该方法通过模态感知扩散 Transformer 联合演化动作先验与未来场景，并利用压缩的 MM-Tokens 支持高效多模式推演。实验表明其在 NAVSIM 和 HUGSIM 上取得领先性能，并验证了多模式联合建模优于单模式和纯动作建模。

**创新点**:  
核心创新在于多模式联合世界-动作建模：同时生成多个配对的未来场景与动作假设，并在每个假设内部建模场景演化与决策的双向耦合；引入结构化动作先验与独立未来场景源初始化，通过模态感知扩散 Transformer 共同演化；提出面向规划的多视图视频压缩表示 MM-Tokens，以及基于未来条件的候选轨迹评分器。

**方法**:  
MM-Future 从结构化动作先验和独立未来场景源初始化多组成对假设，使用模态感知扩散 Transformer 实现场景与动作的协同演化。为支持高效多模式 rollout，它将多视图视频压缩为面向规划的 MM-Tokens。最后，未来条件提案评分器结合共享历史上下文与成对预测未来，对轨迹候选进行排序。

**结果**:  
在 NAVSIM navtest 上达到 94.0 PDMS 和 91.5 EPDMS；在 HUGSIM 零样本闭环评估中取得 32.3 HD-Score。消融实验显示，相较于单模式变体和仅动作变体均有稳定提升，验证了多模式联合世界-动作建模的有效性。

**相关性与影响**:  
该工作推动了自动驾驶中世界模型与决策规划的结合，尤其关注多模态不确定性和场景-动作耦合问题。其多模式联合建模、高效规划表示和未来条件评分机制，对自动驾驶闭环规划、安全决策以及通用世界-动作模型研究具有重要参考价值和潜在影响。

---


---

## 📊 统计信息

| 类别 | 论文数量 | 占比 |
|------|----------|------|
| 🎨 AIGC 相关内容 | 0 | 0.0% |
| 🖼️ 图像/视频/全模态生成 | 10 | 9.1% |
| 🧠 大模型蒸馏与压缩 | 6 | 5.5% |
| ⚙️ 训练推理基础设施 | 4 | 3.6% |
| 🧠 Agent 相关内容 | 10 | 9.1% |
| 🌍 World Model 相关内容 | 4 | 3.6% |
| 其他 | 76 | 69.1% |
| **总计** | **110** | **100%** |
