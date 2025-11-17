------

# Chapter 17: Reasoning Techniques | <mark>第 17 章：推理技术</mark>

This chapter delves into advanced reasoning methodologies for intelligent agents, focusing on multi-step logical inferences and problem-solving. These techniques go beyond simple sequential operations, making the agent's internal reasoning explicit. This allows agents to break down problems, consider intermediate steps, and reach more robust and accurate conclusions.  A core principle among these advanced methods is the allocation of increased computational resources during inference. This means granting the agent, or the underlying LLM, more processing time or steps to process a query and generate a response. Rather than a quick, single pass, the agent can engage in iterative refinement, explore multiple solution paths, or utilize external tools. This extended processing time during inference often significantly enhances accuracy, coherence, and robustness, especially for complex problems requiring deeper analysis and deliberation.

<mark>本章深入探讨了智能体的先进推理方法，重点介绍多步逻辑推理和问题解决技术。这些技术超越了简单的顺序操作，使智能体的内部推理过程更加明确。这使得智能体能够分解问题、考虑中间步骤，并得出更加稳健和准确的结论。在这些先进方法中，一个核心原则是在推理过程中分配更多的计算资源。这意味着给予智能体或底层 LLM 更多的处理时间或步骤来处理查询并生成响应。智能体可以进行迭代优化、探索多种解决方案路径或利用外部工具，而不是进行快速的单次处理。这种在推理过程中延长的处理时间通常能显著提高准确性、连贯性和稳健性，尤其对于需要深入分析和思考的复杂问题。</mark>

## Practical Applications & Use Cases | <mark>实际应用与使用案例</mark>

Practical applications include:

<mark>实际应用包括：</mark>

●**Complex Question Answering**: Facilitating the resolution of multi-hop queries, which necessitate the integration of data from diverse sources and the execution of logical deductions, potentially involving the examination of multiple reasoning paths, and benefiting from extended inference time to synthesize information.

<mark>●**复杂问答**：促进多跳查询的解决，这类查询需要整合来自不同来源的数据并执行逻辑推理，可能涉及检查多条推理路径，并得益于更长的推理时间来综合信息。</mark>

●**Mathematical Problem Solving**: Enabling the division of mathematical problems into smaller, solvable components, illustrating the step-by-step process, and employing code execution for precise computations, where prolonged inference enables more intricate code generation and validation.

<mark>●**数学问题解决**：将数学问题分解为更小、可解决的组成部分，展示逐步解决过程，并使用代码执行进行精确计算，其中长时间的推理能够支持更复杂的代码生成和验证。</mark>

●**Code Debugging and Generation**: Supporting an agent's explanation of its rationale for generating or correcting code, pinpointing potential issues sequentially, and iteratively refining the code based on test results (Self-Correction), leveraging extended inference time for thorough debugging cycles.

<mark>●**代码调试与生成**：支持智能体对其生成或修正代码的推理依据进行解释，顺序识别潜在问题，并根据测试结果迭代优化代码（自我修正），利用扩展的推理时间进行彻底的调试周期。</mark>

●**Strategic Planning**: Assisting in the development of comprehensive plans through reasoning across various options, consequences, and preconditions, and adjusting plans based on real-time feedback (ReAct), where extended deliberation can lead to more effective and reliable plans.

<mark>●**战略规划**：通过推理各种选项、结果和先决条件来协助制定全面计划，并根据实时反馈（ReAct）调整计划，其中深入的思考可以导致更有效和可靠的计划。</mark>

●**Medical Diagnosis**: Aiding an agent in systematically assessing symptoms, test outcomes, and patient histories to reach a diagnosis, articulating its reasoning at each phase, and potentially utilizing external instruments for data retrieval (ReAct). Increased inference time allows for a more comprehensive differential diagnosis.

<mark>●**医疗诊断**：帮助智能体系统评估症状、检查结果和患者病史以做出诊断，在每个阶段阐述其推理过程，并可能利用外部工具进行数据检索（ReAct）。增加推理时间可以实现更全面的鉴别诊断。</mark>

●**Legal Analysis**: Supporting the analysis of legal documents and precedents to formulate arguments or provide guidance, detailing the logical steps taken, and ensuring logical consistency through self-correction. Increased inference time allows for more in-depth legal research and argument construction.

<mark>●**法律分析**：支持对法律文件和判例的分析，以制定论点或提供指导，详细说明所采取的逻辑步骤，并通过自纠正（self-correction）确保逻辑一致性。增加推理时间可以进行更深入的法律研究和论点构建。</mark>

## Reasoning techniques
## <mark>推理技巧</mark>

To start, let's delve into the core reasoning techniques used to enhance the problem-solving abilities of AI models.

<mark>首先，我们深入探究旨在提升 AI 模型问题解决能力的核心推理技巧。</mark>

**Chain-of-Thought (CoT)** prompting significantly enhances LLMs' complex reasoning abilities by mimicking a step-by-step thought process (see Fig. 1). Instead of providing a direct answer, CoT prompts guide the model to generate a sequence of intermediate reasoning steps. This explicit breakdown allows LLMs to tackle complex problems by decomposing them into smaller, more manageable sub-problems. This technique markedly improves the model's performance on tasks requiring multi-step reasoning, such as arithmetic, common sense reasoning, and symbolic manipulation. A primary advantage of CoT is its ability to transform a difficult, single-step problem into a series of simpler steps, thereby increasing the transparency of the LLM's reasoning process. This approach not only boosts accuracy but also offers valuable insights into the model's decision-making, aiding in debugging and comprehension. CoT can be implemented using various strategies, including offering few-shot examples that demonstrate step-by-step reasoning or simply instructing the model to "think step by step." Its effectiveness stems from its ability to guide the model's internal processing toward a more deliberate and logical progression. As a result, Chain-of-Thought has become a cornerstone technique for enabling advanced reasoning capabilities in contemporary LLMs. This enhanced transparency and breakdown of complex problems into manageable sub-problems is particularly important for autonomous agents, as it enables them to perform more reliable and auditable actions in complex environments.

<mark>**思维链 (CoT)** 提示通过模仿逐步思考的过程（参见图 1），显著增强了大型语言模型（LLM）的复杂推理能力。CoT 提示并非直接给出答案，而是引导模型生成一系列中间推理步骤。这种清晰的拆解使 LLM 能够将复杂问题分解为更小、更易处理的子问题，从而攻克难题。这项技术显著提升了模型在需要多步推理任务上的表现，例如算术、常识推理和符号操作等。</mark>

<mark>CoT 的一个主要优势在于它能够将困难的单步问题转化为一系列简单步骤，进而提高 LLM 推理过程的透明度。这种方法不仅提高了准确性，还为模型的决策提供了有价值的洞察，有助于调试和理解。CoT 可以通过多种策略实现，包括提供展示逐步推理的少样本示例，或者直接指示模型“逐步思考”。其有效性源于它能够引导模型的内部处理流程朝着更审慎、更逻辑化的方向发展。因此，思维链已成为赋能当代 LLM 高级推理能力的关键基石。</mark>

<mark>这种增强的透明度，以及将复杂问题拆解为可管理子问题的做法，对于自主智能体（Autonomous Agents）尤为重要，因为它使智能体能够在复杂环境中执行更可靠、更可审计的行动。</mark>

<img width="800" height="564" alt="image" src="https://github.com/user-attachments/assets/3f0623d5-867b-41e0-9880-ff355a76aace" />

Fig. 1: CoT prompt alongside the detailed, step-by-step response generated by the agent.
<mark>图 1：思维链提示以及智能体生成的详细、逐步响应。</mark>

Let's see an example. It begins with a set of instructions that tell the AI how to think, defining its persona and a clear five-step process to follow. This is the prompt that initiates structured thinking.

<mark>让我们看一个例子。它首先包含一组指令，告诉 AI 如何思考，定义其角色以及一个明确的五步流程。这是启动结构化思考的提示。</mark>

Following that, the example shows the CoT process in action. The section labeled "Agent's Thought Process" is the internal monologue where the model executes the instructed steps. This is the literal "chain of thought." Finally, the "Agent's Final Answer" is the polished, comprehensive output generated as a result of that careful, step-by-step reasoning process

<mark>随后，该示例展示了 CoT 过程的实际应用。标记为"Agent's Thought Process"的部分是模型执行指定步骤时的内心独白，这就是字面意义上的"思维链"。最后，"Agent's Final Answer"是经过仔细、逐步推理过程后生成的精炼且全面的输出。</mark>

```python
You are an Information Retrieval Agent. Your goal is to answer the user's question comprehensively and accurately by thinking step-by-step.
Here's the process you must follow:

1. **Analyze the Query:** Understand the core subject and specific requirements of the user's question. Identify key entities, keywords, and the type of information being sought.
2. **Formulate Search Queries (for Knowledge Base):** Based on your analysis, generate a list of precise search queries that you would use to retrieve relevant information from a knowledge base or external tools.
3. **Simulate Information Retrieval (Self-Correction/Reasoning):**For each search query, mentally consider what kind of information you expect to find. If you were to retrieve the content, what would be the most relevant snippets? Think about potential ambiguities or
missing pieces.
4. **Synthesize Information:** Based on the simulated retrieval and your understanding of the user's original query, synthesize the gathered information into a coherent and complete answer. Ensure all aspects of the query are addressed.
5. **Review and Refine:** Before finalizing, critically evaluate your answer. Is it accurate? Is it comprehensive? Is it easy to understand? Is it concise? If not, identify what needs to be improved and how.

**User Query:** "Explain the main differences between classical computers and quantum computers, and briefly describe a potential application of quantum computing."

**Agent's Thought Process (Internal CoT Output - encouraged by the prompt):**

**Thought 1 (Analyze Query):**
The user wants two things:
1. Main differences between classical and quantum computers.
2. One potential application of quantum computing.
Keywords: classical computers, quantum computers, differences, potential application.

**Thought 2 (Formulate Search Queries):**
- "differences classical vs quantum computers"
- "how quantum computers work"
- "how classical computers work"
- "applications of quantum computing"

**Thought 3 (Simulate Information Retrieval & Identify Key Concepts):**
- From "differences": Expect concepts like bits vs. qubits, superposition, entanglement, probabilistic nature, computational power for specific problems.
- From "how they work": Classical uses transistors/binary. Quantum uses quantum mechanics.
- From "applications": Expect drug discovery, material science, cryptography, optimization.

**Thought 4 (Synthesize Information):**
Classical computers use bits (0 or 1), processing information sequentially. Quantum computers use qubits, which can be 0, 1, or both simultaneously (superposition), and can be entangled, allowing for vastly different computational approaches. This enables them to
solve certain problems (like factoring large numbers or simulating complex molecules) far more efficiently than classical computers. A potential application is in drug discovery, where quantum computers could simulate molecular interactions with unprecedented accuracy,
accelerating the development of new medicines.

**Thought 5 (Review and Refine):**
- Differences are covered (bits vs qubits, superposition, entanglement, processing).
- Application is given (drug discovery).
- Is it brief? Yes.
- Is it clear? Yes.
- Looks good.

**Agent's Final Answer (Output to User):**
Classical computers process information using bits, which can be either a 0 or a 1 at any given time, performing operations sequentially. In contrast, quantum computers utilize qubits, which can exist in multiple states simultaneously through superposition and can be linked through entanglement, allowing for exponentially more complex computations. This fundamental difference enables quantum machines to tackle certain problems, such as simulating molecular structures or breaking complex encryption, that are intractable for even the most powerful classical supercomputers. A significant potential application of quantum computing lies in drug discovery, where its ability to precisely model molecular behavior could revolutionize the development of new pharmaceuticals.

```

```python

你是一名信息检索智能体（Information Retrieval Agent）。你的目标是通过循序渐进的思考，全面且准确地回答用户的问题。
你必须遵循以下流程：

1. **分析查询（Analyze the Query）：** 理解用户问题的核心主题和具体要求。识别关键实体、关键词以及所需信息的类型。
2. **制定搜索查询（Formulate Search Queries - 针对知识库）：** 基于你的分析，生成一份精确的搜索查询列表，用于从知识库或外部工具中检索相关信息。
3. **模拟信息检索（Simulate Information Retrieval - 自我修正/推理）：** 对于每项搜索查询，在脑海中思考预期会找到哪种信息。如果检索到内容，哪些片段会是最相关的？思考潜在的歧义或缺失的部分。
4. **综合信息（Synthesize Information）：** 基于模拟检索和你对用户原始查询的理解，将收集到的信息综合成一个连贯且完整的答案。确保回答了查询的所有方面。
5. **审查与优化（Review and Refine）：** 在最终确定答案前，批判性地评估你的回答。它是否准确？是否全面？是否易于理解？是否简洁？如果不是，确定需要改进的内容和方式。

**用户查询：**“解释经典计算机和量子计算机的主要区别，并简要描述一个量子计算的潜在应用。”
**智能体的思维过程（内部思维链输出 - 由提示鼓励生成）**

**思考 1（分析查询）：**
用户希望得到两点信息：
1. 经典计算机与量子计算机的主要区别。
2. 一个潜在的量子计算应用。
关键词：经典计算机、量子计算机、区别、潜在应用。

思考 2（制定搜索查询）：
- “经典计算机 vs 量子计算机 区别”
- “量子计算机如何工作”
- “经典计算机如何工作”
- “量子计算应用”

**思考 3（模拟信息检索与识别关键概念）：**
- 从“区别”中：预期会找到比特（bits） vs 量子比特（qubits）、叠加态（superposition）、纠缠（entanglement）、概率性质、解决特定问题的计算能力等概念。
- 从“如何工作”中：经典计算机使用晶体管/二进制。量子计算机使用量子力学。
- 从“应用”中：预期会找到药物发现、材料科学、密码学、优化等。

**思考 4（综合信息）：**
经典计算机使用比特（0 或 1），并按顺序处理信息。量子计算机使用量子比特，量子比特可以同时处于 0、1 或两者兼具的状态（叠加态），并且可以相互纠缠，从而实现截然不同的计算方法。这使它们能够比经典计算机更高效地解决某些特定问题（如分解大数或模拟复杂分子）。一个潜在的应用是药物发现，量子计算机可以前所未有地准确模拟分子相互作用，从而加速新药的研发。

**思考 5（审查与优化）：**
- 区别已涵盖（比特 vs 量子比特、叠加态、纠缠、处理方式）。
- 应用已给出（药物发现）。
- 是否简洁？是。
- 是否清晰？是。
- 看起来不错。

**智能体的最终答案（输出给用户）：**
经典计算机使用比特来处理信息，比特在任一时刻只能是 0 或 1，并按顺序执行操作。相比之下，量子计算机利用量子比特，量子比特可以通过叠加态同时存在于多种状态，并通过纠缠相互关联，从而实现指数级复杂的计算。这种根本性的差异使得量子机器能够解决某些问题（例如模拟分子结构或破解复杂加密），这些问题对于最强大的经典超级计算机来说都是无法攻克的。量子计算的一个重要的潜在应用在于药物发现，它精确建模分子行为的能力可以彻底改变新药的研发。

```

**Tree-of-Thought (ToT)** is a reasoning technique that builds upon Chain-of-Thought(CoT). It allows large language models to explore multiple reasoning paths by branching into different intermediate steps, forming a tree structure (see Fig. 2) This approach supports complex problem-solving by enabling backtracking,self-correction, and exploration of alternative solutions. Maintaining a tree of possibilities allows the model to evaluate various reasoning trajectories before finalizing an answer. This iterative process enhances the model's ability to handle challenging tasks that require strategic planning and decision-making.
<mark>**思维树（ToT）** 是一种建立在思维链（Chain-of-Thought, CoT）基础上的推理技巧。它允许大型语言模型通过分支到不同的中间步骤，探索多条推理路径，从而形成一个树状结构（参见图 2）。这种方法通过支持回溯、自我修正和探索替代解决方案，来支持复杂的解题过程。维护一棵可能性之树，使得模型能够在最终确定答案之前评估各种推理轨迹。这种迭代过程增强了模型处理需要战略规划和决策制定的挑战性任务的能力。</mark>
<img width="2048" height="1445" alt="image" src="https://github.com/user-attachments/assets/c0bb1ace-e01e-4231-b730-7f166ec7478d" />
Fig.2: Example of Tree of Thoughts
图 2：思维树示例

**Self-correction**, also known as self-refinement, is a crucial aspect of an agent's reasoning process, particularly within Chain-of-Thought prompting. It involves the agent's internal evaluation of its generated content and intermediate thought processes. This critical review enables the agent to identify ambiguities, information gaps, or inaccuracies in its understanding or solutions. This iterative cycle of reviewing and refining allows the agent to adjust its approach, improve response quality, and ensure accuracy and thoroughness before delivering a final output. This internal critique enhances the agent's capacity to produce reliable and high-quality results, as demonstrated in examples within the dedicated Chapter 4.

<mark>**自我修正（Self-correction）**，也称为自我精炼（self-refinement），是智能体推理过程的关键方面，尤其是在思维链提示中。它涉及智能体对其生成的内容和中间思维过程进行内部评估。这种批判性审查使智能体能够识别其理解或解决方案中的歧义、信息空白或不准确之处。这种审查和精炼的迭代循环允许智能体调整其方法、提高响应质量，并确保在交付最终输出前的准确性和彻底性。这种内部批判增强了智能体生成可靠和高质量结果的能力，正如专门的第 4 章示例所示。</mark>


This example demonstrates a systematic process of self-correction, crucial for refining AI-generated content. It involves an iterative loop of drafting, reviewing against original requirements, and implementing specific improvements. The illustration begins by outlining the AI's function as a "Self-Correction Agent" with a67defined five-step analytical and revision workflow. Following this, a subpar "InitialDraft" of a social media post is presented. The "Self-Correction Agent's Thought Process" forms the core of the demonstration. Here, the Agent critically evaluates the draft according to its instructions, pinpointing weaknesses such as low engagement and a vague call to action. It then suggests concrete enhancements, including the use of more impactful verbs and emojis. The process concludes with the "Final Revised Content," a polished and notably improved version that integrates the self-identified adjustments.

<mark>这个示例展示了一个系统化的自我修正过程，这对于精炼 AI 生成的内容至关重要。它涉及一个起草、对照原始要求进行审查，以及实施具体改进的迭代循环。该示例首先概述了 AI 作为“自我修正智能体”（Self-Correction Agent）的功能，并定义了一个明确的五步分析和修订工作流。随后，呈现了一份质量欠佳的社交媒体帖子“初始草稿”（Initial Draft）。“自我修正智能体的思维过程”（Self-Correction Agent's Thought Process）构成了演示的核心。在这个环节，智能体根据指令批判性地评估草稿，指出了诸如参与度低和行动号召模糊等弱点。然后，它提出了具体的改进建议，包括使用更具影响力的动词和表情符号。整个过程最终以“最终修订内容”（Final Revised Content）收尾，这是一个整合了自我识别调整后的、更精炼且显著改善的版本。</mark>

```python
You are a highly critical and detail-oriented Self-Correction Agent.
Your task is to review a previously generated piece of content against its original requirements and identify areas for improvement.
Your goal is to refine the content to be more accurate, comprehensive, engaging, and aligned with the prompt.

Here's the process you must follow for self-correction:

1. **Understand Original Requirements:** Review the initial prompt/requirements that led to the content's creation. What was the *original intent*? What were the key constraints or goals?
2. **Analyze Current Content:** Read the provided content carefully.
3. **Identify Discrepancies/Weaknesses:** Compare the current content against the original requirements. Look for:
* **Accuracy Issues:** Are there any factual errors or misleading statements?
* **Completeness Gaps:** Does it fully address all aspects of the original prompt? Is anything missing?
* **Clarity & Coherence:** Is the language clear, concise, and easy to understand? Does it flow logically?
* **Tone & Style:** Does it match the desired tone and style (e.g., professional, engaging, concise)?
* **Engagement:** Is it captivating? Does it hold the reader's attention?
* **Redundancy/Verbosity:** Can any parts be condensed or removed without losing meaning?
4. **Propose Specific Improvements:** For each identified weakness, suggest concrete and actionable changes. Do not just state the problem; propose a solution.
5. **Generate Revised Content:** Based on your proposed improvements, rewrite the original content to incorporate all the necessary changes. Ensure the revised content is polished and ready for final use.

**Original Prompt/Requirements:** "Write a short, engaging social media post (max 150 characters) announcing a new eco-friendly product line: 'GreenTech Gadgets'."

**Initial Draft (Content to be corrected):**

"We have new products. They are green and techy. Buy GreenTech Gadgets now!"

**Self-Correction Agent's Thought Process (Internal CoT Output - encouraged by the prompt):**

**Thought 1 (Understand Original Requirements):**
- Short, engaging social media post.
- Max 150 characters.
- Announce "GreenTech Gadgets" - a new eco-friendly product line.

**Thought 2 (Analyze Current Content):**
"We have new products. They are green and techy. Buy GreenTech Gadgets now!" (64 characters)

**Thought 3 (Identify Discrepancies/Weaknesses):**
- **Engaging:** Not very engaging. Sounds generic.
- **Eco-friendly:** Implied by "green," but not explicitly highlighted as a benefit.
- **Call to Action:** "Buy now!" is okay, but could be more compelling.
- **Conciseness:** It's short, but could use stronger verbs/phrasing.
- **Impact:** Lacks excitement for a new product launch.

**Thought 4 (Propose Specific Improvements):**
- Make it more dynamic and exciting.
- Emphasize "eco-friendly" and "innovation."
- Use stronger verbs and more active voice.
- Add a clear, engaging call to action.
- Ensure it stays under 150 characters.

**Thought 5 (Generate Revised Content):**
Original: "We have new products. They are green and techy. Buy GreenTech Gadgets now!"
Revised idea 1: "🌱 Discover GreenTech Gadgets! Our new eco-friendly line blends innovation with sustainability. Go green, go smart! Shop now! #EcoFriendly #GreenTech" (148 characters)
This revision directly addresses eco-friendliness, uses emojis for engagement, adds a stronger call to action, and includes relevant hashtags while staying within the character limit.

**Self-Correction Agent's Final Revised Content (Output to User):**

🌱 Discover GreenTech Gadgets! Our new eco-friendly line blends innovation with sustainability. Go green, go smart! Shop now! #EcoFriendly #GreenTech

```

```python

自我修正智能体（Self-Correction Agent）工作流程示例
你是一名高度批判性且注重细节的自我修正智能体（Self-Correction Agent）。

你的任务是根据原始要求审查一段先前生成的内容，并识别出需要改进的区域。你的目标是精炼内容，使其更准确、更全面、更具吸引力，并与提示（Prompt）保持一致。

你必须遵循以下自我修正流程：

1. **理解原始要求（Understand Original Requirements）： **审查生成该内容的初始提示/要求。原始意图是什么？关键的约束或目标是什么？
2. **分析现有内容（Analyze Current Content）：** 仔细阅读提供的内容。
3. **识别差异/弱点（Identify Discrepancies/Weaknesses）：** 将现有内容与原始要求进行比较。查找以下问题：
* **准确性问题：** 是否存在任何事实错误或误导性陈述？
* **完整性缺失：** 是否充分解决了原始提示的所有方面？是否遗漏了任何内容？
* **清晰度与连贯性：** 语言是否清晰、简洁、易于理解？逻辑流程是否顺畅？
* **语气与风格：** 是否与所需的语气和风格（例如，专业、引人入胜、简洁）匹配？
* **参与度：** 是否引人注目？能否吸引读者的注意力？
* **冗余/啰嗦：** 是否可以在不失原意的情况下，对某些部分进行精简或删除？
4. **提出具体改进建议（Propose Specific Improvements）：** 对于识别出的每个弱点，提出具体且可操作的更改。不要只陈述问题，还要提出解决方案。
5. **生成修订内容（Generate Revised Content）：** 基于你提出的改进建议，重写原始内容以纳入所有必要的更改。确保修订后的内容经过润饰，可供最终使用。

原始提示/要求： “撰写一篇简短、引人入胜的社交媒体帖子（最多 150 个字符），宣布新的环保产品线：‘GreenTech Gadgets’。”

**（初始草稿 - 待修正的内容）：**

“我们有新产品。它们是绿色的，科技感十足。现在就购买 GreenTech Gadgets 吧！”

**自我修正智能体的思维过程（内部思维链输出 - 由提示鼓励生成）：**

**思考 1（理解原始要求）：**
简短、引人入胜的社交媒体帖子。
最多 150 个字符。
宣布“GreenTech Gadgets”——一条新的环保产品线。

**思考 2（分析现有内容）：**
“我们有新产品。它们是绿色的，科技感十足。现在就购买 GreenTech Gadgets 吧！”（64 个字符）

**思考 3（识别差异/弱点）：**
参与度： 不够吸引人。听起来很普通。
环保性： 由“绿色”（green）暗示，但没有明确强调其益处。
行动号召： “现在就购买！”尚可，但可以更有说服力。
简洁性： 虽然短，但可以使用更强有力的动词/措辞。
影响力： 缺乏新产品发布应有的兴奋感。

**思考 4（提出具体改进建议）：**
使其更具活力和兴奋感。
强调**“环保”和“创新”**。
使用更强有力的动词和更主动的语态。
添加一个清晰、引人入胜的行动号召。
确保字符数保持在 150 以内。

**思考 5（生成修订内容）：**
原稿：“我们有新产品。它们是绿色的，科技感十足。现在就购买 GreenTech Gadgets 吧！”
修订思路 1：“🌱 探索 GreenTech Gadgets！ 我们的新环保系列融合了创新与可持续性。选择绿色，选择智慧！立即购买！ #EcoFriendly #GreenTech”（148 个字符）
这次修订直接强调了环保性，使用了表情符号来增加参与度，添加了更强有力的行动号召，并包含了相关标签，同时保持在字符限制内。

**自我修正智能体的最终修订内容（输出给用户）：**
🌱 探索 GreenTech Gadgets！ 我们的新环保系列融合了创新与可持续性。选择绿色，选择智慧！立即购买！ #EcoFriendly #GreenTech
```

Fundamentally, this technique integrates a quality control measure directly into the Agent's content generation, yielding more refined, precise, and superior results that more effectively meet intricate user demands.

<mark>从根本上说，这项技巧将质量控制措施直接整合到智能体（Agent）的内容生成过程中，从而产生更精炼、更精确、更优质的结果，能更有效地满足复杂的用户需求。</mark>

**Program-Aided Language Models (PALMs)** integrate LLMs with symbolic reasoning capabilities. This integration allows the LLM to generate and execute code, such as Python, as part of its problem-solving process. PALMs offload complex calculations, logical operations, and data manipulation to a deterministic programming environment. This approach utilizes the strengths of traditional programming for tasks where LLMs might exhibit limitations in accuracy or consistency. When faced with symbolic challenges, the model can produce code, execute it, and convert the results into natural language. This hybrid methodology combines the LLM's understanding and generation abilities with precise computation, enabling the model to address a wider range of complex problems with potentially increased reliability and accuracy. This is important for agents as it allows them to perform more accurate and reliable actions by leveraging precise computation alongside their understanding and generation capabilities. An example is the use of external tools within Google's ADK for generating code.

<mark>**程序辅助语言模型（Program-Aided Language Models, PALMs）** 将大语言模型（LLM）与符号推理能力相结合。这种集成允许 LLM 在问题解决过程中生成并执行代码，例如 Python。PALMs 将复杂的计算、逻辑操作和数据处理工作转移到一个确定的编程环境中。这种方法利用了传统编程的优势，来处理 LLM 在准确性或一致性方面可能表现出局限性的任务。当面临符号挑战时，模型可以生成代码、执行代码，并将结果转换为自然语言。这种混合方法将 LLM 的理解和生成能力与精确计算相结合，使模型能够解决更广泛的复杂问题，并有可能提高可靠性和准确性。这对智能体来说至关重要，因为它允许智能体通过利用精确计算以及自身的理解和生成能力，执行更准确、更可靠的行动。一个例子是 Google ADK 中使用外部工具来生成代码。</mark>

```python
from google.adk.tools import agent_tool
from google.adk.agents import Agent
from google.adk.tools import google_search
from google.adk.code_executors import BuiltInCodeExecutor
search_agent = Agent(
   model='gemini-2.0-flash',
   name='SearchAgent',
   instruction="""
   You're a specialist in Google Search
   """,
   tools=[google_search],
)
coding_agent = Agent(
   model='gemini-2.0-flash',
   name='CodeAgent',
   instruction="""
   You're a specialist in Code Execution
9
10
""",
   code_executor=[BuiltInCodeExecutor],
)
root_agent = Agent(
   name="RootAgent",
   model="gemini-2.0-flash",
   description="Root Agent",
   tools=[agent_tool.AgentTool(agent=search_agent),
agent_tool.AgentTool(agent=coding_agent)],
)
```

**Reinforcement Learning with Verifiable Rewards (RLVR):** While effective, the standard Chain-of-Thought (CoT) prompting used by many LLMs is a somewhat basic approach to reasoning. It generates a single, predetermined line of thought without adapting to the complexity of the problem. To overcome these limitations, a new class of specialized "reasoning models" has been developed. These models operate differently by dedicating a variable amount of "thinking" time before providing an answer. This "thinking" process produces a more extensive and dynamic Chain-of-Thought that can be thousands of tokens long. This extended reasoning allows for more complex behaviors like self-correction and backtracking, with the model dedicating more effort to harder problems. The key innovation enabling these models is a training strategy called Reinforcement Learning from Verifiable Rewards (RLVR). By training the model on problems with known correct answers (like math or code), it learns through trial and error to generate effective, long-form reasoning. This allows the model to evolve its problem-solving abilities without direct human supervision. Ultimately, these reasoning models don't just produce an answer; they generate a "reasoning trajectory" that demonstrates advanced skills like planning, monitoring, and evaluation. This enhanced ability to reason and strategize is fundamental to the development of autonomous AI agents, which can break down and solve complex tasks with minimal human intervention.

<mark>**可验证奖励的强化学习（Reinforcement Learning with Verifiable Rewards, RLVR）：** 尽管有效，但许多 LLM 使用的标准思维链（Chain-of-Thought, CoT）提示是一种相对基础的推理方法。它会生成一条单一、预定的思维路线，而无法适应问题的复杂性。为了克服这些限制，一类新型的专业**「推理模型」已被开发出来。这些模型的运作方式有所不同，它们会在提供答案之前投入可变时长的「思考」时间。这个「思考」过程会产生更广泛、更具动态性的思维链**，长度可达数千个 Token。这种扩展的推理能够支持更复杂的行为，例如自我修正和回溯，模型会针对难度更高的问题投入更多精力。赋能这些模型的关键创新是一种名为可验证奖励的强化学习（RLVR）的训练策略。通过在已知正确答案的问题上（例如数学或代码）对模型进行训练，模型通过试错学习生成有效的长篇推理。这使得模型无需直接的人类监督即可演化其问题解决能力。最终，这些推理模型不仅会产生答案，还会生成一条「推理轨迹」，展示出规划、监控和评估等高级技能。这种增强的推理和策略制定能力，是自主 AI 智能体发展的基石，使它们能够以最少的人工干预来拆解和解决复杂的任务。</mark>

**ReAct** (Reasoning and Acting, see Fig. 3, where KB stands for Knowledge Base) is a paradigm that integrates Chain-of-Thought (CoT) prompting with an agent's ability to interact with external environments through tools. Unlike generative models that produce a final answer, a ReAct agent reasons about which actions to take. This reasoning phase involves an internal planning process, similar to CoT, where the agent determines its next steps, considers available tools, and anticipates outcomes. Following this, the agent acts by executing a tool or function call, such as querying a database, performing a calculation, or interacting with an API.

<mark>**ReAct**（推理与行动，参见图 3，其中 KB 代表知识库）是一种将思维链（CoT）提示与智能体通过工具与外部环境进行交互能力相结合的范式。与生成最终答案的生成模型不同，ReAct 智能体会推理要采取哪些行动。这个推理阶段涉及一个类似于 CoT 的内部规划过程，智能体在其中确定其后续步骤、考虑可用的工具并预测结果。随后，智能体通过执行工具或函数调用（例如查询数据库、执行计算或与 API 交互）来采取行动。</mark>

<img width="2048" height="1445" alt="image" src="https://github.com/user-attachments/assets/6ddc2354-f418-4271-a920-792a5bd0ff05" />

Fig.3: Reasoning and Act
<mark>图 3：推理与行动</mark>

ReAct operates in an interleaved manner: the agent executes an action, observes the outcome, and incorporates this observation into subsequent reasoning. This iterative loop of “Thought, Action, Observation, Thought...” allows the agent to dynamically adapt its plan, correct errors, and achieve goals requiring multiple interactions with the environment. This provides a more robust and flexible problem-solving approach compared to linear CoT, as the agent responds to real-time feedback. By combining language model understanding and generation with the capability to use tools, ReAct enables agents to perform complex tasks requiring both reasoning and practical execution. This approach is crucial for agents as it allows them to not only reason but also to practically execute steps and interact with dynamic environments.

<mark>ReAct 以交错的方式运作：智能体执行一个动作，观察结果，并将此观察结果纳入随后的推理中。这种「思考、行动、观察、思考……」的迭代循环允许智能体动态地调整其计划、修正错误，并实现需要与环境进行多次交互的目标。由于智能体对实时反馈作出响应，因此与线性 CoT 相比，这提供了一种更稳健和灵活的问题解决方法。通过将语言模型的理解和生成能力与使用工具的能力相结合，ReAct 使智能体能够执行既需要推理又需要实际执行的复杂任务。这种方法对智能体至关重要，因为它使智能体不仅能够推理，还能实际执行步骤并与动态环境进行交互。</mark>

**CoD** (Chain of Debates) is a formal AI framework proposed by Microsoft where multiple, diverse models collaborate and argue to solve a problem, moving beyond a single AI's "chain of thought." This system operates like an AI council meeting, where different models present initial ideas, critique each other's reasoning, and exchange counterarguments. The primary goal is to enhance accuracy, reduce bias, and improve the overall quality of the final answer by leveraging collective intelligence. Functioning as an AI version of peer review, this method creates a transparent and trustworthy record of the reasoning process. Ultimately, it represents a shift from a solitary Agent providing an answer to a collaborative team of Agents working together to find a more robust and validated solution.

<mark>**CoD**（辩论链，Chain of Debates）是微软提出的一种正式 AI 框架，其中多个、不同的模型协同合作并进行辩论来解决问题，超越了单个 AI 的「思维链」。该系统运作起来就像一个 AI 委员会会议，不同的模型提出初始想法、批判彼此的推理，并交换反驳意见。其主要目标是通过利用集体智慧，提高最终答案的准确性、减少偏见并改善整体质量。该方法充当 AI 版的同行评审，创建了一个透明且值得信赖的推理过程记录。最终，它代表了一种转变，即从一个单独的智能体提供答案，转向一个智能体协作团队共同寻找一个更稳健、经过验证的解决方案。</mark>

GoD (Graph of Debates) is an advanced Agentic framework that reimagines discussion as a dynamic, non-linear network rather than a simple chain. In this model, arguments are individual nodes connected by edges that signify relationships like 'supports' or 'refutes,' reflecting the multi-threaded nature of real debate. This structure allows new lines of inquiry to dynamically branch off, evolve independently, and even merge over time. A conclusion is reached not at the end of a sequence, but by identifying the most robust and well-supported cluster of arguments within the entire graph. In this context, "well-supported" refers to knowledge that is firmly established and verifiable. This can include information considered to be ground truth, which means it is inherently correct and widely accepted as fact. Additionally, it encompasses factual evidence obtained through search grounding, where information is validated against external sources and real-world data. Finally, it also pertains to a consensus reached by multiple models during a debate, indicating a high degree of agreement and confidence in the information presented. This comprehensive approach ensures a more robust and reliable foundation for the information being discussed. This approach provides a more holistic and realistic model for complex, collaborative AI reasoning.

<mark>GoD（辩论图，Graph of Debates）是一种先进的具智能体特性（Agentic）框架，它将讨论重新构想为一个动态、非线性的网络，而不是一个简单的链条。在这个模型中，论点是单独的节点，通过表示「支持」或「反驳」等关系的边连接起来，反映了真实辩论的多线程特性。这种结构允许新的探究路线动态地分支出来、独立演化，甚至随时间推移而合并。结论的得出并非在序列的末尾，而是通过识别整个图中最稳健和得到充分支持的论点集群。在这种背景下，「得到充分支持」指的是坚定确立且可验证的知识。这可以包括被认为是基础事实（ground truth）的信息，即其本质上正确并被广泛接受为事实。此外，它还包括通过搜索溯源（search grounding）获得的事实证据，即信息已根据外部来源和真实世界数据进行了验证。最后，它也涉及多个模型在辩论中达成的共识，表明对所呈现信息的高度一致性和信心。这种综合方法确保了所讨论信息具有更稳健和可靠的基础。这种方法为复杂、协作的 AI 推理提供了一个更整体、更真实的模型。</mark>

**MASS (optional advanced topic):** An in-depth analysis of the design of multi-agent systems reveals that their effectiveness is critically dependent on both the quality of the prompts used to program individual agents and the topology that dictates their interactions. The complexity of designing these systems is significant, as it involves a vast and intricate search space. To address this challenge, a novel framework called Multi-Agent System Search (MASS) was developed to automate and optimize the design of MAS.

<mark>**MASS（可选进阶主题）：** 对多智能体系统（Multi-Agent Systems, MAS）设计的深入分析表明，其有效性关键取决于用于编程单个智能体的提示（Prompt）质量以及决定其交互的拓扑结构。设计这些系统的复杂性非常高，因为它涉及一个庞大而错综复杂的搜索空间。为了应对这一挑战，开发了一个名为**多智能体系统搜索（MASS）**的新颖框架，用于自动化和优化 MAS 的设计。</mark>

MASS employs a multi-stage optimization strategy that systematically navigates the complex design space by interleaving prompt and topology optimization (see Fig. 4)

<mark>MASS 采用一种多阶段优化策略，通过交错进行提示优化和拓扑优化，系统地导航复杂的涉及空间（参见图 4）。</mark>

**1. Block-Level Prompt Optimization:** The process begins with a local optimization of prompts for individual agent types, or "blocks," to ensure each component performs its role effectively before being integrated into a larger system. This initial step is crucial as it ensures that the subsequent topology optimization builds upon well-performing agents, rather than suffering from the compounding impact of poorly configured ones. For example, when optimizing for the HotpotQA dataset, the prompt for a "Debator" agent is creatively framed to instruct it to act as an "expert fact-checker for a major publication". Its optimized task is to meticulously review proposed answers from other agents, cross-reference them with provided context passages, and identify any inconsistencies or unsupported claims. This specialized role-playing prompt, discovered during block-level optimization, aims to make the debator agent highly effective at synthesizing information before it's even placed into a larger workflow.

<mark>**1. 块级提示优化（Block-Level Prompt Optimization）：** 该过程从对单个智能体类型或「块」的提示进行局部优化开始，以确保每个组件在集成到更大系统之前都能有效地执行其角色。这一初始步骤至关重要，因为它能确保后续的拓扑优化是建立在表现良好的智能体之上的，而不是因配置不佳的智能体而遭受复合影响。例如，在针对 HotpotQA 数据集进行优化时，「辩论者」智能体的提示被创造性地构思，指示其扮演**「某主要出版物的专家事实核查员」。其优化后的任务是仔细审查其他智能体提出的答案，将其与提供的上下文段落进行交叉引用，并识别任何不一致或未得到支持的论断。这个在块级优化过程中发现的专业角色扮演提示**，旨在使辩论者智能体在被放入更大工作流之前，就能高效地综合信息。</mark>

**2. Workflow Topology Optimization:** Following local optimization, MASS optimizes the workflow topology by selecting and arranging different agent interactions from a customizable design space. To make this search efficient, MASS employs an influence-weighted method. This method calculates the "incremental influence" of each topology by measuring its performance gain relative to a baseline agent and uses these scores to guide the search toward more promising combinations. For instance, when optimizing for the MBPP coding task, the topology search discovers that a specific hybrid workflow is most effective. The best-found topology is not a simple structure but a combination of an iterative refinement process with external tool use. Specifically, it consists of one predictor agent that engages in several rounds of reflection, with its code being verified by one executor agent that runs the code against test cases. This discovered workflow shows that for coding, a structure that combines iterative self-correction with external verification is superior to simpler MAS designs.

<mark>**2. 工作流拓扑优化（Workflow Topology Optimization）：** 在局部优化之后，MASS 通过从可定制的设计空间中选择和排列不同的智能体交互，来优化工作流拓扑。为了提高搜索效率，MASS 采用了一种影响加权方法。该方法通过测量每种拓扑结构相对于基线智能体的性能增益，计算其「增量影响」，并使用这些分数来指导搜索，使其倾向于更有前途的组合。例如，在针对 MBPP 编码任务进行优化时，拓扑搜索发现特定的混合工作流最为有效。发现的最佳拓扑结构并非一个简单的结构，而是迭代精炼过程与外部工具使用的组合。具体来说，它包含一个进行多轮反思的预测智能体，其代码由一个针对测试用例运行代码的执行智能体进行验证。这个被发现的工作流表明，对于编码任务，将迭代自我修正与外部验证相结合的结构优于更简单的 MAS 设计。</mark>

<img width="1356" height="542" alt="image" src="https://github.com/user-attachments/assets/f98f633b-dced-479d-bc52-d57ad6e5a992" />
Fig. 4: (Courtesy of the Authors): The Multi-Agent System Search (MASS) Framework is a three-stage optimization process that navigates a search space encompassing optimizable prompts (instructions and demonstrations) and configurable agent building blocks (Aggregate, Reflect, Debate, Summarize, and Tool-use). The first stage, Block-level Prompt Optimization, independently optimizes prompts for each agent module. Stage two, Workflow Topology Optimization, samples valid system configurations from an influence-weighted design space, integrating the optimized prompts. The final stage, Workflow-level Prompt Optimization, involves a second round of prompt optimization for the entire multi-agent system after the optimal workflow from Stage two has been identified.

<mark>图 4：（作者供图）：多智能体系统搜索（Multi-Agent System Search, MASS）框架是一个三阶段的优化过程，它在一个包含可优化提示（指令和演示）和可配置智能体构建模块（聚合、反思、辩论、总结和工具使用）的搜索空间中进行导航。第一阶段，块级提示优化，独立优化每个智能体模块的提示。第二阶段，工作流拓扑优化，从影响加权的设计空间中采样有效的系统配置，并整合优化后的提示。最终阶段，工作流级提示优化，在确定第二阶段的最佳工作流之后，对整个多智能体系统进行第二轮提示优化。</mark>

**3. Workflow-Level Prompt Optimization:** The final stage involves a global optimization of the entire system's prompts. After identifying the best-performing topology, the prompts are fine-tuned as a single, integrated entity to ensure they are tailored for orchestration and that agent interdependencies are optimized. As an example, after finding the best topology for the DROP dataset, the final optimization stage refines the "Predictor" agent's prompt. The final, optimized prompt is highly detailed, beginning by providing the agent with a summary of the dataset itself, noting its focus on "extractive question answering" and "numerical information". It then includes few-shot examples of correct question-answering behavior and frames the core instruction as a high-stakes scenario: "You are a highly specialized AI tasked with extracting critical numerical information for an urgent news report. A live broadcast is relying on your accuracy and speed". This multi-faceted prompt, combining meta-knowledge, examples, and role-playing, is tuned specifically for the final workflow to maximize accuracy. 

<mark>** 3. 工作流级提示优化（Workflow-Level Prompt Optimization）：** 最终阶段涉及对整个系统提示的全局优化。在识别出性能最佳的拓扑结构后，将提示作为单一、集成的实体进行微调，以确保它们适应编排，并优化智能体之间的相互依赖关系。例如，在找到 DROP 数据集的最佳拓扑结构后，最终优化阶段会精炼**「预测智能体」（"Predictor" agent）的提示。最终优化后的提示高度详细**，首先向智能体提供数据集本身的摘要，指出其侧重于**「抽取式问答」（"extractive question answering"）和「数值信息」（"numerical information"）。然后，它包含少量示例**（few-shot examples），展示正确的问答行为，并将核心指令框定为一个高风险场景：「你是一个高度专业化的 AI，任务是为一篇紧急新闻报道提取关键的数值信息。一次现场直播正依赖你的准确性和速度」。这种结合了元知识、示例和角色扮演的多方面提示，是专门针对最终工作流进行调优的，以最大限度地提高准确性。</mark>

Key Findings and Principles: Experiments demonstrate that MAS optimized by MASS significantly outperform existing manually designed systems and other automated design methods across a range of tasks. The key design principles for effective MAS, as derived from this research, are threefold:

<mark>关键发现与原则： 实验证明，经 MASS 优化的 MAS 在一系列任务中的表现显著优于现有手动设计的系统和其他自动化设计方法。根据这项研究得出的有效 MAS 的关键设计原则有三点：</mark>

  * Optimize individual agents with high-quality prompts before composing them.
  * Construct MAS by composing influential topologies rather than exploring an unconstrained search space.
  * Model and optimize the interdependencies between agents through a final, workflow-level joint optimization.

<mark>
  * 在组合智能体之前，使用高质量的提示来优化单个智能体。
  * 通过组合有影响力的拓扑结构来构建 MAS，而不是探索无约束的搜索空间。
  * 通过最终的工作流级联合优化，对智能体之间的相互依赖关系进行建模和优化。</mark>

Building on our discussion of key reasoning techniques, let's first examine a core performance principle: the Scaling Inference Law for LLMs. This law states that a model's performance predictably improves as the computational resources allocated to it increase. We can see this principle in action in complex systems like Deep Research, where an AI agent leverages these resources to autonomously investigate a topic by breaking it down into sub-questions, using Web search as a tool, and synthesizing its findings.

<mark>在我们讨论了关键推理技巧之后，首先让我们考察一个核心性能原则：LLM 的推理扩展定律（Scaling Inference Law for LLMs）。该定律指出，随着分配给模型的计算资源增加，模型的性能会可预测地提高。我们可以看到，在像深度研究（Deep Research）这样的复杂系统中，这个原则正在发挥作用，AI 智能体利用这些资源自主调查一个主题：将其分解为子问题，使用 Web 搜索作为工具，并综合其发现。</mark>

**Deep Research.** The term "Deep Research" describes a category of AI Agentic tools designed to act as tireless, methodical research assistants. Major platforms in this space include Perplexity AI, Google's Gemini research capabilities, and OpenAI's advanced functions within ChatGPT (see Fig.5).

<mark>** 深度研究（Deep Research）。** 「深度研究」一词描述了一类具智能体特性（Agentic）的 AI 工具，它们旨在充当不知疲倦、有条不紊的研究助理。该领域的主要平台包括 Perplexity AI、Google Gemini 的研究能力以及 OpenAI ChatGPT 内部的高级功能（参见图 5）。</mark>

<img width="1314" height="1402" alt="image" src="https://github.com/user-attachments/assets/a475f47d-69c3-4dd7-8e8b-2827e1d0f17d" />

Fig. 5: Google Deep Research for Information Gathering
<mark>图 5：用于信息收集的 Google Deep Research</mark>

A fundamental shift introduced by these tools is the change in the search process itself. A standard search provides immediate links, leaving the work of synthesis to you. Deep Research operates on a different model. Here, you task an AI with a complex query and grant it a "time budget"—usually a few minutes. In return for this patience, you receive a detailed report.

<mark>这些工具带来的一个根本性转变是搜索过程本身的改变。标准搜索会立即提供链接，将综合整理的工作留给你。而深度研究则采用不同的模式。在这里，你给 AI 分配一个复杂的查询任务，并授予它一个「时间预算」——通常是几分钟。作为这种耐心的回报，你将收到一份详细的报告*。</mark>

During this time, the AI works on your behalf in an agentic way. It autonomously performs a series of sophisticated steps that would be incredibly time-consuming for a person:

<mark>在此期间，AI 以一种具智能体特性的方式为你工作。它自主执行一系列复杂且对人来说极其耗时的步骤：</mark>

1. Initial Exploration: It runs multiple, targeted searches based on your initial prompt.

<mark>1. 初始探索： 它根据你的初始提示运行多个有针对性的搜索。</mark>

2. Reasoning and Refinement: It reads and analyzes the first wave of results, synthesizes the findings, and critically identifies gaps, contradictions, or areas that require more detail.

<mark>2. 推理与精炼： 它阅读和分析第一波结果，综合其发现，并批判性地识别出空白、矛盾或需要更多细节的领域。</mark>

3. Follow-up Inquiry: Based on its internal reasoning, it conducts new, more nuanced searches to fill those gaps and deepen its understanding.

<mark>3. 后续探究： 基于其内部推理，它进行新的、更细致的搜索，以填补这些空白并加深其理解。</mark>

4. Final Synthesis: After several rounds of this iterative searching and reasoning, it compiles all the validated information into a single, cohesive, and structured summary.

<mark>4. 最终综合： 经过多轮这种迭代搜索和推理后，它将所有经过验证的信息汇编成一个单一、有凝聚力且结构化的摘要。</mark>

This systematic approach ensures a comprehensive and well-reasoned response, significantly enhancing the efficiency and depth of information gathering, thereby facilitating more agentic decision-making.

<mark>这种系统方法确保了全面且有充分理由支持的响应，显著提高了信息收集的效率和深度，从而促进了更具智能体特性的决策制定。</mark>
