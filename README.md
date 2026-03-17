# 🧠 Bengali Empathetic Conversational AI

### Fine-Tuning LLaMA-3.1-8B with LoRA & Unsloth

Fine-tuning the **LLaMA-3.1-8B-Instruct** model to generate **empathetic Bengali conversational responses** using **LoRA** and **4-bit quantization** on Kaggle GPU.



# 📌 Project Overview

Mental health and emotional support systems often lack coverage for **low-resource languages such as Bengali**.

This project fine-tunes a large language model to:

* Understand **emotional Bengali queries**
* Generate **empathetic responses**
* Support **conversational mental-health contexts**

Training is performed using **parameter-efficient fine-tuning (LoRA)** to reduce GPU memory requirements.



# ⚙️ Model Configuration

| Parameter           | Value                 |
| ------------------- | --------------------- |
| Base Model          | LLaMA-3.1-8B-Instruct |
| Fine-Tuning Method  | LoRA                  |
| Training Library    | Unsloth               |
| Quantization        | 4-bit                 |
| Max Sequence Length | 8192                  |
| GPU                 | Kaggle T4             |



# 🔧 LoRA Configuration

| Parameter      | Value                                                         |
| -------------- | ------------------------------------------------------------- |
| Rank (r)       | 16                                                            |
| Alpha          | 32                                                            |
| Dropout        | 0                                                          |
| Target Modules | q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj |

LoRA enables efficient fine-tuning by adapting a **small subset of parameters** while keeping the **original model weights frozen**.


## 🏗 System Architecture

The training pipeline follows a modular **Object-Oriented design**.

```
DatasetProcessor
      ↓
LLAMAFineTuner
      ↓
Evaluator
      ↓
Experiment Logger
```

### Components

**DatasetProcessor**

* Dataset preprocessing
* Prompt formatting
* Train/validation split

**LLAMAFineTuner**

* Load base LLM
* Apply LoRA adapters
* Train the model

**Evaluator**

* Generate responses
* Compute evaluation metrics

**Experiment Logger**

* Track experiments
* Store model results



# 🧾 Prompt Template

Each training example uses an **instruction-style prompt**.

```
<|begin_of_text|>
<|system|>
আপনি একজন সহানুভূতিশীল বাংলা সহকারী।

<|user|>
Topic: {topic}
Title: {title}
Question: {question}

<|assistant|>
{answer}
<|end_of_text|>
```

This structure helps the model learn **empathetic conversational behavior**.



# 📊 Training Configuration

| Parameter             | Value |
| --------------------- | ----- |
| Batch Size            | 1     |
| Gradient Accumulation | 16    |
| Learning Rate         | 2e-4  |
| Training Steps        | 200   |
| Logging Steps         | 10    |
| Checkpoint Interval   | 50    |



# 📈 Evaluation Metrics

| Metric          | Score  |
| --------------- | ------ |
| Training Loss   | 0.3867 |
| Validation Loss | 0.9417 |
| Perplexity      | 2.56   |
| BLEU            | 0    |
| ROUGE           | 0    |



# 💬 Example Inference

### Input

```
Topic: দুঃখ  
Title: একাকীত্ব  
Question: আমি খুব একা অনুভব করছি।
```

### Generated Response

```
আমি বুঝতে পারছি আপনি খুব একা অনুভব করছেন। 
এমন অনুভূতি অনেক সময় খুব কষ্টকর হতে পারে। 
আপনি যদি চান, আপনার অনুভূতির কথা আরও বলতে পারেন—আমি শুনতে এখানে আছি।
```


# 📂 Repository Structure

```
llama-bengali-empathetic-chatbot/
│
├── notebooks/
│   └── llama_finetuning.ipynb
│
├── outputs/
│   ├── LLAMAExperiments.csv
│   ├── GeneratedResponses.xlsx
│   └── human_evaluation_table.xlsx
│
└── README.md
```



# 📊 Experiment Tracking

Two datasets store experiment results.

### LLAMAExperiments

| id | model_name | lora_config | train_loss | val_loss | metrics | timestamp |

### GeneratedResponses

| id | input_text | response_text | timestamp |

---

# 🔮 Future Work

* Human evaluation of empathy quality
* Larger Bengali conversational datasets
* Chatbot deployment (API / Web interface)
* Model compression for real-time inference



# 📜 License

This project is for **research and educational purposes**.


⭐ If you found this project useful, consider **starring the repository**.
