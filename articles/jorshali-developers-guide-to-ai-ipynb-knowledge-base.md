# Knowledge Base: Jupyter Notebooks in `jorshali/developers-guide-to-ai`

This article documents the Jupyter notebooks in the `jorshali/developers-guide-to-ai` repository, specifically the notebook-based workflow in `part4/`.

## Repository Overview
- **Source repository:** `jorshali/developers-guide-to-ai`
- **Primary language:** Python
- **Focus:** AI, LLMs, prompt engineering, classification, and fine-tuning workflows

## Notebook Inventory
The following notebook files were identified in `part4/`:

1. `part4/01-dataset.ipynb`
2. `part4/02.zeroShot.ipynb`
3. `part4/03-finetune-classificationModel.ipynb`
4. `part4/04-chat-examples.ipynb`
5. `part4/05-finetune-dataset.ipynb`
6. `part4/06-finetune-llm.ipynb`
7. `part4/07-test-ft-llm.ipynb`

---

## 1. `part4/01-dataset.ipynb`
### Purpose
Builds the labeled dataset used later for classification and fine-tuning.

### What it does
- Imports `load_dataset` from Hugging Face `datasets`
- Loads four CSV data sources:
  - `rawData/in_bank.csv`
  - `rawData/in_school.csv`
  - `rawData/us_bank.csv`
  - `rawData/us_school.csv`
- Creates datasets representing four categories:
  - `IN_Bank`
  - `IN_School`
  - `US_Bank`
  - `US_School`

### Key concepts
- Data ingestion from CSV files
- Label creation for supervised learning
- Preparing structured datasets for downstream model training

### Expected output
- `DatasetDict` objects with fields such as `text` and `label`
- A reusable labeled dataset for later notebooks

### Dependencies
- `datasets`

### Notes
- Notebook output includes environment warnings related to `ipywidgets` and `urllib3`; these do not appear to affect the notebook’s core purpose.

---

## 2. `part4/02.zeroShot.ipynb`
### Purpose
Explores zero-shot or prompt-based classification before any model fine-tuning.

### What it does
- Loads a saved dataset from `./data/mail_dataset_labeled`
- Defines two model references:
  - `distilbert/distilbert-base-uncased`
  - `Qwen/Qwen2.5-0.5B-Instruct`
- Defines the label set:
  - `IN_Bank`
  - `IN_School`
  - `US_Bank`
  - `US_School`
- Inspects dataset features and examples

### Key concepts
- Zero-shot inference
- Baseline evaluation before training
- Comparing model families for classification-style tasks

### Expected output
- Dataset schema inspection
- Sample labeled examples
- An early baseline for the classification problem

### Dependencies
- `datasets`

### Notes
- The variable `lable_names` appears to contain a typo and would be clearer as `label_names`.

---

## 3. `part4/03-finetune-classificationModel.ipynb`
### Purpose
Fine-tunes a sequence classification model for the email/document categorization task.

### What it does
- Imports Hugging Face training components:
  - `AutoModelForSequenceClassification`
  - `AutoTokenizer`
  - `TrainingArguments`
  - `Trainer`
  - `DataCollatorWithPadding`
- Uses `distilbert/distilbert-base-uncased`
- Loads the labeled dataset from `./data/mail_dataset_labeled`
- Tokenizes text using a preprocessing function
- Defines `label2id` and `id2label` mappings for the four categories

### Key concepts
- Supervised text classification
- Tokenization and truncation
- Trainer-based model training and evaluation
- Mapping between string labels and numeric class IDs

### Expected output
- Tokenized dataset
- Configured classification model
- A fine-tuned text classifier for email sorting

### Dependencies
- `transformers`
- `datasets`
- `numpy`
- `evaluate`

### Notes
- This notebook appears to represent the traditional classification-model path in the workflow.

---

## 4. `part4/04-chat-examples.ipynb`
### Purpose
Demonstrates how to structure chat prompts for a causal language model.

### What it does
- Loads:
  - `AutoTokenizer`
  - `AutoModelForCausalLM`
- Uses model `Qwen/Qwen3-0.6B`
- Builds a simple prompt with:
  - a `system` role
  - a `user` role
- Applies a chat template using `tokenizer.apply_chat_template(...)`

### Key concepts
- Chat prompting
- System/user role formatting
- Preparing prompts for instruction-tuned LLMs

### Expected output
- Tokenized chat input
- A working example of conversational prompt construction

### Dependencies
- `transformers`

### Notes
- The markdown heading `Simple promptimng` appears to contain a typo and should likely be `Simple prompting`.

---

## 5. `part4/05-finetune-dataset.ipynb`
### Purpose
Prepares a chat/instruction-style fine-tuning dataset from the labeled classification dataset.

### What it does
- Loads a tokenizer for `Qwen/Qwen2.5-0.5B-Instruct`
- Loads the labeled dataset from `./data/mail_dataset_labeled`
- Defines the label names
- Creates a system prompt instructing the model to classify email summaries into one of four categories:
  - India Bank
  - India School
  - US Bank
  - US School
- Prepares data records suitable for LLM fine-tuning

### Key concepts
- Dataset transformation for instruction tuning
- Prompt/response dataset formatting
- Converting classification data into conversational training examples

### Expected output
- An LLM-oriented dataset based on the original labeled samples
- Prompt templates ready for causal language model fine-tuning

### Dependencies
- `transformers`
- `datasets`

### Notes
- This notebook acts as the bridge between standard supervised classification data and LLM fine-tuning data.

---

## 6. `part4/06-finetune-llm.ipynb`
### Purpose
Fine-tunes a causal language model using the prepared LLM dataset.

### What it does
- Imports:
  - `AutoTokenizer`
  - `AutoModelForCausalLM`
  - `load_from_disk`
  - `Dataset`
  - `torch`
- Detects whether Apple Silicon MPS is available and falls back to CPU if not
- Loads model `Qwen/Qwen2.5-0.5B-Instruct`
- Loads the dataset from `./data/llm_mail_dataset`
- Begins a training workflow for the LLM

### Key concepts
- Causal language model fine-tuning
- Device selection (`mps` vs `cpu`)
- Training on instruction-formatted data

### Expected output
- A fine-tuned LLM specialized for mail classification behavior
- A local model artifact suitable for later testing

### Dependencies
- `transformers`
- `datasets`
- `torch`

### Notes
- This notebook appears to be the main LLM fine-tuning stage in the notebook sequence.

---

## 7. `part4/07-test-ft-llm.ipynb`
### Purpose
Loads and tests the fine-tuned LLM against the prepared evaluation dataset.

### What it does
- Imports:
  - `AutoTokenizer`
  - `AutoModelForCausalLM`
  - `load_from_disk`
  - `Dataset`
  - `torch`
- Detects and configures `mps` or `cpu`
- Loads the locally saved fine-tuned model from `models/my_llm_mail_classifier`
- Loads the evaluation dataset from `./data/llm_mail_dataset`
- Runs post-training inference/testing

### Key concepts
- Loading a fine-tuned local model
- Evaluation and inference after training
- Validating instruction-tuned classification behavior

### Expected output
- Predictions from the fine-tuned model
- A practical test of whether the model learned the classification task

### Dependencies
- `transformers`
- `datasets`
- `torch`

### Notes
- Notebook output includes a `bitsandbytes` warning and a `'NoneType' object has no attribute 'cadam32bit_grad_fp32'` message, which may indicate a local environment or package configuration issue.

---

## End-to-End Workflow Summary
These notebooks together define a multi-step learning and implementation path:

1. **Create the base dataset** from raw CSV files
2. **Evaluate zero-shot approaches** as an initial baseline
3. **Fine-tune a traditional classifier** using DistilBERT
4. **Explore chat prompting** with a causal LLM
5. **Transform the dataset** into instruction-tuning format
6. **Fine-tune a causal LLM** on the transformed dataset
7. **Test the fine-tuned LLM** on evaluation data

This progression is useful for demonstrating the differences between:
- Traditional supervised text classification
- Prompt-based LLM usage
- Instruction tuning and causal model fine-tuning

## Recommended Tags
- AI
- Python
- Jupyter
- Hugging Face
- Transformers
- LLM
- Fine-tuning
- Text Classification
- Dataset Preparation

## Suggested File Location
A suitable path in the `rmssoftwaretech/Knowledgebase` repository would be:

`articles/jorshali-developers-guide-to-ai-ipynb-knowledge-base.md`
