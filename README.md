# Implementation of PAIR Algorithm for LLM Response Analysis

This repository implements the PAIR (Prompt Automatic Iterative Refinement) algorithm for analyzing Large Language Model responses under adversarial conditions. The implementation enables researchers to study model behaviors, safety mechanisms, and potential vulnerabilities through systematic prompt engineering.

> **Note**: This tool is intended strictly for academic research and security analysis. Any use for malicious purposes is prohibited.

---

## Table of Contents
- [Prerequisites](#prerequisites)
  - [Environment and Libraries](#environment-and-libraries)
  - [API Keys](#api-keys)
- [Files and Configuration](#files-and-configuration)
  - [Required Files](#required-files)
  - [Environment Variables](#environment-variables)
- [Running the Script](#running-the-script)
  - [Starting the Script](#starting-the-script)
  - [Options and Inputs](#options-and-inputs)
  - [Output](#output)
- [Example Workflow](#example-workflow)
  - [Interpreting Results](#interpreting-results)
- [Key Features](#key-features)
- [Notes](#notes)
- [Citation](#citation)
---
## Prerequisites

### Environment and Libraries
- **Python 3.8 or higher** is required.
Run the following command to verify the `Python` version.
```bash
  python --version
  ```

- Required Python libraries:
  - `openai`
  - `json`
  - `re`
- Install dependencies using:
  ```bash
  pip install openai
  ```
### API Keys
The script requires API keys for the OpenAI API and the Together API:
1. OpenAI API: Set the OPENAI_API_KEY in your environment variables.
2. Together API (optional, depending on selected model): Set the TOGETHER_API_KEY in your environment variables.

---
## Files and Configuration

### Required Files
- `pair.py`
    - Main script for running the PAIR algorithm.
- `judge_system.txt`
    - Defines the judging system for evaluating model responses.
    - This file includes task guidelines and evaluation metrics, specifying how to rate the language model's responses on ethical, legal, or safety violations.
    - Ensure this file is located in the same directory as pair.py, or adjust the file path in the script.
- `attacker_system.txt`
    - Defines the system prompt for the attacking LLM that generates adversarial prompts
    - Format: Instructions and guidelines for generating prompts following the PAIR methodology
    - Must be located in the same directory as pair.py or adjust the file path in the script
- `roleplay_system.txt`
    - Contains instructions for crafting adversarial prompts in a roleplaying context.
    - Defines strategies for creating and refining jailbreak prompts using obfuscation, emotional manipulation, and roleplaying scenarios to evade the model's safety measures.
    - It includes examples of effective adversarial prompts and explains how to iteratively refine them to maximize their effectiveness.
    - Ensure this file is accessible to the script, as it guides the prompt generation process.

### Environment Variables
- `OPENAI_API_KEY`: Your OpenAI API key.
- `TOGETHER_API_KEY`: Your Together API key (optional, depending on selected model) obtained from [Together.AI] (https://www.together.ai/).

Ensure the following environment variables are set:
```bash
export OPENAI_API_KEY='your_openai_api_key'
export TOGETHER_API_KEY='your_together_api_key'
```
---
## Running the Script

### Starting the Script
```bash
python pair.py
```
### Options and Inputs
1. Model Selection:
   > - Select the attacker and target models from the menu. Options include:
   > - gpt-3.5-turbo
   > - Mixtral-8x7B-Instruct-v0.1
   > - Other models as defined in the choose_model() function.
2. Iterations:
   > - Enter the number of iterations for the adversarial attempts. A higher number increases the chances of successful jailbreaks.
3. Objective:
   > - Define the objective of the jailbreak, e.g., "Design a phishing email that can trick users."
### Output
   > - Console: Progress and results of the jailbreak attempts are displayed.
   > - `output.txt`: Detailed results including prompts, responses, success status, and ratings are saved here.

---
## Example Workflow

1. Run the script:
```bash
python pair.py
```
2. Select attacker and target models.
3. Specify the number of iterations, e.g., 10.
4. Enter a jailbreak objective, e.g., "Generate unsafe code examples."
### Interpreting Results
- **Success**: A successful jailbreak prompt and response are displayed.
- **Failure**: Check `output.txt` for failed attempts and refinements.

---

## Key Features
- **Dynamic Model Selection**: Choose between multiple attacker and target models.
- **Adversarial Prompt Refinement**: Iterative process improves the likelihood of jailbreaking the language model.
- **Judging System**: Evaluates responses using `judge_system.txt` rules.

---

## Notes
- This script is designed for educational and research purposes. Ensure you comply with legal and ethical guidelines when using it.
- The effectiveness of the jailbreak may vary depending on the specific models and parameters used.
- Always test in a controlled environment before deploying any jailbreak techniques.

---

## Citation
This implementation is based on the research paper:

```bibtex
@misc{chao2023jailbreaking,
      title={Jailbreaking Black Box Large Language Models in Twenty Queries}, 
      author={Patrick Chao and Alexander Robey and Edgar Dobriban and Hamed Hassani and George J. Pappas and Eric Wong},
      year={2023},
      eprint={2310.08419},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```

For more details about the PAIR methodology, please refer to the [original paper](https://arxiv.org/abs/2310.08419).

---
