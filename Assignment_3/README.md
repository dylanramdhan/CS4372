# CS 4372: Assignment #3
## Assignment #3 - Deep Learning with Keras
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

[ASSIGNMENT INSTRUCTIONS](Assign3_Instructions.pdf) <br>
[ASSIGNMENT REPORT](REPORT3.pdf)

**Colab Notebook:** [Open in Google Colab](PASTE_YOUR_PUBLIC_COLAB_LINK_HERE) <br>
**Dataset:** [Dog Breed Identification](https://www.kaggle.com/competitions/dog-breed-identification) (Kaggle)

| Notebook | Task |
|---|---|
| `CS4372_Assignment_3.ipynb` | Performing _Feature Extraction_ and _Fine-Tuning_ to the _Dog Breed Identification_ |


### Summary
In this assignment, we are exploring Deep Learning using Keras (Transfer Learning). This project builds an image classifier that identifies a dog's breed from a photo, using Kaggle's Dog Breed Identification dataset (10,222 labeled images across 120 breeds, split 70% / 15% / 15% into training, validation, and test sets). Rather than training a model from scratch, it uses transfer learning with a MobileNetV2 base pre-trained on ImageNet, in two stages: feature extraction, where the base is frozen and only a new classification head is trained, and fine-tuning, where the top layers of the base are unfrozen and trained at a much lower learning rate. Six experiments compared data augmentation, learning rate, dropout, and the number of unfrozen layers, with every decision based on validation accuracy. The final model, fine-tuned on its top 30 layers, reached 76.9% test accuracy. Built in Google Colab with TensorFlow/Keras; the dataset is downloaded at runtime through the Kaggle API.


### How To Run The Code
**One-time setup:**
1. Create a free account at [kaggle.com](https://www.kaggle.com).
2. Accept the [competition rules](https://www.kaggle.com/competitions/dog-breed-identification/rules) (**Join Competition** / **Late Submission**). Without this, the download fails with a 403 error.
3. In Kaggle, go to **Settings → API → Create New Token**. This downloads `kaggle.json`, which holds your `username` and `key`.

**Running the notebook:**
1. Open the Colab link above (**File → Save a copy in Drive** to run your own copy).
2. Set **Runtime → Change runtime type → T4 GPU**.
3. Run cell **0.0**. When the Kaggle login box appears, enter the `username` and `key` from `kaggle.json`.
4. Run all remaining cells in order. A full run takes about *20–30* minutes.

#### Requirements
- [Google Colab](https://colab.research.google.com/) with a **T4 GPU**
- A free [Kaggle](https://www.kaggle.com) account and API token (see *How to Run*)
- Packages (installed by the first code cell of the notebook):
```
pip install --upgrade kagglehub
```
  All other libraries (TensorFlow/Keras, NumPy, Pandas, Matplotlib, scikit-learn) come pre-installed in Colab.

#### Origin of Data
The data is downloaded directly from Kaggle at runtime using the `kagglehub` package (Cell 1.1.), so no local file paths are used and the dataset is not included in this submission. Since this is a Kaggle **competition** dataset, downloading it requires a Kaggle account and API token.


### Assumptions
- Only the labeled `train/` images (*10,222*) are used, because the competition's `test/` images have no labels.
- The labeled images are split *70/15/15* into training, validation, and test sets (stratified by breed), giving *7,155 / 1,533 / 1,534* images.
- Images are resized to *160 × 160* and loaded in batches of *32*.
- All hyperparameter choices are based on validation accuracy. The test set is evaluated only once, on the final model.
- Random seeds are fixed (`SEED = 42`), so results should closely match the saved outputs. Small differences can come from GPU computation.
- The notebook creates a `dog_split/` folder and a `best_feature_extraction.weights.h5` file inside the Colab session. Both are temporary and not part of the submission.