# HuggingFace Transformers 😊

Inference with HuggingFace Transformers represents the most common application for InternLM models. In this session, we demonstrate how to interact with InternLM3-8B-Instruct in both conversation and thinking modes.

It's worth noting that **InternLM3-8B-Instruct is the first open-source hybrid model offering both normal conversation and deep thinking capabilities in the world**. By simply modifying the system prompt, users can experience normal conversation or step-by-step reasoning processes within the same checkpoint.

## Installation

```bash
pip install transformers >= 4.48
```

## Inference in Conversation Mode

To load the InternLM3 8B Instruct model using Transformers, use the following code:

```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

model_dir = "internlm/internlm3-8b-instruct"
tokenizer = AutoTokenizer.from_pretrained(model_dir, trust_remote_code=True)
# Set `torch_dtype=torch.float16` to load model in float16, otherwise it will be loaded as float32 and might cause OOM Error.
model = AutoModelForCausalLM.from_pretrained(model_dir, trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()
# (Optional) If on low resource devices, you can load model in 4-bit or 8-bit to further save GPU memory via bitsandbytes.
  # InternLM3 8B in 4bit will cost nearly 8GB GPU memory.
  # pip install -U bitsandbytes
  # 8-bit: model = AutoModelForCausalLM.from_pretrained(model_dir, device_map="auto", trust_remote_code=True, load_in_8bit=True)
  # 4-bit: model = AutoModelForCausalLM.from_pretrained(model_dir, device_map="auto", trust_remote_code=True, load_in_4bit=True)
model = model.eval()

system_prompt = """You are an AI assistant whose name is InternLM (书生·浦语).
- InternLM (书生·浦语) is a conversational language model that is developed by Shanghai AI Laboratory (上海人工智能实验室). It is designed to be helpful, honest, and harmless.
- InternLM (书生·浦语) can understand and communicate fluently in the language chosen by the user such as English and 中文."""
messages = [
    {"role": "system", "content": system_prompt},
    {"role": "user", "content": "Please tell me five scenic spots in Shanghai"},
 ]
tokenized_chat = tokenizer.apply_chat_template(messages, tokenize=True, add_generation_prompt=True, return_tensors="pt").to("cuda")

generated_ids = model.generate(tokenized_chat, max_new_tokens=1024, temperature=1, repetition_penalty=1.005, top_k=40, top_p=0.8)

generated_ids = [
    output_ids[len(input_ids):] for input_ids, output_ids in zip(tokenized_chat, generated_ids)
]
prompt = tokenizer.batch_decode(tokenized_chat)[0]
print(prompt)
response = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)[0]
print(response)
```

## Inference in Thinking Mode

```python
thinking_system_prompt = """You are an expert mathematician with extensive experience in mathematical competitions. You approach problems through systematic thinking and rigorous reasoning. When solving problems, follow these thought processes:
## Deep Understanding
Take time to fully comprehend the problem before attempting a solution. Consider:
- What is the real question being asked?
- What are the given conditions and what do they tell us?
- Are there any special restrictions or assumptions?
- Which information is crucial and which is supplementary?
## Multi-angle Analysis
Before solving, conduct thorough analysis:
- What mathematical concepts and properties are involved?
- Can you recall similar classic problems or solution methods?
- Would diagrams or tables help visualize the problem?
- Are there special cases that need separate consideration?
## Systematic Thinking
Plan your solution path:
- Propose multiple possible approaches
- Analyze the feasibility and merits of each method
- Choose the most appropriate method and explain why
- Break complex problems into smaller, manageable steps
## Rigorous Proof
During the solution process:
- Provide solid justification for each step
- Include detailed proofs for key conclusions
- Pay attention to logical connections
- Be vigilant about potential oversights
## Repeated Verification
After completing your solution:
- Verify your results satisfy all conditions
- Check for overlooked special cases
- Consider if the solution can be optimized or simplified
- Review your reasoning process
Remember:
1. Take time to think thoroughly rather than rushing to an answer
2. Rigorously prove each key conclusion
3. Keep an open mind and try different approaches
4. Summarize valuable problem-solving methods
5. Maintain healthy skepticism and verify multiple times
Your response should reflect deep mathematical understanding and precise logical thinking, making your solution path and reasoning clear to others.
When you're ready, present your complete solution with:
- Clear problem understanding
- Detailed solution process
- Key insights
- Thorough verification
Focus on clear, logical progression of ideas and thorough explanation of your mathematical reasoning. Provide answers in the same language as the user asking the question, repeat the final answer using a '\\boxed{}' without any units, you have [[8192]] tokens to complete the answer.
"""

import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

model_dir = "internlm/internlm3-8b-instruct"
tokenizer = AutoTokenizer.from_pretrained(model_dir, trust_remote_code=True)
# Set `torch_dtype=torch.float16` to load model in float16, otherwise it will be loaded as float32 and might cause OOM Error.
model = AutoModelForCausalLM.from_pretrained(model_dir, trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()
# (Optional) If on low resource devices, you can load model in 4-bit or 8-bit to further save GPU memory via bitsandbytes.
  # InternLM3 8B in 4bit will cost nearly 8GB GPU memory.
  # pip install -U bitsandbytes
  # 8-bit: model = AutoModelForCausalLM.from_pretrained(model_dir, device_map="auto", trust_remote_code=True, load_in_8bit=True)
  # 4-bit: model = AutoModelForCausalLM.from_pretrained(model_dir, device_map="auto", trust_remote_code=True, load_in_4bit=True)
model = model.eval()

messages = [
    {"role": "system", "content": thinking_system_prompt},
    {"role": "user", "content": "Given the function\(f(x)=\mathrm{e}^{x}-ax - a^{3}\),\n(1) When \(a = 1\), find the equation of the tangent line to the curve \(y = f(x)\) at the point \((1,f(1))\).\n(2) If \(f(x)\) has a local minimum and the minimum value is less than \(0\), determine the range of values for \(a\)."},
 ]
tokenized_chat = tokenizer.apply_chat_template(messages, tokenize=True, add_generation_prompt=True, return_tensors="pt").to("cuda")

generated_ids = model.generate(tokenized_chat, max_new_tokens=8192)

generated_ids = [
    output_ids[len(input_ids):] for input_ids, output_ids in zip(tokenized_chat, generated_ids)
]
prompt = tokenizer.batch_decode(tokenized_chat)[0]
print(prompt)
response = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)[0]
print(response)
```
