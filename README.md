# Key Insight Extraction from Scientific Papers

# Introduction

This project is my Final Year Project for my BS in Computer Science at the University of the Punjab. The project was supervised by Dr. Zara Nisar. The project was completed in June 2023.

# Abstract

The exponential growth of scholarly papers presents a challenge for researchers to efficiently extract key insights from the vast corpus of knowledge. This study explores the use of Deep learning algorithms to automate the extraction of information from scientific articles, with a 
focus on structured abstracts, Citation analysis, and Named Entity Recognition. By categorizing abstract sentences into semantic headings and classifying citations based on their purpose, researchers can quickly locate relevant information. Named entity recognition further 
enhances understanding and contextualization of papers. The study utilizes datasets such as PubMed 200k RCT and SciCite for training and evaluation, employing models like Naïve Bayes, LSTM, CRF, Conv1D, Bi-GRU, and BERT. The results demonstrate the effectiveness of these techniques in improving information retrieval and extraction from scientific literature. The findings contribute to the development of more efficient tools for navigating and utilizing the extensive body of research papers across various disciplines.

# Dataset

## PubMed 200k RCT

The dataset used for this project is the [PubMed 200k RCT](https://github.com/Franck-Dernoncourt/pubmed-rct) dataset. The dataset contains 200,000 abstracts and 2.3 million sentences from Randomized Controlled Trials (RCTs). The dataset is divided into training, validation, and test sets. The dataset is annotated with 3 labels: background, objective, and methods. The dataset is annotated by 3 annotators. The dataset is used for training and evaluation of the models.

## SciCite

The dataset used for this project is the [SciCite](https://s3-us-west-2.amazonaws.com/ai2-s2-research/scicite/scicite.tar.gz) dataset. The dataset contains 11K manually annotated citation intents based on citation context in the computer science and biomedical domains. The dataset is annotated with 3 labels: background, method, and result. The dataset is used for training and evaluation of the models. 

## NER Dataset

The dataset used for this project is yet to be published. The dataset contains 60 manually annotated papers from the field of Computer Science. It contains 18768 sentences. The dataset is annotated with tags such as O, I-O_Result, I-O_Process, I-B_Process, B-O_Process, I-B_Problem, B-B_Process, I-O_Material etc. The dataset is used for training and evaluation of the models.

# Models

The models used for this project are as follows:

* Multinomial Naïve Bayes (This served as the baseline model)
* LSTM
* CRF
* Conv1D
* Bi-GRU
* BERT
* LSTM + CRF
* Bi-GRU + CRF
* Attention Bi-GRU
* BERT + Bi-GRU

# Results

## Results for SciCite

| Model | Accuracy | Precision | Recall | F1-score |
| --- | --- | --- | --- | --- |
| Naïve Bayes | 0.66 | 0.61 | 0.66 | 0.58 |
| Conv1D | 0.80 | 0.80 | 0.80 | 0.80 |
| Bi-GRU | 0.78 | 0.78 | 0.78 | 0.78 |
| Conv1D on Char Embeddings | 0.80 | 0.80 | 0.80 | 0.79 |
| Bi-GRU on Char Embeddings | 0.74 | 0.74 | 0.74 | 0.73 |
| BERT+Bi-GRU | 0.80 | 0.82 | 0.80 | 0.80 |
| USE Embeddings + Dense | 0.79 | 0.79 | 0.79 | 0.79 |
| BERT + Bi-GRU on Char and Token Embeddings | 0.85 | 0.85 | 0.85 | 0.84 |
| BERT + Bi-GRU on Char, Token and Positional Embeddings | 0.85 | 0.85 | 0.85 | 0.85 |

## Results for NER

| No of Tags | Model | Precision | Recall | F1-score |
| --- | --- | --- | --- | --- |
| 55 | LSTM | 0.17 | 0.12 | 0.13 |
| 55 | LSTM + CRF | 0.28 | 0.15 | 0.17 |
| 55 | CRF | 0.41 | 0.26 | 0.29 |
| 31 | LSTM | 0.31 | 0.22 | 0.24 |
| 31 | LSTM + CRF | 0.44 | 0.28 | 0.32 |
| 31 | CRF | 0.47 | 0.33 | 0.37 |
| 10 | LSTM | 0.55 | 0.38 | 0.44 |
| 10 | LSTM + CRF | 0.60 | 0.38 | 0.44 |
| 10 | CRF | 0.61 | 0.47 | 0.53 |
| 5 | LSTM | 0.69 | 0.64 | 0.66 |
| 5 | LSTM + CRF | 0.65 | 0.69 | 0.67 | 
| 5 | CRF | 0.71 | 0.63 | 0.67 |


## Results for PubMed 200k RCT

| Model | Accuracy | Precision | Recall | F1-score |
| --- | --- | --- | --- | --- |
| Naïve Bayes on Token Embeddings | 0.72 | 0.72 | 0.72 | 0.70 |
| Conv1D on Token Embeddings | 0.83 | 0.82 | 0.83 | 0.82 |
| USE+Dense on Token Embeddings | 0.76 | 0.76 | 0.76 | 0.76 |
| Conv1D on Char Embeddings | 0.70 | 0.72 | 0.70 | 0.70 |
| Bi-GRU Char Token Embeddings | 0.74 | 0.74 | 0.74 | 0.74 |
| BI-GRU on Token Embeddings | 0.82 | 0.83 | 0.82 | 0.82 |
| BERT on Token Embeddings | 0.79 | 0.78 | 0.79 | 0.78 |
| BI-GRU on USE+Char Embeddings | 0.75 | 0.74 | 0.75 | 0.74 |
| BI-GRU on USE+Char+positional Embeddings | 0.85 | 0.86 | 0.85 | 0.85 |
| BI-GRU on Token+Char+Positional | 0.88 | 0.88 | 0.88 | 0.88 |
| BI-GRU on Token+Char+Positional On All data | 0.92 | 0.92 | 0.91 | 0.92 |

# Limitations

* The dataset used for NER was small. 
* There were not enough resources to train the models on the entire dataset of PubMed 200k RCT. BERT couldn't even be trained on just the 20k dataset.
* The models were trained on a single GPU.
* The models were trained for a limited number of epochs.
* The models were trained on a limited number of hyperparameters.

# Conclusion

The results demonstrate the effectiveness of these techniques in improving information retrieval and extraction from scientific literature. The findings contribute to the development of more efficient tools for navigating and utilizing the extensive body of research papers across various disciplines.

