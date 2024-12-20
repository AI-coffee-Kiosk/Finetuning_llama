# ☕ Fine-Tuning LLaMA for a Coffee Kiosk Model

## Table of Contents
- [Project Description](#project-description)
- [How to Replicate](#how-to-replicate)
- [Uploaded Models](#uploaded-models)
- [Results and Examples](#results-and-examples)
- [Limitations and Future Improvements](#limitations-and-future-improvements)

---
## Project Description
This project focuses on fine-tuning Meta’s LLaMA model to create an AI assistant for coffee kiosks. The goal was to enable the model to process customer orders via natural language input and generate accurate responses and backend-friendly JSON outputs. This was achieved through a series of iterative fine-tuning processes using specifically tailored datasets for coffee order scenarios.

By leveraging an advanced conversation-based AI, this kiosk aims to enhance accessibility, streamline the ordering process, and improve overall customer satisfaction.

---

## How to Replicate

1. **Prepare the Dataset**
   - Create a dataset of coffee order scenarios in JSON format. The dataset should include variations of customer inputs, correct responses, and backend action formats.
   - Example:
     ```json
     {
       "instruction": "Respond only in the correct action formats without any explanations or additional comments. When the current order and input below is:",
       "current_orders": {"drinks": []},
       "input": "아메리카노 1잔 주세요",
       "response": "\"new_order_item\", \"name\": \"아메리카노\", \"size\": \"미디움\", \"temperature\": \"핫\", \"quantity\": 1, \"add_ons\": \"None\""
     }
     ```
2. **Set Up Training Environment**
   - Load the LLaMA model (3B or 8B). Quantization is optional but recommended for resource efficiency.
   - Place the dataset in the `training/datasets` directory.

3. **Fine-Tune the Model**
   - Configure the training settings:
     - Epochs: `5`
     - Batch size: `8`
     - Learning rate: `2e-5`
   - Start the fine-tuning process.
4. **Upload and Test**
   - Upload the fine-tuned model to Hugging Face.
   - Test the model using various prompts to validate its understanding of coffee orders.

---
## Uploaded Models

Below are the fine-tuned models uploaded to Hugging Face:

| Version | Link | Notes |
| --- | --- | --- |
| 9th | [wolf010/9th_finetuned_llama-3-Korean-Bllossom-8B_q4](https://huggingface.co/wolf010/9th_finetuned_llama-3-Korean-Bllossom-8B_q4) | Final version with quantization. |
| 9th (non-quantized) | [wolf010/9th_finetuned_llama-3-Korean-Bllossom-8B](https://huggingface.co/wolf010/9th_finetuned_llama-3-Korean-Bllossom-8B) | Fully fine-tuned without quantization. |
| 9th (LoRA) | [wolf010/9th_finetuned_llama-3-Korean-Bllossom-8B-lora](https://huggingface.co/wolf010/9th_finetuned_llama-3-Korean-Bllossom-8B-lora) | Fine-tuned using LoRA. |
| 8th | [wolf010/8th_finetuned_llama-3-Korean-Bllossom-8B](https://huggingface.co/wolf010/8th_finetuned_llama-3-Korean-Bllossom-8B) | Pre-final iteration. |
| 7th | [wolf010/7th_finetuned_llama-3-Korean-Bllossom-8B_q4](https://huggingface.co/wolf010/7th_finetuned_llama-3-Korean-Bllossom-8B_q4) | Earlier iteration with quantization. |
| 7th (non-quantized) | [wolf010/7th_finetuned_llama-3-Korean-Bllossom-8B](https://huggingface.co/wolf010/7th_finetuned_llama-3-Korean-Bllossom-8B) | Non-quantized earlier iteration. |
| 6th | [wolf010/6th_finetuned_llama-3-Korean-Bllossom-8B](https://huggingface.co/wolf010/6th_finetuned_llama-3-Korean-Bllossom-8B) | Fine-tuned with enhancements for edge cases. |
| 5th | [wolf010/5TH_fine_tuned_llama-3.2-Korean-Bllossom-3B.q8_0-gguf](https://huggingface.co/wolf010/5TH_fine_tuned_llama-3.2-Korean-Bllossom-3B.q8_0-gguf) | Optimized with gguf format. |
| 5th (non-quantized) | [wolf010/5TH_fine_tuned_llama-3.2-Korean-Bllossom-3B](https://huggingface.co/wolf010/5TH_fine_tuned_llama-3.2-Korean-Bllossom-3B) | Fully fine-tuned in a non-quantized format. |
| 4th | [wolf010/4th_finetuned_korean8b-gguf](https://huggingface.co/wolf010/4th_finetuned_korean8b-gguf) | Fine-tuned with gguf for performance. |
| 4th (non-quantized) | [wolf010/4TH_fine_tuned_Llama-3.2-3B-Instruct](https://huggingface.co/wolf010/4TH_fine_tuned_Llama-3.2-3B-Instruct) | Pre-optimized iteration for instructions. |
| 3rd | [wolf010/3rd_fine_tuned_Llama-3.2-3B-Instruct](https://huggingface.co/wolf010/3rd_fine_tuned_Llama-3.2-3B-Instruct) | Initial model tailored for coffee kiosk orders. |
| 2nd | [wolf010/2nd_fine_tuned_Llama-3.2-3B-Instruct](https://huggingface.co/wolf010/2nd_fine_tuned_Llama-3.2-3B-Instruct) | Second iteration with refined dataset. |
| 1st | [wolf010/1st_fine_tuned_Llama-3.2-3B-Instruct](https://huggingface.co/wolf010/1st_fine_tuned_Llama-3.2-3B-Instruct) | Baseline model for fine-tuning experiments. |

## Results and Examples

After fine-tuning, the model successfully handled complex customer orders and returned accurate responses. Here’s a comparison of input and output:

| Input | Action Response
| --- | --- |
| "아이스 아메리카노 라지 1잔 주세요" | `"new_order_item", "name": "아메리카노", "size": "라지", "temperature": "아이스", "quantity": 1, "add_ons": "None"` |

**Performance Metrics**:
- Total F1 Score: **93%**
- Average Precision: **91%**
- Average Recall: **95%**
---

## Limitations and Future Improvements

### Current Limitations
- **Resource-Intensive**: The LLaMA 8B model requires high-end GPUs for fast inference.
- **Hallucinations**: The model sometimes generates incorrect responses.
- **STT Integration**: Speech-to-text processing is not fully integrated, which can affect user experience in noisy environments.

### Future Improvements
- **Enhanced Datasets**: Adding more diverse and complex order scenarios.
- **Model Optimization**: Further fine-tuning for edge devices.
- **STT Integration**: Seamless integration with speech recognition systems.

---
