# [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory)

LLaMA-Factory 是一个开源、易于使用的大语言模型微调和训练框架。

```bash
llamafactory-cli train \
    --model_name_or_path internlm/internlm2-chat-1_8b \
    --quantization_bit 4 --stage sft  --lora_target all \
    --dataset 'identity,alpaca_en_demo' --template intern2 \
    --output_dir output --do_train
```
