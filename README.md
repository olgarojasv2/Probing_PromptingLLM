# Probing & Prompting LLM #

## Part 1
### Research Question

The initial question posed—*“Is an LLM’s internal representation of a story closer to the book or the movie version?”*—is quite broad. To refine it, we propose the following research question:

**How do LLM-generated representations of a story compare to its book and movie adaptations in terms of textual and semantic similarity?**

This refined question allows for measurable comparisons using textual and semantic similarity metrics.

## Research Outline

### 1. Data Collection
- Obtain the full text of the following Twilight book series Breaking Dawn, New Moon, Eclipse in plain text format.
- Extract movie scripts or transcripts for corresponding sections.
- Preprocess both datasets by removing character names, formatting inconsistencies, and non-dialogue elements.

### 2. Data Segmentation
- Extract passages where key characters (e.g., Edward, Jacob, Bella, wedding, marriage) are involved in important dialogue.
- Align similar scenes from book and movie based on plot structure.

### 3. Measuring Similarity
Two approaches were applied to compare book and movie dialogue:

#### **A. TF-IDF + Cosine Similarity**
- **Method:** Transform book and movie passages into numerical vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**.
- **Comparison:** Compute **cosine similarity** to measure textual overlap.
- **Output:** Extract and rank the most and least similar book-movie passage pairs.

#### **B. SBERT (Sentence-BERT) + Cosine Similarity**
- **Method:** Convert passages into dense vector embeddings using **SBERT**, which captures deeper semantic meaning.
- **Comparison:** Compute cosine similarity between book and movie embeddings.
- **Output:** Rank the top and bottom similar book-movie passage pairs.

### 4. Visualization & Interpretation
A histogram was generated to show the **distribution of similarity scores**, providing insight into whether book and movie dialogues are closely aligned or diverge significantly.

**Example Results:**
- **Top 5 Most Similar Matches** had a cosine similarity score above 0.10, showing strong textual or semantic overlap.
- **Bottom 5 Least Similar Matches** had much lower scores, highlighting significant differences between book and movie versions.

### 5. Experiment with Open-Source LLM
- Generate LLM responses to selected book/movie scenes.
- Compare the generated responses with both book and movie versions.
- Analyze whether the LLM’s response aligns more with the book or movie adaptation.

### 6. Limitations & Ethical Considerations
- **Subjectivity in scene alignment:** Some book passages may not have direct movie counterparts.
- **Paraphrasing in adaptations:** Movies often condense or rewrite dialogue.
- **LLM biases:** The model may favor one medium based on its training data.
- **Legal & Ethical Review:** The legal department ensures compliance with copyright when using book and movie excerpts. The student annotator assists in evaluating the accuracy of LLM-generated responses.

### Conclusion
By using both **textual (TF-IDF) and semantic (SBERT) similarity metrics**, we can quantitatively assess whether an LLM aligns more with books or movies. Preliminary results suggest that while movies simplify dialogue, key themes and phrases remain recognizable. The LLM’s output will provide further insight into which medium it models more closely.

---------------------------------------------------------------------------------------------------
## Part 2

# Genre Annotation with Ollama

## Overview

This repository provides an approach for genre annotation of song lyrics using **Ollama**, a large language model, through Zero-Shot and Few-Shot prompting strategies. By leveraging **Ollama**'s ability to classify text into predefined categories, we can automatically predict the genre of a given set of lyrics.

The following genres are considered for classification:
- **Rock**
- **Pop**
- **Hip-Hop**
- **Electronic**
- **R&B**
- **Country**
- **Jazz**
- **Metal**
- **Indie**
- **Folk**

## Files

- **genreLyrics.csv**: A CSV file containing the song lyrics and their corresponding genre labels.
- **Annotator_Ollama.py**: Python script for performing genre annotation using **Ollama**.

## Requirements

- **Pandas** library for data manipulation.
- **Ollama** Python API for interacting with the language model. // Model Llama3

## Evaluation

Use Precision, Recall, and F1 Score to evaluate the model's performance.

## Classification Report

### Zero-Shot Classification Report

| Category   | Precision | Recall | F1-Score |
|------------|-----------|--------|----------|
| Electronic | 0.00      | 0.00   | 0.00     |
| Hip-Hop    | 0.67      | 0.67   | 0.67     |
| Indie      | 0.00      | 0.00   | 0.00     |
| Pop        | 0.17      | 0.33   | 0.22     |
| Rock       | 0.00      | 0.00   | 0.00     |
| unknown    | 0.00      | 0.00   | 0.00     |

Accuracy: 0.20

Macro Average: Precision 0.14, Recall 0.17, F1-Score 0.15

Weighted Average: Precision 0.17, Recall 0.20, F1-Score 0.18


### Few-Shot Classification Report

| Category   | Precision | Recall | F1-Score | 
|------------|-----------|--------|----------|
| Electronic | 0.00      | 0.00   | 0.00     | 
| Hip-Hop    | 0.67      | 0.67   | 0.67     |
| Pop        | 0.00      | 0.00   | 0.00     |
| Rock       | 0.33      | 0.50   | 0.40     |
| unknown    | 0.00      | 0.00   | 0.00     |

Accuracy: 0.33

Macro Average: Precision 0.20, Recall 0.23, F1-Score 0.21

Weighted Average: Precision 0.27, Recall 0.33, F1-Score 0.29

## Discussion

### Which strategy worked better?
The Few-Shot strategy generally works better because it leverages a few labelled examples, improving classification performance compared to Zero-Shot.

### Did the model struggle with specific genres?
Yes, genres such as Indie, Electronic, and Pop were difficult for the model, especially when there were fewer examples or a lack of context in the prompts.

### How could performance be improved?

Few-Shot performance could improve by adding more representative examples for underperforming genres.

Zero-Shot might benefit from adjusting the prompt to be more explicit or providing more guidance on genre distinctions.
