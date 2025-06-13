# Audio Spectrogram Transformer

An end-to-end Jupyter notebook pipeline for environmental sound classification using a lightweight Audio Spectrogram Transformer (TinyAST) on the ESC-50 dataset.

---

## 📁 Project Structure

```text
audio_spectogram_transformer/
├── audio_transformer_pipeline.ipynb   # Main notebook
├── README.md                          # This file
└── data/
    ├── raw/                          # Raw ESC-50 repository (wav + metadata)
    │   └── ESC-50-master/
    │       ├── audio/                # 2000 audio clips
    │       └── meta/                 # esc50.csv metadata
    └── processed/                    # Generated .npy spectrograms + metadata.csv
```

---

## 🚀 Quickstart

1. **Clone the repo**

   ```bash
   git clone <your-repo-url> audio_spectogram_transformer
   cd audio_spectogram_transformer
   ```

2. **Install dependencies** (CPU-only example):

   ```bash
   pip install torch torchvision transformers librosa pandas numpy matplotlib
   ```

3. **Launch the notebook**:

   ```bash
   jupyter notebook audio_transformer_pipeline.ipynb
   ```

4. **Run each cell** in order:

   * Download & verify ESC-50
   * Preprocess audio → mel-spectrogram `.npy`
   * Train TinyAST (5 epochs, fixed 64×64 inputs)
   * Evaluate on 10-sample hold-out test set
   * (Optional) Batch inference on any WAVs under `data/test/`

---

## 📊 Data Details

* **ESC-50**: A public benchmark of 2,000 labelled environmental audio clips (5 s each) across 50 classes (e.g. dog bark, rain, clock tick).
* **Preprocessing**: Clips are resampled to 16 kHz, converted to 64-bin mel-spectrograms, log-scaled and normalised per-clip, then saved as `.npy` for fast loading.

> **Note:** For CPU-only experimentation we process a limited subset (\~400 clips for training + 10 hold-out), and train only 5 epochs.
> This yields low accuracy on 50 classes, but the methodology scales with more compute and data.

---

## 🛠️ Pipeline Overview

1. **Dataset Download**: Clone the ESC-50 GitHub repository if missing.
2. **Preprocessing**: Generate normalised mel-spectrograms & metadata CSV.
3. **Model Definition**: TinyAST — a compact Vision Transformer adapting spectrograms to 64×64 patches.
4. **Training**: 5 epochs on CPU, Adam optimizer, cross-entropy loss.
5. **Evaluation**: 10-sample hold-out test, print actual vs predicted labels.
6. **Batch Inference** (optional): Predict on WAVs in `data/test/`.

---

## 🔧 Customisation

* Adjust **hyperparameters** (learning rate, batch size, epochs) in the notebook.
* Swap in your own audio dataset by placing WAVs under `data/raw/` and updating metadata paths.
* For larger training runs, enable GPU by installing the appropriate CUDA build of PyTorch.

---

## 🙏 Acknowledgements

* **ESC-50** dataset by Karol J. Piczak: [https://github.com/karolpiczak/ESC-50](https://github.com/karolpiczak/ESC-50)
* **Hugging Face Transformers** for the Vision Transformer backbone.

---

## 📄 License

This project is licensed under the MIT License. Feel free to adapt and extend for your own research or portfolio.
