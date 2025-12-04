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

<mark>MASS 采用一种多阶段优化策略，通过交错进行提示优化和拓扑优化，系统地导航复杂的设计空间（参见图 4）。</mark>

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

<mark>这些工具带来的一个根本性转变是搜索过程本身的改变。标准搜索会立即提供链接，将综合整理的工作留给你。而深度研究则采用不同的模式。在这里，你给 AI 分配一个复杂的查询任务，并授予它一个「时间预算」——通常是几分钟。作为这种耐心的回报，你将收到一份详细的报告。</mark>

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

## Scaling Inference Law
This critical principle dictates the relationship between an LLM's performance and the computational resources allocated during its operational phase, known as inference. The Inference Scaling Law differs from the more familiar scaling laws for training, which focus on how model quality improves with increased data volume and computational power during a model's creation. Instead, this law specifically examines the dynamic trade-offs that occur when an LLM is actively generating an output or answer.
A cornerstone of this law is the revelation that superior results can frequently be achieved from a comparatively smaller LLM by augmenting the computational investment at inference time. This doesn't necessarily mean using a more powerful GPU, but rather employing more sophisticated or resource-intensive inference strategies. A prime example of such a strategy is instructing the model to generate multiple potential answers—perhaps through techniques like diverse beam search or self-consistency methods—and then employing a selection mechanism to identify the most optimal output. This iterative refinement or multiple-candidate generation process demands more computational cycles but can significantly elevate the quality of the final response.
This principle offers a crucial framework for informed and economically sound decision-making in the deployment of Agents systems. It challenges the intuitive notion that a larger model will always yield better performance. The law posits that a smaller model, when granted a more substantial "thinking budget" during inference, can occasionally surpass the performance of a much larger model that relies on a simpler, less computationally intensive generation process. The "thinking budget" here refers to the additional computational steps or complex algorithms applied during inference, allowing the smaller model to explore a wider range of possibilities or apply more rigorous internal checks before settling on an answer.
Consequently, the Scaling Inference Law becomes fundamental to constructing efficient and cost-effective Agentic systems. It provides a methodology for meticulously balancing several interconnected factors:
●**Model Size**: Smaller models are inherently less demanding in terms of memory and storage.
●**Response Latency**: While increased inference-time computation can add to latency, the law helps identify the point at which the performance gains outweigh this increase, or how to strategically apply computation to avoid excessive delays.
●**Operational Cost**: Deploying and running larger models typically incurs higher ongoing operational costs due to increased power consumption and infrastructure requirements. The law demonstrates how to optimize performance without unnecessarily escalating these costs.
By understanding and applying the Scaling Inference Law, developers and organizations can make strategic choices that lead to optimal performance for specific agentic applications, ensuring that computational resources are allocated where they will have the most significant impact on the quality and utility of the LLM's output. This allows for more nuanced and economically viable approaches to AI deployment, moving beyond a simple "bigger is better" paradigm.
<mark>
## 推理缩放定律 
这一关键原则规定了在 LLM 的运行阶段（称为推理）期间，LLM 的性能与分配给它的计算资源之间的关系。推理缩放定律不同于更熟悉的训练缩放定律，后者侧重于模型的质量如何随着模型创建过程中的数据量和计算能力的增加而提高。相反，该定律专门研究当 LLM 积极生成输出或答案时所发生的动态权衡。

该定律的一个基石在于揭示，通过在推理时增加计算投入，往往可以从小型的 LLM 中获得更优的结果。这不一定意味着使用更强大的 GPU，而是采用更复杂或资源密集型的推理策略。这种策略的一个主要例子是指示模型生成多个潜在答案——可能通过诸如多样化束搜索或自洽性方法等技术——然后采用选择机制来确定最优输出。这种迭代精炼或多候选生成过程需要更多的计算周期，但可以显著提升最终响应的质量。

该原则为 Agent 系统部署中的知情且经济合理的决策提供了一个关键框架。它挑战了“更大的模型总是能带来更好性能”的直观观念。该定律认为，在推理过程中，一个较小的模型如果获得更多的“思考预算”，有时可以超越一个依赖于更简单、计算密集度较低的生成过程的更大模型。“思考预算”在此指的是在推理过程中应用的额外计算步骤或复杂算法，它允许较小的模型在最终确定答案之前探索更广泛的可能性或应用更严格的内部检查。

因此，推理缩放定律对于构建高效且成本效益高的 Agentic 系统至关重要。它提供了一种细致平衡几个相互关联因素的方法：

●**模型大小**：较小的模型在内存和存储方面本身要求较低。
●**响应延迟**：虽然增加推理时间的计算会增加延迟，但该定律有助于确定性能提升超过这种增加的阈值，或者如何策略性地应用计算以避免过度的延迟。
●**运营成本**：部署和运行更大的模型通常会因更高的功耗和基础设施需求而产生更高的持续运营成本。该定律展示了如何在不不必要地增加这些成本的情况下优化性能。

通过理解和应用推理缩放定律，开发人员和组织可以做出战略选择，从而为特定的 agentic 应用带来最佳性能，确保计算资源被分配到对 LLM 输出的质量和效用影响最大的地方。这使得 AI 部署能够采取更细致、经济上可行的方​​法，超越简单的“越大越好”的范式。
</mark>

## Hands-On Code Example
The DeepSearch code, open-sourced by Google, is available through the gemini-fullstack-langgraph-quickstart repository (Fig. 6). This repository provides a template for developers to construct full-stack AI agents using Gemini 2.5 and the LangGraph orchestration framework. This open-source stack facilitates experimentation with agent-based architectures and can be integrated with local LLLMs such as Gemma. It utilizes Docker and modular project scaffolding for rapid prototyping. It should be noted that this release serves as a well-structured demonstration and is not intended as a production-ready backend.

<mark>Google 开源的 DeepSearch 代码，可通过 gemini-fullstack-langgraph-quickstart 仓库（图 6）获取。该仓库为开发者提供了一个模板，用于使用 Gemini 2.5 和 LangGraph 编排框架构建全栈 AI 智能体。这种开源栈便于进行智能体架构的实验，并可与 Gemma 等本地 LLM 集成。它利用 Docker 和模块化项目脚手架实现快速原型开发。需要注意的是，本次发布是一个结构良好的演示，并非用于生产环境的后端。</mark>

<img width="959" height="1474" alt="image" src="https://github.com/user-attachments/assets/32c32593-42c9-41eb-bd69-d31137dd22cc" />

Fig. 6: (Courtesy of authors) Example of DeepSearch with multiple Reflection steps
图 6：（作者提供）包含多个反思步骤的 DeepSearch 示例

This project provides a full-stack application featuring a React frontend and a LangGraph backend, designed for advanced research and conversational AI. A LangGraph agent dynamically generates search queries using Google Gemini models and integrates web research via the Google Search API. The system employs reflective reasoning to identify knowledge gaps, refine searches iteratively, and synthesize answers with citations. The frontend and backend support hot-reloading. The project's structure includes separate frontend/ and backend/ directories. Requirements for setup include Node.js, npm, Python 3.8+, and a Google Gemini API key. After configuring the API key in the backend's .env file, dependencies for both the backend (using pip install .) and frontend (npm install) can be installed. Development servers can be run concurrently with make dev or individually. The backend agent, defined in backend/src/agent/graph.py, generates initial search queries, conducts web research, performs knowledge gap analysis, refines queries iteratively, and synthesizes a cited answer using a Gemini model. Production deployment involves the backend server delivering a static frontend build and requires Redis for streaming real-time output and a Postgres database for managing data. A Docker image can be built and run using docker-compose up, which also requires a LangSmith API key for the docker-compose.yml example. The application utilizes React with Vite, Tailwind CSS, Shadcn UI, LangGraph, and Google Gemini. The project is licensed under the Apache License 2.0.
<mark>
本项目提供了一个全栈应用程序，包含 React 前端和 LangGraph 后端，专为高级研究和对话式 AI 设计。LangGraph 智能体使用 Google Gemini 模型动态生成搜索查询，并通过 Google Search API 集成网络研究。该系统采用反思性推理来识别知识差距，迭代地优化搜索，并合成带引用的答案。前端和后端支持热重载。项目的结构包括独立的 frontend/ 和 backend/ 目录。设置要求包括 Node.js、npm、Python 3.8+ 和 Google Gemini API 密钥。在配置好后端 .env 文件中的 API 密钥后，可以安装后端（使用 pip install .）和前端（npm install）的依赖项。开发服务器可以与 make dev 同时运行，或单独运行。后端智能体定义在 backend/src/agent/graph.py 中，负责生成初始搜索查询，进行网络研究，执行知识差距分析，迭代优化查询，并使用 Gemini 模型合成带引用的答案。生产部署涉及后端服务器交付静态前端构建，并需要 Redis 进行实时输出流式传输，以及 Postgres 数据库用于管理数据。可以使用 docker-compose up 构建和运行 Docker 镜像，该镜像也需要 LangSmith API 密钥用于 docker-compose.yml 示例。该应用程序使用 Vite、Tailwind CSS、Shadcn UI、LangGraph 和 Google Gemini 的 React。该项目根据 Apache License 2.0 授权。
</mark>

```python
# Create our Agent Graph
builder = StateGraph(OverallState, config_schema=Configuration)
# Define the nodes we will cycle between
builder.add_node("generate_query", generate_query)
builder.add_node("web_research", web_research)
builder.add_node("reflection", reflection)
builder.add_node("finalize_answer", finalize_answer)
# Set the entrypoint as `generate_query`
# This means that this node is the first one called
builder.add_edge(START, "generate_query")
# Add conditional edge to continue with search queries in a parallel
branch
builder.add_conditional_edges(
   "generate_query", continue_to_web_research, ["web_research"]
)
# Reflect on the web research
builder.add_edge("web_research", "reflection")
# Evaluate the research
builder.add_conditional_edges(
   "reflection", evaluate_research, ["web_research",
"finalize_answer"]
)
# Finalize the answer
builder.add_edge("finalize_answer", END)
graph = builder.compile(name="pro-search-agent")
```
Fig.4: Example of DeepSearch with LangGraph (code from backend/src/agent/graph.py)
## So, what do agents think?
In summary, an agent's thinking process is a structured approach that combines reasoning and acting to solve problems. This method allows an agent to explicitly plan its steps, monitor its progress, and interact with external tools to gather information.
At its core, the agent's "thinking" is facilitated by a powerful LLM. This LLM generates a series of thoughts that guide the agent's subsequent actions. The process typically follows a thought-action-observation loop:
1. **Thought**:Theagentfirstgeneratesatextualthoughtthatbreaksdownthe problem, formulates a plan, or analyzes the current situation. This internal monologue makes the agent's reasoning process transparent and steerable.
2. **Action**:Basedonthethought,theagentselectsanactionfromapredefined, discrete set of options. For example, in a question-answering scenario, the action space might include searching online, retrieving information from a specific webpage, or providing a final answer.
3. **Observation**:Theagentthenreceivesfeedbackfromitsenvironmentbasedon the action taken. This could be the results of a web search or the content of a webpage.
This cycle repeats, with each observation informing the next thought, until the agent determines that it has reached a final solution and performs a "finish" action.
The effectiveness of this approach relies on the advanced reasoning and planning capabilities of the underlying LLM. To guide the agent, the ReAct framework often employs few-shot learning, where the LLM is provided with examples of human-like problem-solving trajectories. These examples demonstrate how to effectively combine thoughts and actions to solve similar tasks.
The frequency of an agent's thoughts can be adjusted depending on the task. For knowledge-intensive reasoning tasks like fact-checking, thoughts are typically interleaved with every action to ensure a logical flow of information gathering and reasoning. In contrast, for decision-making tasks that require many actions, such as navigating a simulated environment, thoughts may be used more sparingly, allowing the agent to decide when thinking is necessary
<mark>
## 那么，智能体是如何思考的？

简单来说，智能体的思考过程是一种结构化的方法，它结合了推理和行动来解决问题。这种方法允许智能体明确地规划其步骤、监控其进展，并与外部工具交互以收集信息。

其核心在于，智能体的“思考”是由一个强大的大语言模型（LLM）驱动的。这个 LLM 会生成一系列指导智能体后续行动的思考。整个过程通常遵循一个“思考-行动-观察”的循环：

1.  **思考 (Thought)**：智能体首先生成一个文本思考，该思考会分解问题、制定计划或分析当前情况。这种内部的独白使得智能体的推理过程透明且可控。
2.  **行动 (Action)**：基于思考，智能体从一组预定义的、离散的选项中选择一个行动。例如，在问答场景中，行动空间可能包括在线搜索、从特定网页检索信息，或提供最终答案。
3.  **观察 (Observation)**：智能体随后根据所采取的行动接收来自环境的反馈。这可能是网络搜索的结果，或是网页的内容。

这个循环会不断重复，每一次观察都会为下一次思考提供信息，直到智能体确定它已达成最终解决方案并执行“完成”行动。

这种方法的有效性依赖于底层 LLM 的高级推理和规划能力。为了指导智能体，ReAct 框架通常采用少样本学习（few-shot learning），即向 LLM 提供类似人类解决问题轨迹的示例。这些示例演示了如何有效地结合思考和行动来解决相似的任务。

智能体的思考频率可以根据任务进行调整。对于像事实核查这样的知识密集型推理任务，思考通常会与每个行动交织进行，以确保信息收集和推理的逻辑流程。相比之下，对于需要许多行动的决策任务，例如在模拟环境中导航，思考可能会更谨慎地使用，让智能体自行决定何时需要思考。
</mark>

## At a Glance
**What**: Complex problem-solving often requires more than a single, direct answer, posing a significant challenge for AI. The core problem is enabling AI agents to tackle multi-step tasks that demand logical inference, decomposition, and strategic planning. Without a structured approach, agents may fail to handle intricacies, leading to inaccurate or incomplete conclusions. These advanced reasoning methodologies aim to make an agent's internal "thought" process explicit, allowing it to systematically work through challenges.
**Why**: The standardized solution is a suite of reasoning techniques that provide a structured framework for an agent's problem-solving process. Methodologies like Chain-of-Thought (CoT) and Tree-of-Thought (ToT) guide LLMs to break down problems and explore multiple solution paths. Self-Correction allows for the iterative refinement of answers, ensuring higher accuracy. Agentic frameworks like ReAct integrate reasoning with action, enabling agents to interact with external tools and environments to gather information and adapt their plans. This combination of explicit reasoning, exploration, refinement, and tool use creates more robust, transparent, and capable AI systems.
**Rule of thumb**: Use these reasoning techniques when a problem is too complex for a single-pass answer and requires decomposition, multi-step logic, interaction with external data sources or tools, or strategic planning and adaptation. They are ideal for tasks where showing the "work" or thought process is as important as the final answer.

<mark>
## 要点速览

**问题所在 (What)**：复杂问题的解决常常需要不止一个直接答案，这对 AI 构成了重大挑战。核心问题是如何让 AI 智能体能够处理需要逻辑推理、分解和战略规划的多步骤任务。没有结构化的方法，智能体可能无法处理其中的复杂性，导致不准确或不完整的结论。这些高级推理方法旨在使智能体的内部“思考”过程明确化，从而使其能够系统地应对挑战。

**解决之道 (Why)**：标准化的解决方案是一系列推理技术，为智能体的解决问题过程提供了一个结构化框架。像思维链（Chain-of-Thought, CoT）和思维树（Tree-of-Thought, ToT）这样的方法可以指导 LLM 分解问题并探索多种解决方案路径。自我纠正（Self-Correction）则允许对答案进行迭代改进，确保更高的准确性。ReAct 等智能体框架将推理与行动相结合，使智能体能够与外部工具和环境交互以收集信息并调整其计划。这种显性推理、探索、改进和工具使用的结合，创造了更强大、更透明、能力更强的 AI 系统。

**经验法则 (Rule of thumb)**：当一个问题过于复杂，无法一次性给出答案，需要分解、多步逻辑、与外部数据源或工具交互，或是需要战略规划和适应时，请使用这些推理技术。它们非常适用于那些展示“工作过程”或思考过程与最终答案同等重要的任务。
</mark>
**Visual summary**
<mark>**可视化总结**</mark>
<img width="2048" height="1445" alt="image" src="https://github.com/user-attachments/assets/8b2dd85e-4c14-4582-809a-ecf9410f0f51" />
Fig. 7: Reasoning design pattern
<mark>图 7：推理设计模式</mark>

● By making their reasoning explicit, agents can formulate transparent, multi-step plans, which is the foundational capability for autonomous action and user trust.
<mark>● 通过明确其推理过程，智能体能够制定透明的、多步骤的计划，这是实现自主行动和赢得用户信任的基础能力。</mark>

● The ReAct framework provides agents with their core operational loop, empowering them to move beyond mere reasoning and interact with external tools to dynamically act and adapt within an environment.
<mark>● ReAct 框架为智能体提供了其核心的操作循环，使其能够超越单纯的推理，并与外部工具进行交互，从而在环境中动态地行动和适应。</mark>

● The Scaling Inference Law implies an agent's performance is not just about its underlying model size, but its allocated "thinking time," allowing for more deliberate and higher-quality autonomous actions.
<mark>● 推理缩放定律（Scaling Inference Law）表明，智能体的性能不仅与其底层模型的大小有关，还与其分配的“思考时间”有关，这使得智能体能够执行更审慎、更高质量的自主行动。</mark>

● Chain-of-Thought (CoT) serves as an agent's internal monologue, providing a structured way to formulate a plan by breaking a complex goal into a sequence of manageable actions.
<mark>● 思维链（Chain-of-Thought, CoT）作为智能体的内部独白，通过将复杂的目标分解为一系列可管理的操作，提供了一种结构化的方法来制定计划。</mark>

● Tree-of-Thought and Self-Correction give agents the crucial ability to deliberate, allowing them to evaluate multiple strategies, backtrack from errors, and improve their own plans before execution.
<mark>● 思维树（Tree-of-Thought）和自我修正（Self-Correction）赋予智能体关键的审议能力，使其能够在执行前评估多种策略、从错误中回溯并改进自己的计划。</mark>

● Collaborative frameworks like Chain of Debates (CoD) signal the shift from solitary agents to multi-agent systems, where teams of agents can reason together to tackle more complex problems and reduce individual biases.
<mark>● 像辩论链（Chain of Debates, CoD）这样的协作框架标志着从单个智能体向多智能体系统的转变，在这种系统中，智能体团队可以协同推理，以解决更复杂的问题并减少个体偏见。</mark>

● Applications like Deep Research demonstrate how these techniques culminate in agents that can execute complex, long-running tasks, such as in-depth investigation, completely autonomously on a user's behalf.
<mark>● 像深度研究（Deep Research）这样的应用展示了这些技术如何最终转化为智能体，使其能够完全代表用户自主执行复杂的、耗时长的任务，例如深度调查。</mark>

● To build effective teams of agents, frameworks like MASS automate the optimization of how individual agents are instructed and how they interact, ensuring the entire multi-agent system performs optimally.
<mark>● 为了构建有效的智能体团队，MASS 等框架自动化了单个智能体指令的下发方式及其交互的优化过程，确保整个多智能体系统能够以最佳状态运行。</mark>

● By integrating these reasoning techniques, we build agents that are not just automated but truly autonomous, capable of being trusted to plan, act, and solve complex problems without direct supervision.
<mark>● 通过整合这些推理技术，我们构建的智能体不仅是自动化的，更是真正自主的，能够被信任在无需直接监督的情况下进行规划、行动和解决复杂问题。</mark>

---

## Conclusions
<mark>## 结语</mark>

Modern AI is evolving from passive tools into autonomous agents, capable of tackling complex goals through structured reasoning.
<mark>现代人工智能正从被动的工具演变为能够通过结构化推理来达成复杂目标的自主智能体。</mark>

This agentic behavior begins with an internal monologue, powered by techniques like Chain-of-Thought (CoT), which allows an agent to formulate a coherent plan before acting.
<mark>这种具智能体特性的行为始于内部独白，由思维链（CoT）等技术驱动，使智能体在行动前能够制定连贯的计划。</mark>

True autonomy requires deliberation, which agents achieve through Self-Correction and Tree-of-Thought (ToT), enabling them to evaluate multiple strategies and independently improve their own work.
<mark>真正的自主性需要审议，智能体通过自我修正和思维树（ToT）来实现这一点，使其能够评估多种策略并独立改进自身工作。</mark>

The pivotal leap to fully agentic systems comes from the ReAct framework, which empowers an agent to move beyond thinking and start acting by using external tools.
<mark>向完全具智能体特性的系统迈进的关键一步来自于 ReAct 框架，它使智能体能够通过使用外部工具，超越单纯的思考而开始行动。</mark>

This establishes the core agentic loop of thought, action, and observation, allowing the agent to dynamically adapt its strategy based on environmental feedback.
<mark>这确立了思考、行动和观察的核心智能体循环，使智能体能够根据环境反馈动态地调整其策略。</mark>

An agent's capacity for deep deliberation is fueled by the Scaling Inference Law, where more computational "thinking time" directly translates into more robust autonomous actions.
<mark>智能体深度审议的能力由推理缩放定律（Scaling Inference Law）驱动，更多的计算“思考时间”直接转化为更鲁棒的自主行动。</mark>

The next frontier is the multi-agent system, where frameworks like Chain of Debates (CoD) create collaborative agent societies that reason together to achieve a common goal.
<mark>下一个前沿是多智能体系统，其中辩论链（CoD）等框架创建了协作性的智能体社会，它们能够协同推理以达成共同目标。</mark>

This is not theoretical; agentic applications like Deep Research already demonstrate how autonomous agents can execute complex, multi-step investigations on a user's behalf.
<mark>这并非纸上谈兵；像深度研究（Deep Research）这样的具智能体应用已经展示了自主智能体如何能代表用户执行复杂的、多步骤的调查。</mark>

The overarching goal is to engineer reliable and transparent autonomous agents that can be trusted to independently manage and solve intricate problems.
<mark>总体的目标是构建可靠且透明的自主智能体，这些智能体能够被信任独立地管理和解决复杂的难题。</mark>

Ultimately, by combining explicit reasoning with the power to act, these methodologies are completing the transformation of AI into truly agentic problem-solvers.
<mark>最终，通过将明确的推理与行动能力相结合，这些方法论正在完成人工智能向真正具智能体特性的问题解决者的转变。</mark>

---

## References
<mark>## 参考文献</mark>

Relevant research includes:
<mark>相关研究包括：</mark>

1. "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models" by Wei et al. (2022)
<mark>1. Wei 等人（2022）的《Chain-of-Thought Prompting Elicits Reasoning in Large Language Models》</mark>

2. "Tree of Thoughts: Deliberate Problem Solving with Large Language Models" by Yao et al. (2023)
<mark>2. Yao 等人（2023）的《Tree of Thoughts: Deliberate Problem Solving with Large Language Models》</mark>

3. "Program-Aided Language Models" by Gao et al. (2023)
<mark>3. Gao 等人（2023）的《Program-Aided Language Models》</mark>

4. "ReAct: Synergizing Reasoning and Acting in Language Models" by Yao et al. (2023)
<mark>4. Yao 等人（2023）的《ReAct: Synergizing Reasoning and Acting in Language Models》</mark>

5. Inference Scaling Laws: An Empirical Analysis of Compute-Optimal Inference for LLM Problem-Solving, 2024
<mark>5. 《Inference Scaling Laws: An Empirical Analysis of Compute-Optimal Inference for LLM Problem-Solving》, 2024</mark>

6. Multi-Agent Design: Optimizing Agents with Better Prompts and Topologies, https://arxiv.org/abs/2502.02533
<mark>6. 《Multi-Agent Design: Optimizing Agents with Better Prompts and Topologies》, https://arxiv.org/abs/2502.02533</mark>

