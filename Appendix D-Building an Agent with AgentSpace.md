# Appendix D-Building an Agent with AgentSpace** | <mark>附录D: 基于AgentSpace构建智能体</mark>

**Agentspace现已更名为Gemini Enterprise;考虑与原文保持一致的原则，本译文仍继续采用AgentSpace名称。

## Overview | <mark>概览</mark>

AgentSpace is a platform designed to facilitate an "agent-driven enterprise" by integrating artificial intelligence into daily workflows. At its core, it provides a unified search capability across an organization's entire digital footprint, including documents, emails, and databases. This system utilizes advanced AI models, like Google's Gemini, to comprehend and synthesize information from these varied sources.

<mark>AgentSpace 是一个旨在通过将人工智能融入日常工作流程来促进“智能体驱动型企业”发展的平台。其核心是提供统一的搜索功能，涵盖组织的全部数字足迹，包括文档、电子邮件和数据库。该系统利用先进的人工智能模型（例如 Google Gemini）来理解和整合来自不同来源的信息。</mark>

The platform enables the creation and deployment of specialized AI "agents" that can perform complex tasks and automate processes. These agents are not merely chatbots; they can reason, plan, and execute multi-step actions autonomously. For instance, an agent could research a topic, compile a report with citations, and even generate an audio summary.

<mark>该平台支持创建和部署专门的人工智能体，这些智能体可以执行复杂任务并实现流程自动化。这些智能体不仅仅是聊天机器人；它们可以自主推理、规划和执行多步骤操作。例如，智能体可以研究某个主题，编写包含引文的报告，甚至生成音频摘要。</mark>

To achieve this, AgentSpace constructs an enterprise knowledge graph, mapping the relationships between people, documents, and data. This allows the AI to understand context and deliver more relevant and personalized results. The platform also includes a no-code interface called Agent Designer for creating custom agents without requiring deep technical expertise.

<mark>为了实现这一点，AgentSpace 构建了一个企业知识图谱，映射了人员、文档和数据之间的关系。这使得人工智能够理解上下文并提供更相关、更个性化的结果。该平台还包含一个名为 Agent Designer 的无代码界面，无需深厚的技术专业知识即可创建自定义智能体。</mark>

Furthermore, AgentSpace supports a multi-agent system where different AI agents can communicate and collaborate through an open protocol known as the Agent2Agent (A2A) Protocol. This interoperability allows for more complex and orchestrated workflows. Security is a foundational component, with features like role-based access controls and data encryption to protect sensitive enterprise information. Ultimately, AgentSpace aims to enhance productivity and decision-making by embedding intelligent, autonomous systems directly into an organization's operational fabric.

<mark>此外，AgentSpace 支持多智能体系统，不同的 AI 智能体可以通过Agent2Agent (A2A) 协议的开放协议进行通信和协作。这种互操作性支持更复杂、更协调的工作流程。安全性是其基础组件，它还提供基于角色的访问控制和数据加密等功能来保护敏感的企业信息。AgentSpace 的最终目标是通过将智能自主系统直接嵌入到组织的运营结构中来提高生产力和决策能力。</mark>

How to build an Agent with AgentSpace UI

<mark>如何使用 AgentSpace UI 构建智能体</mark>

Figure 1 illustrates how to access AgentSpace by selecting AI Applications from the Google Cloud Console.

<mark>图 1 展示了如何通过从 Google Cloud Console 选择“AI Appcalition”来访问 AgentSpace。</mark>

![](https://cdn.nlark.com/yuque/0/2025/png/57829142/1761140597818-455d7428-484f-4bf5-858f-7495fd418bbd.png)

Fig. 1:  How to use Google Cloud Console to access AgentSpace

<mark>图 1：如何使用 Google Cloud Console 访问 AgentSpace</mark>

Your agent can be connected to various services, including Calendar, Google Mail, Workaday, Jira, Outlook, and Service Now (see Fig. 2).

<mark>您的智能体可以连接到各种服务，包括日历、Google Mail、Workaday、Jira、Outlook 和 Service Now（见图 2）。</mark>

![](https://cdn.nlark.com/yuque/0/2025/png/57829142/1761140597872-5c91627d-6ad6-4f13-a72e-82888c0b0eee.png)

Fig. 2: Integrate with diverse services, including Google and third-party platforms.

<mark>图 2：与包括 Google 和第三方平台在内的各种服务集成。</mark>

The Agent can then utilize its own prompt, chosen from a gallery of pre-made prompts provided by Google, as illustrated in Fig. 3.

<mark>然后，智能体可以使用自己的提示，这些提示可以从 Google 提供的预制提示库中选择，如图 3 所示。</mark>

![](https://cdn.nlark.com/yuque/0/2025/png/57829142/1761140598084-0db2871e-1251-44d1-8bcd-ab4c9b13d6f1.png)

Fig.3: Google's Gallery of Pre-assembled  prompts

<mark>图 3：Google 预置提示库</mark>

In alternative you can create your own prompt as in Fig.4, which will be then used by your agent

<mark>或者，您可以像图 4 所示那样创建自己的提示，供您的智能体使用</mark>

![](https://cdn.nlark.com/yuque/0/2025/png/57829142/1761140598048-09bf9f3c-c8bd-4ff9-9514-fc76840344c5.png)

Fig.4: Customizing the Agent's Prompt

<mark>图 4：自定义智能体提示</mark>

AgentSpace offers a number of advanced features such as integration with datastores to store your own data, integration with Google Knowledge Graph or with your private Knowledge Graph, Web interface for exposing your agent to the Web, and Analytics to monitor usage, and more (see Fig. 5) 

<mark>AgentSpace 提供许多高级功能，例如与数据存储集成以存储您自己的数据、与 Google 知识图谱或您的私有知识图谱集成、用于将您的智能体公开到Web界面以及用于监控使用情况的 Analytics 等等（参见图 5）。</mark>

![](https://cdn.nlark.com/yuque/0/2025/png/57829142/1761140598223-8f7249bf-931c-42c2-8f33-a916c0a4bdcb.png)

Fig. 5: AgentSpace advanced capabilities 

<mark>图 5：AgentSpace 高级功能</mark>

Upon completion, the AgentSpace chat interface (Fig. 6) will be accessible.

<mark>完成后，即可访问 AgentSpace 聊天界面（图 6）。</mark>

![](https://cdn.nlark.com/yuque/0/2025/png/57829142/1761140598253-264347cb-f46d-468c-abcc-a87eb21ef909.png)

Fig. 6: The AgentSpace User Interface for initiating a chat with your Agent.

<mark>图 6：用于与您的智能体发起聊天的 AgentSpace 用户界面。</mark>

## Conclusion | <mark>结语</mark>

In conclusion, AgentSpace provides a functional framework for developing and deploying AI agents within an organization's existing digital infrastructure. The system's architecture links complex backend processes, such as autonomous reasoning and enterprise knowledge graph mapping, to a graphical user interface for agent construction. Through this interface, users can configure agents by integrating various data services and defining their operational parameters via prompts, resulting in customized, context-aware automated systems.

<mark>总而言之，AgentSpace 提供用于在组织现有的数字基础架构内开发和部署AI智能体的功能框架。该系统的架构将复杂的后端流程（例如自主推理和企业知识图谱映射）链接到用于构建智能体的图形用户界面。通过该界面，用户可以通过集成各种数据服务并通过提示定义其操作参数来配置智能体，从而构建定制的、情境感知的自动化系统。</mark>

This approach abstracts the underlying technical complexity, enabling the construction of specialized multi-agent systems without requiring deep programming expertise. The primary objective is to embed automated analytical and operational capabilities directly into workflows, thereby increasing process efficiency and enhancing data-driven analysis. For practical instruction, hands-on learning modules are available, such as the "Build a Gen AI Agent with Agentspace" lab on Google Cloud Skills Boost, which provides a structured environment for skill acquisition.

<mark>这种方法抽象了底层的技术复杂性，无需深厚的编程专业知识即可构建专用的多智能体系统。其主要目标是将自动化分析和操作功能直接嵌入到工作流中，从而提高流程效率并增强数据驱动的分析能力。在实践教学方面，我们提供动手学习模块，例如 Google Cloud Skills Boost 上的“Build a Gen AI Agent with Agentspace”实验，它为技能学习提供结构化的环境。</mark>

## References | <mark>参考文献</mark>

1. Create a no-code agent with Agent Designer, [https://cloud.google.com/agentspace/agentspace-enterprise/docs/agent-designer](https://cloud.google.com/agentspace/agentspace-enterprise/docs/agent-designer)

     <mark>使用 Agent Designer 创建无代码智能体，[https://cloud.google.com/agentspace/agentspace-enterprise/docs/agent-designer](https://cloud.google.com/agentspace/agentspace-enterprise/docs/agent-designer)</mark>

2. Google Cloud Skills Boost,[https://www.cloudskillsboost.google/](https://www.cloudskillsboost.google/)

      <mark>Google Cloud Skills Boost,[https://www.cloudskillsboost.google/](https://www.cloudskillsboost.google/)</mark>

