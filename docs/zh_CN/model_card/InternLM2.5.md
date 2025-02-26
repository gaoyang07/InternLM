# InternLM2.5

## InternLM2.5-1.8B

### Introduction

InternLM2.5, the 2.5th generation InternLM, has open-sourced a 1.8 billion parameter base model and a chat model tailored for practical scenarios. For the convenience of users and researchers, we have open-sourced two versions of each scale of the model, which are:

- InternLM2.5-1.8B: Further pretrain with general domain data and domain-enhanced corpus, obtaining state-of-the-art performance in evaluation with good language capability. InternLM2.5 models are recommended for consideration in most applications.
- InternLM2.5-chat-1.8B: Further aligned on top of InternLM2.5 through supervised fine-tuning (SFT) and online RLHF. InternLM2.5-Chat exhibits better instruction following, chat experience, and function calling, which is recommended for downstream applications.

The model has the following characteristics:

- **Outstanding reasoning capability**: State-of-the-art performance on Math reasoning, surpassing models like MiniCPM-2 and Qwen2-1.5B.

- **Stronger tool use**: InternLM2.5 supports gathering information from more than 100 web pages, corresponding implementation has be released in [MindSearch](https://github.com/InternLM/MindSearch). InternLM2.5 has better tool utilization-related capabilities in instruction following, tool selection and reflection. See [examples](https://github.com/InternLM/InternLM/blob/main/agent/lagent.md).

### Model Zoo

| Model                     | Transformers(HF)                           | ModelScope(HF)                           | OpenXLab(HF)                           | OpenXLab(Origin)                            | Release Date |
| ------------------------- | ------------------------------------------ | ---------------------------------------- | -------------------------------------- | ------------------------------------------- | ------------ |
| **InternLM2.5-1.8B**      | [🤗internlm2_5-1_8b](https://huggingface.co/internlm/internlm2_5-1_8b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-1_8b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-1_8b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-1_8b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-1_8b-original) | 2024-08-05   |
| **InternLM2.5-1.8B-Chat** | [🤗internlm2_5-1_8b-chat](https://huggingface.co/internlm/internlm2_5-1_8b-chat) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-1_8b-chat](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-1_8b-chat/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-1_8b-chat) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-1_8b-chat-original) | 2024-08-05   |

- `HF` refers to the format used by HuggingFace in [transformers](https://github.com/huggingface/transformers), whereas `Origin` denotes the format adopted by the InternLM team in [InternEvo](https://github.com/InternLM/InternEvo).

### Performance Evaluation

We have evaluated InternLM2.5 on several important benchmarks using the open-source evaluation tool [OpenCompass](https://github.com/open-compass/opencompass). Some of the evaluation results are shown in the table below. You are welcome to visit the [OpenCompass Leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

#### Base Model

| Benchmark | InternLM2.5-1.8B | InternLM2-1.8B | Qwen2-1.5B |
| --------- | ---------------- | -------------- | ---------- |
| MMLU      | 53.52            | 45.99          | 57.45      |
| CMMLU     | 65.44            | 45.27          | 70.58      |
| BBH       | 41.16            | 36.03          | 35.75      |
| MATH      | 27.28            | 9.42           | 24.38      |
| HUMANEVAL | 35.98            | 30.49          | 34.15      |
| GPQA      | 24.24            | 24.24          | 31.82      |

#### Chat Model

| Benchmark         | InternLM2.5-1.8B-Chat | MiniCPM-2 | Qwen2-1.5B-Instruct |
| ----------------- | --------------------- | --------- | ------------------- |
| MMLU (5-shot)     | 50.7                  | 54.2      | 55.7                |
| CMMLU (5-shot)    | 62.2                  | 50.6      | 65.2                |
| BBH (3-shot CoT)  | **41.9**              | 41.5      | 36.5                |
| MATH (0-shot CoT) | **40.2**              | 15.5      | 21.4                |
| GPQA (0-shot)     | **27.8**              | 23.7      | 27.3                |

- We use `ppl` for the MCQ evaluation on base model.
- The evaluation results were obtained from [OpenCompass](https://github.com/open-compass/opencompass) , and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/open-compass/opencompass).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/open-compass/opencompass), so please refer to the latest evaluation results of [OpenCompass](https://github.com/open-compass/opencompass).
- \* means the result is copied from the original paper.

## InternLM2.5-7B

### Introduction

InternLM2.5, the 2.5th generation InternLM, has open-sourced a 7 billion parameter base model and a chat model tailored for practical scenarios. For the convenience of users and researchers, we have open-sourced three versions of each scale of the model, which are:

- InternLM2.5-7B: Further pretrain with general domain data and domain-enhanced corpus, obtaining state-of-the-art performance in evaluation with good language capability. InternLM2.5 models are recommended for consideration in most applications.
- InternLM2.5-chat-7B: Further aligned on top of InternLM2.5 through supervised fine-tuning (SFT) and online RLHF. InternLM2.5-Chat exhibits better instruction following, chat experience, and function calling, which is recommended for downstream applications.
- InternLM2.5-7B-Chat-1M: 1M-long-context version of InternLM2.5-7B-Chat. InternLM2.5-Chat-1M supports million-word extra-long contextual reasoning while maintaining the same performance as InternLM2.5-Chat.

The model has the following characteristics:

- **Outstanding reasoning capability**: State-of-the-art performance on Math reasoning, surpassing models like Llama3 and Gemma2-9B.
- **1M Context window**: Nearly perfect at finding needles in the haystack with 1M-long context, with leading performance on long-context tasks like LongBench. Try it with [LMDeploy](./chat/lmdeploy.md) for 1M-context inference. More details and a file chat demo are found [here](./long_context/README.md).
- **Stronger tool use**: InternLM2.5 supports gathering information from more than 100 web pages, corresponding implementation will be released in Lagent soon. InternLM2.5 has better tool utilization-related capabilities in instruction following, tool selection and reflection. See [examples](https://huggingface.co/internlm/internlm2_5-7b-chat-1m/blob/main/agent/).

### Model Zoo

| Model                      | Transformers(HF)                           | ModelScope(HF)                           | OpenXLab(HF)                           | OpenXLab(Origin)                           | Release Date |
| -------------------------- | ------------------------------------------ | ---------------------------------------- | -------------------------------------- | ------------------------------------------ | ------------ |
| **InternLM2.5-7B**         | [🤗internlm2_5-7b](https://huggingface.co/internlm/internlm2_5-7b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-7b](https://www.modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-7b-original) | 2024-07-03   |
| **InternLM2.5-Chat-7B**    | [🤗internlm2_5-7b-chat](https://huggingface.co/internlm/internlm2_5-7b-chat) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-7b-chat](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-7b-chat) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-7b-chat) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-7b-chat-original) | 2024-07-03   |
| **InternLM2.5-7B-Chat-1M** | [🤗internlm2_5-7b-chat-1m](https://huggingface.co/internlm/internlm2_5-7b-chat-1m) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-7b-chat-1m](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-7b-chat-1m) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-7b-chat-1m) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-7b-chat-1m-original) | 2024-07-03   |

- `HF` refers to the format used by HuggingFace in [transformers](https://github.com/huggingface/transformers), whereas `Origin` denotes the format adopted by the InternLM team in [InternEvo](https://github.com/InternLM/InternEvo).

### Performance Evaluation

We have evaluated InternLM2.5 on several important benchmarks using the open-source evaluation tool [OpenCompass](https://github.com/open-compass/opencompass). Some of the evaluation results are shown in the table below. You are welcome to visit the [OpenCompass Leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

#### Base Model

| Benchmark     | InternLM2.5-7B | LLaMA-3-8B | Yi-1.5-9B |
| ------------- | -------------- | ---------- | --------- |
| MMLU(5-shot)  | **71.6**       | 66.4       | 71.6      |
| CMMLU(5-shot) | **79.1**       | 51.0       | 74.1      |
| BBH(3-shot)   | 70.1           | 59.7       | 71.1      |
| MATH(4-shot)  | **34.0**       | 16.4       | 31.9      |
| GSM8K(4-shot) | **74.8**       | 54.3       | 74.5      |
| GPQA(0-shot)  | **31.3**       | 31.3       | 27.8      |

#### Chat Model

| Benchmark          | InternLM2.5-7B-Chat | Llama3-8B-Instruct | Gemma2-9B-IT | Yi-1.5-9B-Chat | GLM-4-9B-Chat | Qwen2-7B-Instruct |
| ------------------ | ------------------- | ------------------ | ------------ | -------------- | ------------- | ----------------- |
| MMLU (5-shot)      | **72.8**            | 68.4               | 70.9         | 71.0           | 71.4          | 70.8              |
| CMMLU (5-shot)     | 78.0                | 53.3               | 60.3         | 74.5           | 74.5          | 80.9              |
| BBH (3-shot CoT)   | **71.6**            | 54.4               | 68.2\*       | 69.6           | 69.6          | 65.0              |
| MATH (0-shot CoT)  | **60.1**            | 27.9               | 46.9         | 51.1           | 51.1          | 48.6              |
| GSM8K (0-shot CoT) | 86.0                | 72.9               | 88.9         | 80.1           | 85.3          | 82.9              |
| GPQA (0-shot)      | **38.4**            | 26.1               | 33.8         | 37.9           | 36.9          | 38.4              |

- We use `ppl` for the MCQ evaluation on base model.
- The evaluation results were obtained from [OpenCompass](https://github.com/open-compass/opencompass) , and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/open-compass/opencompass).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/open-compass/opencompass), so please refer to the latest evaluation results of [OpenCompass](https://github.com/open-compass/opencompass).
- \* means the result is copied from the original paper.

## InternLM2.5-20B

### Introduction

InternLM2.5, the 2.5th generation InternLM, has open-sourced a 20 billion parameter base model and a chat model tailored for practical scenarios. For the convenience of users and researchers, we have open-sourced two versions of each scale of the model, which are:

- InternLM2.5-20B: Further pretrain with general domain data and domain-enhanced corpus, obtaining state-of-the-art performance in evaluation with good language capability. InternLM2.5 models are recommended for consideration in most applications.
- InternLM2.5-chat-20B: Further aligned on top of InternLM2.5 through supervised fine-tuning (SFT) and online RLHF. InternLM2.5-Chat exhibits better instruction following, chat experience, and function calling, which is recommended for downstream applications.

The model has the following characteristics:

- **Outstanding reasoning capability**: State-of-the-art performance on Math reasoning, surpassing models like Llama3 and Gemma2-27B.

- **Stronger tool use**: InternLM2.5 supports gathering information from more than 100 web pages, corresponding implementation has be released in [MindSearch](https://github.com/InternLM/MindSearch). InternLM2.5 has better tool utilization-related capabilities in instruction following, tool selection and reflection. See [examples](https://github.com/InternLM/InternLM/blob/main/agent/lagent.md).

### Model Zoo

| Model                    | Transformers(HF)                           | ModelScope(HF)                           | OpenXLab(HF)                            | OpenXLab(Origin)                            | Release Date |
| ------------------------ | ------------------------------------------ | ---------------------------------------- | --------------------------------------- | ------------------------------------------- | ------------ |
| **InternLM2.5-20B**      | [🤗internlm2_5-20b](https://huggingface.co/internlm/internlm2_5-20b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-20b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-20b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-20b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-20b-original) | 2024-08-05   |
| **InternLM2.5-20B-Chat** | [🤗internlm2_5-20b-chat](https://huggingface.co/internlm/internlm2_5-20b-chat) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2_5-20b-chat](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2_5-20b-chat/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-20b-chat) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2_5-20b-chat-original) | 2024-08-05   |

- `HF` refers to the format used by HuggingFace in [transformers](https://github.com/huggingface/transformers), whereas `Origin` denotes the format adopted by the InternLM team in [InternEvo](https://github.com/InternLM/InternEvo).

### Performance Evaluation

We have evaluated InternLM2.5 on several important benchmarks using the open-source evaluation tool [OpenCompass](https://github.com/open-compass/opencompass). Some of the evaluation results are shown in the table below. You are welcome to visit the [OpenCompass Leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

#### Base Model

| Benchmark | InternLM2.5-20B | InternLM2-20B |
| --------- | --------------- | ------------- |
| MMLU      | 74.25           | 67.58         |
| CMMLU     | 82.22           | 68.29         |
| BBH       | 77.82           | 71.36         |
| MATH      | 48              | 32.66         |
| HUMANEVAL | 71.95           | 51.22         |
| GPQA      | 37.88           | 31.31         |

#### Chat Model

| Benchmark         | InternLM2.5-20B-Chat | Gemma2-27B-IT |
| ----------------- | -------------------- | ------------- |
| MMLU (5-shot)     | 73.5                 | 75.0          |
| CMMLU (5-shot)    | **79.7**             | 63.3          |
| BBH (3-shot CoT)  | **76.3**             | 71.5          |
| MATH (0-shot CoT) | **64.7**             | 50.1          |
| GPQA (0-shot)     | **33.3**             | 29.3          |

- We use `ppl` for the MCQ evaluation on base model.
- The evaluation results were obtained from [OpenCompass](https://github.com/open-compass/opencompass) , and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/open-compass/opencompass).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/open-compass/opencompass), so please refer to the latest evaluation results of [OpenCompass](https://github.com/open-compass/opencompass).
- \* means the result is copied from the original paper.
