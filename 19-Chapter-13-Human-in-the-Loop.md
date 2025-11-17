# Chapter 13: Human-in-the-Loop | <mark>第 13 章：人机协同</mark>

The Human-in-the-Loop (HITL) pattern represents a pivotal strategy in the development and deployment of Agents. It deliberately interweaves the unique strengths of human cognition—such as judgment, creativity, and nuanced understanding—with the computational power and efficiency of AI. This strategic integration is not merely an option but often a necessity, especially as AI systems become increasingly embedded in critical decision-making processes.

<mark>人机协同（Human-in-the-Loop，HITL，即人类在决策环路中直接参与）模式代表了智能体开发和部署中的一项关键策略。它有意地将人类认知的独特优势（如判断力、创造力和细致入微的理解力）与 AI 的计算能力和效率结合起来。这种战略性整合不仅仅是一种选择，而且往往是一种必需，尤其是当 AI 系统日益深入地嵌入到关键决策过程中时。</mark>

The core principle of HITL is to ensure that AI operates within ethical boundaries, adheres to safety protocols, and achieves its objectives with optimal effectiveness. These concerns are particularly acute in domains characterized by complexity, ambiguity, or significant risk, where the implications of AI errors or misinterpretations can be substantial. In such scenarios, full autonomy—where AI systems function independently without any human intervention—may prove to be imprudent. HITL acknowledges this reality and emphasizes that even with rapidly advancing AI technologies, human oversight, strategic input, and collaborative interactions remain indispensable.

<mark>人机协同的核心原则是确保 AI 在道德约束下运行，遵守安全协议，并以最佳效率实现其目标。这些考量在具有复杂性、模糊性或重大风险的领域尤为重要，因为在这些领域，AI 的错误或误解可能带来严重后果。在这种情况下，完全自主（即 AI 系统在没有任何人工干预的情况下独立运行）往往是不明智的。人机协同模式承认这一现实，并强调即使 AI 技术日新月异，人类的监督、战略性输入和协作互动仍然不可或缺。</mark>

The HITL approach fundamentally revolves around the idea of synergy between artificial and human intelligence. Rather than viewing AI as a replacement for human workers, HITL positions AI as a tool that augments and enhances human capabilities. This augmentation can take various forms, from automating routine tasks to providing data-driven insights that inform human decisions. The end goal is to create a collaborative ecosystem where both humans and AI Agents can leverage their distinct strengths to achieve outcomes that neither could accomplish alone.

<mark>人机协同方法从根本上围绕着人工智能与人类智能之间的协同作用展开。人机协同模式并不将 AI 视为人类工作者的替代品，而是将其定位为一种增强和提升人类能力的工具。这种增强可以采取多种形式，从自动化常规任务到提供数据驱动的洞察以辅助人类决策。最终目标是创建一个协作生态系统，使人类和 AI 智能体都能利用各自的独特优势，实现任何一方都无法单独取得的成果。</mark>

In practice, HITL can be implemented in diverse ways. One common approach involves humans acting as validators or reviewers, examining AI outputs to ensure accuracy and identify potential errors. Another implementation involves humans actively guiding AI behavior, providing feedback or making corrections in real-time. In more complex setups, humans may collaborate with AI as partners, jointly solving problems or making decisions through interactive dialog or shared interfaces. Regardless of the specific implementation, the HITL pattern underscores the importance of maintaining human control and oversight, ensuring that AI systems remain aligned with human ethics, values, goals, and societal expectations.

<mark>在实践中，人机协同模式可以通过多种方式实现。一种常见的方法是让人类担任验证者或审查者，检查 AI 的输出以确保准确性并识别潜在错误。另一种实现方式是让人类主动引导 AI 的行为，实时提供反馈或进行纠正。在更复杂的设置中，人类可以作为合作伙伴与 AI 协作，通过交互式对话或共享界面共同解决问题或制定决策。无论具体实现方式如何，人机协同模式都强调了保持人类控制和监督的重要性，确保 AI 系统始终与人类的伦理、价值观、目标和社会期望保持一致。</mark>

## Human-in-the-Loop Pattern Overview | <mark>人机协同模式概述</mark>

The Human-in-the-Loop (HITL) pattern integrates artificial intelligence with human input to enhance Agent capabilities. This approach acknowledges that optimal AI performance frequently requires a combination of automated processing and human insight, especially in scenarios with high complexity or ethical considerations. Rather than replacing human input, HITL aims to augment human abilities by ensuring that critical judgments and decisions are informed by human understanding.

<mark>人机协同（HITL）模式将人工智能与人类输入相结合，以增强智能体的能力。这种方法认为，最佳的 AI 性能往往需要自动化处理与人类洞察力的结合，尤其是在具有高度复杂性或伦理考量的场景中。人机协同模式并非取代人类输入，而是通过确保关键判断和决策基于人类理解，从而增强人类的能力。</mark>

HITL encompasses several key aspects: Human Oversight, which involves monitoring AI agent performance and output (e.g., via log reviews or real-time dashboards) to ensure adherence to guidelines and prevent undesirable outcomes. Intervention and Correction occurs when an AI agent encounters errors or ambiguous scenarios and may request human intervention; human operators can rectify errors, supply missing data, or guide the agent, which also informs future agent improvements. Human Feedback for Learning is collected and used to refine AI models, prominently in methodologies like reinforcement learning with human feedback, where human preferences directly influence the agent's learning trajectory. Decision Augmentation is where an AI agent provides analyses and recommendations to a human, who then makes the final decision, enhancing human decision-making through AI-generated insights rather than full autonomy. Human-Agent Collaboration is a cooperative interaction where humans and AI agents contribute their respective strengths; routine data processing may be handled by the agent, while creative problem-solving or complex negotiations are managed by the human. Finally, Escalation Policies are established protocols that dictate when and how an agent should escalate tasks to human operators, preventing errors in situations beyond the agent's capability.

<mark>人机协同模式包含几个关键方面：人类监督（Human Oversight），涉及监控 AI 智能体的性能和输出（例如，通过日志审查或实时仪表板），以确保其遵守准则并防止不良后果。当 AI 智能体遇到错误或模糊场景时，需要干预与纠正，此时智能体可能请求人类干预；人类操作员可以纠正错误、提供缺失数据或指导智能体，这也有助于智能体未来的改进。用于学习的人类反馈（Human Feedback for Learning）被收集并用于优化 AI 模型，这在诸如基于人类反馈的强化学习（RLHF）等方法中尤为突出，其中人类偏好直接影响智能体的学习轨迹。决策增强（Decision Augmentation）是指 AI 智能体向人类提供分析和建议，由人类做出最终决定，通过 AI 生成的洞察力来增强人类决策，而非完全自主。人机协作（Human-Agent Collaboration）是一种合作互动，人类和 AI 智能体各自贡献其优势；常规数据处理可能由智能体负责，而创造性问题解决或复杂谈判则由人类管理。最后，上报策略（Escalation Policies）是既定的协议，规定了智能体应在何时以及如何将任务上报给人类操作员，以防止在超出智能体能力的情况下出错。</mark>

Implementing HITL patterns enables the use of Agents in sensitive sectors where full autonomy is not feasible or permitted. It also provides a mechanism for ongoing improvement through feedback loops. For example, in finance, the final approval of a large corporate loan requires a human loan officer to assess qualitative factors like leadership character. Similarly, in the legal field, core principles of justice and accountability demand that a human judge retain final authority over critical decisions like sentencing, which involve complex moral reasoning.

<mark>实施人机协同模式使得智能体能够在不允许或不可行完全自主的敏感行业中得到应用。它还通过反馈循环提供了一种持续改进的机制。例如，在金融领域，大额企业贷款的最终批准需要人类信贷员来评估领导者品格等定性因素。同样，在法律领域，正义和问责的核心原则要求人类法官对量刑等涉及复杂道德推理的关键决策保留最终决定权。</mark>

**Caveats**: Despite its benefits, the HITL pattern has significant caveats, chief among them being a lack of scalability. While human oversight provides high accuracy, operators cannot manage millions of tasks, creating a fundamental trade-off that often requires a hybrid approach combining automation for scale and HITL for accuracy. Furthermore, the effectiveness of this pattern is heavily dependent on the expertise of the human operators; for example, while an AI can generate software code, only a skilled developer can accurately identify subtle errors and provide the correct guidance to fix them. This need for expertise also applies when using HITL to generate training data, as human annotators may require special training to learn how to correct an AI in a way that produces high-quality data. Lastly, implementing HITL raises significant privacy concerns, as sensitive information must often be rigorously anonymized before it can be exposed to a human operator, adding another layer of process complexity.

<mark><strong>注意事项：</strong>尽管人机协同模式有其好处，但它也存在一些显著的注意事项，其中最主要的是缺乏可扩展性。虽然人类监督能提供高准确性，但操作员无法管理数百万个任务，这就需要进行权衡，通常使用一种混合方法，将自动化用于规模化，将人机协同模式用于保证准确性。此外，该模式的有效性在很大程度上取决于人类操作员的专业知识；例如，虽然 AI 可以生成软件代码，但只有熟练的开发人员才能准确识别细微错误并提供正确的指导来修复它们。这种对专业知识的需求也适用于使用人机协同模式生成训练数据时，因为人类标注者可能需要接受专门培训，以学习如何纠正 AI 才能产生高质量的数据。最后，实施人机协同模式会引发严重的隐私问题，因为敏感信息在暴露给人类操作员之前通常必须经过严格的匿名化处理，这又增加了一层流程复杂性。</mark>

## Practical Applications & Use Cases | <mark>实际应用与用例</mark>

The Human-in-the-Loop pattern is vital across a wide range of industries and applications, particularly where accuracy, safety, ethics, or nuanced understanding are paramount.

<mark>人机协同模式在众多行业和应用中都至关重要，特别是在那些对准确性、安全性、伦理或细致入微的理解有极高要求的领域。</mark>

- **Content Moderation**: AI agents can rapidly filter vast amounts of online content for violations (e.g., hate speech, spam). However, ambiguous cases or borderline content are escalated to human moderators for review and final decision, ensuring nuanced judgment and adherence to complex policies.

   <mark><strong>内容审核：</strong>AI 智能体可以快速过滤海量内容，筛查违规行为（例如仇恨言论或垃圾信息）。然而，一些模棱两可或处于边缘地带的内容需要上报给人类审核员进行审查并做出最终决定，以确保细致入微的判断和遵守复杂的政策。</mark>

- **Autonomous Driving**: While self-driving cars handle most driving tasks autonomously, they are designed to hand over control to a human driver in complex, unpredictable, or dangerous situations that the AI cannot confidently navigate (e.g., extreme weather, unusual road conditions).

  <mark><strong>自动驾驶：</strong>虽然自动驾驶汽车能自主处理大多数驾驶任务，但在 AI 无法自信应对的复杂、不可预测或危险情况下（例如极端天气或异常路况），需要将控制权交还给人类驾驶员。</mark>

- **Financial Fraud Detection**: AI systems can flag suspicious transactions based on patterns. However, high-risk or ambiguous alerts are often sent to human analysts who investigate further, contact customers, and make the final determination on whether a transaction is fraudulent.

   <mark><strong>金融欺诈检测：</strong>AI 系统可以根据模式标记可疑交易。但是，高风险或模棱两可的警报通常会发送给专业分析师，由他们进行深入调查、联系客户，并最终确定交易是否具有欺诈性。</mark>

- **Legal Document Review**: AI can quickly scan and categorize thousands of legal documents to identify relevant clauses or evidence. Human legal professionals then review the AI's findings for accuracy, context, and legal implications, especially for critical cases.

   <mark><strong>法律文件审查：</strong>AI 可以快速扫描和分类数千份法律文件，以识别相关条款或证据。接着，对于关键案件，还需要专业法律人士审查 AI 的发现，核实其准确性、上下文和法律含义。</mark>

- **Customer Support (Complex Queries)**: A chatbot might handle routine customer inquiries. If the user's problem is too complex, emotionally charged, or requires empathy that the AI cannot provide, the conversation is seamlessly handed over to a human support agent.

  <mark><strong>客户支持（复杂咨询）：</strong>聊天机器人可以处理常规的客户咨询。如果用户的问题过于复杂、情绪过于激动，或者需要 AI 无法提供的情感共鸣时，需要将对话转接给人工坐席进行处理。</mark>

- **Data Labeling and Annotation**: AI models often require large datasets of labeled data for training. Humans are put in the loop to accurately label images, text, or audio, providing the ground truth that the AI learns from. This is a continuous process as models evolve.

  <mark><strong>数据标注：</strong>AI 模型通常需要大量标注数据进行训练。为确保准确标注图像、文本或音频，人类需要参与到这个过程中，为 AI 提供学习所需的“真实值”（ground truth）。随着模型的发展，这是一个持续的过程。</mark>

- **Generative AI Refinement**: When an LLM generates creative content (e.g., marketing copy, design ideas), human editors or designers review and refine the output, ensuring it meets brand guidelines, resonates with the target audience, and maintains quality.

  <mark><strong>生成式 AI 优化：</strong>当使用大语言模型生成创意内容（例如营销文案或设计理念）时，专业编辑或设计师会审查和优化输出，确保其符合品牌准则，能与目标受众产生共鸣，并确保输出内容的质量。</mark>

- **Autonomous Networks**: AI systems are capable of analyzing alerts and forecasting network issues and traffic anomalies by leveraging key performance indicators (KPIs) and identified patterns. Nevertheless, crucial decisions—such as addressing high-risk alerts—are frequently escalated to human analysts. These analysts conduct further investigation and make the ultimate determination regarding the approval of network changes.

  <mark><strong>自治网络：</strong>AI 系统能够利用关键性能指标（KPI）和已识别的模式来分析警报、预测网络问题和流量异常。然而，一些关键的决策（例如处理高风险警报）经常被上报给专业分析师。这些分析师会进行进一步调查，并决定是否批准网络变更。</mark>

This pattern exemplifies a practical method for AI implementation. It harnesses AI for enhanced scalability and efficiency, while maintaining human oversight to ensure quality, safety, and ethical compliance.

<mark>该模式展示了一种实用的 AI 实施策略。它利用 AI 来提高可扩展性和效率，同时保持人类监督，以确保质量、安全和伦理合规性。</mark>

"Human-on-the-loop" is a variation of this pattern where human experts define the overarching policy, and the AI then handles immediate actions to ensure compliance. Let's consider two examples:

<mark>「人机监督」（Human-on-the-loop，即人类在环路之上监督并设定策略）是该模式的另一种变体，其中人类专家负责定义总体策略，然后由 AI 处理即时操作以确保合规性。我们来看两个具体的例子：</mark>

- **Automated financial trading system**: In this scenario, a human financial expert sets the overarching investment strategy and rules. For instance, the human might define the policy as: "Maintain a portfolio of 70% tech stocks and 30% bonds, do not invest more than 5% in any single company, and automatically sell any stock that falls 10% below its purchase price." The AI then monitors the stock market in real-time, executing trades instantly when these predefined conditions are met. The AI is handling the immediate, high-speed actions based on the slower, more strategic policy set by the human operator.

  <mark><strong>自动化金融交易系统：</strong>在此场景中，人类金融专家设定总体投资策略和规则。例如，人类可能定义策略为：「保持 70% 科技股和 30% 债券的投资组合，对任何单一公司的投资不超过 5%，并在任何股票价格低于其购买价 10% 时自动卖出。」然后，AI 实时监控股票市场，在这些预定义条件满足时立即执行交易。AI 正在基于人类操作员设定的较慢、更具战略性的策略来处理即时、高速的行动。</mark>

- **Modern call center**: In this setup, a human manager establishes high-level policies for customer interactions. For instance, the manager might set rules such as "any call mentioning 'service outage' should be immediately routed to a technical support specialist," or "if a customer's tone of voice indicates high frustration, the system should offer to connect them directly to a human agent." The AI system then handles the initial customer interactions, listening to and interpreting their needs in real-time. It autonomously executes the manager's policies by instantly routing the calls or offering escalations without needing human intervention for each individual case. This allows the AI to manage the high volume of immediate actions according to the slower, strategic guidance provided by the human operator.

  <mark><strong>现代化呼叫中心：</strong>在此场景中，经理为客户互动建立高级策略。例如，经理可能设定规则，如「任何提到服务中断的电话应立即转接给技术支持专员」，或者「如果客户的语气表现出高度沮丧，系统应主动提出将他们转接给人工坐席。」然后，AI 系统会处理最初的客户互动，实时倾听并解释他们的需求。它通过即时转接电话或提供升级服务选项来自主执行经理的策略，而无需为每个个案都进行人工干预。这使得 AI 能够根据人类操作员提供的较慢、战略性的指导来管理大量的即时行动。</mark>

## Hands-On Code Example | <mark>实战代码示例</mark>

To demonstrate the Human-in-the-Loop pattern, an ADK agent can identify scenarios requiring human review and initiate an escalation process . This allows for human intervention in situations where the agent's autonomous decision-making capabilities are limited or when complex judgments are required. This is not an isolated feature; other popular frameworks have adopted similar capabilities. LangChain, for instance, also provides tools to implement these types of interactions.

<mark>为了演示人机协同模式，ADK 智能体可以识别需要人工审查的场景并发起上报流程。这允许在智能体的自主决策能力有限或需要复杂判断的情况下进行人工干预。这不是一个孤立的功能；其他流行的框架也采用了类似的功能。例如，LangChain 也提供了实现此类交互的工具。</mark>

```python
from google.adk.agents import Agent 
from google.adk.tools.tool_context import ToolContext 
from google.adk.callbacks import CallbackContext 
from google.adk.models.llm import LlmRequest 
from google.genai import types 
from typing import Optional 

# Placeholder for tools (replace with actual implementations if needed) 
# 占位符，用于替换实际的工具实现
def troubleshoot_issue(issue: str) -> dict:
   return {"status": "success", "report": f"Troubleshooting steps for {issue}."} 

def create_ticket(issue_type: str, details: str) -> dict:
   return {"status": "success", "ticket_id": "TICKET123"} 

def escalate_to_human(issue_type: str) -> dict:
   # This would typically transfer to a human queue in a real system
   # 模拟转交给专家处理
   return {"status": "success", "message": f"Escalated {issue_type} to a human specialist."} 

technical_support_agent = Agent(
   name="technical_support_specialist",
   model="gemini-2.0-flash-exp",
   instruction=""" You are a technical support specialist for our electronics company. FIRST, check if the user has a support history in state["customer_info"]["support_history"]. If they do, reference this history in your responses. For technical issues: 1. Use the troubleshoot_issue tool to analyze the problem. 2. Guide the user through basic troubleshooting steps. 3. If the issue persists, use create_ticket to log the issue. For complex issues beyond basic troubleshooting: 1. Use escalate_to_human to transfer to a human specialist. Maintain a professional but empathetic tone. Acknowledge the frustration technical issues can cause, while providing clear steps toward resolution. """,
   tools=[troubleshoot_issue, create_ticket, escalate_to_human]
)

def personalization_callback(
   callback_context: CallbackContext, llm_request: LlmRequest 
) -> Optional[LlmRequest]:
   """Adds personalization information to the LLM request."""
   # Get customer info from state
   # 获取客户信息
   customer_info = callback_context.state.get("customer_info")
   if customer_info:
      customer_name = customer_info.get("name", "valued customer")
      customer_tier = customer_info.get("tier", "standard")
      recent_purchases = customer_info.get("recent_purchases", [])
      personalization_note = (
         f"\nIMPORTANT PERSONALIZATION:\n"
         f"Customer Name: {customer_name}\n"
         f"Customer Tier: {customer_tier}\n"
      )
      if recent_purchases:
         personalization_note += f"Recent Purchases: {', '.join(recent_purchases)}\n"

      if llm_request.contents:
         # Add as a system message before the first content
         system_content = types.Content(
            role="system",
            parts=[types.Part(text=personalization_note)]
         )
         llm_request.contents.insert(0, system_content)
   return None # Return None to continue with the modified request 
```

This code offers a blueprint for creating a technical support agent using Google's ADK, designed around a HITL framework. The agent acts as an intelligent first line of support, configured with specific instructions and equipped with tools like `troubleshoot_issue`, `create_ticket`, and `escalate_to_human` to manage a complete support workflow. The escalation tool is a core part of the HITL design, ensuring complex or sensitive cases are passed to human specialists.

<mark>此代码提供了使用 Google 的 ADK 框架来创建一个围绕人机协同框架设计的技术支持智能体。该智能体作为智能的第一道防线，配置了具体指令，并配备了像 <code>troubleshoot_issue</code>、<code>create_ticket</code> 和 <code>escalate_to_human</code> 这样的工具来管理完整的支持工作流。上报工具是人机协同设计的核心部分，确保复杂或敏感的案例被转交给人类专家。</mark>

A key feature of this architecture is its capacity for deep personalization, achieved through a dedicated callback function. Before contacting the LLM, this function dynamically retrieves customer-specific data—such as their name, tier, and purchase history—from the agent's state. This context is then injected into the prompt as a system message, enabling the agent to provide highly tailored and informed responses that reference the user's history. By combining a structured workflow with essential human oversight and dynamic personalization, this code serves as a practical example of how the ADK facilitates the development of sophisticated and robust AI support solutions.

<mark>该架构的一个关键特性是通过专用回调函数实现的深度个性化能力。在使用大语言模型之前，该函数会从智能体的状态中动态检索客户特定数据，例如他们的姓名、等级和购买历史。然后，此上下文作为系统消息被注入到提示中，使智能体能够提供高度定制化和信息充分的、并引用用户历史的回复。通过将结构化工作流与必要的人类监督和动态个性化相结合，此代码展示了如何使用 ADK 开发复杂且强大的 AI 支持解决方案的实践范例。</mark>

## At a Glance | <mark>要点速览</mark>

**What**: AI systems, including advanced LLMs, often struggle with tasks that require nuanced judgment, ethical reasoning, or a deep understanding of complex, ambiguous contexts. Deploying fully autonomous AI in high-stakes environments carries significant risks, as errors can lead to severe safety, financial, or ethical consequences. These systems lack the inherent creativity and common-sense reasoning that humans possess. Consequently, relying solely on automation in critical decision-making processes is often imprudent and can undermine the system's overall effectiveness and trustworthiness.

<mark><strong>问题背景（What）：</strong>AI 系统，包括先进的大语言模型，在处理需要细致入微的判断、伦理推理或对复杂模糊上下文有深刻理解的任务时往往力不从心。在事关重大的场景使用完全自主的 AI 会带来巨大风险，因为错误可能导致严重的安全、财务或伦理后果。这些系统缺乏人类所拥有的内在创造力和常识性推理能力。因此，在关键决策过程中完全依赖自动化通常是不明智的，并且可能损害系统的整体有效性和可信度。</mark>

**Why**: The Human-in-the-Loop (HITL) pattern provides a standardized solution by strategically integrating human oversight into AI workflows. This agentic approach creates a symbiotic partnership where AI handles computational heavy-lifting and data processing, while humans provide critical validation, feedback, and intervention. By doing so, HITL ensures that AI actions align with human values and safety protocols. This collaborative framework not only mitigates the risks of full automation but also enhances the system's capabilities through continuous learning from human input. Ultimately, this leads to more robust, accurate, and ethical outcomes that neither human nor AI could achieve alone.

<mark><strong>模式价值（Why）：</strong>人机协同（HITL）模式通过将人类监督战略性地整合到 AI 工作流中，提供了一种标准化的解决方案。这种自主式方法创建了一种共生伙伴关系，其中 AI 处理计算密集型任务和数据处理，而人类则提供关键的验证、反馈和干预。通过这样做，人机协同模式确保 AI 的行动与人类价值观和安全协议保持一致。这种协作框架不仅降低了完全自动化的风险，而且通过不断从人类输入中学习来增强系统的能力。最终，这会带来更稳健、准确和合乎伦理的结果，这是人类或 AI 任何一方都无法单独实现的。</mark>

**Rule of thumb**: Use this pattern when deploying AI in domains where errors have significant safety, ethical, or financial consequences, such as in healthcare, finance, or autonomous systems. It is essential for tasks involving ambiguity and nuance that LLMs cannot reliably handle, like content moderation or complex customer support escalations. Employ HITL when the goal is to continuously improve an AI model with high-quality, human-labeled data or to refine generative AI outputs to meet specific quality standards.

<mark><strong>经验法则：</strong>当在医疗、金融或自动驾驶系统等错误会带来严重安全、伦理或财务后果的领域使用 AI 时，请使用此模式。对于涉及大语言模型（LLM）无法可靠处理的模糊性和细微差别的任务（如内容审核或复杂的客户支持上报），该模式至关重要。另外，当目标是利用高质量、人工标注的数据持续改进 AI 模型，或优化生成式 AI 的输出以满足特定质量标准时，也应采用人机协同模式。</mark>

**Visual summary** | <mark>**可视化总结：**</mark>

![Human in the loop design pattern](/images/chapter13_fig1.png)

Fig.1: Human in the loop design pattern

<mark>图 1：人机协同设计模式</mark>

## Key Takeaways | <mark>核心要点</mark>

Key takeaways include:

<mark>核心要点包括：</mark>

- Human-in-the-Loop (HITL) integrates human intelligence and judgment into AI workflows.

   <mark>人机协同（HITL）将人类的智能和判断力整合到 AI 工作流中。</mark>

- It's crucial for safety, ethics, and effectiveness in complex or high-stakes scenarios.

   <mark>它对于复杂或高风险场景下的安全性、伦理性和有效性至关重要。</mark>

- Key aspects include human oversight, intervention, feedback for learning, and decision augmentation.

   <mark>关键方面包括人类监督、干预、用于学习的反馈以及决策增强。</mark>

- Escalation policies are essential for agents to know when to hand off to a human.

   <mark>上报策略对于智能体了解何时应转交给人类至关重要。</mark>

- HITL allows for responsible AI deployment and continuous improvement.

   <mark>人机协同模式实现了负责任的 AI 部署并持续改进。</mark>

- The primary drawbacks of Human-in-the-Loop are its inherent lack of scalability, creating a trade-off between accuracy and volume, and its dependence on highly skilled domain experts for effective intervention.

   <mark>人机协同模式的主要缺点是其固有的可扩展性不足（在准确性和处理量之间造成了权衡）以及它对高技能领域专家进行有效干预的依赖。</mark>

- Its implementation presents operational challenges, including the need to train human operators for data generation and to address privacy concerns by anonymizing sensitive information.

   <mark>其实施带来了运营上的挑战，包括需要培训人类操作员以生成数据，以及需要通过匿名化敏感信息来解决隐私问题。</mark>

## Conclusion | <mark>结语</mark>

This chapter explored the vital Human-in-the-Loop (HITL) pattern, emphasizing its role in creating robust, safe, and ethical AI systems. We discussed how integrating human oversight, intervention, and feedback into agent workflows can significantly enhance their performance and trustworthiness, especially in complex and sensitive domains. The practical applications demonstrated HITL's widespread utility, from content moderation and medical diagnosis to autonomous driving and customer support. The conceptual code example provided a glimpse into how ADK can facilitate these human-agent interactions through escalation mechanisms. As AI capabilities continue to advance, HITL remains a cornerstone for responsible AI development, ensuring that human values and expertise remain central to intelligent system design.

<mark>本章探讨了至关重要的人机协同（HITL）模式，强调了其在创建稳健、安全和合乎伦理的 AI 系统中的作用。我们讨论了将人类监督、干预和反馈整合到智能体工作流中如何能显著提高其性能和可信度，尤其是在复杂和敏感的领域。实际应用展示了人机协同模式的广泛效用，从内容审核、医疗诊断到自动驾驶和客户支持。实战代码让我们了解 ADK 如何通过上报机制促进这些人机交互。随着 AI 能力的不断进步，人机协同模式仍然是负责任 AI 发展的基石，确保人类价值观和专业知识始终处于智能系统设计的核心。</mark>

## References | <mark>参考文献</mark>

1. A Survey of Human-in-the-loop for Machine Learning, Xingjiao Wu, Luwei Xiao, Yixuan Sun, Junhang Zhang, Tianlong Ma, Liang He, [https://arxiv.org/abs/2108.00941](https://arxiv.org/abs/2108.00941)

  <mark>《机器学习中的人机协同综述》，Xingjiao Wu, Luwei Xiao, Yixuan Sun, Junhang Zhang, Tianlong Ma, Liang He, [https://arxiv.org/abs/2108.00941](https://arxiv.org/abs/2108.00941)</mark>
