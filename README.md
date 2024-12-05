# ☕ Fine-Tuning LLaMA for a Coffee Kiosk Model

## Table of Contents
- [Project Description](#project-description)
- [How to Replicate](#how-to-replicate)
- [Uploaded Models](#uploaded-models)
- [Results and Examples](#results-and-examples)
- [Limitations and Future Improvements](#limitations-and-future-improvements)
- [License](#license)
- [Acknowledgements](#acknowledgements)

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
   - Use [oobabooga's text generation webui](https://github.com/oobabooga/text-generation-webui) for training.
   - Load the LLaMA model (3B or 8B). Quantization is optional but recommended for resource efficiency.
   - Place the dataset in the `training/datasets` directory.
