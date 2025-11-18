# Chapter 12: Exception Handling and Recovery | <mark>第 12 章：异常处理与恢复</mark>

For AI agents to operate reliably in diverse real-world environments, they must be able to manage unforeseen situations, errors, and malfunctions. Just as humans adapt to unexpected obstacles, intelligent agents need robust systems to detect problems, initiate recovery procedures, or at least ensure controlled failure. This essential requirement forms the basis of the Exception Handling and Recovery pattern.

<mark>为使 AI 智能体（AI Agent）能够在多样化的现实环境中可靠运行，它们必须具备管理突发状况、错误和故障的能力。正如人类能适应意外的障碍，智能体（Agent）也需要强大的系统来检测问题、启动恢复程序，或者至少确保可控的失败。这项基本要求构成了「异常处理与恢复」模式的基础。</mark>

This pattern focuses on developing exceptionally durable and resilient agents that can maintain uninterrupted functionality and operational integrity despite various difficulties and anomalies. It emphasizes the importance of both proactive preparation and reactive strategies to ensure continuous operation, even when facing challenges. This adaptability is critical for agents to function successfully in complex and unpredictable settings, ultimately boosting their overall effectiveness and trustworthiness.

<mark>该模式专注于开发具有出色的耐用性和韧性的智能体，使其在面对各种困难和异常时仍能保持不间断的功能和操作完整性。它强调主动准备和被动响应策略的重要性，以确保即使在面临挑战时也能持续运行。这种适应能力对于智能体在复杂且不可预测的环境中成功运行至关重要，最终能提升它们的整体效能和可信赖度。</mark>

The capacity to handle unexpected events ensures these AI systems are not only intelligent but also stable and reliable, which fosters greater confidence in their deployment and performance. Integrating comprehensive monitoring and diagnostic tools further strengthens an agent's ability to quickly identify and address issues, preventing potential disruptions and ensuring smoother operation in evolving conditions. These advanced systems are crucial for maintaining the integrity and efficiency of AI operations, reinforcing their ability to manage complexity and unpredictability.

<mark>处理意外事件的能力确保了 AI 系统能够智能且稳定可靠，从而让人们对其部署和性能抱有更大信心。集成全面的监控和诊断工具，进一步增强了智能体快速识别和解决问题的能力，防止潜在的中断，并确保在不断变化的条件中更平稳地运行。这些先进系统对于维护 AI 操作的完整性和效率至关重要，增强了它们管理复杂性和不可预测性的能力。</mark>

This pattern may sometimes be used with reflection. For example, if an initial attempt fails and raises an exception, a reflective process can analyze the failure and reattempt the task with a refined approach, such as an improved prompt, to resolve the error.

<mark>此模式有时可以与「反思」模式结合使用。例如，如果初次尝试失败并引发异常，反思过程可以分析该失败，并采用更完善的方法（如改进提示词）重新尝试任务，以解决错误。</mark>

# Exception Handling and Recovery Pattern Overview | <mark>异常处理与恢复模式概述</mark>

The Exception Handling and Recovery pattern addresses the need for AI agents to manage operational failures. This pattern involves anticipating potential issues, such as tool errors or service unavailability, and developing strategies to mitigate them. These strategies may include error logging, retries, fallbacks, graceful degradation, and notifications. Additionally, the pattern emphasizes recovery mechanisms like state rollback, diagnosis, self-correction, and escalation, to restore agents to stable operation. Implementing this pattern enhances the reliability and robustness of AI agents, allowing them to function in unpredictable environments. Examples of practical applications include chatbots managing database errors, trading bots handling financial errors, and smart home agents addressing device malfunctions. The pattern ensures that agents can continue to operate effectively despite encountering complexities and failures.

<mark>「异常处理与恢复」模式解决了 AI 智能体管理运行故障的需求。该模式涉及预测潜在问题（如工具错误或服务不可用）并制定缓解策略。这些策略可能包括错误日志记录、重试、回退、优雅降级和通知。此外，该模式还强调了恢复机制（如状态回滚、诊断、自我纠正和上报升级），以使智能体恢复到稳定运行状态。实施此模式可增强 AI 智能体的可靠性和鲁棒性，使其能够在不可预测的环境中运行。实际应用示例包括：聊天机器人管理数据库错误、交易机器人处理金融错误，以及智能家居智能体解决设备故障。该模式确保智能体在遇到复杂情况和失败时仍能继续有效运行。</mark>

![](/images/chapter12_fig1.png "Key Components")
Fig.1: Key components of exception handling and recovery for AI agents
<mark><strong>图 1：</strong> AI 智能体异常处理与恢复的关键组件</mark>

Error Detection: This involves meticulously identifying operational issues as they arise. This could manifest as invalid or malformed tool outputs, specific API errors such as 404 (Not Found) or 500 (Internal Server Error) codes, unusually long response times from services or APIs, or incoherent and nonsensical responses that deviate from expected formats. Additionally, monitoring by other agents or specialized monitoring systems might be implemented for more proactive anomaly detection, enabling the system to catch potential issues before they escalate.

<mark><strong>错误检测：</strong>这一环节需要细致地识别运行中出现的问题。具体可能表现为工具输出的无效或格式错误、特定 API 错误（如 404 Not Found 或 500 Internal Server Error 状态码）、服务或 API 响应时间异常延长，以及偏离预期格式的混乱无意义响应。此外，系统还可能部署其他智能体或专用监控系统进行更主动的异常监测，从而在潜在问题升级前及时捕捉它们。</mark>

Error Handling: Once an error is detected, a carefully thought-out response plan is essential. This includes recording error details meticulously in logs for later debugging and analysis (logging). Retrying the action or request, sometimes with slightly adjusted parameters, may be a viable strategy, especially for transient errors (retries). Utilizing alternative strategies or methods (fallbacks) can ensure that some functionality is maintained. Where complete recovery is not immediately possible, the agent can maintain partial functionality to provide at least some value (graceful degradation). Finally, alerting human operators or other agents might be crucial for situations that require human intervention or collaboration (notification).

<mark><strong>错误处理：</strong>一旦检测到错误，必须制定周密的响应计划。这包括在日志中详细记录错误详情以便后续调试和分析（日志记录）。重试操作或请求（有时会稍作调整参数）可能是一种可行的策略，特别是对于瞬时错误（重试）。
采用替代策略或方法（回退机制）可确保部分功能保持运行。当无法立即完全恢复时，智能体可维持部分功能以提供基础服务（优雅降级）。最后，对于需要人工干预的情况，向操作人员或其他智能体发出警报（通知机制）可能成为关键措施。</mark>

Recovery: This stage is about restoring the agent or system to a stable and operational state after an error. It could involve reversing recent changes or transactions to undo the effects of the error (state rollback). A thorough investigation into the cause of the error is vital for preventing recurrence. Adjusting the agent's plan, logic, or parameters through a self-correction mechanism or replanning process may be needed to avoid the same error in the future. In complex or severe cases, delegating the issue to a human operator or a higher-level system (escalation) might be the best course of action.

<mark><strong>恢复：</strong>该阶段旨在将智能体或系统恢复到稳定且可运行的状态。这可能涉及撤销最近的更改或事务，以消除错误的影响（状态回滚）。深入调查错误原因是防止再次发生的关键。可能需要通过自我纠正机制或重新规划过程，调整智能体的计划、逻辑或参数，以避免将来出现相同错误。在复杂或严重的情况下，将问题上报给人工操作员或更高级系统（升级处理）可能是最佳解决方案。</mark>

Implementation of this robust exception handling and recovery pattern can transform AI agents from fragile and unreliable systems into robust, dependable components capable of operating effectively and resiliently in challenging and highly unpredictable environments. This ensures that the agents maintain functionality, minimize downtime, and provide a seamless and reliable experience even when faced with unexpected issues.

<mark>实施这种健壮的异常处理和恢复模式，可以将 AI 智能体从脆弱不可靠的系统转变为强大、可靠的组件，能够在充满挑战和高度不可预测的环境中有效且有韧性地运行。这确保了智能体即使在面临意外状况时也能保持功能、最大限度地减少停机时间，并提供无缝、可靠的体验。</mark>

# Practical Applications & Use Cases | <mark>实际应用与用例</mark>

Exception Handling and Recovery is critical for any agent deployed in a real-world scenario where perfect conditions cannot be guaranteed.

<mark>对于部署在真实世界场景中的任何智能体而言，都无法保证有完美的条件，因此「异常处理与恢复」也至关重要。</mark>

- Customer Service Chatbots: If a chatbot tries to access a customer database and the database is temporarily down, it shouldn't crash. Instead, it should detect the API error, inform the user about the temporary issue, perhaps suggest trying again later, or escalate the query to a human agent.
    
- <mark><strong>客户服务聊天机器人：</strong>如果聊天机器人在尝试访问客户数据库时数据库暂时宕机，它不应直接崩溃。相反，它应该检测到 API 错误，告知用户临时问题，或许建议稍后再试，或将查询上报给人工客服。</mark>
    
- Automated Financial Trading: A trading bot attempting to execute a trade might encounter an "insufficient funds" error or a "market closed" error. It needs to handle these exceptions by logging the error, not repeatedly trying the same invalid trade, and potentially notifying the user or adjusting its strategy.
    
- <mark><strong>自动化金融交易：</strong>交易机器人在尝试执行交易时可能会遇到「资金不足」或「市场休市」的错误。它需要通过记录错误来处理这些异常，而不是重复尝试相同的无效交易，并可能通知用户或调整其策略。</mark>
    
- Smart Home Automation: An agent controlling smart lights might fail to turn on a light due to a network issue or a device malfunction. It should detect this failure, perhaps retry, and if still unsuccessful, notify the user that the light could not be turned on and suggest manual intervention.
    
- <mark><strong>智能家居自动化：</strong>控制智能灯具的智能体可能由于网络问题或设备故障而无法打开灯。它应该检测到此故障，或许进行重试，如果仍不成功，则通知用户灯无法打开，并建议手动干预。</mark>
    
- Data Processing Agents: An agent tasked with processing a batch of documents might encounter a corrupted file. It should skip the corrupted file, log the error, continue processing other files, and report the skipped files at the end rather than halting the entire process.
    
- <mark><strong>数据处理智能体：</strong>负责处理一批文档的智能体可能会遇到损坏的文件。它应该跳过损坏的文件，而不是中止整个过程，同时记录错误，继续处理其他文件，并在最后报告跳过的文件。</mark>
    
- Web Scraping Agents: When a web scraping agent encounters a CAPTCHA, a changed website structure, or a server error (e.g., 404 Not Found, 503 Service Unavailable), it needs to handle these gracefully. This could involve pausing, using a proxy, or reporting the specific URL that failed.
    
- <mark><strong>网页抓取智能体：</strong>当网页抓取智能体遇到 CAPTCHA、网站结构变更或服务器错误（例如，404 Not Found、503 Service Unavailable）时，它需要优雅地处理这些情况。这可能包括暂停、使用代理或报告失败的具体 URL。</mark>
    
- Robotics and Manufacturing: A robotic arm performing an assembly task might fail to pick up a component due to misalignment. It needs to detect this failure (e.g., via sensor feedback), attempt to readjust, retry the pickup, and if persistent, alert a human operator or switch to a different component.
    
- <mark><strong>机器人与制造：</strong>执行装配任务的机械臂可能由于未对准而抓取组件失败。它需要检测到此故障（例如，通过传感器反馈），尝试重新调整，重试抓取，如果仍然失败，则提醒人类操作员或切换到其他组件。</mark>
    

In short, this pattern is fundamental for building agents that are not only intelligent but also reliable, resilient, and user-friendly in the face of real-world complexities.

<mark>简而言之，要构建一个不仅智能，还能在面对现实世界的复杂性时，能够可靠、有韧性且用户友好的智能体，该模式就其基础。</mark>

# Hands-On Code Example (ADK) | <mark>使用 ADK 的实战代码</mark>

Exception handling and recovery are vital for system robustness and reliability. Consider, for instance, an agent's response to a failed tool call. Such failures can stem from incorrect tool input or issues with an external service that the tool depends on.

<mark>异常处理和恢复对于系统的鲁棒性和可靠性至关重要。例如，当智能体调用工具失败时，此类失败可能源于不正确的工具输入，或工具所依赖的外部服务出现问题。</mark>

```python
from google.adk.agents import Agent, SequentialAgent
from google.adk.tools import get_general_area_info, get_precise_location_info

# Agent 1: Tries the primary tool. Its focus is narrow and clear.
primary_handler = Agent(
    name="primary_handler",
    model="gemini-2.0-flash-exp",
    instruction="""
Your job is to get precise location information.
Use the get_precise_location_info tool with the user's provided address.
""",
    tools=[get_precise_location_info],
)

# Agent 2: Acts as the fallback handler, checking state to decide its action.
fallback_handler = Agent(
    name="fallback_handler",
    model="gemini-2.0-flash-exp",
    instruction="""
Check if the primary location lookup failed by looking at state["primary_location_failed"].
- If it is True, extract the city from the user's original query and use
  the get_general_area_info tool.
- If it is False, do nothing.
""",
    tools=[get_general_area_info],
)

# Agent 3: Presents the final result from the state.
response_agent = Agent(
    name="response_agent",
    model="gemini-2.0-flash-exp",
    instruction="""
Review the location information stored in state["location_result"].
Present this information clearly and concisely to the user.
If state["location_result"] does not exist or is empty, apologize that you
could not retrieve the location.
""",
)

# The SequentialAgent ensures the handlers run in a guaranteed order.
robust_location_agent = SequentialAgent(
    name="robust_location_agent",
    sub_agents=[primary_handler, fallback_handler, response_agent],
)
```

This code defines a robust location retrieval system using a ADK's SequentialAgent with three sub-agents. The primary\_handler is the first agent, attempting to get precise location information using the get\_precise\_location\_info tool. The fallback\_handler acts as a backup, checking if the primary lookup failed by inspecting a state variable. If the primary lookup failed, the fallback agent extracts the city from the user's query and uses the get\_general\_area\_info tool. The response\_agent is the final agent in the sequence. It reviews the location information stored in the state. This agent is designed to present the final result to the user. If no location information was found, it apologizes. The SequentialAgent ensures that these three agents execute in a predefined order. This structure allows for a layered approach to location information retrieval.

<mark>此代码使用 ADK 的 <code>SequentialAgent</code> 及三个子智能体（sub-agent）定义了一个强大的位置检索系统。<code>primary_handler</code> 是第一个智能体，尝试使用 <code>get_precise_location_info</code> 工具获取精确的位置信息。<code>fallback_handler</code> 充当备用智能体，通过检查状态变量来判断主要查询是否失败。如果主要查询失败，备用智能体将从用户查询中提取城市信息，并使用 <code>get_general_area_info</code> 工具。<code>response_agent</code> 是序列中的最后一个智能体。它负责审查存储在状态中的位置信息。该智能体将向用户清晰地呈现最终结果。如果未找到位置信息，它会向用户致歉。<code>SequentialAgent</code> 确保这三个智能体按预定顺序执行。这种结构为位置信息检索提供了一种分层的方法。</mark>

# At a Glance | <mark>要点速览</mark>

What: AI agents operating in real-world environments inevitably encounter unforeseen situations, errors, and system malfunctions. These disruptions can range from tool failures and network issues to invalid data, threatening the agent's ability to complete its tasks. Without a structured way to manage these problems, agents can be fragile, unreliable, and prone to complete failure when faced with unexpected hurdles. This unreliability makes it difficult to deploy them in critical or complex applications where consistent performance is essential.

<mark><strong>问题所在：</strong>在现实环境中运行的 AI 智能体不可避免地会遇到无法预见的情况、错误和系统故障。这些干扰范围很广，从工具故障、网络问题到无效数据，威胁着智能体完成任务的能力。如果没有结构化的方法来管理这些问题，智能体在面对意外障碍时可能会变得脆弱、不可靠，并容易完全失效。这种不可靠性，使得要将它们部署在对性能一致性要求极高的关键或复杂应用中变得困难。</mark>

Why: The Exception Handling and Recovery pattern provides a standardized solution for building robust and resilient AI agents. It equips them with the agentic capability to anticipate, manage, and recover from operational failures. The pattern involves proactive error detection, such as monitoring tool outputs and API responses, and reactive handling strategies like logging for diagnostics, retrying transient failures, or using fallback mechanisms. For more severe issues, it defines recovery protocols, including reverting to a stable state, self-correction by adjusting its plan, or escalating the problem to a human operator. This systematic approach ensures agents can maintain operational integrity, learn from failures, and function dependably in unpredictable settings.

<mark><strong>解决之道：</strong>「异常处理与恢复」模式为构建强大且有弹性的 AI 智能体提供了标准化的解决方案。它使智能体具备了预测、管理和从操作失败中恢复的智能体式（agentic）能力。该模式涉及主动错误检测（例如监控工具输出和 API 响应）和被动处理策略（例如用于诊断的日志记录、瞬时故障的重试或使用回退机制）。对于更严重的问题，它定义了恢复协议，包括恢复到稳定状态、通过调整计划进行自我纠正，或将问题上报给人类操作员。这种系统化的方法确保智能体能够保持操作完整性，从失败中学习，并在不可预测的环境中可靠地运行。</mark>

Rule of thumb: Use this pattern for any AI agent deployed in a dynamic, real-world environment where system failures, tool errors, network issues, or unpredictable inputs are possible and operational reliability is a key requirement.

<mark><strong>经验法则：</strong>任何部署在动态、真实世界环境且对操作可靠性要求极高的 AI 智能体，在这些场景中可能遭遇系统故障、工具错误、网络问题或不可预测的输入。</mark>

# Visual Summary | <mark>可视化总结</mark>

![](/images/chapter12_fig2.png "Exception handling pattern")
Fig.2: Exception handling pattern

<mark><strong>图 2：</strong>异常处理模式</mark>

# Key Takeaways | <mark>核心要点</mark>

Essential points to remember:

<mark>需要记住的关键点：</mark>

- Exception Handling and Recovery is essential for building robust and reliable Agents.
    
- <mark>「异常处理与恢复」对于构建强大且可靠的智能体至关重要。</mark>
    
- This pattern involves detecting errors, handling them gracefully, and implementing strategies to recover.
    
- <mark>此模式涉及检测错误、优雅地处理错误以及实施恢复策略。</mark>
    
- Error detection can involve validating tool outputs, checking API error codes, and using timeouts.
    
- <mark>错误检测涉及验证工具输出、检查 API 错误代码以及使用超时机制。</mark>
    
- Handling strategies include logging, retries, fallbacks, graceful degradation, and notifications.
    
- <mark>处理策略包括日志记录、重试、回退、优雅降级和通知。</mark>
    
- Recovery focuses on restoring stable operation through diagnosis, self-correction, or escalation.
    
- <mark>故障恢复专注于通过诊断、自我纠正或上报来恢复稳定运行。</mark>
    
- This pattern ensures agents can operate effectively even in unpredictable real-world environments.
    
- <mark>此模式确保智能体即使在不可预测的现实世界环境中也能有效运行。</mark>
    

# Conclusion | <mark>结语</mark>

This chapter explores the Exception Handling and Recovery pattern, which is essential for developing robust and dependable AI agents. This pattern addresses how AI agents can identify and manage unexpected issues, implement appropriate responses, and recover to a stable operational state. The chapter discusses various aspects of this pattern, including the detection of errors, the handling of these errors through mechanisms such as logging, retries, and fallbacks, and the strategies used to restore the agent or system to proper function. Practical applications of the Exception Handling and Recovery pattern are illustrated across several domains to demonstrate its relevance in handling real-world complexities and potential failures. These applications show how equipping AI agents with exception handling capabilities contributes to their reliability and adaptability in dynamic environments.

<mark>本章探讨了「异常处理与恢复」模式，这对于开发健壮且可靠的 AI 智能体至关重要。该模式阐述 AI 智能体如何识别和管理意外问题、生成适当响应并恢复到稳定操作状态。本章讨论了该模式的各个方面，包括错误检测、通过日志记录、重试和回退等机制来处理这些错误，以及使智能体或系统恢复正常功能的策略。通过几个领域的实际应用展示了「异常处理与恢复」模式在处理现实世界复杂性和潜在故障方面的相关性。这些应用表明，为 AI 智能体配备异常处理能力有助于提高在动态环境中的可靠性和适应性。</mark>

# References | <mark>参考文献</mark>

1. McConnell, S. (2004). Code Complete (2nd ed.). Microsoft Press.
    
<mark>1. McConnell, S. (2004). 《代码大全》（第 2 版）。微软出版社。</mark>

1. Shi, Y., Pei, H., Feng, L., Zhang, Y., & Yao, D. (2024). Towards Fault Tolerance in Multi-Agent Reinforcement Learning. arXiv preprint arXiv:2412.00534.

<mark>2. Shi, Y., Pei, H., Feng, L., Zhang, Y., & Yao, D. (2024). 迈向多智能体强化学习的容错性。arXiv 预印本 arXiv:2412.00534。</mark>

3. O'Neill, V. (2022). Improving Fault Tolerance and Reliability of Heterogeneous Multi-Agent IoT Systems Using Intelligence Transfer. Electronics, 11(17), 2724.
    
<mark>3. O'Neill, V. (2022). 利用智能迁移提高异构多智能体物联网系统的容错性和可靠性。Electronics, 11(17), 2724。</mark>
