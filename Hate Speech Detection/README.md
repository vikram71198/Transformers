Ethos is a dataset containing phrases labelled as hate speech or not hate speech. This dataset was class imbalanced, which is why I prompted GPT-3 to generate training examples for the minority class.

Following are the Large Language Models (LLMs)/ Transformers I fine tune from HuggingFace for Sequence Classification.

I did get a warning from GPT-3 because of the nature of my prompt and the output (hate speech) it generated haha 

For every one of my experiments, the dataset (original + GPT-3 generated) have been split 75/15/10 into training, validation & test sets. I've pre-set my code to automatically select the best performing model based on the validation loss.

1. DistilBERT:

num_epochs = 3

weight_decay = 0.01

batch_size = 8

warmup_steps = 500

Average F-1 Score : 0.77

Recall on Hate Speech : 0.93 (Pretty Good !)

You can find the fine tuned model [here](https://drive.google.com/drive/folders/18TTJ2KVJcMdWKXYJcYRz1fCr4kzDDVEn)
