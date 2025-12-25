# 🩺 Physician Notetaker: AI-Powered Medical Transcription

## 📌 Project Overview

The **Physician Notetaker** is an advanced NLP-based system designed to automate medical documentation. By processing transcribed physician-patient conversations, the system extracts critical clinical data, analyzes patient sentiment and intent, and formats everything into a structured **SOAP (Subjective, Objective, Assessment, Plan)** note.

This project aims to reduce administrative burnout for healthcare professionals by providing accurate, real-time documentation assistance.

---

## 🚀 Key Features

* **Medical NLP Summarization:** Extracts symptoms, diagnoses, treatments, and prognosis using specialized medical NER models.
* **Sentiment & Intent Analysis:** Uses Transformer-based models to detect patient distress and classify their intent (e.g., seeking reassurance vs. reporting symptoms).
* **Automated SOAP Note Generation:** Dynamically maps raw transcripts into the gold-standard medical documentation format.
* **Built-in Resilience:** Includes robust fallback logic to handle API rate limits and ensure clinical documentation continuity.

---

## 🛠️ Tech Stack & Models

* **Language:** Python 3.x
* **Generative AI:** `Gemini-1.5-Flash` / `Gemini-2.0-Flash` (via Google Generative AI SDK)
* **NER Model:** `d4data/biomedical-ner-all` (Hugging Face)
* **Classification:** `facebook/bart-large-mnli` (Zero-Shot Classification)
* **Libraries:** `transformers`, `torch`, `spacy`, `google-generativeai`

---

## ⚙️ Setup & Installation

### 1. Environment Setup

It is recommended to run this project in **Google Colab** to leverage free GPU resources.

### 2. API Configuration

1. Obtain a **Gemini API Key** from [Google AI Studio](https://aistudio.google.com/app/apikey).
2. In Colab, click the **Secrets (🔑)** icon on the left sidebar.
3. Add a secret named `GOOGLE_API_KEY` and paste your key.
4. Toggle "Notebook access" to **ON**.

### 3. Install Dependencies

```bash
pip install -q -U google-generativeai transformers torch spacy
python -m spacy download en_core_web_sm

```
---

## 📝 Assignment Questions & Answers

### 1. Medical NLP Summarization

* **Q: How would you handle ambiguous or missing medical data?**
* **A:** By implementing a confidence threshold. Entities with a low probability score are flagged for human verification. Missing data fields are assigned a "Not Specified" label to prevent AI hallucinations.


* **Q: What pre-trained NLP models would you use?**
* **A:** `BioBERT` or `PubMedBERT` for clinical context, and `BART` or `Gemini-Flash` for summarizing large conversations.



### 2. Sentiment & Intent Analysis

* **Q: How would you fine-tune BERT for medical sentiment detection?**
* **A:** I would use `BioBERT` with a classification head and fine-tune it on the `MTS-Dialog` dataset, using a weighted loss function to prioritize rare but critical "Anxious" sentiments.


* **Q: What datasets would you use?**
* **A:** `MedDialog` for conversational patterns and `SST-5` for general sentiment nuances.



### 3. SOAP Note Generation

* **Q: How would you train an NLP model to map transcripts into SOAP format?**
* **A:** Using **Few-Shot Learning**. By providing the model with examples of raw dialogues paired with professional SOAP notes, the AI learns to map subjective vs. objective details.


* **Q: What techniques would improve accuracy?**
* **A:** **Speaker Diarization** is essential to distinguish between what the patient reports (Subjective) and what the physician observes (Objective).
