# Chapter 7: Multi-Agent Collaboration | <mark>第七章：多智能体协作</mark>

While a monolithic agent architecture can be effective for well-defined problems, its capabilities are often constrained when faced with complex, multi-domain tasks. The Multi-Agent Collaboration pattern addresses these limitations by structuring a system as a cooperative ensemble of distinct, specialized agents. This approach is predicated on the principle of task decomposition, where a high-level objective is broken down into discrete sub-problems. Each sub-problem is then assigned to an agent possessing the specific tools, data access, or reasoning capabilities best suited for that task.

<mark>单智能体在处理任务明确、范围清晰的问题时表现良好，但在面对更复杂的跨领域任务时往往力不从心。多智能体协作模式通过组织一组相互合作、各司其职的专长型智能体来克服这些限制。这种模式基于任务分解原则，将高层次目标拆解为若干独立的子问题，然后将每个子问题分配给拥有相应工具、数据权限或推理能力的智能体来处理，以发挥各自优势。</mark>

For example, a complex research query might be decomposed and assigned to a Research Agent for information retrieval, a Data Analysis Agent for statistical processing, and a Synthesis Agent for generating the final report. The efficacy of such a system is not merely due to the division of labor but is critically dependent on the mechanisms for inter-agent communication. This requires a standardized communication protocol and a shared ontology, allowing agents to exchange data, delegate sub-tasks, and coordinate their actions to ensure the final output is coherent.

<mark>例如，一个复杂的研究问题可以这样拆分：由研究智能体负责信息检索、数据分析智能体负责统计处理、综合智能体负责生成最终报告。这类系统的效果不仅源于分工，更取决于智能体之间的通信机制。为此需要标准化的通信协议和共享本体（Ontology），使智能体之间能够交换数据、委派子任务和协调行动，以确保最终结果的连贯一致。</mark>

This distributed architecture offers several advantages, including enhanced modularity, scalability, and robustness, as the failure of a single agent does not necessarily cause a total system failure. The collaboration allows for a synergistic outcome where the collective performance of the multi-agent system surpasses the potential capabilities of any single agent within the ensemble.

<mark>这种分工协作架构具有多项优势，包括更强的模块化、可扩展性和鲁棒性。因为单个智能体的故障不一定会导致整个系统瘫痪。更重要的是，通过分工协作，多智能体系统能够发挥协同效应，其整体表现往往超越任何单个智能体的能力上限。</mark>

---

## Multi-Agent Collaboration Pattern Overview | <mark>多智能体协作模式概览</mark>

The Multi-Agent Collaboration pattern involves designing systems where multiple independent or semi-independent agents work together to achieve a common goal. Each agent typically has a defined role, specific goals aligned with the overall objective, and potentially access to different tools or knowledge bases. The power of this pattern lies in the interaction and synergy between these agents.

<mark>多智能体协作模式是指设计由多个独立或半独立智能体组成的系统，它们之间协同工作以实现共同目标。每个智能体通常承担明确的角色，拥有与整体目标一致的目标，并可以使用不同的工具或知识库。其强大之处在于智能体之间的互动与协同，能够产生超越单体能力的协同效应。</mark>

Collaboration can take various forms:

<mark>协作可以有多种形式：</mark>

- **Sequential Handoffs:** One agent completes a task and passes its output to another agent for the next step in a pipeline (similar to the Planning pattern, but explicitly involving different agents).

   <mark><strong>顺序交接：</strong> 一个智能体完成任务后将输出交给另一个智能体继续处理，形成管道式工作流（类似于规划模式，但涉及不同的智能体）。</mark>

- **Parallel Processing:** Multiple agents work on different parts of a problem simultaneously, and their results are later combined.

   <mark><strong>并行处理：</strong> 多个智能体同时处理同一问题的不同部分，最后将各自的结果进行合并。</mark>

- **Debate and Consensus:** Multi-Agent Collaboration where Agents with varied perspectives and information sources engage in discussions to evaluate options, ultimately reaching a consensus or a more informed decision.

   <mark><strong>辩论与共识：</strong> 在多智能体协作中，来自不同视角和信息来源的智能体通过讨论和评估各种方案，最终形成共识或得出更加可靠的决策。</mark>

- **Hierarchical Structures:** A manager agent might delegate tasks to worker agents dynamically based on their tool access or plugin capabilities and synthesize their results. Each agent can also handle relevant groups of tools, rather than a single agent handling all the tools.

   <mark><strong>层级结构：</strong> 管理型智能体可以根据各个执行型智能体的工具权限或插件能力，动态分配任务并汇总结果。每个智能体也可以负责一组相关工具，而不是让单个智能体承担所有工具调用的责任。</mark>

- **Expert Teams:** Agents with specialized knowledge in different domains (e.g., a researcher, a writer, an editor) collaborate to produce a complex output.

   <mark><strong>专家团队：</strong> 由研究员、撰稿人、编辑等在各自领域具备专业知识的智能体组成，他们协同合作，共同完成复杂的任务。</mark>

- **Critic-Reviewer:** Agents create initial outputs such as plans, drafts, or answers. A second group of agents then critically assesses this output for adherence to policies, security, compliance, correctness, quality, and alignment with organizational objectives. The original creator or a final agent revises the output based on this feedback. This pattern is particularly effective for code generation, research writing, logic checking, and ensuring ethical alignment. The advantages of this approach include increased robustness, improved quality, and a reduced likelihood of hallucinations or errors.

   <mark><strong>评审者模式：</strong> 一组智能体先生成初始输出（如计划、草稿或答案），另一组智能体随后严格评估该输出是否符合政策、安全性、合规性、正确性、质量要求以及组织目标。原始输出的智能体或最终智能体再据此反馈来改进输出。这种模式对于代码生成、学术写作、逻辑检查以及确保伦理合规方面尤其有效，其优势包括更强的稳定性、更高的质量，以及显著减少幻觉和其他错误的可能性。</mark>

A multi-agent system (see Fig.1) fundamentally comprises the delineation of agent roles and responsibilities, the establishment of communication channels through which agents exchange information, and the formulation of a task flow or interaction protocol that directs their collaborative endeavors.

<mark>多智能体系统（见图 1）的设计主要包括三个方面：明确每个智能体的角色和职责、建立用于信息交换的通信通道，以及制定引导它们协同工作的任务流程或交互协议。</mark>

![Multi-Agent System Example](/images/chapter07_fig1.png)

Fig.1: Example of multi-agent system

<mark>图 1：多智能体系统示例</mark>

Frameworks such as Crew AI and Google ADK are engineered to facilitate this paradigm by providing structures for the specification of agents, tasks, and their interactive procedures. This approach is particularly effective for challenges necessitating a variety of specialized knowledge, encompassing multiple discrete phases, or leveraging the advantages of concurrent processing and the corroboration of information across agents.

<mark>Crew AI 和 Google ADK 等框架通过提供智能体、任务和交互流程的组件，实现这些协作模式。这种方法对于那些需要多种专业知识、包含多个独立阶段，或者能从不同智能体间相互验证信息中受益的场景特别有效。</mark>

---

## Practical Applications & Use Cases | <mark>实际应用场景</mark>

Multi-Agent Collaboration is a powerful pattern applicable across numerous domains:

<mark>多智能体协作是一种强大且通用的模式，适用于许多不同的领域：</mark>

- **Complex Research and Analysis:** A team of agents could collaborate on a research project. One agent might specialize in searching academic databases, another in summarizing findings, a third in identifying trends, and a fourth in synthesizing the information into a report. This mirrors how a human research team might operate.

   <mark><strong>复杂研究与分析：</strong> 多个智能体可以协同完成一个研究项目，采用和人类研究团队类似的分工形式。比如一个智能体负责搜索学术数据库，另一个负责整理和总结要点，第三个负责发现和归纳趋势，第四个将这些信息整合成最终报告。</mark>

- **Software Development:** Imagine agents collaborating on building software. One agent could be a requirements analyst, another a code generator, a third a tester, and a fourth a documentation writer. They could pass outputs between each other to build and verify components.

   <mark><strong>软件开发：</strong> 设想由多个专职智能体协同开发软件的场景。需求分析智能体负责需求分析，开发智能体负责编写代码，测试智能体负责测试，文档智能体负责编写文档。它们的输出可以相互可见，协同开发和验证各个组件。</mark>

- **Creative Content Generation:** Creating a marketing campaign could involve a market research agent, a copywriter agent, a graphic design agent (using image generation tools), and a social media scheduling agent, all working together.

   <mark><strong>创意内容生成：</strong> 在策划一项营销活动时，可以由多个专长不同的智能体共同配合，比如负责市场调研的智能体、负责撰写文案的智能体、负责设计素材的智能体（使用图像生成工具），以及负责社媒排期的智能体，它们协同工作完成整个活动。</mark>

- **Financial Analysis:** A multi-agent system could analyze financial markets. Agents might specialize in fetching stock data, analyzing news sentiment, performing technical analysis, and generating investment recommendations.

   <mark><strong>财务分析：</strong> 多智能体系统还可以用于分析金融市场，不同的智能体分别负责获取股票数据、分析新闻情绪、分析技术面以及生成投资建议。</mark>

- **Customer Support Escalation:** A front-line support agent could handle initial queries, escalating complex issues to a specialist agent (e.g., a technical expert or a billing specialist) when needed, demonstrating a sequential handoff based on problem complexity.

   <mark><strong>客户支持：</strong> 一线客户支持智能体可以处理用户的常见咨询，在遇到复杂或专业性强的问题时，会按问题复杂度将工单升级给相应的专业智能体（如技术专家智能体或计费专家智能体）。</mark>

- **Supply Chain Optimization:** Agents could represent different nodes in a supply chain (suppliers, manufacturers, distributors) and collaborate to optimize inventory levels, logistics, and scheduling in response to changing demand or disruptions.

   <mark><strong>供应链优化：</strong> 智能体可以代表供应链中的不同节点（如供应商、制造商、分销商），通过协作来优化库存、物流和排期，以应对不断变化的需求或其他突发的情况。</mark>

- **Network Analysis & Remediation:** Autonomous operations benefit greatly from an agentic architecture, particularly in failure pinpointing. Multiple agents can collaborate to triage and remediate issues, suggesting optimal actions. These agents can also integrate with traditional machine learning models and tooling, leveraging existing systems while simultaneously offering the advantages of Generative AI.

   <mark><strong>网络分析与故障修复：</strong> 在自主运维系统中，采用多智能体架构对故障定位和问题处理也特别有用。多个专职智能体可以协同进行问题排查与修复，并提出最优处理建议。它们还可以与现有的机器学习模型和运维工具无缝集成，既利用现有系统，又能发挥生成式 AI 带来的额外价值。</mark>

The capacity to delineate specialized agents and meticulously orchestrate their interrelationships empowers developers to construct systems exhibiting enhanced modularity, scalability, and the ability to address complexities that would prove insurmountable for a singular, integrated agent.

<mark>将任务拆分给多个专业智能体并精心编排它们的协作，可以让开发者构建出更具模块化和可扩展性的系统，从而解决单个整体智能体无法应对的复杂问题。这正是多智能体协作模式的核心价值所在。</mark>

---

## Multi-Agent Collaboration: Exploring Interrelationships and Communication Structures | <mark>多智能体协作：研究各智能体之间的关系与通信体系</mark>

Understanding the intricate ways in which agents interact and communicate is fundamental to designing effective multi-agent systems. As depicted in Fig. 2, a spectrum of interrelationship and communication models exists, ranging from the simplest single-agent scenario to complex, custom-designed collaborative frameworks. Each model presents unique advantages and challenges, influencing the overall efficiency, robustness, and adaptability of the multi-agent system.

<mark>理解智能体之间如何交互和通信是设计高效多智能体系统的基础。如图 2 所示，智能体间的互联关系和通信模型形成一个谱系，从最简单的单智能体场景到复杂的定制协作框架。每种模型各有优劣，会影响多智能体系统的整体效率、稳定性和灵活性。</mark>

### 1. Single Agent | <mark>单智能体</mark>

At the most basic level, a "Single Agent" operates autonomously without direct interaction or communication with other entities. While this model is straightforward to implement and manage, its capabilities are inherently limited by the individual agent's scope and resources. It is suitable for tasks that are decomposable into independent sub-problems, each solvable by a single, self-sufficient agent.

<mark>在最基本的层面上，「单智能体」独立运行，不需要与其他智能体进行直接交互或通信。虽然这种模型易于实现和管理，但其能力本质上受限于单个智能体的职责和资源。它适合那些能被分解为独立子问题的场景，其中每个子问题都可以交给单个自给自足的智能体来解决。</mark>

### 2. Network | <mark>网络化</mark>

The "Network" model represents a significant step towards collaboration, where multiple agents interact directly with each other in a decentralized fashion. Communication typically occurs peer-to-peer, allowing for the sharing of information, resources, and even tasks. This model fosters resilience, as the failure of one agent does not necessarily cripple the entire system. However, managing communication overhead and ensuring coherent decision-making in a large, unstructured network can be challenging.

<mark>「网络」模型向协作迈出了重要一步，多个智能体以去中心化、点对点的方式直接交互，能够共享信息、资源乃至分担任务。这种模型结构更具弹性，因为某个智能体的故障不一定会影响整个系统。然而，在大规模、非结构化的网络中，如何控制通信开销并确保决策的一致性仍然是个挑战。</mark>

### 3. Supervisor | <mark>监督者</mark>

In the "Supervisor" model, a dedicated agent, the "supervisor," oversees and coordinates the activities of a group of subordinate agents. The supervisor acts as a central hub for communication, task allocation, and conflict resolution. This hierarchical structure offers clear lines of authority and can simplify management and control. However, it introduces a single point of failure (the supervisor) and can become a bottleneck if the supervisor is overwhelmed by a large number of subordinates or complex tasks.

<mark>在「监督者」模型中，专门的「监督者」智能体负责监督和协调下级智能体的工作。监督者充当通信、任务分配和冲突解决的中心枢纽，能带来清晰的职责分工并简化管理和控制。然而，这种层级结构也会带来单点故障问题（即监督者本身），而且当下级智能体数量过多或任务非常复杂时，监督者可能成为整体系统的瓶颈。</mark>

### 4. Supervisor as a Tool | <mark>将监督者视为工具</mark>

This model is a nuanced extension of the "Supervisor" concept, where the supervisor's role is less about direct command and control and more about providing resources, guidance, or analytical support to other agents. The supervisor might offer tools, data, or computational services that enable other agents to perform their tasks more effectively, without necessarily dictating their every action. This approach aims to leverage the supervisor's capabilities without imposing rigid top-down control.

<mark>这种模型是「监督者」概念的细微扩展，监督者的角色不再直接指挥和控制，而是通过提供资源、指导或分析来辅助其他智能体。监督者可能提供工具、数据或计算服务，帮助其他智能体更高效地完成任务，而不是干预或支配它们的每一步行动。此方法旨在发挥监督者的能力，同时避免僵化的自上而下的控制。</mark>

### 5. Hierarchical | <mark>层级</mark>

The "Hierarchical" model expands upon the supervisor concept to create a multi-layered organizational structure. This involves multiple levels of supervisors, with higher-level supervisors overseeing lower-level ones, and ultimately, a collection of operational agents at the lowest tier. This structure is well-suited for complex problems that can be decomposed into sub-problems, each managed by a specific layer of the hierarchy. It provides a structured approach to scalability and complexity management, allowing for distributed decision-making within defined boundaries.

<mark>「层级」模型基于监督者概念创建了一个多层组织结构：高层级的监督者负责监督低层级监督者，最底层则由具体的执行智能体组成。该架构非常适合于可以拆分为若干子问题的复杂任务，每一层负责管理特定的子问题。通过这种分层管理，它为应对复杂性和实现可扩展性提供了清晰的结构，并允许在既定边界内进行分工决策。</mark>

![Agent Communication Models](/images/chapter07_fig2.png)

Fig. 2: Agents communicate and interact in various ways.

<mark>图 2：智能体以各种方式进行通信和交互。</mark>

### 6. Custom | <mark>自定义</mark>

The "Custom" model represents the ultimate flexibility in multi-agent system design. It allows for the creation of unique interrelationship and communication structures tailored precisely to the specific requirements of a given problem or application. This can involve hybrid approaches that combine elements from the previously mentioned models, or entirely novel designs that emerge from the unique constraints and opportunities of the environment. Custom models often arise from the need to optimize for specific performance metrics, handle highly dynamic environments, or incorporate domain-specific knowledge into the system's architecture. Designing and implementing custom models typically requires a deep understanding of multi-agent systems principles and careful consideration of communication protocols, coordination mechanisms, and emergent behaviors.

<mark>「自定义」模型代表了多智能体系统设计的终极灵活性，允许为特定问题或应用精确定制相互关系和通信结构。它既可以是融合了已有模型特点的混合方案，也可以是针对独特环境约束和机会时产生的全新设计。自定义模型通常用于优化特定性能指标、处理高度动态环境或将领域特定知识纳入系统架构的场景。设计与实现这类模型通常要求对多智能体系统原理有深入理解，并需慎重规划通信协议、协调机制及可能出现的涌现行为。</mark>

In summary, the choice of interrelationship and communication model for a multi-agent system is a critical design decision. Each model offers distinct advantages and disadvantages, and the optimal choice depends on factors such as the complexity of the task, the number of agents, the desired level of autonomy, the need for robustness, and the acceptable communication overhead. Future advancements in multi-agent systems will likely continue to explore and refine these models, as well as develop new paradigms for collaborative intelligence.

<mark>总之，为多智能体系统选定相互关系与通信模型是一个关键的设计决策。各种模型各有优劣，哪种最合适取决于任务复杂度、智能体数量、所需自治程度、对系统鲁棒性的要求以及可接受的通信开销。未来，多智能体系统领域可能会继续改进这些模型，并探索新的协作智能范式。</mark>

---

## Hands-On code (Crew AI) | <mark>实战代码：使用 CrewAI</mark>

This Python code defines an AI-powered crew using the CrewAI framework to generate a blog post about AI trends. It starts by setting up the environment, loading API keys from a .env file. The core of the application involves defining two agents: a researcher to find and summarize AI trends, and a writer to create a blog post based on the research.

<mark>以下 Python 代码演示了如何使用 CrewAI 框架创建一个 AI 赋能的「创作团队」，来撰写一篇关于 AI 趋势的博客。程序首先配置环境，从 <code>.env</code> 文件中加载 API 密钥。核心部分定义了两个智能体：研究员智能体负责查找和总结 AI 趋势，写手智能体负责编写博客文章。</mark>

Two tasks are defined accordingly: one for researching the trends and another for writing the blog post, with the writing task depending on the output of the research task. These agents and tasks are then assembled into a Crew, specifying a sequential process where tasks are executed in order. The Crew is initialized with the agents, tasks, and a language model (specifically the "gemini-2.0-flash" model). The main function executes this crew using the kickoff() method, orchestrating the collaboration between the agents to produce the desired output. Finally, the code prints the final result of the crew's execution, which is the generated blog post.

<mark>根据上述要求定义了两个任务：调研趋势任务和撰写博客任务，其中写作任务依赖于调研任务的输出。然后将这些智能体和任务组装成 <code>Crew</code> 实例，并按顺序执行任务。主函数使用 <code>kickoff()</code> 方法启动此 <code>Crew</code> 实例，编排智能体之间的协作以产出目标结果。最后程序会在控制台打印执行的结果，即生成的博客文章。</mark>

```python
import os
from dotenv import load_dotenv
from crewai import Agent, Task, Crew, Process
from langchain_google_genai import ChatGoogleGenerativeAI

def setup_environment():
   """
   Loads environment variables and checks for the required API key.
   加载环境变量并检查所需的 API 密钥
   """
   load_dotenv()
   if not os.getenv("GOOGLE_API_KEY"):
       raise ValueError("GOOGLE_API_KEY not found. Please set it in your .env file.")

def main():
   """
   Initializes and runs the AI crew for content creation using the latest Gemini model.
   使用 Gemini 2.0 Flash 模型初始化并运行用于内容创建的 AI 智能体「创作团队」
   """
   setup_environment()

   # Define the language model to use.
   # Updated to a model from the Gemini 2.0 series for better performance and features.
   # For cutting-edge (preview) capabilities, you could use "gemini-2.5-flash".
   # 定义要使用的语言模型
   # 更新为 Gemini 2.0 系列的模型以获得更好的性能和功能
   # 如需最新的特性，可以使用 "gemini-2.5-flash" 模型
   llm = ChatGoogleGenerativeAI(model="gemini-2.0-flash")

   # Define Agents with specific roles and goals
   # 定义具体的角色和目标的智能体
   researcher = Agent(
       role='Senior Research Analyst',
       goal='Find and summarize the latest trends in AI.',
       backstory="You are an experienced research analyst with a knack for identifying key trends and synthesizing information.",
       verbose=True,
       allow_delegation=False,
   )

   writer = Agent(
       role='Technical Content Writer',
       goal='Write a clear and engaging blog post based on research findings.',
       backstory="You are a skilled writer who can translate complex technical topics into accessible content.",
       verbose=True,
       allow_delegation=False,
   )

   # Define Tasks for the agents
   # 为智能体定义任务
   research_task = Task(
       description="Research the top 3 emerging trends in Artificial Intelligence in 2024-2025. Focus on practical applications and potential impact.",
       expected_output="A detailed summary of the top 3 AI trends, including key points and sources.",
       agent=researcher,
   )

   writing_task = Task(
       description="Write a 500-word blog post based on the research findings. The post should be engaging and easy for a general audience to understand.",
       expected_output="A complete 500-word blog post about the latest AI trends.",
       agent=writer,
       context=[research_task],
   )

   # Create the Crew
   # 创建 Crew 实例
   blog_creation_crew = Crew(
       agents=[researcher, writer],
       tasks=[research_task, writing_task],
       process=Process.sequential,
       llm=llm,
       # verbose=2 # Set verbosity for detailed crew execution logs
       verbose=True  # 译者注：CrewAI 的 Crew 类在最新版本中，verbose 参数只接受布尔值（True 或 False），不再支持整数级别（0, 1, 2）
   )

   # Execute the Crew
   # 启动 Crew 实例
   print("## Running the blog creation crew with Gemini 2.0 Flash... ##")
   try:
       result = blog_creation_crew.kickoff()
       print("\n------------------\n")
       print("## Crew Final Output ##")
       print(result)
   except Exception as e:
       print(f"\nAn unexpected error occurred: {e}")


if __name__ == "__main__":
   main()
```

We will now delve into further examples within the Google ADK framework, with particular emphasis on hierarchical, parallel, and sequential coordination paradigms, alongside the implementation of an agent as an operational instrument.

<mark>接下来，我们将深入探讨 Google ADK 框架内的更多示例，重点介绍层级、并行和顺序三种协调模式，并演示如何将智能体作为一个工具来使用。</mark>

---

## Hands-on Code (Google ADK) | <mark>实战代码：使用 Google ADK</mark>

The following code example demonstrates the establishment of a hierarchical agent structure within the Google ADK through the creation of a parent-child relationship. The code defines two types of agents: LlmAgent and a custom TaskExecutor agent derived from BaseAgent. The TaskExecutor is designed for specific, non-LLM tasks and in this example, it simply yields a "Task finished successfully" event. An LlmAgent named greeter is initialized with a specified model and instruction to act as a friendly greeter. The custom TaskExecutor is instantiated as task_doer. A parent LlmAgent called coordinator is created, also with a model and instructions. The coordinator's instructions guide it to delegate greetings to the greeter and task execution to the task_doer. The greeter and task_doer are added as sub-agents to the coordinator, establishing a parent-child relationship. The code then asserts that this relationship is correctly set up. Finally, it prints a message indicating that the agent hierarchy has been successfully created.

<mark>以下代码演示了如何在 Google ADK 中通过创建父子智能体关系来建立多层级结构。</mark>

<mark>代码中采用了两种方式来定义智能体：<code>LlmAgent</code> 和继承自 <code>BaseAgent</code> 的自定义 <code>TaskExecutor</code>。<code>TaskExecutor</code> 用于处理非大语言模型任务，在这个示例中，它只是发出「任务成功完成」事件。</mark>

<mark>另外一个名为 <code>greeter</code> 的 <code>LlmAgent</code> 智能体使用大语言模型（这里使用 <code>gemini-2.0-flash-exp</code> 模型）并被要求扮演迎宾人员。接着使用自定义的 <code>TaskExecutor</code> 来实例化 <code>task_doer</code>。</mark>

<mark>随后创建名为 <code>coordinator</code> 的父智能体，同样指定了模型与指令，要求它将问候任务分派给 <code>greeter</code>，将具体的任务执行分派给 <code>task_doer</code>。这样就通过把 <code>greeter</code> 和 <code>task_doer</code> 作为 <code>coordinator</code> 的子智能体，建立了父子关系。代码接着断言此关系已正确设置，并打印消息表示智能体层级关系已成功创建。</mark>

```python
from google.adk.agents import LlmAgent, BaseAgent
from google.adk.agents.invocation_context import InvocationContext
from google.adk.events import Event
from typing import AsyncGenerator

# Correctly implement a custom agent by extending BaseAgent
# 通过继承 BaseAgent 类实现自定义智能体
class TaskExecutor(BaseAgent):
   """
   A specialized agent with custom, non-LLM behavior.
   一个自定义的非基于大语言模型的智能体
   """
   name: str = "TaskExecutor"
   description: str = "Executes a predefined task."

   async def _run_async_impl(self, context: InvocationContext) -> AsyncGenerator[Event, None]:
       """
       Custom implementation logic for the task.
       自定义任务的实现逻辑
       """
       # This is where your custom logic would go.
       # For this example, we'll just yield a simple event.
       # 这里是自定义逻辑所在
       # 在这个示例中，我们只是返回一个简单的事件
       yield Event(author=self.name, content="Task finished successfully.")

# Define individual agents with proper initialization
# LlmAgent requires a model to be specified.
# 定义具有明确功能的智能体
# LlmAgent 需要指定使用的模型
greeter = LlmAgent(
   name="Greeter",
   model="gemini-2.0-flash-exp",
   instruction="You are a friendly greeter."
)

# Instantiate our concrete custom agent
# 实例化自定义智能体
task_doer = TaskExecutor() 

# Create a parent agent and assign its sub-agents
# The parent agent's description and instructions should guide its delegation logic.
# 创建一个父智能体并声明其子智能体列表
# 父智能体的描述和指令应该能够指导其委派子智能体的逻辑
coordinator = LlmAgent(
   name="Coordinator",
   model="gemini-2.0-flash-exp",
   description="A coordinator that can greet users and execute tasks.",
   instruction="When asked to greet, delegate to the Greeter. When asked to perform a task, delegate to the TaskExecutor.",
   sub_agents=[
       greeter,
       task_doer
   ]
)

# The ADK framework automatically establishes the parent-child relationships.
# These assertions will pass if checked after initialization.
# ADK 框架会自动建立上述层级关系
# 如果在初始化后检查，这些断言将成立
assert greeter.parent_agent == coordinator
assert task_doer.parent_agent == coordinator

print("Agent hierarchy created successfully.")
```

This code excerpt illustrates the employment of the LoopAgent within the Google ADK framework to establish iterative workflows. The code defines two agents: ConditionChecker and ProcessingStep. ConditionChecker is a custom agent that checks a "status" value in the session state. If the "status" is "completed", ConditionChecker escalates an event to stop the loop. Otherwise, it yields an event to continue the loop. ProcessingStep is an LlmAgent using the "gemini-2.0-flash-exp" model. Its instruction is to perform a task and set the session "status" to "completed" if it's the final step. A LoopAgent named StatusPoller is created. StatusPoller is configured with max_iterations=10. StatusPoller includes both ProcessingStep and an instance of ConditionChecker as sub-agents. The LoopAgent will execute the sub-agents sequentially for up to 10 iterations, stopping if ConditionChecker finds the status is "completed".

<mark>下一个示例演示了如何在 Google ADK 框架中使用 <code>LoopAgent</code> 创建迭代工作流。</mark>

<mark>代码定义了两个智能体：<code>ConditionChecker</code> 和 <code>ProcessingStep</code>。<code>ConditionChecker</code> 是自定义智能体，用于检查会话状态中的「status」字段值。如果「status」为「completed」，<code>ConditionChecker</code> 会终止循环；否则，它会发出事件以继续循环。</mark>

<mark><code>ProcessingStep</code> 是使用 <code>gemini-2.0-flash-exp</code> 模型的 <code>LlmAgent</code> 智能体，用来执行具体任务；如果是最后一步，则将会话「status」设置为「completed」。</mark>

<mark>示例中创建了名为 <code>StatusPoller</code> 的 <code>LoopAgent</code>，配置为最多循环 10 次（<code>max_iterations=10</code>），并将 <code>ProcessingStep</code> 和 <code>ConditionChecker</code> 作为子智能体顺序执行。最终效果是 <code>LoopAgent</code> 最多执行 10 次循环，如果 <code>ConditionChecker</code> 检测到状态为「completed」则提前终止循环。</mark>

```python
import asyncio
from typing import AsyncGenerator
from google.adk.agents import LoopAgent, LlmAgent, BaseAgent
from google.adk.events import Event, EventActions
from google.adk.agents.invocation_context import InvocationContext

# Best Practice: Define custom agents as complete, self-describing classes.
# 最佳实践：将自定义智能体定义为完整的、自描述的类
class ConditionChecker(BaseAgent):
   """
   A custom agent that checks for a 'completed' status in the session state.
   一个自定义的智能体，用于检查会话是否为「completed」状态
   """
   name: str = "ConditionChecker"
   description: str = "Checks if a process is complete and signals the loop to stop."

   async def _run_async_impl(
       self, context: InvocationContext
   ) -> AsyncGenerator[Event, None]:
       """
       Checks state and yields an event to either continue or stop the loop.
       检查状态并产生事件以继续或停止循环
       """
       status = context.session.state.get("status", "pending")
       is_done = (status == "completed")

       if is_done:
           # Escalate to terminate the loop when the condition is met.
           # 满足条件时终止循环
           yield Event(author=self.name, actions=EventActions(escalate=True))
       else:
           # Yield a simple event to continue the loop.
           # 否则，发出简单事件以继续循环
           yield Event(author=self.name, content="Condition not met, continuing loop.")

# Correction: The LlmAgent must have a model and clear instructions.
# 说明：LlmAgent 必须指定使用的模型和清晰的指令
process_step = LlmAgent(
   name="ProcessingStep",
   model="gemini-2.0-flash-exp",
   instruction="You are a step in a longer process. Perform your task. If you are the final step, update session state by setting 'status' to 'completed'."
)

# The LoopAgent orchestrates the workflow.
# 使用 LoopAgent 编排工作流
poller = LoopAgent(
   name="StatusPoller",
   max_iterations=10,
   sub_agents=[
       process_step,
       ConditionChecker() # Instantiating the well-defined custom agent.
   ]
)

# This poller will now execute 'process_step'
# and then 'ConditionChecker'
# repeatedly until the status is 'completed' or 10 iterations
# have passed.
# 此轮询器现在将执行 'process_step' 智能体
# 然后执行 'ConditionChecker' 智能体    
# 重复执行直到状态为 'completed' 或达到 10 次循环
```

This code excerpt elucidates the SequentialAgent pattern within the Google ADK, engineered for the construction of linear workflows. This code defines a sequential agent pipeline using the google.adk.agents library. The pipeline consists of two agents, step1 and step2. step1 is named "Step1_Fetch" and its output will be stored in the session state under the key "data". step2 is named "Step2_Process" and is instructed to analyze the information stored in session.state["data"] and provide a summary. The SequentialAgent named "MyPipeline" orchestrates the execution of these sub-agents. When the pipeline is run with an initial input, step1 will execute first. The response from step1 will be saved into the session state under the key "data". Subsequently, step2 will execute, utilizing the information that step1 placed into the state as per its instruction. This structure allows for building workflows where the output of one agent becomes the input for the next. This is a common pattern in creating multi-step AI or data processing pipelines.

<mark>下面的代码演示了如何通过 Google ADK 中的 <code>SequentialAgent</code> 来构建线性工作流。

<mark>代码首先使用 <code>google.adk.agents</code> 库定义了由两个智能体组成的顺序流水线：<code>step1</code> 和 <code>step2</code>。</mark>

<mark><code>step1</code> 智能体的名称是「Step1_Fetch」，它的输出将存储在会话状态的「data」属性下。<code>step2</code> 智能体的名称是「Step2_Process」，它的作用是分析存储在 <code>session.state["data"]</code> 中的信息并给出摘要。</mark>

<mark>然后创建一个名为「MyPipeline」的 <code>SequentialAgent</code> 来编排这两个子智能体的执行。当使用原始输入传入并开始运行流水线时，<code>step1</code> 会先执行并把结果写入会话状态的「data」属性下，随后 <code>step2</code> 再执行，根据它的指令读取状态中的信息并继续处理。这样的结构便于构建多步流程，使一个智能体的输出作为下一个智能体的输入，是常见的多步骤 AI 或数据处理流水线模式。</mark>

```python
from google.adk.agents import SequentialAgent, Agent

# This agent's output will be saved to session.state["data"]
# 该智能体的输出将保存到 session.state["data"]
step1 = Agent(name="Step1_Fetch", output_key="data")

# This agent will use the data from the previous step.
# We instruct it on how to find and use this data.
# 该智能体会使用上一步的输出
# 通过指令告诉它如何查找和使用上一步的输出
step2 = Agent(
   name="Step2_Process",
   instruction="Analyze the information found in state['data'] and provide a summary."
)

pipeline = SequentialAgent(
   name="MyPipeline",
   sub_agents=[step1, step2]
)

# When the pipeline is run with an initial input, Step1 will execute,
# its response will be stored in session.state["data"], and then
# Step2 will execute, using the information from the state as instructed.
# 当使用原始输入运行 pipeline 时，Step1 先执行，
# 它的响应会保存到 session.state["data"] 中，然后
# Step2 再执行，按照指令使用状态中的信息
```

The following code example illustrates the ParallelAgent pattern within the Google ADK, which facilitates the concurrent execution of multiple agent tasks. The data_gatherer is designed to run two sub-agents concurrently: weather_fetcher and news_fetcher. The weather_fetcher agent is instructed to get the weather for a given location and store the result in session.state["weather_data"]. Similarly, the news_fetcher agent is instructed to retrieve the top news story for a given topic and store it in session.state["news_data"]. Each sub-agent is configured to use the "gemini-2.0-flash-exp" model. The ParallelAgent orchestrates the execution of these sub-agents, allowing them to work in parallel. The results from both weather_fetcher and news_fetcher would be gathered and stored in the session state. Finally, the example shows how to access the collected weather and news data from the final_state after the agent's execution is complete.

<mark>下面的代码示例演示了如何通过 Google ADK 中的 <code>ParallelAgent</code> 来实现多个智能体任务的并行执行。</mark>

<mark><code>data_gatherer</code> 智能体声明需要并行运行两个子智能体：<code>weather_fetcher</code> 和 <code>news_fetcher</code>。</mark>

<mark><code>weather_fetcher</code> 智能体被要求获取给定位置的天气，并将结果保存在会话状态中的 <code>weather_data</code> 属性中；<code>news_fetcher</code> 智能体则被要求搜索给定主题的头条新闻，并将其保存在会话状态中的 <code>news_data</code> 属性中。这两个子智能体都使用 <code>gemini-2.0-flash-exp</code> 模型。</mark>

<mark><code>ParallelAgent</code> 负责编排这些子智能体的并行执行，收集执行结果并存储在会话状态中。最后，示例展示了如何在智能体执行完成后从会话状态中获取收集的天气和新闻数据。</mark>

```python
from google.adk.agents import Agent, ParallelAgent

# It's better to define the fetching logic as tools for the agents
# For simplicity in this example, we'll embed the logic in the agent's instruction.
# In a real-world scenario, you would use tools.
# 在实际场景中最好将查询数据的逻辑定义为智能体的工具
# 为了简单起见，在这个示例中，我们将查询数据的逻辑放在了智能体的指令中

# Define the individual agents that will run in parallel
# 定义两个并行运行的子智能体：weather_fetcher 和 news_fetcher
weather_fetcher = Agent(
   name="weather_fetcher",
   model="gemini-2.0-flash-exp",
   instruction="Fetch the weather for the given location and return only the weather report.",
   output_key="weather_data"  # The result will be stored in session.state["weather_data"]
)

news_fetcher = Agent(
   name="news_fetcher",
   model="gemini-2.0-flash-exp",
   instruction="Fetch the top news story for the given topic and return only that story.",
   output_key="news_data"      # The result will be stored in session.state["news_data"]
)

# Create the ParallelAgent to orchestrate the sub-agents
# 使用 ParallelAgent 编排子智能体并行执行
data_gatherer = ParallelAgent(
   name="data_gatherer",
   sub_agents=[
       weather_fetcher,
       news_fetcher
   ]
)
```

The provided code segment exemplifies the "Agent as a Tool" paradigm within the Google ADK, enabling an agent to utilize the capabilities of another agent in a manner analogous to function invocation. Specifically, the code defines an image generation system using Google's LlmAgent and AgentTool classes. It consists of two agents: a parent artist_agent and a sub-agent image_generator_agent. The generate_image function is a simple tool that simulates image creation, returning mock image data. The image_generator_agent is responsible for using this tool based on a text prompt it receives. The artist_agent's role is to first invent a creative image prompt. It then calls the image_generator_agent through an AgentTool wrapper. The AgentTool acts as a bridge, allowing one agent to use another agent as a tool. When the artist_agent calls the image_tool, the AgentTool invokes the image_generator_agent with the artist's invented prompt. The image_generator_agent then uses the generate_image function with that prompt. Finally, the generated image (or mock data) is returned back up through the agents. This architecture demonstrates a layered agent system where a higher-level agent orchestrates a lower-level, specialized agent to perform a task.

<mark>最后一个示例演示了 Google ADK 中的「智能体作为工具使用」场景，使智能体能够以类似于函数调用的方式利用另一个智能体的能力。</mark>

<mark>代码中使用框架中的 <code>LlmAgent</code> 和 <code>AgentTool</code> 类定义图像生成系统。它由两个智能体组成：父智能体 <code>artist_agent</code> 和子智能体 <code>image_generator_agent</code>。</mark>

<mark><code>generate_image</code> 函数是一个简单的工具，用来模拟图像创建并返回模拟图像数据。<code>image_generator_agent</code> 则负责根据接收到的提示词使用此工具。</mark>

<mark><code>artist_agent</code> 智能体负责先构思出富有创意的图像提示词，然后使用被 <code>AgentTool</code> 封装后的 <code>image_tool</code> 工具来调用 <code>image_generator_agent</code> 智能体。这里 <code>AgentTool</code> 起到桥梁作用，允许一个智能体将另一个智能体用作工具。</mark>

<mark>当 <code>artist_agent</code> 智能体调用 <code>image_tool</code> 工具时，<code>AgentTool</code> 使用 <code>artist_agent</code> 智能体输出的提示词调用 <code>image_generator_agent</code> 智能体。然后 <code>image_generator_agent</code> 智能体使用该提示词调用 <code>generate_image</code> 工具。</mark>

<mark>最后，生成的图像（或模拟数据）通过智能体输出。整个架构展示了分层的智能体体系，上层智能体负责编排，下层专用智能体负责具体执行任务。</mark>

```python
from google.adk.agents import LlmAgent
from google.adk.tools import agent_tool
from google.genai import types

# 1. A simple function tool for the core capability.
# This follows the best practice of separating actions from reasoning.
# 1. 一个简单的函数工具
# 遵循分离操作与推理的最佳实践
def generate_image(prompt: str) -> dict:
   """
   Generates an image based on a textual prompt.
   基于文本提示生成图像

   Args:
       prompt: A detailed description of the image to generate.
       要生成的图像的详细描述
   Returns:
       A dictionary with the status and the generated image bytes.
       包含状态和生成的图像字节的字典
   """

   print(f"TOOL: Generating image for prompt: '{prompt}'")
   # In a real implementation, this would call an image generation API.
   # For this example, we return mock image data.
   # 在实际实现中，这里将调用真实的图像生成 API
   # 但是为了简便起见，在这个示例中，我们仅返回模拟的图像数据
   mock_image_bytes = b"mock_image_data_for_a_cat_wearing_a_hat"
   return {
       "status": "success",
       # The tool returns the raw bytes, the agent will handle the Part creation.
       # 工具返回原始字节，智能体将处理 Part 创建
       "image_bytes": mock_image_bytes,
       "mime_type": "image/png"
   }

# 2. Refactor the ImageGeneratorAgent into an LlmAgent.
# It now correctly uses the input passed to it.
# 2. 将 ImageGeneratorAgent 重构为 LlmAgent
# 它现在能接收并使用传给它的参数了
image_generator_agent = LlmAgent(
   name="ImageGen",
   model="gemini-2.0-flash",
   description="Generates an image based on a detailed text prompt.",
   instruction=(
       "You are an image generation specialist. Your task is to take the user's request "
       "and use the `generate_image` tool to create the image. "
       "The user's entire request should be used as the 'prompt' argument for the tool. "
       "After the tool returns the image bytes, you MUST output the image."
   ),
   tools=[generate_image]
)

# 3. Wrap the corrected agent in an AgentTool.
# The description here is what the parent agent sees.
# 3. 将智能体封装在 AgentTool 中
# 这里的描述对父智能体是可见的
image_tool = agent_tool.AgentTool(
   agent=image_generator_agent,
   description="Use this tool to generate an image. The input should be a descriptive prompt of the desired image."
)

# 4. The parent agent remains unchanged. Its logic was correct.
# 4. 父智能体保持不变。
artist_agent = LlmAgent(
   name="Artist",
   model="gemini-2.0-flash",
   instruction=(
       "You are a creative artist. First, invent a creative and descriptive prompt for an image. "
       "Then, use the `ImageGen` tool to generate the image using your prompt."
   ),
   tools=[image_tool]
)
```

---

## At a Glance | <mark>要点速览</mark>

**What:** Complex problems often exceed the capabilities of a single, monolithic LLM-based agent. A solitary agent may lack the diverse, specialized skills or access to the specific tools needed to address all parts of a multifaceted task. This limitation creates a bottleneck, reducing the system's overall effectiveness and scalability. As a result, tackling sophisticated, multi-domain objectives becomes inefficient and can lead to incomplete or suboptimal outcomes.

<mark><strong>问题所在：</strong> 复杂问题往往超出单个智能体的能力范围，因为单个智能体可能不具备处理复杂任务所需的各种专业技能或特定工具的访问权限。这种限制造成了瓶颈，降低了系统的整体效率和可扩展性。从而导致单个智能体在处理复杂的跨领域任务时变得低效，容易产出不完整或次优的结果。</mark>

**Why:** The Multi-Agent Collaboration pattern offers a standardized solution by creating a system of multiple, cooperating agents. A complex problem is broken down into smaller, more manageable sub-problems. Each sub-problem is then assigned to a specialized agent with the precise tools and capabilities required to solve it. These agents work together through defined communication protocols and interaction models like sequential handoffs, parallel workstreams, or hierarchical delegation. This agentic, distributed approach creates a synergistic effect, allowing the group to achieve outcomes that would be impossible for any single agent.

<mark><strong>解决之道：</strong> 多智能体协作模式通过创建由多个相互协作的智能体组成的系统，提供了标准化解决方案。复杂问题被分解为更小、更易管理的子问题，每个子问题分配给具有解决该问题所需工具和能力的专业智能体处理。这些智能体按预定义的通信协议和交互模型（如顺序交接、并行工作流或层级委派）协同工作。这样的智能体分工协作方法能够产生协同效应，实现单个智能体无法达成的结果。</mark>

**Rule of thumb:** Use this pattern when a task is too complex for a single agent and can be decomposed into distinct sub-tasks requiring specialized skills or tools. It is ideal for problems that benefit from diverse expertise, parallel processing, or a structured workflow with multiple stages, such as complex research and analysis, software development, or creative content generation.

<mark><strong>经验法则：</strong> 当某个任务对于单个智能体过于复杂并且可以拆分为多个各自需要专业技能或工具的子任务时，应使用此模式。它非常适合从多样化专业知识、并行处理或具有多个阶段的工作流程中受益的问题，例如复杂的研究与分析、软件开发或创意内容生成等。</mark>

**Visual summary:** | <mark>可视化总结：</mark>

![Multi-Agent Design Pattern](/images/chapter07_fig3.png)

Fig.3: Multi-Agent design pattern

<mark>图 3：多智能体设计模式</mark>

---

## Key Takeaways | <mark>核心要点</mark>

- Multi-agent collaboration involves multiple agents working together to achieve a common goal.

   <mark>多个智能体通过协同合作，完成一个共同的目标。</mark>

- This pattern leverages specialized roles, distributed tasks, and inter-agent communication.

   <mark>该模式通过明确分工的专业角色、可独立执行的任务以及智能体间协同通信机制，来实现智能体间的协作。</mark>

- Collaboration can take forms like sequential handoffs, parallel processing, debate, or hierarchical structures.

   <mark>协作可以有多种形式，如顺序交接、并行处理、辩论式讨论或层级结构等。</mark>

- This pattern is ideal for complex problems requiring diverse expertise or multiple distinct stages.

   <mark>该模式非常适合处理需要多种专业技能或包含多个独立阶段的复杂问题。</mark>

---

## Conclusion | <mark>结语</mark>

This chapter explored the Multi-Agent Collaboration pattern, demonstrating the benefits of orchestrating multiple specialized agents within systems. We examined various collaboration models, emphasizing the pattern's essential role in addressing complex, multifaceted problems across diverse domains. Understanding agent collaboration naturally leads to an inquiry into their interactions with the external environment.

<mark>本章探讨了多智能体协作模式，展示了在系统内协同多个专长不同的智能体所带来的优势。我们分析了多种协作模型，强调了该模式在不同领域应对复杂、多阶段问题的重要性。对智能体协作的理解还引出了对它们如何与外部环境交互的进一步思考。</mark>

---

## References | <mark>参考文献</mark>

1. Multi-Agent Collaboration Mechanisms: A Survey of LLMs, [https://arxiv.org/abs/2501.06322](https://arxiv.org/abs/2501.06322)

   <mark>多智能体协作机制：大语言模型综述，[https://arxiv.org/abs/2501.06322](https://arxiv.org/abs/2501.06322)</mark>

2. Multi-Agent System — The Power of Collaboration, [https://aravindakumar.medium.com/introducing-multi-agent-frameworks-the-power-of-collaboration-e9db31bba1b6](https://aravindakumar.medium.com/introducing-multi-agent-frameworks-the-power-of-collaboration-e9db31bba1b6)

   <mark>多智能体系统 -- 协作的力量，[https://aravindakumar.medium.com/introducing-multi-agent-frameworks-the-power-of-collaboration-e9db31bba1b6](https://aravindakumar.medium.com/introducing-multi-agent-frameworks-the-power-of-collaboration-e9db31bba1b6)</mark>
