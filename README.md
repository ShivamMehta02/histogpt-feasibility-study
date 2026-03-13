# HistoGPT Feasibility Study
# HistoGPT Feasibility Study

This project evaluates the **technical feasibility of running the HistoGPT model for computational pathology workflows**.  
The goal is to understand the **hardware requirements, inference latency, and scaling behaviour** of the model.

---

## Project Overview

HistoGPT is a multimodal model designed for **histopathology image understanding and report generation**.

The model processes:

- Slide image patch embeddings
- Text tokens (medical vocabulary)

and produces:

- pathology report logits

---

## Experiments Conducted

The following experiments were implemented in this feasibility study:

### 1. Model Initialization Test
Verified that the architecture can be instantiated without pretrained weights and measured base GPU memory usage.

### 2. GPU Memory Usage Analysis
Measured GPU memory requirements during:

- architecture initialization
- loading pretrained weights
- inference execution

Observed memory usage:

| Stage | GPU Memory |
|------|------|
Architecture only | ~3.2 GB |
With pretrained weights | ~6.6 GB |
During inference | ~8.8 GB |

### 3. Inference Latency Benchmark

Inference time was measured across multiple runs.

Average inference time:
768

Tested compressed representations:

- 512
- 256
- 128
- 64

Results show that **moderate compression reduces latency while maintaining output shape**.

---

## Key Findings

- HistoGPT requires **~9GB GPU memory during inference**
- Consumer GPUs with **4GB VRAM are insufficient**
- GPUs such as **Tesla T4 / RTX 3060+ are recommended**
- Inference latency remains **below ~0.35 seconds per sample**

---

## System Architecture

Tested compressed representations:

- 512
- 256
- 128
- 64

Results show that **moderate compression reduces latency while maintaining output shape**.

---

## Key Findings

- HistoGPT requires **~9GB GPU memory during inference**
- Consumer GPUs with **4GB VRAM are insufficient**
- GPUs such as **Tesla T4 / RTX 3060+ are recommended**
- Inference latency remains **below ~0.35 seconds per sample**

---

## System Architecture
Whole Slide Image
↓
Patch Extraction
↓
Feature Embeddings
↓
Perceiver Resampler
↓
BioGPT Decoder
↓
Pathology Report Generation

## Repository Contents


README.md
ShivamMehta02_histogpt_feasibility_study.ipynb
.gitignore


---

## Future Work

Potential next steps include:

- Whole-slide image pipeline integration
- attention-based patch selection
- pathology report generation evaluation
- clinical dataset benchmarking

---

## Author

Shivam Mehta  
AIML Engineering Student
