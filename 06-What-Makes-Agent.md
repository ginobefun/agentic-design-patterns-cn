# What makes an AI system an Agent? | <mark>是什么让 AI 系统成为「智能体」？</mark>

In simple terms, an **AI agent** is a system designed to perceive its environment and take actions to achieve a specific goal. It's an evolution from a standard Large Language Model (LLM), enhanced with the abilities to plan, use tools, and interact with its surroundings. Think of an Agentic AI as a smart assistant that learns on the job. It follows a simple, five-step loop to get things done (see Fig.1):

<mark>简单来说，<strong>AI 智能体</strong>是一个能够感知环境并采取行动以实现特定目标的系统。它从标准大语言模型演进而来，被赋予了规划、使用工具以及与周围环境交互的能力。可以把智能体 AI 想象成一个能在工作中不断学习的智能助手。它遵循一个简单的五步循环来完成任务（见图 1）。</mark>

1. **Get the Mission:** You give it a goal, like "organize my schedule."

   <mark><strong>获取任务：</strong>你给它一个目标，比如「帮我安排日程」。</mark>

2. **Scan the Scene:** It gathers all the necessary information—reading emails, checking calendars, and accessing contacts—to understand what's happening.

   <mark><strong>分析环境：</strong>收集所有必要信息——阅读邮件、查看日历、访问联系人——以了解当前状况。</mark>

3. **Think It Through:** It devises a plan of action by considering the optimal approach to achieve the goal.

   <mark><strong>思考对策：</strong>它通过考量达成目标的最佳方法来制定一个行动计划。</mark>

4. **Take Action:** It executes the plan by sending invitations, scheduling meetings, and updating your calendar.

   <mark><strong>采取行动：</strong>通过发送邀请、安排会议、更新日历来执行计划。</mark>

5. **Learn and Get Better:** It observes successful outcomes and adapts accordingly. For example, if a meeting is rescheduled, the system learns from this event to enhance its future performance.

   <mark><strong>学习并改进：</strong>它观察成功的产出并相应地调整自身。例如，如果一个会议被重新安排，系统会从这一事件中学习，以提升其未来的表现。</mark>

![AI Agent Five-Step Loop](/images/fig1.png)

**Fig.1:** Agentic AI functions as an intelligent assistant, continuously learning through experience. It operates via a straightforward five-step loop to accomplish tasks.

<mark>图 1：AI 智能体如同一位智能助手，通过经验持续学习。它通过一个简单的五步循环来完成任务。</mark>

Agents are becoming increasingly popular at a stunning pace. According to recent studies, a majority of large IT companies are actively using these agents, and a fifth of them just started within the past year. The financial markets are also taking notice. By the end of 2024, AI agent startups had raised more than $2 billion, and the market was valued at $5.2 billion. It's expected to explode to nearly $200 billion in value by 2034. In short, all signs point to AI agents playing a massive role in our future economy.

<mark>智能体的普及速度惊人。根据最近的研究，大多数大型 IT 公司正在积极使用这些智能体，其中五分之一的公司是在过去一年内才开始使用的。金融市场也注意到了这一点。到 2024 年底，AI 智能体初创公司已筹集了超过 20 亿美元，市场估值达到 52 亿美元。预计到 2034 年，其市场价值将爆炸式增长至近 2000 亿美元。简而言之，所有迹象都表明 AI 智能体将在我们未来的经济中扮演极为重要的角色。</mark>

In just two years, the AI paradigm has shifted dramatically, moving from simple automation to sophisticated, autonomous systems (see Fig. 2). Initially, workflows relied on basic prompts and triggers to process data with LLMs. This evolved with Retrieval-Augmented Generation (RAG), which enhanced reliability by grounding models on factual information. We then saw the development of individual AI Agents capable of using various tools. Today, we are entering the era of Agentic AI, where a team of specialized agents works in concert to achieve complex goals, marking a significant leap in AI's collaborative power.

<mark>仅仅两年时间，AI 的范式就发生了巨大转变，从简单的自动化演进为复杂的自主系统（见图 2）。最初，工作流依赖于基本的提示和触发器来通过大语言模型处理数据。随后，检索增强生成（RAG）的出现提升了系统的可靠性，因为它将模型建立在事实信息之上。接着，我们看到了能够使用各种工具的独立智能体的发展。如今，我们正在进入 AI 智能体的时代，在这个时代里，一个由专业化智能体组成的团队协同工作以实现复杂目标，这标志着AI协作能力的一次重大飞跃。</mark>

![AI Evolution Timeline](/images/fig2.png)

Fig 2.: Transitioning from LLMs to RAG, then to Agentic RAG, and finally to Agentic AI.

<mark>图 2：从 LLM 到 RAG，再到智能体 RAG，最终走向 AI 智能体的演进。</mark>

The intent of this book is to discuss the design patterns of how specialized agents can work in concert and collaborate to achieve complex goals, and you will see one paradigm of collaboration and interaction in each chapter.

<mark>本书旨在讨论专业化智能体如何协同工作以实现复杂目标的设计模式，你将在每一章中看到一种协作与交互的范式。</mark>

Before doing that, let's examine examples that span the range of agent complexity (see Fig. 3).

<mark>在此之前，让我们先来看几个贯穿智能体复杂度范围的例子（见图 3）。</mark>

---

## Level 0: The Core Reasoning Engine | <mark>0 级：核心推理引擎</mark>

While an LLM is not an agent in itself, it can serve as the reasoning core of a basic agentic system. In a 'Level 0' configuration, the LLM operates without tools, memory, or environment interaction, responding solely based on its pretrained knowledge. Its strength lies in leveraging its extensive training data to explain established concepts. The trade-off for this powerful internal reasoning is a complete lack of current-event awareness. For instance, it would be unable to name the 2025 Oscar winner for "Best Picture" if that information is outside its pre-trained knowledge.

<mark>虽然大语言模型本身不是智能体，但它可以作为基础智能体系统的推理核心。在一个「0 级」配置中，大语言模型在没有工具、记忆或环境交互的情况下运行，仅仅基于其预训练的知识进行响应。它的优势在于利用其海量的训练数据来解释已有的概念，代价是完全缺乏对当前事件的感知。例如，如果关于“2025年奥斯卡最佳影片奖”得主的信息超出了它的预训练知识范围，它将无法给出答案。</mark>

---

## Level 1: The Connected Problem-Solver | <mark>1 级：连接外部的问题解决者</mark>

At this level, the LLM becomes a functional agent by connecting to and utilizing external tools. Its problem-solving is no longer limited to its pre-trained knowledge. Instead, it can execute a sequence of actions to gather and process information from sources like the internet (via search) or databases (via Retrieval Augmented Generation, or RAG). For detailed information, refer to Chapter 14.

<mark>在这个级别，大语言模型通过连接并使用外部工具，摇身成为功能性智能体。它解决问题的能力不再局限于其预训练的知识。相反，它能够执行一系列动作，从互联网（通过搜索）或数据库（通过检索增强生成，即 RAG）等来源收集和处理信息。更多详细信息，请参阅第 14 章。</mark>

For instance, to find new TV shows, the agent recognizes the need for current information, uses a search tool to find it, and then synthesizes the results. Crucially, it can also use specialized tools for higher accuracy, such as calling a financial API to get the live stock price for AAPL. This ability to interact with the outside world across multiple steps is the core capability of a Level 1 agent.

<mark>例如，为了寻找新的电视节目，智能体识别出需要最新信息，于是使用搜索工具来查找，然后综合处理结果。至关重要的一点是，它还可以使用专业工具以获得更高精度，例如调用金融 API 来获取苹果公司的实时股价。这种跨多个步骤与外部世界交互的能力，正是 1 级智能体的核心。</mark>

---

## Level 2: The Strategic Problem-Solver | <mark>2 级：战略性问题解决者</mark>

At this level, an agent's capabilities expand significantly, encompassing strategic planning, proactive assistance, and self-improvement, with prompt engineering and context engineering as core enabling skills.

<mark>在这个级别，智能体的能力显著扩展，涵盖战略规划、主动协助和自我提升，而提示工程和上下文工程是其核心赋能技能。</mark>

First, the agent moves beyond single-tool use to tackle complex, multi-part problems through strategic problem-solving. As it executes a sequence of actions, it actively performs context engineering: the strategic process of selecting, packaging, and managing the most relevant information for each step. For example, to find a coffee shop between two locations, it first uses a mapping tool. It then engineers this output, curating a short, focused context—perhaps just a list of street names—to feed into a local search tool, preventing cognitive overload and ensuring the second step is efficient and accurate. To achieve maximum accuracy from an AI, it must be given a short, focused, and powerful context. Context engineering is the discipline that accomplishes this by strategically selecting, packaging, and managing the most critical information from all available sources. It effectively curates the model's limited attention to prevent overload and ensure high-quality, efficient performance on any given task. For detailed information, refer to the Appendix A.

<mark>首先，智能体超越了单一工具的使用，通过战略性问题解决来处理复杂、多部分的问题。在执行一系列动作时，它会主动进行上下文工程（Context Engineering）：即为每一步战略性地选择、打包和管理最相关信息的过程。例如，要在两个地点之间找一家咖啡店，它首先会使用地图工具。然后，它会对输出结果进行工程化处理，筛选出一个简短、集中的上下文——也许只是一串街道名称列表——再输入给本地搜索工具，以避免认知过载，确保第二步既高效又准确。要从 AI 获得最高精度，就必须给它一个简短、专注且有力的上下文。上下文工程正是实现这一目标的学科，它通过战略性地从所有可用来源中选择、打包和管理最关键的信息来做到这一点。它有效地管理模型的有限注意力以防止过载，确保在任何给定任务上都能实现高质量、高效率的表现。更多详细信息，请参阅附录A。</mark>

This level leads to proactive and continuous operation. A travel assistant linked to your email demonstrates this by engineering the context from a verbose flight confirmation email; it selects only the key details (flight numbers, dates, locations) to package for subsequent tool calls to your calendar and a weather API.

<mark>这个级别带来主动且持续的运行方式。一个与你的邮箱关联的旅行助手就展示了这一点：它会从一封冗长的航班确认邮件中进行上下文工程，只选择关键细节（航班号、日期、地点），然后打包这些信息用于后续调用你的日历和天气 API。</mark>

In specialized fields like software engineering, the agent manages an entire workflow by applying this discipline. When assigned a bug report, it reads the report and accesses the codebase, then strategically engineers these large sources of information into a potent, focused context that allows it to efficiently write, test, and submit the correct code patch.

<mark>在软件工程等专业领域，智能体通过应用这门学科来管理整个工作流。当分配给它一个错误报告时，它会阅读报告并访问代码库，然后战略性地将这些海量信息源工程化处理成一个强有力、高度集中的上下文，使其能够高效地编写、测试并提交正确的代码补丁。</mark>

Finally, the agent achieves self-improvement by refining its own context engineering processes. When it asks for feedback on how a prompt could have been improved, it is learning how to better curate its initial inputs. This allows it to automatically improve how it packages information for future tasks, creating a powerful, automated feedback loop that increases its accuracy and efficiency over time. For detailed information, refer to Chapter 17.

<mark>最后，智能体通过优化自身的上下文工程流程来实现自我提升。当它就“某个提示本可以如何改进”而征求反馈时，它实际上是在学习如何更好地筛选其初始输入。这使其能够自动改进为未来任务打包信息的方式，从而创建一个强大的自动化反馈循环，随着时间的推移不断提高其准确性和效率。更多详细信息，请参阅第 17 章。</mark>

![Agent Complexity Levels](/images/fig3.png)

Fig. 3: Various instances demonstrating the spectrum of agent complexity.

<mark>图 3：展示不同复杂度智能体的实例。</mark>

---

## Level 3: The Rise of Collaborative Multi-Agent Systems | <mark>3 级：协作型多智能体系统的兴起</mark>

At Level 3, we see a significant paradigm shift in AI development, moving away from the pursuit of a single, all-powerful super-agent and towards the rise of sophisticated, collaborative multi-agent systems. In essence, this approach recognizes that complex challenges are often best solved not by a single generalist, but by a team of specialists working in concert. This model directly mirrors the structure of a human organization, where different departments are assigned specific roles and collaborate to tackle multi-faceted objectives. The collective strength of such a system lies in this division of labor and the synergy created through coordinated effort. For detailed information, refer to Chapter 7.

<mark>在 3 级，我们看到了 AI 发展的一次重大范式转变：不再追求单一、全能的超级智能体，而是转向发展复杂的、协作式的多智能体系统。本质上，这种方法认识到，复杂的挑战通常不是由一个通才，而是由一个协同工作的专家团队来解决的。这个模型直接映射了人类组织的结构，其中不同部门被赋予特定角色，并协作处理多方面的目标。这种系统的集体力量在于劳动分工以及通过协调努力产生的协同效应。更多详细信息，请参阅第 7 章。</mark>

To bring this concept to life, consider the intricate workflow of launching a new product. Rather than one agent attempting to handle every aspect, a "Project Manager" agent could serve as the central coordinator. This manager would orchestrate the entire process by delegating tasks to other specialized agents: a "Market Research" agent to gather consumer data, a "Product Design" agent to develop concepts, and a "Marketing" agent to craft promotional materials. The key to their success would be the seamless communication and information sharing between them, ensuring all individual efforts align to achieve the collective goal.

<mark>为了将这个概念具体化，可以想象一下发布一款新产品的复杂工作流。并非由一个智能体尝试处理所有方面，而是一个「项目经理」智能体可以作为中心协调者。这个经理会通过将任务委派给其他专业化智能体来统筹整个过程：一个「市场研究」智能体负责收集消费者数据，一个「产品设计」智能体负责开发概念，以及一个「市场营销」智能体负责制作宣传材料。它们成功的关键在于彼此之间无缝的沟通和信息共享，确保所有个体努力都统一指向集体目标。</mark>

While this vision of autonomous, team-based automation is already being developed, it's important to acknowledge the current hurdles. The effectiveness of such multi-agent systems is presently constrained by the reasoning limitations of LLMs they are using. Furthermore, their ability to genuinely learn from one another and improve as a cohesive unit is still in its early stages. Overcoming these technological bottlenecks is the critical next step, and doing so will unlock the profound promise of this level: the ability to automate entire business workflows from start to finish.

<mark>虽然这种基于团队的自主自动化愿景已在开发中，但认识到当前的障碍也很重要。这类多智能体系统的有效性目前受限于它们所使用模型的推理能力。此外，它们真正相互学习并作为一个有凝聚力的整体来改进的能力仍处于早期阶段。克服这些技术瓶颈是关键的一步，而一旦做到这一点，将释放这一级别的深远潜力：实现从头到尾自动化整个业务工作流的能力。</mark>

---

## The Future of Agents: Top 5 Hypotheses | <mark>智能体的未来：五大假设</mark>

AI agent development is progressing at an unprecedented pace across domains such as software automation, scientific research, and customer service among others. While current systems are impressive, they are just the beginning. The next wave of innovation will likely focus on making agents more reliable, collaborative, and deeply integrated into our lives. Here are five leading hypotheses for what's next (see Fig. 4).

<mark>AI 智能体开发正在软件自动化、科学研究和客户服务等领域以前所未有的速度推进。虽然当前的系统令人印象深刻，但它们仅仅是开始。下一波创新浪潮可能会聚焦于让智能体更可靠、更具协作性，并更深度融入我们的生活。以下是关于未来的五个主要假说（见图 4）。</mark>

### Hypothesis 1: The Emergence of the Generalist Agent | <mark>假设 1：通用智能体的崛起</mark>

The first hypothesis is that AI agents will evolve from narrow specialists into true generalists capable of managing complex, ambiguous, and long-term goals with high reliability. For instance, you could give an agent a simple prompt like, "Plan my company's offsite retreat for 30 people in Lisbon next quarter." The agent would then manage the entire project for weeks, handling everything from budget approvals and flight negotiations to venue selection and creating a detailed itinerary from employee feedback, all while providing regular updates. Achieving this level of autonomy will require fundamental breakthroughs in AI reasoning, memory, and near-perfect reliability. An alternative, yet not mutually exclusive, approach is the rise of Small Language Models (SLMs). This "Lego-like" concept involves composing systems from small, specialized expert agents rather than scaling up a single monolithic model. This method promises systems that are cheaper, faster to debug, and easier to deploy. Ultimately, the development of large generalist models and the composition of smaller specialized ones are both plausible paths forward, and they could even complement each other.

<mark>第一个假设是，AI 智能体将从狭隘的专家演变为真正的通用型选手，能够高可靠性地管理复杂、模糊和长期的目标。例如，你可以给智能体一个简单的提示，如「为我们公司 30 名员工筹划下个季度在里斯本的异地团建」。随后，这个智能体将管理整个项目长达数周，处理从预算审批、航班谈判到场地选择，再到根据员工反馈创建详细行程的所有事宜，并同时提供定期更新。实现这种级别的自主性将需要在 AI 推理、记忆与近乎完美可靠性方面取得根本性突破。一种替代性但并非相互排斥的方法是小型语言模型（SLM）的兴起。这种「乐高式」的概念涉及用小型的、专业化的专家智能体来组合成系统，而不是扩展单一的巨型模型。这种方法有望使系统更便宜、调试更快、部署更容易。最终，大型通用模型的发展和小型专业模型的组合都是未来可行的路径，它们甚至可能相得益彰。</mark>

### Hypothesis 2: Deep Personalization and Proactive Goal Discovery | <mark>假设 2：深度个性化与主动发现目标</mark>

The second hypothesis posits that agents will become deeply personalised and proactive partners. We are witnessing the emergence of a new class of agent: the proactive partner. By learning from your unique patterns and goals, these systems are beginning to shift from just following orders to anticipating your needs. AI systems operate as agents when they move beyond simply responding to chats or instructions. They initiate and execute tasks on behalf of the user, actively collaborating in the process. This moves beyond simple task execution into the realm of proactive goal discovery.

<mark>第二个假设认为智能体将成为深度个性化且主动的合作伙伴。我们正在见证类新型智能体的诞生：主动合作伙伴。通过学习你独特的模式与目标，这些系统开始从仅仅遵循命令，转向预测你的需求。当 AI 系统超越简单地响应聊天或指令时，它们便作为智能体在运作。它们代表用户发起并执行任务，在过程中积极协作。这超越了简单的任务执行，进入主动目标发现的领域。</mark>

For instance, if you're exploring sustainable energy, the agent might identify your latent goal and proactively support it by suggesting courses or summarizing research. While these systems are still developing, their trajectory is clear. They will become increasingly proactive, learning to take initiative on your behalf when highly confident that the action will be helpful. Ultimately, the agent becomes an indispensable ally, helping you discover and achieve ambitions you have yet to fully articulate.

<mark>例如，如果你正在探索可持续能源，智能体可能会识别你的潜在目标，并主动支持它，比如推荐相关课程或总结研究报告。虽然这些系统仍在发展中，但它们的轨迹很清楚。它们将变得越来越主动，并在高度确信该行动会有帮助时，学会代表你采取行动。最终，智能体将成为不可或缺的盟友，帮助你发现并实现那些你尚未完全清晰表达的抱负。</mark>

![Future Agent Hypotheses](/images/fig4.png)

**Fig. 4:** Five hypotheses about the future of agents

<mark><strong>图 4：</strong>关于智能体未来的五个假设</mark>

### Hypothesis 3: Embodiment and Physical World Interaction | <mark>假设 3：具身化与物理世界交互</mark>

This hypothesis foresees agents breaking free from their purely digital confines to operate in the physical world. By integrating agentic AI with robotics, we will see the rise of "embodied agents." Instead of just booking a handyman, you might ask your home agent to fix a leaky tap. The agent would use its vision sensors to perceive the problem, access a library of plumbing knowledge to formulate a plan, and then control its robotic manipulators with precision to perform the repair. This would represent a monumental step, bridging the gap between digital intelligence and physical action, and transforming everything from manufacturing and logistics to elder care and home maintenance.

<mark>这个假说预见智能体将挣脱纯粹的数字束缚，在物理世界中运作。通过将 AI 智能体与机器人技术相结合，我们将看到具身智能体（Embodied Agents）的兴起。你或许不再是仅仅预订一个水电工，而是直接让你的家庭智能体修理一个漏水的水龙头。智能体将使用其视觉传感器来感知问题，访问一个管道知识库来制定计划，然后精确地控制其机械臂来执行修复。这将是里程碑式的一步，弥合了数字智能与物理行动之间的鸿沟，并将彻底改变从制造业、物流到老年护理和家庭维护的方方面面。</mark>

### Hypothesis 4: The Agent-Driven Economy | <mark>假设 4：智能体驱动的经济</mark>

The fourth hypothesis is that highly autonomous agents will become active participants in the economy, creating new markets and business models. We could see agents acting as independent economic entities, tasked with maximising a specific outcome, such as profit. An entrepreneur could launch an agent to run an entire e-commerce business. The agent would identify trending products by analysing social media, generate marketing copy and visuals, manage supply chain logistics by interacting with other automated systems, and dynamically adjust pricing based on real-time demand. This shift would create a new, hyper-efficient "agent economy" operating at a speed and scale impossible for humans to manage directly.

<mark>第四个假设是，高度自主的智能体将成为经济中的积极参与者，创造新的市场和商业模式。我们可能会看到智能体作为独立的经济实体，其任务是最大化一个特定结果，例如利润。企业家可以启动一个智能体来运营整个电子商务业务。该智能体将通过分析社交媒体来识别热门产品，生成营销文案和视觉材料，通过与其他自动化系统交互来管理供应链物流，并根据实时需求动态调整定价。这一转变将创造一个全新的、超高效率的「智能体经济」，其运行速度和规模是人类无法直接管理的。</mark>

### Hypothesis 5: The Goal-Driven, Metamorphic Multi-Agent System | <mark>假设 5：目标驱动的、可演化的多智能体系统</mark>

This hypothesis posits the emergence of intelligent systems that operate not from explicit programming, but from a declared goal. The user simply states the desired outcome, and the system autonomously figures out how to achieve it. This marks a fundamental shift towards metamorphic multi-agent systems capable of true self-improvement at both the individual and collective levels.

<mark>该假说断言，将会出现一种并非基于显式编程，而是基于一个声明性目标来运作的智能系统。用户只需陈述期望的结果，系统便能自主地找出如何实现它。这标志着向可演化多智能体系统的根本性转变，这种系统能够在个体和集体层面实现真正的自我提升。</mark>

This system would be a dynamic entity, not a single agent. It would have the ability to analyze its own performance and modify the topology of its multi-agent workforce, creating, duplicating, or removing agents as needed to form the most effective team for the task at hand. This evolution happens at multiple levels:

<mark>这个系统将是一个动态实体，而非单个智能体。它将有能力分析自身表现并修改其多智能体工作团队的拓扑结构，根据需要创建、复制或移除智能体，以组成最适合当前任务的团队。这种演化发生在多个层面：</mark>

- **Architectural Modification:** At the deepest level, individual agents can rewrite their own source code and re-architect their internal structures for higher efficiency, as in the original hypothesis.

- <mark><strong>架构层面的修改：</strong>在最深层次，单个智能体可以重写自身的源代码并重构其内部结构以提高效率，正如最初的假说所设想的那样。</mark>

- **Instructional Modification:** At a higher level, the system continuously performs automatic prompt engineering and context engineering. It refines the instructions and information given to each agent, ensuring they are operating with optimal guidance without any human intervention.

- <mark><strong>指令层面的修改：</strong>在更高层次，系统持续进行自动化的提示工程和上下文工程。它不断优化给予每个智能体的指令和信息，确保它们在没有任何人工干预的情况下以最佳指导进行运作。</mark>

For instance, an entrepreneur would simply declare the intent: "Launch a successful e-commerce business selling artisanal coffee." The system, without further programming, would spring into action. It might initially spawn a "Market Research" agent and a "Branding" agent. Based on the initial findings, it could decide to remove the branding agent and spawn three new specialized agents: a "Logo Design" agent, a "Webstore Platform" agent, and a "Supply Chain" agent. It would constantly tune their internal prompts for better performance. If the webstore agent becomes a bottleneck, the system might duplicate it into three parallel agents to work on different parts of the site, effectively re-architecting its own structure on the fly to best achieve the declared goal.

<mark>例如，企业家只需声明一个意图：「启动一个成功的手工咖啡电商业务」。系统无需进一步编程即刻行动：它可能先生成「市场研究」与「品牌」两个智能体；随后基于初步结论，移除品牌智能体，并衍生出三个更细分的角色：「Logo 设计」「网店平台」「供应链」。系统会持续调校它们的内部提示以优化表现。如果网店智能体成为瓶颈，系统可能会将其复制成三个并行的智能体来处理网站的不同部分，从而动态地重构自身结构，以更好地实现声明的目标。</mark>

---

## Conclusion | <mark>总结</mark>

In essence, an AI agent represents a significant leap from traditional models, functioning as an autonomous system that perceives, plans, and acts to achieve specific goals. The evolution of this technology is advancing from single, tool-using agents to complex, collaborative multi-agent systems that tackle multifaceted objectives. Future hypotheses predict the emergence of generalist, personalized, and even physically embodied agents that will become active participants in the economy. This ongoing development signals a major paradigm shift towards self-improving, goal-driven systems poised to automate entire workflows and fundamentally redefine our relationship with technology.

<mark>本质上，AI 智能体代表了从传统模型的一次重大飞跃，它作为一个自主系统，能够感知、规划和行动以达成特定目标。这项技术正从使用单一工具的智能体，演进为处理多方面目标的复杂、协作式多智能体系统。未来的假说预测了通用型、个性化、乃至物理具身化的智能体的出现，它们将成为经济活动的积极参与者。这一持续的发展标志着一次重大的范式转变，即向能够自动化整个工作流并从根本上重新定义我们与技术关系的、自我提升的、目标驱动的系统迈进。</mark>

---

## References | <mark>参考文献</mark>

1. Cloudera, Inc. (April 2025), 96% of enterprises are increasing their use of AI agents. [https://www.cloudera.com/about/news-and-blogs/press-releases/2025-04-16-96-percent-of-enterprises-are-expanding-use-of-ai-agents-according-to-latest-data-from-cloudera.html](https://www.cloudera.com/about/news-and-blogs/press-releases/2025-04-16-96-percent-of-enterprises-are-expanding-use-of-ai-agents-according-to-latest-data-from-cloudera.html)

   <mark>Cloudera, Inc.（2025 年 4 月），96% 的企业正在增加对 AI 智能体的使用。</mark>

2. Autonomous generative AI agents: [https://www.deloitte.com/us/en/insights/industry/technology/technology-media-and-telecom-predictions/2025/autonomous-generative-ai-agents-still-under-development.html](https://www.deloitte.com/us/en/insights/industry/technology/technology-media-and-telecom-predictions/2025/autonomous-generative-ai-agents-still-under-development.html)

   <mark>自主生成式 AI 智能体：</mark>

3. Market.us. Global Agentic AI Market Size, Trends and Forecast 2025–2034. [https://market.us/report/agentic-ai-market/](https://market.us/report/agentic-ai-market/)

   <mark>Market.us. 全球智能体 AI 市场规模、趋势和 2025-2034 年预测。</mark>
