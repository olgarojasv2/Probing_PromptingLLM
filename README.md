# Research Proposal: Investigating LLM's Internal Representation of Stories

## Research Question

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
