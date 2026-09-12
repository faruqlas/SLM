# 🩺 Small Language Model for Medical Advice

---

## Project Overview

This project aims to build and train a small language model for medical question answering.
The model learns from a structured CSV dataset containing:
  - Medical questions
  - Medical topics
  - Care settings
  - Patient populations
  - Reference answers
  - Document identifiers
The model is trained to generate an answer given a medical question and its associated context.
Unlike approaches that load an existing GPT-2 model and fine-tune it, this project starts with randomly initialised model parameters.

---

## Objectives

Develop a Clinical Retrieval System: Train and fine-tune a domain-specific small language model (SLM) integrated with Retrieval-Augmented Generation (RAG) to synthesise peer-reviewed medical literature and interpret symptom queries accurately.

Ensure Patient Data Privacy: Implement automated, multi-pass data de-identification and sanitisation pipelines to guarantee patient confidentiality and prevent the exposure of sensitive health attributes.

Eliminate Medical Hallucinations: Constrain model outputs strictly to verified, peer-reviewed clinical literature with explicit source citations to keep medical guidance firmly grounded in evidence.

Empower Clinical & Patient Decision-Making: Provide frontline healthcare workers with fast, reliable point-of-care decision support while offering patients safe, clear, and accessible health summaries.

Enable Resource-Efficient Deployment: Optimise the model footprint into a lightweight SLM format suitable for low-cost, offline-first hardware in resource-constrained primary healthcare settings.

---

## Why Train From Scratch?
The purpose of this project is not simply to fine-tune an existing language model.
Instead, it demonstrates the complete process of building a GPT-2-style model:
  - Preparing the training data
  - Building the tokeniser
  - Converting text into token IDs
  - Implementing Transformer blocks
  - Implementing causal self-attention
  - Implementing positional embeddings
  - Implementing the language-model head
  - Initialising model parameters
  - Training using next-token prediction
  - Saving learned weights
  - Loading the trained model
  - Generating answers autoregressively
  - Evaluating the generated responses
This makes the project useful for understanding how decoder-only Transformer language models work internally.

---

## Dataset
Source: https://www.kaggle.com/competitions/medical-advice-slm-challenge 
The project uses two CSV files:
- train_qa.csv
- test_questions.csv

#### Training dataset
train_qa.csv contains the training examples.
Example structure:
  Column            Description
  question          Medical question
  topic             Medical topic
  care_setting      Healthcare setting
  population        Patient population
  document_id       Source document identifier
  reference_answer  Expected/reference answer
  QuestionId        Question identifier

#### Test dataset
test_questions.csv contains questions held out for evaluation.
It contains fields such as:
- QuestionId
- question
- topic
- care_setting
- population

The test questions are not used to train the model.

---

## Limitations
This project has several important limitations.

### Small dataset
The available medical QA dataset is relatively small compared with the datasets used to train large language models.
A GPT-2-style model with many parameters may therefore overfit.

### No pretrained knowledge
Because the model starts from random weights, it does not initially know:
English language structure
Medical terminology
General world knowledge
Clinical concepts
It must learn these patterns from the training data.

### Limited medical knowledge
A model trained on a small dataset cannot be expected to provide comprehensive medical knowledge.

### Hallucination
The model can generate plausible but incorrect statements.

### Clinical safety
Generated responses must not be treated as medical advice or used as a substitute for a qualified healthcare professional.

---

## Tools and dependencies
* Kaggle
* Python
* Pandas
* Numpy
* SciKit Learn
* PyTorch

---

## Project Structure
A possible project structure is:
main/
│
├── data/
│   ├── medical-advice-slm-challenge.zip
│   └── submission.csv
│
├── docs/
│   └── data_card.pdf
│   └── impact_statement.pdf
│   └── problem_statement.pdf
│   └── stakeholder_engagement.pdf
│
├── scripts
│   └── c10_med_advice_slm.ipynb
│   └── dataset-metadata.json
│
└── README.md

