# Chapter 21: Exploration and Discovery | <mark>第二十一章：探索与发现</mark>

This chapter explores patterns that enable intelligent agents to actively seek out novel information, uncover new possibilities, and identify unknown unknowns within their operational environment. Exploration and discovery differ from reactive behaviors or optimization within a predefined solution space. Instead, they focus on agents proactively venturing into unfamiliar territories, experimenting with new approaches, and generating new knowledge or understanding. This pattern is crucial for agents operating in open-ended, complex, or rapidly evolving domains where static knowledge or pre-programmed solutions are insufficient. It emphasizes the agent's capacity to expand its understanding and capabilities.

<mark>本章探讨的模式使智能体能够主动寻找新信息、发现新可能性，并识别其运行环境中的未知之未知。探索与发现模式不同于在预定义解决方案空间内的反应式行为或优化。相反，它们侧重于智能体主动进入陌生领域、尝试新方法并生成新知识或理解。对于在开放式、复杂或快速演变的领域中运行的智能体来说，这种模式至关重要，因为在这些领域中，静态知识或预编程解决方案是不够的。它强调智能体扩展其理解和能力的潜力。</mark>

---

## Practical Applications & Use Cases | <mark>实际应用场景</mark>

AI agents possess the ability to intelligently prioritize and explore, which leads to applications across various domains. By autonomously evaluating and ordering potential actions, these agents can navigate complex environments, uncover hidden insights, and drive innovation. This capacity for prioritized exploration enables them to optimize processes, discover new knowledge, and generate content.

<mark>AI 智能体拥有智能化优先排序和探索的能力，这使其能够在各个领域中得到应用。通过自主评估和排序潜在行动，这些智能体可以在复杂环境中导航、发现隐藏的洞察并推动创新。这种优先探索的能力使它们能够优化流程、发现新知识并生成内容。</mark>

Examples:

<mark>示例：</mark>

- **Scientific Research Automation:** An agent designs and runs experiments, analyzes results, and formulates new hypotheses to discover novel materials, drug candidates, or scientific principles.

  <mark><strong>科学研究自动化：</strong>智能体设计和运行实验、分析结果并提出新假设，以发现新材料、候选药物或科学原理。</mark>

- **Game Playing and Strategy Generation:** Agents explore game states, discovering emergent strategies or identifying vulnerabilities in game environments (e.g., AlphaGo).

  <mark><strong>游戏博弈与策略生成：</strong>智能体探索游戏状态，发现涌现策略或识别游戏环境中的漏洞（例如 AlphaGo）。</mark>

- **Market Research and Trend Spotting:** Agents scan unstructured data (social media, news, reports) to identify trends, consumer behaviors, or market opportunities.

  <mark><strong>市场研究和趋势发现：</strong>智能体扫描非结构化数据（社交媒体、新闻、报告）以识别趋势、消费者行为或市场机会。</mark>

- **Security Vulnerability Discovery:** Agents probe systems or codebases to find security flaws or attack vectors.

  <mark><strong>安全漏洞发现：</strong>智能体探测系统或代码库以发现安全漏洞或攻击向量。</mark>

- **Creative Content Generation:** Agents explore combinations of styles, themes, or data to generate artistic pieces, musical compositions, or literary works.

  <mark><strong>创意内容生成：</strong>智能体探索风格、主题或数据的组合，以生成艺术作品、音乐作品或文学作品。</mark>

- **Personalized Education and Training:** AI tutors prioritize learning paths and content delivery based on a student's progress, learning style, and areas needing improvement.

  <mark><strong>个性化教育和培训：</strong>AI 导师根据学生的进度、学习风格和需要改进的领域来优先安排学习路径和内容交付。</mark>

### Google Co-Scientist | <mark>Google 协作科学家</mark>

An AI co-scientist is an AI system developed by Google Research designed as a computational scientific collaborator. It assists human scientists in research aspects such as hypothesis generation, proposal refinement, and experimental design. This system operates on the Gemini LLM.

<mark>AI 协作科学家是 Google Research 开发的一个 AI 系统，旨在作为计算科学协作者。它协助人类科学家进行研究，包括假设生成、提案优化和实验设计等方面。该系统基于 Gemini 大语言模型运行。</mark>

The development of the AI co-scientist addresses challenges in scientific research. These include processing large volumes of information, generating testable hypotheses, and managing experimental planning. The AI co-scientist supports researchers by performing tasks that involve large-scale information processing and synthesis, potentially revealing relationships within data. Its purpose is to augment human cognitive processes by handling computationally demanding aspects of early-stage research.

<mark>AI 协作科学家的开发旨在解决科学研究中的挑战。这些挑战包括处理大量信息、生成可测试的假设以及管理实验计划。AI 协作科学家通过执行涉及大规模信息处理和综合的任务来支持研究人员，可能会揭示数据中的关系。其目的是通过处理早期研究中计算密集型的方面来增强人类认知过程。</mark>

**System Architecture and Methodology:** The architecture of the AI co-scientist is based on a multi-agent framework, structured to emulate collaborative and iterative processes. This design integrates specialized AI agents, each with a specific role in contributing to a research objective. A supervisor agent manages and coordinates the activities of these individual agents within an asynchronous task execution framework that allows for flexible scaling of computational resources.

<mark><strong>系统架构和方法：</strong>AI 协作科学家的架构基于多智能体框架，旨在模拟协作和迭代过程。该设计集成了专门的 AI 智能体，每个智能体在实现研究目标方面都有特定的角色。监督智能体在异步任务执行框架内管理和协调这些单个智能体的活动，该框架允许计算资源的灵活扩展。</mark>

The core agents and their functions include (see Fig. 1):

<mark>核心智能体及其功能包括（见图 1）：</mark>

- **Generation agent:** Initiates the process by producing initial hypotheses through literature exploration and simulated scientific debates.

  <mark><strong>生成智能体：</strong>通过文献探索和模拟科学辩论生成初始假设来启动该过程。</mark>

- **Reflection agent:** Acts as a peer reviewer, critically assessing the correctness, novelty, and quality of the generated hypotheses.

  <mark><strong>反思智能体：</strong>作为同行评审者，批判性地评估生成假设的正确性、新颖性和质量。</mark>

- **Ranking agent:** Employs an Elo-based tournament to compare, rank, and prioritize hypotheses through simulated scientific debates.

  <mark><strong>排名智能体：</strong>采用基于 Elo 评级的竞赛模式，通过模拟科学辩论来比较、排名和优先排序假设。</mark>

- **Evolution agent:** Continuously refines top-ranked hypotheses by simplifying concepts, synthesizing ideas, and exploring unconventional reasoning.

  <mark><strong>演化智能体：</strong>通过简化概念、综合想法和探索非常规推理来持续优化排名靠前的假设。</mark>

- **Proximity agent:** Computes a proximity graph to cluster similar ideas and assist in exploring the hypothesis landscape.

  <mark><strong>邻近智能体：</strong>计算邻近图以聚类相似的想法，并协助探索假设空间。</mark>

- **Meta-review agent:** Synthesizes insights from all reviews and debates to identify common patterns and provide feedback, enabling the system to continuously improve.

  <mark><strong>元评审智能体：</strong>综合所有评审和辩论的见解，以识别共同模式并提供反馈，使系统能够持续改进。</mark>

The system's operational foundation relies on Gemini, which provides language understanding, reasoning, and generative abilities. The system incorporates "test-time compute scaling," a mechanism that allocates increased computational resources to iteratively reason and enhance outputs. The system processes and synthesizes information from diverse sources, including academic literature, web-based data, and databases.

<mark>该系统的运行基础依赖于 Gemini，它提供语言理解、推理和生成能力。该系统采用「测试时计算扩展」机制，该机制分配更多的计算资源以迭代推理并增强输出。该系统处理和综合来自不同来源的信息，包括学术文献、网络数据和数据库。</mark>

![AI Co-Scientist: Ideation to Validation](/images/chapter21_fig1.png)

Fig. 1: (Courtesy of the Authors) AI Co-Scientist: Ideation to Validation

<mark>图 1：（由作者提供）AI 协作科学家：从构思到验证</mark>

The system follows an iterative "generate, debate, and evolve" approach mirroring the scientific method. Following the input of a scientific problem from a human scientist, the system engages in a self-improving cycle of hypothesis generation, evaluation, and refinement. Hypotheses undergo systematic assessment, including internal evaluations among agents and a tournament-based ranking mechanism.

<mark>该系统遵循迭代的「生成、辩论和演化」方法，反映了科学方法。在接收来自人类科学家的科学问题输入后，该系统进入假设生成、评估和优化的自我改进循环。假设经过系统性评估，包括智能体之间的内部评估和基于竞赛的排名机制。</mark>

**Validation and Results:** The AI co-scientist's utility has been demonstrated in several validation studies, particularly in biomedicine, assessing its performance through automated benchmarks, expert reviews, and end-to-end wet-lab experiments.

<mark><strong>验证和结果：</strong>AI 协作科学家的实用性已在多项验证研究中得到证明，特别是在生物医学领域，通过自动化基准测试、专家评审和端到端湿实验室实验来评估其性能。</mark>

**Automated and Expert Evaluation:** On the challenging GPQA benchmark, the system's internal Elo rating was shown to be concordant with the accuracy of its results, achieving a top-1 accuracy of 78.4% on the difficult "diamond set". Analysis across over 200 research goals demonstrated that scaling test-time compute consistently improves the quality of hypotheses, as measured by the Elo rating. On a curated set of 15 challenging problems, the AI co-scientist outperformed other state-of-the-art AI models and the "best guess" solutions provided by human experts. In a small-scale evaluation, biomedical experts rated the co-scientist's outputs as more novel and impactful compared to other baseline models. The system's proposals for drug repurposing, formatted as NIH Specific Aims pages, were also judged to be of high quality by a panel of six expert oncologists.

<mark><strong>自动化和专家评估：</strong>在具有挑战性的 GPQA 基准测试中，该系统的内部 Elo 评级与其结果的准确性一致，在困难的「钻石集」上达到了 78.4% 的 top-1 准确率。对超过 200 个研究目标的分析表明，扩展测试时计算可以持续提高假设质量（通过 Elo 评级衡量）。在精心策划的 15 个具有挑战性的问题集上，AI 协作科学家的表现优于其他最先进的 AI 模型和人类专家提供的「最佳猜测」解决方案。在小规模评估中，生物医学专家认为协作科学家的输出比其他基线模型更新颖、更具影响力。该系统提出的药物重定位提案（格式化为 NIH 特定目标页面）也被六位肿瘤学专家小组评为高质量。</mark>

**End-to-End Experimental Validation:**

<mark><strong>端到端实验验证：</strong></mark>

**Drug Repurposing:** For acute myeloid leukemia (AML), the system proposed novel drug candidates. Some of these, like KIRA6, were completely novel suggestions with no prior preclinical evidence for use in AML. Subsequent in vitro experiments confirmed that KIRA6 and other suggested drugs inhibited tumor cell viability at clinically relevant concentrations in multiple AML cell lines.

<mark><strong>药物再利用：</strong>对于急性髓系白血病（AML），该系统提出了新的候选药物。其中一些，如 KIRA6，是完全新颖的建议，之前没有用于 AML 的临床前证据。随后的体外实验证实，KIRA6 和其他建议的药物在多个 AML 细胞系中以临床相关浓度抑制肿瘤细胞活力。</mark>

**Novel Target Discovery:** The system identified novel epigenetic targets for liver fibrosis. Laboratory experiments using human hepatic organoids validated these findings, showing that drugs targeting the suggested epigenetic modifiers had significant anti-fibrotic activity. One of the identified drugs is already FDA-approved for another condition, opening an opportunity for repurposing.

<mark><strong>新靶点发现：</strong>该系统识别出肝纤维化的新表观遗传靶点。使用人类肝脏类器官的实验室实验验证了这些发现，表明针对建议的表观遗传修饰剂的药物具有显著的抗纤维化活性。识别出的药物之一已被 FDA 批准用于另一种疾病，为再利用提供了机会。</mark>

**Antimicrobial Resistance:** The AI co-scientist independently recapitulated unpublished experimental findings. It was tasked to explain why certain mobile genetic elements (cf-PICIs) are found across many bacterial species. In two days, the system's top-ranked hypothesis was that cf-PICIs interact with diverse phage tails to expand their host range. This mirrored the novel, experimentally validated discovery that an independent research group had reached after more than a decade of research.

<mark><strong>抗菌素耐药性：</strong>AI 协作科学家独立重现了未发表的实验发现。它被要求解释为什么某些可移动遗传元素（cf-PICIs）在许多细菌物种中被发现。在两天内，该系统的最高排名假设是 cf-PICIs 与不同的噬菌体尾部相互作用以扩大其宿主范围。这反映了一个独立研究小组经过十多年研究才达到的新颖、经实验验证的发现。</mark>

**Augmentation, and Limitations:** The design philosophy behind the AI co-scientist emphasizes augmentation rather than complete automation of human research. Researchers interact with and guide the system through natural language, providing feedback, contributing their own ideas, and directing the AI's exploratory processes in a "scientist-in-the-loop" collaborative paradigm. However, the system has some limitations. Its knowledge is constrained by its reliance on open-access literature, potentially missing critical prior work behind paywalls. It also has limited access to negative experimental results, which are rarely published but crucial for experienced scientists. Furthermore, the system inherits limitations from the underlying LLMs, including the potential for factual inaccuracies or "hallucinations".

<mark><strong>增强和局限性：</strong>AI 协作科学家背后的设计理念强调增强而非完全自动化人类研究。研究人员通过自然语言与系统交互并指导系统，提供反馈、贡献自己的想法，并在「科学家在回路中」的协作范式中指导 AI 的探索过程。然而，该系统存在一些局限性。其知识受限于对开放获取文献的依赖，可能会错过付费墙后的关键先前工作。它对负面实验结果的访问也有限，而这些结果很少发表但对经验丰富的科学家至关重要。此外，该系统继承了底层大语言模型的局限性，包括事实不准确或「幻觉」的可能性。</mark>

**Safety:** Safety is a critical consideration, and the system incorporates multiple safeguards. All research goals are reviewed for safety upon input, and generated hypotheses are also checked to prevent the system from being used for unsafe or unethical research. A preliminary safety evaluation using 1,200 adversarial research goals found that the system could robustly reject dangerous inputs. To ensure responsible development, the system is being made available to more scientists through a Trusted Tester Program to gather real-world feedback.

<mark><strong>安全性：</strong>安全性是一个关键考虑因素，该系统包含多重保护措施。所有研究目标在输入时都会进行安全审查，生成的假设也会被检查，以防止系统被用于不安全或不道德的研究。使用 1,200 个对抗性研究目标进行的初步安全评估发现，该系统可以稳健地拒绝危险输入。为确保负责任的开发，该系统正通过可信测试者计划向更多科学家提供，以收集真实世界的反馈。</mark>

---

## Hands-On Code Example | <mark>实战代码示例</mark>

Let's look at a concrete example of agentic AI for Exploration and Discovery in action: Agent Laboratory, a project developed by Samuel Schmidgall under the MIT License.

<mark>让我们看一个探索与发现的智能体 AI 实际应用的具体示例：Agent Laboratory，这是 Samuel Schmidgall 在 MIT 许可证下开发的项目。</mark>

"Agent Laboratory" is an autonomous research workflow framework designed to augment human scientific endeavors rather than replace them. This system leverages specialized LLMs to automate various stages of the scientific research process, thereby enabling human researchers to dedicate more cognitive resources to conceptualization and critical analysis.

<mark>「Agent Laboratory」是一个自主研究工作流框架，旨在增强而非替代人类科学工作。该系统利用专门的大语言模型自动化科学研究过程的各个阶段，从而使人类研究人员能够将更多认知资源用于概念化和批判性分析。</mark>

The framework integrates "AgentRxiv," a decentralized repository for autonomous research agents. AgentRxiv facilitates the deposition, retrieval, and development of research outputs.

<mark>该框架集成了「AgentRxiv」，这是一个用于自主研究智能体的去中心化存储库。AgentRxiv 促进研究成果的存储、检索和开发。</mark>

Agent Laboratory guides the research process through distinct phases:

<mark>Agent Laboratory 通过不同的阶段指导研究过程：</mark>

- **Literature Review:** During this initial phase, specialized LLM-driven agents are tasked with the autonomous collection and critical analysis of pertinent scholarly literature. This involves leveraging external databases such as arXiv to identify, synthesize, and categorize relevant research, effectively establishing a comprehensive knowledge base for the subsequent stages.

  <mark><strong>文献综述：</strong>在这个初始阶段，由大语言模型驱动的专门智能体负责自主收集和批判性分析相关学术文献。这涉及利用 arXiv 等外部数据库来识别、综合和分类相关研究，有效地为后续阶段建立全面的知识库。</mark>

- **Experimentation:** This phase encompasses the collaborative formulation of experimental designs, data preparation, execution of experiments, and analysis of results. Agents utilize integrated tools like Python for code generation and execution, and Hugging Face for model access, to conduct automated experimentation. The system is designed for iterative refinement, where agents can adapt and optimize experimental procedures based on real-time outcomes.

  <mark><strong>实验：</strong>这个阶段包括实验设计的协作制定、数据准备、实验执行和结果分析。智能体利用集成工具（如用于代码生成和执行的 Python，以及用于模型访问的 Hugging Face）进行自动化实验。该系统设计用于迭代优化，智能体可以根据实时结果调整和优化实验程序。</mark>

- **Report Writing:** In the final phase, the system automates the generation of comprehensive research reports. This involves synthesizing findings from the experimentation phase with insights from the literature review, structuring the document according to academic conventions, and integrating external tools like LaTeX for professional formatting and figure generation.

  <mark><strong>报告撰写：</strong>在最后阶段，该系统自动生成全面的研究报告。这涉及将实验阶段的发现与文献综述的见解相结合，根据学术惯例构建文档，并集成外部工具（如 LaTeX）以进行专业格式化和图表生成。</mark>

- **Knowledge Sharing:** AgentRxiv is a platform enabling autonomous research agents to share, access, and collaboratively advance scientific discoveries. It allows agents to build upon previous findings, fostering cumulative research progress.

  <mark><strong>知识共享：</strong>AgentRxiv 是一个平台，使自主研究智能体能够共享、访问和协作推进科学发现。它允许智能体在先前发现的基础上构建，促进累积性研究进展。</mark>

The modular architecture of Agent Laboratory ensures computational flexibility. The aim is to enhance research productivity by automating tasks while maintaining the human researcher.

<mark>Agent Laboratory 的模块化架构确保了计算灵活性。其目标是通过自动化任务来提高研究生产力，同时保持人类研究人员的参与。</mark>

**Code analysis:** While a comprehensive code analysis is beyond the scope of this book, I want to provide you with some key insights and encourage you to delve into the code on your own.

<mark><strong>代码分析：</strong>虽然全面的代码分析超出了本书的范围，但我想为你提供一些关键见解，并鼓励你自己深入研究代码。</mark>

**Judgment:** In order to emulate human evaluative processes, the system employs a tripartite agentic judgment mechanism for assessing outputs. This involves the deployment of three distinct autonomous agents, each configured to evaluate the production from a specific perspective, thereby collectively mimicking the nuanced and multi-faceted nature of human judgment. This approach allows for a more robust and comprehensive appraisal, moving beyond singular metrics to capture a richer qualitative assessment.

<mark><strong>评判：</strong>为了模拟人类评估过程，该系统采用三方智能体判断机制来评估输出。这涉及部署三个不同的自主智能体，每个智能体都配置为从特定角度评估生产，从而共同模拟人类判断的细微和多方面性质。这种方法允许更强大和全面的评估，超越单一指标以捕获更丰富的定性评估。</mark>

```python
class ReviewersAgent:
    def __init__(self, model="gpt-4o-mini", notes=None, openai_api_key=None):
        if notes is None: self.notes = []
        else: self.notes = notes
        self.model = model
        self.openai_api_key = openai_api_key

    def inference(self, plan, report):
        reviewer_1 = "You are a harsh but fair reviewer and expect good experiments that lead to insights for the research topic."
        review_1 = get_score(outlined_plan=plan, latex=report, reward_model_llm=self.model, reviewer_type=reviewer_1, openai_api_key=self.openai_api_key)

        reviewer_2 = "You are a harsh and critical but fair reviewer who is looking for an idea that would be impactful in the field."
        review_2 = get_score(outlined_plan=plan, latex=report, reward_model_llm=self.model, reviewer_type=reviewer_2, openai_api_key=self.openai_api_key)

        reviewer_3 = "You are a harsh but fair open-minded reviewer that is looking for novel ideas that have not been proposed before."
        review_3 = get_score(outlined_plan=plan, latex=report, reward_model_llm=self.model, reviewer_type=reviewer_3, openai_api_key=self.openai_api_key)

        return f"Reviewer #1:\n{review_1}, \nReviewer #2:\n{review_2}, \nReviewer #3:\n{review_3}"
```

The judgment agents are designed with a specific prompt that closely emulates the cognitive framework and evaluation criteria typically employed by human reviewers. This prompt guides the agents to analyze outputs through a lens similar to how a human expert would, considering factors like relevance, coherence, factual accuracy, and overall quality. By crafting these prompts to mirror human review protocols, the system aims to achieve a level of evaluative sophistication that approaches human-like discernment.

<mark>判断智能体被设计为使用特定的提示词，紧密模拟人类评审者通常采用的认知框架和评估标准。该提示词指导智能体通过类似于人类专家的视角来分析输出，考虑相关性、连贯性、事实准确性和整体质量等因素。通过设计这些提示词以镜像人类评审协议，该系统旨在达到接近人类辨别力的评估复杂程度。</mark>

````python
def get_score(outlined_plan, latex, reward_model_llm, reviewer_type=None, attempts=3, openai_api_key=None):
    e = str()
    for _attempt in range(attempts):
        try:

            template_instructions = """
Respond in the following format:
THOUGHT:
<THOUGHT>
REVIEW JSON:
```json
<JSON>
```
In <THOUGHT>, first briefly discuss your intuitions
and reasoning for the evaluation.
Detail your high-level arguments, necessary choices
and desired outcomes of the review.
Do not make generic comments here, but be specific
to your current paper.
Treat this as the note-taking phase of your review.
In <JSON>, provide the review in JSON format with
the following fields in the order:
- "Summary": A summary of the paper content and
its contributions.
- "Strengths": A list of strengths of the paper.
- "Weaknesses": A list of weaknesses of the paper.
- "Originality": A rating from 1 to 4
(low, medium, high, very high).
- "Quality": A rating from 1 to 4
(low, medium, high, very high).
- "Clarity": A rating from 1 to 4
(low, medium, high, very high).
- "Significance": A rating from 1 to 4
(low, medium, high, very high).
- "Questions": A set of clarifying questions to be
answered by the paper authors.
- "Limitations": A set of limitations and potential
negative societal impacts of the work.
- "Ethical Concerns": A boolean value indicating
whether there are ethical concerns.
- "Soundness": A rating from 1 to 4
(poor, fair, good, excellent).
- "Presentation": A rating from 1 to 4
(poor, fair, good, excellent).
- "Contribution": A rating from 1 to 4
(poor, fair, good, excellent).
- "Overall": A rating from 1 to 10
(very strong reject to award quality).
- "Confidence": A rating from 1 to 5
(low, medium, high, very high, absolute).
- "Decision": A decision that has to be one of the
following: Accept, Reject.
For the "Decision" field, don't use Weak Accept,
Borderline Accept, Borderline Reject, or Strong Reject.
Instead, only use Accept or Reject.
This JSON will be automatically parsed, so ensure
the format is precise.
"""
````

In this multi-agent system, the research process is structured around specialized roles, mirroring a typical academic hierarchy to streamline workflow and optimize output.

<mark>在这个多智能体系统中，研究过程围绕专门角色进行结构化，反映典型的学术层级结构，以简化工作流程并优化输出。</mark>

**Professor Agent:** The Professor Agent functions as the primary research director, responsible for establishing the research agenda, defining research questions, and delegating tasks to other agents. This agent sets the strategic direction and ensures alignment with project objectives.

<mark><strong>教授智能体：</strong>教授智能体作为主要研究主管，负责建立研究议程、定义研究问题并将任务委派给其他智能体。该智能体设定战略方向并确保与项目目标保持一致。</mark>

```python
class ProfessorAgent(BaseAgent):
    def __init__(self, model="gpt4omini", notes=None, max_steps=100, openai_api_key=None):
        super().__init__(model, notes, max_steps, openai_api_key)
        self.phases = ["report writing"]

    def generate_readme(self):
        sys_prompt = f"""You are {self.role_description()} \n Here is the written paper \n{self.report}. Task instructions: Your goal is to integrate all of the knowledge, code, reports, and notes provided to you and generate a readme.md for a github repository."""
        history_str = "\n".join([_[1] for _ in self.history])
        prompt = (
            f"""History: {history_str}\n{'~' * 10}\n"""
            f"Please produce the readme below in markdown:\n")
        model_resp = query_model(model_str=self.model, system_prompt=sys_prompt, prompt=prompt, openai_api_key=self.openai_api_key)
        return model_resp.replace("```markdown", "")
```

**PostDoc Agent:** The PostDoc Agent's role is to execute the research. This includes conducting literature reviews, designing and implementing experiments, and generating research outputs such as papers. Importantly, the PostDoc Agent has the capability to write and execute code, enabling the practical implementation of experimental protocols and data analysis. This agent is the primary producer of research artifacts.

<mark><strong>博士后智能体：</strong>博士后智能体的角色是执行研究。这包括进行文献综述、设计和实施实验以及生成研究成果（如论文）。重要的是，博士后智能体具有编写和执行代码的能力，能够实际实施实验协议和数据分析。该智能体是研究成果的主要生产者。</mark>

```python
class PostdocAgent(BaseAgent):
    def __init__(self, model="gpt4omini", notes=None, max_steps=100, openai_api_key=None):
        super().__init__(model, notes, max_steps, openai_api_key)
        self.phases = ["plan formulation", "results interpretation"]

    def context(self, phase):
        sr_str = str()
        if self.second_round:
            sr_str = (
                f"The following are results from the previous experiments\n",
                f"Previous Experiment code: {self.prev_results_code}\n"
                f"Previous Results: {self.prev_exp_results}\n"
                f"Previous Interpretation of results: {self.prev_interpretation}\n"
                f"Previous Report: {self.prev_report}\n"
                f"{self.reviewer_response}\n\n\n"
            )
        if phase == "plan formulation":
            return (
                sr_str,
                f"Current Literature Review: {self.lit_review_sum}",
            )
        elif phase == "results interpretation":
            return (
                sr_str,
                f"Current Literature Review: {self.lit_review_sum}\n"
                f"Current Plan: {self.plan}\n"
                f"Current Dataset code: {self.dataset_code}\n"
                f"Current Experiment code: {self.results_code}\n"
                f"Current Results: {self.exp_results}"
            )
        return ""
```

**Reviewer Agents:** Reviewer agents perform critical evaluations of research outputs from the PostDoc Agent, assessing the quality, validity, and scientific rigor of papers and experimental results. This evaluation phase emulates the peer-review process in academic settings to ensure a high standard of research output before finalization.

<mark><strong>评审智能体：</strong>评审智能体对博士后智能体的研究成果进行批判性评估，评估论文和实验结果的质量、有效性和科学严谨性。该评估阶段模拟学术环境中的同行评审过程，以确保在最终确定之前研究成果达到高标准。</mark>

**ML Engineering Agents:** The Machine Learning Engineering Agents serve as machine learning engineers, engaging in dialogic collaboration with a PhD student to develop code. Their central function is to generate uncomplicated code for data preprocessing, integrating insights derived from the provided literature review and experimental protocol. This guarantees that the data is appropriately formatted and prepared for the designated experiment.

<mark><strong>机器学习工程智能体：</strong>机器学习工程智能体充当机器学习工程师，与博士生进行对话式协作以开发代码。它们的核心功能是生成简单的数据预处理代码，整合从提供的文献综述和实验协议中得出的见解。这确保数据格式正确并为指定实验做好准备。</mark>

```python
"You are a machine learning engineer being directed by a PhD student who will help you write the code, and you can interact with them through dialogue.\n"
"Your goal is to produce code that prepares the data for the provided experiment. You should aim for simple code to prepare the data, not complex code. You should integrate the provided literature review and the plan and come up with code to prepare data for this experiment.\n"
```

**SWEngineerAgents:** Software Engineering Agents guide Machine Learning Engineer Agents. Their main purpose is to assist the Machine Learning Engineer Agent in creating straightforward data preparation code for a specific experiment. The Software Engineer Agent integrates the provided literature review and experimental plan, ensuring the generated code is uncomplicated and directly relevant to the research objectives.

<mark><strong>软件工程智能体：</strong>软件工程智能体指导机器学习工程智能体。它们的主要目的是协助机器学习工程智能体为特定实验创建简单的数据准备代码。软件工程智能体整合提供的文献综述和实验计划，确保生成的代码简单明了并直接与研究目标相关。</mark>

```python
"You are a software engineer directing a machine learning engineer, where the machine learning engineer will be writing the code, and you can interact with them through dialogue.\n"
"Your goal is to help the ML engineer produce code that prepares the data for the provided experiment. You should aim for very simple code to prepare the data, not complex code. You should integrate the provided literature review and the plan and come up with code to prepare data for this experiment.\n"
```

In summary, "Agent Laboratory" represents a sophisticated framework for autonomous scientific research. It is designed to augment human research capabilities by automating key research stages and facilitating collaborative AI-driven knowledge generation. The system aims to increase research efficiency by managing routine tasks while maintaining human oversight.

<mark>总而言之，「Agent Laboratory」代表了一个复杂的自主科学研究框架。它旨在通过自动化关键研究阶段和促进协作式 AI 驱动的知识生成来增强人类研究能力。该系统旨在通过管理日常任务来提高研究效率，同时保持人类监督。</mark>

---

## At a Glance | <mark>要点速览</mark>

**What:** AI agents often operate within predefined knowledge, limiting their ability to tackle novel situations or open-ended problems. In complex and dynamic environments, this static, pre-programmed information is insufficient for true innovation or discovery. The fundamental challenge is to enable agents to move beyond simple optimization to actively seek out new information and identify "unknown unknowns." This necessitates a paradigm shift from purely reactive behaviors to proactive, Agentic exploration that expands the system's own understanding and capabilities.

<mark><strong>问题所在：</strong>AI 智能体通常在预定义的知识范围内运行，限制了它们处理新情况或开放式问题的能力。在复杂和动态的环境中，这种静态的、预编程的信息不足以实现真正的创新或发现。根本挑战是使智能体超越简单的优化，主动寻找新信息并识别「未知之未知」。这需要从纯粹的反应式行为转变为主动的智能体探索，以扩展系统自身的理解和能力。</mark>

**Why:** The standardized solution is to build Agentic AI systems specifically designed for autonomous exploration and discovery. These systems often utilize a multi-agent framework where specialized LLMs collaborate to emulate processes like the scientific method. For instance, distinct agents can be tasked with generating hypotheses, critically reviewing them, and evolving the most promising concepts. This structured, collaborative methodology allows the system to intelligently navigate vast information landscapes, design and execute experiments, and generate genuinely new knowledge. By automating the labor-intensive aspects of exploration, these systems augment human intellect and significantly accelerate the pace of discovery.

<mark><strong>解决之道：</strong>标准化解决方案是构建专门设计用于自主探索和发现的智能体 AI 系统。这些系统通常利用多智能体框架，其中专门的大语言模型协作以模拟科学方法等过程。例如，可以为不同的智能体分配生成假设、批判性审查假设和演化最有前景的概念等任务。这种结构化的协作方法使系统能够智能地导航广阔的信息景观、设计和执行实验，并生成真正的新知识。通过自动化探索的劳动密集型方面，这些系统增强了人类智力并显著加快了发现的步伐。</mark>

**Rule of thumb:** Use the Exploration and Discovery pattern when operating in open-ended, complex, or rapidly evolving domains where the solution space is not fully defined. It is ideal for tasks requiring the generation of novel hypotheses, strategies, or insights, such as in scientific research, market analysis, and creative content generation. This pattern is essential when the objective is to uncover "unknown unknowns" rather than merely optimizing a known process.

<mark><strong>经验法则：</strong>在解决方案空间未完全定义的开放式、复杂或快速演变的领域中使用探索与发现模式。它非常适合需要生成新假设、策略或见解的任务，例如科学研究、市场分析和创意内容生成。当目标是发现「未知之未知」而不仅仅是优化已知过程时，这种模式至关重要。</mark>

**Visual summary:**

<mark><strong>可视化总结：</strong></mark>

![Exploration and Discovery design pattern](/images/chapter21_fig2.png)

Fig.2: Exploration and Discovery design pattern

<mark>图 2：探索与发现设计模式</mark>

---

## Key Takeaways | <mark>核心要点</mark>

- Exploration and Discovery in AI enable agents to actively pursue new information and possibilities, which is essential for navigating complex and evolving environments.

  <mark>AI 中的探索与发现使智能体能够主动追求新信息和新可能性，这对于在复杂和不断演变的环境中导航至关重要。</mark>

- Systems such as Google Co-Scientist demonstrate how Agents can autonomously generate hypotheses and design experiments, supplementing human scientific research.

  <mark>Google 协作科学家等系统展示了智能体如何自主生成假设和设计实验，补充人类科学研究。</mark>

- The multi-agent framework, exemplified by Agent Laboratory's specialized roles, improves research through the automation of literature review, experimentation, and report writing.

  <mark>以 Agent Laboratory 的专门角色为例的多智能体框架通过自动化文献综述、实验和报告撰写来改进研究。</mark>

- Ultimately, these Agents aim to enhance human creativity and problem-solving by managing computationally intensive tasks, thus accelerating innovation and discovery.

  <mark>最终，这些智能体旨在通过管理计算密集型任务来增强人类创造力和解决问题的能力，从而加速创新和发现。</mark>

---

## Conclusion | <mark>结语</mark>

In conclusion, the Exploration and Discovery pattern is the very essence of a truly agentic system, defining its ability to move beyond passive instruction-following to proactively explore its environment. This innate agentic drive is what empowers an AI to operate autonomously in complex domains, not merely executing tasks but independently setting sub-goals to uncover novel information. This advanced agentic behavior is most powerfully realized through multi-agent frameworks where each agent embodies a specific, proactive role in a larger collaborative process. For instance, the highly agentic system of Google's Co-scientist features agents that autonomously generate, debate, and evolve scientific hypotheses.

<mark>总之，探索与发现模式是真正智能体系统的本质，定义了其超越被动遵循指令而主动探索环境的能力。这种固有的智能体驱动力使 AI 能够在复杂领域中自主运行，不仅执行任务，而且独立设定子目标以发现新信息。这种高级智能体行为通过多智能体框架最有力地实现，其中每个智能体在更大的协作过程中体现特定的主动角色。例如，Google 协作科学家的高度智能体系统具有自主生成、辩论和演化科学假设的智能体。</mark>

Frameworks like Agent Laboratory further structure this by creating an agentic hierarchy that mimics human research teams, enabling the system to self-manage the entire discovery lifecycle. The core of this pattern lies in orchestrating emergent agentic behaviors, allowing the system to pursue long-term, open-ended goals with minimal human intervention. This elevates the human-AI partnership, positioning the AI as a genuine agentic collaborator that handles the autonomous execution of exploratory tasks. By delegating this proactive discovery work to an agentic system, human intellect is significantly augmented, accelerating innovation. The development of such powerful agentic capabilities also necessitates a strong commitment to safety and ethical oversight. Ultimately, this pattern provides the blueprint for creating truly agentic AI, transforming computational tools into independent, goal-seeking partners in the pursuit of knowledge.

<mark>像 Agent Laboratory 这样的框架通过创建模仿人类研究团队的智能体层级结构来进一步构建这一点，使系统能够自我管理整个发现生命周期。该模式的核心在于编排涌现的智能体行为，允许系统在最少的人工干预下追求长期的开放式目标。这提升了人机合作伙伴关系，将 AI 定位为真正的智能体协作者，处理探索任务的自主执行。通过将这种主动发现工作委托给智能体系统，人类智力得到显著增强，加速创新。开发如此强大的智能体能力也需要对安全性和道德监督做出坚定承诺。最终，这种模式为创建真正的智能体 AI 提供了蓝图，将计算工具转变为追求知识的独立、目标寻求的合作伙伴。</mark>

---

## References | <mark>参考文献</mark>

1. Exploration-Exploitation Dilemma: A fundamental problem in reinforcement learning and decision-making under uncertainty. <https://en.wikipedia.org/wiki/Exploration%E2%80%93exploitation_dilemma>

   <mark>探索-利用困境：强化学习和不确定性决策中的基本问题。<https://en.wikipedia.org/wiki/Exploration%E2%80%93exploitation_dilemma></mark>

2. Google Co-Scientist: <https://research.google/blog/accelerating-scientific-breakthroughs-with-an-ai-co-scientist/>

   <mark>Google 协作科学家：<https://research.google/blog/accelerating-scientific-breakthroughs-with-an-ai-co-scientist/></mark>

3. Agent Laboratory: Using LLM Agents as Research Assistants <https://github.com/SamuelSchmidgall/AgentLaboratory>

   <mark>Agent Laboratory：使用 LLM 智能体作为研究助手 <https://github.com/SamuelSchmidgall/AgentLaboratory></mark>

4. AgentRxiv: Towards Collaborative Autonomous Research: <https://agentrxiv.github.io/>

   <mark>AgentRxiv：迈向协作式自主研究：<https://agentrxiv.github.io/></mark>
