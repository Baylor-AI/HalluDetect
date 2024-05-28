# HalluDetect
Detecting Hallucinations in Large Language Model Generation: A Token Probability Approach. This repository includes the implementation of our method for training and evaluation of a Logistic Regression and MLP using features extracted with LLMs from text to classify it as an hallucination across different tasks.

# General Pipeline
Given a set of pairs of texts of the type (condition-text, generated-text) from an LLM (we will call it the LLM-Generator ($LLM_G$)), we extract four numerical features based on the generated tokens and vocabulary tokens probabilities from another LLM that we call the LLM-Evaluator ($LLM_E$).

# Datasets
Here, we list the three datasets we are using for experimentation and comparison.

## HaluEval
Hallucination Evaluation for Large Language Models (HaluEval) benchmark is a collection of generated and human-annotated hallucinated samples for evaluating the performance of LLMs in recognizing hallucinations. HaluEval includes 5,000 general user queries with ChatGPT responses and 30,000 task-specific examples (10,000 per task) from three tasks: question answering, knowledge-grounded dialogue, and text summarization. Hallucination Evaluation for Large Language Models (HaluEval) benchmark is a collection of generated and human-annotated hallucinated samples for evaluating the performance of LLMs in recognizing hallucinations. HaluEval includes 5,000 general user queries with ChatGPT responses and 30,000 task-specific examples (10,000 per task) from three tasks: question answering, knowledge-grounded dialogue, and text summarization. (https://aclanthology.org/2023.emnlp-main.397/) 

## HELM
Hallucination detection Evaluation for multiple LLMs (HELM) benchmark is a list of 3582 sentences from randomly sampling 50,000 articles from WikiText-103 where the selected LLMs were tasked with prompt-based continuation writing. The resulting sentences were annotated as hallucination or not. (https://arxiv.org/abs/2403.06448)

## True-False
Comprises 6,084 sentences divided in the topics of "Cities", "Inventions", "Chemical Elements", "Animals", "Companies", and "Scientific Facts". All of these sentences in each category are conformed of true statements and false statements. Unlike HaluEval, this dataset only has generated-text and does not include any condition-text. (https://aclanthology.org/2023.findings-emnlp.68.pdf)



