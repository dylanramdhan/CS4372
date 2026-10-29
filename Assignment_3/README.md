# CS 4372: Assignment #3
## Assignment #3 - Deep Learning with Keras
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

**Colab Notebook:** [Open in Google Colab](PASTE_YOUR_PUBLIC_COLAB_LINK_HERE) <br>
**Dataset:** [Dog Breed Identification](https://www.kaggle.com/competitions/dog-breed-identification) (Kaggle)

## Summary
In this assignment, we are exploring Deep Learning using Keras (Transfer Learning). This project builds an image classifier that identifies a dog's breed from a photo, using Kaggle's Dog Breed Identification dataset (10,222 labeled images across 120 breeds, split 70% / 15% / 15% into training, validation, and test sets). Rather than training a model from scratch, it uses transfer learning with a MobileNetV2 base pre-trained on ImageNet, in two stages: feature extraction, where the base is frozen and only a new classification head is trained, and fine-tuning, where the top layers of the base are unfrozen and trained at a much lower learning rate. Six experiments compared data augmentation, learning rate, dropout, and the number of unfrozen layers, with every decision based on validation accuracy. The final model, fine-tuned on its top 30 layers, reached 76.9% test accuracy. Built in Google Colab with TensorFlow/Keras; the dataset is downloaded at runtime through the Kaggle API.

## Where the Data Is Loaded From
The data is downloaded directly from Kaggle at runtime using the `kagglehub` package (Cell 1.1.), so no local file paths are used and the dataset is not included in this submission. Since this is a Kaggle **competition** dataset, downloading it requires a Kaggle account and API token.

## How To Run The Code

### One-time setup
1. Create a free account at [kaggle.com](https://www.kaggle.com).
2. Go to the [competition rules page](https://www.kaggle.com/competitions/dog-breed-identification/rules) and accept the rules (**Join Competition** / **Late Submission**). Without this, the download fails with a 403 error.
3. In Kaggle, go to **Settings → API → Create New Token**. This downloads `kaggle.json`, which contains your `username` and `key`.

### Running the notebook
1. Open the Colab link above (**File → Save a copy in Drive** to run your own copy).
2. Set **Runtime → Change runtime type → T4 GPU**.
3. Run cell **0.0**. A Kaggle login box appears; enter the `username` and `key` from `kaggle.json`, and wait for *"Kaggle credentials successfully validated."*
4. Run the remaining cells in order (**Runtime → Run cell and below** from Cell 1.1.).

The only package installed by the notebook is `kagglehub` (Cell 0.0.); all other libraries (TensorFlow/Keras, NumPy, Pandas, Matplotlib, scikit-learn) come pre-installed in Google Colab. A full run takes about **~20–30 minutes** on a T4 GPU.

## Notes
- Random seeds are fixed (`SEED = 42`), so results should closely match the saved outputs; small differences can occur from GPU computation.
- The test set is evaluated only once (Cell 7.1.), on the final model.
- The notebook creates a `dog_split/` folder and a `best_feature_extraction.weights.h5` file inside the Colab session; both are temporary and are not part of the submission.
