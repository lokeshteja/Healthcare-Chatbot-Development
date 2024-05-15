# Healthcare Chatbot Development

## Overview
This project involves developing a healthcare chatbot using the open-source large language model: mistralai/Mistral-7B-v0.1). The chatbot is fine-tuned on a healthcare dataset (lavita/ChatDoctor-HealthCareMagic-100k) and responds to user queries. The project includes data preprocessing, model fine-tuning, chatbot interface development, and performance evaluation.

## Project Structure
- `medical_chat.ipynb`: Main script of the project
- `requirements.txt`: List of dependencies.
- `mistral-chat-doctor-finetune/checkpoint-500`: Directory to save model checkpoints.
- `healthcare_llm`: Directory to save model checkpoints.
- `evaluation`: Directory to save evaluation results.

## Prerequisites
Ensure you have the following installed:
- Python 3.10 or higher
- PyTorch
- Transformers library from Hugging Face
- Datasets library from Hugging Face
- Gradio for the chatbot interface
- Additional libraries as listed in `requirements.txt`

## Setup and Installation

### Clone the Repository
```bash
git clone https://github.com/lokeshteja/Healthcare-Chatbot-Development
cd Healthcare-Chatbot-Development
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

## Summary of Approach and Challenges

## Dataset

I used the ChatDoctor-HealthCareMagic-100k dataset, containing around 110K+ rows of patient queries and doctor responses. For this project, I sampled 5000 rows for training and evaluation.

## Formatting and Tokenizing

I formatted the dataset into a specific structure to be fed into the LLM and tokenized it using Huggingface’s `AutoTokenizer`. The input format includes patient queries and doctor responses, with padding tokens added to the beginning of the sequence.

## Model Initialization with QLoRA

I used quantized low rank adaptation (QLoRA) to load the model in 4-bit mode, significantly reducing memory usage without sacrificing performance.

## PEFT and LoRA Configuration

Then further used Parameter Efficient Fine-Tuning (PEFT) and LoRA to freeze most of the model parameters and fine-tune a small subset. This allows efficient fine-tuning even with limited data and computational resources.

## Training

I trained the model for 500 steps, saving checkpoints along the way.

## Evaluation

I evaluated the model using BLEU, ROUGE, and METEOR scores to assess the quality of the generated responses compared to the reference answers.

## Usage

The fine-tuned model can be used to generate responses to medical queries through a user-friendly interface built with Gradio.



## Example Queries for the Chatbot
Here are some example queries you can try with the chatbot:
- "Hi Doctor, my sugar level is 220 what to do?"
- "I am feeling sick after travel and my body is hot what might be reason?"
- "How should I control my thyroid levels?"

## Fine-tuned model uploaded on Hugging Face - Lokesh477/healthcare_llm

## Response example generated by the model
![image.png](attachment:image.png)

<img width="1042" alt="Screenshot 2024-05-14 at 10 13 28 PM" src="https://github.com/lokeshteja/Healthcare-Chatbot-Development/assets/28762945/62899879-6d1f-4085-96da-80be4e758fa6">
