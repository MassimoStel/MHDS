# Codebook — Mental Health Digital Shadows Dataset


This codebook provides detailed information about the data structures and encoding schemas used in the **Mental Health Digital Shadows** dataset. The dataset contains generations from different Large Language Models (LLMs) which have been cleaned and validated.

## Table of contents

- [Pipeline Overview](#pipeline-overview)
- [Dataset Overview](#dataset-overview)
- [Metadata](#metadata)
- [Numeric Variables](#numeric-variables)
- [Categorical variables](#categorical-variables)
  - [Automatically Encoded Variables](#automatically-encoded-variables)
  - [Manually Encoded Variables](#manually-encoded-variables)
- [Mental Health Topics](#mental-health-topics)
- [Emotional Recall Task (`ert`)](#emotional-recall-task-ert)
- [DASS-21 responses](#dass-21-responses)
- [License](#license)

---
## Pipeline Overview

The figure below illustrates the full data generation pipeline, from persona synthesis and mode assignment to task administration and dataset construction.

![Infographic](infographic.png)

## Dataset Overview

#### Model Legend

Short abbreviations used throughout the paper to refer to the language models under evaluation. Each row lists the abbreviation, the full model name, and the corresponding Hugging Face model identifier used to load the model.


| **Abbrev.** | **Full Model Name** | **HF Model ID** |
|:------------|:--------------------|:----------------|
| ANITA-U | ANITA-NEXT-24B-Dolphin-Mistral-UNCENSORED-ITA | `mradermacher/ANITA-NEXT-24B-Dolphin-Mistral-UNCENSORED-ITA-i1-GGUF` |
| DSK-R1-32B | DeepSeek-R1-Distill-Qwen-32B | `deepseek-ai/DeepSeek-R1-Distill-Qwen-32B` |
| DSK-R1-70B | DeepSeek-R1-Distill-Llama-70B | `deepseek-ai/DeepSeek-R1-Distill-Llama-70B` |
| GPT-OSS | GPT-OSS-20B | `openai/gpt-oss-20b` |
| Granite-4H-T | Granite 4.0 H Tiny (7B) | `ibm-granite/granite-4.0-h-tiny` |
| Magistral-S | Magistral Small 2506 (Reasoning) | `mistralai/Magistral-Small-2506` |
| Ministral-14B-R | Ministral 3 14B Reasoning 2512 | `mistralai/Ministral-3-14B-Reasoning-2512` |
| Mistral-S4 | Mistral Small 4 (119B MoE, 2603) | `mistralai/Mistral-Small-4-119B-2603` |
| Mistral-S3.2 | Mistral Small 3.2 24B Instruct 2506 | `mistralai/Mistral-Small-3.2-24B-Instruct-2506` |
| Phi-4-R+ | Microsoft Phi-4-reasoning-plus (14B) | `microsoft/Phi-4-reasoning-plus` |
| Qwen3-4B-IN | Qwen3-4B-Instruct | `Qwen/Qwen3-4B-Instruct-2507` |
| Qwen3.5-9B | Qwen3.5-9B | `Qwen/Qwen3.5-9B` |
| Qwen3-4B-TH | Qwen3-4B-Thinking | `Qwen/Qwen3-4B-Thinking-2507` |
| Qwen3-30B | Qwen3-30B-A3B (MoE) | `Qwen/Qwen3-30B-A3B` |
| Grok-4.1-R | Grok-4.1-Reasoning | `N/A (Closed-source, xAI API access)` |

---
## Metadata

#### Path ID (`path`) 

Output json file identifier.

#### Mode (`mode`) 

LLM role assigned

- **LLM-assistant (`mode == "llm"`)** — No sociodemographic features were assigned.
- **Human-shadow (`mode == "human"`)** — Different sociodemographic features were assigned to simulate a persona.

#### Summary of the reasoning (`reasoning_summary`)

Reasoning summary produced by the model alongside the structured response.

---


## Numeric Variables

#### Age (`age`)
Integer values from 18 to 90.

#### Children (`children`)
Integer values from 0 to 5.

#### Hobbies (`hobbies`)
Integer count of the total number of hobbies given (2-5).

---

## Categorical variables

The dataset utilizes two methods for encoding demographic information: **automatic mapping** and **manual mapping**.


### Automatically Encoded Variables

These variables were encoded algorithmically using `LabelEncoder` for alphabetical sorting.

#### Occupation (`occupation`)

| Code | Value | Code | Value |
|:----:|:------|:----:|:------|
| 0  | UX designer        | 16 | lawyer              |
| 1  | accountant         | 17 | mechanic            |
| 2  | architect          | 18 | not applicable      |
| 3  | barista            | 19 | nurse               |
| 4  | carpenter          | 20 | pharmacist          |
| 5  | chef               | 21 | plumber             |
| 6  | civil servant      | 22 | retail worker       |
| 7  | cleaner            | 23 | sales associate     |
| 8  | data scientist     | 24 | school teacher      |
| 9  | delivery driver    | 25 | scientist           |
| 10 | doctor             | 26 | software developer  |
| 11 | electrician        | 27 | startup founder     |
| 12 | engineer           | 28 | translator          |
| 13 | fitness trainer    | 29 | university professor|
| 14 | hairdresser        | 30 | university researcher|
| 15 | journalist         | 31 | waiter/waitress     |

#### City (`city`)

| Code | Value | Code | Value |
|:----:|:------|:----:|:------|
| 0 | Bari        | 6  | Milan         |
| 1 | Bologna     | 7  | Naples        |
| 2 | Chicago     | 8  | New York      |
| 3 | Kansas City | 9  | Philadelphia  |
| 4 | Lecce       | 10 | Rome          |
| 5 | Los Angeles | 11 | Washington DC |

#### Religion (`religion`)

| Code | Value |
|:----:|:------|
| 0 | Agnostic     |
| 1 | Atheist      |
| 2 | Buddhism     |
| 3 | Christianity |
| 4 | Hinduism     |
| 5 | Islam        |
| 6 | Judaism      |

### Manually Encoded Variables

These variables map semantic meaning directly onto a numerical scale according to manual definitions. Note that DASS-related symptoms reuse an ordinal scale for severity.

#### Gender (`gender`)

| Code | Value |
|:----:|:------|
| 0 | man           |
| 1 | woman         |
| 2 | non-binary    |
| 3 | agender       |
| 4 | queergender   |
| 5 | transgender   |

#### Sexual Orientation (`sexual_orientation`)

| Code | Value |
|:----:|:------|
| 0 | asexual      |
| 1 | heterosexual |
| 2 | bisexual     |
| 3 | homosexual   |

#### Employment Status (`employment_status`)

| Code | Value |
|:----:|:------|
| 0 | unemployed          |
| 1 | part-time student   |
| 2 | full-time student   |
| 3 | self-employed       |
| 4 | employed part-time  |
| 5 | employed full-time  |
| 6 | retired             |

#### Education (`education`, `parents_education_1`, `parents_education_2`)

| Code | Value |
|:----:|:------|
| 0 | no formal education |
| 1 | primary school      |
| 2 | lower secondary     |
| 3 | upper secondary     |
| 4 | vocational diploma  |
| 5 | bachelor's degree   |
| 6 | master's degree     |
| 7 | PhD                 |

#### Marital Status (`marital_status`)

| Code | Value |
|:----:|:------|
| 0 | single            |
| 1 | in a relationship |
| 2 | widowed           |
| 3 | divorced          |
| 4 | married           |

#### Migration Status (`migration_status`)

| Code | Value |
|:----:|:------|
| 0 | immigrant                               |
| 1 | native-born Italian                     |
| 2 | native-born American                    |

#### OCEAN Traits (`openness`, `conscientiousness`, `extraversion`, `agreeableness`, `neuroticism`)

| Code | Value |
|:----:|:------|
| 0 | low      |
| 1 | moderate |
| 2 | high     |

#### Symptoms (`depression` / `anxiety` / `stress`)

| Code | Value |
|:----:|:------|
| 0 | without [symptom] symptoms  |
| 1 | with light [symptom] symptoms    |
| 2 | with moderate [symptom] symptoms |
| 3 | with severe [symptom] symptoms   |


___

## Mental Health Topics

| **Dataset entry** | **Topic label** | **Topic question** |
|:------------------|:----------------|:-------------------|
| `topic_1` | Family support             | *Does your family support your mental wellbeing? What is their attitude towards mental health?* |
| `topic_2` | Drugs treatment            | *Did you ever take drugs for improving your mental health? Did you have any side effects?* |
| `topic_3` | Professional support       | *Did you ever meet a therapist, psychologist or life coach? How was your professional relationship with them?* |
| `topic_4` | Stigma and discrimination  | *Did you ever face stigma or discrimination due to mental health issues? How did you cope with it?* |
| `topic_5` | AI-Psychologist Support    | *Did you ever use mental health apps or AI-psychologists? Were they helpful?* |
| `topic_6` | OCD Symptoms               | *Did you ever experience intrusive thoughts or obsessive behaviors? How did you manage them?* |


## Emotional Recall Task (`ert`)

*Please recall 10 English words to describe feelings you have experienced during the past month*

The generated personas were asked to freely recall 10 English words describing feelings experienced in the past month. 
The words are stored as a list of strings (e.g., `["happy", "anxious", "tired", ...]`).
This task provides an unstructured, self-generated snapshot of the participant's recent emotional landscape.

## DASS-21 responses


#### Score (`dass_item_{n}_score`)

Score (0-3) assigned to item {n} of the DASS-21. Variable `n` takes values from 1 to 21.

#### Explanation (`dass_item_{n}_explanation`)
Textual explanation of the assigned score to item {n}. Variable `n` takes values from 1 to 21.

#### Subscale composition

Each DASS-21 subscale is the sum of seven items. To recover the depression, anxiety, and stress totals from the per-item scores, sum the items listed below:

| Subscale | Item indices (`n`) |
|:---------|:-------------------|
| **Depression** | 3, 5, 10, 13, 16, 17, 21 |
| **Anxiety**    | 2, 4, 7, 9, 15, 19, 20 |
| **Stress**     | 1, 6, 8, 11, 12, 14, 18 |

Each subscale therefore ranges from 0 to 21 on the DASS-21 scale.

---

## License

This dataset is released under the **Creative Commons Zero v1.0 Universal (CC0 1.0)** public-domain dedication — see the `LICENSE` file at the repository root for the full text.