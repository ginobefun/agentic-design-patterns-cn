# Chapter 11: Goal Setting and Monitoring | <mark>第 11 章：目标设定与监控</mark>

For AI agents to be truly effective and purposeful, they need more than just the ability to process information or use tools; they need a clear sense of direction and a way to know if they're actually succeeding. This is where the Goal Setting and Monitoring pattern comes into play. It's about giving agents specific objectives to work towards and equipping them with the means to track their progress and determine if those objectives have been met.

<mark>要让 AI 智能体真正有效且有目的性，它们需要的不仅仅是处理信息或使用工具的能力；它们需要明确的方向感，并能够知道自己是否真的在取得成功。这就是目标设定与监控模式发挥作用的地方。该模式旨在为智能体提供要努力实现的具体目标，并配备跟踪进度和判断这些目标是否实现的手段。</mark>

## Goal Setting and Monitoring Pattern Overview | <mark>目标设定与监控模式概述</mark>

Think about planning a trip. You don't just spontaneously appear at your destination. You decide where you want to go (the goal state), figure out where you are starting from (the initial state), consider available options (transportation, routes, budget), and then map out a sequence of steps: book tickets, pack bags, travel to the airport/station, board the transport, arrive, find accommodation, etc. This step-by-step process, often considering dependencies and constraints, is fundamentally what we mean by planning in agentic systems.

<mark>想想计划一次旅行。你不会凭空就出现在目的地。你需要决定想去哪里（目标状态），弄清楚从哪里出发（初始状态），考虑可用的选项（交通、路线、预算），然后规划出一系列步骤：订票、打包行李、前往机场/车站、登上交通工具、到达、找到住宿地等。这个逐步进行的过程，通常考虑依赖关系和约束条件，基本上就是我们在智能体系统中所说的规划。</mark>

In the context of AI agents, planning typically involves an agent taking a high-level objective and autonomously, or semi-autonomously, generating a series of intermediate steps or sub-goals. These steps can then be executed sequentially or in a more complex flow, potentially involving other patterns like tool use, routing, or multi-agent collaboration. The planning mechanism might involve sophisticated search algorithms, logical reasoning, or increasingly, leveraging the capabilities of large language models (LLMs) to generate plausible and effective plans based on their training data and understanding of tasks.

<mark>在 AI 智能体的背景下，规划通常涉及智能体接受一个高层目标，自主或半自主地生成一系列中间步骤或子目标。这些步骤可以顺序执行，或以更复杂的流程执行，可能涉及其它模式，如工具使用、路由或多智能体协作。规划机制可能涉及复杂的搜索算法、逻辑推理，或者越来越多地利用大语言模型 (LLMs) 的能力，基于它们的训练数据和任务理解来生成合理且有效的计划。</mark>

A good planning capability allows agents to tackle problems that aren't simple, single-step queries. It enables them to handle multi-faceted requests, adapt to changing circumstances by replanning, and orchestrate complex workflows. It's a foundational pattern that underpins many advanced agentic behaviors, turning a simple reactive system into one that can proactively work towards a defined objective.

<mark>良好的规划能力，使智能体不止能够处理简单的单步查询问题。规划还使得智能体能够处理多个面向的请求，通过重新规划来适应变化，并编排复杂的工作流程。这是一个基础模式，支撑着许多高级智能体行为，将简单的反应式系统，转变为能够主动努力实现既定目标的系统。</mark>

## Practical Applications & Use Cases | <mark>实际应用场景</mark>

The Goal Setting and Monitoring pattern is essential for building agents that can operate autonomously and reliably in complex, real-world scenarios. Here are some practical applications:

<mark>目标设定与监控模式，对于构建能够在复杂现实场景中自主可靠运行的智能体至关重要。以下是一些实际应用：</mark>

* **Customer Support Automation:** An agent's goal might be to "resolve customer's billing inquiry." It monitors the conversation, checks database entries, and uses tools to adjust billing. Success is monitored by confirming the billing change and receiving positive customer feedback. If the issue isn't resolved, it escalates.

   <mark>* **自动化客户支持：** 智能体的目标可能是“解决客户的账单查询”。它监控对话，检查数据库条目，并使用工具调整账单。通过确认账单变更和收到积极的客户反馈来监控是否成功。如果问题未解决，它会升级处理。</mark>
* **Personalized Learning Systems:** A learning agent might have the goal to "improve students' understanding of algebra." It monitors the student's progress on exercises, adapts teaching materials, and tracks performance metrics like accuracy and completion time, adjusting its approach if the student struggles.
   
   <mark>* **个性化学习系统：** 学习智能体的目标可能是“提高学生对代数的理解”。它监控学生在练习上的进度，调整教学材料，并跟踪准确性和完成时间等性能指标，如果学生遇到困难则调整其方法。</mark>
* **Project Management Assistants:** An agent could be tasked with "ensuring project milestone X is completed by Y date." It monitors task statuses, team communications, and resource availability, flagging delays and suggesting corrective actions if the goal is at risk.
   
   <mark>* **项目管理助手：** 智能体可以被赋予“确保项目里程碑 X 在 Y 日期前完成”的任务。它监控任务状态、团队沟通和资源可用性，如果目标存在风险，则标记延迟并建议纠正措施。</mark>
* **Automated Trading Bots:** A trading agent's goal might be to "maximize portfolio gains while staying within risk tolerance." It continuously monitors market data, its current portfolio value, and risk indicators, executing trades when conditions align with its goals and adjusting strategy if risk thresholds are breached.
   
   <mark>* **自动交易机器人：** 交易智能体的目标可能是“在风险容忍范围内最大化投资组合收益”。它持续监控市场数据、当前投资组合价值和风险指标，在条件符合目标时执行交易，如果违反风险阈值则调整策略。</mark>
* **Robotics and Autonomous Vehicles:** An autonomous vehicle's primary goal is "safely transport passengers from A to B." It constantly monitors its environment (other vehicles, pedestrians, traffic signals), its own state (speed, fuel), and its progress along the planned route, adapting its driving behavior to achieve the goal safely and efficiently.
   
   <mark>* **机器人和自动驾驶车辆：** 自动驾驶车辆的主要目标是“安全地将乘客从 A 点运送到 B 点”。它不断监控环境（其它车辆、行人、交通信号）、自身状态（速度、燃料）以及沿计划路线的进度，调整驾驶行为以安全高效地到达目的地。</mark>
* **Content Moderation:** An agent's goal could be to "identify and remove harmful content from platform X." It monitors incoming content, applies classification models, and tracks metrics like false positives/negatives, adjusting its filtering criteria or escalating ambiguous cases to human reviewers.
   
   <mark>* **内容审核：** 智能体的目标可能是“识别并删除平台 X 上的有害内容”。它监控输入内容，应用分类模型，并跟踪误报/漏报等指标，调整过滤标准或将不确定的情况升级到人工审核。</mark>

This pattern is fundamental for agents that need to operate reliably, achieve specific outcomes, and adapt to dynamic conditions, providing the necessary framework for intelligent self-management.

<mark>对于需要可靠运行、实现特定结果并适应动态条件的智能体来说，这种模式是基础，它为智能化的自我管理提供了必要的框架。</mark>

## Hands-On Code Example | <mark>实战示例</mark>

To illustrate the Goal Setting and Monitoring pattern, we have an example using LangChain and OpenAI APIs. This Python script outlines an autonomous AI agent engineered to generate and refine Python code. Its core function is to produce solutions for specified problems, ensuring adherence to user-defined quality benchmarks.

<mark>为了说明目标设定与监控模式，我们有一个使用 LangChain 和 OpenAI API 的示例。这个 Python 脚本概述了一个自主 AI 智能体，专门用于生成和优化 Python 代码。其核心功能，是为特定问题生成解决方案，并确保符合用户定义的质量基准。</mark>

It employs a "goal-setting and monitoring" pattern where it doesn't just generate code once, but enters into an iterative cycle of creation, self-evaluation, and improvement. The agent's success is measured by its own AI-driven judgment on whether the generated code successfully meets the initial objectives. The ultimate output is a polished, commented, and ready-to-use Python file that represents the culmination of this refinement process.

<mark>它采用“目标设定和监控”模式，不只是生成一次代码，而是进入创建、自我评估和改进的迭代循环。智能体的成功，通过其自身的 AI 驱动判断来衡量，即生成的代码是否满足初始目标。最终输出一个经过润色、注释完整、可随时使用的 Python 文件，代表了这一优化过程的最终成果。</mark>

 **Dependencies**:

<mark>**依赖项：**</mark>

| `pip install langchain_openai openai python-dotenv .env file with key in OPENAI_API_KEY` |
| :---- |

You can best understand this script by imagining it as an autonomous AI programmer assigned to a project (see Fig. 1). The process begins when you hand the AI a detailed project brief, which is the specific coding problem it needs to solve.

<mark>您可以把它想象为，一个被分配到项目的自主 AI 程序员，这样可以更好地理解这个脚本（见图 1）。当您向 AI 提供详细的项目简报时 - 就是它需要解决的特定编程问题 - 它就开始工作了。</mark>

```python
# MIT License
# Copyright (c) 2025 Mahtab Syed
# https://www.linkedin.com/in/mahtabsyed/

"""
Hands-On Code Example - Iteration 2
- To illustrate the Goal Setting and Monitoring pattern, we have an example using LangChain and OpenAI APIs:

Objective: Build an AI Agent which can write code for a specified use case based on specified goals:
- Accepts a coding problem (use case) in code or can be as input.
- Accepts a list of goals (e.g., "simple", "tested", "handles edge cases")  in code or can be input.
- Uses an LLM (like GPT-4o) to generate and refine Python code until the goals are met. (I am using max 5 iterations, this could be based on a set goal as well)
- To check if we have met our goals I am asking the LLM to judge this and answer just True or False which makes it easier to stop the iterations.
- Saves the final code in a .py file with a clean filename and a header comment.
"""

import os
import random
import re
from pathlib import Path
from langchain_openai import ChatOpenAI
from dotenv import load_dotenv, find_dotenv

# 🔐 Load environment variables
# 🔐 加载环境变量
_ = load_dotenv(find_dotenv())
OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")
if not OPENAI_API_KEY:
   raise EnvironmentError("❌ Please set the OPENAI_API_KEY environment variable.")
   # ❌ 请设置 OPENAI_API_KEY 环境变量

# ✅ Initialize OpenAI model
# ✅ 初始化 OpenAI 模型
print("📡 Initializing OpenAI LLM (gpt-4o)...")
llm = ChatOpenAI(
   model="gpt-4o", # If you dont have access to got-4o use other OpenAI LLMs
                  # 如果你没有 gpt-4o 的访问权限，可以使用其他 OpenAI LLM
   temperature=0.3,
   openai_api_key=OPENAI_API_KEY,
)

# --- Utility Functions ---
# --- 实用工具函数 ---

def generate_prompt(
   use_case: str, goals: list[str], previous_code: str = "", feedback: str = ""
) -> str:
   print("📝 Constructing prompt for code generation...")
   # 📝 正在构建代码生成的提示词...
   base_prompt = f"""
You are an AI coding agent. Your job is to write Python code based on the following use case:

Use Case: {use_case}

Your goals are:
{chr(10).join(f"- {g.strip()}" for g in goals)}
"""
   if previous_code:
       print("🔄 Adding previous code to the prompt for refinement.")
       # 🔄 将之前的代码添加到提示词中进行改进
       base_prompt += f"\nPreviously generated code:\n{previous_code}"
   if feedback:
       print("📋 Including feedback for revision.")
       # 📋 包含反馈信息用于修订
       base_prompt += f"\nFeedback on previous version:\n{feedback}\n"

   base_prompt += "\nPlease return only the revised Python code. Do not include comments or explanations outside the code."
   # 请只返回修订后的 Python 代码。不要包含代码之外的注释或解释
   return base_prompt

def get_code_feedback(code: str, goals: list[str]) -> str:
   print("🔍 Evaluating code against the goals...")
   # 🔍 正在根据目标评估代码...
   feedback_prompt = f"""
You are a Python code reviewer. A code snippet is shown below. Based on the following goals:

{chr(10).join(f"- {g.strip()}" for g in goals)}

Please critique this code and identify if the goals are met. Mention if improvements are needed for clarity, simplicity, correctness, edge case handling, or test coverage.

Code:
{code}
"""
   return llm.invoke(feedback_prompt)

def goals_met(feedback_text: str, goals: list[str]) -> bool:
   """
   Uses the LLM to evaluate whether the goals have been met based on the feedback text.
   Returns True or False (parsed from LLM output).
   """
   # 使用 LLM 根据反馈文本评估目标是否达成
   # 返回 True 或 False（从 LLM 输出解析）
   review_prompt = f"""
You are an AI reviewer.

Here are the goals:
{chr(10).join(f"- {g.strip()}" for g in goals)}

Here is the feedback on the code:
\"\"\"
{feedback_text}
\"\"\"

Based on the feedback above, have the goals been met?

Respond with only one word: True or False.
"""
   # 你是一个 AI 评审员
   #
   # 目标如下：
   # {chr(10).join(f"- {g.strip()}" for g in goals)}
   #
   # 以下是代码的反馈：
   # """
   # {feedback_text}
   # """
   #
   # 根据以上反馈，目标是否已经达成？
   #
   # 请只回答一个词：True 或 False
   response = llm.invoke(review_prompt).content.strip().lower()
   return response == "true"

def clean_code_block(code: str) -> str:
   # 清理代码块，移除 markdown 格式的代码块标记
   lines = code.strip().splitlines()
   if lines and lines[0].strip().startswith("```"):
       lines = lines[1:]
   if lines and lines[-1].strip() == "```":
       lines = lines[:-1]
   return "\n".join(lines).strip()

def add_comment_header(code: str, use_case: str) -> str:
   # 为代码添加注释头部
   comment = f"# This Python program implements the following use case:\n# {use_case.strip()}\n"
   # # 此 Python 程序实现了以下用例：\n# {use_case.strip()}\n
   return comment + "\n" + code

def to_snake_case(text: str) -> str:
   # 将文本转换为蛇形命名法 (snake_case)
   text = re.sub(r"[^a-zA-Z0-9 ]", "", text)
   return re.sub(r"\s+", "_", text.strip().lower())

def save_code_to_file(code: str, use_case: str) -> str:
   print("💾 Saving final code to file...")
   # 💾 正在保存最终代码到文件...

   summary_prompt = (
       f"Summarize the following use case into a single lowercase word or phrase, "
       f"no more than 10 characters, suitable for a Python filename:\n\n{use_case}"
   )
   # 将以下用例总结为单个小写单词或短语，不超过 10 个字符，适合作为 Python 文件名
   raw_summary = llm.invoke(summary_prompt).content.strip()
   short_name = re.sub(r"[^a-zA-Z0-9_]", "", raw_summary.replace(" ", "_").lower())[:10]

   random_suffix = str(random.randint(1000, 9999))
   filename = f"{short_name}_{random_suffix}.py"
   filepath = Path.cwd() / filename

   with open(filepath, "w") as f:
       f.write(code)

   print(f"✅ Code saved to: {filepath}")
   return str(filepath)

# --- Main Agent Function ---
# --- 主要智能体函数 ---

def run_code_agent(use_case: str, goals_input: str, max_iterations: int = 5) -> str:
   # 运行代码智能体的主要函数
   goals = [g.strip() for g in goals_input.split(",")]

   print(f"\n🎯 Use Case: {use_case}")
   print("🎯 Goals:")
   for g in goals:
       print(f"  - {g}")

   previous_code = ""
   feedback = ""

   for i in range(max_iterations):
       print(f"\n=== 🔁 Iteration {i + 1} of {max_iterations} ===")
       # === 🔁 第 {i + 1} 次迭代，共 {max_iterations} 次 ===
       prompt = generate_prompt(use_case, goals, previous_code, feedback if isinstance(feedback, str) else feedback.content)

       print("🚧 Generating code...")
       # 🚧 正在生成代码...
       code_response = llm.invoke(prompt)
       raw_code = code_response.content.strip()
       code = clean_code_block(raw_code)
       print("\n🧾 Generated Code:\n" + "-" * 50 + f"\n{code}\n" + "-" * 50)
       # 🧾 生成的代码：

       print("\n📤 Submitting code for feedback review...")
       # 📤 正在提交代码进行反馈审查...
       feedback = get_code_feedback(code, goals)
       feedback_text = feedback.content.strip()
       print("\n📥 Feedback Received:\n" + "-" * 50 + f"\n{feedback_text}\n" + "-" * 50)
       # 📥 收到的反馈：

       if goals_met(feedback_text, goals):
           print("✅ LLM confirms goals are met. Stopping iteration.")
           # ✅ LLM 确认目标已达成。停止迭代。
           break

       print("🛠️ Goals not fully met. Preparing for next iteration...")
       # 🛠️ 目标未完全达成。准备下一次迭代...
       previous_code = code

   final_code = add_comment_header(code, use_case)
   return save_code_to_file(final_code, use_case)

# --- CLI Test Run ---
# --- 命令行测试运行 ---

if __name__ == "__main__":
   print("\n🧠 Welcome to the AI Code Generation Agent")
   # 🧠 欢迎使用 AI 代码生成智能体

   # Example 1
   # 示例 1
   use_case_input = "Write code to find BinaryGap of a given positive integer"
   goals_input = "Code simple to understand, Functionally correct, Handles comprehensive edge cases, Takes positive integer input only, prints the results with few examples"
   run_code_agent(use_case_input, goals_input)

   # Example 2
   # 示例 2
   # use_case_input = "Write code to count the number of files in current directory and all its nested sub directories, and print the total count"
   # goals_input = (
   #     "Code simple to understand, Functionally correct, Handles comprehensive edge cases, Ignore recommendations for performance, Ignore recommendations for test suite use like unittest or pytest"
   # )
   # run_code_agent(use_case_input, goals_input)

   # Example 3
   # 示例 3
   # use_case_input = "Write code which takes a command line input of a word doc or docx file and opens it and counts the number of words, and characters in it and prints all"
   # goals_input = "Code simple to understand, Functionally correct, Handles edge cases"
   # run_code_agent(use_case_input, goals_input)

```
译者注：[Colab 代码](https://colab.research.google.com/drive/1553L0BIxqhPFS6RHiLnF_ELjEkWZpqsC?usp=drive_open) 已维护在[此处](/codes/17-Chapter-11-Goal-Setting-and-Monitoring-Example.py)。

Along with this brief, you provide a strict quality checklist, which represents the objectives the final code must meet—criteria like "the solution must be simple," "it must be functionally correct," or "it needs to handle unexpected edge cases."

<mark>除了这个简报，您还提供一个严格的质量检查清单，这代表了最终代码必须满足的目标——诸如“解决方案必须简单”、“它必须正确地运行”或“它需要处理意外的边界情况”等标准。</mark>

![][image1]

Fig.1: Goal Setting and Monitor example

<mark>图 1：目标设定与监控示例</mark>

With this assignment in hand, the AI programmer gets to work and produces its first draft of the code. However, instead of immediately submitting this initial version, it pauses to perform a crucial step: a rigorous self-review. It meticulously compares its own creation against every item on the quality checklist you provided, acting as its own quality assurance inspector. After this inspection, it renders a simple, unbiased verdict on its own progress: "True" if the work meets all standards, or "False" if it falls short.

<mark>接到这个任务后，AI 程序员开始工作并生成代码初稿。然而，它不会立即提交这个初始版本，而是暂停下来，去执行一个关键步骤：严格的自我审查。它一丝不苟地，扮演自己的质量保证检查员，将自己的创作与您提供的质量检查清单逐项比较。检查完成后，它对自己的进展给出一个简单、公正的评判：如果工作符合所有标准，则为“True”，如果未达到标准，则为“False”。</mark>

If the verdict is "False," the AI doesn't give up. It enters a thoughtful revision phase, using the insights from its self-critique to pinpoint the weaknesses and intelligently rewrite the code. This cycle of drafting, self-reviewing, and refining continues, with each iteration aiming to get closer to the goals. This process repeats until the AI finally achieves a "True" status by satisfying every requirement, or until it reaches a predefined limit of attempts, much like a developer working against a deadline. Once the code passes this final inspection, the script packages the polished solution, adding helpful comments and saving it to a clean, new Python file, ready for use.

<mark>如果评判结果为“False”，AI 也不会放弃。它会进入一个深思熟虑的修订阶段，利用自我批判的见解来找出弱点，并智能地重写代码。这种起草、自我审查和优化的循环持续进行，朝向目标一次次迭代。这个过程重复进行，直到 AI 满足每一个要求，最终达到“True”状态，或者达到预先设定的尝试次数限制 - 就像一个面对截止日期的开发者一样。一旦代码通过了最终检查，脚本就会打包经过润色的解决方案，添加有用的注释，并将其保存到一个新的 Python 文件中，以待使用。</mark>

**Caveats and Considerations:** It is important to note that this is an exemplary illustration and not production-ready code. For real-world applications, several factors must be taken into account. An LLM may not fully grasp the intended meaning of a goal and might incorrectly assess its performance as successful. Even if the goal is well understood, the model may hallucinate. When the same LLM is responsible for both writing the code and judging its quality, it may have a harder time discovering it is going in the wrong direction.

<mark>**警告和注意事项：** 需要注意的是，这是一个示例性说明，而不是生产就绪的代码。对于实际应用，必须考虑几个因素。LLM 可能无法完全理解目标，可能会错误地评估其表现为成功。即使很好地理解了目标，模型也可能产生幻觉。尤其是当一个 LLM 既负责编写代码又负责判断其质量时，它可能更难发现自己走错了方向。</mark>

Ultimately, LLMs do not produce flawless code by magic; you still need to run and test the produced code. Furthermore, the "monitoring" in the simple example is basic and creates a potential risk of the process running forever.

<mark>最终，LLM 不会神奇地产生完美无缺的代码；您仍然需要运行代码并测试。此外，示例中的“监控”很基础，存在进程永远无法结束的风险。</mark> 

| `Act as an expert code reviewer with a deep commitment to producing clean, correct, and simple code. Your core mission is to eliminate code "hallucinations" by ensuring every suggestion is grounded in reality and best practices. When I provide you with a code snippet, I want you to: -- Identify and Correct Errors: Point out any logical flaws, bugs, or potential runtime errors. -- Simplify and Refactor: Suggest changes that make the code more readable, efficient, and maintainable without sacrificing correctness. -- Provide Clear Explanations: For every suggested change, explain why it is an improvement, referencing principles of clean code, performance, or security. -- Offer Corrected Code: Show the "before" and "after" of your suggested changes so the improvement is clear. Your feedback should be direct, constructive, and always aimed at improving the quality of the code.` |
| :---- |

<mark>**充当专业代码评审员**，深度致力于生成整洁、正确且简单的代码。您的核心使命，是通过确保每个建议都基于实际情况和最佳实践，来消除代码“幻觉”。当我向您提供代码片段时，我希望您：-- **识别和纠正错误：** 指出任何逻辑缺陷、错误或潜在的运行时错误。-- **简化和重构：** 在不牺牲正确性的前提下，提出改善代码可读性、性能和可维护性的修改。-- **提供清晰的解释：** 对于每个建议的变更，引用整洁代码、性能或安全的原则，解释为什么它能改进代码。-- **提供更正后的代码：** 显示您建议变更的前后对比，使改进更清晰。您的反馈应该是直接的、建设性的，并且始终旨在提高代码质量。</mark>

A more robust approach involves separating these concerns by giving specific roles to a crew of agents. For instance, I have built a personal crew of AI agents using Gemini where each has a specific role:

<mark>更健壮的途径，涉及通过给一组智能体分配特定角色来分离这些关注点。例如，我使用 Gemini 构建了一个个人 AI 智能体团队，其中每个智能体都有特定角色：</mark>

* The Peer Programmer: Helps write and brainstorm code.
<mark>* **程序员同伴：** 帮助头脑风暴和编写代码。</mark>
* The Code Reviewer: Catches errors and suggests improvements.
<mark>* **代码评审员：** 发现错误并提出改进建议。</mark>
* The Documenter: Generates clear and concise documentation.
<mark>* **文档编写员：** 生成清晰简洁的文档。</mark>
* The Test Writer: Creates comprehensive unit tests.
<mark>* **测试编写员：** 创建全面的单元测试。</mark>
* The Prompt Refiner: Optimizes interactions with the AI.
<mark>* **提示词优化员：** 优化与 AI 的交互。</mark>

In this multi-agent system, the Code Reviewer, acting as a separate entity from the programmer agent, has a prompt similar to the judge in the example, which significantly improves objective evaluation. This structure naturally leads to better practices, as the Test Writer agent can fulfill the need to write unit tests for the code produced by the Peer Programmer.

<mark>在这个多智能体系统中，代码评审员作为与程序员智能体分离的实体，具有类似于示例中评判者的提示词，这使得评估更加客观。这种结构，自然带来更好的实践，因为测试编写员智能体可以满足为同伴程序员生成的代码编写单元测试的需求。</mark>

I leave to the interested reader the task of adding these more sophisticated controls and making the code closer to production-ready.

<mark>添加更复杂的控制并使代码更接近生产就绪，这个任务就留给感兴趣的读者了。</mark>

## At a Glance | <mark>要点速览</mark>

**What**: AI agents often lack a clear direction, preventing them from acting with purpose beyond simple, reactive tasks. Without defined objectives, they cannot independently tackle complex, multi-step problems or orchestrate sophisticated workflows. Furthermore, there is no inherent mechanism for them to determine if their actions are leading to a successful outcome. This limits their autonomy and prevents them from being truly effective in dynamic, real-world scenarios where mere task execution is insufficient.

<mark>**是什么：** AI 智能体通常缺乏明确的方向，使它们无法有目的地行动，只能执行简单的反应式任务。如果没有定义目标，它们就无法独立处理复杂的多步骤问题或编排复杂的工作流程。此外，它们没有内嵌的机制来确定自己的行动是否会带来成果。这限制了它们的自主性，阻碍了它们在动态的现实场景中真正发挥作用，因为这种场景下，仅执行任务是不够的。</mark>

**Why**: The Goal Setting and Monitoring pattern provides a standardized solution by embedding a sense of purpose and self-assessment into agentic systems. It involves explicitly defining clear, measurable objectives for the agent to achieve. Concurrently, it establishes a monitoring mechanism that continuously tracks the agent's progress and the state of its environment against these goals. This creates a crucial feedback loop, enabling the agent to assess its performance, correct its course, and adapt its plan if it deviates from the path to success. By implementing this pattern, developers can transform simple reactive agents into proactive, goal-oriented systems capable of autonomous and reliable operation.

<mark>**为什么：** 目标设定与监控模式，通过将目的感和自我评估，嵌入到智能体系统中来提供标准化解决方案。它涉及明确定义智能体要实现的清晰、可测量的目标。同时，它建立了一个监控机制，持续跟踪智能体的进度，并且对比目标与环境状态。这创建了一个关键的反馈循环，使智能体能够评估其表现，纠正其路线，并在偏离成功路径时调整其计划。通过实施这种模式，开发人员可以将简单的反应式智能体转变为能够自主可靠运行的主动的、目标导向的系统。</mark>

**Rule of thumb**: Use this pattern when an AI agent must autonomously execute a multi-step task, adapt to dynamic conditions, and reliably achieve a specific, high-level objective without constant human intervention.

<mark>**经验法则：** 当 AI 智能体必须自主执行多步骤任务、适应动态条件，并在没有持续人工干预的情况下，可靠地实现特定的、高层次的目标时，请使用这种模式。</mark>

**Visual summary** | <mark>**可视化总结**：</mark>

![][image2]

Fig.2: Goal design patterns

<mark>图 2：目标设计模式</mark>

## Key takeaways | <mark>核心要点</mark>

Key takeaways include:

<mark>核心要点包括：</mark>

* Goal Setting and Monitoring equips agents with purpose and mechanisms to track progress.
<mark>* 目标设定与监控，为智能体提供了目的感和进度跟踪机制。</mark>
* Goals should be specific, measurable, achievable, relevant, and time-bound (SMART).
<mark>* 目标应该是具体的、可测量的、可实现的、相关的和有时限的 (SMART)。</mark>
* Clearly defining metrics and success criteria is essential for effective monitoring.
<mark>* 明确定义指标和成功标准，对于有效监控至关重要。</mark>
* Monitoring involves observing agent actions, environmental states, and tool outputs.
<mark>* 监控，涉及观察智能体行动、环境状态和工具输出。</mark>
* Feedback loops from monitoring allow agents to adapt, revise plans, or escalate issues.
<mark>* 来自监控的反馈循环，允许智能体适应、修订计划或升级问题。</mark>
* In Google's ADK, goals are often conveyed through agent instructions, with monitoring accomplished through state management and tool interactions.
<mark>* 在 Google 的 ADK 中，目标通常通过智能体指令传达，监控则通过状态管理和工具交互来完成。</mark>

## Conclusion | <mark>结语</mark>

This chapter focused on the crucial paradigm of Goal Setting and Monitoring. I highlighted how this concept transforms AI agents from merely reactive systems into proactive, goal-driven entities. The text emphasized the importance of defining clear, measurable objectives and establishing rigorous monitoring procedures to track progress. Practical applications demonstrated how this paradigm supports reliable autonomous operation across various domains, including customer service and robotics. A conceptual coding example illustrates the implementation of these principles within a structured framework, using agent directives and state management to guide and evaluate an agent's achievement of its specified goals. Ultimately, equipping agents with the ability to formulate and oversee goals is a fundamental step toward building truly intelligent and accountable AI systems.

<mark>本章重点讨论了目标设定与监控这一关键范式。我强调了这一概念如何将 AI 智能体从纯粹的反应式系统转变为主动的、目标驱动的实体。文本强调了明确定义可测量目标和建立严格监控程序以跟踪进度的重要性。实际应用展示了这一范式如何在各个领域（包括客户服务和机器人技术）支持可靠的自主操作。一个概念性编码示例，说明了在结构化框架内实现这些原则，使用智能体指令和状态管理，来指导和评估智能体实现其指定目标的能力。最终，为智能体配备制定和监督目标的能力，是构建真正智能和负责任的 AI 系统的基石。</mark>

## References | <mark>参考文献</mark>

1. SMART Goals Framework. [https://en.wikipedia.org/wiki/SMART\_criteria](https://en.wikipedia.org/wiki/SMART_criteria) 
   
   <mark>SMART 目标框架 [https://en.wikipedia.org/wiki/SMART\_criteria](https://en.wikipedia.org/wiki/SMART_criteria) </mark>

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnAAAAG4CAIAAABKIk2wAABXF0lEQVR4Xu2dd7wV1bm/Z5fTG0VBRYpeFBE0oGh+VhTsig3r1UQURY1ivDERNTG2iJqouRbwKqLXFhU1WANirtgjiqJgEAkaUapwetunzu+b9WYvZmbts8sp++zyff7Yn9lr1tTznnn2u2bNGssmhBBCSJexvAWEEEIISRwKlZDYtLe3t7S0yIQg0/hsbW3FJ+ZiQkoIIdkJhUpIDESZenr58uXPP//8rFmzXnzxxfXr17e1tYlrCSFZDoVKSFysXLnS5/NZCr/fj0/9NRAIbN26FXUgV+9ihJCsgUIlpEOam5uRfe611175+fkQ5zfffCPK1OJsb2+vq6s7/vjjxazIX5mtEpK1UKiERGP8+PFFRUX33nuv7b5pKqBEy3XixInFxcX33HOPnksIySooVEIiIKbce++9kXdWV1fH2dvo0EMPRf1nnnkmzvqEkEyCQiUkAg0NDWeccQbsuGLFivjvjLa0tJxyyik+n89WzcXe2YSQjIZCJSQCDzzwgN/vX758uTww42zmjYJUnjZtGkwMDTNPJSSroFAJiQCMOG7cuE70MJJ+SVj88ccfp1AJySooVEK8QIrSZdc7Iw4aGxvxOXDgQKzBO48QktHwf54QL5dddtmee+7ZifRUA61CqPX19d4ZhJDMhUIlxEV7e7vP5/vqq6+8MxIEQp08eXL8HZoIIekOhUqIF+mm20UCgUBOTo63lBCSuVCohHjx+/1dae8VdtttNziVD88Qkj1QqIR46Zb+RMOHD4eYvaWEkMylGy4chGQMcstThNrFh16Qnsp6OtdbmBCSdlCohGyjVQERfvDBB955iSCPol566aUy7Z1NCMlEKFRCvDzxxBN9+vSxu5CkLlmyJBgMsosvIVkFhUqIF8kvQ6GQd0Z8YPF+/fp1emgIQkiaQqES4kWECinCqZ1LUrH4O++8wwyVkKyCQiUkAq+++iqk+NFHH8nXmFqVx2OamppqamrkJW7eGoSQTIf/9oR4kW5E11xzTU5Ozpw5cyTRjOlU4YgjjvD5fOJXNvkSklVQqIR0yMSJEwOBQHl5uXx19tc1/Qp99uvXLy8vr+vDFhJC0hEKlZAOgSPPOuus3NzcKVOmSInuqaTTVt3YC5sGg8EFCxbU1NSEV0AIySIoVEI6RKzZ0NBQWloKWZaUlNx///0bN27UFVatWnXwwQf7fD7LssaOHStyNZNXQkg2QKES8i9gTVs16n700UeWIj8//+abb7ZVVgpHVlRUFBUVySzIVSZATk7OhAkTbOVRCBjVCgsLZdbw4cPXrFljh7ss8ZYqIZkNhUrIv9lvv/2Qa0KQcOHUqVMnTZqECWSlzjpQZn19/WeffbZs2bKVK1dWVVXZyrgwMXz54Ycfon5ubu7MmTOHDh2qpXvttdc6V0IIyUgoVJKlIGvUnYwOPvhg8ehjjz3mrPPFF19Ic+706dNR2dndV5YVj6Jk3bp1I0eORM3+/ft7RoQYO3asaHX27Nk281RCMhcKlWQvcBuUCdVtt912+IrU01OhpqZGuh3tuuuuOt3s27fvSSeddO655x5zzDFIRqXQ7/ePGzfONkbuFX02NTV9//330hRcW1trh+/OEkIyCQqVZClQGlJGGG7mzJlOvTm7FIkOUQIjYvqtt97SDbm+MDfeeOPGjRslfxWbemQpX7EGW42gFAwGv/76a2cFQkhmQKGSrEN6Dz366KPQ24QJExLtlOus34n3h0vbsrc0DqDkUCgkjm9oaGhsbPTWIIT0Kp35xyYkfYGWYMF169b5/f5ly5bZnbqpCR+LVhOVMaitrT355JPz8vK8M6IiG3rzzTclP/bOJoSkAPzPJFlHXV1dIBDYZ599OpFfdguQOnS+1157VVdXR3mnDXLQf72dVfl+0aJFolIwf/58b1VCSApAoZKs49Zbbw0Gg3JTs7e4++67ocZNmzZ1lB/L7Vgo/9JLLxWP4keAPP/KDk2EpCYUKskuoCg4adSoUXakbr1JA4mppd4Q11GWDGueddZZcsMVKrVUR2Kfzzdp0qQoSS0hpBehUEkWgXRwypQpVm/fg0Ry3NDQ0N7eDlOaA/8uXrxYUlJ5BNaJZKiwrO5jTHoL+Yvwxw1x0stXFkKShvTrKSoq2nvvvTtqaE0a0mwLoe65556eWdBtS0vLww8/7HJpmOuuu27Tpk1bSG/z4Ycf+sLv6SNEoFBJtiCjGuEiKJ17ex049cgjj7RUuhzxtih+Aaxdu9YXHg3Rr5D6pNf55z//yb8F8cCAIFnE7Nmz4SdvaS8BwVdXV1sddDKSfFoe8sHE66+/np+fL42Nr776qrc2SToUKjFhQJAs4oQTTkidi2CzAkmnHiU4Cu2K1atXW+pOKlsaex0KlZgwIEgWMXr06KKiotbW1hQREvYEQvWWdoxotby83DuDJB0KlZgwIEi2ABUNGTKktLTUO6OXkKxUMtQ4O0nJ7wBUDim8s0kSoVCJCQOCZAsQ6rBhw8rKymTaO1shgxN5SxNHv3MG2jMfjHHCi3KaQqESEwYEyRbiEWp9fX1CbbDROffcc4PBYPT7o7wopykUKjFhQJBsIR6hIrPsxqvk+PHjY64tZgWSmlCoxIQBQbIFCpV0IxQqMWFAkGyBQiXdCIVKTBgQJFugUEk3QqESEwYEyRYoVNKNUKjEhAFBsgUKlXQjFCoxYUCQbIFCJd0IhUpMGBAkW6BQSTdCoRITBgTJFihU0o1QqMSEAUGyBQqVdCMUKjFhQJBsgUIl3QiFSkwYECRboFBJN0KhEhMGBMkWQqHQHnvsIUK1lVNN6uvrCwoKvKWJg/XAzUceeWReXl5H25J3seXk5LS2tjY0NDh3laQ+FCoxYUCQLGK77bYLBALnnHPOtGnTLojE+eef7/f7vaWJM3Xq1EsvvbR///4+n++8887zzlZMmTLl8ssvx0W5ra2tqanJu68ktaFQiQkDgmQLSAqvuOKKYDCI66B8mkC33qKuAaF6iwywbxRq2kGhEhMGBCGEJAyFSkwYEIQQkjAUKjFhQBCyjfb29paWFk9hY2OjdCAiREOhEhMGBCEuQqFQfX29zfuaJCoUKjFhQBCyjbq6utraWp/PB6e2trbq8sLCQjNzJdkMhUpMGBCEuGhra4NQbcfgDzCrlGCWlDQ2Noarbyv0NAtjKcyCmHUFkklQqMSEAUGIiyhChR1nzJgRDAZzcnLuuecevcipp56am5vbt29fW421hM8TTzxx/vz5uOCedNJJFGpGQqESEwYEIduQMYw8QgUogRefe+45XEM3btxoqxGOFi1aZKuxA8eMGYOJv/zlL9AqqiF/RWGfPn1Q+NBDD+mVkEyCQiUmDAhCthFFqMhTr7vuOlxDodVtCyihhkIhueF64YUXjhw5UoQqLcBIWJ3rIRkDhUpMGBCEbEOaZz1CxYTf75dpKBO5aTAY3H777UWinsGV+vfvbzuGvG9SyDTJJChUYsKAIGQb4kjJLyFCfMVEbW1tQUGBHb4/Ko4cPnx4SUkJXJufn49Cz+j2WAMT08yGQiUmDAhCvJx77rmTJk2yw0kqrpuXXHIJJs4880xM40qK6Z122umYY45pbGyEa8ePHw/1VlRUWOEGYQo146FQiQkDghAvyEql/TYYDPp8vkGDBlVWVkoOetxxx6Hc7/cfdNBBoVCorq4Ohdtvv31paSkK3377bVkDL7UZD4VKTBgQhMSgurraDrcGy2dTU5MU2upZmogPxkQsJBkDhUpMGBCEeJHWWummKwaFHfVXZ1uuczSllpYWZLFy59U2xnkgGQaFSkwYEIQkjDiVOWg2Q6ESEwYEIYkhNl26dCkmnGMQkqyCQiUmDAhCEsP5rCqT1KyFQiUmDAhCOgOFmuVQqMSEAUFIYkiTL4Wa5VCoxIQBQUhiUKjEplBJJBgQhCQGhUpsCpVEggFBSGJQqMSmUEkkGBCEJAaFSmwKlUSCAUFIYlCoxKZQSSQYEIQkBoVKbAqVRIIBQUhiUKjEplBJJBgQhMQA1pTx7mWgQVOofPVpFkKhEhMGBCExEJvKq09tQ6j42tLS4qhOsgIKlZgwIAiJC4gzNzd37Nix4ldMh0Khb7/9Nj8/v6yszFubZDoUKjFhQBASFxBqcXGxpcjJyZEJEAgEFi9e7K1NMh0KlZgwIAiJCwh16tSpPp9P29Tv9+co2OSbhVCoxIQBQUgC6MRUs2LFitraWm89kulQqMSEAUFIAkybNs0j1La2Nt1fiWQPFCoxYUAQkhi5ublOoXpnk+yAQiUmDAhCEqCpqWnHHXcMBoOBQMDn882bN69N4a1HMh0KlZgwIAhJmKCC19NshkIlJgwIQhImJycnLy/vjjvu8M6IGw6ulO5QqMSEAUFIYoRCoa1bt8rFtHONvTU1NQ8++KC3lKQVFCoxYUCQjMXT+ba9m7DVYISzZ8+Oslp5MlXGVJJPJ9KbqZ1JajpDoRITBgTJZBYuXLjTTjv5/X5c+3zdBNaWl5eHidzc3GAw6J2tEGX2798f+9Dc3OzcJSS1qIAFKdS0hkIlJgwIkmk0NTXBVX/9619LSkoKCgq03pIMtjtixAjPvknmmp+fjwrYT89c6TC8bNkyJLWo6TExSSkoVGLCgCCZBmwKFeXk5Oywww66ubWhocFdKxlI86+nBJ/yyM2Pf/xj5ywNL9NpAYVKTBgQJNOoqKjAlQ7XO++MJKI96rmBivKioiJJYXNzc50VkJIedNBBMisYDB577LHIVs0slqQIFCoxYUCQTGPYsGHI/+Rl4KlGTU2N3NAVzjnnHD2rRXHiiSeiHNKFaHmTNZWhUIkJA4JkDpLSwVhXXnmld15qIMNBCD714poffvhBZml9ymUaB9Lc3Gz2ECYpAoVKTBgQJHOQrA5CXbt2rXdeLyG9kDZt2gRBTpw4UdtUCxUToVBI18chsC9SWkChEhMGBMkcJJ/DZW79+vUp0l4KWcrgD7vssot07tVJqu5+nJubC+/ydml6QaESEwYEyRy0UNetW+ed10vApsuXL+/bt6+404n4VYBlb775Zu/CJIWhUIkJA4JkDiLUnJycrVu3euclHezMJ598MnLkyG0KjUVeXt7TTz/d2NiIZevr6+X5H+96SWpAoRITBgTJNLSftg1clBSKi4ux9Y8++khemAqvO7sgxUkgEJBuwMhfBwwY0CuPz5J4oFCJCQOCZBpw25o1axqTSygUEvl999132o7OV5GLdPVXJ85ysamY+Oijj/YeG0kZKFRiwoAgmYbVe/dQm5ubq6qqZICkpqamp556Sm6UdqRSwTn3qquuWr9+vfQNZjelVIZCJSYMCJJpWKnUyxfU19fvs88+4stAIODsi2SplFSSV5jYNt6TSqemLBQqMWFAkEwjpYQqu9Ha2nrbbbc5PSoUFBRAqDvssIOzsuYXv/hFTk4OnZqaUKjEhAFBMg0rlYQq1NXVIU998sknPempIHVkh/VuY+LSSy8tLCzUKyEpBYVKTBgQJNOwogpVD+bX06P69e/f/8477/QUOj0qwyR9++23njpCW1vbFVdcgQoc1Dc1oVCJCQOCZBrRhQoaw+Pm9+hTnpbqrOvZjZaWFmcXpHnz5jnnOqFQUxwKlZgwIEim0ZFQGxoaYCko7b333uvTpw+qHXjggZ46XQF6DoVCIumrrrpKHoCpq6vzVBswYIAV7osU5QVtFGqKQ6ESEwYEyTQ6EqqtctMpU6YEAoH+/fvvt99+kiZ6K3UBPQ6DrFnAnkgPXpErjC7lQ4YMcQ6L74FCTXEoVGLCgCCZhtWBUNvVSH6Y+/HHH9vhe6ijRo3Kz8/31Ow0WqJwtnMCyahsRfLX4uJiS4k2SpszhZriUKjEhAFBMg2rA6GCV155JScnx3b3SILtoD0ki/X19duqJohsDqvSoyMFFUVFRTI9evRoqQlTimVdyxtQqCkOhUpMGBAk0+hIqE1NTTU1NZi7evVqfecSEoWxRIHl5eXuJRJGGnWXLl0qK5T+R3pPkI/KtKUyV+eCJhRqikOhEhMGBMk0OhKqIKqrqKiwHbc8bZVc5uXl2eFXgneR4447DitEYorLrneeGkD/xBNP9Ja6oVBTHAqVmDAgSKYRXahg/PjxAwcOhLH08zOSsMqDoa6qXSA/Pz83NxdbMd8YE6UvkoZCTXEoVGLCgCCZRkyhgrPPPhvVnH2CpD3WUu20joqdx+/377nnnnYHI0hE6Y4kUKgpDoVKTBgQJNOIKVSZVVZWhiQS6aOzjRc5q6Ve9L2tdmdB1mvmpvFDoaY4FCoxYUCQTCO6UCEqPX3EEUcgH/VoDyIcPHjwwIEDu9LpV7bS0aAN8UChpjgUKjFhQJBMI7pQNSKqU089VfJRp2httZIvvvjCWZJkKNQUh0IlJgwIkmnEKVRbSUvaeAGmnYug5Prrr3fUTTYUaopDoRITBgTJNOIXKnjuuedyc3O/++4729FCK72TPvvsM1fV5EKhpjgUKjFhQJBMI06h1tXV9evXL2L/o4KCgtLS0phr6FEo1BSHQiUmDAiSacQp1MGDB6PmkiVLnI+1QGNIWP1+v6Ni70ChpjgUKjFhQJBMI7pQ4Sfkps8++2wwGHS+3Bv1Q6EQli0pKamsrJRCeVq0NRH0CrsIhZriUKjEhAFBMo3oQoUjZ8+eHQgEvvjiC88ogxdccAGWra6uttUAhHJL9Sc/+cmYRDjkkENso89wJ6BQUxwKlZgwIEim0ZFQpWTw4MEFBQVLlizR5TJGkrxyXEpEh9OnT0e2OnTo0AfDPBQHhx56KNbz8ssv19fX8znUDIZCJSYMCJJpdCRU8O233/p8vmXLlukSeVoGi+Tm5iIr1ZllY2NjXl7e1KlTE5VieXk51i/jF8YzZm9HUKgpDoVKTBgQJNPoSKgouemmm6A6Z3ss8khLva9U3rym2bBhg7w5tXN0/VJLoaY4FCoxYUCQTKMjoYJPP/0Uc6uqqiTvRJ2+ffsWFRXJXGeXIlSAZR9++OFEM1R5UXlhYaF3RoJQqCkOhUpMGBAk0+hIqOJLS/HXv/511apVJSUlmNZdk/QimIDPRowYgbkzZ87cnAivvvoqljrvvPPCm+0kFGqKQ6ESEwYEyTRwmfv++++j9LMVp/oVyFa9sx2MHj0adaR+QnhX1ClEqG0K7zzS21CoxIQBQTIHyTUtlaF654VpV8hEmxrLN4quQqGQfgl5nGC1ibYSR6S5uZlCTWUoVGLCgCCZg5jS5/MtX748yhu89SxpBI4yGgPUmGhza5t7kP1Og7069thjkR93i55Jt0OhEhMGBMkcYEr4LBgMjhkzplus1ovU1NQEAoHBgwd7Rp8gKQKFSkwYECTTOPvsszPgSrdq1Sqk2uXl5XZ3jLtEuh0KlZgwIEgG4vf7kdvZanwGO32EpO/vAqSnp59+uns+SSEoVGLCgCCZRktLiwxzn5ubizxPCqPcKE0dxKZz5szBzu++++52+vwUyEIoVGLCgCCZSUVFhXqAxUKqJxMpjs/nk4mcnJyxY8d6j4ekGBQqMWFAkIxFevPecsst11xzzXXXXXdNanPttdfOmDHjqaeeslXvYu/BkBSDQiUmDAiSsbS0tMg91LToKKsbpdO9f3KWQKESEwYEIf8C0hWTdeUVMSR7oFCJCQOCZDWtCplubm6uqanp0e5LaZErk3igUIkJA4JkL+3hN6FKb6BgMIjp1atXy1zpYQvLNjQ02GEX6lGW6urqzC64KGlW2KqmuFnGOJTXw02ePBkXYvdCJC2hUIkJA4JkL1BdUVGRDJYr8tt7770DgYDz3aj6jqbIUmoCsawTZLe2w7gRycnJqaioYJ+jDIBCJSYMCJK9SIZqh3vV4itUaqk3pp122mnr16/H9H777Ye5H3/88bBhw/D15ptvlmWnTJlSWVl52GGH+f3+xx9/HCUHHHAAKvz5z3+21YASxxxzzFdffQU9Dx8+fMuWLRDwCy+8AKGedNJJr7zyyradIOkJhUpMGBAke4FBITw7PAhwS0vLZZdd5vP5MCGNwFVVVaeeeurXX39dUFDwwAMPwIvQ54QJE7BIfn5+cXHxvHnzYNBgMAhTLl68WN4PY6v2YUs9AltfXz958mQpnD9/PhanUDMDCpWYMCBI9gKh5uXlWeruqYz/UFJSIuWYXrZsWSgU2rp1K6YXLVokd0xlFhJQ1JwxY4asByVLlizBRG1tLXwMidrqpTdIbZHsQq7w8S9/+UuZ2LBhgx2rZZikPhQqMWFAkOxFN/ma5dCh7j2ETLSysrJdAa3CwchcS0tL77//fqmAvHPdunVSQYQKj+o1o/D0008fN26crdQb/ZXmJF2gUIkJA4JkL3EKFXXef/996eUrs5BfRheqrTJUO5yJ9uvXb/r06bIq6btE0h0KlZgwIEj2Eo9QMf3yyy/j69KlSzdv3gyPFhYWQpkxhYo1DxgwIBQK3XXXXXorwWBQj9dP0hoKlZgwIEj20pFQAaypM1TklHPnzg0EAmVlZYceeqgUQpb33XefDG0IiUKoUg5lyugQWPMjjzyCz/z8fFRrUUyZMgUl559/vlQm6QuFSkwYECR7gVDtDt7s5iyEDiX7lH5JDQ0NesQG29G9SC+Ccunl++/l1SwshZpYFfJXTNTW1uq5JB2hUIkJA4KQhBG/2lEH/vX7/d4ikkFQqMSEAUFIYughCfV0R4h0SUZCoRITBgQhnWHevHkNDQ1yD9VEWn2j65akNRQqMWFAEJIw8KhcTPn2mKyFQiUmDAhCEkaP28BG3ayFQiUmDAhCEkMkKuM2sFE3a6FQiQkDgpDEoFCJTaGSSDAgCEkMCpXYFCqJBAOCkMSgUIlNoZJIMCAISQwKldgUKokEA4KQxKBQiU2hkkgwIAhJDAqV2BQqiQQDgpC4aFeD4+tRfJ1C5dOoWQiFSkwYEITEwPM6GlOoJAuhUIkJA4KQuKitrRWVeoQa8e1vJOOhUIkJA4KQ2Eh7Ly6gI0eOlHeJY7qxsXHhwoWYKCkp8S5AMh0KlZgwIAiJgbTrilDz8vJycnIwEQwG8en3+/H56aefepchmQ6FSkwYEITEy5133mlFQt6NSrIKCpWYMCAIiRd5yYyHNWvWeOuRLIBCJSYMCEIS4Pzzz/cI1VuDZAcUKjFhQBASL9K/V+6h4tPn8+Xn56OkqanJW5VkOhQqMWFAEJIAzc3Ne+65ZzAY9Pv9gUBg4cKF3hokO6BQiQkDgpDEkDupyFAhVO88kjVQqMSEAUFIwpSWluJi+sgjj3hnkKyBQiUmDAhCEqahoYEX0yyHQiUmDAiSgchwgD000C5W3tjY+Kc//UmmvbO7TEtLi80B91MeCpWYMCBIBtLc3FxXVzdjxgxLDWbUvWCdPp9PPTJjBQIB7+zu4LnnnnO+2YakIBQqMWFAkAwEQs3LyxPnpR2QND4LCwv5NE4qQ6ESEwYEyTRaW1vLysrGjBljq5udbemGHAWS4F122YUZaspCoRITBgTJKGBTyfC8M9KNxsZGHMiMGTPklipJNShUYsKAIJlDKBRqbm4OBoNz585N99wOQh04cGBpaSmFmppQqMSEAUEyDVzmVq5c6S1NQy688EK5ZOOHgnce6W0oVGLCgCCZBi5z69evT/cMta2t7YorrsCxtLa2pvuxZCQUKjFhQJBMg0IlSYBCJSYMCJJpJEeoujuuZ7q7oFBTHAqVmDAgSKaRHKHa6mlXGeHhrbfe8s7rMhRqikOhEhMGBMk0kiNUyUrz8vL8fr93XndAoaY4FCoxYUCQTCM5QoXn4DxLgVTVO7vLUKgpDoVKTBgQJNNIjlDBBx98EAgEgsGgd0Z3QKGmOBQqMWFAkEyj24Xa0dAKJ598Mmy6aNEiZKhSp1XhrdcpKNQUh0IlJgwIkml0o1B1991Zs2Z5tArPSXtveXm5lDz77LNS3l2bplBTGQqVmDAgSKbRjUIFdXV1fr//qKOO8s5QG3JeUgOBwB577OGY3yUo1BSHQiUmDAiSaXSXUJuamsaPHy9D7Z9wwgne2bYdDAadl1Txa05OzgMPPAALIqPtypCBFGqKQ6ESEwYEyTS6LtTm5maxo8YU6uWXXy4Podrhm6xSUwqLi4uffPLJrtxPpVBTHAqVmDAgSKZhJS5USSUbGxvxifyypKRE7Cg5aN++fT0PxmDlw4YNQzKK/FVK4NSNGzfKUgJmYcFNmzbpG7F1dXXbVhELCjXFoVCJCQOCpDQ1NTUQVZvCO68DrMSFqrvpah1KognuueceT2XZE6kwe/Zs5yxs9LDDDvOsYebMmTJXhB0nFGqKQ6ESEwYESXUmTpwIOfn9/n/84x9QS0cPsWisRITa0NBgK9UVFhaKApF34rOoqKiystJbOwxW7rmB6uG4445DhpqXl4e1oSY+99tvPyyFVFjagWOOBUGhpjgUKjFhQJA0QFI9kJ+f/80333hnu4lTqLrC0KFDZeXiSGj1pJNOgvDEtR0hi3hLHTQ1NYmb8VNAejaBqqqq2tpanRBHgUJNcShUYsKAIKkO0seSkhLtJCHKePRWfELFaj/++GNxngBb9+3bFx6tq6uL0sIss1AfCWhH1WBTmbV06VLUzM3NtcKNwCNHjoyn9y+FmuJQqMSEAUG8/PDDD+UpQ2VlJT6XLFmib0k6ufbaa5HwedqBrfiECmPp3NRSLb0QmLdSByxYsACCP+aYY2K23ArODYE333yTGWq6Q6ESEwYEceG87qcIUKkzj9SF0kKL5K+mpsaZKVqJC3X06NHSY6ijjNMJ6ki6vGzZsnjq19fXy0RxcbFsjkLNAChUYsKAIC5wjfjTn/7kLe09pHX0F7/4haUeRPH7/ZKqwqOnnXZadXW1d4G4hQp22203MZwI+5FHHhFByrJR1iAuj0eK7Yqzzz4bi+gkG0KN2epLoaY4FCoxYUAQF6kmVEE8JEB+48aNk+6yEU1jxSdUVPj666+Lioog6by8PEtlvcOGDbOVxZuamrwLhNHDPnhnOBAxw/e1tbVWuLsTNoTP4cOH2+zlm/5QqMSEAUFcWKkn1Mcee0xst9NOO9lKRfrJk4g5YpxC1XzxxReyfmnIlWzVW8nBu+++i8olJSXYREc9gbFvL7zwgqWyarEpPjEtO1xTU+NdwIBCTXEoVGLCgCAuUk2oyBSxS3fccYcdtQ3WSaJChbrgxRkzZohQ8/PzLcVFF11kh9ucWxRS/6yzzsLcp59+2nbskthd57V9+vSBmJ0dqZYsWSKz4twxCjXFoVCJCQOCuLBSTKhOl8TpFStBodpqeAfpOmSpnNIKN8+Ct99+21PZr/j+++895WLc3/3ud6JkrEeEevHFF3tqxgOFmuJQqMSEAUFcpJpQO0EnhKpBinnjjTf6FCJUTBx++OG6AjwnsxwLbUPfi7VU0zEmVq5c6a0UHxRqikOhEhMGBHGR5UIVQqHQlClTRI2Sqp5yyim2ykHr6urktqh3GfU+VG3T0tJSvQNyxzdRKNQUh0IlJgwI4oJCRZKqHbbzzjuLJo8//niZ+8ADD1gK1zLKmrqV+NRTT+301jUUaopDoRITBgRxQaF6+Prrr0WoEC0y1LFjx0YUKjaH3DQvL89T3mko1BSHQiUmDAjigkL1IOuZPn26TMvTLxEHKZw2bZqt6iT0mraOoFBTHAqVmDAgiAsKNQpwm9xA7YmVe6BQUxwKlZgwIIgLCjUK9fX10t4bc5yjrkOhpjgUKjFhQBAXFGoULrjgguLiYp/P553RA1CoKQ6FSkwYEMQFhRoFSU+POuoo74wegEJNcShUYsKAIC4o1CgcfPDB48ePf/31170zegAKNcWhUIkJA4K4oFBTBAo1xaFQiQkDgrigUFMECjXFoVCJCQOCuEhrobapt5DiEDZs2OCdl240NTVddNFFvGSnLBQqMWFAEBdpLdTm5uZQKBQMBr/77jvvvDTk9NNP9/v98iuBpBoUKjFhQBAXaS1UWw1UhEOYNGmSd0a60draWlhYOGTIEDuceZOUgkIlJgwI4iLdhQreeOMNudIhW+2WUQCTD2x66KGHlpWV8e5pykKhEhMGBHGR1kJtVS9Ka2pq+tGPfoQDWbx4sa1y1vSivLz8yiuvDAQCDzzwgOcASepAoRITBgRxkdZC1bS1tfXp08dKT4LBoM/n+/jjj9uZnqYwFCoxYUAQF1b6C1U81NLSgs+5c+fem2689tprtvpN0NzczLunKQuFSkwYEMRFBgjVVndP0ze9w08B7dH0PYqMh0IlJgwI4iIzhNppJK+1wyZrbGyMM0eU27fySbIBCpWYMCCIiywXqiA2lXe0acVGByptamrylpLMhUIlJgwI4oJCHTFiBE7COeecc/LJJxcWFhYXF4tZa2trpYKnGRYehU2RyI4aNaq6uto5S7JbNttmJBQqMWFAEBdZLtSJEyfKVVKnm/qiqe3oyVmlvL6+fvTo0fgUfYZCoTjbikmaQqESEwYEcZHlQsXhL126VKbhVLjzoYce0hL9r//6LySsZWVld9xxh14EHsVSl1xyCSYki0V9JLgo3Gmnnd5//31dk2QSFCoxYUAQF9kpVJ19RrxEwqyosGDBAr/fv2XLluXLl6Pa6tWrMWvo0KHHH3+8rcbdRWFVVRWmL7vssn322QcTzz//fMQVkgyAQiUmDAjiIjuFqsnPz/cW2XZdXR0yVMyqrKzE14aGBjvcFJybmwvXNipGjRolQsUsZ7Mwklc9TTIGCpWYMCCIi+wUqvQqam5uxuGHQiFdDi/W1NSgHElqQUGBrXJZVIZTka1+9913Vvh9pagzbdo0aLW+vj4QCFgKn8+Havvuu++2LZFMgUIlJgwI4iI7hQojSqtvcXHx559/rsshy9dff71v377iWjvcOIxMFLKsra3NycmRxaFeiBP2tdU5dPbsTdMB+kl0KFRiwoAgLrJTqJolS5Ygp/zkk09gRPjyrbfekosmzPr73/8+NzdXev/usMMOb7zxBiYGDhx4ww03ICt99dVXUVMemxk3btyZZ54J9ZaXl+fl5S1cuNC9EZIJUKjEhAFBXGS5UMFTTz2Fk1BQUCBtttAhJCrD6kohPo8//njdMoyS/Px8ZLGQqH4Odccdd7QURx99NJ9DzUgoVGLCgCAuKFSI0znmkYzbYIfvszY0NDhvskaBz6FmNhQqMWFAEBcUKiHxQKESEwYEcUGhEhIPFCoxYUAQFxRqTKQF+IYbbmhubub90ayFQiUmDAjigkKNSVtbGzyan58vIzyQ7IRCJSYMCOKCQo2JZKVFRUV8+2k2Q6ESEwYEcUGhxkSE6vP5bHblzWIoVGLCgCAuKNSYUKjEplBJJBgQxAWFGhMKldgUKokEA4K4oFBjQqESm0IlkWBAEBcUakwoVGJTqCQSDAjigkKNCYVKbAqVRIIBQVxQqDGhUIlNoZJIMCCICwq1I/SgSBQqsSlUEgkGBHFBoZqIQTsSKp2anVCoxIQBQVxQqB3R0tIiEx6h4iudmoVQqMSEAUFcUKgmrQqIs7i4eOjQoUuWLIFccaKampr+8Ic/YGLw4MHeZUimQ6ESEwYEcUGhmsirxYGlyMvLw2dZWVl+fj4mgsHg8uXLvcuQTIdCJSYMCOKCQo3CrFmz/H6/aFUTCAQaGxu9VUmmQ6ESEwYEcUGhRqGurs5jU7B161bdX4lkDxQqMWFAEBcWhdoxTU1N06dPDwaDPp8PnyJUO/zKcZJVUKjEhAFBXFCoUWhubsZnaWlpbm5uIBDAuYJZGxsbKdQshEIlJgwI4oJCjclBBx0kuSlsumDBAu9skh1QqMSEAUFcUKjxIP17CwsLvTNI1kChEhMGBHFBocaktbW1rKwM6enzzz/P7khZC4VKTBgQxEUvCjW95IQT1azwzkhJZCwn3uvtRihUYsKAIC56Uahy0W9PeWRv58+f36Lwzk49ZIf1BOkWKFRiwoAgLnpFqLNnz5ZOs/KZ+pSWlhYovDNSEp/Ph8+BAwdu2rTJe+pJZ6FQiQkDgriwkitUZHhlZWXYqN/vP/DAA39FeoCrr7569913z8nJwUnecccdm5qaKisrvX8JkiAUKjFhQBAXyRTqqlWrZCQ/+cp3tvQczc3NDQ0Nr7zyiuSs+s05pNNQqMSEAUFcJEeouL6vXLkS20LylC79ejKGnXfe2VKvyuFd1a5AoRITBgRxkRyh2mpD/fv3tx3vGSVJw+/32+ym1DUoVGLCgCAukinUVatW8UGO5INfMKNGjTrggAPYNtAVKFRiwoAgLpIjVORGkiQlmp7qpKqmpua77747++yzLdWhKS8vLycnx+fzBQKBU045Zd26dXZ46N0UQd5J3l0dg6Xj7hNPPFFXV9eJe884dbm5ud5SkggUKjFhQBAXVlKEaqsNyUSiTgVbtmwRr+hXvkCo8sgNSoqLiy1lWdQMhULehXsD/A6Q15Lrr10EK5kwYYIcY6LghK9duzY/P78TJiYaCpWYMCCIi6QJFQmlTIgeYlJbW2urN5KOGzdOJCpZmjgV0+arv5GEDRs2DEvV19f3btsyjhF7OGXKFJn2zu4UjY2NOEY5LYny9ddf6/NPOgeFSkwYEMSFlapCRTr1ww8/DBgwQAamF2QauenIkSNHjBghhSUlJTIhOev+++8v4xl515hEsHXsydSpU70zOgvOBn4iWBRq70GhEhMGBHFhpZ5QUUH8gUW0JpF93nbbbd6qioaGhvvvv18qo1phYaG+8MXcVg8hQr3wwgu9M7oGhdqLUKjEhAFBXKSaUHVTrTTw6qZdu+Obr7AvnArTiErx6Rw+oleIIlTMwt56S+ODQu1FKFRiwoAgLlJNqDL35z//uaV6HkGN0j01SiuuU7TFxcX63urkyZMdtZJKR0I977zzcDiNjY1NTU2eWfFAofYiFCoxYUAQF6kmVLB161YxohXuuxuT8vLy+vp6aSgOBoNYShLcmNvqIUyhYt/w+2D06NH6olxXV3f55Zc77xCb6MUFi0LtPShUYsKAIC6s1BOqvnUKA0lJzC67SPiam5sl7XvppZf8Ye68805v1aRgClX2beHChTguKcFBnXPOOS5/OpA7x3pxwaJQew8KlZgwIIgLK/WEiqQNKs3NzcWEd56bmpoauR/5k5/8pKysTK8ZNoJN8dnF0QycD26K1ON8lNMUqvDGG284L8oXXHCBU6JOJMN2LPovLAq196BQiQkDgriwUkyoLS0tokPs2CmnnOKd7aZOccstt0CcsggUGwqFbrvtNtESNorUEC6MU4QeFixY8H//939vKT766KP4R2LqSKiLFy+W8yB6fvbZZy+77LIrIvGLX/zikksu8SxOofYiFCoxYUAQF6km1E8++URcGM/FC/aVV6lYapC/PffcE+KEcrAJKFZaTZcvX965HkC2OjkaCDv+3rkdCVUTsxE7IhaF2ntQqMSEAUFcWCkjVCl/5pln5B5qxItXq8JWlevr6w899FDdqWfMmDG2Uqwko1IIfv7zn3cuPbXVS1qk6dVSbbB2l5t8u4hFofYeFCoxYUAQF1bKCFW44447JLOEzJxp3Ny5c3/729/KdLviyy+/1E/IOK90cF5zczMyVCnvysMzFCrRUKjEhAFBXFgpJtSnnnpK7qGKUKW19rnnnhOrFRcXQ2mhUOjGG2+0VFfYiJ13bOVCWeT888/3zusYz9gRsgYhGAx6Rt6PIlePUOWXQUFBAfYWKfU999zTpnAtEwcWhdp7UKjEhAFBXFgpJtT3339fJ4W6UI/Wa6mRe2fNmlVYWAgzSS7rWaGnyXfRokXx30MVZUoG3K5uxOr321hqf+JclUeo+Prxxx9DqE888cTLL78sqwKvv/76H//4x1kd8OCDD25bo8KiUHsPCpWYMCCICyvFhGqrXRKnbtiwoa6uDuldc3OzKE30BjNhbZKDQoE6kdWsWbNGi9BZHhNLNTXLglb4WVj9tayszOnXr776yrt8GI9QkfhWV1fb6jU4RxxxRGlpqXQYRvas1+YhYuZtUai9B4VKTBgQxIWVYkJFfqmlImMgiFDt8Oi+lnIeppGkehdWYA2jRo2SmnpoiDiRlesdiAJ2YNWqVd7lw5hClU/ss5wH/FbAQV188cVyLCYc2CHVoFCJCQOCuLBSTKiwjtNbutBW7bEjRoyQll5kirZ6RajZBrtx40ZZFq4SpcV/t1KWcu5AR/gSESr2EzsvC/ZV2OolOT/96U+9Ig0jlV0rpVB7FQqVmDAgiAsrxYQKXnvtNSs89t5+++0Hm27dulXP7dOnD8pXrFjhWOLfbN68ubq6Wh6kyVF4a8RCtuu0mm7j9auhl5yzvvnmG5jSuwqFR6hgzpw5sh5LybijN+eYyC8GpOkQMHagqqrKM75EzPNpU6jdAYVKTBgQxIWVekKFpQIKS+ntkUce8QyD8Mknnzi/Onnvvfe080DMbXmA57B16YILpOuTFqGt0kpnB934hYpF/tXNSRHlzTkmqCwGdebZ8S8uUKhdh0IlJgwI4iIFhSpojQFYzfnICgQTMcMbNGiQJJTSbAsZe8Y2inPTmu56DrVJIdPi4PLycl05IiJgW6XdckT6FwY+Fy9erK1sqZ5Z3uXdUKhdh0IlJgwI4sJKVaFWVlaKPAQsLg2/WFys5nQbjKLNp+vj89xzz0V98U2zQi8SD90lVMlKMXH66adfcMEFrqodg0X23ntvbLe0tBSHs+OOOw4ZMsRSPy/w+f7770PScqRnn322d2E3FGrXoVCJCQOCuLBSVahQV0VFhVNpwh/+8IctW7aIn+CJ++67TxyjOxOhvtg0Nze3sLAQNvrtb387ZsyYpUuXercRi+4Sqq0emEHJPvvsM3DgQOxSxAzbw7PPPivdr+BOO/yMLH4T4Ki/+uorTAwYMKCgoEB+dnTU+CxQqF2HQiUmDAjiwkpVocp909tvvx1SFKU58YUfLJFpsalu6cW2PBoWpk2bltCo9LKUXwE9x5/gmkK1w429SDR32203Kbn44otl7AgnWPDdd9+V7NPvfr96S3ikYju8b0VFRXDqe++956xmQqF2HQqVmDAgiAsrVYUqVFVV4fPxxx/XY/MKTl9q4951111iMmxL987V6NuQ3m10zIIFC5aESSjBNYUKkdfW1n700Uenn346ZiFhRclFF13kHDhCQEldXZ1l2FSftyOPPFJq4hiHDx8ePTcVKNSuQ6ESEwYEcWGltlCd/OpXv+rXr5+45F9deMNOhWunT5+uV6uHVeoIaAz5X8yOPF3BFOpnn3127LHHbtmypbq6GiKURHnq1KlW+Fg0cpNVdtVWLb0777zzUUcdhUWw2htuuEEfyNVXX63XHx0KtetQqMSEAUFcWOkjVFhQN7piWj9PYqs7lHoaiaAeTN9E2m8hLYgKS8ki3Y5HqKLP/Pz84uJilE+cONFWh7By5cp3DGyVGaMask87bFZLdeUdPXq0vlV84IEHYi7qTJkyRW+3IyjUrkOhEhMGBHFhpY9Qbfd7udvDXWdlhVqobW1tK1as0B7yEAgEpIn42muvjbOHUScwM1Rb7RgUjn2uqKiQr7qyE1vl4rAvklF8fe+99yzVDuw8ipdeegmz3n77bUwPHjzYuZWIUKhdh0IlJgwI4sJKK6HGyeeff+7UT0fMnz/fu2Q30R5JqHGCXwaffvqpT/VV/tcQEm1tJ5xwghV+AlVGJ25sbMQmzjjjDJTceuut3lUYUKhdh0IlJgwI4sLKOKEii21zjLAfEbn/Km2qPUFXhCp5ajAYRJIqwzvIXeFchfPslZaWBtT7A2JCoXYdCpWYMCCICyvjhKoRdzpHhzDxLtN9wNkQavxP2niQ3auoqJBW7oEDB5aVlbWrVm496JKlbgnH03BNoXYdCpWYMCCICytzhRoKhfTDNpKSauQrUkDvMt0H1n/44YdjH+BUablNCN1X+fPPP8dK2pQ15dRBqJs3b8b5xNHVKbzbNqBQuw6FSkwYEMSFlblCtVXv36KioohJKmz01FNPeRfoJhobG88444xgMHjiiSeeffbZP0kcSUNlV/fZZx+9ZiSsV111lZSvWrXKfHtdRCjUrkOhEhMGBHFhJUuofr9fVBrPqHvdSE1NjejHk6SCnt6T22+/3Yr7Basm2POXX365pKREvjrfewNuuukmW/k1+g8UOUbIgELtIhQqMWFAEBdWEoXqLUoK0BI+y8rKnGIbOHCgcxi/nkByx+i2i4IsXl1djc9f//rXstsi1zPPPFPvecz1SxentWvXUqhdhEIlJgwI4iI5Qm1T3W7tjl8gmjREMN7SzAVixsl//PHHCwsLvfNIIlCoxIQBQVwkR6jt6jGSI4880g6/NaVXaFF4SzMa+fUQCARkDCbSaShUYsKAIC6SI1RwwgknBINBb2ly6dE23pRl8eLF+Ct3+gEeIlCoxIQBQVwkR6iSJ8ktwIULF0qhPB8ibbCke9H6nDJlynbbbXfrrbe2KvRfhCQKhUpMGBDERXKEKkCfAwYMyMnJOe200zZv3tyeTfcykwzcKa80B9dcc438cPFWIolAoRITBgRxkUyhCu+8847zCRZ5/QvpRuSsyundtGmT9w9AOgWFSkwYEMRFMoWqkyR5HemCBQteffXVl0kPsHjxYmcDb3bePO5eKFRiwoAgLnpOqHIzz86Iq3ly2ksz4ERlMBQqMWFAEBc9J1R55DQ5KupRkvakTU+PNUG6AoVKTBgQxEXPCRVuaG1tjXOw2VQmOb8JcK6c70snqQaFSkwYEMRF9wpVhpb9+9//npOTc/jhh48bN65Pnz62++6pTEAe2DTKp0+fjomhQ4dKOUomT55cUlLiU2A9ZWVlzrzNHGtJ5i5cuHC//faTEnklqqtSp6iqqsK+jRw5EruEiT/84Q/eGm7EiNj6jBkznn32WRzLHnvsgZJ33303ZpobCAQOPvjgY489FkctwyXOnTu3trbWdg+FoQ/NXCFmYSedBy4CeOONN8aMGaP3TWZh3/7nf/5H1yQxoVCJCQOCuOheoQo77LCDdC6FD84444zzzjvPVtprbm7WT0Pi+i4vxy4sLPzmm2+ci59yyinffvut/gqnrl+/XqYl69WzTLrFoxp9cmSjUa6noittvmuuuQZClaWwSwcccECU8aEwa+LEiTJsL6aXL18uZwZCbWho8NZ2o583lXMLGTvn6h02f4XU1dVFORxiQqESEwYEcdG9QoVXcFkvKCiwVTKKr99///3jjz9eXl6Okr322gube+KJJ+xwOnX77bdDHqeddhqSWr0SfP3qq6+kTxOu+xMmTLjzzjtl1vDhw3Nzc5E4wlLwtJbrxRdfjEWuu+462QHkhVDLK6+8glkXXXSRrTZ3+eWXY22o8PDDD2tRiZCwNiTKtpH25eXlaRVh1pVXXolsFdMXXHCBFF566aUyIXk2ePHFF20l1Hnz5mH/sUtff/113759p0yZMnXqVExL/Z///OcyIXiu1AceeCA+H330UWx9wIAB/fv31z8ULrzwQvzC+O///m997Pvvvz8W/+GHH2zHes4555zKykr5it8rV199Nf4cV111Fc7eoYceisI5c+Zg7k9/+lOpT2JCoRITBgRx0b1CFa644gpLvRlbWixtlSGhRPSTn58PjUFpRUVFv/3tb1GOBM450uzpp5/+3Xff6a+w2ubNm221q9dee62kVljDXXfdJVKpr6+HPt94441x48ZBPMFg8JZbbrFV7otP2AhGEX8//fTTsh7xkzjbVkKFaWRzWl2YkF8Gms8++ww7DzNhz22l2CFDhmACx1JcXIzkEgrHyjGhhYpd+uSTT7AncCR+NMDHslG9OVtJ3XOlxhHhE3uL8q1bt5511lny6tZf/vKX8Cu2u9NOO7377ru2Oha4HPX96mU+8koZHPJ9990nc/H59ttv77333uvWrZMDHzFixKmnnopThK8i15h5MLEpVBIJBgRx0RNCbVX3+XbZZRcZwEEKJ0+eLOkgfHD99ddDKjAlvqLO8uXLnYuffPLJ8I2MUQAVyVLvv/8+MjyIGStH0okEC4Vjx46FvSAb6AFChTZsd/IHwyFRO/7447Hg4YcfLjsjn1qlVhjsiYw2LLMgTslHNRUVFbIsaop3Bw0a1K7G+cNBYU+wCIRnOzJUeTc4tIrpFnXb2FaXZiSszjV7rtSojPXff//9W7ZswfFizf369ZNdbVMt57Z6Hd769et33nln2RP5bYH9v+GGG1566SXsCaphP7FR+akBneOsSsuzbsGGSlFNjpdEh0IlJgwI4sLqVqF6biVCY7CjXIagT62uI444AnUwIYnjt99+u2LFChncB+kUMtQNGzbIGvQl7KabbrKU80TSF198scyFOSz1Lu7Fixfvv//+Uig18fnrX/9aNgHrLFu2TNaGXZJ1CosWLXrttdeQdL7wwgt6nGEBCZ/I0lbqRc4txsVnmxrMD/oUOeGIggrZhBbqj370I1u1ytpKk7vttttHH32E1UoLrSAZqs6MbXUaq6qqIFR8YqnW8M1RVJNNWGosJOz2scceq5eSCsihdUO07Mybb74pPzUGDhxoqf5fyPKxOUlqSZxQqMSEAUFcWN0qVFz9YUrpU4NpaUvEVygB+aWuJjcmLSVUzIWopFykcvTRR69Zs+ZfDaPt7X369IEMYM2ZM2fefPPNUqi7CotmRAwwMbwFFd1zzz12+L3ittoNSGjp0qXYVnFxMXK+jRs3yiwN6kj7sNNqAPVtx43V888/f8SIEU4V7bjjjrZqMh0/frwkjpAWKkQUKvjb3/6GrBf7ozsTCc4rNU4OjgvZ8COPPKKFii3iU3ZSUmFk3kuWLDnooINE7dICLDum1+YRKg6ktrb2uOOOk6bsXn/5T3pBoRITBgRx0e1CBUOGDDn11FOl5LHHHpP7hfpiBNlIFyRLPTaDi/uXX34peZ6tWiMnTZq0atUq+Worq3322Wcy1DvUJRknBAmvrFy5cuedd/7Zz35mq4dDfvzjH0u2BydhLiS3fv16ZGNTpkw55phjoBPU33777fW2NHLPUj6djBs3rl+/fna4ZbikpMRWeyi3KiEnOahHH33UmVJjH66++mo5qyLUQw45RFYi+fSECRP+vYEwyIwnT55sq863e+21F3YSeztnzhwtVOT30mIsbd34eWGFs3McbHV1teyJ7BiSdd2cjo2+9dZbY8aMmTFjhqSz+KmBc65/Q9jGzwgSEQqVmDAgiIvuFarGciDX69/97neWaqiELaQEl3tc1pGhQqjtjtt4UMvq1av1V+gKl37YDjkuhIH6u+66q0hR+jpJtVdeeWWfffbBmn/605/KdrEtOA91oCJIvVlhKYvrlUcHGx02bBjWAwMhn8NKRO2jR4+WTYwaNUpqYpaUwNz4+pvf/Obxxx/HhNxDvfzyy0XGYN999/332h1gl/C7IUdRVlYmhfgtIs/SyG7jkEXhlmrXlXLprAumTZtmqwxV2qhLS0s/+ugjyeA/+OAD7LB05rLUafnkk0+wNuwSTiZtGicUKjFhQBAXVg8IVRsLV3boB5/tqpdNRUWFvr2q67TGGoRBpAIqKytl8ZbwEH2yZtvIsaQQldtVVyA4VTexmulpdOThH73C3Xff3VailSOSOs7229ZIAx5BZnp6hx120NMemhTt4aZyD+ZZkhKzXFrU21RTsO5zpBuubfe+kTihUIkJA4K46AmhZipd9BBci1y8T58+4njvbJLaUKjEhAFBXFCo8eNM8joBksU1a9boHlUkvaBQiQkDgrigUGOCzDJiGyzJKihUYsKAIC4o1HiQHrbOe7Ek26BQiQkDgrigUGMit06lx6zZA4hkCRQqMWFAEBcUakwoVGJTqCQSDAjigkKNCYVKbAqVRIIBQVxQqDGhUIlNoZJIMCCICwo1JhQqsSlUEgkGBHFBocaEQiU2hUoiwYAgLijUmFCoxKZQSSQYEMQFhRoTCpXYFCqJBAOCuKBQY0KhEptCJZFgQBAXFGpMKFRiU6gkEgwI4oJCjQmFSmwKlUSCAUFcUKgxoVCJTaGSSDAgiAsKNSYUKrEpVBIJBgRxQaHGhEIlNoVKIsGAIC4o1JhQqMSmUEkkGBDEBYUaEwqV2BQqiQQDgrigUGNCoRKbQiWRYEAQFxRqTChUYlOoJBIMCOKCQo2OGPQf//hHbm4uJlpaWrw1SHZAoRITBgRxQaFGAfpEenrjjTfm5ORYiqqqKm8lkh1QqMSEAUFcUKgdIcno9ttvj1N0xhlnNDc39+nTB2bduHGjrhMKhbYtQDIaCpWYMCCICwrVpKKiAvr8+uuv8/PzIdQqRX19vczCGSsuLkbmKiUkS6BQiQkDgrigUJ20KmDKmTNn+nw+JKbeGrYN0Urz76pVq2x2U3JTV1eHz9WrVx999NHjxo3bp4cZM2YMPl966SW9A/gltG1vuhUKlZgwIIgLCtVkxIgROC2HHnooEtOOLtDi1G+++QYV6FRNKBTq27cvzkxRUVEwGJSz1HPgR4/f78fELrvs4t2V7oZCJSYMCOLColDdIOnBOXn11Vfb29ulsddbI3x79cILL0TNa665pqmpyVsjW1m7dm1xcfHf/va3xsZGWz1x1KO0trbKdgsKCi655BL8IdrVM049AYVKTBgQxAWFKkAAt956q/TmtcPPnkahtrYWn+Xl5UiSsMj69etxcc9ys+Kk4VR88MEH3hk9DM78yy+/jE1joudaCyhUYsKAIC4oVGHQoEGBQODkk0/GNLzYUUuviVgEbN682Tsv+8B56DmlRQEqxS+bzz//3Duj+6BQiQkDgrjITqHqBFTaDEeNGoXL8TvvvOOqFB/ij6KiorKysuuvv95Tnj3IKUU4xUzuux296QULFvTcaadQiQkDgrjITqEKDQ0Nd999t9/v32677bzzEkEu6LW1tTiZOTk59fX1uKy3tLT03MU9BaFQSRbCgCAuslmoOHAc/pFHHtnF8Rl01xhIFHkq1rlp0yZdmCVQqCQLYUAQF1kr1OHDhwcCgUWLFnV7TyLp2fSb3/zGVkmwd3b30e7GVmrvOaNEh0IlWQgDgrjINqHi4gvJ5eXl5efnP/roo7j+djE99YC11dXVnXDCCVZPPhwpj3j63CA/lodVegUKlWQhDAjiInuEiuwNtoNECwsLx48fX1FREc/YgStWrPj000/112+++eb999+X8YBiYinWrl3rndFlRo8evd9+++200044FiTEP1LILE9Tc21trc6Se/RVOUkTqtmWDok2NTVh03/5y1/i756dKBQqMWFAEBfZI1RcdgcPHozjXbx4cZyXXVymhw4dqi+jo0aNEke+/vrr7opeJE9qDz9Rc/3113dvHixDJL799tt+v3/33XdvU6C8uroaE9DtHXfcITXLy8v1UpWVlXo3DjnkkAkTJuCXgdhI1+k0yRHqhx9+iN8QP/zwg228mQCb/vLLL5mhkmTCgCAuskeo4rZ58+bJHcdmhbeSG1QbPny4z+eTYRwKFDU1Nd56kZBECknhcccdh+3OmjXLW6PLPP3009gfCFWOCJrBho4++mh8/sd//AcqQLcPPvggZmE3ggoU/v73v8/Pz/ep8SjAli1bvOvtFMkRKmI1NzcXW3nyySed5fKnjLPloHNQqMSEAUFcZLBQRSTIY+bOnYvDnDhxohR660VFMlR5JEbIycnxVooKdgAOlrue69atk2wy0d2IyMsvvwwvjhgxQr5u2rQpEAgggZOmbGwFQp09e7ZsSwza0NCAwv79+8tTPXJEznV2muQI9c9//vOuu+767bfflpaW4pR2b94fHQqVmDAgiAsrc4UqDBkyBDnNmDFjdIl5Ey4KItTq6uqtW7diAjaCrhLq+6ObfyEAWG369OneGp3FI9QNGzZg98aPHy9fIwoVxy4SlcHrIWBMx8zU4yE5QkVSPnz4cFul/nIgf//73xP6g3YaCpWYMCCIi8wTqtwRlNzFUu8uRVrjrRQ3IlQxqFzB7cTTXM0JJ5yADPLuu+/WqVWnV2UbQl2/fj1277jjjpOv0CS+/vGPf5S+SJjGDwv8MoBHjz/+eF2nuwaUT45Qn3/+eWSo+ut2222HLZ5++um6pOc6XlGoxIQBQVxknlAlI9SpWBev790rVFt1G4YFdafcrhBdqAAJ6I9//GPsPLJq2BQqlbZrLCUV5JHZiG/USZReESrALwYk4qNHj5av3ZJtR4RCJSYMCOIik4QKc4hNR44caakXmnb98jp8+HBLNYoC+Akqald46yUIVpWXl6ffcda5/XzxxRexb6NGjZKvmzZtglqQBMtXnIrS0lL5EYBtSesuyisqKjARUCB912szSegw4xQq9mrr1q1I0CsrK+sT53//93932mknzzpx9vDLAL8YZsyYISXd0m/ZA4VKTBgQxEUmCVW3bcIrL7zwgt0dF9YhQ4ZghbIekZOdoGlMZPFJkyZBeI8++qh3dpdx7p78wtDnIaERhqVLl7e0A+IUqvx1fOEXg3eCE0880bNO/ETAfk6dOtVS94Zt44maboFCJSYMCOLCyiChIlORzrTwR11dXUJvYesIZKi49EujaEFBgVyv43dSRCCq1tbW2traQw45JD8/f8899+yc+OUHhL5r2NDQgOPVfaDscPunc2/FNMgOVV/jf3U2RklH9x2RQG/YsGHp0qV2HIccv1Crq6tttW8q1U8M7+rCYPdqampWrlyJ9RcWFnb9725CoRITBgRxke5CbVfPxmBi7NixVvj5yyhX3pSivr6+PTz4AyRnJ9gDOQlA0nvssYelmoi///57ET/sZRpLznl0oWJB/VBvlGqdRqyPSOin8M7uGhQqMWFAEBfpLlThoIMOwoG8+OKLEECLGtK2J67X3UubGqJIbqOecMIJMNbcuXNTSqiyM8j1cW5LSkpkaIjly5djz2WsIie9LlSsUISK9X/++efYE2T/dvf1+6VQiQkDgrhId6GGQiHJ8BJ6NtR2N4q2qpe0AEx0rvU1Igldyg8++GDIBtkV9gELSgtnKoB9GzBggOeW52233Sa7jdMlGpOaVu8J1YM8qIrNffLJJ7baXBfZsmULTkJCf1OS8VCoxIWVzkJds2YNshBLjWRkNkJGRyRaXV2tJZGbm9ve2Q63TmRtdoJCBfPnz8eCZWVlsFRtylBVVfX+++/LzWlLdSmyVLdhuOr3v/99e9iLMmGljFDlh5E8qIofK96jSpxly5bhJFRUVHi3RLIYCpW4sNJZqDvvvDP2f6+99rITvPsold98802RBEw2e/ZsmZ46daq3doLIeuw4OvI4kXFo5fdBqgGRyAi6Apyak5MjZn3ttdfkZKaaUG31qoC//OUvere7Tp8+fbzbINkNhUpcWOks1IaGhoceeqikpCT685QdYSlVyLQkpnLdhNuQXKJk8eLFv/rVr1555RVt6xbF7bfffuWVV0qyAknI+9Fw7b7hhhtqampkJfELQ3Kpf/7zn6IoKZQNpQLYGfxksVTzqc5TCwsLFyxY4DyKlBKqbGLPPffEfo4aNQp/Su9RJY6d4C8kkg1QqMSFlc5Cra+vbwu/C1OrKE7EfE8//bStLpTO67s8fzJ69OgchV65XE/lq6UE89xzz8G1WBa5Mq7dljK0DKeQkDC+//57LCgdU+XanTqEQiGfGgdYbLrddtt5ayhSSqigrKwM28KPIe+MziJjNPb0bpP0IrGLDsl4rHQWqtCiHutEOpKXlyfpCGQZ801ezzzzjLw3BpdIrWQBa/vZz34WCARkrq3egzZgwABbna4ddtjBVht9++23ZXRcGeZw5syZTuPGvPLqrNdSrlq7dq08mumu1ctgJw855BCcivz8/OijJcQv1I0bN9oJNtHHD/4uP/rRj7C3CIau3w4nJDoUKnFhpb9QmxWNjY0PPvggDufYY4+Nck0XcNl95513LNU3WHJcyS9BQUFBm/FeM1yd5Ss+V6xYIWuAs3Hh/t3vfgc3wM368i2D/MXcB/hpw4YNssVvvvnGOzsFkNePFxUVYfda1MNI3hoO4heqtJB3O2LofffdF/tw9913S1R4KxHSrVCoxIWV/kIVcJmGoqTXbsxXlspFH3khshmdKqFQMhtMb7/99tI4iUJUQCGSURgFK3/jjTfkSo3NwYX33XeflMujmfLUZnSvCGvWrEE1bEi+xqyffOC/evVqVTu8e1FuIsYvVBha/kZyohICP1Yee+wx73oVCAB5UlYa8NtVh+0oO0NI16FQiQsrU4QqINfUT6auW7dOjz7vrafG1ZOeq+Xl5dKYqR+hQf3rr7/e0+Q7bdo0adq1wpnrlClTZCRClJeWliIzxnpwWdcr2baxMKgpirrjjjtQZ9KkSXYHu5d2xCNUcPTRR/u7ANY/ePBg5wpxzrHF+++/31KS7qH0l5CIUKjEhZVZQpV0s6Wl5YEHHsChHX744XZ42FhntXY1qg6qIWGSPkT6sZBrrrlGLsq333573759pdBSEpWVFyhQgrmbN29uVq8UvfDCCy3VTUnXN73ivGmKzW3atMmOmvOlF/EItev3TefPnz9o0CD9Vf6y8vTU999/b4cfL46yD4R0IxQqcWFlllCdfPfdd5Z6/YjuTWOOgoQr8tq1ay+44IKf/exnX3zxhWeu2E46PXlmeXDerhNT2u7NtSukmRc+1uUZQzxC7TryPlR9Nxd+1a+lIyT5MPKIiwwWapt6A4mlWgJhTTvSEylahBGV2a5uoNrGgvJgoqfXa6saMlCmI3aIvffee+XGoXdGRpBMocoPneeeey4YDO64447sfER6i8z8ZyadJoOFKlbD9b1Pnz44zC+//DLildfZ6BpRBmarbIsaa9d21Nc+lgnPIkhV5TVwp5xyisyKuCdpTTKFaoffIT9v3jwp79GNEtIRFCpxkcFCFWC4xsZGaWsNBALJH4u1vLy8tLS0f//+mK6qqtL9ZjOM5Aj1ySeftBRDhw5tVUNqeCqwUxJJJhQqcZHxQhVw5d26datci73zepI777wTialzDFiz2TkzSI5QX3vtNZ/P95vf/MZ5f1puqb7xxhvb6hGSFJJ6NSGpT5YIVTNw4EBLjdbrndF9iFHa2truvffe3Nzcww47rEcdkyIkR6hg8+bNnhJpRYdoFy5cGPFeOCE9BIVKXGSPUOXNnQ0NDbfccguOWtpgux2dgMp7Y9wzM5nkCLU10gtrRajY9IIFCzK1AYCkJln0H07iIXuE6qS8vBzCKy0tbXeMpxOxa2786McfRdhImKKP1ZdhJEeoEdGbhlDNHmSE9BwUKnGRnUJFntqmBuwNBoPV1dVS2PXWwtra2tmzZwcCgf333x+rzbyuvFGgUEkWQqESF9kpVKGurq6srAxnYNasWa0Kb40EGTdunN/v/+tf/ypfu77CNIJCJVkIhUpcZLNQbXXLc9WqVTgJ/fr1k+ty59ppZaTDjBwCKX5wAq3euG0sQ2pg06+//npWtQqQXqcXwp2kMlkuVEkixQSWemNMJ+6kvvDCC1h2zJgxnVg2Y5DeQL0iVPklFAgE3nnnHe88QnqSXgh3kspkuVCFNvVKVHHqbbfd5p3dATKGwP/7f/+vsLDwlVdeYWMjskOcwPr6epwK50CMSWD16tVFRUWNjY3MUEkyoVCJCwrVdvTvXblyJU5IcXExZBl9SCMIuKKiIi8vLz8/v6qqyjs7+5DfE3PmzNFJanLy9Rb15nN5WZB3HiE9DGOOuKBQbUfvobq6Olygg8FgzKvzwoUL4d29995bvkIeWdUFqSNwEsRtV1xxxfPPP/9iDzNv3ryHHnoIm/P7/bbjySVCkkOMywTJNijUiECWyD5lGqmqDBurG3Xh0UAgcMABB2xbgITBb4uSkhJpP08C8tZxc7QHQpIAhUpcWBSqG53iHH300Tg58+fPl6/IXKURWF7BNnfu3IqKimTeJkw7kjNOvfwJmJiSXoFCJS4o1Chs2bJF0qDy8vLGxsY5c+b4fL6DDjrIW48QkpVQqMQFhRqdUCgEieIsjR07Fp+77757cvraEEJSHwqVuKBQo1BfX19dXd3S0jJp0iScqGeeecZbgxCSxVCoxAWFGpN2hdUbg+qlKfJWH1tFV2FhYa5iwoQJ3npu6urq5s6d6y2NxVVXXeUtIiRZUKjEBYUaEz0GEIUaJ00KSHTRokVSIq8iGDJkiLuii1133fXOO+/0lkblb3/7m+6MTUjyoVCJi7QWquSOGrtnepbKmn0+nx0evoDEZObMmWVlZbaj/62MRfXDDz+46tl2TU2NTAwaNOjuu++2VU1bLXjZZZetWLFCBj/y3LrGV2S0S5cuLS4ulsrOuYQkBwqVuEhToUJsVVVVPjfydL8JrrZfffUVjrSystI7Lw4o1E6Av8WUKVP0VzmH/fr1y8/Pl2xVz8L0woULd999d3kl+5YtW2bNmiVvAdpnn30sNUgynFpSUnLxxRfLIo899piswQrDEQdJr0ChEhdpKlQ7nPHccccdzgy1WSFJT7saigF5DKb/8Y9/wIhVCinRSOrT0tIiK5H0CCvR7qRQOwH+NIsXL/YUnnfeefCirXQrZ9VWNV988UV83W677SRDlfELpaUdJ1x+J22//fZaqE8++aQI9cMPP5QJQnoFBh9xke5C9dx1gwghyMMOO0wSl8mTJ9vqjWwrV64UoWL68ssvDwQCuEyPGzcOlcvLy+sUBx10EMr33XdfWUSvk0JNFMlBoT1P+Zlnnglr2oZQX375ZY9QBw0aJD90Wltb5S7pwIEDL7vsMllEZ6gUKuldGHzERboL9ZZbbnEW4vo7ZMgQyG/ixInHHntsTk7OiBEjbEeGunr16n79+sGdRx11lEhXxuCV6dNOOw2f4k4NhZooOGPDhg2TnyZO8vPzpR3YI9QXXnjBI1QsbofbGAoKCiBX/NWmTZsmizz88MMUKkkFGHzERboL1YmtMtQWBfLO+fPno7CoqAjlf//733ERr6ysRNqUm5sbDAYXL15cXV0tq3rwwQdRoteM6/4HH3ygv1KonQAnqqSkRPcRw8TYsWOhxvr6evnDvfrqq7W1tfiKM79gwQLU6du378yZM/GjZ9asWaiwceNGFGLWgAEDMHHiiSduv/320hfJCv/o+fjjj7E4B4AkvQWFSlxYaS7U+++/31P+61//2mlZj1BtR08WgCwWvrz00kudhbhYQ7G8h9ppcMYgyzVr1uBkDho0aI899pCzil8wKEeFm266CSXyXpqDDz74tddeQ+Hll18OOy5ZsuSxxx6DeqUCJtatWyerRYm8COjtt9+21O8nSBcTpaWljo0TkjwoVOLCSluhyqCAzveBowQZKq7CuMIia0FWhKOT/GbVqlXS5CuvzwT33nvvrrvuaqlxeu+66y55+sIO907S67Qp1C6AU4dfPJdccsnKlSu98zpmzpw5hYWFnr8CISkIhUpcZJJQBahR0heY0lJvC0dW9NVXX4lQf/KTn1jqvinE+eyzz1rhN39h4tRTT8VFfPz48Tk5Oc6Xm1KoXSTRN8VSqCRdoFCJiwwTKoT3zjvvWKqBcZdddsF1WR660ELF9DHHHBMIBCyFLIW8dunSpdICaYVHRNKPNlKoXQQnMCGnUqgkXaBQiYv0FaodVW+Sd0p3Fd1pRS7rYkrn9botPPZsRChUQkhEKFTiIh2FKlaD52BKM/UxSzy5ZsT3r6GOLCgmdkKhEkIiQqESF+ko1CRDoRJCIkKhEhcUakwoVEJIRChU4oJCjQmFSgiJCIVKXPj9/ieffLKVdIycKAqVEOKBQiUu4Al5yIR0hDxL46NQCSFuKFTi4tFHH/3P//zPC0hUpk6d+sQTTzQ0NPDhSEKIhkIlhBBCugEKlRBCCOkGKFRCCCGkG/j/G5DhLAMq4EUAAAAASUVORK5CYII=>

[image2]: <data:image/png;base64,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6i9/+Yt5z2GHHWY6oNNOO828bt68uTtp2WS7ge/tt99uytSxuZ2bnmUanTbfLUNyqdUA567LUmi9xR3g7F6HQuXaA6fxl19+eTheoleputPbcYUGuLhp+bUa4Epti1pnSQa4XHv0tectWxuNhrGGhquvvjrjvRqXbXkPPvhg1mUlKe3lIT7UnAdsJ1AMdQ5z5841v9uO5q233jLzKWeImzFjhjm85XZw0aFXr15mI71o0SL37RnTlaJWA5zO4Wosrbe4A5zkqo933323XtvQkCvA6RYkl1xySTg/e68u+9qdj+geXu74OIaGaJpaDXCl0jpLMsDlqjcd7uzZs6c72jjppJPq1b07vP322+7bwve56urqzPjohTRJy/Y54AdqzgOFbhSsWbNm5Z2+ZcuWOe9zlDS3c2tocOUrK0StBjidNK2Qoyt+bbAvltZbmgEuG02bLcBp0D8qt912mxnuvPPOjGmyTS9J7IErZA+Tll+LAc4+nmrChAluUYP0vnIEOI3//ve/74423DaVbchm5syZOcs0XhfwpCXX50Dlo+Y8kK8jyCZXSHHPJSr2fkZx0efIdlm9BoWMb3/72+5bQvbcklIfl5Vr3VQ7e6jSrmMNelRPIWHD0nvTDHDZPpumve6668Lf7bD77rtn/I12nhdffHF4qCpaZssLCXCa79KlS93RjaLl12KAk2gd6H58hZ4KoenLFeB++MMfuqMNt01FB9tXZfPyyy/nLNP4v//97+7oxOT6HKh81JwHbIdQKHtSrW48mcs777xjplGIy7ahTJqWOWXKlHqdXrbDplF2ulIfcVSrAU4eeuiheutbwzPPPONOmpWmTTPAWdH2me8cOPfvsuNtmTuN6BBqQwHOttM4aX6XXXaZO7omZKuLffbZx9yyJR9NV64Ap3OJs4lehJVryEZ7iLUOsvW9ek++i3riluszovJRcx7I1xHkois27XlBLttp6L88TTNmzBhnimRFO63o3clvvfXWyFTZKYANHDjQHV2wWg5w4m5cohvShgKFpkkqwGXbkK1YsSLr580W4EoZJNc5cFHDhg2rN66xNL9a3QN3zDHHZKzraBvUbTyynTMmKk8qwKn92T21ri9/+cvm1INsZs+eXa/tRIexY8e6bzH22msvU+62e/0Dm+tzJCXuto30UHMesJ1Bsfr06WPet3DhQrcogzqMcl7Y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>
