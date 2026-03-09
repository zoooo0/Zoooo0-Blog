---
title: BestBlogs 第 85 期：Harness Engineering（全文翻译）
date: 2026-03-09
category: 技术
tags: [AI周报]
top: 11
---

# BestBlogs 第 85 期：Harness Engineering（全文翻译）

> 来源：BestBlogs.dev Newsletter  
> 原文链接：https://www.bestblogs.dev/newsletter/issue85

大家好，欢迎来到 BestBlogs.dev 第 85 期。

贯穿本期内容的一个关键词是：**Harness（驭使 / 驾驭 / 编排）**。

本周，martinfowler.com 上的两篇文章都在表达一个相近的判断：开发者的核心工作，正在从“亲手写代码”转向“为智能体搭建运行框架”——也就是规格说明、质量门禁、工作流指引，以及一整套让 Agent 可控、可复用、可演进的约束系统。中文播客里甚至说得更直接：**别再埋头干活了，先去给 AI 搭办公室。**

OpenAI 团队在 5 个月里用 Codex 生成了 100 万行代码、完成了 1500 个 PR，靠的并不是更强的模型本身，而是结构化知识库、严格架构约束与持续的系统整顿。随着 Agent 变得越来越能干，真正拉开差距的，不再只是“你用不用 AI”，而是“你会不会驾驭 AI”。

对 BestBlogs.dev 来说，我们最近也一直在围绕 AI Coding 深挖，推进 2.0 版本的建设。重点方向是自定义订阅源和个性化信息流，让每个人都能按自己的兴趣塑造阅读体验。同时，我也在基于开放 API 开发一系列 Skills，用于内容搜索、深度阅读和日常操作——目标只有一个：真正把“未来的阅读方式”驯服到可用、好用、长期可用。

下面是本周值得关注的 20 条内容。

## 目录

1. GPT-5.4 发布：OpenAI 首个真正统一的原生模型  
2. OpenAI 连夜把默认模型换成 GPT-5.3：重点是“去油腻”  
3. Qwen3.5 小尺寸模型来了  
4. FireRed-OCR 开源：新一代端到端 SOTA  
5. 开源大模型背后的架构逻辑  
6. Boris Cherny 谈 Claude Code 的诞生  
7. 软件工程中的 Humans and Agents in the Loop  
8. 设计优先协作（Design-First Collaboration）  
9. AI 编码的反思：从工具提效到范式迁移，还缺什么？  
10. OpenClaw 上下文压缩机制深度拆解  
11. 别再谈“10x 工程师”了：AI Agent 不是加速 SDLC，而是在终结它  
12. 1500 个 PR、零人工编码：Codex 驱动百万行代码实践  
13. 别工作了，先去给 AI 搭办公室  
14. 设计流程已经死了：Jenny Wen 谈新的替代方式  
15. Zapier 产品副总裁谈 800+ AI Agent 的组织实践  
16. Nano Banana 2 深度解析：更快、更好玩、更高质量  
17. AI 转型的四个阶段：个人、组织、产品与商业  
18. 孟岩对谈李继刚：人在 AI 时代如何安放自己  
19. 为什么 Cursor 已经死了？AI 海啸正在到来  
20. 2028 全球智能危机：最终谁来买单？

---

## 1. GPT-5.4 发布：OpenAI 首个真正统一的原生模型

**来源**：量子位  
**原文**：https://www.bestblogs.dev/en/article/6f17468b

OpenAI 的 GPT-5.4 首次把推理、编程、原生计算机操作、深度搜索和百万 token 上下文统一进了同一个模型里，而且并没有明显牺牲任何单项能力。

其中最突出的能力，是**原生计算机操作**：模型能读取屏幕截图、移动鼠标、敲击键盘，在 OSWorld 这类桌面任务基准上，已经超过普通人类平均水平。

另外，一个新的工具搜索机制把 Agent 场景下的 token 消耗降低了 47%，这很少见地实现了“能力更强、成本更低”同时成立。与此同时，GPT-5.3 Instant 也更注重使用体感而不是单纯跑分，把联网模式下的幻觉率降低了 26.8%，这对于把 ChatGPT 真正变成日常可靠工具，是很重要的一步。

![GPT-5.4 Released: OpenAI's First Unified Model, Truly Native](https://image.jido.dev/20260306013348_fb5421d8fc51628a29ab215487da1d12.webp)

---

## 2. OpenAI 连夜把默认模型换成 GPT-5.3：重点是“去油腻”

**来源**：51CTO 技术栈  
**原文**：https://www.bestblogs.dev/en/article/825a3674

GPT-5.3 Instant 没有继续执着于 benchmark 冠军，而是把重点放在**真实使用体验**上：少一点说教式免责声明，更敏锐地理解用户意图，更顺滑地结合搜索能力。

在联网场景下，它把幻觉率降低了 26.8%，这件事的意义其实很直接：不是模型更“炫”了，而是它更适合做一个你每天愿意用、也更敢信一点的工作助手。

![OpenAI Drops New Default GPT-5.3 Model Overnight!](https://image.jido.dev/20260306051541_a371b70.png)

---

## 3. Qwen3.5 小尺寸模型来了

**来源**：通义大模型  
**原文**：https://www.bestblogs.dev/en/article/a8c5578b

Qwen3.5 一次发布了 0.8B 到 9B 的四个小模型，全部采用 Apache 2.0 协议，并支持在消费级 GPU 上微调。

其中，4B 版本在多模态与 Agent 能力上尤其亮眼，9B 版本则已经逼近不少更大模型的表现。这类模型的意义，不只是“小而省”，而是它们开始真正适合垂直场景部署：成本可控、迭代更快、工程落地门槛更低。

![Qwen3.5 Small-Size Models Are Here!](https://image.jido.dev/20260306052225_c568be5.png)

---

## 4. FireRed-OCR 开源：新一代端到端 SOTA

**来源**：小红书技术 REDtech  
**原文**：https://www.bestblogs.dev/en/article/44e28dc2

FireRed-OCR 通过三阶段渐进式训练，把 Qwen3-VL-2B 微调成了一个专门做文档解析的模型，在 OmniDocBench v1.5 上拿到 92.94%，位列端到端方案第一。

它支持公式、表格、手写内容等复杂文档元素，已经不是“玩具 OCR”，而是接近工业级效果。这说明一个很有意思的趋势：与其盲目堆参数，不如做有针对性的训练设计，小模型一样能在专门场景里打出高质量结果。

![FireRed-OCR Open Source Release](https://image.jido.dev/20260306051816_4418840.jpeg)

---

## 5. 开源大模型背后的架构逻辑

**来源**：ByteByteGo Newsletter  
**原文**：https://www.bestblogs.dev/en/article/e94961a3

这篇文章简明对比了六个主流开源大模型，梳理了它们在 MoE 设计、注意力机制取舍以及后训练策略上的差异。

它的价值不在于帮你背参数表，而在于提醒你：选模型时真正该看的，不是宣传词，而是这些底层架构决策会如何影响推理成本、吞吐效率、效果稳定性以及后续微调空间。

对于现在正在做开源模型选型的人来说，这是篇很实用的“地图型文章”。

![The Architecture Behind Open-Source LLMs](https://image.jido.dev/20260302170628_0b745b95-60a3-498f-baf4-cfef00f0f9d4_3042x1626.png)

---

## 6. Boris Cherny 谈 Claude Code 的诞生

**来源**：The Pragmatic Engineer  
**原文**：https://www.bestblogs.dev/en/video/8f3d453

Pragmatic Engineer 对谈了 Claude Code 的创造者 Boris Cherny，回顾了它如何从 Anthropic 内部的一个边缘项目，变成增长最快的开发者工具之一。

Boris 现在每天会提交 20 到 30 个 PR，而且全部由 AI 生成，自己一行代码都不手改。节目里还聊到一个很关键的话题：在 AI 时代，代码评审的意义正在改变，工程师真正重要的能力也正在被重写。

另外，Anthropic 内部曾对是否公开发布 Claude Code 有过争论，而 Claude Code 背后的分层安全架构也被详细提到。整段访谈很像是一份“AI 原生编程工作流”的现场口述史。

![Building Claude Code with Boris Cherny](https://image.jido.dev/20260305070617_hqdefault.jpg)

---

## 7. 软件工程中的 Humans and Agents in the Loop

**来源**：Martin Fowler  
**原文**：https://www.bestblogs.dev/en/article/03980cf2

文章把 AI 协作中的开发者位置分成三类：

- **Human outside the loop**：人基本不介入，只做 vibe coding；
- **Human inside the loop**：人对每个产出都逐项审核；
- **Human on the loop**：人不再手工介入所有细节，而是负责构建和维护约束系统。

作者认为，真正合理的位置是第三种：开发者的核心工作，不再是亲手写每一段代码，而是搭建 Agent 运行所依赖的“缰绳系统”——规格、质量检查、流程说明，以及如何让 Agent 自己参与改进这些规则。

文章最后提出一个很重要的概念：**agentic flywheel**。Agent 不只是执行任务，还会持续评估并优化它所处的 harness。这比“AI 帮我写点代码”要深得多。

![Humans and Agents in Software Engineering Loops](https://image.jido.dev/20260206060522_donkey-card.png)

---

## 8. 设计优先协作（Design-First Collaboration）

**来源**：Martin Fowler  
**原文**：https://www.bestblogs.dev/en/article/0c84d443

这篇文章指出了 AI 编码里一个经常被忽略的问题：**AI 会直接跳过设计阶段**，悄悄把大量架构决策埋进生成代码里，结果让代码评审变成一种疲惫的“逆向推理”。

作者提出的解决办法是 Design-First：在真正开始生成代码之前，先逐层对齐五个层面——能力、组件、交互、接口契约、实现。

这不是在增加流程主义，而是在降低认知负担。因为很多问题应该在抽象层被解决，而不是等落成代码后再从细节里反推架构。对常用 AI 编码工具的人来说，这是一套很值得吸收的方法论。

---

## 9. AI 编码的反思：从工具提效到范式迁移，还缺什么？

**来源**：大淘宝技术  
**原文**：https://www.bestblogs.dev/en/article/7088e92f

天猫工程团队的判断很到位：企业 AI Coding 的真正瓶颈，不是 Agent 执行力不够，而是**复杂任务目标无法准确传达给 AI**。

他们的解法是建立分层统一的专家知识库，用系统性的“降熵”方式，让 AI 更精准理解业务、工程结构与规则边界。由此，AI Coding 才能从“工具层的提效”走向“知识驱动的智能开发”。

这和 OpenAI 用 Codex 的内部实践，其实讲的是同一个道理：当系统规模上来之后，真正值钱的不是单次输出质量，而是能不能把知识、约束和架构长期沉淀下来。

![Reflections on AI Coding](https://image.jido.dev/20260302124143_b705d48.png)

---

## 10. OpenClaw 上下文压缩机制深度拆解

**来源**：腾讯云开发者  
**原文**：https://www.bestblogs.dev/en/article/83d23d4f

这可能是中文里对 OpenClaw 上下文管理机制最完整的一次拆解。

文章梳理了它的三层防线：

1. **预防性裁剪**  
2. **基于 LLM 的总结压缩**  
3. **溢出后的恢复机制**

同时还分析了不同操作对 Provider KV cache 成本的影响。对任何正在做长会话 Agent 的人来说，这篇文章都很值得看，因为它讲的不是抽象概念，而是“如何让系统真的跑得久、跑得稳、跑得起”。

![Deep Dive into OpenClaw's Context Window Compression](https://image.jido.dev/20260304033618_281b31f.jpeg)

---

## 11. 别再谈“10x 工程师”了：AI Agent 不是加速 SDLC，而是在终结它

**来源**：InfoQ 中文  
**原文**：https://www.bestblogs.dev/en/article/fa13c8a0

这篇文章的论点很锋利：AI Agent 不是在给传统软件开发生命周期踩油门，而是在直接改写、甚至终结它。

作者逐项拆解了 SDLC 的每个环节：需求变成迭代副产物，设计转向协同涌现，测试与代码同步生成，PR 审查逐渐变成旧时代的仪式，而可观测性则从被动看板变成主动反馈闭环。

结论也很干脆：最终真正留下来的核心能力，可能只剩下两项——**上下文工程** 与 **可观测性**。这篇文章值得严肃对待，而不是当作标题党看过去。

![Stop Talking About '10x Developers'](https://image.jido.dev/20260302001659_9ebbfe7.png)

---

## 12. 1500 个 PR、零人工编码：Codex 驱动百万行代码实践

**来源**：AI 前线  
**原文**：https://www.bestblogs.dev/en/article/997b2ba8

OpenAI 工程团队在 5 个月里，用 Codex 生成了 100 万行代码、完成 1500 个 PR，而且没有一行代码是人工直接写出来的。

文章总结出它之所以能跑通的关键：

- 结构化知识管理  
- 刚性架构约束  
- Agent 可访问的可观测工具  
- 周期性的代码熵清理

这篇文章最有价值的地方，是它给出了一份“Agent 驱动开发如何规模化”的现实蓝图。它告诉你，重点不只是模型会不会写，而是整个工程系统是否允许 AI 持续、稳定、低失控地写。

---

## 13. 别工作了，先去给 AI 搭办公室

**来源**：AI 炼金术  
**原文**：https://www.bestblogs.dev/en/podcast/d72dca9

两位 AI 创业者在这期播客里聊到一个很具时代感的工作流变化：在 Agent 时代，人的工作正在从“执行”转为“布置环境”。

他们提炼出的日常流程是：

**规划 → 运行 → 验证**

真正稀缺的，不再是你敲代码有多快，而是你的判断带宽有多大、你为 AI 搭好的工作环境有多成熟。这期内容特别适合那些已经开始用 AI 编程，但还没完全意识到“岗位本质正在迁移”的人。

![Stop Working! Go Set Up an Office for AI!](https://image.jido.dev/20251127045527_cef25284)

---

## 14. 设计流程已经死了：Jenny Wen 谈新的替代方式

**来源**：Lenny's Podcast  
**原文**：https://www.bestblogs.dev/en/video/516ace7

Anthropic 设计负责人 Jenny Wen 讲了一个很有冲击力的判断：**传统设计流程已经死了**。

不是设计师主动放弃它，而是因为工程师借助 AI 提升了交付速度，逼得设计流程必须重构。她自己的工作时间分配也发生了明显变化：过去 60% 到 70% 时间花在高保真稿和精修 mockup 上，现在只剩 30% 到 40%，更多时间转向与工程师直接结对，甚至自己下场改代码。

她认为，设计工作正在分化成两条线：

- 实时支持工程执行的协作型设计  
- 面向未来 3 到 6 个月的方向型设计

这对设计师来说不是简单的“效率升级”，而是职业角色的重新定义。

![The design process is dead. Here’s what’s replacing it.](https://image.jido.dev/20260306045125_hqdefault.jpg)

---

## 15. Zapier 产品副总裁谈 800+ AI Agent 的组织实践

**来源**：Product School  
**原文**：https://www.bestblogs.dev/en/video/209e104

Zapier 的产品副总裁分享了他们在内部管理 800 多个 AI Agent 的第一手经验。

最值得记住的一点是：**技术采用** 和 **业务转型** 是两件不同的事，不能混为一谈。组织层面的真正变化，必须由管理层亲自使用 AI 工具、亲自推动工作方式迁移，才可能落地。

在他看来，传统工作流和 Agent 工作流的本质差别，就在于后者具备了**推理与动态改道**能力。也就是说，AI 不再只是自动化脚本，而是在某种程度上开始承担“临场判断”。

![Zapier VP of Product on Orchestrating 800+ AI Agents](https://image.jido.dev/20260306021824_hqdefault.jpg)

---

## 16. Nano Banana 2 深度解析：更快、更好玩、更高质量

**来源**：阿真 Irene  
**原文**：https://www.bestblogs.dev/en/article/8dce015c

这篇内容详细体验了 Gemini 3.1 Flash Image 的表现，结论是：文本渲染更准了，角色一致性更稳了，还支持了 1:4、1:8 这种极端长宽比。

文章里还附带了大量现成可用的提示词，对于想快速做设计、做内容实验的人来说，参考价值很高。它代表的是另一条演进路线：不是一味追求“万能”，而是把生成式模型打磨成一个高频可用、可快速迭代的创作工具。

![Deep Dive into Nano Banana 2](https://image.jido.dev/20260304135841_b7cbc2e.png)

---

## 17. AI 转型的四个阶段：个人、组织、产品与商业

**来源**：AI 炼金术  
**原文**：https://www.bestblogs.dev/en/podcast/b741844

这期播客指出，AI 产品最常见的错误，不是技术不够强，而是把 AI 生硬塞进功能里，却没有真正帮助用户完成具体工作。

节目提出了一个三步框架：

**拆解 → 重构 → 颠覆**

同时梳理了四类 AI 原生创业路径：

- 打开新市场  
- 包装成熟技术  
- 售卖基础设施  
- 改造传统行业

整体很务实，讲的不是空泛愿景，而是产品和商业如何真正完成 AI 转型。

---

## 18. 孟岩对谈李继刚：人在 AI 时代如何安放自己

**来源**：无人知晓  
**原文**：https://www.bestblogs.dev/en/podcast/17ad4f7

这场长达三小时的对谈，从一个非常有力量的命题展开：

**工业革命夺走了体力劳动，AI 正在夺走脑力劳动，那么人剩下的是什么？**

他们给出的答案是：**心力**。也就是意志、直觉、审美，以及一种难以完全被系统化的主体性。

对谈随后延伸到很多问题：向量世界的本质、商业模式从“织网”转向“打井”、人到底该借助 AI 放大自我，还是干脆退出思考，以及教育如何从“灌输知识”转向“点燃火种”。

里面有两句话尤其值得单独拎出来想：

- **你的信息流，就是你的命运**  
- **提示词是有形状的**

这不是一场技术节目，而更像是一场关于“人类还剩下什么”的时代讨论。

![E45 Meng Yan in Conversation with Li Jigang](https://image.jido.dev/20260303232418_440f92c.png)

---

## 19. 为什么 Cursor 已经死了？AI 海啸正在到来

**来源**：跨国串门儿计划  
**原文**：https://www.bestblogs.dev/en/podcast/31911b6

Insight Partners 联合创始人 Jerry Murdock 的观点相当激进：真正的核心不是 Cursor 这类工具，而是**自主 Agent**。

他认为，这一波浪潮里，按席位收费的 SaaS 模式会逐渐让位于按消耗计费，而白领岗位被替代的问题，很可能在两年内就会变成政治议题。

这段讨论未必全都正确，但它至少逼着你面对一个现实：AI 的冲击已经不只是“效率变高”，而是会直接改写软件、组织和就业市场的基本规则。

---

## 20. 2028 全球智能危机：最终谁来买单？

**来源**：Datawhale  
**原文**：https://www.bestblogs.dev/en/article/6fedf503

这篇文章用一个设想中的 2028 年视角，推演了一条 AI 冲击经济系统的左尾风险链条：

**白领失业 → 消费萎缩 → 私募信贷违约 → 房贷市场承压**

这不是预言，而是一个相当系统的风险推演框架。它提醒我们，AI 的影响不只会落在工作台、IDE 和聊天窗口里，也可能穿透到更大的宏观经济结构中，并形成没有自然刹车的负反馈回路。

如果你关心 AI 的社会后果，而不只关心模型性能，这篇文章值得认真读一遍。

![The 2028 Global Intelligence Crisis: Who Pays the Price?](https://image.jido.dev/20260306050154_e7d5bf7.jpeg)

---

## 结语

这一期最核心的启发，其实可以浓缩成一句话：

**未来最重要的能力，不只是使用 AI，而是搭建能够稳定驾驭 AI 的系统。**

不管是写代码、做设计、做产品，还是经营组织，很多岗位都在从“亲自执行”转向“构建框架、设定边界、维护质量、持续调优”。谁能把这套 harness 搭得更稳，谁就更有可能在下一轮变化里占到主动。

如果这一期让你冒出了新的想法，那它就值了。
