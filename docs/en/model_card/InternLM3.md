# InternLM3

## InternLM3-8B-Instruct

### Introduction

InternLM3 has open-sourced an 8-billion parameter instruction model, InternLM3-8B-Instruct, designed for general-purpose usage and advanced reasoning. This model has the following characteristics:

- **Enhanced performance at reduced cost**:
  State-of-the-art performance on reasoning and knowledge-intensive tasks surpass models like Llama3.1-8B and Qwen2.5-7B. Remarkably, InternLM3 is trained on only 4 trillion high-quality tokens, saving more than 75% of the training cost compared to other LLMs of similar scale.
- **Deep thinking capability**:
  InternLM3 supports both the deep thinking mode for solving complicated reasoning tasks via the long chain-of-thought and the normal response mode for fluent user interactions.

### Model Zoo

| Model                     | Transformers                                             | ModelScope                                             | Modelers                                              | Release Date |
| ------------------------- | -------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------- | ------------ |
| **InternLM3-8B-Instruct** | [🤗internlm3_8B_instruct](https://huggingface.co/internlm/internlm3-8b-instruct) | [<img src="./assets/modelscope_logo.png" width="20px" /> internlm3_8b_instruct](https://www.modelscope.cn/models/Shanghai_AI_Laboratory/internlm3-8b-instruct/summary) | [![Open in Modelers](https://modelers.cn/assets/logo1-1bf58310.svg)](https://modelers.cn/models/Intern/internlm3-8b-instruct) | 2025-01-15   |

### Performance Evaluation

We conducted a comprehensive evaluation of InternLM using the open-source evaluation tool [OpenCompass](https://github.com/internLM/OpenCompass/). The evaluation covered five dimensions of capabilities: disciplinary competence, language competence, knowledge competence, inference competence, and comprehension competence. Here are some of the evaluation results, and you can visit the [OpenCompass leaderboard](https://rank.opencompass.org.cn) for more evaluation results.

| Benchmark    |                                 | InternLM3-8B-Instruct | Qwen2.5-7B-Instruct | Llama3.1-8B-Instruct | GPT-4o-mini(close source) |
| ------------ | ------------------------------- | --------------------- | ------------------- | -------------------- | ------------------------- |
| General      | CMMLU(0-shot)                   | **83.1**              | 75.8                | 53.9                 | 66.0                      |
|              | MMLU(0-shot)                    | 76.6                  | **76.8**            | 71.8                 | 82.7                      |
|              | MMLU-Pro(0-shot)                | **57.6**              | 56.2                | 48.1                 | 64.1                      |
| Reasoning    | GPQA-Diamond(0-shot)            | **37.4**              | 33.3                | 24.2                 | 42.9                      |
|              | DROP(0-shot)                    | **83.1**              | 80.4                | 81.6                 | 85.2                      |
|              | HellaSwag(10-shot)              | **91.2**              | 85.3                | 76.7                 | 89.5                      |
|              | KOR-Bench(0-shot)               | **56.4**              | 44.6                | 47.7                 | 58.2                      |
| MATH         | MATH-500(0-shot)                | **83.0**\*            | 72.4                | 48.4                 | 74.0                      |
|              | AIME2024(0-shot)                | **20.0**\*            | 16.7                | 6.7                  | 13.3                      |
| Coding       | LiveCodeBench(2407-2409 Pass@1) | **17.8**              | 16.8                | 12.9                 | 21.8                      |
|              | HumanEval(Pass@1)               | 82.3                  | **85.4**            | 72.0                 | 86.6                      |
| Instrunction | IFEval(Prompt-Strict)           | **79.3**              | 71.7                | 75.2                 | 79.7                      |
| Long Context | RULER(4-128K Average)           | 87.9                  | 81.4                | **88.5**             | 90.7                      |
| Chat         | AlpacaEval 2.0(LC WinRate)      | **51.1**              | 30.3                | 25.0                 | 50.7                      |
|              | WildBench(Raw Score)            | **33.1**              | 23.3                | 1.5                  | 40.3                      |
|              | MT-Bench-101(Score 1-10)        | **8.59**              | 8.49                | 8.37                 | 8.87                      |

- The evaluation results were obtained from [OpenCompass](https://github.com/internLM/OpenCompass/) (some data marked with \*, which means evaluating with Thinking Mode), and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/internLM/OpenCompass/).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/internLM/OpenCompass/), so please refer to the latest evaluation results of [OpenCompass](https://github.com/internLM/OpenCompass/).
  **Limitations:** Although we have made efforts to ensure the safety of the model during the training process and to encourage the model to generate text that complies with ethical and legal requirements, the model may still produce unexpected outputs due to its size and probabilistic generation paradigm. For example, the generated responses may contain biases, discrimination, or other harmful content. Please do not propagate such content. We are not responsible for any consequences resulting from the dissemination of harmful information.
