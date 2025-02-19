
:github_url: https://github.com/InternLM/InternLM

InternLM documentation
=========================================

我们发布了 InternLM3，开源了一个80亿参数的指令模型 InternLM3-8B-Instruct，旨在用于通用目的和高级推理。该模型具有以下特点：

- **以更低的成本实现更高的性能**：
  在推理和知识密集型任务上的最先进性能超过了 Llama3.1-8B 和 Qwen2.5-7B 等模型。值得注意的是，InternLM3 仅使用 4 万亿个高质量 token 进行训练，与同等规模的其他大语言模型相比，训练成本节省了 75% 以上。
- **深度思考能力**：
  InternLM3 支持深度思考模式，通过长思维链解决复杂的推理任务，同时也支持流畅的用户交互的正常响应模式。


.. toctree::
   :glob:
   :maxdepth: 1
   :caption: ecosystem

   ecosystem/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: Model Card

   model_card/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: finetune

   finetune/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: dialogue interface

   dialogue_interface/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: agent

   agent/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: long_context

   long_context/*

.. toctree::
   :caption: Switch Language

   switch_language.md

Indices and tables
====================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
