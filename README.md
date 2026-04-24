# Mental Health Digital Shadows (MHDS) Dataset
Digital shadows in Mental Health: A dataset mapping how LLMs simulate Depression, Anxiety, and Stress through language and psychometrics

## Overview

This repository accompanies the paper introducing **Mental Health Digital Shadows (MHDS)**, a benchmark of 75,000 LLM outputs from 15 large language models in conversation with human personas and AI assistants. MHDS includes personas derived from cutting-edge model families such as Grok, DeepSeek, Mistral, Qwen, ChatGPT, Granite, and Phi. Personas are conditioned on sociodemographics and personality traits alongside assessments of depression, anxiety, and stress levels based on the DASS-21 scale.

The dataset enables researchers to compare distress levels across individuals, analyze the centrality of language use, and study linguistic framing effects between psychometrics and natural language.

---

## Data Folder

The `data` directory contains **15 CSV files**, one per LLM evaluated in the study. Each file is named after the model's abbreviation (e.g., `DSK-R1-32B.csv`, `Mistral-S3.2.csv`) and contains all generations produced by that model across both experimental modes (LLM Mode and Human Mode).

The table below maps each filename (abbreviation) to its full model name and the corresponding Hugging Face model identifier used to load and run the model:

| **File (Abbrev.)** | **Full Model Name** | **HF Model ID** |
|:------------|:--------------------|:----------------|
| `ANITA-U.csv` | ANITA-NEXT-24B-Dolphin-Mistral-UNCENSORED-ITA | `mradermacher/ANITA-NEXT-24B-Dolphin-Mistral-UNCENSORED-ITA-i1-GGUF` |
| `DSK-R1-32B.csv` | DeepSeek-R1-Distill-Qwen-32B | `deepseek-ai/DeepSeek-R1-Distill-Qwen-32B` |
| `DSK-R1-70B.csv` | DeepSeek-R1-Distill-Llama-70B | `deepseek-ai/DeepSeek-R1-Distill-Llama-70B` |
| `GPT-OSS.csv` | GPT-OSS-20B | `openai/gpt-oss-20b` |
| `Granite-4H-T.csv` | IBM Granite 4.0 H Tiny (7B, MoE hybrid) | `ibm-granite/granite-4.0-h-tiny` |
| `Magistral-S.csv` | Magistral Small 2506 (MoE reasoning) | `mistralai/Magistral-Small-2506` |
| `Ministral-14B-R.csv` | Ministral 3 14B Reasoning 2512 | `mistralai/Ministral-3-14B-Reasoning-2512` |
| `Mistral-S4.csv` | Mistral Small 4 (119B MoE, 2603) | `mistralai/Mistral-Small-4-119B-2603` |
| `Mistral-S3.2.csv` | Mistral Small 3.2 24B Instruct 2506 | `mistralai/Mistral-Small-3.2-24B-Instruct-2506` |
| `Phi-4-R+.csv` | Microsoft Phi-4-reasoning-plus (14B) | `microsoft/Phi-4-reasoning-plus` |
| `Qwen3-4B-IN.csv` | Qwen3-4B-Instruct | `Qwen/Qwen3-4B-Instruct-2507` |
| `Qwen3.5-9B.csv` | Qwen3.5-9B-Thinking (MoE) | `Qwen/Qwen3.5-9B` |
| `Qwen3-4B-TH.csv` | Qwen3-4B-Thinking | `Qwen3-4B-Thinking-2507` |
| `Qwen3-30B.csv` | Qwen3-30B-A3B (MoE) | `Qwen/Qwen3-30B-A3B` |
| `Grok-4.1-R.csv` | Grok-4.1-Reasoning | N/A (closed-source, xAI API access) |

## Codebook

The `codebook.md` contains all the instructions useful carry data analysis with MHDS (e.g., variables encoding, column names).