# Chapter 19: Evaluation and Monitoring | <mark>第 19 章：评估与监控</mark>

This chapter examines methodologies that allow intelligent agents to systematically assess their performance, monitor progress toward goals, and detect operational anomalies. While Chapter 11 outlines goal setting and monitoring, and Chapter 17 addresses Reasoning mechanisms, this chapter focuses on the continuous, often external, measurement of an agent's effectiveness, efficiency, and compliance with requirements. This includes defining metrics, establishing feedback loops, and implementing reporting systems to ensure agent performance aligns with expectations in operational environments (see Fig.1)

<mark>本章探讨了使智能体能够系统性地评估自身性能、监控目标进展并检测运行异常的方法论。虽然第 11 章概述了目标设定与监控，第 17 章讨论了推理机制，但本章聚焦于对智能体有效性、效率及需求合规性的持续性外部测量。这包括定义指标、建立反馈循环以及实施报告系统，以确保智能体性能在运行环境中符合预期（见图 1）。</mark>

![Best practices for evaluation and monitoring](/images/chapter19_fig1.png)

Fig:1. Best practices for evaluation and monitoring

<mark>图 1：评估与监控的最佳实践</mark>

---

## Practical Applications & Use Cases | <mark>实际应用与用例</mark>

Most Common Applications and Use Cases:

<mark>最常见的应用与用例：</mark>

- **Performance Tracking in Live Systems:** Continuously monitoring the accuracy, latency, and resource consumption of an agent deployed in a production environment (e.g., a customer service chatbot's resolution rate, response time).

- <mark><strong>实时系统中的性能跟踪：</strong>持续监控部署在生产环境中的智能体的准确性、延迟和资源消耗（例如，客户服务聊天机器人的解决率、响应时间）。</mark>

- **A/B Testing for Agent Improvements:** Systematically comparing the performance of different agent versions or strategies in parallel to identify optimal approaches (e.g., trying two different planning algorithms for a logistics agent).

- <mark><strong>智能体改进的 A/B 测试：</strong>系统性地并行比较不同智能体版本或策略的性能，以识别最优方法（例如，为物流智能体尝试两种不同的规划算法）。</mark>

- **Compliance and Safety Audits:** Generate automated audit reports that track an agent's compliance with ethical guidelines, regulatory requirements, and safety protocols over time. These reports can be verified by a human-in-the-loop or another agent, and can generate KPIs or trigger alerts upon identifying issues.

- <mark><strong>合规性与安全审计：</strong>生成自动化审计报告，跟踪智能体随时间对道德准则、监管要求和安全协议的遵守情况。这些报告可由人在回路中（Human-in-the-Loop）或另一个智能体进行验证，并可生成 KPI 或在发现问题时触发警报。</mark>

- **Enterprise systems:** To govern Agentic AI in corporate systems, a new control instrument, the AI "Contract," is needed. This dynamic agreement codifies the objectives, rules, and controls for AI-delegated tasks.

- <mark><strong>企业系统：</strong>为了在企业系统中管理具智能体特性的 AI（Agentic AI），需要一种新的控制工具——AI「合约」。这种动态协议将 AI 委托任务的目标、规则和控制进行编码。</mark>

- **Drift Detection:** Monitoring the relevance or accuracy of an agent's outputs over time, detecting when its performance degrades due to changes in input data distribution (concept drift) or environmental shifts.

- <mark><strong>漂移检测：</strong>随时间监控智能体输出的相关性或准确性，检测其性能何时因输入数据分布变化（概念漂移）或环境变化而下降。</mark>

- **Anomaly Detection in Agent Behavior:** Identifying unusual or unexpected actions taken by an agent that might indicate an error, a malicious attack, or an emergent un-desired behavior.

- <mark><strong>智能体行为异常检测：</strong>识别智能体采取的异常或意外行为，这些行为可能表明错误、恶意攻击或涌现的非预期行为。</mark>

- **Learning Progress Assessment:** For agents designed to learn, tracking their learning curve, improvement in specific skills, or generalization capabilities over different tasks or data sets.

- <mark><strong>学习进展评估：</strong>对于设计为可学习的智能体，跟踪其学习曲线、特定技能的改进或在不同任务或数据集上的泛化能力。</mark>

---

## Hands-On Code Example | <mark>实战代码示例</mark>

Developing a comprehensive evaluation framework for AI agents is a challenging endeavor, comparable to an academic discipline or a substantial publication in its complexity. This difficulty stems from the multitude of factors to consider, such as model performance, user interaction, ethical implications, and broader societal impact. Nevertheless, for practical implementation, the focus can be narrowed to critical use cases essential for the efficient and effective functioning of AI agents.

<mark>为 AI 智能体开发一个全面的评估框架是一项具有挑战性的工作，其复杂性可与一门学术学科或一本实质性出版物相媲美。这种困难源于需要考虑的众多因素，例如模型性能、用户交互、伦理影响和更广泛的社会影响。然而，对于实际实施而言，可以将重点缩小到对 AI 智能体高效有效运作至关重要的关键用例上。</mark>

**Agent Response Assessment:** This core process is essential for evaluating the quality and accuracy of an agent's outputs. It involves determining if the agent delivers pertinent, correct, logical, unbiased, and accurate information in response to given inputs. Assessment metrics may include factual correctness, fluency, grammatical precision, and adherence to the user's intended purpose.

<mark><strong>智能体响应评估：</strong>这一核心过程对于评估智能体输出的质量和准确性至关重要。它涉及确定智能体是否针对给定输入提供相关、正确、合乎逻辑、无偏见且准确的信息。评估指标可能包括事实正确性、流畅性、语法精确性以及对用户预期目的的遵循程度。</mark>

```py
def evaluate_response_accuracy(agent_output: str, expected_output: str) -> float:
    """Calculates a simple accuracy score for agent responses."""
    # This is a very basic exact match; real-world would use more sophisticated metrics
    return 1.0 if agent_output.strip().lower() == expected_output.strip().lower() else 0.0

# Example usage
agent_response = "The capital of France is Paris."
ground_truth = "Paris is the capital of France."
score = evaluate_response_accuracy(agent_response, ground_truth)
print(f"Response accuracy: {score}")
```

The Python function \`evaluate_response_accuracy\` calculates a basic accuracy score for an AI agent's response by performing an exact, case-insensitive comparison between the agent's output and the expected output, after removing leading or trailing whitespace. It returns a score of 1.0 for an exact match and 0.0 otherwise, representing a binary correct or incorrect evaluation. This method, while straightforward for simple checks, does not account for variations like paraphrasing or semantic equivalence.

<mark>Python 函数 <code>evaluate_response_accuracy</code> 通过在去除前导或尾随空格后，对智能体的输出和预期输出执行精确的不区分大小写比较，来计算 AI 智能体响应的基本准确性分数。对于精确匹配，它返回 1.0 的分数，否则返回 0.0，表示二元的正确或错误评估。这种方法虽然对于简单检查来说很直接，但不考虑释义或语义等价性等变化。</mark>

The problem lies in its method of comparison. The function performs a strict, character-for-character comparison of the two strings. In the example provided:

<mark>问题在于其比较方法。该函数对两个字符串执行严格的逐字符比较。在提供的示例中：</mark>

- agent_response: "The capital of France is Paris."
- ground_truth: "Paris is the capital of France."

Even after removing whitespace and converting to lowercase, these two strings are not identical. As a result, the function will incorrectly return an accuracy score of 0.0, even though both sentences convey the same meaning.

<mark>即使在去除空格并转换为小写后，这两个字符串也不相同。因此，该函数将错误地返回 0.0 的准确性分数，尽管两个句子传达的是相同的意思。</mark>

A straightforward comparison falls short in assessing semantic similarity, only succeeding if an agent's response exactly matches the expected output. A more effective evaluation necessitates advanced Natural Language Processing (NLP) techniques to discern the meaning between sentences. For thorough AI agent evaluation in real-world scenarios, more sophisticated metrics are often indispensable. These metrics can encompass String Similarity Measures like Levenshtein distance and Jaccard similarity, Keyword Analysis for the presence or absence of specific keywords, Semantic Similarity using cosine similarity with embedding models, LLM-as-a-Judge Evaluations (discussed later for assessing nuanced correctness and helpfulness), and RAG-specific Metrics such as faithfulness and relevance.

<mark>直接比较在评估语义相似性方面存在不足，只有当智能体的响应完全匹配预期输出时才会成功。更有效的评估需要先进的自然语言处理（NLP）技术来辨别句子之间的意义。对于现实场景中的 AI 智能体彻底评估，更复杂的指标通常是不可或缺的。这些指标可以包括字符串相似性度量（如 Levenshtein 距离和 Jaccard 相似性）、关键词分析（用于特定关键词的存在或缺失）、使用嵌入模型的余弦相似性进行语义相似性分析、LLM 作为评判者（LLM-as-a-Judge）评估（稍后讨论用于评估细微的正确性和有用性），以及 RAG 特定指标（如忠实度和相关性）。</mark>

**Latency Monitoring:** Latency Monitoring for Agent Actions is crucial in applications where the speed of an AI agent's response or action is a critical factor. This process measures the duration required for an agent to process requests and generate outputs. Elevated latency can adversely affect user experience and the agent's overall effectiveness, particularly in real-time or interactive environments. In practical applications, simply printing latency data to the console is insufficient. Logging this information to a persistent storage system is recommended. Options include structured log files (e.g., JSON), time-series databases (e.g., InfluxDB, Prometheus), data warehouses (e.g., Snowflake, BigQuery, PostgreSQL), or observability platforms (e.g., Datadog, Splunk, Grafana Cloud).

<mark>**延迟监控：**智能体操作的延迟监控在 AI 智能体响应或操作速度是关键因素的应用中至关重要。此过程测量智能体处理请求和生成输出所需的持续时间。延迟升高会对用户体验和智能体的整体有效性产生不利影响，特别是在实时或交互式环境中。在实际应用中，仅将延迟数据打印到控制台是不够的。建议将此信息记录到持久化存储系统。选项包括结构化日志文件（如 JSON）、时间序列数据库（如 InfluxDB、Prometheus）、数据仓库（如 Snowflake、BigQuery、PostgreSQL）或可观测性平台（如 Datadog、Splunk、Grafana Cloud）。</mark>

**Tracking Token Usage for LLM Interactions:** For LLM-powered agents, tracking token usage is crucial for managing costs and optimizing resource allocation. Billing for LLM interactions often depends on the number of tokens processed (input and output). Therefore, efficient token usage directly reduces operational expenses. Additionally, monitoring token counts helps identify potential areas for improvement in prompt engineering or response generation processes.

<mark>**跟踪 LLM 交互的 Token 使用：**对于基于 LLM 的智能体，跟踪 token 使用对于管理成本和优化资源分配至关重要。LLM 交互的计费通常取决于处理的 token 数量（输入和输出）。因此，高效的 token 使用直接降低运营费用。此外，监控 token 计数有助于识别提示工程或响应生成过程中潜在的改进领域。</mark>

```py
# This is conceptual as actual token counting depends on the LLM API
class LLMInteractionMonitor:
    def __init__(self):
        self.total_input_tokens = 0
        self.total_output_tokens = 0

    def record_interaction(self, prompt: str, response: str):
        # In a real scenario, use LLM API's token counter or a tokenizer
        input_tokens = len(prompt.split())  # Placeholder
        output_tokens = len(response.split())  # Placeholder
        self.total_input_tokens += input_tokens
        self.total_output_tokens += output_tokens
        print(f"Recorded interaction: Input tokens={input_tokens}, Output tokens={output_tokens}")

    def get_total_tokens(self):
        return self.total_input_tokens, self.total_output_tokens

# Example usage
monitor = LLMInteractionMonitor()
monitor.record_interaction("What is the capital of France?", "The capital of France is Paris.")
monitor.record_interaction("Tell me a joke.", "Why don't scientists trust atoms? Because they make up everything!")
input_t, output_t = monitor.get_total_tokens()
print(f"Total input tokens: {input_t}, Total output tokens: {output_t}")
```

This section introduces a conceptual Python class, \`LLMInteractionMonitor\`, developed to track token usage in large language model interactions. The class incorporates counters for both input and output tokens. Its \`record_interaction\` method simulates token counting by splitting the prompt and response strings. In a practical implementation, specific LLM API tokenizers would be employed for precise token counts. As interactions occur, the monitor accumulates the total input and output token counts. The \`get_total_tokens\` method provides access to these cumulative totals, essential for cost management and optimization of LLM usage.

<mark>本节介绍了一个概念性的 Python 类 <code>LLMInteractionMonitor</code>，用于跟踪大语言模型交互中的 token 使用情况。该类包含输入和输出 token 的计数器。其 <code>record_interaction</code> 方法通过分割提示和响应字符串来模拟 token 计数。在实际实现中，将使用特定的 LLM API 分词器来获得精确的 token 计数。随着交互的发生，监控器累积输入和输出 token 的总数。<code>get_total_tokens</code> 方法提供对这些累积总数的访问，这对于成本管理和 LLM 使用优化至关重要。</mark>

**Custom Metric for "Helpfulness" using LLM-as-a-Judge:** Evaluating subjective qualities like an AI agent's "helpfulness" presents challenges beyond standard objective metrics. A potential framework involves using an LLM as an evaluator. This LLM-as-a-Judge approach assesses another AI agent's output based on predefined criteria for "helpfulness." Leveraging the advanced linguistic capabilities of LLMs, this method offers nuanced, human-like evaluations of subjective qualities, surpassing simple keyword matching or rule-based assessments. Though in development, this technique shows promise for automating and scaling qualitative evaluations.

<mark><strong>使用 LLM 作为评判者的「有用性」自定义指标：</strong>评估 AI 智能体的「有用性」等主观品质带来了超越标准客观指标的挑战。一个潜在的框架涉及使用 LLM 作为评估者。这种 LLM 作为评判者（LLM-as-a-Judge）的方法基于「有用性」的预定义标准来评估另一个 AI 智能体的输出。利用 LLM 的高级语言能力，这种方法提供细微的、类人的主观品质评估，超越了简单的关键词匹配或基于规则的评估。尽管仍在开发中，但这项技术在自动化和扩展定性评估方面显示出前景。</mark>

```py
import google.generativeai as genai
import os
import json
import logging
from typing import Optional

# --- Configuration ---
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')

# Set your API key as an environment variable to run this script
# For example, in your terminal: export GOOGLE_API_KEY='your_key_here'
try:
    genai.configure(api_key=os.environ["GOOGLE_API_KEY"])
except KeyError:
    logging.error("Error: GOOGLE_API_KEY environment variable not set.")
    exit(1)

# --- LLM-as-a-Judge Rubric for Legal Survey Quality ---
LEGAL_SURVEY_RUBRIC = """
You are an expert legal survey methodologist and a critical legal reviewer. Your task is to evaluate the quality of a given legal survey question.

Provide a score from 1 to 5 for overall quality, along with a detailed rationale and specific feedback.

Focus on the following criteria:

1. **Clarity & Precision (Score 1-5):**
   * 1: Extremely vague, highly ambiguous, or confusing.
   * 3: Moderately clear, but could be more precise.
   * 5: Perfectly clear, unambiguous, and precise in its legal terminology (if applicable) and intent.

2. **Neutrality & Bias (Score 1-5):**
   * 1: Highly leading or biased, clearly influencing the respondent towards a specific answer.
   * 3: Slightly suggestive or could be interpreted as leading.
   * 5: Completely neutral, objective, and free from any leading language or loaded terms.

3. **Relevance & Focus (Score 1-5):**
   * 1: Irrelevant to the stated survey topic or out of scope.
   * 3: Loosely related but could be more focused.
   * 5: Directly relevant to the survey's objectives and well-focused on a single concept.

4. **Completeness (Score 1-5):**
   * 1: Omits critical information needed to answer accurately or provides insufficient context.
   * 3: Mostly complete, but minor details are missing.
   * 5: Provides all necessary context and information for the respondent to answer thoroughly.

5. **Appropriateness for Audience (Score 1-5):**
   * 1: Uses jargon inaccessible to the target audience or is overly simplistic for experts.
   * 3: Generally appropriate, but some terms might be challenging or oversimplified.
   * 5: Perfectly tailored to the assumed legal knowledge and background of the target survey audience.

**Output Format:**
Your response MUST be a JSON object with the following keys:
* `overall_score`: An integer from 1 to 5 (average of criterion scores, or your holistic judgment).
* `rationale`: A concise summary of why this score was given, highlighting major strengths and weaknesses.
* `detailed_feedback`: A bullet-point list detailing feedback for each criterion (Clarity, Neutrality, Relevance, Completeness, Audience Appropriateness). Suggest specific improvements.
* `concerns`: A list of any specific legal, ethical, or methodological concerns.
* `recommended_action`: A brief recommendation (e.g., "Revise for neutrality", "Approve as is", "Clarify scope").
"""

class LLMJudgeForLegalSurvey:
    """A class to evaluate legal survey questions using a generative AI model."""

    def __init__(self, model_name: str = 'gemini-1.5-flash-latest', temperature: float = 0.2):
        """
        Initializes the LLM Judge.

        Args:
            model_name (str): The name of the Gemini model to use.
                'gemini-1.5-flash-latest' is recommended for speed and cost.
                'gemini-1.5-pro-latest' offers the highest quality.
            temperature (float): The generation temperature. Lower is better for deterministic evaluation.
        """
        self.model = genai.GenerativeModel(model_name)
        self.temperature = temperature

    def _generate_prompt(self, survey_question: str) -> str:
        """Constructs the full prompt for the LLM judge."""
        return f"{LEGAL_SURVEY_RUBRIC}\n\n---\n**LEGAL SURVEY QUESTION TO EVALUATE:**\n{survey_question}\n---"

    def judge_survey_question(self, survey_question: str) -> Optional[dict]:
        """
        Judges the quality of a single legal survey question using the LLM.

        Args:
            survey_question (str): The legal survey question to be evaluated.

        Returns:
            Optional[dict]: A dictionary containing the LLM's judgment, or None if an error occurs.
        """
        full_prompt = self._generate_prompt(survey_question)

        try:
            logging.info(f"Sending request to '{self.model.model_name}' for judgment...")
            response = self.model.generate_content(
                full_prompt,
                generation_config=genai.types.GenerationConfig(
                    temperature=self.temperature,
                    response_mime_type="application/json"
                )
            )

            # Check for content moderation or other reasons for an empty response.
            if not response.parts:
                safety_ratings = response.prompt_feedback.safety_ratings
                logging.error(f"LLM response was empty or blocked. Safety Ratings: {safety_ratings}")
                return None

            return json.loads(response.text)

        except json.JSONDecodeError:
            logging.error(f"Failed to decode LLM response as JSON. Raw response: {response.text}")
            return None

        except Exception as e:
            logging.error(f"An unexpected error occurred during LLM judgment: {e}")
            return None

# --- Example Usage ---
if __name__ == "__main__":
    judge = LLMJudgeForLegalSurvey()

    # --- Good Example ---
    good_legal_survey_question = """
    To what extent do you agree or disagree that current intellectual property laws in Switzerland adequately protect emerging AI-generated content, assuming the content meets the originality criteria established by the Federal Supreme Court?

    (Select one: Strongly Disagree, Disagree, Neutral, Agree, Strongly Agree)
    """

    print("\n--- Evaluating Good Legal Survey Question ---")
    judgment_good = judge.judge_survey_question(good_legal_survey_question)
    if judgment_good:
        print(json.dumps(judgment_good, indent=2))

    # --- Biased/Poor Example ---
    biased_legal_survey_question = """
    Don't you agree that overly restrictive data privacy laws like the FADP are hindering essential technological innovation and economic growth in Switzerland?

    (Select one: Yes, No)
    """

    print("\n--- Evaluating Biased Legal Survey Question ---")
    judgment_biased = judge.judge_survey_question(biased_legal_survey_question)
    if judgment_biased:
        print(json.dumps(judgment_biased, indent=2))

    # --- Ambiguous/Vague Example ---
    vague_legal_survey_question = """
    What are your thoughts on legal tech?
    """

    print("\n--- Evaluating Vague Legal Survey Question ---")
    judgment_vague = judge.judge_survey_question(vague_legal_survey_question)
    if judgment_vague:
        print(json.dumps(judgment_vague, indent=2))
```

The Python code defines a class LLMJudgeForLegalSurvey designed to evaluate the quality of legal survey questions using a generative AI model. It utilizes the google.generativeai library to interact with Gemini models.

<mark>该 Python 代码定义了一个类 LLMJudgeForLegalSurvey，旨在使用生成式 AI 模型评估法律调查问题的质量。它利用 google.generativeai 库与 Gemini 模型进行交互。</mark>

The core functionality involves sending a survey question to the model along with a detailed rubric for evaluation. The rubric specifies five criteria for judging survey questions: Clarity & Precision, Neutrality & Bias, Relevance & Focus, Completeness, and Appropriateness for Audience. For each criterion, a score from 1 to 5 is assigned, and a detailed rationale and feedback are required in the output. The code constructs a prompt that includes the rubric and the survey question to be evaluated.

<mark>核心功能涉及将调查问题与详细的评估标准一起发送到模型。该标准指定了评判调查问题的五个标准：清晰度与精确性、中立性与偏见、相关性与聚焦、完整性以及对受众的适当性。对于每个标准，分配 1 到 5 的分数，并且输出中需要详细的理由和反馈。代码构建一个包含标准和待评估调查问题的提示。</mark>

The judge_survey_question method sends this prompt to the configured Gemini model, requesting a JSON response formatted according to the defined structure. The expected output JSON includes an overall score, a summary rationale, detailed feedback for each criterion, a list of concerns, and a recommended action. The class handles potential errors during the AI model interaction, such as JSON decoding issues or empty responses. The script demonstrates its operation by evaluating examples of legal survey questions, illustrating how the AI assesses quality based on the predefined criteria.

<mark>judge_survey_question 方法将此提示发送到配置的 Gemini 模型，请求根据定义的结构格式化的 JSON 响应。预期的输出 JSON 包括总体分数、摘要理由、每个标准的详细反馈、关注点列表以及推荐操作。该类处理 AI 模型交互期间的潜在错误，例如 JSON 解码问题或空响应。该脚本通过评估法律调查问题的示例来演示其操作，说明 AI 如何基于预定义标准评估质量。</mark>

Before we conclude, let's examine various evaluation methods, considering their strengths and weaknesses.

<mark>在结束之前，让我们考虑各种评估方法的优缺点。</mark>

| Evaluation Method | Strengths | Weaknesses |
| --- | --- | --- |
| Human Evaluation | Captures subtle behavior | Difficult to scale, expensive, and time-consuming, as it considers subjective human factors. |
| LLM-as-a-Judge | Consistent, efficient, and scalable. | Intermediate steps may be overlooked. Limited by LLM capabilities. |
| Automated Metrics | Scalable, efficient, and objective | Potential limitation in capturing complete capabilities. |

| <mark>评估方法</mark> | <mark>优势</mark> | <mark>劣势</mark> |
| --- | --- | --- |
| <mark>人工评估</mark> | <mark>捕捉细微行为</mark> | <mark>难以扩展、成本高且耗时，因为涉及主观的人为因素。</mark> |
| <mark>LLM 作为评判者</mark> | <mark>一致、高效且可扩展</mark> | <mark>中间步骤可能被忽略，受 LLM 能力限制。</mark> |
| <mark>自动化指标</mark> | <mark>可扩展、高效且客观</mark> | <mark>在捕捉完整能力方面可能存在局限性。</mark> |

---

## Agents trajectories | <mark>智能体轨迹</mark>

Evaluating agents' trajectories is essential, as traditional software tests are insufficient. Standard code yields predictable pass/fail results, whereas agents operate probabilistically, necessitating qualitative assessment of both the final output and the agent's trajectory-the sequence of steps taken to reach a solution. Evaluating multi-agent systems is challenging because they are constantly in flux. This requires developing sophisticated metrics that go beyond individual performance to measure the effectiveness of communication and teamwork. Moreover, the environments themselves are not static, demanding that evaluation methods, including test cases, adapt over time.

<mark>评估智能体的轨迹至关重要，因为传统的软件测试是不够的。标准代码产生可预测的通过/失败结果，而智能体以概率方式运行，需要对最终输出和智能体轨迹——达到解决方案所采取的步骤序列——进行定性评估。评估多智能体系统具有挑战性，因为它们不断变化。这需要开发超越个体性能的复杂指标，以衡量沟通和团队合作的有效性。此外，环境本身不是静态的，要求评估方法（包括测试用例）随时间适应。</mark>

This involves examining the quality of decisions, the reasoning process, and the overall outcome. Implementing automated evaluations is valuable, particularly for development beyond the prototype stage. Analyzing trajectory and tool use includes evaluating the steps an agent employs to achieve a goal, such as tool selection, strategies, and task efficiency. For example, an agent addressing a customer's product query might ideally follow a trajectory involving intent determination, database search tool use, result review, and report generation. The agent's actual actions are compared to this expected, or ground truth, trajectory to identify errors and inefficiencies. Comparison methods include exact match (requiring a perfect match to the ideal sequence), in-order match (correct actions in order, allowing extra steps), any-order match (correct actions in any order, allowing extra steps), precision (measuring the relevance of predicted actions), recall (measuring how many essential actions are captured), and single-tool use (checking for a specific action). Metric selection depends on specific agent requirements, with high-stakes scenarios potentially demanding an exact match, while more flexible situations might use an in-order or any-order match.

<mark>这涉及检查决策质量、推理过程和整体结果。实施自动化评估是有价值的，特别是对于原型阶段之后的开发。分析轨迹和工具使用包括评估智能体实现目标所采用的步骤，如工具选择、策略和任务效率。例如，处理客户产品查询的智能体可能理想地遵循涉及意图确定、数据库搜索工具使用、结果审查和报告生成的轨迹。智能体的实际操作与这个预期的或真实的（ground truth）轨迹进行比较，以识别错误和低效。比较方法包括精确匹配（要求与理想序列完美匹配）、顺序匹配（正确操作按顺序，允许额外步骤）、任意顺序匹配（正确操作以任意顺序，允许额外步骤）、精确度（测量预测操作的相关性）、召回率（测量捕获多少基本操作）和单工具使用（检查特定操作）。指标选择取决于特定的智能体需求，高风险场景可能要求精确匹配，而更灵活的情况可能使用顺序或任意顺序匹配。</mark>

Evaluation of AI agents involves two primary approaches: using test files and using evalset files. Test files, in JSON format, represent single, simple agent-model interactions or sessions and are ideal for unit testing during active development, focusing on rapid execution and simple session complexity. Each test file contains a single session with multiple turns, where a turn is a user-agent interaction including the user's query, expected tool use trajectory, intermediate agent responses, and final response. For example, a test file might detail a user request to "Turn off device_2 in the Bedroom," specifying the agent's use of a set_device_info tool with parameters like location: Bedroom, device_id: device_2, and status: OFF, and an expected final response of "I have set the device_2 status to off." Test files can be organized into folders and may include a test_config.json file to define evaluation criteria. Evalset files utilize a dataset called an "evalset" to evaluate interactions, containing multiple potentially lengthy sessions suited for simulating complex, multi-turn conversations and integration tests. An evalset file comprises multiple "evals," each representing a distinct session with one or more "turns" that include user queries, expected tool use, intermediate responses, and a reference final response. An example evalset might include a session where the user first asks "What can you do?" and then says "Roll a 10 sided dice twice and then check if 9 is a prime or not," defining expected roll\\\_die tool calls and a check_prime tool call, along with the final response summarizing the dice rolls and the prime check.

<mark>AI 智能体的评估涉及两种主要方法：使用测试文件和使用评估集（evalset）文件。测试文件采用 JSON 格式，代表单个、简单的智能体-模型交互或会话，非常适合在积极开发期间进行单元测试，专注于快速执行和简单的会话复杂性。每个测试文件包含一个具有多个回合的单个会话，其中回合是用户-智能体交互，包括用户查询、预期工具使用轨迹、中间智能体响应和最终响应。例如，测试文件可能详细说明用户请求「Turn off device_2 in the Bedroom」，指定智能体使用 <code>set_device_info</code> 工具及参数如 <code>location: Bedroom</code>、<code>device_id: device_2</code> 和 <code>status: OFF</code>，以及预期的最终响应「I have set the device_2 status to off」。测试文件可以组织到文件夹中，并可能包含一个 <code>test_config.json</code> 文件来定义评估标准。评估集文件利用称为 <code>evalset</code> 的数据集来评估交互，包含多个可能很长的会话，适合模拟复杂的多回合对话和集成测试。评估集文件包含多个 <code>evals</code>，每个代表一个独立的会话，具有一个或多个回合，包括用户查询、预期工具使用、中间响应和参考最终响应。示例评估集可能包括一个会话，其中用户首先询问「What can you do?」，然后说「Roll a 10 sided dice twice and then check if 9 is a prime or not」，定义预期的 <code>roll_die</code> 工具调用和 <code>check_prime</code> 工具调用，以及总结骰子投掷和素数检查的最终响应。</mark>

**Multi-agents**: Evaluating a complex AI system with multiple agents is much like assessing a team project. Because there are many steps and handoffs, its complexity is an advantage, allowing you to check the quality of work at each stage. You can examine how well each individual "agent" performs its specific job, but you must also evaluate how the entire system is performing as a whole.

<mark><strong>多智能体：</strong>评估具有多个智能体的复杂 AI 系统很像评估团队项目。由于有许多步骤和交接，其复杂性是一个优势，允许您检查每个阶段的工作质量。您可以检查每个单独的「智能体」执行其特定工作的情况，但也必须评估整个系统作为一个整体的表现。</mark>

To do this, you ask key questions about the team's dynamics, supported by concrete examples:

<mark>为此，您需要提出关于团队动态的关键问题，并通过具体示例支持：</mark>

- Are the agents cooperating effectively? For instance, after a 'Flight-Booking Agent' secures a flight, does it successfully pass the correct dates and destination to the 'Hotel-Booking Agent'? A failure in cooperation could lead to a hotel being booked for the wrong week.

- <mark>智能体是否有效合作？例如，在「航班预订智能体」确保航班后，它是否成功地将正确的日期和目的地传递给「酒店预订智能体」？合作失败可能导致为错误的周预订酒店。</mark>

- Did they create a good plan and stick to it? Imagine the plan is to first book a flight, then a hotel. If the 'Hotel Agent' tries to book a room before the flight is confirmed, it has deviated from the plan. You also check if an agent gets stuck, for example, endlessly searching for a "perfect" rental car and never moving on to the next step.

- <mark>它们是否制定了良好的计划并坚持执行？想象一下，计划是先预订航班，然后预订酒店。如果「酒店智能体」在航班确认之前尝试预订房间，它就偏离了计划。您还要检查智能体是否卡住了，例如，无休止地搜索「完美」的租车，永远不进入下一步。</mark>

- Is the right agent being chosen for the right task? If a user asks about the weather for their trip, the system should use a specialized 'Weather Agent' that provides live data. If it instead uses a 'General Knowledge Agent' that gives a generic answer like "it's usually warm in summer," it has chosen the wrong tool for the job.

- <mark>是否为正确的任务选择了正确的智能体？如果用户询问旅行的天气，系统应该使用提供实时数据的专门「天气智能体」。如果它使用「通用知识智能体」给出像「夏天通常很温暖」这样的通用答案，则它为这项工作选择了错误的工具。</mark>

- Finally, does adding more agents improve performance? If you add a new 'Restaurant-Reservation Agent' to the team, does it make the overall trip-planning better and more efficient? Or does it create conflicts and slow the system down, indicating a problem with scalability?.

- <mark>最后，添加更多智能体是否会提高性能？如果您向团队添加新的「餐厅预订智能体」，它是否会使整体旅行规划更好、更有效率？还是它会造成冲突并减慢系统速度，表明存在可扩展性问题？</mark>

---

## From Agents to Advanced Contractors | <mark>从智能体到高级承包商</mark>

Recently, it has been proposed (Agent Companion, gulli et al.) an evolution from simple AI agents to advanced "contractors", moving from probabilistic, often unreliable systems to more deterministic and accountable ones designed for complex, high-stakes environments (see Fig.2).

<mark>最近有人提出（Agent Companion，Gulli 等人）从简单的 AI 智能体演进到高级「承包商」，从概率性的、往往不可靠的系统转向更确定性和可问责的系统，专为复杂、高风险环境设计（见图 2）。</mark>

Today's common AI agents operate on brief, underspecified instructions, which makes them suitable for simple demonstrations but brittle in production, where ambiguity leads to failure. The "contractor" model addresses this by establishing a rigorous, formalized relationship between the user and the AI, built upon a foundation of clearly defined and mutually agreed-upon terms, much like a legal service agreement in the human world. This transformation is supported by four key pillars that collectively ensure clarity, reliability, and robust execution of tasks that were previously beyond the scope of autonomous systems.

<mark>当今常见的 AI 智能体基于简短、未充分指定的指令运行，这使它们适合简单演示，但在生产环境中脆弱，模糊性会导致失败。「承包商」模型通过在用户和 AI 之间建立严格的、正式化的关系来解决这个问题，建立在明确定义且双方同意的条款基础上，很像人类世界的法律服务协议。这一转变由四个关键支柱支撑，它们共同确保了先前超出自主系统范围的任务的清晰性、可靠性和稳健执行。</mark>

First is the pillar of the Formalized Contract, a detailed specification that serves as the single source of truth for a task. It goes far beyond a simple prompt. For example, a contract for a financial analysis task wouldn't just say "analyze last quarter's sales"; it would demand "a 20-page PDF report analyzing European market sales from Q1 2025, including five specific data visualizations, a comparative analysis against Q1 2024, and a risk assessment based on the included dataset of supply chain disruptions." This contract explicitly defines the required deliverables, their precise specifications, the acceptable data sources, the scope of work, and even the expected computational cost and completion time, making the outcome objectively verifiable.

<mark>第一个支柱是正式化合约（Formalized Contract），这是一个详细的规范，作为任务的单一真实来源。它远远超出了简单的提示。例如，财务分析任务的合约不会只是说「分析上一季度的销售额」；它会要求「一份 20 页的 PDF 报告，分析 2025 年第一季度欧洲市场销售情况，包括五个特定的数据可视化、与 2024 年第一季度的比较分析，以及基于包含的供应链中断数据集的风险评估」。此合约明确定义了所需的交付成果、其精确规范、可接受的数据源、工作范围，甚至预期的计算成本和完成时间，使结果客观可验证。</mark>

Second is the pillar of a Dynamic Lifecycle of Negotiation and Feedback. The contract is not a static command but the start of a dialogue. The contractor agent can analyze the initial terms and negotiate. For instance, if a contract demands the use of a specific proprietary data source the agent cannot access, it can return feedback stating, "The specified XYZ database is inaccessible. Please provide credentials or approve the use of an alternative public database, which may slightly alter the data's granularity." This negotiation phase, which also allows the agent to flag ambiguities or potential risks, resolves misunderstandings before execution begins, preventing costly failures and ensuring the final output aligns perfectly with the user's actual intent.

<mark>第二个支柱是协商与反馈的动态生命周期（Dynamic Lifecycle of Negotiation and Feedback）。合约不是静态命令，而是对话的开始。承包商智能体可以分析初始条款并协商。例如，如果合约要求使用智能体无法访问的特定专有数据源，它可以返回反馈说：「指定的 XYZ 数据库无法访问。请提供凭据或批准使用替代公共数据库，这可能会略微改变数据的粒度。」这个协商阶段还允许智能体标记模糊性或潜在风险，在执行开始之前解决误解，防止代价高昂的失败，并确保最终输出完全符合用户的实际意图。</mark>


![Contract execution example among agents](/images/chapter19_fig2.png)
Fig. 2: Contract execution example among agents

<mark>图 2：智能体之间的合约执行示例</mark>

The third pillar is Quality-Focused Iterative Execution. Unlike agents designed for low-latency responses, a contractor prioritizes correctness and quality. It operates on a principle of self-validation and correction. For a code generation contract, for example, the agent would not just write the code; it would generate multiple algorithmic approaches, compile and run them against a suite of unit tests defined within the contract, score each solution on metrics like performance, security, and readability, and only submit the version that passes all validation criteria. This internal loop of generating, reviewing, and improving its own work until the contract's specifications are met is crucial for building trust in its outputs.

<mark>第三个支柱是质量导向的迭代执行（Quality-Focused Iterative Execution）。与设计为低延迟响应的智能体不同，承包商优先考虑正确性和质量。它基于自我验证和纠正的原则运作。例如，对于代码生成合约，智能体不会只是编写代码；它会生成多种算法方法，针对合约中定义的一套单元测试编译并运行它们，根据性能、安全性和可读性等指标为每个解决方案评分，并且只提交通过所有验证标准的版本。这种生成、审查和改进自己工作的内部循环，直到满足合约规范，对于建立对其输出的信任至关重要。</mark>

Finally, the fourth pillar is Hierarchical Decomposition via Subcontracts. For tasks of significant complexity, a primary contractor agent can act as a project manager, breaking the main goal into smaller, more manageable sub-tasks. It achieves this by generating new, formal "subcontracts." For example, a master contract to "build an e-commerce mobile application" could be decomposed by the primary agent into subcontracts for "designing the UI/UX," "developing the user authentication module," "creating the product database schema," and "integrating a payment gateway." Each of these subcontracts is a complete, independent contract with its own deliverables and specifications, which could be assigned to other specialized agents. This structured decomposition allows the system to tackle immense, multifaceted projects in a highly organized and scalable manner, marking the transition of AI from a simple tool to a truly autonomous and reliable problem-solving engine.

<mark>最后，第四个支柱是通过子合约的分层分解（Hierarchical Decomposition via Subcontracts）。对于重大复杂性的任务，主承包商智能体可以充当项目经理，将主要目标分解为更小、更可管理的子任务。它通过生成新的、正式的「子合约」来实现这一点。例如，「构建电子商务移动应用程序」的主合约可以由主智能体分解为「设计 UI/UX」、「开发用户身份验证模块」、「创建产品数据库模式」和「集成支付网关」的子合约。这些子合约中的每一个都是一个完整的、独立的合约，具有自己的交付成果和规范，可以分配给其他专业智能体。这种结构化分解允许系统以高度组织化和可扩展的方式处理庞大、多方面的项目，标志着 AI 从简单工具过渡到真正自主和可靠的问题解决引擎。</mark>

Ultimately, this contractor framework reimagines AI interaction by embedding principles of formal specification, negotiation, and verifiable execution directly into the agent's core logic. This methodical approach elevates artificial intelligence from a promising but often unpredictable assistant into a dependable system capable of autonomously managing complex projects with auditable precision. By solving the critical challenges of ambiguity and reliability, this model paves the way for deploying AI in mission-critical domains where trust and accountability are paramount.

<mark>最终，这个承包商框架通过将正式规范、协商和可验证执行的原则直接嵌入到智能体的核心逻辑中，重新构想了 AI 交互。这种系统性方法将人工智能从一个有前途但往往不可预测的助手提升为一个能够以可审计的精度自主管理复杂项目的可靠系统。通过解决模糊性和可靠性的关键挑战，该模型为在信任和问责至关重要的关键任务领域部署 AI 铺平了道路。</mark>

---

## Google's ADK | <mark>Google ADK</mark>

Before concluding, let's look at a concrete example of a framework that supports evaluation. Agent evaluation with Google's ADK (see Fig.3) can be conducted via three methods: web-based UI (adk web) for interactive evaluation and dataset generation, programmatic integration using pytest for incorporation into testing pipelines, and direct command-line interface (adk eval) for automated evaluations suitable for regular build generation and verification processes.

<mark>在结束之前，让我们看一个支持评估的框架的具体示例。使用 Google ADK 进行智能体评估（见图 3）可以通过三种方法进行：基于 Web 的 UI（<code>adk web</code>）用于交互式评估和数据集生成、使用 pytest 的程序化集成用于融入测试管道，以及直接命令行界面（<code>adk eval</code>）用于适合定期构建生成和验证过程的自动化评估。</mark>

![Evaluation Support for Google ADK](/images/chapter19_fig3.png)

Fig.3: Evaluation Support for Google ADK

<mark>图 3：Google ADK 的评估支持</mark>

The web-based UI enables interactive session creation and saving into existing or new eval sets, displaying evaluation status. Pytest integration allows running test files as part of integration tests by calling AgentEvaluator.evaluate, specifying the agent module and test file path.

<mark>基于 Web 的 UI 可以交互式创建会话并将其保存到现有或新的评估集中，显示评估状态。Pytest 集成允许通过调用 <code>AgentEvaluator.evaluate</code> 将测试文件作为集成测试的一部分运行，指定智能体模块和测试文件路径。</mark>

The command-line interface facilitates automated evaluation by providing the agent module path and eval set file, with options to specify a configuration file or print detailed results. Specific evals within a larger eval set can be selected for execution by listing them after the eval set filename, separated by commas.

<mark>命令行界面通过提供智能体模块路径和评估集文件来促进自动化评估，并提供指定配置文件或打印详细结果的选项。可以通过在评估集文件名后列出它们并用逗号分隔来选择更大评估集中的特定评估进行执行。</mark>

---

## At a Glance | <mark>要点速览</mark>

**What:** Agentic systems and LLMs operate in complex, dynamic environments where their performance can degrade over time. Their probabilistic and non-deterministic nature means that traditional software testing is insufficient for ensuring reliability. Evaluating dynamic multi-agent systems is a significant challenge because their constantly changing nature and that of their environments demand the development of adaptive testing methods and sophisticated metrics that can measure collaborative success beyond individual performance. Problems like data drift, unexpected interactions, tool calling, and deviations from intended goals can arise after deployment. Continuous assessment is therefore necessary to measure an agent's effectiveness, efficiency, and adherence to operational and safety requirements.

<mark><strong>问题所在：</strong>智能体系统（Agentic systems）和 LLM 在复杂、动态的环境中运行，其性能可能随时间而下降。它们的概率性和非确定性特性意味着传统的软件测试不足以确保可靠性。评估动态多智能体系统是一项重大挑战，因为它们不断变化的本质及其环境要求开发自适应测试方法和复杂指标，这些指标可以衡量超越个体性能的协作成功。数据漂移、意外交互、工具调用和偏离预期目标等问题可能在部署后出现。因此，持续评估对于衡量智能体的有效性、效率以及对运营和安全要求的遵守是必要的。</mark>

**Why:** A standardized evaluation and monitoring framework provides a systematic way to assess and ensure the ongoing performance of intelligent agents. This involves defining clear metrics for accuracy, latency, and resource consumption, like token usage for LLMs. It also includes advanced techniques such as analyzing agentic trajectories to understand the reasoning process and employing an LLM-as-a-Judge for nuanced, qualitative assessments. By establishing feedback loops and reporting systems, this framework allows for continuous improvement, A/B testing, and the detection of anomalies or performance drift, ensuring the agent remains aligned with its objectives.

<mark><strong>解决之道：</strong>标准化的评估与监控框架提供了一种系统性方法来评估和确保智能体的持续性能。这涉及为准确性、延迟和资源消耗（如 LLM 的 token 使用）定义清晰的指标。它还包括先进的技术，如分析智能体轨迹以理解推理过程，以及采用 LLM 作为评判者进行细微的定性评估。通过建立反馈循环和报告系统，该框架允许持续改进、A/B 测试以及异常或性能漂移的检测，确保智能体保持与其目标一致。</mark>

**Rule of thumb:** Use this pattern when deploying agents in live, production environments where real-time performance and reliability are critical. Additionally, use it when needing to systematically compare different versions of an agent or its underlying models to drive improvements, and when operating in regulated or high-stakes domains requiring compliance, safety, and ethical audits. This pattern is also suitable when an agent's performance may degrade over time due to changes in data or the environment (drift), or when evaluating complex agentic behavior, including the sequence of actions (trajectory) and the quality of subjective outputs like helpfulness.

<mark><strong>经验法则：</strong>在将智能体部署到实时性能和可靠性至关重要的实时生产环境时使用此模式。此外，当需要系统性地比较智能体的不同版本或其底层模型以推动改进时，以及在需要合规性、安全性和伦理审计的受监管或高风险领域运营时使用它。当智能体的性能可能因数据或环境变化（漂移）而随时间下降时，或当评估复杂的智能体行为（包括操作序列（轨迹）和主观输出（如有用性）的质量）时，此模式也适用。</mark>

**Visual summary**

<mark><strong>可视化总结</strong></mark>

![Evaluation and Monitoring design pattern](/images/chapter19_fig4.png)

Fig.4: Evaluation and Monitoring design pattern

<mark>图 4：评估与监控设计模式</mark>

---

## Key Takeaways | <mark>关键要点</mark>

- Evaluating intelligent agents goes beyond traditional tests to continuously measure their effectiveness, efficiency, and adherence to requirements in real-world environments.

- <mark>评估智能体超越了传统测试，可以持续测量其在现实世界环境中的有效性、效率以及对需求的遵守。</mark>

- Practical applications of agent evaluation include performance tracking in live systems, A/B testing for improvements, compliance audits, and detecting drift or anomalies in behavior.

- <mark>智能体评估的实际应用包括实时系统中的性能跟踪、改进的 A/B 测试、合规性审计以及检测行为漂移或异常。</mark>

- Basic agent evaluation involves assessing response accuracy, while real-world scenarios demand more sophisticated metrics like latency monitoring and token usage tracking for LLM-powered agents.

- <mark>基本的智能体评估涉及评估响应准确性，而现实场景需要更复杂的指标，如延迟监控和基于 LLM 的智能体的 token 使用跟踪。</mark>

- Agent trajectories, the sequence of steps an agent takes, are crucial for evaluation, comparing actual actions against an ideal, ground-truth path to identify errors and inefficiencies.

- <mark>智能体轨迹，即智能体采取的步骤序列，对于评估至关重要，将实际操作与理想的真实路径进行比较，以识别错误和低效。</mark>

- The ADK provides structured evaluation methods through individual test files for unit testing and comprehensive evalset files for integration testing, both defining expected agent behavior.

- <mark>ADK 通过用于单元测试的单个测试文件和用于集成测试的综合评估集文件提供结构化评估方法，两者都定义了预期的智能体行为。</mark>

- Agent evaluations can be executed via a web-based UI for interactive testing, programmatically with pytest for CI/CD integration, or through a command-line interface for automated workflows.

- <mark>智能体评估可以通过基于 Web 的 UI 进行交互式测试、使用 pytest 以编程方式进行 CI/CD 集成，或通过命令行界面进行自动化工作流程执行。</mark>

- In order to make AI reliable for complex, high-stakes tasks, we must move from simple prompts to formal "contracts" that precisely define verifiable deliverables and scope. This structured agreement allows the Agents to negotiate, clarify ambiguities, and iteratively validate its own work, transforming it from an unpredictable tool into an accountable and trustworthy system.

- <mark>为了使 AI 在复杂、高风险任务中可靠，我们必须从简单的提示转向精确定义可验证交付成果和范围的正式「合约」。这种结构化协议允许智能体协商、澄清模糊性并迭代验证其自身工作，将其从不可预测的工具转变为可问责和可信赖的系统。</mark>

---

## Conclusions | <mark>结论</mark>

In conclusion, effectively evaluating AI agents requires moving beyond simple accuracy checks to a continuous, multi-faceted assessment of their performance in dynamic environments. This involves practical monitoring of metrics like latency and resource consumption, as well as sophisticated analysis of an agent's decision-making process through its trajectory. For nuanced qualities like helpfulness, innovative methods such as the LLM-as-a-Judge are becoming essential, while frameworks like Google's ADK provide structured tools for both unit and integration testing. The challenge intensifies with multi-agent systems, where the focus shifts to evaluating collaborative success and effective cooperation.

<mark>总之，有效评估 AI 智能体需要超越简单的准确性检查，对其在动态环境中的性能进行持续、多方面的评估。这涉及对延迟和资源消耗等指标的实际监控，以及通过其轨迹对智能体决策过程的复杂分析。对于有用性等细微品质，LLM 作为评判者等创新方法正变得至关重要，而像 Google ADK 这样的框架为单元测试和集成测试提供了结构化工具。在多智能体系统中，挑战加剧，焦点转移到评估协作成功和有效合作上。</mark>

To ensure reliability in critical applications, the paradigm is shifting from simple, prompt-driven agents to advanced "contractors" bound by formal agreements. These contractor agents operate on explicit, verifiable terms, allowing them to negotiate, decompose tasks, and self-validate their work to meet rigorous quality standards. This structured approach transforms agents from unpredictable tools into accountable systems capable of handling complex, high-stakes tasks. Ultimately, this evolution is crucial for building the trust required to deploy sophisticated agentic AI in mission-critical domains.

<mark>为确保关键应用中的可靠性，范式正从简单的、由提示驱动的智能体转向受正式协议约束的高级"承包商"。这些承包商智能体基于明确、可验证的条款运作，允许它们协商、分解任务并自我验证其工作以满足严格的质量标准。这种结构化方法将智能体从不可预测的工具转变为能够处理复杂、高风险任务的可问责系统。最终，这一演进对于建立在关键任务领域部署复杂智能体 AI 所需的信任至关重要。</mark>

---

## References | <mark>参考文献</mark>

Relevant research includes:

<mark>相关研究包括：</mark>

- ADK Web: <https://github.com/google/adk-web>
- ADK Evaluate: <https://google.github.io/adk-docs/evaluate/>
- Survey on Evaluation of LLM-based Agents, <https://arxiv.org/abs/2503.16416>
- Agent-as-a-Judge: Evaluate Agents with Agents, <https://arxiv.org/abs/2410.10934>
- Agent Companion, gulli et al: <https://www.kaggle.com/whitepaper-agent-companion>
