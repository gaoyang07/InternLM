# [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory)

LLaMA-Factory is an open-source, easy-to-use fine-tuning and training framework for LLMs

```bash
llamafactory-cli train \
    --model_name_or_path internlm/internlm2-chat-1_8b \
    --quantization_bit 4 --stage sft  --lora_target all \
    --dataset 'identity,alpaca_en_demo' --template intern2 \
    --output_dir output --do_train
```
