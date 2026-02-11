<h1 align="center">
Awesome-Chinese-Video-Generation
</h1>
<p align="center">
<b>An Awesome Collection for Video Generation in Chinese / 收集和梳理中文视频生成相关</b>
</p>
<p align="center">
  <a href="https://github.com/leeguandong/Awesome-Chinese-Video-Generation/stargazers"> <img src="https://img.shields.io/github/stars/leeguandong/Awesome-Chinese-Video-Generation.svg?style=popout-square" alt="GitHub stars"></a>
  <a href="https://github.com/leeguandong/Awesome-Chinese-Video-Generation/issues"> <img src="https://img.shields.io/github/issues/leeguandong/Awesome-Chinese-Video-Generation.svg?style=popout-square" alt="GitHub issues"></a>
  <a href="https://github.com/leeguandong/Awesome-Chinese-Video-Generation/forks"> <img src="https://img.shields.io/github/forks/leeguandong/Awesome-Chinese-Video-Generation.svg?style=popout-square" alt="GitHub forks"></a>
</p>

> A curated list of Chinese Video Generation resources, including open-source models, applications, datasets, and tutorials focused on Chinese text-to-video generation.

本项目旨在收集和梳理中文视频生成相关的开源模型、应用、数据集及教程等资料，主要关注支持中文的视频生成模型和算法！

如果本项目能给您带来一点点帮助，麻烦点个⭐️吧～

同时也欢迎大家贡献本项目未收录的开源模型、应用、数据集等。提供新的仓库信息请发起PR，并按照本项目的格式提供仓库链接、star数，简介等相关信息，感谢~

## 目录

- [1. 中文视频生成模型](#1-中文视频生成模型)
  - [1.1 开源模型汇总](#11-开源模型汇总)
  - [1.2 开源模型](#12-开源模型)
  - [1.3 闭源模型](#13-闭源模型)
- [2. 测评](#2-测评)
  - [2.1 评测基准](#21-评测基准)
  - [2.2 评测工具](#22-评测工具)
  - [2.3 排行榜](#23-排行榜)
- [3. 数据集](#3-数据集)
  - [3.1 开源训练数据集](#31-开源训练数据集)
  - [3.2 评测/标注数据集](#32-评测标注数据集)
- [Star History](#star-history)
- [License](#license)

## 1. 中文视频生成模型

### 1.1 开源模型汇总

| 模型 | 参数量 | 架构 | 文本编码器 | 最大分辨率 | 中文提示词 | 主要能力 |
|------|--------|------|-----------|-----------|-----------|---------|
| CogVideo | 9.4B | 3D Transformer | CogLM | - | 支持 | T2V |
| CogVideoX | 2B / 5B | 3D DiT | T5 | 720p | 支持 | T2V, I2V |
| Open-Sora | 11B | DiT | T5 | 720p | 有限 | T2V, I2V |
| Open-Sora-Plan | - | WF-VAE + Skiparse DiT | T5 | 720p | 有限 | T2V |
| HunyuanVideo | 13B | 双流DiT | CLIP + LLM | 720p | 支持 | T2V, I2V |
| HunyuanVideo 1.5 | 8.3B | DiT | CLIP + LLM | 720p | 支持 | T2V, I2V |
| Wan2.1 | 1.3B / 14B | DiT + 3D VAE | umT5 | 720p | 支持 | T2V, I2V, VACE, V2A |
| Wan2.2 | 5B / 14B (MoE) | MoE DiT | umT5 | 720p+ | 支持 | T2V, I2V, S2V |
| SkyReels-V2 | 14B | MLLM + Diffusion Forcing | - | 720p | 支持 | T2V, I2V, 无限时长 |
| SkyReels-V3 | 19B | 统一多模态框架 | - | 720p+ | 支持 | I2V, A2V, V2V |
| Step-Video-T2V | 30B | DiT | Step-LLM | 720p | 支持 | T2V, TI2V |
| Goku | - | Rectified Flow Transformer | - | 720p | 支持 | T2V, I2V |

### 1.2 开源模型

* **CogVideo**：
  * 地址：https://github.com/THUDM/CogVideo ![](https://img.shields.io/github/stars/THUDM/CogVideo.svg)
  * 简介：CogVideo是由清华大学（THUDM）和智谱AI于2022年发布的首个大规模中文文本到视频生成模型，参数量9.4B。模型基于CogView2的预训练文本到图像生成模型，利用多帧率分层训练策略，有效地对文本到视频的对齐进行建模。CogVideo原生支持中文提示词输入，是最早具备中文视频生成能力的开源模型之一。

* **CogVideoX**：
  * 地址：https://github.com/THUDM/CogVideo ![](https://img.shields.io/github/stars/THUDM/CogVideo.svg)
  * 简介：CogVideoX是CogVideo的现代化升级版本，提供2B和5B两个参数规模。采用3D Diffusion Transformer架构，支持中英双语提示词输入。CogVideoX1.5-5B变体支持更高分辨率和更长视频生成。模型在中文场景下也被称为"清影"。相比初代CogVideo，CogVideoX在视频质量、运动连贯性和文本理解能力上都有显著提升。

* **Open-Sora**：
  * 地址：https://github.com/hpcaitech/Open-Sora ![](https://img.shields.io/github/stars/hpcaitech/Open-Sora.svg)
  * 简介：Open-Sora由HPC-AI Tech（ColossalAI团队）开发，旨在复现Sora的能力。Open-Sora 2.0（2025年3月发布）参数量达11B，采用可扩展的Diffusion Transformer架构，支持灵活的分辨率和时长。支持文本到视频和图像到视频生成，最长可生成15秒720p视频。训练成本仅约20万美元，是同类商业模型的十分之一。完全开源，包括训练代码、数据管线和模型权重。中文提示词支持有限，主要面向英文，但可通过翻译使用。

* **Open-Sora-Plan**：
  * 地址：https://github.com/PKU-YuanGroup/Open-Sora-Plan ![](https://img.shields.io/github/stars/PKU-YuanGroup/Open-Sora-Plan.svg)
  * 简介：Open-Sora-Plan由北京大学袁粒团队主导开发，旨在以开源方式复现Sora的视频生成能力。采用Wavelet-Flow Variational Autoencoder（WFVAE）+ Joint Image-Video Skiparse Denoiser + Condition Controller架构。v1.3.0引入了WFVAE、提示词优化器、数据过滤策略、稀疏注意力和分桶训练策略。支持在24GB显存内进行高分辨率长时长视频生成。中文提示词支持有限，主要面向英文。

* **HunyuanVideo**：
  * 地址：https://github.com/Tencent-Hunyuan/HunyuanVideo ![](https://img.shields.io/github/stars/Tencent-Hunyuan/HunyuanVideo.svg)
  * 简介：HunyuanVideo由腾讯混元团队于2024年12月发布，参数量13B，是发布时最大的开源视频生成模型。采用统一的Diffusion Transformer架构，具有Full Attention机制，设计为双流到单流的混合结构，允许视觉和文本token先独立处理再融合。支持文本到视频（最长5秒720p）和图像到视频生成。通过提示词改写模型支持中文提示词输入。构建了完整的数据管理、图像-视频联合训练和高效基础设施框架。

* **HunyuanVideo 1.5**：
  * 地址：https://huggingface.co/tencent/HunyuanVideo-1.5
  * 简介：HunyuanVideo 1.5是腾讯混元视频模型的轻量化版本，参数量8.3B。在保持视觉质量和运动连贯性达到SOTA水平的同时，显著减少了参数量。支持文本到视频和图像到视频生成，仅需约14GB显存即可运行，适合消费级GPU使用。

* **Wan2.1**：
  * 地址：https://github.com/Wan-Video/Wan2.1 ![](https://img.shields.io/github/stars/Wan-Video/Wan2.1.svg)
  * 简介：Wan2.1由阿里巴巴通义实验室于2025年3月发布，提供1.3B和14B两个参数规模。采用Diffusion Transformer架构配合3D VAE潜空间，使用交叉注意力嵌入文本条件，并加入完整的时空注意力机制增强复杂动态捕捉能力。文本编码器采用umT5，支持512个token长度。训练数据包含数十亿图像和视频。Wan-VAE仅127M参数，遵循MagViT-v2设计，利用流匹配框架建模图片和视频领域的统一去噪过程。训练采用渐进式策略：先在低分辨率256p文本到图像预训练，然后逐步引入高分辨率视频模态，经过三个阶段（256p→480p→720p）的图像-视频联合训练。1.3B模型仅需约8.2GB显存，适合消费级GPU。支持文本到视频、图像到视频、VACE（视频全能创作与编辑）、视频到音频等多种能力。是首个能在视频中原生生成中英文文字的视频模型。

* **Wan2.2**：
  * 地址：https://github.com/Wan-Video/Wan2.2 ![](https://img.shields.io/github/stars/Wan-Video/Wan2.2.svg)
  * 简介：Wan2.2是通义万相视频模型的重大升级版本，提供5B（混合MoE）和14B（MoE）两个参数规模。首个采用混合专家（MoE）架构的开源视频生成模型，将模型分为高噪声专家和低噪声专家：高噪声专家负责视频的整体布局，低噪声专家负责细节完善。两个专家各约14B参数，总计27B，但每步仅激活14B，在保持计算成本不变的情况下大幅提升模型参数量和生成质量。基于高压缩率的3D VAE实现时间和空间的高压缩比，支持在消费级显卡上快速生成高清视频。基于精心标注的美学数据（光影、色彩、构图等），模型能生成具有专业电影质感的视频内容。支持文本到视频、图像到视频、主体到视频（S2V）和动画模式。

* **SkyReels-V2**：
  * 地址：https://github.com/SkyworkAI/SkyReels-V2 ![](https://img.shields.io/github/stars/SkyworkAI/SkyReels-V2.svg)
  * 简介：SkyReels-V2由昆仑万维（SkyworkAI）开发，参数量14B，是首个AI短剧创作模型，专注于以人为中心的电影级视频生成。结合了多模态大语言模型（MLLM）、多阶段预训练、强化学习和Diffusion Forcing技术。支持无限时长的自回归视频生成，能够理解专业电影语言。提供720P的文本到视频和图像到视频模型（SkyReels-V2-DF-14B-720P、SkyReels-V2-I2V-14B-720P）。SkyReels-V1基于HunyuanVideo微调，V2则是全新架构。

* **SkyReels-V3**：
  * 地址：https://huggingface.co/Skywork/SkyReels-V3-A2V-19B
  * 简介：SkyReels-V3参数量19B，采用统一多模态框架，在单一架构内支持三种生成范式。支持参考图像到视频、视频到视频扩展、音频引导视频生成等能力。将视觉、听觉和叙事生成统一在一个框架下，是昆仑万维视频生成系列的最新版本。

* **Step-Video-T2V**：
  * 地址：https://github.com/stepfun-ai/Step-Video-T2V ![](https://img.shields.io/github/stars/stepfun-ai/Step-Video-T2V.svg)
  * 简介：Step-Video-T2V由阶跃星辰（StepFun）于2025年2月发布，参数量30B，是最大的开源视频生成模型之一。采用Diffusion Transformer架构，支持中英双语提示词输入。可生成最长204帧的视频。同时提供Step-Video-TI2V变体，支持文本+图像到视频生成。

* **Goku**：
  * 简介：Goku由字节跳动与香港大学联合开发，于2025年2月发布。采用Rectified Flow Transformer架构，是一种基于流的视频生成基础模型。支持文本到视频和图像到视频生成，在GenEval上达到0.76分，在DPG-Bench上达到83.65分。代码和权重已开源。

### 1.3 闭源模型

* **快手可灵 Kling**：
  * 地址：https://kling.kuaishou.com/
  * 简介：可灵（Kling）是快手推出的AI视频生成平台，是全球领先的商业视频生成模型之一。从Kling 1.0发展到Kling 3.0（2026年1月发布），经历了多个重要版本迭代。Kling O1（2025年12月）是首个统一多模态AI视频模型，采用多模态视觉语言（MVL）框架，集成7合1视频引擎。Kling 3.0支持全模态输入输出（文本、图像、音频、视频）。核心能力包括文本到视频、图像到视频、多参考元素库、视频编辑、口型同步、原生音视频生成（Kling 2.6+）和多镜头生成。原生支持中文提示词。

* **生数科技 Vidu**：
  * 地址：https://www.vidu.com/
  * 简介：Vidu由生数科技（ShengShu Technology）开发，采用自研的U-ViT架构。从Vidu 1.0发展到Vidu Q3（2026年初），支持文本到视频、图像到视频、口型同步、模板等功能。视频生成速度极快，可在10秒内完成。Vidu Q3支持多镜头叙事。提供API平台（MaaS），支持MCP集成。每个片段最长可达16秒。原生支持中文提示词。

* **字节即梦 Seedance**：
  * 地址：https://jimeng.jianying.com/
  * 简介：Seedance是字节跳动的旗舰视频生成模型，驱动即梦（Jimeng）AI创作平台。Seedance 2.0（2026年2月发布）是多模态视频生成模型，可同时处理图像、视频、音频和文本，支持多场景叙事和同步音频，生成2K分辨率视频，速度比1.0版本快约30%。支持最多4种输入类型同时使用：最多9张图像、3个视频、3个音频文件。Seedance 1.0曾在Artificial Analysis视频生成排行榜上排名第一（2025年6月）。底层研究模型Seaweed（Seed-Video）约7B参数，采用Diffusion Transformer架构。原生支持中文提示词。

* **PixVerse**：
  * 地址：https://pixverse.ai/
  * 简介：PixVerse由AISphere开发（阿里巴巴投资），最新版本为PixVerse V5.6和PixVerse-R1。支持文本到视频、图像到视频，原生4K生成，多镜头摄像机控制。全球用户超过6000万，月活用户1600万。PixVerse-R1是实时世界模型，支持交互式视频生成，内容可即时响应用户输入。支持中文提示词。

* **阿里通义万相（商业版）**：
  * 地址：https://tongyi.aliyun.com/wanxiang/
  * 简介：通义万相是阿里云的AI视频生成服务，Wan系列（Wan2.1/2.2/2.5/2.6）是其开源版本。商业云服务提供额外功能和更高质量的输出。Wan2.5增加了原生音视频同步能力，支持1080p 24fps和电影级摄像机控制。Wan2.6（2025年12月发布）是中国首个具备角色扮演能力的AI视频模型，支持多镜头叙事、原生音频生成、视频风格迁移，最长可生成15秒视频。原生支持中文提示词。

## 2. 测评

### 2.1 评测基准

* **VBench / VBench-2.0**：
  * 地址：https://github.com/Vchitect/VBench ![](https://img.shields.io/github/stars/Vchitect/VBench.svg)
  * 简介：目前最全面的视频生成模型评测基准套件。VBench 1.0从16个维度评估视频生成质量，包括主体身份一致性、运动平滑度、时序闪烁、空间关系、文本-视频对齐、逐帧美学等。VBench-2.0进一步从5个关键维度评估内在忠实度：人体保真度、可控性、创造力、物理规律和常识。由中国研究团队（Vchitect）开发，发表于CVPR和NeurIPS。

* **EvalCrafter**：
  * 地址：https://github.com/evalcrafter/EvalCrafter ![](https://img.shields.io/github/stars/evalcrafter/EvalCrafter.svg)
  * 简介：全面的文本到视频生成模型评测框架，使用17个客观指标评估视觉质量、内容质量、运动质量和文本-视频对齐。包含700条基于真实用户数据分析的多样化提示词。发表于CVPR 2024。

* **VMBench**：
  * 简介：感知对齐的视频运动生成评测基准，是首个从人类感知对齐角度评估运动质量的基准。专注于评估视频生成模型的运动生成能力是否符合人类的视觉感知预期。

* **Video-Bench**：
  * 简介：人类对齐的视频生成评测基准，采用基于MLLM的评估框架，在与人类偏好的对齐度上超越了传统的基于指标和基于LLM的评测基准。

### 2.2 评测工具

* **VBench评测工具包**：
  * 地址：https://github.com/Vchitect/VBench ![](https://img.shields.io/github/stars/Vchitect/VBench.svg)
  * 简介：VBench不仅是评测基准，也提供了完整的评测工具包。支持自动化评估视频生成模型在多个维度上的表现，包括视频质量、运动连贯性、文本对齐等。可用于对比不同模型的性能。

* **EvalCrafter评测工具**：
  * 地址：https://github.com/evalcrafter/EvalCrafter ![](https://img.shields.io/github/stars/evalcrafter/EvalCrafter.svg)
  * 简介：提供17个客观评估指标的自动化计算工具，覆盖视觉质量、内容质量、运动质量和文本-视频对齐四大类别。支持批量评估和结果可视化。

### 2.3 排行榜

* **LM Arena Video Arena**：
  * 地址：https://lmarena.ai/leaderboard/video
  * 简介：基于真实用户投票的Elo排名系统，是评估AI视频生成模型的金标准。采用盲测对比方式，由用户选择更好的生成结果来计算排名。截至2026年初，文本到视频已有132K+投票，图像到视频已有269K+投票。分别提供文本到视频和图像到视频的独立排行榜。

* **Artificial Analysis Video Generation**：
  * 地址：https://artificialanalysis.ai/text-to-video
  * 简介：独立的AI模型分析平台，从视频质量（Elo评分）、生成速度、价格等多维度对主流视频生成模型进行基准测试和排名。Seedance 1.0曾于2025年6月排名第一。覆盖Kling、Wan、HunyuanVideo、Seedance等中国模型。

* **VBench Leaderboard**：
  * 地址：https://vchitect.github.io/VBench-project/
  * 简介：基于VBench自动化评测的排行榜，从16+维度对开源和闭源视频生成模型进行评分和排名。提供详细的各维度得分对比，帮助研究者全面了解模型性能。

## 3. 数据集

### 3.1 开源训练数据集

* **Youku-mPLUG（优酷多模态数据集）**：
  * 简介：目前最大的中文视频-语言数据集，包含约1000万中文视频-文本对，从4亿原始视频中筛选而来，覆盖45个多样化类别。专为视频-语言预训练和评测设计，是中文视频生成研究的重要数据资源。

* **VATEX（Video And TEXt）**：
  * 地址：https://eric-xw.github.io/vatex-website/
  * 简介：大规模多语言视频描述数据集，包含41,250个视频和825,000组描述。提供中英双语字幕标注，是少数同时支持中文和英文的视频-文本数据集之一。可用于中文视频生成模型的训练和评测。

* **Panda-70M**：
  * 地址：https://snap-research.github.io/Panda-70M/
  * 简介：大规模视频-描述数据集，包含7000万视频-描述对。描述由多个跨模态教师模型生成，质量较高。虽然主要为英文，但被广泛用于中文视频生成研究中。发表于CVPR 2024。

* **InternVid**：
  * 简介：大规模多语言视频-文本数据集，包含中文在内的多种语言。可用于多模态理解和生成任务的训练。被多个中文视频生成模型用作训练数据的一部分。

### 3.2 评测/标注数据集

* **VATEX评测集**：
  * 地址：https://eric-xw.github.io/vatex-website/
  * 简介：VATEX数据集的测试集部分，提供中英双语视频描述标注，可用于评估视频生成模型在中文场景下的文本-视频对齐能力。

* **VICTOR数据集**：
  * 简介：包含超过1000万完整视频及中文文本描述，用于对比式多模态预训练。可作为中文视频生成模型的评测参考数据集。



## Star History

<a href="https://star-history.com/#leeguandong/Awesome-Chinese-Video-Generation&Date">

  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=leeguandong/Awesome-Chinese-Video-Generation&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=leeguandong/Awesome-Chinese-Video-Generation&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=leeguandong/Awesome-Chinese-Video-Generation&type=Date" />
  </picture>

</a>

## License

This project is licensed under the [MIT License](LICENSE).




