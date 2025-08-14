#Fine-Tuned Llama 3.1 Customer Support Chatbot
This project demonstrates how to fine-tune the Llama 3.1 8B model on a custom dataset for a specific task: a customer support chatbot. The fine-tuning process is optimized using Unsloth for faster training and lower memory usage in a Google Colab environment. The final model is then packaged for local deployment and inference using Ollama.
🚀 Features
Efficient Fine-Tuning: Leverages Unsloth to significantly speed up the training process and reduce GPU memory requirements.
4-bit Quantization: Uses 4-bit quantization to create a lightweight model without a major loss in performance.
Local Deployment: Easily run the fine-tuned model on your local machine using Ollama.
Customizable: The training data and model parameters can be easily modified to adapt the chatbot for different domains and tasks.
Polite & Safe: The training data includes examples for handling greetings and off-topic questions in a respectful manner.
🛠️ Tech Stack
Base Model: unsloth/llama-3.1-8b-bnb-4bit
Fine-Tuning Libraries: Unsloth, Hugging Face trl, peft, accelerate, bitsandbytes
Deployment: Ollama
Training Environment: Google Colab (with T4 GPU)
⚙️ Project Workflow
The project is structured into two main stages:
Fine-Tuning (in Google Colab):
A custom JSON dataset (data.json) containing prompt-response pairs for customer support is prepared.
The Llama 3.1 model is loaded and fine-tuned using the Unsloth library and LoRA (Low-Rank Adaptation).
The fine-tuned adapter is merged with the base model and exported as a single, quantized GGUF file (customer-support-model.gguf).
Local Deployment (with Ollama):
The GGUF model file is downloaded from Colab.
A Modelfile is created to define the model's configuration, system prompt, and parameters for Ollama.
Ollama builds a new local model from the GGUF file and the Modelfile.
The final chatbot is run locally via the command line.
📖 How to Use
To replicate this project, follow these steps:
1. Clone the Repository
git clone <your-repository-url>
cd <your-repository-name>


2. Fine-Tune the Model
Open the provided Google Colab notebook.
Upload the data.json file to your Colab environment.
Run all the cells in the notebook. This will execute the fine-tuning process and generate the customer-support-model.gguf file.
Download the customer-support-model.gguf file and place it in the root directory of this repository.
3. Set Up and Run with Ollama
Make sure you have Ollama installed on your local machine.
Open your terminal and navigate to the repository's root directory.
Create the Ollama model using the following command:
ollama create customer-support -f Modelfile


Once the model is created, run the chatbot:
ollama run customer-support


You can now interact with your custom-trained customer support assistant!
