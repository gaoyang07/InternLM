# 使用 XTuner 微调 InternLM

XTuner 是一个高效的大语言模型微调工具箱。

## 安装

```bash
pip install xtuner
```

## 基本微调

### 准备配置文件

```bash
xtuner list-cfg -p internlm3
xtuner copy-cfg internlm3_8b_qlora_alpaca_e3 ./
```

### 开始训练

```bash
xtuner train internlm3_8b_qlora_alpaca_e3_copy.py --deepspeed deepspeed_zero2
```

### 模型转换

```bash
# 将 PTH 模型转换为 HuggingFace 模型
xtuner convert pth_to_hf internlm3_8b_qlora_alpaca_e3_copy.py ./work_dirs/internlm3_8b_qlora_alpaca_e3_copy/epoch_3.pth ./hf_model

# 将 HuggingFace 模型合并到原模型
xtuner convert merge InternLM/internlm3-8b-instruct ./hf_model ./merged_model
```

## 数据格式

XTuner 支持多种数据格式，包括：

### Alpaca 格式

```json
[
  {
    "instruction": "给出三个保持健康的建议。",
    "input": "",
    "output": "以下是保持健康的三个建议：\n1. 保持均衡的饮食\n2. 定期进行体育锻炼\n3. 保证充足的睡眠"
  }
]
```

### 对话格式

```json
[
  {
    "conversation": [
      {
        "role": "user",
        "content": "你好"
      },
      {
        "role": "assistant",
        "content": "你好！我是InternLM，很高兴为您服务。"
      }
    ]
  }
]
```

## 高级配置

### LoRA 配置

```python
# LoRA 配置
lora_config = dict(
    r=64,
    lora_alpha=16,
    lora_dropout=0.1,
    bias='none',
    task_type='CAUSAL_LM'
)
```

### 训练参数

```python
# 训练配置
train_cfg = dict(
    max_epochs=3,
    dataloader=dict(
        batch_size=1,
        num_workers=0,
    ),
    optim_wrapper=dict(
        optimizer=dict(
            type='AdamW',
            lr=2e-4,
            weight_decay=0.01
        )
    )
)
```

## 评估和测试

```bash
# 使用微调后的模型进行对话
xtuner chat ./merged_model --prompt-template internlm3_chat
```
