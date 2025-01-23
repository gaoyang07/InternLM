
:github_url: https://github.com/InternLM/InternLM

InternLM documentation
=========================================

We released InternLM3, which has open-sourced an 8-billion parameter instruction model, InternLM3-8B-Instruct, designed for general-purpose usage and advanced reasoning. This model has the following characteristics:

- **Enhanced performance at reduced cost**:
  State-of-the-art performance on reasoning and knowledge-intensive tasks surpass models like Llama3.1-8B and Qwen2.5-7B. Remarkably, InternLM3 is trained on only 4 trillion high-quality tokens, saving more than 75% of the training cost compared to other LLMs of similar scale.
- **Deep thinking capability**:
  InternLM3 supports both the deep thinking mode for solving complicated reasoning tasks via the long chain-of-thought and the normal response mode for fluent user interactions.

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: Model Card

   model_card/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: ecosystem

   ecosystem/ecosystem.md

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: finetune

   finetune/finetune.md

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: chat

   chat/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: agent

   agent/*

.. toctree::
   :glob:
   :maxdepth: 1
   :caption: long_context

   long_context/long_context.md

.. toctree::
   :caption: Switch Language

   switch_language.md

Indices and tables
====================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
