# InternLM2

## InternLM2-1.8B

### Introduction

InternLM2-1.8B is the 1.8 billion parameter version of the second generation InternLM series. In order to facilitate user use and research, InternLM2-1.8B has three versions of open-source models. They are:

- InternLM2-1.8B: Foundation models with high quality and high adaptation flexibility, which serve as a good starting point for downstream deep adaptations.
- InternLM2-Chat-1.8B-SFT: Chat model after supervised fine-tuning (SFT) on InternLM2-1.8B.
- InternLM2-Chat-1.8B: Further aligned on top of InternLM2-Chat-1.8B-SFT through online RLHF. InternLM2-Chat-1.8B exhibits better instruction following, chat experience, and function calling, which is recommended for downstream applications.

The base model of InternLM2 has the following technical features:

- Effective support for ultra-long contexts of up to 200,000 characters: The model nearly perfectly achieves "finding a needle in a haystack" in long inputs of 200,000 characters. It also leads among open-source models in performance on long-text tasks such as LongBench and L-Eval.
- Comprehensive performance enhancement: Compared to the previous generation model, it shows significant improvements in various capabilities, including reasoning, mathematics, and coding.

### Model Zoo

| Model                       | Transformers(HF)                          | ModelScope(HF)                           | OpenXLab(HF)                           | OpenXLab(Origin)                           | Release Date |
| --------------------------- | ----------------------------------------- | ---------------------------------------- | -------------------------------------- | ------------------------------------------ | ------------ |
| **InternLM2-1.8B**          | [🤗internlm2-1.8b](https://huggingface.co/internlm/internlm2-1_8b) | [<img src="./assets/modelscope_logo.png" width="20px" /> internlm2-1.8b](https://www.modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-1_8b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-base-1.8b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-base-1.8b-original) | 2024-01-31   |
| **InternLM2-Chat-1.8B-SFT** | [🤗internlm2-chat-1.8b-sft](https://huggingface.co/internlm/internlm2-chat-1_8b-sft) | [<img src="./assets/modelscope_logo.png" width="20px" /> internlm2-chat-1.8b-sft](https://www.modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-chat-1_8b-sft/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-1.8b-sft) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-1.8b-sft-original) | 2024-01-31   |
| **InternLM2-Chat-1.8B**     | [🤗internlm2-chat-1.8b](https://huggingface.co/internlm/internlm2-chat-1_8b) | [<img src="./assets/modelscope_logo.png" width="20px" /> internlm2-chat-1.8b](https://www.modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-chat-1_8b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-1.8b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-1.8b-original) | 2024-02-19   |

### Performance Evaluation

We have evaluated InternLM2 on several important benchmarks using the open-source evaluation tool [OpenCompass](https://github.com/open-compass/opencompass). Some of the evaluation results are shown in the table below. You are welcome to visit the [OpenCompass Leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

| Dataset\\Models | InternLM2-1.8B | InternLM2-Chat-1.8B-SFT | InternLM2-Chat-1.8B | InternLM2-7B | InternLM2-Chat-7B |
| :-------------: | :------------: | :---------------------: | :-----------------: | :----------: | :---------------: |
|      MMLU       |      46.9      |          47.1           |        44.1         |     65.8     |       63.7        |
|     AGIEval     |      33.4      |          38.8           |        34.6         |     49.9     |       47.2        |
|       BBH       |      37.5      |          35.2           |        34.3         |     65.0     |       61.2        |
|      GSM8K      |      31.2      |          39.7           |        34.3         |     70.8     |       70.7        |
|      MATH       |      5.6       |          11.8           |        10.7         |     20.2     |       23.0        |
|    HumanEval    |      25.0      |          32.9           |        29.3         |     43.3     |       59.8        |
| MBPP(Sanitized) |      22.2      |          23.2           |        27.0         |     51.8     |       51.4        |

- The evaluation results were obtained from [OpenCompass](https://github.com/open-compass/opencompass) , and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/open-compass/opencompass).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/open-compass/opencompass), so please refer to the latest evaluation results of [OpenCompass](https://github.com/open-compass/opencompass).

## InternLM2-7B

### Introduction

The second generation of the InternLM model, InternLM2, includes models at two scales: 7B and 20B. For the convenience of users and researchers, we have open-sourced four versions of each scale of the model, which are:

- internlm2-base-7b: Foundation models with high quality and high adaptation flexibility, which serve as a good starting point for downstream deep adaptations.
- internlm2-7b (**recommended**): Further pretrain with general domain data and domain-enhanced corpus, obtaining state-of-the-art performance in evaluation with good language capability. InternLM2 models are recommended for consideration in most applications.
- internlm2-chat-7b-sft: Intermediate version of InternLM2-Chat that only undergoes supervised fine-tuning (SFT), based on the InternLM2-Base model. We release them to benefit research on alignment.
- internlm2-chat-7b (**recommended**): Further aligned on top of InternLM2-Chat-SFT through online RLHF. InternLM2-Chat exhibits better instruction following, chat experience, and function calling, which is recommended for downstream applications.

The base model of InternLM2 has the following technical features:

- Effective support for ultra-long contexts of up to 200,000 characters: The model nearly perfectly achieves "finding a needle in a haystack" in long inputs of 200,000 characters. It also leads among open-source models in performance on long-text tasks such as LongBench and L-Eval.
- Comprehensive performance enhancement: Compared to the previous generation model, it shows significant improvements in various capabilities, including reasoning, mathematics, and coding.

### Model Zoo

| Model                     | Transformers(HF)                           | ModelScope(HF)                           | OpenXLab(HF)                           | OpenXLab(Origin)                            | Release Date |
| ------------------------- | ------------------------------------------ | ---------------------------------------- | -------------------------------------- | ------------------------------------------- | ------------ |
| **InternLM2-Base-7B**     | [🤗internlm2-base-7b](https://huggingface.co/internlm/internlm2-base-7b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-base-7b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-base-7b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-base-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-base-7b-original) | 2024-01-17   |
| **InternLM2-7B**          | [🤗internlm2-7b](https://huggingface.co/internlm/internlm2-7b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-7b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-7b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-7b-original) | 2024-01-17   |
| **InternLM2-Chat-7B-SFT** | [🤗internlm2-chat-7b-sft](https://huggingface.co/internlm/internlm2-chat-7b-sft) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-chat-7b-sft](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-chat-7b-sft/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-7b-sft) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-7b-sft-original) | 2024-01-17   |
| **InternLM2-Chat-7B**     | [🤗internlm2-chat-7b](https://huggingface.co/internlm/internlm2-chat-7b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-chat-7b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-chat-7b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-7b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-7b-original) | 2024-01-17   |

- `HF` refers to the format used by HuggingFace in [transformers](https://github.com/huggingface/transformers), whereas `Origin` denotes the format adopted by the InternLM team in [InternEvo](https://github.com/InternLM/InternEvo).

### Performance Evaluation

We have evaluated InternLM2 on several important benchmarks using the open-source evaluation tool [OpenCompass](https://github.com/open-compass/opencompass). Some of the evaluation results are shown in the table below. You are welcome to visit the [OpenCompass Leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

| Dataset\\Models | InternLM2-7B | InternLM2-Chat-7B | InternLM2-20B | InternLM2-Chat-20B | ChatGPT | GPT-4 |
| --------------- | ------------ | ----------------- | ------------- | ------------------ | ------- | ----- |
| MMLU            | 65.8         | 63.7              | 67.7          | 66.5               | 69.1    | 83.0  |
| AGIEval         | 49.9         | 47.2              | 53.0          | 50.3               | 39.9    | 55.1  |
| BBH             | 65.0         | 61.2              | 72.1          | 68.3               | 70.1    | 86.7  |
| GSM8K           | 70.8         | 70.7              | 76.1          | 79.6               | 78.2    | 91.4  |
| MATH            | 20.2         | 23.0              | 25.5          | 31.9               | 28.0    | 45.8  |
| HumanEval       | 43.3         | 59.8              | 48.8          | 67.1               | 73.2    | 74.4  |
| MBPP(Sanitized) | 51.8         | 51.4              | 63.0          | 65.8               | 78.9    | 79.0  |

- The evaluation results were obtained from [OpenCompass](https://github.com/open-compass/opencompass) , and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/open-compass/opencompass).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/open-compass/opencompass), so please refer to the latest evaluation results of [OpenCompass](https://github.com/open-compass/opencompass).

## InternLM2-20B

### Introduction

The second generation of the InternLM model, InternLM2, includes models at two scales: 7B and 20B. For the convenience of users and researchers, we have open-sourced four versions of each scale of the model, which are:

- internlm2-base-20b: Foundation models with high quality and high adaptation flexibility, which serve as a good starting point for downstream deep adaptations.
- internlm2-20b (**recommended**): Further pretrain with general domain data and domain-enhanced corpus, obtaining state-of-the-art performance in evaluation with good language capability. InternLM2 models are recommended for consideration in most applications.
- internlm2-chat-20b-sft: Intermediate version of InternLM2-Chat that only undergoes supervised fine-tuning (SFT), based on the InternLM2-Base model. We release them to benefit research on alignment.
- internlm2-chat-20b (**recommended**): Further aligned on top of InternLM2-Chat-SFT through online RLHF. InternLM2-Chat exhibits better instruction following, chat experience, and function calling, which is recommended for downstream applications.

The base model of InternLM2 has the following technical features:

- Effective support for ultra-long contexts of up to 200,000 characters: The model nearly perfectly achieves "finding a needle in a haystack" in long inputs of 200,000 characters. It also leads among open-source models in performance on long-text tasks such as LongBench and L-Eval.
- Comprehensive performance enhancement: Compared to the previous generation model, it shows significant improvements in various capabilities, including reasoning, mathematics, and coding.

### Model Zoo

| Model                      | Transformers(HF)                           | ModelScope(HF)                           | OpenXLab(HF)                           | OpenXLab(Origin)                           | Release Date |
| -------------------------- | ------------------------------------------ | ---------------------------------------- | -------------------------------------- | ------------------------------------------ | ------------ |
| **InternLM2-Base-20B**     | [🤗internlm2-base-20b](https://huggingface.co/internlm/internlm2-base-20b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-base-20b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-base-20b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-base-20b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-base-20b-original) | 2024-01-17   |
| **InternLM2-20B**          | [🤗internlm2-20b](https://huggingface.co/internlm/internlm2-20b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-20b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-20b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-20b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-20b-original) | 2024-01-17   |
| **InternLM2-Chat-20B-SFT** | [🤗internlm2-chat-20b-sft](https://huggingface.co/internlm/internlm2-chat-20b-sft) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-chat-20b-sft](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-chat-20b-sft/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-20b-sft) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-20b-sft-original) | 2024-01-17   |
| **InternLM2-Chat-20B**     | [🤗internlm2-chat-20b](https://huggingface.co/internlm/internlm2-chat-20b) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-chat-20b](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-chat-20b/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-20b) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-chat-20b-original) | 2024-01-17   |

- `HF` refers to the format used by HuggingFace in [transformers](https://github.com/huggingface/transformers), whereas `Origin` denotes the format adopted by the InternLM team in [InternEvo](https://github.com/InternLM/InternEvo).

### Performance Evaluation

We have evaluated InternLM2 on several important benchmarks using the open-source evaluation tool [OpenCompass](https://github.com/open-compass/opencompass). Some of the evaluation results are shown in the table below. You are welcome to visit the [OpenCompass Leaderboard](https://opencompass.org.cn/rank) for more evaluation results.

| Dataset\\Models | InternLM2-7B | InternLM2-Chat-7B | InternLM2-20B | InternLM2-Chat-20B | ChatGPT | GPT-4 |
| --------------- | ------------ | ----------------- | ------------- | ------------------ | ------- | ----- |
| MMLU            | 65.8         | 63.7              | 67.7          | 66.5               | 69.1    | 83.0  |
| AGIEval         | 49.9         | 47.2              | 53.0          | 50.3               | 39.9    | 55.1  |
| BBH             | 65.0         | 61.2              | 72.1          | 68.3               | 70.1    | 86.7  |
| GSM8K           | 70.8         | 70.7              | 76.1          | 79.6               | 78.2    | 91.4  |
| MATH            | 20.2         | 23.0              | 25.5          | 31.9               | 28.0    | 45.8  |
| HumanEval       | 43.3         | 59.8              | 48.8          | 67.1               | 73.2    | 74.4  |
| MBPP(Sanitized) | 51.8         | 51.4              | 63.0          | 65.8               | 78.9    | 79.0  |

- The evaluation results were obtained from [OpenCompass](https://github.com/open-compass/opencompass) , and evaluation configuration can be found in the configuration files provided by [OpenCompass](https://github.com/open-compass/opencompass).
- The evaluation data may have numerical differences due to the version iteration of [OpenCompass](https://github.com/open-compass/opencompass), so please refer to the latest evaluation results of [OpenCompass](https://github.com/open-compass/opencompass).

## InternLM2-Reward

### Introduction

**InternLM2-Reward** is a series of reward models trained on the foundation of InternLM2-Chat-SFT. These model have been trained using over 2.4 million preference samples, both human-annotated and AI-synthesized, achieving outstanding performance while ensuring a balance between helpfulness and harmlessness.

#### Key Features:

- **Variety of Sizes Available**: Our open-sourced reward models are available in sizes of **1.8B, 7B, and 20B**, each demonstrating exceptional performance across various metrics. We aim for these different-sized models to facilitate research on the scaling laws of reward models, providing valuable insights to the community.
- **Comprehensive Coverage of Preference**: Trained with **2.4 million** preference pairs derived from both human annotations and AI synthesis, covering diverse areas such as dialogue, writing, poetry, summarization, coding, mathematics, etc. It also maintains a balance between helpful and harmless.
- **Multilingual Support**: InternLM2-Reward was trained on high-quality **English and Chinese** preference data, delivering robust performance in both languages.

This model was applied to the RLHF training process of InternLM2-Chat. The reward model training techniques from the [InternLM2 Technical Report](https://arxiv.org/abs/2403.17297) have been open-sourced in XTuner, try it out [here](https://github.com/InternLM/xtuner)!

### Download links

| Model                     | RewardBench Score | Transformers(HF)                                   | ModelScope(HF)                                    | OpenXLab(HF)                                    | Release Date |
| ------------------------- | ----------------- | -------------------------------------------------- | ------------------------------------------------- | ----------------------------------------------- | ------------ |
| **InternLM2-1.8B-Reward** | 80.6              | [🤗internlm2-1_8b-reward](https://huggingface.co/internlm/internlm2-1_8b-reward) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-1_8b-reward](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-1_8b-reward/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-1_8b-reward) | 2024-07-19   |
| **InternLM2-7B-Reward**   | 86.6              | [🤗internlm2-7b-reward](https://huggingface.co/internlm/internlm2-7b-reward) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-7b-reward](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-7b-reward/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-7b-reward) | 2024-07-19   |
| **InternLM2-20B-Reward**  | 89.5              | [🤗internlm2-20b-reward](https://huggingface.co/internlm/internlm2-20b-reward) | [<img src="../assets/modelscope_logo.png" width="20px" /> internlm2-20b-reward](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-20b-reward/summary) | [![Open in OpenXLab](https://cdn-static.openxlab.org.cn/header/openxlab_models.svg)](https://openxlab.org.cn/models/detail/OpenLMLab/internlm2-20b-reward) | 2024-07-19   |

### Performance Evaluation on RewardBench

| Models                | Score | Chat | Chat Hard | Safety | Reasoning |
| --------------------- | ----- | ---- | --------- | ------ | --------- |
| InternLM2-20B-Reward  | 89.5  | 98.6 | 74.1      | 89.4   | 95.7      |
| InternLM2-7B-Reward   | 86.6  | 98.6 | 66.7      | 88.3   | 92.8      |
| InternLM2-1.8B-Reward | 80.6  | 95.0 | 58.1      | 81.8   | 87.4      |

- The evaluation is conducted on the [RewardBench](https://github.com/allenai/reward-bench) dataset.
- For a fair comparison, conditional system prompts proposed in our technical report were not included during testing.

### Demo Code

#### Basic Usage

We provide some user-friendly APIs for you to use the model. Here is an example of how to use the model to get the reward score of a chat, compare two chats, or rank multiple chats.

```python
import torch
from transformers import AutoModel, AutoTokenizer

model = AutoModel.from_pretrained(
    "internlm/internlm2-20b-reward",
    device_map="cuda",
    torch_dtype=torch.float16,
    trust_remote_code=True,
)
tokenizer = AutoTokenizer.from_pretrained("internlm/internlm2-20b-reward", trust_remote_code=True)

chat_1 = [
    {"role": "user", "content": "Hello! What's your name?"},
    {"role": "assistant", "content": "My name is InternLM2! A helpful AI assistant. What can I do for you?"}
]
chat_2 = [
    {"role": "user", "content": "Hello! What's your name?"},
    {"role": "assistant", "content": "I have no idea."}
]


# get reward score for a single chat
score1 = model.get_score(tokenizer, chat_1)
score2 = model.get_score(tokenizer, chat_2)
print("score1: ", score1)
print("score2: ", score2)
# >>> score1:  0.767578125
# >>> score2:  -2.22265625


# batch inference, get multiple scores at once
scores = model.get_scores(tokenizer, [chat_1, chat_2])
print("scores: ", scores)
# >>> scores:  [0.767578125, -2.22265625]


# compare whether chat_1 is better than chat_2
compare_res = model.compare(tokenizer, chat_1, chat_2)
print("compare_res: ", compare_res)
# >>> compare_res:  True


# rank multiple chats, it will return the ranking index of each chat
# the chat with the highest score will have ranking index as 0
rank_res = model.rank(tokenizer, [chat_1, chat_2])
print("rank_res: ", rank_res)  # lower index means higher score
# >>> rank_res:  [0, 1]
```

#### Best of N Sampling

Here is an example of how to use the reward model to perform best of N sampling.
The code below demonstrates how to select the best response from the candidates generated by the language model.

```python
import torch
from transformers import AutoModel, AutoTokenizer

# prepare the llm model and tokenizer
llm = AutoModel.from_pretrained(
    "internlm/internlm2-chat-7b",
    device_map="cuda",
    torch_dtype=torch.float16,
    trust_remote_code=True,
)
llm_tokenizer = AutoTokenizer.from_pretrained("internlm/internlm2-chat-7b", trust_remote_code=True)

# prepare the reward model and tokenizer
reward = AutoModel.from_pretrained(
    "internlm/internlm2-20b-reward",
    device_map="cuda",
    torch_dtype=torch.float16,
    trust_remote_code=True,
)
reward_tokenizer = AutoTokenizer.from_pretrained("internlm/internlm2-20b-reward", trust_remote_code=True)

# prepare the chat prompt
prompt = "Write an article about the artificial intelligence revolution."
messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": prompt}
]
text = llm_tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)
model_inputs = llm_tokenizer([text], return_tensors="pt").to("cuda")

# generate best of N candidates
num_candidates = 10  # N=10
candidates = []

outputs = llm.generate(
    **model_inputs,
    max_new_tokens=512,
    num_return_sequences=num_candidates,
    pad_token_id=llm_tokenizer.eos_token_id,
    do_sample=True,
    top_k=50,
    top_p=0.95,
    temperature=0.8,
)
outputs = outputs[:, model_inputs["input_ids"].shape[1]:]
for i in range(num_candidates):
    candidate = llm_tokenizer.decode(outputs[i], skip_special_tokens=True)
    candidates.append(messages + [{"role": "assistant", "content": candidate}])

rank_indices = reward.rank(reward_tokenizer, candidates)
sorted_candidates = sorted(zip(rank_indices, candidates), key=lambda x: x[0])

## print the ranked candidates
# for i, (rank_index, candidate) in enumerate(sorted_candidates):
#     print(f"------------Rank {i}------------: \n{candidate[-1]['content']}")

# print the best response
best_response = sorted_candidates[0][1][-1]['content']
print(best_response)
```
