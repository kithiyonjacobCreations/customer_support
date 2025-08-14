# Fine-Tuned Llama 3.1 Customer Support Chatbot

This project demonstrates how to fine-tune the **Llama 3.1 8B** model on a custom dataset to build a **customer support chatbot**.  
The fine-tuning process uses **[Unsloth](https://github.com/unslothai/unsloth)** for faster training and reduced GPU memory usage in a **Google Colab** environment.  
The final model is packaged for **local deployment** and **inference** using [Ollama](https://ollama.com/).

---

## 🚀 Features

- **Efficient Fine-Tuning** – Uses **Unsloth** to significantly speed up training and lower memory usage.  
- **4-bit Quantization** – Creates a lightweight model without major performance loss.  
- **Local Deployment** – Easily run the fine-tuned model locally using **Ollama**.  
- **Customizable** – Modify training data and parameters to adapt the chatbot for any domain.  
- **Polite & Safe** – Includes examples to handle greetings and off-topic queries respectfully.

---

## 🛠️ Tech Stack

- **Base Model:** `unsloth/llama-3.1-8b-bnb-4bit`
- **Fine-Tuning Libraries:** Unsloth, Hugging Face `trl`, `peft`, `accelerate`, `bitsandbytes`
- **Deployment:** Ollama
- **Training Environment:** Google Colab (T4 GPU)

---

## ⚙️ Project Workflow

### 1. Fine-Tuning (Google Colab)
1. Prepare a **custom JSON dataset** (`data.json`) containing prompt-response pairs for customer support.
2. Load **Llama 3.1** and fine-tune it using **Unsloth** with **LoRA** (Low-Rank Adaptation).
3. Merge the fine-tuned adapter with the base model.
4. Export the model as a quantized **GGUF file**: `customer-support-model.gguf`.

### 2. Local Deployment (Ollama)
1. Download the `customer-support-model.gguf` file from Colab.
2. Create a `Modelfile` to define:
   - Model configuration
   - System prompt
   - Ollama parameters
3. Build and run the chatbot locally with Ollama.

---

## 📖 How to Use

### 1️ Clone the Repository

git clone <your-repository-url>
cd <your-repository-name>
**### 2. Fine-Tune the Model**
Open the provided Google Colab notebook.

Upload the data.json file to your Colab environment.

Run all the cells in the notebook. This will execute the fine-tuning process and generate the customer-support-model.gguf file.

Download the customer-support-model.gguf file and place it in the root directory of this repo

**### 3. Set Up and Run with Ollama**
Make sure Ollama is installed.
in terminal
ollama create customer-support -f Modelfile
ollama run customer-support

You can now interact with your custom-trained customer support assistant!
