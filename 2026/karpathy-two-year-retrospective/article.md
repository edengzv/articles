# Karpathy 两年全记录：从 llm.c 到 autoresearch，一个天才程序员的 AI 进化论

> 如果你只关注一个 AI 人物的 GitHub，那应该是 @karpathy。

2024 年初，Andrej Karpathy 离开了 Tesla。在此之前，他是 Tesla 的 AI 总监，斯坦福博士，深度学习领域的标志性人物——他的 Neural Networks Zero to Hero 系列课程影响了数以十万计的 AI 学习者。

离开 Tesla 后的 600 多天里，Karpathy 没有闲着。他发布了 **12 个开源项目**（累计超过 25 万星），发表了 **7 场重要演讲和访谈**，写下了多篇深度博客。他的每一个项目都在做同一件事：**把复杂的东西变简单，让每个人都能理解 AI 的本质。**

这篇文章按时间线梳理 Karpathy 过去两年的所有重要活动，提取他对 AI 的核心判断，并探讨这些判断给程序员群体带来的启示。

---

## 一、时间线：从 llm.c 到 autoresearch

### 2024 年：简化一切

#### 2 月 · minbpe —— 200 行代码讲透 BPE 算法

GitHub 星标：10,465

Karpathy 发布了 minbpe——一个极简的 Byte Pair Encoding（BPE）算法实现。BPE 是 GPT-4 等模型使用的分词算法（tiktoken），但之前没有人用"人能读懂"的方式实现过它。

> "Production tokenizers like tiktoken operate on chunks of characters for efficiency, but the simplest possible tokenizer just assigns one integer to each unique character."

这个项目延续了 Karpathy 的一贯风格：**不是造轮子，而是拆轮子给你看。**

#### 4 月 · llm.c —— 用纯 C 训练 GPT

GitHub 星标：29,804

这是 Karpathy 2024 年最轰动的项目。llm.c 用纯 C/CUDA 实现了 LLM 的完整训练流程，不需要 PyTorch（245MB），不需要 Python（107MB）。

> "LLMs in simple, pure C/CUDA with no need for 245MB of PyTorch or 107MB of cPython."

llm.c 的意义不在于性能（它比 PyTorch Nightly 还快约 7%），而在于它**打破了"训练 LLM 必须依赖庞大框架"的迷思**。一个本科生读完 llm.c 的代码，就能理解 GPT 训练的全部细节。

#### 5 月 · LLM101n —— Let's Build a Storyteller

GitHub 星标：36,884

继 llm.c 之后，Karpathy 推出了 LLM101n——一个面向初学者的 LLM 教学项目。目标是"从零开始构建一个讲故事的人"。

这个项目延续了他在 YouTube 上 Zero to Hero 系列的教学理念：**从标量开始，一步步构建完整的神经网络。**

#### 6 月 · build-nanogpt —— 视频 + 代码的 nanoGPT 教程

GitHub 星标：4,966

把 nanoGPT 的构建过程做成了视频 + 代码的完整教程。这是 Karpathy 教育理念的又一次实践——**代码就是最好的文档，视频就是最好的课堂。**

#### 🎤 演讲：「Software Is Changing (Again)」

在 Tech Talks Weekly #65 中，Karpathy 提出了一个核心观点：**软件正在再次发生变化。**

2015 年他写过一篇著名的文章「Software 2.0」，认为神经网络将取代传统软件。2024 年，他再次强调：**LLM 正在让编程变成"说话"**。这不是编程的终结，而是编程范式的又一次迁移。

---

### 2025 年：从工具到生态

#### 10 月 · nanochat —— 100 美元训练一个 GPT-2

GitHub 星标：52,910

nanochat 是 Karpathy 迄今为止最实用的项目。它提供了一个完整的 LLM 训练框架，可以在单张 GPU 上完成分词、预训练、微调、评估和推理。

> "You can train your own GPT-2 capability LLM for only $48 (~2 hours of 8XH100 GPU node) and then talk to it in a familiar ChatGPT-like web UI. On a spot instance, the total cost can be closer to ~$15."

**15 美元，训练一个 GPT-2 级别的模型。** 这个数字在 2019 年是 43,000 美元。六年时间，成本降低了近 3000 倍。

nanochat 还维护了一个 "Time-to-GPT-2 Leaderboard"，激励社区竞争最短训练时间。截至 2026 年 3 月，最快纪录已经压缩到 **1.65 小时**。

#### 11 月 · reader3 —— 和 LLM 一起读书

GitHub 星标：3,586

reader3 演示了如何轻松地与 LLM 一起阅读书籍。Karpathy 在这个项目中探索了一个新的交互范式：**不是让 LLM 总结书，而是让 LLM 和你一起"读"书。**

#### 11 月 · llm-council —— LLM 议会

GitHub 星标：18,237

这是 Karpathy 最有趣的项目之一。与其向一个 LLM 提问，不如把多个 LLM 组成一个"议会"：

1. **第一阶段**：所有 LLM 分别回答问题
2. **第二阶段**：每个 LLM 匿名评审其他 LLM 的答案
3. **第三阶段**：由一个"主席"LLM 综合所有意见，给出最终回答

> "This project was 99% vibe coded as a fun Saturday hack."

Karpathy 用 "vibe coded" 来形容这个项目——**代码不再是精心设计的工程，而是随性的创作。** 他在 README 中写道：

> "Code is ephemeral now and libraries are over, ask your LLM to change it in whatever way you like."

**代码是短暂的，库已经过时了。让你的 LLM 随便改。**

#### 12 月 · hn-time-capsule —— 十年后的 Hacker News 时光机

GitHub 星标：616

用 LLM 分析十年前的 Hacker News 讨论，看看哪些预测准确、哪些翻车。这个项目看似有趣，实则暗含 Karpathy 对 AI 预测能力的思考——**用历史检验判断力。**

#### 🎤 演讲与访谈密集期

**Dwarkesh Podcast：「AGI is still a decade away」**

Karpathy 在这期播客中表达了他对 AGI 时间线的核心判断：**AGI 仍然需要十年。** 不是明年，不是五年，而是十年。

> "AI researcher Andrej Karpathy says agentic AI is years away from practical reality."

他区分了"能用的 AI"和"真正的 agentic AI"。当前的 LLM 可以写代码、聊天、做翻译，但距离真正的自主智能体还有本质差距。

**「We're summoning ghosts, not building animals」**

这是 Karpathy 最诗意的一个判断。他认为当前 LLM 的训练方式更像是**"召唤幽灵"（summoning ghosts）**——通过海量数据让模型"涌现"出能力，而不是**"建造动物"（building animals）**——从第一性原理出发构建真正的智能。

> 这个比喻暗示：我们当前的方法虽然有效，但可能不是通向真正智能的正确路径。

**KDnuggets：「Unlock the Secrets of LLMs in 60 Minutes」**

60 分钟的 LLM 深度入门，Karpathy 用他标志性的教学方式，解释了 LLM 的能力、未来潜力和安全风险。

---

### 2026 年：自主研究时代

#### 1 月 · rustbpe —— 缺失的 tiktoken 训练代码

GitHub 星标：446

用 Rust 实现了 BPE 训练算法，填补了 tiktoken 没有开源训练代码的空白。

#### 2 月 · microgpt —— 200 行 Python 训练 GPT

这是 Karpathy 的"艺术品"。他在博客中写道：

> "This is a brief guide to my new art project microgpt, a single file of 200 lines of pure Python with no dependencies that trains and inferences a GPT. This file contains the full algorithmic content of what is needed: dataset of documents, tokenizer, autograd engine, a GPT-2-like neural network architecture, the Adam optimizer, training loop, and inference loop. Everything else is just efficiency."

**200 行纯 Python，零依赖，训练并推理一个 GPT。** 包含数据集、分词器、自动微分引擎、GPT-2 架构、Adam 优化器、训练循环和推理循环。

> "I cannot simplify this any further."

Karpathy 说他已经无法再简化了。这是他对 LLM 本质理解的终极表达——**剥离所有效率优化后，LLM 的核心算法只需要 200 行代码。**

#### 3 月 · autoresearch —— AI 研究 AI

GitHub 星标：78,896（目前 Karpathy 星标最高的项目）

这是 Karpathy 2026 年最具野心的项目。autoresearch 的核心思想是：**让 AI 自主研究如何训练更好的 AI。**

> "One day, frontier AI research used to be done by meat computers in between eating, sleeping, having other fun, and synchronizing once in a while using sound wave interconnect in the ritual of 'group meeting'. That era is long gone. Research is now entirely the domain of autonomous swarms of AI agents running across compute cluster megastructures in the skies."

Karpathy 用幽默的笔调描述了 AI 自主研究的未来：

- 给 AI 一个真实的 LLM 训练环境
- AI 自主修改代码、训练 5 分钟、检查结果、保留或丢弃
- 第二天早上，你看到的是一整夜的实验日志和（ hopefully）更好的模型

> "The agents claim that we are now in the 10,205th generation of the code base, in any case no one could tell if that's right or wrong as the 'code' is now a self-modifying binary that has grown beyond human comprehension. This repo is the story of how it all began."

**这是 Karpathy 对 AI 研究未来形态的预言：人类研究者将不再是主力，AI 自主研究将成为常态。**

#### 🎤 演讲：Sequoia Ascent 2026

在 Sequoia Ascent 2026 上，Karpathy 发表了关于 Agentic Engineering 的演讲，提出了 **5 个预测**：

1. **Agentic AI 需要多年才能真正实用**——不是工具升级，而是范式转变
2. **LLM 的训练成本将继续指数级下降**——nanochat 的 15 美元只是开始
3. **自主 AI 研究将改变 AI 开发的节奏**——从"人驱动"到"AI 驱动"
4. **多模型协作将成为标配**——llm-council 只是一个开始
5. **编程将进一步"自然语言化"**——"Coding by Speaking" 将成为主流

---

## 二、Karpathy 的七个核心判断

梳理 Karpathy 过去两年的所有公开内容，我们可以提取出他对 AI 的七个核心判断：

### 判断一：AGI 仍然遥远，至少十年

Karpathy 在 Dwarkesh Podcast 中明确表示：**AGI 仍然需要十年**。他反对"明年就有 AGI"的炒作，认为当前的 LLM 虽然在某些任务上表现出色，但距离真正的通用智能还有本质差距。

> 他的理由：当前的 LLM 是"召唤幽灵"而非"建造动物"——我们通过缩放和训练让能力"涌现"，但这不等于构建了真正的理解力。

### 判断二：Agentic AI 离实用还有距离

Karpathy 认为，虽然 agentic AI 是方向，但**离真正的实用还有数年**。当前的 AI agent 在简单任务上表现不错，但在复杂、多步骤、需要长期规划的任务上仍然不可靠。

### 判断三：LLM 的本质可以极度简化

从 minbpe（200 行 BPE）到 llm.c（纯 C 训练）到 microgpt（200 行 Python 训练 GPT），Karpathy 反复证明了一个观点：**LLM 的核心算法并不复杂，复杂的是工程优化。**

> "Everything else is just efficiency."——剥离效率优化后，LLM 的本质只需要 200 行代码。

### 判断四：训练成本将呈指数级下降

nanochat 的 15 美元训练 GPT-2 级别模型，autoresearch 的 5 分钟实验周期——Karpathy 用实际行动证明：**LLM 的训练成本正在以远超摩尔定律的速度下降。**

### 判断五：自主 AI 研究是必然趋势

autoresearch 是 Karpathy 对 AI 研究未来的具象化表达。他认为，**AI 研究将越来越多地由 AI 自己完成**——人类设定方向，AI 执行实验、分析结果、迭代改进。

### 判断六：代码是短暂的，库已经过时

在 llm-council 的 README 中，Karpathy 写下了一句震动开发者圈子的话：

> "Code is ephemeral now and libraries are over, ask your LLM to change it in whatever way you like."

**传统的软件工程范式正在瓦解。** 当 LLM 可以即时生成、修改、调试代码时，维护代码库的意义在下降，"描述需求"的能力在上升。

### 判断七：多模型协作优于单一模型

llm-council 的设计哲学是：**没有哪个 LLM 能永远是最好的。** 通过让多个 LLM 协作、互相评审，可以得到比单一模型更好的答案。这暗示了未来 AI 应用的架构方向——不是选一个最好的模型，而是让多个模型协作。

---

## 三、给程序员群体的启示

Karpathy 的每一个项目、每一场演讲，都在向程序员群体传递同一个信息。以下是我总结的五个启示：

### 启示一：理解本质，而非依赖框架

Karpathy 的所有项目都在做同一件事：**剥离框架，展示本质。**

- llm.c 告诉你：没有 PyTorch，你也能训练 GPT
- minbpe 告诉你：没有 tiktoken，你也能实现 BPE
- microgpt 告诉你：没有任何依赖，200 行 Python 就能训练 GPT

**启示：不要把你的技能绑定在某个框架上。** 框架会过时，API 会改变，但对算法本质的理解永远不会过时。Karpathy 在 2015 年做的 RNN 教程，到今天仍然有价值——因为 Transformer 的本质和 RNN 是相通的。

### 启示二：简化是一种超能力

Karpathy 的项目有一个共同特点：**极度简化。** 他不是在做"更完整"的工具，而是在做"更简单"的解释。

- llm.c 比 PyTorch 简单 100 倍
- microgpt 比 nanoGPT 简单 100 倍
- nanochat 的 `--depth` 参数把复杂的超参数调优简化为一个数字

**启示：在你的领域里，你能不能做出"micro"版本？** 不是更强大的工具，而是更简单的解释。这种能力在 AI 时代越来越稀缺，也越来越有价值。

### 启示三：拥抱"vibe coding"，但不要放弃理解

Karpathy 是第一个公开说"代码是短暂的"的一线 AI 研究者。他用 llm-council 演示了"vibe coding"——一个周六下午，让 LLM 帮你写一个完整的应用。

但请注意：**Karpathy 的 vibe coding 建立在他对 AI 的深刻理解之上。** 他知道 LLM 在做什么、能做什么、不能做什么。他不是在盲目信任 LLM，而是在有意识地利用 LLM。

**启示：拥抱 AI 辅助编程，但不要放弃对底层原理的理解。** 当你能用 200 行 Python 写一个 GPT 时，你才有资格说"代码是短暂的"。

### 启示四：教育是最好的投资

Karpathy 离开 Tesla 后，没有去创业，没有去 VC，而是继续做他一直在做的事：**教育。**

- llm.c、minbpe、microgpt 都是教育项目
- YouTube 的 Zero to Hero 系列持续更新
- nanochat 的 README 本身就是一篇完整的 LLM 教程

**启示：在 AI 时代，最好的学习方式不是上课，而是动手。** Karpathy 的教学理念始终如一：给你能跑的代码，让你看到效果，再解释原理。这种"从做中学"的方式，比任何理论课程都有效。

### 启示五：保持长期主义

Karpathy 的简化之路不是一天走成的：

- micrograd（2018）→ makemore（2020）→ nanoGPT（2022）→ llm.c（2024）→ microgpt（2026）

**八年的时间，他在做同一件事：把 LLM 变简单。** 从标量微分（micrograd）到 200 行 GPT（microgpt），每一步都在前一步的基础上构建。

**启示：找到一个你相信的长期方向，然后持续投入。** AI 领域变化很快，但有些东西是恒定的——对本质理解的追求、对简化解释的执着、对教育的热情。

---

## 四、结语：Karpathy 的"道"

如果要用一句话概括 Karpathy 过去两年的核心信息，那就是：

> **AI 没有你想象的那么神秘，也没有你希望的那么神奇。**

他没有被 AGI 炒作裹挟，也没有陷入 AI 悲观主义。他选择了一条最朴素的路：**写代码，做教育，把复杂的东西变简单。**

在 autoresearch 的 README 开头，他写了一段看似幽默实则深刻的话：

> "One day, frontier AI research used to be done by meat computers in between eating, sleeping, having other fun, and synchronizing once in a while using sound wave interconnect in the ritual of 'group meeting'. That era is long gone."

**"肉脑计算机"（meat computers）——这是 Karpathy 对人类研究者的自嘲。** 但他也清楚地知道，"肉脑计算机"仍然是设定方向、提出问题的主体。AI 可以自主研究，但研究方向仍然是人选择的。

Karpathy 的"道"，就是在这两者之间找到平衡：**既不过度迷信 AI，也不低估 AI。用代码说话，用教育传播，用简化证明理解。**

对于程序员来说，这或许是最好的启示：**不要焦虑 AI 会不会取代你，而去思考你能不能用 AI 做更多以前做不到的事。**

---

「注」本文所有 GitHub 星标数据截至 2026 年 5 月 5 日

#Karpathy #LLM #开源 #AI观点 #程序员
