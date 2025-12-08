# Chapter 8: Memory Management | <mark>第 8 章：记忆管理</mark>

Effective memory management is crucial for intelligent agents to retain information. Agents require different types of memory, much like humans, to operate efficiently. This chapter delves into memory management, specifically addressing the immediate (short-term) and persistent (long-term) memory requirements of agents.

<mark>有效的记忆管理是智能体保留信息的关键。与人类类似，智能体需要多种类型的记忆才能高效运行。本章将深入探讨记忆管理，重点聚焦于智能体的即时（短期）和持久（长期）记忆需求。</mark>

In agent systems, memory refers to an agent's ability to retain and utilize information from past interactions, observations, and learning experiences. This capability allows agents to make informed decisions, maintain conversational context, and improve over time. Agent memory is generally categorized into two main types:

<mark>在智能体系统中，<strong>记忆</strong> 指智能体从过往交互、观察和学习经验中保留并利用信息的能力。这一能力使智能体能够做出明智决策、维持对话上下文，并持续改进。智能体记忆通常可分为两大主要类型：</mark>

● **Short-Term Memory (Contextual Memory)**: Similar to working memory, this holds information currently being processed or recently accessed. For agents using large language models (LLMs), short-term memory primarily exists within the context window. This window contains recent messages, agent replies, tool usage results, and agent reflections from the current interaction, all of which inform the LLM's subsequent responses and actions. The context window has a limited capacity, restricting the amount of recent information an agent can directly access. Efficient short-term memory management involves keeping the most relevant information within this limited space, possibly through techniques like summarizing older conversation segments or emphasizing key details. The advent of models with 'long context' windows simply expands the size of this short-term memory, allowing more information to be held within a single interaction. However, this context is still ephemeral and is lost once the session concludes, and it can be costly and inefficient to process every time. Consequently, agents require separate memory types to achieve true persistence, recall information from past interactions, and build a lasting knowledge base.

● <mark><strong>短期记忆（上下文记忆）</strong>：类似于工作记忆，存储当前正在处理或近期访问的信息。</mark>

<mark>对于基于大语言模型的智能体，短期记忆主要存在于上下文窗口内。该窗口包含最近的对话消息、智能体回复、工具调用结果以及当前交互中的反思内容，这些信息共同为后续的响应和决策提供上下文支撑。</mark>

<mark>上下文窗口的容量有限，限制了智能体可直接访问的近期信息范围。高效的短期记忆管理需要在有限空间内选择性地保留最相关信息，可通过总结旧对话片段或强调关键细节等技术实现。</mark>

<mark>具有「长上下文」窗口的模型虽然扩大了短期记忆容量，允许在单次交互中保存更多信息，但这种上下文仍然是短暂的，会话结束后即丢失，且每次处理成本高昂、效率较低。</mark>

<mark>因此，智能体需要不同类型的记忆来实现真正的持久化，从过往交互中回忆信息并构建持久的知识库。</mark>

● **Long-Term Memory (Persistent Memory)**: This acts as a repository for information agents need to retain across various interactions, tasks, or extended periods, akin to long-term knowledge bases. Data is typically stored outside the agent's immediate processing environment, often in databases, knowledge graphs, or vector databases. In vector databases, information is converted into numerical vectors and stored, enabling agents to retrieve data based on semantic similarity rather than exact keyword matches, a process known as semantic search. When an agent needs information from long-term memory, it queries the external storage, retrieves relevant data, and integrates it into the short-term context for immediate use, thus combining prior knowledge with the current interaction.

● <mark><strong>长期记忆（持久记忆）</strong>：充当一个长期知识库，用于存储智能体在各种交互场景、任务执行或长时间跨度内需要保留的信息。</mark>

<mark>数据通常存储在智能体的运行时环境之外，常见于数据库、知识图谱或向量数据库中。在向量数据库中，信息被转换为数值向量并存储，使智能体能够基于语义相似性而非精确关键词匹配来检索数据，这个过程被称为语义搜索。</mark>

<mark>当智能体需要长期记忆中的信息时，会查询外部存储、检索相关数据并将其整合到短期上下文中以便随时使用，从而将先验知识与当前交互信息相结合。</mark>

---

## Practical Applications & Use Cases | <mark>实际应用场景</mark>

Memory management is vital for agents to track information and perform intelligently over time. This is essential for agents to surpass basic question-answering capabilities. Applications include:

<mark>记忆管理对于智能体至关重要，使其能够持续跟踪信息并在长时间运行中表现出智能行为。这一能力是智能体超越基础问答、展现高级智能的关键。主要应用场景包括：</mark>

● **Chatbots and Conversational AI**: Maintaining conversation flow relies on short-term memory. Chatbots require remembering prior user inputs to provide coherent responses. Long-term memory enables chatbots to recall user preferences, past issues, or prior discussions, offering personalized and continuous interactions.

● <mark><strong>聊天机器人和对话式 AI：</strong> 维持对话流程依赖于短期记忆。聊天机器人需要记住先前的用户输入才能提供连贯的回答。长期记忆使聊天机器人能够调取用户偏好、过往问题或过往对话记录，从而提供个性化且连续一致的交互体验。</mark>

● **Task-Oriented Agents**: Agents managing multi-step tasks need short-term memory to track previous steps, current progress, and overall goals. This information might reside in the task's context or temporary storage. Long-term memory is crucial for accessing specific user-related data not in the immediate context.

● <mark><strong>任务导向型智能体：</strong> 处理多步骤任务的智能体需要借助短期记忆来跟踪已完成步骤、当前进度状态及总体目标。这些信息通常存储在任务上下文或临时缓存中。长期记忆对于访问非即时上下文的用户特定数据至关重要。</mark>

● **Personalized Experiences**: Agents offering tailored interactions utilize long-term memory to store and retrieve user preferences, past behaviors, and personal information. This allows agents to adapt their responses and suggestions.

● <mark><strong>个性化体验服务：</strong> 提供定制化交互的智能体利用长期记忆系统来存储和调用用户偏好、历史行为模式及个人信息。这种能力使得智能体能够动态调整其响应策略和建议内容。</mark>

● **Learning and Improvement**: Agents can refine their performance by learning from past interactions. Successful strategies, mistakes, and new information are stored in long-term memory, facilitating future adaptations. Reinforcement learning agents store learned strategies or knowledge in this way.

● <mark><strong>学习与性能优化：</strong> 智能体通过从历史交互中学习来持续改进自身的性能表现。成功的策略方案、错误经验以及新获取的知识都被存储在长期记忆中，为未来的自适应优化提供支持。强化学习智能体正是通过这种方式保存习得的策略和知识体系。</mark>

● **Information Retrieval (RAG)**: Agents designed for answering questions access a knowledge base, their long-term memory, often implemented within Retrieval Augmented Generation (RAG). The agent retrieves relevant documents or data to inform its responses.

● <mark><strong>信息检索（RAG）：</strong> 为问答场景设计的智能体需要访问知识库（即长期记忆），这一功能通常在检索增强生成（RAG）框架中实现。智能体通过检索相关文档和数据资源来支撑其回答的准确性和完整性。</mark>

● **Autonomous Systems**: Robots or self-driving cars require memory for maps, routes, object locations, and learned behaviors. This involves short-term memory for immediate surroundings and long-term memory for general environmental knowledge.

● <mark><strong>自主控制系统：</strong> 机器人或自动驾驶车辆需要记忆系统来存储地图信息、导航路线、物体位置以及学习获得的行为模式。这包括用于实时环境感知的短期记忆和用于通用环境知识存储的长期记忆。</mark>

Memory enables agents to maintain history, learn, personalize interactions, and manage complex, time-dependent problems.

<mark>记忆能力使智能体能够维护历史记录、实现持续学习、提供个性化交互，并有效处理复杂的时序依赖性问题。</mark>

---

## Hands-On Code: Memory Management in Google Agent Developer Kit (ADK) | <mark>实战代码：Google ADK 中的记忆管理</mark>

The Google Agent Developer Kit (ADK) offers a structured method for managing context and memory, including components for practical application. A solid grasp of ADK's Session, State, and Memory is vital for building agents that need to retain information.

<mark>Google ADK 提供了一套结构化的上下文与记忆管理方法，包含多个可直接应用于实际场景的组件。深入理解 ADK 中会话（Session）、状态（State）和记忆（Memory）这三个核心概念，对于构建需要信息持久化能力的智能体至关重要。</mark>

Just as in human interactions, agents require the ability to recall previous exchanges to conduct coherent and natural conversations. ADK simplifies context management through three core concepts and their associated services.

<mark>正如人类交流需要记忆，智能体同样需要具备回忆历史对话的能力，才能进行连贯自然的交流。ADK 通过三个核心概念及其配套服务，简化了上下文管理的复杂性。</mark>

Every interaction with an agent can be considered a unique conversation thread. Agents might need to access data from earlier interactions. ADK structures this as follows:

<mark>每次与智能体的交互都可视为一个独立的对话，而智能体往往需要访问历史交互数据。ADK 通过以下架构组织这些信息：</mark>

● **Session**: An individual chat thread that logs messages and actions (Events) for that specific interaction, also storing temporary data (State) relevant to that conversation.

● <mark><strong>Session（会话）：</strong> 一个独立的聊天会话，记录特定交互过程中的消息和执行动作（事件），同时存储与该对话相关的临时数据（状态）。</mark>

● **State (session.state)**: Data stored within a Session, containing information relevant only to the current, active chat thread.

● <mark><strong>State（状态，<code>session.state</code>）：</strong> 存储在会话内部的数据，仅包含与当前活跃聊天会话相关的上下文信息。</mark>

● **Memory**: A searchable repository of information sourced from various past chats or external sources, serving as a resource for data retrieval beyond the immediate conversation.

● <mark><strong>Memory（记忆）：</strong> 一个可检索的信息知识库，数据来源包括历史聊天记录和外部数据源，为超越当前对话范围的数据检索提供支持。</mark>

ADK provides dedicated services for managing critical components essential for building complex, stateful, and context-aware agents. The SessionService manages chat threads (Session objects) by handling their initiation, recording, and termination, while the MemoryService oversees the storage and retrieval of long-term knowledge (Memory).

<mark>ADK 提供专门的服务组件，它们是构建有状态、上下文感知的智能体的关键要素。<code>SessionService</code> 负责管理聊天会话（<code>Session</code> 对象），处理会话的创建、记录和终止，而 <code>MemoryService</code> 负责长期知识（<code>Memory</code>）的存储与检索。</mark>

Both the SessionService and MemoryService offer various configuration options, allowing users to choose storage methods based on application needs. In-memory options are available for testing purposes, though data will not persist across restarts. For persistent storage and scalability, ADK also supports database and cloud-based services.

<mark><code>SessionService</code> 和 <code>MemoryService</code> 均提供多种配置选项，允许开发者根据应用需求选择合适的存储方案。比如内存存储适用于测试环境，数据不会持久化，在重启后会丢失。对于需要持久化存储和可扩展性等需求，ADK 支持使用数据库和云服务。</mark>

---

## Session: Keeping Track of Each Chat | <mark>Session：跟踪每次聊天</mark>

A Session object in ADK is designed to track and manage individual chat threads. Upon initiation of a conversation with an agent, the SessionService generates a Session object, represented as `google.adk.sessions.Session`. This object encapsulates all data relevant to a specific conversation thread, including unique identifiers (id, app_name, user_id), a chronological record of events as Event objects, a storage area for session-specific temporary data known as state, and a timestamp indicating the last update (last_update_time). Developers typically interact with Session objects indirectly through the SessionService. The SessionService is responsible for managing the lifecycle of conversation sessions, which includes initiating new sessions, resuming previous sessions, recording session activity (including state updates), identifying active sessions, and managing the removal of session data. The ADK provides several SessionService implementations with varying storage mechanisms for session history and temporary data, such as the InMemorySessionService, which is suitable for testing but does not provide data persistence across application restarts.

<mark>ADK 中的 <code>Session</code> 对象用于跟踪和管理独立的聊天会话。</mark>

<mark>当用户与智能体开始对话时，<code>SessionService</code> 会生成一个 <code>Session</code> 对象（<code>google.adk.sessions.Session</code>）。该对象封装特定对话线程的所有相关数据，包括唯一标识符（<code>id</code>、<code>app_name</code>、<code>user_id</code>）、按时间顺序记录的事件对象、用于会话临时数据（也称为状态）的存储区域，以及指示最后更新时间的时间戳（<code>last_update_time</code>）。</mark>

<mark>开发者通常通过 <code>SessionService</code> 与 <code>Session</code> 对象交互。<code>SessionService</code> 负责管理对话会话的生命周期，包括启动新会话、恢复先前会话、记录会话活动（含状态更新）、识别活跃会话以及删除会话数据等。</mark>

<mark>ADK 内置了多种 <code>SessionService</code> 实现，具有不同的会话历史和临时数据存储机制。例如 <code>InMemorySessionService</code> 适用于测试环境，因为它不会在应用重启后保持数据持久化。</mark>

```python
# 示例：使用 InMemorySessionService
# 注意：数据不会持久化，应用重启后会丢失，仅适用于本地开发和测试环境。
from google.adk.sessions import InMemorySessionService
session_service = InMemorySessionService()
```

Then there's DatabaseSessionService if you want reliable saving to a database you manage.

<mark>如果你需要将数据保存到自行管理的数据库中，还可以选择 <code>DatabaseSessionService</code>。</mark>

```python
# 示例：使用 DatabaseSessionService
# 这适用于需要持久存储的生产环境或开发环境。
# 你需要配置数据库 URL（例如，用于 SQLite、PostgreSQL 等）。
# 安装依赖：pip install google-adk[sqlalchemy] 和数据库驱动（例如，PostgreSQL 的 psycopg2）
from google.adk.sessions import DatabaseSessionService
# 使用本地 SQLite 文件的示例：
db_url = "sqlite:///./my_agent_data.db"
session_service = DatabaseSessionService(db_url=db_url)
```

Besides, there's VertexAiSessionService which uses Vertex AI infrastructure for scalable production on Google Cloud.

<mark>此外，还有 <code>VertexAiSessionService</code>，它使用 Google Cloud 上 Vertex AI 的基础设施以满足可扩展的生产部署要求。</mark>

```python
# 示例：使用 VertexAiSessionService
# 这适用于 Google Cloud Platform 上需要可扩展性的生产环境，利用 Vertex AI 基础设施进行会话管理。
# 安装依赖：pip install google-adk[vertexai] 以及 GCP 设置/身份验证
from google.adk.sessions import VertexAiSessionService

PROJECT_ID = "your-gcp-project-id" # 替换为你的 GCP 项目 ID
LOCATION = "us-central1" # 替换为你所需的 GCP 位置
# 与此服务一起使用的 app_name 应对应于 Reasoning Engine ID 或名称
REASONING_ENGINE_APP_NAME = "projects/your-gcp-project-id/locations/us-central1/reasoningEngines/your-engine-id" # 替换为你的 Reasoning Engine 资源名称

session_service = VertexAiSessionService(project=PROJECT_ID, location=LOCATION)
# 使用此服务时，将 REASONING_ENGINE_APP_NAME 传递给以下方法：
# session_service.create_session(app_name=REASONING_ENGINE_APP_NAME, ...)
# session_service.get_session(app_name=REASONING_ENGINE_APP_NAME, ...)
# session_service.append_event(session, event, app_name=REASONING_ENGINE_APP_NAME)
# session_service.delete_session(app_name=REASONING_ENGINE_APP_NAME, ...)
```

Choosing an appropriate SessionService is crucial as it determines how the agent's interaction history and temporary data are stored and their persistence.

<mark>选择合适的 <code>SessionService</code> 至关重要，因为它决定了智能体的交互历史和临时数据如何存储以及持久化方式。</mark>

Each message exchange involves a cyclical process: A message is received, the Runner retrieves or establishes a Session using the SessionService, the agent processes the message using the Session's context (state and historical interactions), the agent generates a response and may update the state, the Runner encapsulates this as an Event, and the session_service.append_event method records the new event and updates the state in storage. The Session then awaits the next message. Ideally, the delete_session method is employed to terminate the session when the interaction concludes. This process illustrates how the SessionService maintains continuity by managing the Session-specific history and temporary data.

<mark>每次消息交换都遵循以下流程：接收消息后，<code>Runner</code> 通过 <code>SessionService</code> 检索或创建对应的 <code>Session</code>，智能体利用 <code>Session</code> 的上下文（包括状态和历史交互）来处理消息，接着智能体生成响应并更新状态，<code>Runner</code> 将其封装为 <code>Event</code> 事件，<code>session_service.append_event</code> 方法记录该事件并更新状态。然后 <code>Session</code> 继续等待下一条消息。理想情况下，在交互结束时应该使用 <code>delete_session</code> 方法终止会话。</mark>

<mark>以上过程展示了 <code>SessionService</code> 如何通过管理 <code>Session</code> 特定的历史和临时数据来维持连续性。</mark>

---

## State: The Session's Scratchpad | <mark>State：会话暂存区</mark>

In the ADK, each Session, representing a chat thread, includes a state component akin to an agent's temporary working memory for the duration of that specific conversation. While session.events logs the entire chat history, session.state stores and updates dynamic data points relevant to the active chat.

<mark>在 ADK 中，每个代表聊天会话的 <code>Session</code> 都包含一个状态组件，类似于智能体在该特定对话期间的临时工作记忆。<code>session.events</code> 记录整个聊天历史，而 <code>session.state</code> 则存储和更新与当前会话相关的动态信息。</mark>

Fundamentally, session.state operates as a dictionary, storing data as key-value pairs. Its core function is to enable the agent to retain and manage details essential for coherent dialogue, such as user preferences, task progress, incremental data collection, or conditional flags influencing subsequent agent actions.

<mark><code>session.state</code> 本质上是一个字典，以键值对形式存储数据。其主要功能是帮助智能体保留和管理对话连贯性所需的关键信息，例如用户偏好、任务进展、增量数据收集，或影响后续智能体行为的条件标志。</mark>

The state's structure comprises string keys paired with values of serializable Python types, including strings, numbers, booleans, lists, and dictionaries containing these basic types. State is dynamic, evolving throughout the conversation. The permanence of these changes depends on the configured SessionService.

<mark>状态结构由字符串键与可序列化 Python 类型值组成，包括字符串、数字、布尔值、列表以及包含这些基本类型的字典。状态是动态的，在整个对话过程中不断演化。这些更改的持久性取决于所使用的 <code>SessionService</code>。</mark>

State organization can be achieved using key prefixes to define data scope and persistence. Keys without prefixes are session-specific.

<mark>可以通过键前缀来管理数据范围和持久性，从而实现有效的状态组织。不带前缀的键属于会话级别的数据。</mark>

● The **user:** prefix associates data with a user ID across all sessions.

● <mark><strong>user:</strong> 该前缀的数据为用户级别，与用户 ID 关联，可以跨多个会话使用。</mark>

● The **app:** prefix designates data shared among all users of the application.

● <mark><strong>app:</strong> 该前缀的数据为应用级别，可以在应用内被所有用户共享。</mark>

● The **temp:** prefix indicates data valid only for the current processing turn and is not persistently stored.

● <mark><strong>temp:</strong> 该前缀标识临时数据，仅在当前处理轮次内有效，不会被持久化。</mark>

The agent accesses all state data through a single session.state dictionary. The SessionService handles data retrieval, merging, and persistence. State should be updated upon adding an Event to the session history via session_service.append_event(). This ensures accurate tracking, proper saving in persistent services, and safe handling of state changes.

<mark>智能体通过统一的 <code>session.state</code> 字典访问所有状态数据。<code>SessionService</code> 负责处理数据的检索、合并和持久化。状态更新应该通过 <code>session_service.append_event()</code> 向会话历史添加事件来实现。这样可以确保跟踪的完整性、在持久化服务中的正确保存以及安全的状态变更。</mark>

**1.The Simple Way: Using output_key (for Agent Text Replies):** This is the easiest method if you just want to save your agent's final text response directly into the state. When you set up your LlmAgent, just tell it the output_key you want to use. The Runner sees this and automatically creates the necessary actions to save the response to the state when it appends the event. Let's look at a code example demonstrating state update via output_key.

<mark><strong>1. 简单方法：使用 output_key（用于智能体的文本输出）</strong> 如果只需将智能体的最终响应直接保存到状态中，这是最简单的方法。定义 <code>LlmAgent</code> 时，只需指定要使用的 <code>output_key</code> 属性。<code>Runner</code> 会识别此参数设置，并创建必要的操作来将响应保存到状态中。我们来看一个通过 <code>output_key</code> 实现状态更新的代码示例。</mark>

```python
# 从 Google ADK 导入必要的类
from google.adk.agents import LlmAgent
from google.adk.sessions import InMemorySessionService, Session
from google.adk.runners import Runner
from google.genai.types import Content, Part

# 定义一个带有 output_key 的 LlmAgent。
greeting_agent = LlmAgent(
   name="Greeter",
   model="gemini-2.0-flash",
   instruction="Generate a short, friendly greeting.",
   output_key="last_greeting"
)

# --- 设置 Runner 和 Session ---
app_name, user_id, session_id = "state_app", "user1", "session1"
session_service = InMemorySessionService()
runner = Runner(
   agent=greeting_agent,
   app_name=app_name,
   session_service=session_service
)

session = session_service.create_session(
   app_name=app_name,
   user_id=user_id,
   session_id=session_id
)

print(f"Initial state: {session.state}")

# --- 运行智能体 ---
user_message = Content(parts=[Part(text="Hello")])
print("\n--- Running the agent ---")
for event in runner.run(
   user_id=user_id,
   session_id=session_id,
   new_message=user_message
):
   if event.is_final_response():
     print("Agent responded.")

# --- 检查更新后的状态 ---
# 在 runner 完成处理所有事件后正确检查状态。
updated_session = session_service.get_session(app_name, user_id, session_id)
print(f"\nState after agent run: {updated_session.state}")
```

Behind the scenes, the Runner sees your output_key and automatically creates the necessary actions with a state_delta when it calls append_event.

<mark>在幕后，<code>Runner</code> 会识别 <code>output_key</code>，并在调用 <code>append_event</code> 时自动创建带有 <code>state_delta</code> 的必要操作。</mark>

**2.The Standard Way: Using EventActions.state_delta (for More Complicated Updates):** For times when you need to do more complex things – like updating several keys at once, saving things that aren't just text, targeting specific scopes like user: or app:, or making updates that aren't tied to the agent's final text reply – you'll manually build a dictionary of your state changes (the state_delta) and include it within the EventActions of the Event you're appending. Let's look at one example:

<mark><strong>2. 标准方法：使用 EventActions.state_delta（用于更复杂的场景）</strong> 当需要进行更复杂的操作时，例如同时更新多个键、保存非纯文本内容、针对特定作用域（如 <code>user:</code> 或 <code>app:</code>），或者执行与智能体最终文本回复无关的更新时，需要手动构建状态变更的字典（即 <code>state_delta</code>），并将其放在要附加的 <code>Event</code> 的 <code>EventActions</code> 中。让我们来看一个示例：</mark>

```python
import time
from google.adk.tools.tool_context import ToolContext
from google.adk.sessions import InMemorySessionService

# --- 定义推荐的基于工具的方法 ---
def log_user_login(tool_context: ToolContext) -> dict:
   """
   在用户登录事件时更新会话状态。
   此工具封装了与用户登录相关的所有状态更改。
   参数：
       tool_context：由 ADK 自动提供，提供对会话状态的访问。
   返回：
       确认操作成功的字典。
   """
   # 通过提供的上下文直接访问状态。
   state = tool_context.state
  
   # 获取当前值或默认值，然后更新状态。
   # 这样更清晰，并且将逻辑集中在一起。
   login_count = state.get("user:login_count", 0) + 1
   state["user:login_count"] = login_count
   state["task_status"] = "active"
   state["user:last_login_ts"] = time.time()
   state["temp:validation_needed"] = True
  
   print("State updated from within the `log_user_login` tool.")
  
   return {
       "status": "success",
       "message": f"User login tracked. Total logins:
{login_count}."
   }

# --- 使用演示 ---
# 在实际应用中，LLM 智能体会决定调用此工具。
# 在这里，我们模拟直接调用以进行演示。

# 1. 设置
session_service = InMemorySessionService()
app_name, user_id, session_id = "state_app_tool", "user3", "session3"
session = session_service.create_session(
   app_name=app_name,
   user_id=user_id,
   session_id=session_id,
   state={"user:login_count": 0, "task_status": "idle"}
)
print(f"Initial state: {session.state}")

# 2. 模拟工具调用（在实际应用中，ADK Runner 执行此操作）
# 我们手动创建一个 ToolContext 仅用于此示例。
from google.adk.tools.tool_context import InvocationContext
mock_context = ToolContext(
   invocation_context=InvocationContext(
       app_name=app_name, user_id=user_id, session_id=session_id,
       session=session, session_service=session_service
   )
)

# 3. 执行工具
log_user_login(mock_context)

# 4. 检查更新后的状态
updated_session = session_service.get_session(app_name, user_id, session_id)
print(f"State after tool execution: {updated_session.state}")
```

This code demonstrates a tool-based approach for managing user session state in an application. It defines a function log_user_login, which acts as a tool. This tool is responsible for updating the session state when a user logs in.

<mark>此代码演示了一种基于工具的方法来管理应用程序中的用户会话状态。它定义了一个工具函数 <code>log_user_login</code>，负责在用户登录时更新会话状态。</mark>

The function takes a ToolContext object, provided by the ADK, to access and modify the session's state dictionary. Inside the tool, it increments a user:login_count, sets the task_status to "active", records the user:last_login_ts (timestamp), and adds a temporary flag temp:validation_needed.

<mark>该函数接收由 ADK 提供的 <code>ToolContext</code> 对象，用于访问和修改会话的状态字典。在工具内部，它会递增 <code>user:login_count</code>，将 <code>task_status</code> 设置为 <code>active</code>，记录 <code>user:last_login_ts</code>（时间戳），并添加临时标志 <code>temp:validation_needed</code>。</mark>

The demonstration part of the code simulates how this tool would be used. It sets up an in-memory session service and creates an initial session with some predefined state. A ToolContext is then manually created to mimic the environment in which the ADK Runner would execute the tool. The log_user_login function is called with this mock context. Finally, the code retrieves the session again to show that the state has been updated by the tool's execution. The goal is to show how encapsulating state changes within tools makes the code cleaner and more organized compared to directly manipulating state outside of tools.

<mark>代码的演示部分模拟了此工具的使用方式。它设置了一个内存会话服务，并创建了一个包含预定义状态的初始会话。随后手动创建 <code>ToolContext</code> 来模拟 ADK <code>Runner</code> 执行工具的环境。使用此模拟上下文调用 <code>log_user_login</code> 函数。最后，代码再次检索会话以展示状态已通过工具执行而更新。其目的是展示与在工具外部直接操作状态相比，将状态变更封装在工具内部可以使代码更加清晰和内聚。</mark>

Note that direct modification of the `session.state` dictionary after retrieving a session is strongly discouraged as it bypasses the standard event processing mechanism. Such direct changes will not be recorded in the session's event history, may not be persisted by the selected `SessionService`, could lead to concurrency issues, and will not update essential metadata such as timestamps. The recommended methods for updating the session state are using the `output_key` parameter on an `LlmAgent` (specifically for the agent's final text responses) or including state changes within `EventActions.state_delta` when appending an event via `session_service.append_event()`. The `session.state` should primarily be used for reading existing data.

<mark><strong>⚠️ 重要警告</strong>：严禁在检索会话后直接修改 <code>session.state</code> 字典，因为这会绕过标准的事件处理机制。此类更改不会被记录在会话的事件历史中，可能无法被 <code>SessionService</code> 持久化，引起并发问题，并且不会更新时间戳等关键元数据。更新会话状态的推荐方法包括：在 <code>LlmAgent</code> 上使用 <code>output_key</code> 参数（专门用于智能体的最终文本输出），或在通过 <code>session_service.append_event()</code> 添加事件时，在 <code>EventActions.state_delta</code> 中包含状态变更的内容。<code>session.state</code> 主要用于读取现有数据。</mark>

To recap, when designing your state, keep it simple, use basic data types, give your keys clear names and use prefixes correctly, avoid deep nesting, and always update state using the append_event process.

<mark>总而言之，在设计状态时，应保持简洁，使用基本数据类型，使用具体清晰的名称及合适前缀的键，避免深度嵌套，并始终通过 <code>append_event</code> 来更新状态。</mark>

---

## Memory: Long-Term Knowledge with MemoryService | <mark>记忆：使用 MemoryService 实现长期知识管理</mark>

In agent systems, the Session component maintains a record of the current chat history (events) and temporary data (state) specific to a single conversation. However, for agents to retain information across multiple interactions or access external data, long-term knowledge management is necessary. This is facilitated by the MemoryService.

<mark>在智能体系统中，<code>Session</code> 组件负责维护单个对话的聊天历史（事件）和临时数据（状态）。然而，为了让智能体能够在多次交互中持久保存信息或访问外部数据，需要实现长期知识管理功能。这一功能由 <code>MemoryService</code> 提供支持。</mark>

```python
# 示例：使用 InMemoryMemoryService
# 这适用于本地开发和测试，不需要在应用重启后保持数据持久化的场景。
# 因为应用停止时记忆内容会丢失。
from google.adk.memory import InMemoryMemoryService
memory_service = InMemoryMemoryService()
```

Session and State can be conceptualized as short-term memory for a single chat session, whereas the Long-Term Knowledge managed by the MemoryService functions as a persistent and searchable repository. This repository may contain information from multiple past interactions or external sources. The MemoryService, as defined by the BaseMemoryService interface, establishes a standard for managing this searchable, long-term knowledge. Its primary functions include adding information, which involves extracting content from a session and storing it using the add_session_to_memory method, and retrieving information, which allows an agent to query the store and receive relevant data using the search_memory method.

<mark>从概念上来说，<code>Session</code> 和 <code>State</code> 管理的是单个聊天会话的短期记忆，而由 <code>MemoryService</code> 管理的长期知识则充当持久化且可搜索的知识库。该知识库可能包含来自多次历史交互或外部数据源的信息。</mark>

<mark><code>MemoryService</code> 通过 <code>BaseMemoryService</code> 接口定义，为管理这种可搜索的长期知识建立了规范。其主要功能包括：信息添加（从会话中提取内容并使用 <code>add_session_to_memory</code> 方法存储）和信息检索（允许智能体使用 <code>search_memory</code> 方法查询存储库并获取相关数据）。</mark>

The ADK offers several implementations for creating this long-term knowledge store. The InMemoryMemoryService provides a temporary storage solution suitable for testing purposes, but data is not preserved across application restarts. For production environments, the VertexAiRagMemoryService is typically utilized. This service leverages Google Cloud's Retrieval Augmented Generation (RAG) service, enabling scalable, persistent, and semantic search capabilities (Also, refer to the chapter 14 on RAG).

<mark>ADK 提供多种实现来创建这种长期知识存储。<code>InMemoryMemoryService</code> 适用于测试目的的临时存储解决方案，但其数据在应用程序重启后不会保留。对于生产环境，通常采用 <code>VertexAiRagMemoryService</code>。该服务利用 Google Cloud 的检索增强生成（RAG）服务，提供可扩展、持久化且支持语义搜索的能力（有关 RAG 的详细信息，请参阅第 14 章）。</mark>

```python
# 示例：使用 VertexAiRagMemoryService
# 这适用于 GCP 上的可扩展生产环境，利用 Vertex AI RAG 实现持久、可搜索的记忆。
# 需要安装依赖：pip install google-adk[vertexai]、GCP 设置/身份验证，以及 Vertex AI RAG 语料库。
from google.adk.memory import VertexAiRagMemoryService

# 你的 Vertex AI RAG 语料库的资源名称
RAG_CORPUS_RESOURCE_NAME = "projects/your-gcp-project-id/locations/us-central1/ragCorpora/your-corpus-id" # 替换为你的语料库资源名称

# 检索的可选配置
SIMILARITY_TOP_K = 5 # 要检索的 Top 结果数量
VECTOR_DISTANCE_THRESHOLD = 0.7 # 向量相似性的阈值

memory_service = VertexAiRagMemoryService(
   rag_corpus=RAG_CORPUS_RESOURCE_NAME,
   similarity_top_k=SIMILARITY_TOP_K,
   vector_distance_threshold=VECTOR_DISTANCE_THRESHOLD
)
# 使用此服务时，add_session_to_memory 和 search_memory 等方法将与指定的 Vertex AI RAG 语料库交互。
```

---

## Hands-On Code: Memory Management in LangChain and LangGraph | <mark>代码实战：使用 LangChain 和 LangGraph</mark>

In LangChain and LangGraph, Memory is a critical component for creating intelligent and natural-feeling conversational applications. It allows an AI agent to remember information from past interactions, learn from feedback, and adapt to user preferences. LangChain's memory feature provides the foundation for this by referencing a stored history to enrich current prompts and then recording the latest exchange for future use. As agents handle more complex tasks, this capability becomes essential for both efficiency and user satisfaction.

<mark>在 LangChain 和 LangGraph 中，记忆是创建智能、自然流畅的对话应用的关键组件。它使智能体能够记住历史交互信息、从反馈中学习并适应用户偏好。</mark>

<mark>LangChain 的记忆功能通过引用存储的历史记录来丰富当前提示词，并记录最新的交互内容供将来使用。随着智能体处理更复杂的任务，这种能力对提升效率和用户满意度至关重要。</mark>

**Short-Term Memory:** This is thread-scoped, meaning it tracks the ongoing conversation within a single session or thread. It provides immediate context, but a full history can challenge an LLM's context window, potentially leading to errors or poor performance. LangGraph manages short-term memory as part of the agent's state, which is persisted via a checkpointer, allowing a thread to be resumed at any time.

<mark><strong>短期记忆：</strong> 其作用域限于单个会话，它提供即时上下文，但完整的历史对话记录可能超出大语言模型的上下文窗口限制，导致错误或性能下降。LangGraph 将短期记忆作为智能体状态的一部分管理，通过检查点机制实现持久化，允许随时恢复会话继续执行。</mark>

**Long-Term Memory:** This stores user-specific or application-level data across sessions and is shared between conversational threads. It is saved in custom "namespaces" and can be recalled at any time in any thread. LangGraph provides stores to save and recall long-term memories, enabling agents to retain knowledge indefinitely.

<mark><strong>长期记忆：</strong> 跨会话存储用户特定数据或应用级别数据，并在对话之间共享。它保存在自定义的「命名空间」中，可在任何会话的任何时间被检索。LangGraph 提供存储机制来保存和检索长期记忆，使智能体能够永久保留知识。</mark>

LangChain provides several tools for managing conversation history, ranging from manual control to automated integration within chains.

<mark>LangChain 提供了多种工具来管理对话历史，从手动控制到链内自动集成。</mark>

**ChatMessageHistory: Manual Memory Management.** For direct and simple control over a conversation's history outside of a formal chain, the ChatMessageHistory class is ideal. It allows for the manual tracking of dialogue exchanges.

<mark><strong>ChatMessageHistory：手动记忆管理</strong> 对于想在链之外简单直接地控制对话历史，<code>ChatMessageHistory</code> 类是理想选择。它支持手动跟踪对话交互。</mark>

```python
from langchain.memory import ChatMessageHistory

# 初始化历史对象
history = ChatMessageHistory()

# 添加用户和 AI 消息
history.add_user_message("I'm heading to New York next week.")
history.add_ai_message("Great! It's a fantastic city.")

# 访问消息列表
print(history.messages)
```

> 新版本 `langchain > 1.0` 中 `from langchain.memory import ChatMessageHistory` 无法导入，如需可从 `from langchain_community.chat_message_histories.in_memory import ChatMessageHistory` 导入 `ChatMessageHistory` , 可参考 [`issues#1499`](https://github.com/langchain-ai/langchain/issues/1499#issuecomment-2034691706)

**ConversationBufferMemory: Automated Memory for Chains.** For integrating memory directly into chains, ConversationBufferMemory is a common choice. It holds a buffer of the conversation and makes it available to your prompt. Its behavior can be customized with two key parameters:

<mark><strong>ConversationBufferMemory：链的自动化记忆管理</strong> 若需将记忆功能直接集成到链中，<code>ConversationBufferMemory</code> 是更好的选择。它维护对话内容的缓冲区并提供给提示词。其行为可通过两个关键参数配置：</mark>

● **memory_key**: A string that specifies the variable name in your prompt that will hold the chat history. It defaults to "history".

● <mark><code>memory_key</code>：一个字符串参数，用于指定提示词模板中存储聊天历史的变量名称，默认值为「history」。</mark>

● **return_messages**: A boolean that dictates the format of the history. ○If False (the default), it returns a single formatted string, which is ideal for standard LLMs. ○If True, it returns a list of message objects, which is the recommended format for Chat Models.

● <mark><code>return_messages</code>：布尔值参数，控制历史记录的处理方式。若为 False（默认值），则返回单个格式化的字符串，适用于标准的大语言模型；若为 True，则返回消息对象列表，适用于聊天模型。</mark>

```python
from langchain.memory import ConversationBufferMemory

# 初始化记忆
memory = ConversationBufferMemory()

# 保存对话轮次
memory.save_context({"input": "What's the weather like?"}, {"output":
"It's sunny today."})

# 将记忆加载为字符串
print(memory.load_memory_variables({}))
```

> 新版本 `langchain > 1.0` 中 `from langchain.memory import ConversationBufferMemory` (自 0.3.1 版本开始被标记为弃用, 在 1.0.0 版本中被完全移除) 无法导入，如需可修改为 `from langchain_classic.memory import ConversationBufferMemory` 导入 `ConversationBufferMemory`, 可参考 [`libs/langchain/langchain_classic/memory/buffer.py`](https://github.com/langchain-ai/langchain/blob/3ace4e36808220d6a1c5402691f5d37867521458/libs/langchain/langchain_classic/memory/buffer.py#L21), [`commit#4d1cfa4`](https://github.com/langchain-ai/langchain/commit/4d1cfa494ab3040698fcb8164fe860a7ef87f979); 由于源代码中使用 `@deprecated` 标记，运行结果会抛出 `Warning`

Integrating this memory into an LLMChain allows the model to access the conversation's history and provide contextually relevant responses

<mark>下面的例子演示将记忆功能集成到 <code>LLMChain</code> 后，模型能够访问对话历史并提供上下文相关的响应。</mark>

```python
from langchain_openai import OpenAI
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate
from langchain.memory import ConversationBufferMemory

# 1. 定义 LLM 和提示词模板
llm = OpenAI(temperature=0)
template = """You are a helpful travel agent.

Previous conversation:1
{history}

New question: {question}
Response:"""
prompt = PromptTemplate.from_template(template)

# 2. 配置记忆
# memory_key 设置为 "history" 与提示词中的变量匹配
memory = ConversationBufferMemory(memory_key="history")

# 3. 构建链
conversation = LLMChain(llm=llm, prompt=prompt, memory=memory)

# 4. 运行对话
response = conversation.predict(question="I want to book a flight.")
print(response)
response = conversation.predict(question="My name is Sam, by the
way.")
print(response)
response = conversation.predict(question="What was my name again?")
print(response)
```

> 新版本 `langchain > 1.0` 中 `from langchain.chains import LLMChain` (自 0.1.17 版本开始被标记为弃用, 在 1.0.0 版本中被完全移除) `from langchain.prompts import PromptTemplate`  无法导入，如需可从 `langchain_classic.chains` 导入 `LLMChain`, 从 `langchain_classic.prompts` 或 `langchain_core.prompts` 导入 `PromptTemplate`, 可参考 [`commit#4d1cfa4`](https://github.com/langchain-ai/langchain/commit/4d1cfa494ab3040698fcb8164fe860a7ef87f979); 由于源代码中使用 `@deprecated` 标记，运行结果会抛出 `Warning`

For improved effectiveness with chat models, it is recommended to use a structured list of message objects by setting `return_messages=True`.

<mark>对于聊天模型，建议设置 <code>return_messages=True</code> 以使用结构化的消息对象列表。</mark>

```python
from langchain_openai import ChatOpenAI
from langchain.chains import LLMChain
from langchain.memory import ConversationBufferMemory
from langchain_core.prompts import (
   ChatPromptTemplate,
   MessagesPlaceholder,
   SystemMessagePromptTemplate,
   HumanMessagePromptTemplate,
)

# 1. 定义聊天模型和提示
llm = ChatOpenAI()
prompt = ChatPromptTemplate(
   messages=[
       SystemMessagePromptTemplate.from_template("You are a friendly assistant."),
       MessagesPlaceholder(variable_name="chat_history"),
       HumanMessagePromptTemplate.from_template("{question}")
   ]
)

# 2. 配置记忆
# 设置 return_messages=True 对聊天模型来说至关重要
memory = ConversationBufferMemory(memory_key="chat_history", return_messages=True)

# 3. 构建链
conversation = LLMChain(llm=llm, prompt=prompt, memory=memory)

# 4. 运行对话
response = conversation.predict(question="Hi, I'm Jane.")
print(response)
response = conversation.predict(question="Do you remember my name?")
print(response)
```
> 新版本 `langchain > 1.0` 中 `from langchain.chains import LLMChain` (自 0.1.17 版本开始被标记为弃用, 在 1.0.0 版本中被完全移除) `from langchain.memory import ConversationBufferMemory` (自 0.1.170.3.1 版本开始被标记为弃用, 在 1.0.0 版本中被完全移除) 无法导入，如需可从 `langchain_classic.chains` `langchain_classic.memory` 导入 `LLMChain` `ConversationBufferMemory`, 可参考 [`commit#4d1cfa4`](https://github.com/langchain-ai/langchain/commit/4d1cfa494ab3040698fcb8164fe860a7ef87f979); 由于源代码中使用 `@deprecated` 标记，运行结果会抛出 `Warning`

**Types of Long-Term Memory:** Long-term memory allows systems to retain information across different conversations, providing a deeper level of context and personalization. It can be broken down into three types analogous to human memory:

<mark><strong>长期记忆的类型：</strong>长期记忆使系统能够跨对话保存信息，提供更深层次的上下文理解和个性化服务。类比人类记忆机制，它可分为以下三种类型：</mark>

● **Semantic Memory: Remembering Facts:** This involves retaining specific facts and concepts, such as user preferences or domain knowledge. It is used to ground an agent's responses, leading to more personalized and relevant interactions. This information can be managed as a continuously updated user "profile" (a JSON document) or as a "collection" of individual factual documents.

● <mark><strong>语义记忆：事实记忆</strong> 存储具体的事实信息和概念知识，例如用户偏好或领域知识。它为智能体的响应提供事实依据，实现更加个性化和相关的交互。这类信息可以作为持续更新的用户「档案」（以 JSON 格式保存的文档）或一个独立的文档「集合」进行管理。</mark>

● **Episodic Memory: Remembering Experiences:** This involves recalling past events or actions. For AI agents, episodic memory is often used to remember how to accomplish a task. In practice, it's frequently implemented through few-shot example prompting, where an agent learns from past successful interaction sequences to perform tasks correctly.

● <mark><strong>情景记忆：经历记忆</strong> 回忆过往事件或行为序列。对于 AI 智能体，情景记忆通常用于记忆如何完成特定任务。在实践中，常通过少样本示例提示实现，智能体从历史成功的交互序列中学习，以正确执行任务。</mark>

● **Procedural Memory: Remembering Rules:** This is the memory of how to perform tasks—the agent's core instructions and behaviors, often contained in its system prompt. It's common for agents to modify their own prompts to adapt and improve. An effective technique is "Reflection," where an agent is prompted with its current instructions and recent interactions, then asked to refine its own instructions.

● <mark><strong>程序性记忆：规则记忆</strong> 关于如何执行任务的记忆，包括智能体的核心指令和行为规范，通常体现在系统提示词中。常见做法是智能体通过修改自身提示词来实现自适应和改进。一种有效技术是「反思机制」，即向智能体呈现当前指令和近期交互记录，要求其自主优化指令内容。</mark>

Below is pseudo-code demonstrating how an agent might use reflection to update its procedural memory stored in a LangGraph BaseStore

<mark>以下伪代码示例演示了智能体如何运用反思机制来更新存储在 LangGraph <code>BaseStore</code> 中的程序记忆：</mark>

```python
# 更新智能体指令的函数
def update_instructions(state: State, store: BaseStore):
   namespace = ("instructions",)
   # 从存储中获取当前指令
   current_instructions = store.search(namespace)[0]
  
   # 创建提示以要求大语言模型反思对话并生成改进后的指令
   prompt = prompt_template.format(
       instructions=current_instructions.value["instructions"],
       conversation=state["messages"]
   )
  
   # 从大语言模型获取新的指令
   output = llm.invoke(prompt)
   new_instructions = output['new_instructions']
  
   # 将改进后的指令保存回存储
   store.put(("agent_instructions",), "agent_a", {"instructions": new_instructions})

# 使用指令生成响应的函数
def call_model(state: State, store: BaseStore):
   namespace = ("agent_instructions", )
   # 从存储中检索最新的指令
   instructions = store.get(namespace, key="agent_a")[0]
  
   # 使用检索到的指令格式化提示词
   prompt = prompt_template.format(instructions=instructions.value["instructions"])
   # ... 应用逻辑继续执行
```

LangGraph stores long-term memories as JSON documents in a store. Each memory is organized under a custom namespace (like a folder) and a distinct key (like a filename). This hierarchical structure allows for easy organization and retrieval of information. The following code demonstrates how to use InMemoryStore to put, get, and search for memories.

<mark>LangGraph 将长期记忆以 JSON 格式存储起来。每个记忆条目通过自定义命名空间（类似文件夹结构）和唯一键名（类似文件名）组织。这种层次化结构便于信息的系统化组织和高效检索。以下代码示例演示如何使用 <code>InMemoryStore</code> 来实现记忆的存储、获取和搜索操作。</mark>

```python
from langgraph.store.memory import InMemoryStore

# 实际嵌入函数的占位符
def embed(texts: list[str]) -> list[list[float]]:
   # 在实际应用中，使用适当的嵌入模型
   return [[1.0, 2.0] for _ in texts]

# 初始化内存存储。对于生产环境，请使用基于数据库的存储方式。
store = InMemoryStore(index={"embed": embed, "dims": 2})

# 为特定用户和应用上下文定义命名空间
user_id = "my-user"
application_context = "chitchat"
namespace = (user_id, application_context)

# 1. 将记忆放入存储
store.put(
   namespace,
   "a-memory",  # 此记忆的键
   {
       "rules": [
           "User likes short, direct language",
           "User only speaks English & python",
       ],
       "my-key": "my-value",
   },
)

# 2. 通过其命名空间和键获取记忆
item = store.get(namespace, "a-memory")
print("Retrieved Item:", item)

# 3. 在命名空间内搜索记忆，按内容过滤并按与查询的向量相似性排序。
items = store.search(
   namespace,
   filter={"my-key": "my-value"},
   query="language preferences"
)
print("Search Results:", items)
```

---

## Vertex Memory Bank | <mark>Vertex Memory Bank 服务</mark>

Memory Bank, a managed service in the Vertex AI Agent Engine, provides agents with persistent, long-term memory. The service uses Gemini models to asynchronously analyze conversation histories to extract key facts and user preferences.

<mark>Memory Bank 是 Vertex AI Agent Engine 中的托管服务，为智能体提供持久化长期记忆。该服务利用 Gemini 模型异步分析对话历史，提取关键事实信息和用户偏好。</mark>

This information is stored persistently, organized by a defined scope like user ID, and intelligently updated to consolidate new data and resolve contradictions. Upon starting a new session, the agent retrieves relevant memories through either a full data recall or a similarity search using embeddings. This process allows an agent to maintain continuity across sessions and personalize responses based on recalled information.

<mark>这些信息被持久化存储，按预定义范围（如用户 ID）组织，并通过智能更新机制整合新数据和解决信息冲突。启动新会话时，智能体通过完整数据检索或基于嵌入的相似性搜索来获取相关记忆。这一流程使智能体能够维持跨会话的连续性，并根据检索到的记忆信息提供个性化响应。</mark>

The agent's runner interacts with the VertexAiMemoryBankService, which is initialized first. This service handles the automatic storage of memories generated during the agent's conversations. Each memory is tagged with a unique USER_ID and APP_NAME, ensuring accurate retrieval in the future.

<mark>智能体的执行器与 <code>VertexAiMemoryBankService</code> 服务交互（该服务需预先初始化）。该服务负责自动存储智能体对话过程中生成的记忆内容。每个记忆条目通过唯一的 <code>USER_ID</code> 和 <code>APP_NAME</code> 标记，确保可以被准确检索。</mark>

```python
from google.adk.memory import VertexAiMemoryBankService

agent_engine_id = agent_engine.api_resource.name.split("/")[-1]

memory_service = VertexAiMemoryBankService(
   project="PROJECT_ID",
   location="LOCATION",
   agent_engine_id=agent_engine_id
)

session = await session_service.get_session(
   app_name=app_name,
   user_id="USER_ID",
   session_id=session.id
)
await memory_service.add_session_to_memory(session)
```

Memory Bank offers seamless integration with the Google ADK, providing an immediate out-of-the-box experience. For users of other agent frameworks, such as LangGraph and CrewAI, Memory Bank also offers support through direct API calls. Online code examples demonstrating these integrations are readily available for interested readers.

<mark>Memory Bank 可以与 Google ADK 无缝集成，提供开箱即用的体验。对于其他智能体框架（如 LangGraph 和 CrewAI）的用户，Memory Bank 也通过 API 调用提供支持。感兴趣的读者可以通过在线代码示例，了解这些集成方案的实现。</mark>

---

## At a Glance | <mark>要点速览</mark>

**What:** Agentic systems need to remember information from past interactions to perform complex tasks and provide coherent experiences. Without a memory mechanism, agents are stateless, unable to maintain conversational context, learn from experience, or personalize responses for users. This fundamentally limits them to simple, one-shot interactions, failing to handle multi-step processes or evolving user needs. The core problem is how to effectively manage both the immediate, temporary information of a single conversation and the vast, persistent knowledge gathered over time.

<mark><strong>问题所在：</strong> 智能体系统需要记住过往交互信息以执行复杂任务并提供连贯体验。若缺少记忆机制，智能体将处于无状态，无法维持对话上下文、从经验中学习或提供个性化响应。这从根本上将它们限制在简单的一次性交互中，无法处理多步骤流程或不断变化的用户需求。核心问题在于如何有效管理单次对话的即时信息与长期积累的持久知识。</mark>

**Why:** The standardized solution is to implement a dual-component memory system that distinguishes between short-term and long-term storage. Short-term, contextual memory holds recent interaction data within the LLM's context window to maintain conversational flow. For information that must persist, long-term memory solutions use external databases, often vector stores, for efficient, semantic retrieval. Agentic frameworks like the Google ADK provide specific components to manage this, such as Session for the conversation thread and State for its temporary data. A dedicated MemoryService is used to interface with the long-term knowledge base, allowing the agent to retrieve and incorporate relevant past information into its current context.

<mark><strong>解决之道：</strong> 标准解决方案是实现区分短期与长期存储的双组件记忆系统。短期上下文记忆位于大语言模型的上下文窗口内，保存最近的交互数据以维持对话流程。对于必须持久化的信息，长期记忆解决方案采用外部数据库（通常是向量存储）进行高效的语义检索。</mark>

<mark>智能体框架（如 Google ADK）提供专门的组件来管理记忆，例如 <code>Session</code>（对话线程）和 <code>State</code>（临时数据）。专门的 <code>MemoryService</code> 组件用于与长期知识库交互，允许智能体检索相关历史信息并整合到当前上下文中。</mark>

**Rule of thumb:** Use this pattern when an agent needs to do more than answer a single question. It is essential for agents that must maintain context throughout a conversation, track progress in multi-step tasks, or personalize interactions by recalling user preferences and history. Implement memory management whenever the agent is expected to learn or adapt based on past successes, failures, or newly acquired information.

<mark><strong>经验法则：</strong> 当智能体需要执行的任务超越单一问题回答时，应采用此模式。对于必须在整个对话中维持上下文、跟踪多步骤任务进度或通过回忆用户偏好和历史来个性化交互的智能体，记忆管理至关重要。当智能体需要基于过去的成功、失败或新获得的信息进行学习或自适应调整时，也应该实施记忆管理。</mark>

**Visual summary** | <mark><strong>可视化总结</strong></mark>

![记忆管理设计模式](./images/chapter08_fig1.png)

Fig. 1: Memory management design pattern

<mark>图 1：记忆管理设计模式</mark>

---

## Key Takeaways | <mark>核心要点</mark>

To quickly recap the main points about memory management:

<mark>快速回顾记忆管理的核心要点：</mark>

● Memory is super important for agents to keep track of things, learn, and personalize interactions.

   <mark>记忆机制对于智能体的事件跟踪、经验学习和个性化交互至关重要。</mark>

● Conversational AI relies on both short-term memory for immediate context within a single chat and long-term memory for persistent knowledge across multiple sessions.

   <mark>对话式 AI 系统同时依赖短期记忆（管理单次聊天中的即时上下文）和长期记忆（维护跨多个会话的持久化知识）。</mark>

● Short-term memory (the immediate stuff) is temporary, often limited by the LLM's context window or how the framework passes context.

   <mark>短期记忆（处理即时内容）具有临时性，通常受限于大语言模型的上下文窗口容量或框架的上下文传递机制。</mark>

● Long-term memory (the stuff that sticks around) saves info across different chats using outside storage like vector databases and is accessed by searching.

   <mark>长期记忆（存储持久化内容）利用外部存储系统（如向量数据库）在不同聊天会话间保存信息，并通过搜索机制进行访问。</mark>

● Frameworks like ADK have specific parts like Session (the chat thread), State (temporary chat data), and MemoryService (the searchable long-term knowledge) to manage memory.

   <mark>诸如 ADK 之类的框架通过特定组件管理记忆：<code>Session</code>（管理聊天线程）、<code>State</code>（存储临时聊天数据）和 <code>MemoryService</code>（提供可搜索的长期知识库）。</mark>

● ADK's SessionService handles the whole life of a chat session, including its history (events) and temporary data (state).

   <mark>ADK 的 <code>SessionService</code> 负责管理聊天会话的完整生命周期，包括历史记录（事件日志）和临时数据（状态信息）。</mark>

● ADK's session.state is a dictionary for temporary chat data. Prefixes (user:, app:, temp:) tell you where the data belongs and if it sticks around.

   <mark>ADK 的 <code>session.state</code> 是一个用于存储临时聊天数据的字典结构。前缀标识符（<code>user:</code>、<code>app:</code>、<code>temp:</code>）明确数据归属范围及其持久化特性。</mark>

● In ADK, you should update state by using EventActions.state_delta or output_key when adding events, not by changing the state dictionary directly.

   <mark>在 ADK 框架中，状态更新应通过 <code>EventActions.state_delta</code> 或 <code>output_key</code> 在添加事件时进行，而非直接修改状态字典。</mark>

● ADK's MemoryService is for putting info into long-term storage and letting agents search it, often using tools.

   <mark>ADK 的 <code>MemoryService</code> 专用于将信息存入长期存储系统，并支持智能体通过工具接口进行搜索检索。</mark>

● LangChain offers practical tools like ConversationBufferMemory to automatically inject the history of a single conversation into a prompt, enabling an agent to recall immediate context.

   <mark>LangChain 提供诸如 <code>ConversationBufferMemory</code> 等实用工具，能够自动将单次对话历史注入提示词中，使智能体具备即时上下文回忆能力。</mark>

● LangGraph enables advanced, long-term memory by using a store to save and retrieve semantic facts, episodic experiences, or even updatable procedural rules across different user sessions.

   <mark>LangGraph 通过存储机制实现高级长期记忆功能，支持跨用户会话保存和检索语义事实、情景经历乃至可更新的程序规则。</mark>

● Memory Bank is a managed service that provides agents with persistent, long-term memory by automatically extracting, storing, and recalling user-specific information to enable personalized, continuous conversations across frameworks like Google's ADK, LangGraph, and CrewAI.

   <mark>Memory Bank 作为托管服务，通过自动提取、存储和检索用户特定信息，为智能体提供持久化长期记忆，从而在 Google ADK、LangGraph 和 CrewAI 等框架中实现个性化连续对话。</mark>

---

## Conclusion | <mark>结语</mark>

This chapter dove into the really important job of memory management for agent systems, showing the difference between the short-lived context and the knowledge that sticks around for a long time. We talked about how these types of memory are set up and where you see them used in building smarter agents that can remember things. We took a detailed look at how Google ADK gives you specific pieces like Session, State, and MemoryService to handle this. Now that we've covered how agents can remember things, both short-term and long-term, we can move on to how they can learn and adapt. The next pattern "Learning and Adaptation" is about an agent changing how it thinks, acts, or what it knows, all based on new experiences or data.

<mark>本章深入探讨了智能体系统中记忆管理这一关键任务，阐明了临时上下文信息与长期持久化知识之间的本质区别。我们剖析了各类记忆机制的架构原理及其在构建智能体系统中的实际应用，并详细介绍了 Google ADK 框架如何通过 <code>Session</code>、<code>State</code> 和 <code>MemoryService</code> 等组件来实现记忆管理。</mark>

<mark>在掌握了智能体短期与长期记忆技术的基础上，我们将继续探索智能体如何实现学习和自适应。下一个核心模式「学习与适应」将探讨智能体如何基于新的经验和数据输入，动态调整其认知模式、行为策略和知识体系。</mark>

---

## References | <mark>参考文献</mark>

1. ADK Memory: <https://google.github.io/adk-docs/sessions/memory/>

   <mark>ADK 的记忆管理：<https://google.github.io/adk-docs/sessions/memory/></mark>

2. LangGraph Memory: <https://langchain-ai.github.io/langgraph/concepts/memory/>

   <mark>LangGraph 的记忆管理：<https://langchain-ai.github.io/langgraph/concepts/memory/></mark>

3. Vertex AI Agent Engine Memory Bank: <https://cloud.google.com/blog/products/ai-machine-learning/vertex-ai-memory-bank-in-public-preview>

   <mark>Vertex AI 智能体引擎的 Memory Bank：<https://cloud.google.com/blog/products/ai-machine-learning/vertex-ai-memory-bank-in-public-preview></mark>

