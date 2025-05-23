Welcome to InternLM’s tutorials!
====================================

.. figure:: ./_static/image/internlm-logo.svg
  :width: 50%
  :align: center
  :alt: InternLM
  :class: no-scaled-link

.. raw:: html

   <p style="text-align:center">
   <strong>InternLM keeps open-sourcing high quality LLMs as well as<br>
   a full-stack toolchain for development and application.</strong>
   </p>

   <p style="text-align:center">
   <script async defer src="https://buttons.github.io/buttons.js"></script>
   <a class="github-button" href="https://github.com/InternLM/InternLM" data-show-count="true" data-size="large" aria-label="Star">Star</a>
   <a class="github-button" href="https://github.com/InternLM/InternLM/subscription" data-icon="octicon-eye" data-size="large" aria-label="Watch">Watch</a>
   <a class="github-button" href="https://github.com/InternLM/InternLM/fork" data-icon="octicon-repo-forked" data-size="large" aria-label="Fork">Fork</a>
   </p>


Latest News 🔥
-------------

We released InternLM3, which has open-sourced an 8-billion parameter instruction model, InternLM3-8B-Instruct, designed for general-purpose usage and advanced reasoning. This model has the following characteristics:

- **Enhanced performance at reduced cost**:
  State-of-the-art performance on reasoning and knowledge-intensive tasks surpass models like Llama3.1-8B and Qwen2.5-7B. Remarkably, InternLM3 is trained on only 4 trillion high-quality tokens, saving more than 75% of the training cost compared to other LLMs of similar scale.
- **Deep thinking capability**:
  InternLM3 supports both the deep thinking mode for solving complicated reasoning tasks via the long chain-of-thought and the normal response mode for fluent user interactions.


Documentation
-------------

.. toctree::
   :maxdepth: 1
   :caption: Get Started

   get_started/chat_web.md
   get_started/chat_local.md
   get_started/InternLM_API.md

.. toctree::
   :maxdepth: 1
   :caption: Inference

   inference/huggingface_transformers.md
   inference/chat_format.md

.. toctree::
   :maxdepth: 1
   :caption: Run Locally

   run_locally/ollama.md
   run_locally/llama.cpp.md
   run_locally/llamafile.md
   run_locally/mlx.md
   run_locally/tgi.md

.. toctree::
   :maxdepth: 1
   :caption: Deployment

   deployment/LMDeploy.md
   deployment/vLLM.md
   deployment/SGLang.md

.. toctree::
   :maxdepth: 1
   :caption: Training

   training/xtuner.md
   training/internevo.md
   training/index.rst

.. toctree::
   :maxdepth: 1
   :caption: Application

   application/openaoe.md
   application/langchain.md
   application/lazyllm.md
   application/llamaindex.md
   application/openwebui.md

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: Agent

   agent/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: Long Context

   long_context/*

.. toctree::
   :maxdepth: 1
   :caption: Model Card

   model_card/InternLM3.md
   model_card/InternLM2.5.md
   model_card/InternLM2.md
   model_card/InternLM.md

.. toctree::
   :caption: Switch Language

   switch_zh.md
