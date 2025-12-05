# Chapter 9: Learning and Adaptation | <mark>第 9 章：学习与适应</mark>

Learning and adaptation are pivotal for enhancing the capabilities of artificial intelligence agents. These processes enable agents to evolve beyond predefined parameters, allowing them to improve autonomously through experience and environmental interaction. By learning and adapting, agents can effectively manage novel situations and optimize their performance without constant manual intervention. This chapter explores the principles and mechanisms underpinning agent learning and adaptation in detail.

<mark>学习与适应能力是提升智能体性能的关键所在。通过这些机制，智能体能够突破预设参数的束缚，在与环境交互的过程中通过经验积累实现自我进化。具备学习与适应能力的智能体，可以在无需人工持续干预的情况下，自主应对新场景并优化自身表现。本章将深入探讨智能体学习与适应的核心原理及其实现机制。</mark>

---

## The Big Picture | <mark>整体概览</mark>

Agents learn and adapt by changing their thinking, actions, or knowledge based on new experiences and data. This allows agents to evolve from simply following instructions to becoming smarter over time.

<mark>智能体通过不断积累的经验和数据来调整自身的认知模式、行为策略和知识结构，从而实现学习与适应。这一演化过程让智能体能够从最初的「指令执行者」逐步成长为具备自主学习能力的智能系统。</mark>

- **Reinforcement Learning**: Agents try actions and receive rewards for positive outcomes and penalties for negative ones, learning optimal behaviors in changing situations. Useful for agents controlling robots or playing games.

  <mark><strong>强化学习</strong>：智能体通过尝试不同行动并根据结果获得奖惩，学习在动态环境中的最优行为策略。这种方法特别适用于控制机器人或游戏智能体等场景。</mark>

- **Supervised Learning**: Agents learn from labeled examples, connecting inputs to desired outputs, enabling tasks like decision-making and pattern recognition. Ideal for agents sorting emails or predicting trends.

  <mark><strong>监督学习</strong>：智能体从标记好的示例中学习输入与期望输出之间的映射关系，从而实现决策制定和模式识别等任务。这种方法非常适合邮件分类或趋势预测等应用场景。</mark>

- **Unsupervised Learning**: Agents discover hidden connections and patterns in unlabeled data, aiding in insights, organization, and creating a mental map of their environment. Useful for agents exploring data without specific guidance.

   <mark><strong>无监督学习</strong>：智能体在未标记数据中自主发现隐藏的模式和结构关系，从而构建起对环境的内在理解和知识体系。这种方法特别适用于缺乏明确标注、需要自主探索的数据分析场景。</mark>

- **Few-Shot/Zero-Shot Learning with LLM-Based Agents**: Agents leveraging LLMs can quickly adapt to new tasks with minimal examples or clear instructions, enabling rapid responses to new commands or situations.

   <mark><strong>基于 LLM 的少样本/零样本学习</strong>：利用大语言模型的智能体只需少量示例或明确指令就能快速适应新任务，能够对新的命令或情况做出迅速响应。</mark>

- **Online Learning**: Agents continuously update knowledge with new data, essential for real-time reactions and ongoing adaptation in dynamic environments. Critical for agents processing continuous data streams.

   <mark><strong>在线学习</strong>：智能体能够利用新数据持续更新知识库，这对于需要实时反应和动态适应的场景至关重要。这种方法对处理连续数据流的智能体尤为关键。</mark>

- **Memory-Based Learning**: Agents recall past experiences to adjust current actions in similar situations, enhancing context awareness and decision-making. Effective for agents with memory recall capabilities.

   <mark><strong>基于记忆的学习</strong>：智能体通过回忆过往经验来调整当前类似情境下的行为决策，增强上下文感知能力和决策质量。这种方法对具备记忆回溯能力的智能体效果显著。</mark>

Agents adapt by changing strategy, understanding, or goals based on learning. This is vital for agents in unpredictable, changing, or new environments.

<mark>智能体通过学习不断调整策略、认知或目标来实现适应。这一能力对于在不可预测、动态变化或全新环境中运行的智能体至关重要。</mark>

**Proximal Policy Optimization (PPO)** is a reinforcement learning algorithm used to train agents in environments with a continuous range of actions, like controlling a robot's joints or a character in a game. Its main goal is to reliably and stably improve an agent's decision-making strategy, known as its policy.

<mark><strong>近端策略优化（PPO）</strong> 是一种强化学习算法，主要用于训练需要连续动作输出的智能体，例如控制机器人关节或游戏角色。其核心目标是可靠且稳定地改进智能体的决策策略。</mark>

The core idea behind PPO is to make small, careful updates to the agent's policy. It avoids drastic changes that could cause performance to collapse. Here's how it works:

<mark>PPO 的核心思想是对智能体策略进行小幅、谨慎的更新，避免剧烈变化导致性能崩溃。其工作原理如下：</mark>

1. **Collect Data**: The agent interacts with its environment (e.g., plays a game) using its current policy and collects a batch of experiences (state, action, reward).

   <mark><strong>数据收集</strong>：智能体使用当前策略与环境交互（如玩游戏），收集一批经验数据（状态、动作、奖励）。</mark>

2. **Evaluate a "Surrogate" Goal**: PPO calculates how a potential policy update would change the expected reward. However, instead of just maximizing this reward, it uses a special "clipped" objective function.

   <mark><strong>替代目标评估</strong>：PPO 计算潜在策略更新对预期奖励的影响，但并非简单最大化奖励，而是使用特殊的「剪辑」目标函数。</mark>

3. **The "Clipping" Mechanism**: This is the key to PPO's stability. It creates a "trust region" or a safe zone around the current policy. The algorithm is prevented from making an update that is too different from the current strategy. This clipping acts like a safety brake, ensuring the agent doesn't take a huge, risky step that undoes its learning.

   <mark><strong>剪辑机制</strong>：这是 PPO 算法稳定性的关键所在。它在当前策略周围创建一个「信任区域」或安全范围，防止算法进行与当前策略差异过大的更新。这种剪辑机制如同安全刹车，确保智能体不会因冒险的大幅调整而破坏已有的学习成果。</mark>

In short, PPO balances improving performance with staying close to a known, working strategy, which prevents catastrophic failures during training and leads to more stable learning.

<mark>简而言之，PPO 算法在性能改进与保持策略稳定性之间取得平衡，有效防止训练过程中的灾难性失败，能够实现更稳定的学习效果。</mark>

**Direct Preference Optimization (DPO)** is a more recent method designed specifically for aligning Large Language Models (LLMs) with human preferences. It offers a simpler, more direct alternative to using PPO for this task.

<mark><strong>直接偏好优化（DPO）</strong> 是一种较新的方法，专门用于使大语言模型（LLM）与人类偏好保持一致。与 PPO 相比，它提供了更简单、更直接的解决方案。</mark>

To understand DPO, it helps to first understand the traditional PPO-based alignment method:

<mark>要理解 DPO，首先需要了解传统的基于 PPO 的对齐方法：</mark>

- The PPO Approach (Two-Step Process) | <mark>PPO 方法（两步流程）</mark>

1. **Train a Reward Model**: First, you collect human feedback data where people rate or compare different LLM responses (e.g., "Response A is better than Response B"). This data is used to train a separate AI model, called a reward model, whose job is to predict what score a human would give to any new response.

   <mark><strong>奖励模型训练</strong>：首先收集人类反馈数据，让人们对不同的大语言模型响应进行评分或比较（例如「响应 A 优于响应 B」）。这些数据用于训练一个独立的奖励模型，其任务是预测人类对任何新响应的评分。</mark>

2. **Fine-Tune with PPO**: Next, the LLM is fine-tuned using PPO. The LLM's goal is to generate responses that get the highest possible score from the reward model. The reward model acts as the "judge" in the training game.

   <mark><strong>PPO 微调</strong>：接下来使用 PPO 算法对大语言模型进行微调。其中大语言模型的目标是生成能获得奖励模型最高评分的响应，奖励模型则作为训练过程中的「裁判」角色。</mark>

This two-step process can be complex and unstable. For instance, the LLM might find a loophole and learn to "hack" the reward model to get high scores for bad responses.

<mark>这种两步流程可能存在复杂性和不稳定性问题。例如，大语言模型可能会找到漏洞并学会「欺骗」奖励模型，生成评分高但质量差的响应。</mark>

- The DPO Approach (Direct Process) | <mark>DPO 方法（直接流程）</mark>

1. DPO skips the reward model entirely. Instead of translating human preferences into a reward score and then optimizing for that score, DPO uses the preference data directly to update the LLM's policy.

   <mark>DPO 完全跳过奖励模型环节。它不将人类偏好转换为奖励分数再进行优化，而是直接使用偏好数据更新 LLM 的策略。</mark>

2. It works by using a mathematical relationship that directly links preference data to the optimal policy. It essentially teaches the model: "Increase the probability of generating responses like the preferred one and decrease the probability of generating ones like the disfavored one."

   <mark>它通过一种数学关系直接将偏好数据与最优策略关联起来，本质上是在教导模型：「提高生成类似首选响应的概率，降低生成不受欢迎响应的概率。」</mark>

In essence, DPO simplifies alignment by directly optimizing the language model on human preference data. This avoids the complexity and potential instability of training and using a separate reward model, making the alignment process more efficient and robust.

<mark>本质上，DPO 通过直接在人类偏好数据上优化语言模型来简化对齐过程。这避免了训练和使用独立奖励模型带来的复杂性和潜在不稳定性，使对齐过程更加高效和稳健。</mark>

---

## Practical Applications & Use Cases | <mark>实际应用场景</mark>

Adaptive agents exhibit enhanced performance in variable environments through iterative updates driven by experiential data.

<mark>自适应智能体通过经验数据驱动的迭代更新，在动态环境中展现出卓越的性能提升，以下是一些典型应用场景。</mark>

- **Personalized assistant agents** refine interaction protocols through longitudinal analysis of individual user behaviors, ensuring highly optimized response generation.

   <mark><strong>个性化助理智能体</strong>：通过对用户行为的长期分析优化交互协议，确保生成高度定制化的响应。</mark>

- **Trading bot agents** optimize decision-making algorithms by dynamically adjusting model parameters based on high-resolution, real-time market data, thereby maximizing financial returns and mitigating risk factors.

  <mark><strong>交易机器人智能体</strong>：基于高频实时市场数据动态调整模型参数，优化决策算法以最大化财务回报并降低风险。</mark>

- **Application agents** optimize user interface and functionality through dynamic modification based on observed user behavior, resulting in increased user engagement and system intuitiveness.

   <mark><strong>应用智能体</strong>：根据用户行为数据动态调整界面和功能，提高用户参与度和系统易用性。</mark>

- **Robotic and autonomous vehicle agents** enhance navigation and response capabilities by integrating sensor data and historical action analysis, enabling safe and efficient operation across diverse environmental conditions.

   <mark><strong>机器人和自主车辆智能体</strong>：整合传感器数据和历史行为分析，增强导航和响应能力，实现在各种环境条件下的安全高效运行。</mark>

- **Fraud detection agents** improve anomaly detection by refining predictive models with newly identified fraudulent patterns, enhancing system security and minimizing financial losses.

   <mark><strong>欺诈检测智能体</strong>：利用新发现的欺诈模式持续优化预测模型，提高异常检测能力，增强系统安全性并减少财务损失。</mark>

- **Recommendation agents** improve content selection precision by employing user preference learning algorithms, providing highly individualized and contextually relevant recommendations.

   <mark><strong>推荐智能体</strong>：采用用户偏好学习算法提高内容选择精度，提供高度个性化和上下文相关的推荐服务。</mark>

- **Game AI agents** enhance player engagement by dynamically adapting strategic algorithms, thereby increasing game complexity and challenge.

   <mark><strong>游戏 AI 智能体</strong>：动态调整策略算法增强玩家体验，增加游戏的复杂性和挑战性。</mark>

- **Knowledge Base Learning Agents**: Agents can leverage Retrieval Augmented Generation (RAG) to maintain a dynamic knowledge base of problem descriptions and proven solutions (see Chapter 14). By storing successful strategies and challenges encountered, the agent can reference this data during decision-making, enabling it to adapt to new situations more effectively by applying previously successful patterns or avoiding known pitfalls.

   <mark><strong>知识库学习智能体</strong>：智能体可利用检索增强生成（RAG）技术构建动态知识库，用于存储问题描述和经过验证的解决方案（详见第 14 章）。在决策时，智能体会参考这些历史经验——包括成功的策略和遭遇的挑战，从而能够复用有效模式、规避已知陷阱，更好地适应新情况。</mark>

---

## Case Study: The Self-Improving Coding Agent (SICA) | <mark>案例研究：具备自我改进能力的编码智能体（SICA）</mark>

**The Self-Improving Coding Agent (SICA)**, developed by Maxime Robeyns, Laurence Aitchison, and Martin Szummer, represents an advancement in agent-based learning, demonstrating the capacity for an agent to modify its own source code. This contrasts with traditional approaches where one agent might train another; SICA acts as both the modifier and the modified entity, iteratively refining its code base to improve performance across various coding challenges.

<mark>由 Maxime Robeyns、Laurence Aitchison 和 Martin Szummer 开发的具备自我改进能力的编码智能体（SICA）标志着智能体学习领域的重大突破，它展示了智能体能够自主修改自身源代码的非凡能力。与传统的「一个智能体训练另一个智能体」模式不同，SICA 既是修改者又是被修改对象，通过不断迭代优化自身代码库，持续提升在各类编码任务中的表现。</mark>

SICA's self-improvement operates through an iterative cycle (see Fig.1). Initially, SICA reviews an archive of its past versions and their performance on benchmark tests. It selects the version with the highest performance score, calculated based on a weighted formula considering success, time, and computational cost. This selected version then undertakes the next round of self-modification. It analyzes the archive to identify potential improvements and then directly alters its codebase. The modified agent is subsequently tested against benchmarks, with the results recorded in the archive. This process repeats, facilitating learning directly from past performance. This self-improvement mechanism allows SICA to evolve its capabilities without requiring traditional training paradigms.

<mark>SICA 的自我改进通过迭代循环机制实现（见图 1）。每轮迭代的流程如下：首先，SICA 回顾历史版本库及各版本的基准测试表现，根据综合考量成功率、运行时间和计算成本的加权评分，选出表现最优的版本。然后，基于对历史数据的分析，识别潜在的改进点并直接修改代码库。修改后的新版本会立即接受基准测试，测试结果被记录到版本库中。这一循环往复的过程，使 SICA 能够直接从历史表现中学习，无需依赖传统的训练范式即可持续进化自身能力。</mark>

![Fig.1: SICA's self-improvement, learning and adapting based on its past versions](/images/chapter09_fig1.png)

Fig.1: SICA's self-improvement, learning and adapting based on its past versions

<mark>图 1：SICA 基于历史版本进行自我改进、学习与适应</mark>

SICA underwent significant self-improvement, leading to advancements in code editing and navigation. Initially, SICA utilized a basic file-overwriting approach for code changes. It subsequently developed a "Smart Editor" capable of more intelligent and contextual edits. This evolved into a "Diff-Enhanced Smart Editor," incorporating diffs for targeted modifications and pattern-based editing, and a "Quick Overwrite Tool" to reduce processing demands.

<mark>SICA 经历了显著的自我改进，在代码编辑和导航方面取得了重大进展。最初，SICA 采用基本的文件覆盖方式进行代码修改。随后开发了「智能编辑器」，能够进行更智能的上下文相关编辑。这进一步发展为「差异增强智能编辑器」，结合差异分析进行针对性修改和基于模式的编辑，并开发了「快速覆盖工具」以减少处理需求。</mark>

SICA further implemented "Minimal Diff Output Optimization" and "Context-Sensitive Diff Minimization," using Abstract Syntax Tree (AST) parsing for efficiency. Additionally, a "SmartEditor Input Normalizer" was added. In terms of navigation, SICA independently created an "AST Symbol Locator," using the code's structural map (AST) to identify definitions within the codebase. Later, a "Hybrid Symbol Locator" was developed, combining a quick search with AST checking. This was further optimized via "Optimized AST Parsing in Hybrid Symbol Locator" to focus on relevant code sections, improving search speed (see Fig. 2).

<mark>SICA 进一步实现了「最小差异输出优化」和「上下文敏感差异最小化」，利用抽象语法树（AST）解析提高效率。此外，还添加了「智能编辑器输入规范化器」。在导航方面，SICA 自主开发了「AST 符号定位器」，利用代码的结构图（AST）识别代码库中的定义。后来又开发了「混合符号定位器」，结合快速搜索和 AST 检查。通过「混合符号定位器中的优化 AST 解析」进一步优化，专注于相关代码部分，提高搜索速度（见图 2）。</mark>

![Performance across iterations](/images/chapter09_fig2.png)

Fig.2 : Performance across iterations. Key improvements are annotated with their
corresponding tool or agent modifications. (courtesy of Maxime Robeyns , Martin
Szummer , Laurence Aitchison)

<mark>图 2：各迭代周期的性能表现。图中标注了关键改进及其对应的工具或智能体修改。（致谢：Maxime Robeyns、Martin Szummer、Laurence Aitchison）</mark>

SICA's architecture comprises a foundational toolkit for basic file operations, command execution, and arithmetic calculations. It includes mechanisms for result submission and the invocation of specialized sub-agents (coding, problem-solving, and reasoning). These sub-agents decompose complex tasks and manage the LLM's context length, especially during extended improvement cycles.

<mar模型>SICA 的架构包含基本文件操作、命令执行和算术计算的基础工具包。它提供结果提交机制和专用子智能体（编码、问题解决和推理）的调用接口。这些子智能体负责分解复杂任务并管理大语言模型的上下文长度，特别是在长时间的改进周期中。</mar模型

An asynchronous overseer, another LLM, monitors SICA's behavior, identifying potential issues such as loops or stagnation. It communicates with SICA and can intervene to halt execution if necessary. The overseer receives a detailed report of SICA's actions, including a callgraph and a log of messages and tool actions, to identify patterns and inefficiencies.

<mark>异步监督者是另一个 LLM，负责监控 SICA 的行为，识别循环或停滞等潜在问题。它与 SICA 保持通信，并在必要时进行干预以停止执行。监督者接收 SICA 行为的详细报告，包括调用图和消息、工具操作日志，以识别模式和低效环节。</mark>

SICA's LLM organizes information within its context window, its short-term memory, in a structured manner crucial to its operation. This structure includes a System Prompt defining agent goals, tool and sub-agent documentation, and system instructions. A Core Prompt contains the problem statement or instruction, content of open files, and a directory map. Assistant Messages record the agent's step-by-step reasoning, tool and sub-agent call records and results, and overseer communications. This organization facilitates efficient information flow, enhancing LLM operation and reducing processing time and costs. Initially, file changes were recorded as diffs, showing only modifications and periodically consolidated.

<mark>SICA 的 LLM 在其上下文窗口（即短期记忆）中采用结构化的信息组织方式，这是高效运行的关键。具体结构包含三个层次：**系统提示层**——定义智能体目标、工具及子智能体文档和系统指令；**核心提示层**——包含问题陈述、当前打开文件的内容和目录结构；**助理消息层**——记录智能体的推理轨迹、工具与子智能体的调用过程及结果，以及与监督者的通信。这种清晰的层次结构保证了信息的高效流转，显著提升了 LLM 的运行效率，同时降低了处理时间和成本。为进一步优化，系统最初采用差异记录方式，仅保存文件变更内容并定期合并。</mark>

### SICA: A Look at the Code | <mark>SICA：代码深入了解</mark>

Delving deeper into SICA's implementation reveals several key design choices that underpin its capabilities. As discussed, the system is built with a modular architecture, incorporating several sub-agents, such as a coding agent, a problem-solver agent, and a reasoning agent. These sub-agents are invoked by the main agent, much like tool calls, serving to decompose complex tasks and efficiently manage context length, especially during those extended meta-improvement iterations.

<mark>深入研究 SICA 的实现可以发现支撑其能力的几个关键设计选择。如前所述，该系统采用模块化架构，包含多个子智能体，如编码智能体、问题解决智能体和推理智能体。这些子智能体由主智能体调用，类似于工具调用，用于分解复杂任务并有效管理上下文长度，特别是在长时间的元改进迭代中。</mark>

The project is actively developed and aims to provide a robust framework for those interested in post-training LLMs on tool use and other agentic tasks, with the full code available for further exploration and contribution at the https://github.com/MaximeRobeyns/self_improving_coding_agent/ GitHub repository.

<mark>该项目正在积极开发中，旨在为对 LLM 工具使用和其他智能体任务后训练感兴趣的研究人员提供强大的框架。完整代码可在 GitHub 仓库 https://github.com/MaximeRobeyns/self_improving_coding_agent/ 中获取，供进一步探索和贡献。</mark>

For security, the project strongly emphasizes Docker containerization, meaning the agent runs within a dedicated Docker container. This is a crucial measure, as it provides isolation from the host machine, mitigating risks like inadvertent file system manipulation given the agent's ability to execute shell commands.

<mark>为确保安全性，该项目强烈推荐使用 Docker 容器化部署，即智能体在专用的 Docker 容器中运行。这是一项关键措施，因为它提供了与主机系统的隔离，降低了因智能体执行 shell 命令可能导致的意外文件系统操作等风险。</mark>

To ensure transparency and control, the system features robust observability through an interactive webpage that visualizes events on the event bus and the agent's callgraph. This offers comprehensive insights into the agent's actions, allowing users to inspect individual events, read overseer messages, and collapse sub-agent traces for clearer understanding.

<mark>为确保透明度和可控性，系统通过交互式网页提供强大的可观察性，可视化事件总线上的事件和智能体的调用图。这提供了对智能体行为的全面洞察，允许用户检查单个事件、阅读监督者消息并折叠子智能体跟踪以获得更清晰的理解。</mark>

In terms of its core intelligence, the agent framework supports LLM integration from various providers, enabling experimentation with different models to find the best fit for specific tasks. Finally, a critical component is the asynchronous overseer, an LLM that runs concurrently with the main agent. This overseer periodically assesses the agent's behavior for pathological deviations or stagnation and can intervene by sending notifications or even cancelling the agent's execution if necessary. It receives a detailed textual representation of the system's state, including a callgraph and an event stream of LLM messages, tool calls, and responses, which allows it to detect inefficient patterns or repeated work.

<mark>在核心智能层面，该框架支持集成来自不同供应商的 LLM，便于研究人员针对特定任务选择最适配的模型。框架中的另一个关键组件是**异步监督者**——这是一个与主智能体并行运行的独立 LLM。监督者的职责是持续监测智能体行为，识别异常偏差或陷入停滞的迹象。一旦发现问题，它可以通过发送警告通知进行提醒，必要时甚至直接中止执行。为了实现精准监控，监督者会接收系统状态的详尽文本描述——包括调用图谱、LLM 消息序列、工具调用记录及响应事件流，借此识别出低效模式或重复性工作。</mark>

A notable challenge in the initial SICA implementation was prompting the LLM-based agent to independently propose novel, innovative, feasible, and engaging modifications during each meta-improvement iteration. This limitation, particularly in fostering open-ended learning and authentic creativity in LLM agents, remains a key area of investigation in current research.

<mark>SICA 早期实现面临的一个核心挑战是：如何引导基于 LLM 的智能体在每轮元改进迭代中自主提出既新颖创新、又切实可行且富有价值的修改方案。这一挑战本质上关系到如何培养 LLM 智能体的开放式学习能力和真正的创造性思维，目前仍是该领域的重要研究课题。</mark>

---

## AlphaEvolve and OpenEvolve | <mark>AlphaEvolve 和 OpenEvolve</mark>

AlphaEvolve is an AI agent developed by Google designed to discover and optimize algorithms. It utilizes a combination of LLMs, specifically Gemini models (Flash and Pro), automated evaluation systems, and an evolutionary algorithm framework. This system aims to advance both theoretical mathematics and practical computing applications.

<mark>AlphaEvolve 是 Google 开发的 AI 智能体，专门用于发现和优化算法。它结合了大语言模型（特别是 Gemini 系列的 Flash 和 Pro 模型）、自动化评估系统和进化算法框架。该系统旨在推进理论数学和实际计算应用的发展。</mark>

AlphaEvolve employs an ensemble of Gemini models. Flash is used for generating a wide range of initial algorithm proposals, while Pro provides more in-depth analysis and refinement. Proposed algorithms are then automatically evaluated and scored based on predefined criteria. This evaluation provides feedback that is used to iteratively improve the solutions, leading to optimized and novel algorithms.

<mark>AlphaEvolve 采用 Gemini 模型集成架构。Flash 模型用于生成大量初始算法提案，而 Pro 模型则提供更深入的分析和优化。随后，系统根据预定义标准对提案算法进行自动评估和评分。这种评估提供了迭代改进解决方案的反馈，最终产生优化的新型算法。</mark>

In practical computing, AlphaEvolve has been deployed within Google's infrastructure. It has demonstrated improvements in data center scheduling, resulting in a 0.7% reduction in global compute resource usage. It has also contributed to hardware design by suggesting optimizations for Verilog code in upcoming Tensor Processing Units (TPUs). Furthermore, AlphaEvolve has accelerated AI performance, including a 23% speed improvement in a core kernel of the Gemini architecture and up to 32.5% optimization of low-level GPU instructions for FlashAttention.

<mark>在实际计算应用中，AlphaEvolve 已部署在 Google 的基础设施中。它在数据中心调度方面实现了显著改进，使全球计算资源使用量减少了 0.7%。它还为硬件设计做出贡献，为即将推出的张量处理单元（TPU）中的 Verilog 代码提供优化建议。此外，AlphaEvolve 加速了 AI 性能，包括 Gemini 架构核心内核 23% 的速度提升和 FlashAttention 底层 GPU 指令高达 32.5% 的优化。</mark>

In the realm of fundamental research, AlphaEvolve has contributed to the discovery of new algorithms for matrix multiplication, including a method for 4x4 complex-valued matrices that uses 48 scalar multiplications, surpassing previously known solutions. In broader mathematical research, it has rediscovered existing state-of-the-art solutions to over 50 open problems in 75% of cases and improved upon existing solutions in 20% of cases, with examples including advancements in the kissing number problem.

<mark>在基础研究领域，AlphaEvolve 为矩阵乘法新算法的发现做出了贡献，包括一种仅需 48 次标量乘法的 4x4 复值矩阵方法，超越了先前已知的解决方案。在更广泛的数学研究中，它在 75% 的情况下重新发现了超过 50 个开放问题的现有最优解，并在 20% 的情况下改进了现有解决方案，例如在接吻数问题方面的进展。</mark>

OpenEvolve is an evolutionary coding agent that leverages LLMs (see Fig.3) to iteratively optimize code. It orchestrates a pipeline of LLM-driven code generation, evaluation, and selection to continuously enhance programs for a wide range of tasks. A key aspect of OpenEvolve is its capability to evolve entire code files, rather than being limited to single functions. The agent is designed for versatility, offering support for multiple programming languages and compatibility with OpenAI-compatible APIs for any LLM. Furthermore, it incorporates multi-objective optimization, allows for flexible prompt engineering, and is capable of distributed evaluation to efficiently handle complex coding challenges.

<mark>OpenEvolve 是一个利用 LLM 进行迭代代码优化的进化编码智能体（见图 3）。它协调 LLM 驱动的代码生成、评估和选择流程，持续改进适用于各种任务的程序。OpenEvolve 的一个关键特点是能够优化整个代码文件，而不仅限于单个函数。该智能体设计灵活，支持多种编程语言，并与任何 LLM 的 OpenAI 兼容 API 兼容。此外，它集成了多目标优化，支持灵活的提示工程，并能够进行分布式评估以有效处理复杂的编码挑战。</mark>

**[Figure 3: OpenEvolve architecture would be inserted here]**

This code snippet uses the OpenEvolve library to perform evolutionary optimization on a program. It initializes the OpenEvolve system with paths to an initial program, an evaluation file, and a configuration file. The `evolve.run(iterations=1000)` line starts the evolutionary process, running for 1000 iterations to find an improved version of the program. Finally, it prints the metrics of the best program found during the evolution, formatted to four decimal places.

<mark>以下代码片段展示了如何使用 OpenEvolve 库对程序进行进化优化。它使用初始程序、评估文件和配置文件的路径初始化 OpenEvolve 系统。`evolve.run(iterations=1000)` 启动进化过程，运行 1000 次迭代以找到程序的改进版本。最后，它打印进化过程中找到的最佳程序的指标，保留四位小数。</mark>

```python
from openevolve import OpenEvolve

# Initialize the system
# 初始化系统
evolve = OpenEvolve(
    initial_program_path="path/to/initial_program.py",
    evaluation_file="path/to/evaluator.py",
    config_path="path/to/config.yaml"
)

# Run the evolution
# 运行进化
best_program = await evolve.run(iterations=1000)
print(f"Best program metrics:")
print(f"最佳程序指标：")
for name, value in best_program.metrics.items():
    print(f"  {name}: {value:.4f}")
```

---

## At a Glance | <mark>快速概览</mark>

**What**: AI agents often operate in dynamic and unpredictable environments where pre-programmed logic is insufficient. Their performance can degrade when faced with novel situations not anticipated during their initial design. Without the ability to learn from experience, agents cannot optimize their strategies or personalize their interactions over time. This rigidity limits their effectiveness and prevents them from achieving true autonomy in complex, real-world scenarios.

<mark><strong>问题背景</strong>：AI 智能体往往需要在动态多变且不可预测的环境中运行，仅靠预先编程的逻辑难以应对所有场景。当遭遇设计之初未曾预见的新情况时，其性能会显著下降。若缺乏从经验中学习的能力，智能体便无法优化自身策略或实现个性化交互。这种僵化特性严重制约了它们的适用性，使其难以在复杂的真实世界场景中展现真正的自主智能。</mark>

**Why**: The standardized solution is to integrate learning and adaptation mechanisms, transforming static agents into dynamic, evolving systems. This allows an agent to autonomously refine its knowledge and behaviors based on new data and interactions. Agentic systems can use various methods, from reinforcement learning to more advanced techniques like self-modification, as seen in the Self-Improving Coding Agent (SICA). Advanced systems like Google's AlphaEvolve leverage LLMs and evolutionary algorithms to discover entirely new and more efficient solutions to complex problems. By continuously learning, agents can master new tasks, enhance their performance, and adapt to changing conditions without requiring constant manual reprogramming.

<mark><strong>解决方案</strong>：业界的标准做法是为智能体集成学习与适应机制，将其从静态系统改造为可动态演进的智能体。这使得智能体能够根据新获取的数据和交互经验，自主优化自身的知识库和行为模式。实现路径多样，既包括经典的强化学习方法，也涵盖更前沿的自我修改技术——如本章介绍的自我改进编码智能体（SICA）。像 Google AlphaEvolve 这样的先进系统，通过融合大语言模型与进化算法，能够自主发现全新且高效的复杂问题解决方案。具备持续学习能力的智能体，可以不断掌握新技能、提升任务表现、适应环境变化，而无需频繁的人工重新编程。</mark>

**Rule of thumb**: Use this pattern when building agents that must operate in dynamic, uncertain, or evolving environments. It is essential for applications requiring personalization, continuous performance improvement, and the ability to handle novel situations autonomously.

<mark><strong>应用场景</strong>：当构建需要在动态多变、充满不确定性或持续演进的环境中运行的智能体时，应采用本模式。该模式对于那些要求个性化服务、持续性能优化以及自主应对新场景的应用系统尤为关键。</mark>

---

## Visual Summary | <mark>视觉摘要</mark>

**[Visual summary diagram would be inserted here]**

---

## Key Takeaways | <mark>关键要点</mark>

**Learning and Adaptation are about agents getting better at what they do and handling new situations by using their experiences.**

<mark>学习和适应是指智能体通过经验积累来改进任务执行和应对新情况的能力。</mark>

**"Adaptation" is the visible change in an agent's behavior or knowledge that comes from learning.**

<mark>「适应」是智能体行为或知识中可见的变化，是学习的结果。</mark>

**SICA, the Self-Improving Coding Agent, self-improves by modifying its code based on past performance. This led to tools like the Smart Editor and AST Symbol Locator.**

<mark>SICA（自我改进编码智能体）通过基于历史表现修改代码实现自我改进，开发了智能编辑器和 AST 符号定位器等工具。</mark>

**Having specialized "sub-agents" and an "overseer" helps these self-improving systems manage big tasks and stay on track.**

<mark>专门的「子智能体」和「监督者」有助于这些自我改进系统管理大型任务并保持正确方向。</mark>

**The way an LLM's "context window" is set up (with system prompts, core prompts, and assistant messages) is super important for how efficiently agents work.**

<mark>LLM「上下文窗口」的设置方式（包括系统提示、核心提示和助理消息）对智能体的高效运行至关重要。</mark>

**This pattern is vital for agents that need to operate in environments that are always changing, uncertain, or require a personal touch.**

<mark>此模式对于需要在不断变化、不确定或需要个性化的环境中运行的智能体至关重要。</mark>

**Building agents that learn often means hooking them up with machine learning tools and managing how data flows.**

<mark>构建学习型智能体通常需要集成机器学习工具并管理数据流。</mark>

**An agent system, equipped with basic coding tools, can autonomously edit itself, and thereby improve its performance on benchmark tasks.**

<mark>配备基本编码工具的智能体系统可以自主编辑自身，从而提升在基准任务上的性能。</mark>

**AlphaEvolve is Google's AI agent that leverages LLMs and an evolutionary framework to autonomously discover and optimize algorithms, significantly enhancing both fundamental research and practical computing applications.**

<mark>AlphaEvolve 是 Google 的 AI 智能体，利用 LLM 和进化框架自主发现和优化算法，显著提升了基础研究和实际计算应用的效果。</mark>

---

## Conclusion | <mark>结论</mark>

This chapter examines the crucial roles of learning and adaptation in Artificial Intelligence. AI agents enhance their performance through continuous data acquisition and experience. The Self-Improving Coding Agent (SICA) exemplifies this by autonomously improving its capabilities through code modifications.

<mark>本章深入探讨了学习与适应机制在人工智能领域的核心地位。AI 智能体通过持续获取数据并积累实践经验来不断提升自身性能。自我改进编码智能体（SICA）便是一个典型范例——它通过自主修改代码来迭代优化自身能力。</mark>

We have reviewed the fundamental components of agentic AI, including architecture, applications, planning, multi-agent collaboration, memory management, and learning and adaptation. Learning principles are particularly vital for coordinated improvement in multi-agent systems. To achieve this, tuning data must accurately reflect the complete interaction trajectory, capturing the individual inputs and outputs of each participating agent.

<mark>全书至此，我们已系统回顾了智能体型 AI 的各项基础组件：架构设计、实际应用、任务规划、多智能体协作、记忆管理，以及学习与适应机制。在多智能体系统中，学习原则对于实现协同优化具有特殊意义——为了达成这一目标，训练数据必须完整记录交互全过程，准确捕捉每个参与智能体的输入与输出信息。</mark>

These elements contribute to significant advancements, such as Google's AlphaEvolve. This AI system independently discovers and refines algorithms by LLMs, automated assessment, and an evolutionary approach, driving progress in scientific research and computational techniques. Such patterns can be combined to construct sophisticated AI systems. Developments like AlphaEvolve demonstrate that autonomous algorithmic discovery and optimization by AI agents are attainable.

<mark>上述各项要素的有机结合催生了诸多突破性成果，Google 的 AlphaEvolve 便是其中的代表。这一 AI 系统融合了大语言模型、自动化评估体系和进化算法，能够自主发现并优化算法，为科学研究和计算技术的发展注入强劲动力。通过灵活组合这些设计模式，我们可以构建出功能强大的复杂 AI 系统。AlphaEvolve 等案例充分证明：让 AI 智能体自主发现和优化算法，在技术上已完全可行。</mark>

---

## References | <mark>参考文献</mark>

- Sutton, R. S., & Barto, A. G. (2018). Reinforcement Learning: An Introduction. MIT Press.
- Goodfellow, I., Bengio, Y., & Courville, A. (2016). Deep Learning. MIT Press.
- Mitchell, T. M. (1997). Machine Learning. McGraw-Hill.
- Proximal Policy Optimization Algorithms by John Schulman, Filip Wolski, Prafulla Dhariwal, Alec Radford, and Oleg Klimov. You can find it on arXiv: https://arxiv.org/abs/1707.06347
- Robeyns, M., Aitchison, L., & Szummer, M. (2025). A Self-Improving Coding Agent. arXiv:2504.15228v2. https://arxiv.org/pdf/2504.15228 https://github.com/MaximeRobeyns/self_improving_coding_agent
- AlphaEvolve blog, https://deepmind.google/discover/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/
- OpenEvolve, https://github.com/codelion/openevolve
