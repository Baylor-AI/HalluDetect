# HalluDetect
Detecting Hallucinations in Large Language Model Generation: A Token Probability Approach. This repository includes the implementation of our method for training and evaluation of a Logistic Regression and MLP using features extracted with LLMs from text to classify it as an hallucination across different tasks. In this Readme we explain the implementation and how to use our code. However, at the end of the Readme you can find our paper which contains exteneded explanation in the theory and all the results.

# General Pipeline
Given a set of pairs of texts of the type (condition-text, generated-text) from an LLM (we will call it the LLM-Generator ($LLM_G$)), we extract four numerical features based on the generated tokens and vocabulary tokens probabilities from another LLM that we call the LLM-Evaluator ($LLM_E$).

# Datasets
Here, we list the three datasets we are using for experimentation and comparison.

## HaluEval
Hallucination Evaluation for Large Language Models (HaluEval) benchmark is a collection of generated and human-annotated hallucinated samples for evaluating the performance of LLMs in recognizing hallucinations. HaluEval includes 5,000 general user queries with ChatGPT responses and 30,000 task-specific examples (10,000 per task) from three tasks: question answering, knowledge-grounded dialogue, and text summarization. Hallucination Evaluation for Large Language Models (HaluEval) benchmark is a collection of generated and human-annotated hallucinated samples for evaluating the performance of LLMs in recognizing hallucinations. HaluEval includes 5,000 general user queries with ChatGPT responses and 30,000 task-specific examples (10,000 per task) from three tasks: question answering, knowledge-grounded dialogue, and text summarization. (https://aclanthology.org/2023.emnlp-main.397/) 

The dataset is stored in this repository in the `./HaluEval/data` path.

## HELM
Hallucination detection Evaluation for multiple LLMs (HELM) benchmark is a list of 3582 sentences from randomly sampling 50,000 articles from WikiText-103 where the selected LLMs were tasked with prompt-based continuation writing. The resulting sentences were annotated as hallucination or not. (https://arxiv.org/abs/2403.06448)

The dataset is stored in this repository in the ./helm path.

## True-False
Comprises 6,084 sentences divided in the topics of "Cities", "Inventions", "Chemical Elements", "Animals", "Companies", and "Scientific Facts". All of these sentences in each category are conformed of true statements and false statements. Unlike HaluEval, this dataset only has generated-text and does not include any condition-text. (https://aclanthology.org/2023.findings-emnlp.68.pdf)

The dataset is stored in this repository in the `./true-false-dataset` path.

# Code Explanation
Currently we only have three notebooks with all the implementation necessary for each dataset. We intend in future commits to have the version of the three noteboks and a .py implementation with less code repetition. A more detailed explanatio of each notebooks is on the comments of the code and each cell. Each notebook is dependent on which dataset we were evaluating, however the models and experimentation code is the same which is a repetition we would like to remove. However, on the other hand if you want to experiment with different models and experimentation pipeline the three notebooks might be a better fit.

Next we will summarize the main sections of code in each notebook that are common. The differences are in how we read the datasets and build the training and testing sets. 

## Models
We implemented a `LLMModel` class that includes the common code for each LLM. The main code in this class is the feature extraction given a condition-text and a generated-text.

## Experimentation and Evaluation
- First you will see a group of cells that process the training dataset, pass it to the $LLM_E$ and extracts the four features (or the features you selected) and then we train a Logistic Regression (LR) using sklearn and report accuracy. Next, using the same LR trained we evaluate it in validation set if used and a test set.

- Then we have an implementation of the SNN model and the evaluation code with the metrics used and training pipeline that we execute in the same training, validation and testing set.

# How to Run our code?
Is as simple as running the notebooks until the end. Each notebook has an explanation of the cell and comments in the code, however feel free to contact us for any questions and changes.
Currently the notebooks already contain the paths based on this repository file system, so you shouldn't have to change the paths, unless you want to store the datasets in different paths. Also, be aware that the first configurations are intended in case you run it in Colab, but if you are running in a different environment or local you might need to edit the first cell of each notebook.

# Reference





