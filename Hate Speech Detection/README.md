## Hate Speech Detection

Ethos is a dataset containing phrases labelled as hate speech or not hate speech. This dataset was class imbalanced, which is why I prompted GPT-3 to generate training examples for the minority class.

I did get a warning from GPT-3 because of the nature of my prompt and the output (hate speech) it generated haha 

For every one of my experiments, the dataset (original + GPT-3 generated) has been split 75/15/10 into training, validation & test sets. I've pre-set my code to automatically select the best performing model based on the validation loss. I also used the Tesla T4 GPUs on Colab for training & inference. Code to avoid RAM Overflow has also been added.

Note that I've used the default Sequence Classification Heads for all models, with their default loss functions. Another possible way to go about this is after fine tuning, discard the classification heads & extract the fine tuned sentence embeddings (average pool the token embeddings) and then use them with a more spohisticated downstream classifier (HDBSCAN, Kernel SVM, etc.)

The following hyperparameter settings were constant throughout all experiments across different transformers for better comparison:

num_epochs = 3

weight_decay = 0.01

batch_size = 8

warmup_steps = 500

Following are the Large Language Models (LLMs)/ Transformers I fine tune from HuggingFace for Sequence Classification.

1. DistilBERT:

Average F-1 Score : 0.77

Recall on Hate Speech : 0.93 (Pretty Good !)

2. DistilRoBERTa:

Average F-1 Score : 0.76

Recall on Hate Speech : 0.89 (Pretty Good !)

3. RoBERTa-base:

Average F-1 Score : 0.73

Recall on Hate Speech : 0.62

4.AlBERT-base-v2:

Average F-1 Score : 0.73

Recall on Hate Speech : 0.69
