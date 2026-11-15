# CS 4372: Assignment #4
## Assignment #4 - NLP Using Transformers
Teammates: **Taylor Mitchell** & **Dylan Ramdhan**

**Dataset:** [Frankenstein; or, The modern Prometheus by Mary Wollstonecraft Shelley](https://www.gutenberg.org/ebooks/84)

| Notebooks | NLP Tasks |
|---|---|
| `Summarization_and_Translation.ipynb` | Text Summerization |
| `Summarization_and_Translation.ipynb` | Machine Translation |
| `Chatbot.ipynb` | Question-Answering (Chatbot) on the Text |
| `TextGeneration.ipynb` | Text Generation Starting from a Seed Text from the Book |


### Summary:
In this assignment, we are using pre-trained transformer models from _Hugging Face_ to perform four NLP tasks on the book _Frankenstein; or, The Modern Prometheus by Mary Shelley_ from the [Project Gutenberg](https://www.gutenberg.org/) webpage.


### Where the Data Is Loaded From
The book is loaded directly from its Project Gutenberg URL, so no local paths are used:
```
https://www.gutenberg.org/cache/epub/84/pg84.txt
```
The pre-trained models download automatically from Hugging Face the first time they load. No login or API key is needed.

### How to Run the Code:
Files can be downloaded and run locally.

#### Requirements
- Python 3.10 or newer
- Packages (installed by the first code cell of each notebook):
  ```
  pip install "transformers[sentencepiece]<5" torch requests
  ```
- The summarization and translation have torch commented out because they were trained on local hardware using ROCm. When running those be sure to uncomment the pip install line.



### Assumptions:
- Project Gutenberg's header, license, and the book's table of contents were removed, keeping only the story text. All notebooks use the same cleaned text.
- All models are used as pre-trained, without further training on the book.
- The chatbot splits the book into fixed-size passages by word count, and is evaluated only on questions whose answers appear word-for-word in the text.