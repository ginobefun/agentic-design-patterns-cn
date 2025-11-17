# Chapter 2: Routing | <mark>第二章：路由</mark>

## Routing Pattern Overview | <mark>路由模式概述</mark>

While sequential processing via prompt chaining is a foundational technique for executing deterministic, linear workflows with language models, its applicability is limited in scenarios requiring adaptive responses. Real-world agentic systems must often arbitrate between multiple potential actions based on contingent factors, such as the state of the environment, user input, or the outcome of a preceding operation. This capacity for dynamic decision-making, which governs the flow of control to different specialized functions, tools, or sub-processes, is achieved through a mechanism known as routing.

<mark>提示链虽然是执行确定性线性工作流的基础方法，但在需要自适应响应的场景下显得力不从心。现实场景中，智能体系统往往要根据环境状态、用户输入或上一步的执行结果等情境信息，从多个可选方案中选择合适的行动路径。路由（Routing）机制就是实现这种控制流分发的关键技术，它决定该将请求交给哪个功能模块、工具或子流程处理。</mark>

Routing introduces conditional logic into an agent's operational framework, enabling a shift from a fixed execution path to a model where the agent dynamically evaluates specific criteria to select from a set of possible subsequent actions. This allows for more flexible and context-aware system behavior.

<mark>路由为智能体引入了条件分支能力，让系统不再沿着固定流程执行，而是能根据实际情况动态选择最优的后续动作，从而实现更灵活、更懂上下文的智能行为。</mark>

For instance, an agent designed for customer inquiries, when equipped with a routing function, can first classify an incoming query to determine the user's intent. Based on this classification, it can then direct the query to a specialized agent for direct question-answering, a database retrieval tool for account information, or an escalation procedure for complex issues, rather than defaulting to a single, predetermined response pathway. Therefore, a more sophisticated agent using routing could:

<mark>以客户咨询智能体为例。集成路由功能后，系统会先识别用户的真实意图，然后将请求分发到对应的处理单元：简单问题交由问答智能体处理，账户查询则调用数据库检索工具，复杂问题则升级到人工处理，而非采用单一的预设响应路径。</mark>

<mark>因此，具有路由功能的智能体可以：</mark>

1. Analyze the user's query.

   <mark>分析用户的请求。</mark>

2. **Route** the query based on its *intent*:

    <mark>基于查询的意图将其<strong>路由</strong>到相应的处理路径：</mark>

   - If the intent is "check order status", route to a sub-agent or tool chain that interacts with the order database.

      <mark>「查订单」→ 调用订单查询子智能体或工具链</mark>

   - If the intent is "product information", route to a sub-agent or chain that searches the product catalog.

      <mark>「问产品」→ 调用产品目录检索子智能体或工具链</mark>

   - If the intent is "technical support", route to a different chain that accesses troubleshooting guides or escalates to a human.

      <mark>「求技术支持」→ 查阅故障排除手册或转人工</mark>

   - If the intent is unclear, route to a clarification sub-agent or prompt chain.

      <mark>「意图不明」→ 转到澄清子智能体追问细节</mark>

The core component of the Routing pattern is a mechanism that performs the evaluation and directs the flow. This mechanism can be implemented in several ways:

<mark>路由模式的核心在于评估与决策机制，即判断请求类型并确定执行路径。常见的实现方式包括：</mark>

**LLM-based Routing:** The language model itself can be prompted to analyze the input and output a specific identifier or instruction that indicates the next step or destination. For example, a prompt might ask the LLM to "Analyze the following user query and output only the category: 'Order Status', 'Product Info', 'Technical Support', or 'Other'." The agentic system then reads this output and directs the workflow accordingly.

<mark><strong>基于大语言模型的路由（LLM-based Routing）：</strong>通过提示词引导语言模型分析输入并输出特定的分类标识或指令，以指示下一步的执行目标。例如，提示词可以要求模型「分析以下用户查询并仅输出类别：订单状态、产品信息、技术支持或其他」。智能体系统读取该输出后，据此将工作流导向相应的处理路径。</mark>

**Embedding-based Routing:** The input query can be converted into a vector embedding (see RAG, Chapter 14). This embedding is then compared to embeddings representing different routes or capabilities. The query is routed to the route whose embedding is most similar. This is useful for semantic routing, where the decision is based on the meaning of the input rather than just keywords.

<mark><strong>向量路由（Embedding-based Routing）：</strong>将输入查询转换为向量嵌入（详见第 14 章 RAG），然后与代表不同路由或能力的嵌入向量进行比较，将查询路由到嵌入相似度最高的路径。此方法适用于语义路由场景，其决策基于输入的语义含义而非仅仅关键词匹配。例如，「帮我退款」和「订单有问题想取消」虽然措辞不同，但向量距离相近，因此都会被路由到退款处理流程。</mark>

**Rule-based Routing:** This involves using predefined rules or logic (e.g., if-else statements, switch cases) based on keywords, patterns, or structured data extracted from the input. This can be faster and more deterministic than LLM-based routing, but is less flexible for handling nuanced or novel inputs.

<mark><strong>规则路由（Rule-based Routing）：</strong>基于关键词、模式或从输入中提取的结构化数据，使用预定义规则或逻辑（如 if-else 语句、switch 语句）进行决策。此方法比大模型路由更快速且具有确定性，但在处理复杂语境或新颖输入时灵活性较低。</mark>

**Machine Learning Model-Based Routing:** it employs a discriminative model, such as a classifier, that has been specifically trained on a small corpus of labeled data to perform a routing task. While it shares conceptual similarities with embedding-based methods, its key characteristic is the supervised fine-tuning process, which adjusts the model's parameters to create a specialized routing function. This technique is distinct from LLM-based routing because the decision-making component is not a generative model executing a prompt at inference time. Instead, the routing logic is encoded within the fine-tuned model's learned weights. While LLMs may be used in a pre-processing step to generate synthetic data for augmenting the training set, they are not involved in the real-time routing decision itself.

<mark><strong>机器学习路由（Machine Learning Model-Based Routing）：</strong>采用判别式模型（如分类器），该模型在少量标注数据上经过专门训练以执行路由任务。虽然在概念上与向量路由方法有相似之处，但其关键特征在于监督微调过程，通过调整模型参数来创建专门的路由功能。此技术与大模型路由的区别在于，其决策组件并非在推理时执行提示词的生成式模型，而是将路由逻辑编码在微调后模型的学习权重中。虽然在预处理阶段可能使用大语言模型生成合成数据以扩充训练集，但实时路由决策本身并不涉及大模型。</mark>

Routing mechanisms can be implemented at multiple junctures within an agent's operational cycle. They can be applied at the outset to classify a primary task, at intermediate points within a processing chain to determine a subsequent action, or during a subroutine to select the most appropriate tool from a given set.

<mark>路由机制可在智能体运行周期的多个节点实施：可在初始阶段对主要任务进行分类，可在处理链的中间点确定后续操作，也可在子程序中从给定工具集中选择最合适的工具。</mark>

Computational frameworks such as LangChain, LangGraph, and Google's Agent Developer Kit (ADK) provide explicit constructs for defining and managing such conditional logic. With its state-based graph architecture, LangGraph is particularly well-suited for complex routing scenarios where decisions are contingent upon the accumulated state of the entire system. Similarly, Google's ADK provides foundational components for structuring an agent's capabilities and interaction models, which serve as the basis for implementing routing logic. Within the execution environments provided by these frameworks, developers define the possible operational paths and the functions or model-based evaluations that dictate the transitions between nodes in the computational graph.

<mark>LangChain、LangGraph 和 Google 智能体开发套件（ADK）等计算框架为定义和管理此类条件逻辑提供了明确的构造。凭借基于状态的图架构，LangGraph 特别适合复杂的路由场景，其中决策取决于整个系统的累积状态。类似地，Google ADK 提供了用于构建智能体能力和交互模型的基础组件，这些组件是实现路由逻辑的基础。在这些框架提供的执行环境中，开发人员可定义可能的操作路径，以及决定计算图中节点间转换的函数或基于模型的评估。</mark>

The implementation of routing enables a system to move beyond deterministic sequential processing. It facilitates the development of more adaptive execution flows that can respond dynamically and appropriately to a wider range of inputs and state changes.

<mark>路由的实现使系统能够超越确定性的顺序处理。它促进了更具适应性的执行流程的开发，能够动态且恰当地响应更广泛的输入和状态变化。</mark>

---

## Practical Applications & Use Cases | <mark>实际应用场景</mark>

The routing pattern is a critical control mechanism in the design of adaptive agentic systems, enabling them to dynamically alter their execution path in response to variable inputs and internal states. Its utility spans multiple domains by providing a necessary layer of conditional logic.

<mark>路由模式是自适应智能体系统设计中的关键控制机制，使系统能够根据可变输入和内部状态动态调整执行路径，从而提供必要的条件逻辑层，其应用范围涵盖多个领域。</mark>

In human-computer interaction, such as with virtual assistants or AI-driven tutors, routing is employed to interpret user intent. An initial analysis of a natural language query determines the most appropriate subsequent action, whether it is invoking a specific information retrieval tool, escalating to a human operator, or selecting the next module in a curriculum based on user performance. This allows the system to move beyond linear dialogue flows and respond contextually.

<mark>**人机交互**：在虚拟助手或 AI 驱动的辅导系统等场景中，路由用于解释用户意图。通过对自然语言查询的初步分析，系统可确定最合适的后续操作，无论是调用特定的信息检索工具、升级至人工操作员，还是根据用户表现选择课程中的下一个模块。这使系统能够超越线性对话流程，进行上下文相关的响应。</mark>

Within automated data and document processing pipelines, routing serves as a classification and distribution function. Incoming data, such as emails, support tickets, or API payloads, is analyzed based on content, metadata, or format. The system then directs each item to a corresponding workflow, such as a sales lead ingestion process, a specific data transformation function for JSON or CSV formats, or an urgent issue escalation path.

<mark>**数据处理流水线**：在自动化数据和文档处理流水线中，路由充当分类和分发功能。系统基于内容、元数据或格式对传入的数据（如电子邮件、支持工单或 API 负载）进行分析，然后将每项内容导向相应的工作流，例如销售线索录入流程、针对 JSON 或 CSV 格式的特定数据转换功能，或紧急问题升级路径。</mark>

In complex systems involving multiple specialized tools or agents, routing acts as a high-level dispatcher. A research system composed of distinct agents for searching, summarizing, and analyzing information would use a router to assign tasks to the most suitable agent based on the current objective. Similarly, an AI coding assistant uses routing to identify the programming language and user's intent—to debug, explain, or translate—before passing a code snippet to the correct specialized tool.

<mark>**多智能体协作**：在涉及多个专业工具或智能体的复杂系统中，路由充当高级调度器。由用于搜索、总结和分析信息的不同智能体组成的研究系统，会使用路由器根据当前目标将任务分配给最合适的智能体。类似地，AI 编码助手在将代码片段传递给正确的专业工具之前，会使用路由来识别编程语言和用户意图（调试、解释或翻译）。</mark>

Ultimately, routing provides the capacity for logical arbitration that is essential for creating functionally diverse and context-aware systems. It transforms an agent from a static executor of pre-defined sequences into a dynamic system that can make decisions about the most effective method for accomplishing a task under changing conditions.

<mark>归根结底，路由提供了创建功能多样化和上下文感知系统所必需的逻辑仲裁能力。它将智能体从预定义序列的静态执行器转变为能够在变化条件下决定完成任务最有效方法的动态系统。</mark>

---

## Hands-On Code Example (LangChain) | <mark>实战示例：LangChain 实现</mark>

Implementing routing in code involves defining the possible paths and the logic that decides which path to take. Frameworks like LangChain and LangGraph provide specific components and structures for this. LangGraph's state-based graph structure is particularly intuitive for visualizing and implementing routing logic.

<mark>在代码中实现路由涉及定义可能的路径以及决定选择哪条路径的逻辑。LangChain 和 LangGraph 等框架为此提供了特定的组件和结构。LangGraph 基于状态的图结构对于可视化和实现路由逻辑特别直观。</mark>

This code demonstrates a simple agent-like system using LangChain and Google's Generative AI. It sets up a "coordinator" that routes user requests to different simulated "sub-agent" handlers based on the request's intent (booking, information, or unclear). The system uses a language model to classify the request and then delegates it to the appropriate handler function, simulating a basic delegation pattern often seen in multi-agent architectures.

<mark>以下代码演示了使用 LangChain 和 Google 生成式 AI 构建的简单类智能体系统。它设置了一个「协调员」，根据请求的意图（预订、信息查询或不明确）将用户请求路由到不同的模拟「子智能体」处理器。系统使用语言模型对请求进行分类，然后将其委派给适当的处理函数，模拟了多智能体架构中常见的基本委派模式。</mark>

First, ensure you have the necessary libraries installed:

<mark>首先，确保你安装了必要的库：</mark>

```bash path=null start=null
pip install langchain langgraph google-cloud-aiplatform langchain-google-genai google-adk deprecated pydantic
```

You will also need to set up your environment with your API key for the language model you choose (e.g., OpenAI, Google Gemini, Anthropic).

<mark>你还需要在环境中设置所选语言模型（如 OpenAI、Google Gemini、Anthropic）的 API 密钥。</mark>

```python path=null start=null
# Copyright (c) 2025 Marco Fago
#
# This code is licensed under the MIT License.
# See the LICENSE file in the repository for the full license text.

from langchain_google_genai import ChatGoogleGenerativeAI
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_core.runnables import RunnablePassthrough, RunnableBranch

# --- Configuration ---
# Ensure your API key environment variable is set (e.g., GOOGLE_API_KEY)
# 确保你的 API 密钥环境变量已设置 (如 GOOGLE_API_KEY)
try:
    llm = ChatGoogleGenerativeAI(model="gemini-2.5-flash", temperature=0)
    print(f"Language model initialized: {llm.model}")
except Exception as e:
    print(f"Error initializing language model: {e}")
    llm = None

# --- Define Simulated Sub-Agent Handlers (equivalent to ADK sub_agents) ---
# --- 定义模拟的子智能体处理器 (等同于 ADK 中的 sub_agents) ---

def booking_handler(request: str) -> str:
    """Simulates the Booking Agent handling a request."""
    print("\n--- DELEGATING TO BOOKING HANDLER ---")
    return f"Booking Handler processed request: '{request}'. Result: Simulated booking action."

def info_handler(request: str) -> str:
    """Simulates the Info Agent handling a request."""
    print("\n--- DELEGATING TO INFO HANDLER ---")
    return f"Info Handler processed request: '{request}'. Result: Simulated information retrieval."

def unclear_handler(request: str) -> str:
    """Handles requests that couldn't be delegated."""
    print("\n--- HANDLING UNCLEAR REQUEST ---")
    return f"Coordinator could not delegate request: '{request}'. Please clarify."

# --- Define Coordinator Router Chain (equivalent to ADK coordinator's instruction) ---
# This chain decides which handler to delegate to.
# --- 定义协调员的路由链 (等同于 ADK 协调员的指令) ---
# 这个链负责决定将任务委派给哪个处理器。
coordinator_router_prompt = ChatPromptTemplate.from_messages([
    ("system", """Analyze the user's request and determine which specialist handler should process it.
     - If the request is related to booking flights or hotels, output 'booker'.
     - For all other general information questions, output 'info'.
     - If the request is unclear or doesn't fit either category, output 'unclear'.
     ONLY output one word: 'booker', 'info', or 'unclear'."""),
    ("user", "{request}")
])

if llm:
    coordinator_router_chain = coordinator_router_prompt | llm | StrOutputParser()

# --- Define the Delegation Logic (equivalent to ADK's Auto-Flow based on sub_agents) ---
# Use RunnableBranch to route based on the router chain's output.
# --- 定义委派逻辑 (等同于 ADK 基于 sub_agents 的自动流) ---
# 使用 RunnableBranch 根据路由链的输出进行路由。

# Define the branches for the RunnableBranch
# 为 RunnableBranch 定义分支
branches = {
    "booker": RunnablePassthrough.assign(output=lambda x: booking_handler(x['request']['request'])),
    "info": RunnablePassthrough.assign(output=lambda x: info_handler(x['request']['request'])),
    "unclear": RunnablePassthrough.assign(output=lambda x: unclear_handler(x['request']['request'])),
}

# Create the RunnableBranch. It takes the output of the router chain
# and routes the original input ('request') to the corresponding handler.
# 创建 RunnableBranch。它会接收路由链的输出，
# 并将原始输入 ('request') 路由到相应的处理器。
delegation_branch = RunnableBranch(
    (lambda x: x['decision'].strip() == 'booker', branches["booker"]), # Added .strip()
    (lambda x: x['decision'].strip() == 'info', branches["info"]),     # Added .strip()
    branches["unclear"] # Default branch for 'unclear' or any other output
)

# Combine the router chain and the delegation branch into a single runnable
# The router chain's output ('decision') is passed along with the original input ('request')
# to the delegation_branch.
# 将路由链和委派分支组合成一个可执行单元
# 路由链的输出 ('decision') 会连同原始输入 ('request') 一起
# 传递给 delegation_branch。
coordinator_agent = {
    "decision": coordinator_router_chain,
    "request": RunnablePassthrough()
} | delegation_branch | (lambda x: x['output']) # Extract the final output

# --- Example Usage ---
# --- 使用示例 ---
def main():
    if not llm:
        print("\nSkipping execution due to LLM initialization failure.")
        return

    print("--- Running with a booking request ---")
    request_a = "Book me a flight to London."
    result_a = coordinator_agent.invoke({"request": request_a})
    print(f"Final Result A: {result_a}")

    print("\n--- Running with an info request ---")
    request_b = "What is the capital of Italy?"
    result_b = coordinator_agent.invoke({"request": request_b})
    print(f"Final Result B: {result_b}")

    print("\n--- Running with an unclear request ---")
    request_c = "Tell me about quantum physics."
    result_c = coordinator_agent.invoke({"request": request_c})
    print(f"Final Result C: {result_c}")

if __name__ == "__main__":
    main()
```

译者注：[Colab 代码](https://colab.research.google.com/drive/1Yh3eUcvajJfgTFKhEQga6bJ3yyKodAmg) 已维护在[此处](/codes/Chapter-02-Routing-LangChain-Example.py)。

**运行输出（译者添加）：**

```text
Language model initialized: models/gemini-2.5-flash
--- Running with a booking request ---

--- DELEGATING TO BOOKING HANDLER ---
Final Result A: Booking Handler processed request: 'Book me a flight to London.'. Result: Simulated booking action.

--- Running with an info request ---

--- DELEGATING TO INFO HANDLER ---
Final Result B: Info Handler processed request: 'What is the capital of Italy?'. Result: Simulated information retrieval.

--- Running with an unclear request ---

--- DELEGATING TO INFO HANDLER ---
Final Result C: Info Handler processed request: 'Tell me about quantum physics.'. Result: Simulated information retrieval.
```

As mentioned, this Python code constructs a simple agent-like system using the LangChain library and Google's Generative AI model, specifically gemini-2.5-flash. In detail, It defines three simulated sub-agent handlers: booking_handler, info_handler, and unclear_handler, each designed to process specific types of requests.

<mark>如前所述，这段 Python 代码使用 LangChain 库和 Google 的 gemini-2.5-flash 模型构建了一个简单的类智能体系统。它定义了三个模拟的子智能体处理器：booking_handler、info_handler 和 unclear_handler，分别用于处理特定类型的请求。</mark>

A core component is the coordinator_router_chain, which utilizes a ChatPromptTemplate to instruct the language model to categorize incoming user requests into one of three categories: 'booker', 'info', or 'unclear'. The output of this router chain is then used by a RunnableBranch to delegate the original request to the corresponding handler function. The RunnableBranch checks the decision from the language model and directs the request data to either the booking_handler, info_handler, or unclear_handler. The coordinator_agent combines these components, first routing the request for a decision and then passing the request to the chosen handler. The final output is extracted from the handler's response.

<mark>核心组件是 coordinator_router_chain，它通过 ChatPromptTemplate 指示模型将用户请求分为三类：'booker'、'info' 或 'unclear'。随后 RunnableBranch 使用路由链的输出将原始请求委派给相应的处理函数。RunnableBranch 根据模型的判断，将请求数据发送到 booking_handler、info_handler 或 unclear_handler。coordinator_agent 将这些部分组合在一起：先进行路由决策，然后把请求转给选定的处理器，最后从处理器的响应中提取并返回最终结果。</mark>

The main function demonstrates the system's usage with three example requests, showcasing how different inputs are routed and processed by the simulated agents. Error handling for language model initialization is included to ensure robustness. The code structure mimics a basic multi-agent framework where a central coordinator delegates tasks to specialized agents based on intent.

<mark>主函数通过三个示例请求展示了系统的实际用法，说明不同的输入如何被路由并由各个模拟智能体处理。为了保证稳定性，代码还包含了语言模型初始化的错误处理。整体代码结构类似一个简化的多智能体框架：中央协调器根据意图把任务分配给各个专长不同的智能体。</mark>

---

## Hands-On Code Example (Google ADK) | <mark>实战示例：使用 Google ADK</mark>

The Agent Development Kit (ADK) is a framework for engineering agentic systems, providing a structured environment for defining an agent's capabilities and behaviours. In contrast to architectures based on explicit computational graphs, routing within the ADK paradigm is typically implemented by defining a discrete set of "tools" that represent the agent's functions. The selection of the appropriate tool in response to a user query is managed by the framework's internal logic, which leverages an underlying model to match user intent to the correct functional handler.

<mark>Google 智能体开发套件（ADK）是用于构建智能体系统的框架，提供了一个用于定义智能体能力与行为的结构化环境。与基于显式计算图的架构相比，ADK 中的路由通常是通过定义一组独立的「工具」来实现，这些工具对应智能体的各项功能。框架的内部逻辑会在用户发起查询时选择合适的工具，借助底层模型将用户意图匹配到相应的功能处理器。</mark>

This Python code demonstrates an example of an Agent Development Kit (ADK) application using Google's ADK library. It sets up a "Coordinator" agent that routes user requests to specialized sub-agents ("Booker" for bookings and "Info" for general information) based on defined instructions. The sub-agents then use specific tools to simulate handling the requests, showcasing a basic delegation pattern within an agent system.

<mark>这段 Python 代码演示了如何使用 Google ADK 构建应用。它设置了一个「协调员」智能体，根据预设指令将用户请求分发给两个专门的子智能体：负责预订的「Booker」和提供通用信息的「Info」。各子智能体再调用各自的工具来模拟处理请求，展示了智能体系统中基本的任务委派模式。</mark>

```python path=null start=null
# Copyright (c) 2025 Marco Fago
#
# This code is licensed under the MIT License.
# See the LICENSE file in the repository for the full license text.

import uuid
from typing import Dict, Any, Optional

from google.adk.agents import Agent
from google.adk.runners import InMemoryRunner
from google.adk.tools import FunctionTool
from google.genai import types
from google.adk.events import Event

# Colab 代码链接：https://colab.research.google.com/drive/10wxRlPyDJ70pPEtWWA3Aa3tjvfobrB3m

# 安装依赖
# pip install google-genai google-adk

# --- Define Tool Functions ---
# These functions simulate the actions of the specialist agents.
# --- 定义工具函数 ---
# 这些函数模拟了专业智能体的具体行动。

def booking_handler(request: str) -> str:
    """
    Handles booking requests for flights and hotels.
    Args:
        request: The user's request for a booking.
    Returns:
        A confirmation message that the booking was handled.
    """
    print("-------------------------- Booking Handler Called ----------------------------")
    return f"Booking action for '{request}' has been simulated."

def info_handler(request: str) -> str:
    """
    Handles general information requests.
    Args:
        request: The user's question.
    Returns:
        A message indicating the information request was handled.
    """
    print("-------------------------- Info Handler Called ----------------------------")
    return f"Information request for '{request}'. Result: Simulated information retrieval."

def unclear_handler(request: str) -> str:
    """Handles requests that couldn't be delegated."""
    return f"Coordinator could not delegate request: '{request}'. Please clarify."

# --- Create Tools from Functions ---
# --- 从函数创建工具 ---
booking_tool = FunctionTool(booking_handler)
info_tool = FunctionTool(info_handler)

# Define specialized sub-agents equipped with their respective tools
# --- 定义配备了各自工具的专业子智能体 ---
booking_agent = Agent(
    name="Booker",
    model="gemini-2.0-flash",
    description="A specialized agent that handles all flight and hotel booking requests by calling the booking tool.",
    tools=[booking_tool]
)

info_agent = Agent(
    name="Info",
    model="gemini-2.0-flash",
    description="A specialized agent that provides general information and answers user questions by calling the info tool.",
    tools=[info_tool]
)

# Define the parent agent with explicit delegation instructions
# --- 定义带有明确委派指令的父智能体 ---
coordinator = Agent(
    name="Coordinator",
    model="gemini-2.0-flash",
    instruction=(
        "You are the main coordinator. Your only task is to analyze incoming user requests "
        "and delegate them to the appropriate specialist agent. Do not try to answer the user directly.\n"
        "- For any requests related to booking flights or hotels, delegate to the 'Booker' agent.\n"
        "- For all other general information questions, delegate to the 'Info' agent."
    ),
    description="A coordinator that routes user requests to the correct specialist agent.",
    # The presence of sub_agents enables LLM-driven delegation (Auto-Flow) by default.
    # 定义了 sub_agents 默认就会启用由大语言模型驱动的委派。
    sub_agents=[booking_agent, info_agent]
)

# --- Execution Logic ---
# --- 执行逻辑 ---
def run_coordinator(runner: InMemoryRunner, request: str):
    """Runs the coordinator agent with a given request and delegates."""
    """用给定的请求运行协调员智能体并进行委派。"""
    print(f"\n--- Running Coordinator with request: '{request}' ---")
    final_result = ""
    try:
        user_id = "user_123"
        session_id = str(uuid.uuid4())
        runner.session_service.create_session(
            app_name=runner.app_name, user_id=user_id, session_id=session_id
        )

        for event in runner.run(
            user_id=user_id,
            session_id=session_id,
            new_message=types.Content(
                role='user',
                parts=[types.Part(text=request)]
            ),
        ):
            if event.is_final_response() and event.content:
                # Try to get text directly from event.content to avoid iterating parts
                if hasattr(event.content, 'text') and event.content.text:
                     final_result = event.content.text
                elif event.content.parts:
                    # Fallback: Iterate through parts and extract text (might trigger warning)
                    text_parts = [part.text for part in event.content.parts if part.text]
                    final_result = "".join(text_parts)
                # Assuming the loop should break after the final response
                break

        print(f"Coordinator Final Response: {final_result}")
        return final_result
    except Exception as e:
        print(f"An error occurred while processing your request: {e}")
        return f"An error occurred while processing your request: {e}"

def main():
    """Main function to run the ADK example."""
    """运行 ADK 示例的主函数。"""
    print("--- Google ADK Routing Example (ADK Auto-Flow Style) ---")
    print("Note: This requires Google ADK installed and authenticated.")

    runner = InMemoryRunner(coordinator)
    # Example Usage
    # 使用示例
    result_a = run_coordinator(runner, "Book me a hotel in Paris.")
    print(f"Final Output A: {result_a}")
    result_b = run_coordinator(runner, "What is the highest mountain in the world?")
    print(f"Final Output B: {result_b}")
    result_c = run_coordinator(runner, "Tell me a random fact.") # Should go to Info
    print(f"Final Output C: {result_c}")
    result_d = run_coordinator(runner, "Find flights to Tokyo next month.") # Should go to Booker
    print(f"Final Output D: {result_d}")


if __name__ == "__main__":
    main()
```

译者注：[Colab 代码](https://colab.research.google.com/drive/10wxRlPyDJ70pPEtWWA3Aa3tjvfobrB3m) 已维护在[此处](/codes/Chapter-02-Routing-ADK-Example.py)。

This script consists of a main Coordinator agent and two specialized sub_agents: Booker and Info. Each specialized agent is equipped with a FunctionTool that wraps a Python function simulating an action. The booking_handler function simulates handling flight and hotel bookings, while the info_handler function simulates retrieving general information. The unclear_handler is included as a fallback for requests the coordinator cannot delegate, although the current coordinator logic doesn't explicitly use it for delegation failure in the main run_coordinator function.

<mark>该脚本包含一个主协调员和两个专职子智能体：Booker 和 Info。每个子智能体都配有一个 FunctionTool，用于封装模拟操作的 Python 函数。booking_handler 用来模拟处理航班和酒店预订，info_handler 用来模拟查询信息。脚本中还包含一个 unclear_handler，作为协调器在无法委派请求时的备用处理，不过在当前的 run_coordinator 主流程中，并没有明确使用它来处理委派失败的情况。</mark>

The Coordinator agent's primary role, as defined in its instruction, is to analyze incoming user messages and delegate them to either the Booker or Info agent. This delegation is handled automatically by the ADK's Auto-Flow mechanism because the Coordinator has sub_agents defined. The run_coordinator function sets up an InMemoryRunner, creates a user and session ID, and then uses the runner to process the user's request through the coordinator agent. The runner.run method processes the request and yields events, and the code extracts the final response text from the event.content.

<mark>协调员的主要职责是分析收到的用户消息，并将其分派给 Booker 或 Info 子智能体。因为协调员定义了子智能体，ADK 的流程会自动完成这种分派。run_coordinator 函数会初始化一个 InMemoryRunner，创建用户和会话 ID，然后用该 runner 将用户请求提交给协调员来处理。runner.run 方法会处理请求并生成事件，代码从这些事件的 event.content 中提取最终的响应文本。</mark>

The main function demonstrates the system's usage by running the coordinator with different requests, showcasing how it delegates booking requests to the Booker and information requests to the Info agent.

<mark>主函数通过用不同的请求来演示，展示了协调员如何把预订类请求交给负责预订的子智能体，把查询类信息请求交给信息查询子智能体。</mark>

---

## At a Glance | <mark>要点速览</mark>

**What:** Agentic systems must often respond to a wide variety of inputs and situations that cannot be handled by a single, linear process. A simple sequential workflow lacks the ability to make decisions based on context. Without a mechanism to choose the correct tool or sub-process for a specific task, the system remains rigid and non-adaptive. This limitation makes it difficult to build sophisticated applications that can manage the complexity and variability of real-world user requests.

<mark><strong>问题所在：</strong>智能体系统往往需要应对各种各样的输入和情境，单一的线性流程无法满足这一需求。简单的顺序工作流缺乏基于上下文做出决策的能力。如果没有为特定任务选择正确工具或子流程的机制，系统将保持僵化且缺乏适应性。这一局限性使得构建能够管理真实世界用户请求的复杂性和可变性的成熟应用变得困难。</mark>

**Why:** The Routing pattern provides a standardized solution by introducing conditional logic into an agent's operational framework. It enables the system to first analyze an incoming query to determine its intent or nature. Based on this analysis, the agent dynamically directs the flow of control to the most appropriate specialized tool, function, or sub-agent. This decision can be driven by various methods, including prompting LLMs, applying predefined rules, or using embedding-based semantic similarity. Ultimately, routing transforms a static, predetermined execution path into a flexible and context-aware workflow capable of selecting the best possible action.

<mark><strong>解决之道：</strong>路由模式通过在智能体操作框架中引入条件逻辑，提供了标准化解决方案。它使系统能够首先分析传入查询以确定其意图或性质，然后基于此分析，智能体动态地将控制流导向最合适的专业工具、函数或子智能体。这一决策可由多种方法驱动，包括提示大语言模型、应用预定义规则或使用基于嵌入的语义相似度。最终，路由将静态的预定执行路径转变为能够选择最佳可能操作的灵活且具上下文感知的工作流。</mark>

**Rule of Thumb:** Use the Routing pattern when an agent must decide between multiple distinct workflows, tools, or sub-agents based on the user's input or the current state. It is essential for applications that need to triage or classify incoming requests to handle different types of tasks, such as a customer support bot distinguishing between sales inquiries, technical support, and account management questions.

<mark><strong>经验法则：</strong>当智能体必须根据用户输入或当前状态在多个不同的工作流、工具或子智能体之间做出选择时，应使用路由模式。此模式对于需要对传入请求进行分类或分派以处理不同类型任务的应用至关重要，例如客户支持机器人需要区分销售咨询、技术支持和账户管理问题，并将每种类型的请求路由到相应的处理模块。</mark>

**Visual summary** | <mark>可视化总结</mark>

![可视化总结](/images/chapter02_fig1.jpg)

Fig.1: Router pattern, using an LLM as a Router

<mark>路由模式 —— 利用一个大语言模型作为路由器</mark>

---

## Key Takeaways | <mark>核心要点</mark>

- Routing enables agents to make dynamic decisions about the next step in a workflow based on conditions.

   <mark>路由使智能体能够根据条件，动态决定工作流的下一步。</mark>

- It allows agents to handle diverse inputs and adapt their behavior, moving beyond linear execution.

   <mark>它允许智能体处理多样化的输入并适应其行为，超越了线性的执行方式。</mark>

- Routing logic can be implemented using LLMs, rule-based systems, or embedding similarity.

   <mark>路由逻辑可以使用大语言模型、基于规则的系统或嵌入相似度来实现。</mark>

- Frameworks like LangGraph and Google ADK provide structured ways to define and manage routing within agent workflows, albeit with different architectural approaches.

   <mark>像 LangGraph 和 Google ADK 这样的框架，为在智能体工作流中定义和管理路由提供了结构化的方法，尽管它们的架构方式有所不同。</mark>

---

## Conclusion | <mark>结语</mark>

The Routing pattern is a critical step in building truly dynamic and responsive agentic systems. By implementing routing, we move beyond simple, linear execution flows and empower our agents to make intelligent decisions about how to process information, respond to user input, and utilize available tools or sub-agents.

<mark>路由模式是构建真正动态且能响应变化的智能体系统的关键环节。通过实施路由，系统得以超越简单的线性执行流程，使智能体能够就如何处理信息、响应用户输入以及使用可用工具或子智能体做出智能决策。</mark>

We've seen how routing can be applied in various domains, from customer service chatbots to complex data processing pipelines. The ability to analyze input and conditionally direct the workflow is fundamental to creating agents that can handle the inherent variability of real-world tasks.

<mark>路由在各个领域都有应用，从客户服务聊天机器人到复杂的数据处理流水线。分析输入并根据条件引导工作流的能力，是创建能够处理真实世界任务固有可变性的智能体的基础。</mark>

The code examples using LangChain and Google ADK demonstrate two different, yet effective, approaches to implementing routing. LangGraph's graph-based structure provides a visual and explicit way to define states and transitions, making it ideal for complex, multi-step workflows with intricate routing logic. Google ADK, on the other hand, often focuses on defining distinct capabilities (Tools) and relies on the framework's ability to route user requests to the appropriate tool handler, which can be simpler for agents with a well-defined set of discrete actions.

<mark>使用 LangChain 和 Google ADK 的代码示例展示了两种不同但都有效的路由实现方法。LangGraph 基于图的结构提供了一种可视化和明确的方式来定义状态与转换，非常适合具有复杂路由逻辑的多步骤工作流。另一方面，Google ADK 通常侧重于定义独立的能力（工具），并依赖框架将用户请求路由到适当的工具处理器的能力，这对于具有明确定义的离散操作集的智能体来说可能更简单。</mark>

Mastering the Routing pattern is essential for building agents that can intelligently navigate different scenarios and provide tailored responses or actions based on context. It's a key component in creating versatile and robust agentic applications.

<mark>掌握路由模式对于构建能根据不同场景和上下文智能选择响应或执行操作的智能体至关重要，是打造灵活可靠的智能体应用的核心要素。</mark>

---

## References | <mark>参考文献</mark>

1. LangGraph Documentation: [https://www.langchain.com/](https://www.langchain.com/)

   <mark>LangGraph 官网：[https://www.langchain.com/](https://www.langchain.com/)</mark>

2. Google Agent Developer Kit Documentation: [https://google.github.io/adk-docs/](https://google.github.io/adk-docs/)

   <mark>谷歌智能体开发套件官方文档：[https://google.github.io/adk-docs/](https://google.github.io/adk-docs/)</mark>
