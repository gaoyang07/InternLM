# InternLM3

## InternLM3-8B-Instruct

### 介绍

InternLM3 开源了一个80亿参数的指令模型 InternLM3-8B-Instruct，专为通用用途和高级推理而设计。该模型具有以下特点：

- **以更低成本实现更强性能**：
  在推理和知识密集型任务上的最先进性能超越了 Llama3.1-8B 和 Qwen2.5-7B 等模型。值得注意的是，InternLM3 仅使用4万亿个高质量标记进行训练，相比同等规模的其他LLM节省了75%以上的训练成本。
- **深度思考能力**：
  InternLM3 支持深度思考模式，通过长链思维解决复杂推理任务，同时也支持流畅用户交互的正常响应模式。

### 模型库

| 模型                      | Transformers                                              | ModelScope                                              | Modelers                                              | 发布日期   |
| ------------------------- | --------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------------- | ---------- |
| **InternLM3-8B-Instruct** | [🤗internlm3_8B_instruct](https://huggingface.co/internlm/internlm3-8b-instruct) | [<img src="./assets/modelscope_logo.png" width="20px" /> internlm3_8b_instruct](https://www.modelscope.cn/models/Shanghai_AI_Laboratory/internlm3-8b-instruct/summary) | [![Open in Modelers](https://modelers.cn/assets/logo1-1bf58310.svg)](https://modelers.cn/models/Intern/internlm3-8b-instruct) | 2025-01-15 |

### 性能评估

我们使用开源评估工具 [OpenCompass](https://github.com/internLM/OpenCompass/) 对 InternLM 进行了全面评估。评估涵盖了五个维度的能力：学科能力、语言能力、知识能力、推理能力和理解能力。以下是一些评估结果，您可以访问 [OpenCompass 排行榜](https://rank.opencompass.org.cn) 获取更多评估结果。

| 基准测试 |                                 | InternLM3-8B-Instruct | Qwen2.5-7B-Instruct | Llama3.1-8B-Instruct | GPT-4o-mini(闭源) |
| -------- | ------------------------------- | --------------------- | ------------------- | -------------------- | ----------------- |
| 通用     | CMMLU(0-shot)                   | **83.1**              | 75.8                | 53.9                 | 66.0              |
|          | MMLU(0-shot)                    | 76.6                  | **76.8**            | 71.8                 | 82.7              |
|          | MMLU-Pro(0-shot)                | **57.6**              | 56.2                | 48.1                 | 64.1              |
| 推理     | GPQA-Diamond(0-shot)            | **37.4**              | 33.3                | 24.2                 | 42.9              |
|          | DROP(0-shot)                    | **83.1**              | 80.4                | 81.6                 | 85.2              |
|          | HellaSwag(10-shot)              | **91.2**              | 85.3                | 76.7                 | 89.5              |
|          | KOR-Bench(0-shot)               | **56.4**              | 44.6                | 47.7                 | 58.2              |
| 数学     | MATH-500(0-shot)                | **83.0**\*            | 72.4                | 48.4                 | 74.0              |
|          | AIME2024(0-shot)                | **20.0**\*            | 16.7                | 6.7                  | 13.3              |
| 编程     | LiveCodeBench(2407-2409 Pass@1) | **17.8**              | 16.8                | 12.9                 | 21.8              |
|          | HumanEval(Pass@1)               | 82.3                  | **85.4**            | 72.0                 | 86.6              |
| 指令跟随 | IFEval(Prompt-Strict)           | **79.3**              | 71.7                | 75.2                 | 79.7              |
| 长上下文 | RULER(4-128K Average)           | 87.9                  | 81.4                | **88.5**             | 90.7              |
| 对话     | AlpacaEval 2.0(LC WinRate)      | **51.1**              | 30.3                | 25.0                 | 50.7              |
|          | WildBench(Raw Score)            | **33.1**              | 23.3                | 1.5                  | 40.3              |
|          | MT-Bench-101(Score 1-10)        | **8.59**              | 8.49                | 8.37                 | 8.87              |

- 评估结果来自 [OpenCompass](https://github.com/internLM/OpenCompass/)（部分数据标有 \*，表示使用思考模式评估），评估配置可在 [OpenCompass](https://github.com/internLM/OpenCompass/) 提供的配置文件中找到。
- 由于 [OpenCompass](https://github.com/internLM/OpenCompass/) 版本迭代，评估数据可能存在数值差异，请以 [OpenCompass](https://github.com/internLM/OpenCompass/) 的最新评估结果为准。

**限制：** 尽管我们在训练过程中努力确保模型的安全性，并鼓励模型生成符合伦理和法律要求的文本，但由于模型的规模和概率生成范式，模型仍可能产生意外输出。例如，生成的响应可能包含偏见、歧视或其他有害内容。请不要传播此类内容。我们不对传播有害信息造成的任何后果负责。
