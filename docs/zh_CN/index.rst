欢迎来到 InternLM 教程！
====================================

.. figure:: ./_static/image/internlm-logo.svg
  :width: 50%
  :align: center
  :alt: InternLM
  :class: no-scaled-link

.. raw:: html

   <p style="text-align:center">
   <strong>InternLM 持续开源高质量的大语言模型以及<br>
   用于开发和应用的全栈工具链。</strong>
   </p>

   <p style="text-align:center">
   <script async defer src="https://buttons.github.io/buttons.js"></script>
   <a class="github-button" href="https://github.com/InternLM/InternLM" data-show-count="true" data-size="large" aria-label="Star">Star</a>
   <a class="github-button" href="https://github.com/InternLM/InternLM/subscription" data-icon="octicon-eye" data-size="large" aria-label="Watch">Watch</a>
   <a class="github-button" href="https://github.com/InternLM/InternLM/fork" data-icon="octicon-repo-forked" data-size="large" aria-label="Fork">Fork</a>
   </p>


最新消息 🔥
-------------

我们发布了 InternLM3，开源了一个80亿参数的指令模型 InternLM3-8B-Instruct，专为通用用途和高级推理而设计。该模型具有以下特点：

- **以更低成本实现更强性能**：
  在推理和知识密集型任务上的最先进性能超越了 Llama3.1-8B 和 Qwen2.5-7B 等模型。值得注意的是，InternLM3 仅使用4万亿个高质量标记进行训练，相比同等规模的其他LLM节省了75%以上的训练成本。
- **深度思考能力**：
  InternLM3 支持深度思考模式，通过长链思维解决复杂推理任务，同时也支持流畅用户交互的正常响应模式。


文档导航
-------------

.. toctree::
   :maxdepth: 1
   :caption: 快速开始

   get_started/chat_web.md
   get_started/chat_local.md
   get_started/InternLM_API.md

.. toctree::
   :maxdepth: 1
   :caption: 推理

   inference/huggingface_transformers.md
   inference/chat_format.md

.. toctree::
   :maxdepth: 1
   :caption: 本地运行

   run_locally/ollama.md
   run_locally/llama.cpp.md
   run_locally/llamafile.md
   run_locally/mlx.md
   run_locally/tgi.md

.. toctree::
   :maxdepth: 1
   :caption: 部署

   deployment/LMDeploy.md
   deployment/vLLM.md
   deployment/SGLang.md

.. toctree::
   :maxdepth: 1
   :caption: 训练

   training/xtuner.md
   training/internevo.md
   training/index.rst

.. toctree::
   :maxdepth: 1
   :caption: 应用

   application/openaoe.md
   application/langchain.md
   application/lazyllm.md
   application/llamaindex.md
   application/openwebui.md

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: 智能体

   agent/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: 长上下文

   long_context/*

.. toctree::
   :maxdepth: 1
   :caption: 模型介绍

   model_card/InternLM3.md
   model_card/InternLM2.5.md
   model_card/InternLM2.md
   model_card/InternLM.md

.. toctree::
   :caption: 切换语言

   switch_en.md
