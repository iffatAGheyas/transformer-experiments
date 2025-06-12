Transformer Experiments

This repository contains two lightweight transformer-based pipelines, each built under limited computational resources. Both toy models demonstrate core methodologies—tokenisation, architecture setup, training, and inference—that can scale to high performance when provided with larger datasets and more compute.

For theory of Transformers and Large Language Models (LLMs), see our wiki.

1. Toy Sentiment Classification

Directory: toy_transformer_sentiment/

A simple pipeline using a distilled BERT model to classify sentences as positive or negative.

toy_transformer_sentiment/

data/

training.xlsx    ← 40-sample SST-2 train subset

test.xlsx        ← 200-sample SST-2 held-out test set

.ipynb_checkpoints/  ← Jupyter auto-save files (ignore/delete)

fine_tune_toy_model.ipynb    ← Notebook: subsample SST-2, tokenise, fine-tune on 40 examples

inference_toy_model.ipynb    ← Notebook: interactive inference with toy & official SST-2 models

README.md            ← This folder’s documentation

Note: This toy DistilBERT trains on just 40 examples (with 200 test examples) due to CPU constraints. With a full GPU setup and the complete SST-2 dataset, fine-tuning yields state-of-the-art accuracy on sentiment classification.

2. Audio Spectrogram Transformer

Directory: audio_spectogram_transformer/

An end-to-end Jupyter notebook pipeline for environmental sound classification using a compact Audio Spectrogram Transformer (TinyAST) on the ESC-50 dataset.

audio_spectogram_transformer/

audio_transformer_pipeline.ipynb   ← Main notebook: download, preprocess, train, evaluate, inference

data/

raw/

ESC-50-master/

audio/                  ← 2000 raw .wav clips

meta/                   ← esc50.csv metadata

processed/                      ← .npy spectrograms + metadata.csv

model/

tiny_ast_esc50.pth             ← Saved TinyAST weights

README.md                          ← This folder’s documentation

Note: This model trains on ~400 examples across 50 classes for only 5 epochs (CPU-only), resulting in limited accuracy. With more data, longer training, and GPU acceleration, the same attention-based approach can achieve strong performance on audio classification.

Getting Started

Clone the repository:
