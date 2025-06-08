# toy_transformer_sentiment

A minimal, self-contained demo of sentiment classification using DistilBERT.  
This project shows how to:

1. Subsample the SST-2 dataset to a tiny **40-example** train/validation split and a **200-example** test split  
2. Fine-tune a DistilBERT sentiment classifier on CPU  
3. Save and reload the resulting model  
4. Run interactive inference in Jupyter  

> **Note:** This is a *toy* example trained on only 40 examples due to limited compute. To build a production-quality classifier, fine-tune on the full SST-2 corpus (≈67 000 examples), use more epochs, larger batches, and (ideally) GPU acceleration.

---

## 📁 Repository Layout

toy_transformer_sentiment/
├── data/
│ ├── training.xlsx # 40-sample SST-2 train subset
│ └── test.xlsx # 200-sample SST-2 held-out test set
│
├── models/
│ └── distilbert_finetuned/ # Fine-tuned model & tokenizer files
│
├── fine_tune_toy_model.ipynb # Sample SST-2 → tokenise → fine-tune → save model
│
└── inference_toy_model.ipynb # Interactive inference with toy & official SST-2 models



---

## 🚀 Getting Started

1. **Clone the repo**  
   ```bash
   git clone https://github.com/iffatAGheyas/transformer-experiments.git
   cd transformer-experiments/toy_transformer_sentiment

2. Install dependencies

pip install transformers datasets torch pandas evaluate openpyxl

3. Launch Jupyter
jupyter lab
# or
jupyter notebook

Open the notebooks

fine_tune_toy_model.ipynb: walks through sampling SST-2, tokenisation, fine-tuning on 40 examples, and saving the model.

inference_toy_model.ipynb: lets you feed your own sentences and compare predictions from both the toy model and the official SST-2 DistilBERT checkpoint.

🗂 Data
data/training.xlsx: 40 sentences (20 positive, 20 negative) used for toy training & validation.

data/test.xlsx: 200 sentences (100 positive, 100 negative) held out for final evaluation.

💡 Extend This Demo
Swap in larger subsets (or the full SST-2 dataset) for training.

Increase num_train_epochs or per_device_train_batch_size when running on GPU.

Adapt the notebooks to other classification tasks (e.g. SST-5, IMDb, custom data).

For deeper background on Transformers and LLMs, see our wiki.
