# Fine-Tuning-BERT-for-Movie-Review-Classification-with-PEFT-and-LoRA

**Project Overview**

This project focuses on sentiment classification of movie reviews using a fine-tuned BERT model. We leverage the IMDB dataset, a collection of movie reviews labeled as positive or negative. To enhance efficiency, we employ advanced techniques like Parameter-Efficient Fine-Tuning (PEFT) and Low-Rank Adaptation (LoRA).

**Introduction**

Sentiment analysis aims to determine the emotional tone expressed in text. In this project, we train a BERT model to accurately classify movie reviews as either positive or negative. The IMDB dataset provides a valuable resource for this task, offering a large collection of labeled movie reviews.

**Novel Techniques**

* **Parameter-Efficient Fine-Tuning (PEFT):** PEFT methods significantly reduce the number of trainable parameters during fine-tuning. This is crucial for optimizing training time and resource utilization, especially when dealing with large models like BERT. 
* **Low-Rank Adaptation (LoRA):** LoRA is a prominent PEFT technique. It introduces trainable low-rank matrices to the original model weights. This allows for efficient adaptation by training only these smaller matrices, while the majority of the original model weights remain frozen.

**LoRA Configuration**

* **Rank (r):** 4 
* **lora_alpha:** 32
* **lora_dropout:** 0.01
* **target_modules:** ['q_lin']

This specific LoRA configuration defines the key hyperparameters that control the behavior of the low-rank adaptation process.

**Model Training**

* **Data Preparation:**
    * The IMDB dataset is loaded and split into training and validation sets.
    * The dataset is tokenized using the BERT tokenizer, preparing the text data for the model's input.
* **Model Initialization:**
    * We utilize the pre-trained `distilbert-base-uncased` model, a smaller and faster version of BERT, specifically designed for sequence classification tasks.
    * The model's output is mapped to two classes: "Positive" and "Negative."
* **Training Configuration:**
    * **Learning Rate:** 1e-3
    * **Batch Size:** 4
    * **Number of Epochs:** 1
    * **Evaluation:** The model is evaluated at the end of each epoch to track performance.
    * **Saving:** The model is saved at the end of each epoch to preserve the best-performing checkpoints.
* **Training Process:**
    * The model is fine-tuned using the `Trainer` API provided by the Hugging Face Transformers library, facilitating efficient training and evaluation.
