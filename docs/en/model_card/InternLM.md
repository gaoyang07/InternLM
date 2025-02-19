# InternLM

## InternLM-20B

### Introduction

InternLM-20B was pre-trained on over **2.3T** Tokens containing high-quality English, Chinese, and code data. Additionally, the Chat version has undergone SFT and RLHF training, enabling it to better and more securely meet users' needs.

In terms of model structure, InternLM-20B opted for a deeper architecture, with a depth set at 60 layers. This surpasses the conventional 7B and 13B models that utilize 32 or 40 layers. When parameters are limited, increasing the number of layers can enhance the model's overall capability. Furthermore, compared to InternLM-7B, the pre-training data used for InternLM-20B underwent higher quality cleansing and was supplemented with data rich in knowledge and designed for reinforcing understanding and reasoning capabilities. As a result, it exhibits significant improvements in understanding, reasoning, mathematical, and programming abilities—all of which test the technical proficiency of language models. Overall, InternLM-20B features the following characteristics:

- Outstanding overall performance
- Strong utility invocation capability
- Supports a 16k context length (Through inference extrapolation)
- Better value alignment.

### Model Zoo

| Model                 | Transformers(HF)                           | ModelScope(HF)                            | OpenXLab(HF)                            | OpenXLab(Original)                            | Release Date |
| --------------------- | ------------------------------------------ | ----------------------------------------- | --------------------------------------- | --------------------------------------------- | ------------ |
| **InternLM Chat 20B** | [🤗internlm/internlm-chat-20b](https://huggingface.co/internlm/internlm-20b-chat) | [<img src="../assets/modelscope_logo.png" width="20px" /> Shanghai_AI_Laboratory/internlm-chat-20b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm-20b-chat/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-chat-20b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-chat-20b-original) | 2023-12-12   |
| **InternLM 20B**      | [🤗internlm/internlm-20b](https://huggingface.co/internlm/internlm-20b) | [<img src="../assets/modelscope_logo.png" width="20px" /> Shanghai_AI_Laboratory/internlm-20b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm-20b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-20b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-20b-original) | 2023-09-20   |

### Performance Evaluation

On the 5 capability dimensions proposed by OpenCompass, InternLM-20B has achieved excellent results (the bolded scores represent the best performances within the 13B-33B parameter range).

| Capability    | Llama-13B | Llama2-13B | Baichuan2-13B | InternLM-20B | Llama-33B | Llama-65B | Llama2-70B |
| ------------- | --------- | ---------- | ------------- | ------------ | --------- | --------- | ---------- |
| Language      | 42.5      | 47         | 47.5          | **55**       | 44.6      | 47.1      | 51.6       |
| Knowledge     | 58.2      | 58.3       | 48.9          | 60.1         | **64**    | 66        | 67.7       |
| Understanding | 45.5      | 50.9       | 58.1          | **67.3**     | 50.6      | 54.2      | 60.8       |
| Reasoning     | 42.7      | 43.6       | 44.2          | **54.9**     | 46.4      | 49.8      | 55         |
| Examination   | 37.3      | 45.2       | 51.8          | **62.5**     | 47.4      | 49.7      | 57.3       |
| Overall       | 43.8      | 47.3       | 49.4          | **59.2**     | 48.9      | 51.9      | 57.4       |

The table below compares the performance of mainstream open-source models on some influential and typical datasets.

|               | Benchmarks       | Llama-13B | Llama2-13B | Baichuan2-13B | InternLM-20B | Llama-33B | Llama-65B | Llama2-70B |
| ------------- | ---------------- | --------- | ---------- | ------------- | ------------ | --------- | --------- | ---------- |
| Examination   | MMLU             | 47.73     | 54.99      | 59.55         | **62.05**    | 58.73     | 63.71     | 69.75      |
|               | C-Eval (val)     | 31.83     | 41.4       | **59.01**     | 58.8         | 37.47     | 40.36     | 50.13      |
|               | AGI-Eval         | 22.03     | 30.93      | 37.37         | **44.58**    | 33.53     | 33.92     | 40.02      |
| Knowledge     | BoolQ            | 78.75     | 82.42      | 67            | **87.46**    | 84.43     | 86.61     | 87.74      |
|               | TriviaQA         | 52.47     | 59.36      | 46.61         | 57.26        | **66.24** | 69.79     | 70.71      |
|               | NaturalQuestions | 20.17     | 24.85      | 16.32         | 25.15        | **30.89** | 33.41     | 34.16      |
| Understanding | CMRC             | 9.26      | 31.59      | 29.85         | **68.78**    | 14.17     | 34.73     | 43.74      |
|               | CSL              | 55        | 58.75      | 63.12         | **65.62**    | 57.5      | 59.38     | 60         |
|               | RACE (middle)    | 53.41     | 63.02      | 68.94         | **86.35**    | 64.55     | 72.35     | 81.55      |
|               | RACE (high)      | 47.63     | 58.86      | 67.18         | **83.28**    | 62.61     | 68.01     | 79.93      |
|               | XSum             | 20.37     | 23.37      | 25.23         | **35.54**    | 20.55     | 19.91     | 25.38      |
| Reasoning     | WinoGrande       | 64.64     | 64.01      | 67.32         | **69.38**    | 66.85     | 69.38     | 69.77      |
|               | BBH              | 37.93     | 45.62      | 48.98         | **52.51**    | 49.98     | 58.38     | 64.91      |
|               | GSM8K            | 20.32     | 29.57      | **52.62**     | **52.62**    | 42.3      | 54.44     | 63.31      |
|               | PIQA             | 79.71     | 79.76      | 78.07         | 80.25        | **81.34** | 82.15     | 82.54      |
| Programming   | HumanEval        | 14.02     | 18.9       | 17.07         | **25.61**    | 17.68     | 18.9      | 26.22      |
|               | MBPP             | 20.6      | 26.8       | 30.8          | **35.6**     | 28.4      | 33.6      | 39.6       |

Overall, InternLM-20B comprehensively outperforms open-source models in the 13B parameter range in terms of overall capabilities, and on inference evaluation sets, it approaches or even surpasses the performance of Llama-65B.

- The evaluation results were obtained from [OpenCompass 20230920](https://github.com/internLM/OpenCompass/).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/internLM/OpenCompass/), so please refer to the latest evaluation results of [OpenCompass](https://github.com/internLM/OpenCompass/).

## InternLM-7B

### Introduction

InternLM-7B contains a 7 billion parameter base model and a chat model tailored for practical scenarios. The model has the following characteristics:

- It leverages trillions of high-quality tokens for training to establish a powerful knowledge base.
- It supports an 8k context window length, enabling longer input sequences and stronger reasoning capabilities.
- It provides a versatile toolset for users to flexibly build their own workflows.

### Model Zoo

| Model                | Transformers(HF)                            | ModelScope(HF)                            | OpenXLab(HF)                            | OpenXLab(Original)                            | Release Date |
| -------------------- | ------------------------------------------- | ----------------------------------------- | --------------------------------------- | --------------------------------------------- | ------------ |
| **InternLM Chat 7B** | [🤗internlm/internlm-chat-7b](https://huggingface.co/internlm/internlm-chat-7b) | [<img src="../assets/modelscope_logo.png" width="20px" /> Shanghai_AI_Laboratory/internlm-chat-7b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm-chat-7b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-chat-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-chat-7b-original) | 2023-12-12   |
| **InternLM 7B**      | [🤗internlm/internlm-7b](https://huggingface.co/internlm/internlm-7b) | [<img src="../assets/modelscope_logo.png" width="20px" /> Shanghai_AI_Laboratory/internlm-7b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm-7b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/InternLM-7b-original) | 2023-07-06   |

### Performance Evaluation

We conducted a comprehensive evaluation of InternLM using the open-source evaluation tool [OpenCompass](https://github.com/internLM/OpenCompass/). The evaluation covered five dimensions of capabilities: disciplinary competence, language competence, knowledge competence, inference competence, and comprehension competence. Here are some of the evaluation results, and you can visit the [OpenCompass leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

| Datasets\\Models | **InternLM-Chat-7B** | **InternLM-7B** | LLaMA-7B | Baichuan-7B | ChatGLM2-6B | Alpaca-7B | Vicuna-7B |
| ---------------- | -------------------- | --------------- | -------- | ----------- | ----------- | --------- | --------- |
| C-Eval(Val)      | 52.0                 | 53.4            | 24.2     | 42.7        | 50.9        | 28.9      | 31.2      |
| MMLU             | 52.6                 | 51.0            | 35.2\*   | 41.5        | 46.0        | 39.7      | 47.3      |
| AGIEval          | 46.4                 | 37.6            | 20.8     | 24.6        | 39.0        | 24.1      | 26.4      |
| CommonSenseQA    | 80.8                 | 59.5            | 65.0     | 58.8        | 60.0        | 68.7      | 66.7      |
| BUSTM            | 80.6                 | 50.6            | 48.5     | 51.3        | 55.0        | 48.8      | 62.5      |
| CLUEWSC          | 81.8                 | 59.1            | 50.3     | 52.8        | 59.8        | 50.3      | 52.2      |
| MATH             | 5.0                  | 7.1             | 2.8      | 3.0         | 6.6         | 2.2       | 2.8       |
| GSM8K            | 36.2                 | 31.2            | 10.1     | 9.7         | 29.2        | 6.0       | 15.3      |
| HumanEval        | 15.9                 | 10.4            | 14.0     | 9.2         | 9.2         | 9.2       | 11.0      |
| RACE(High)       | 80.3                 | 57.4            | 46.9\*   | 28.1        | 66.3        | 40.7      | 54.0      |

- The evaluation results were obtained from [OpenCompass 20230706](https://github.com/internLM/OpenCompass/) (some data marked with \*, which means come from the original papers), and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/internLM/OpenCompass/).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/internLM/OpenCompass/), so please refer to the latest evaluation results of [OpenCompass](https://github.com/internLM/OpenCompass/).
