# An Experimental Study of Adaptive Chunking and Context Filtering in RAG

## Overview

This project presents an experimental study of how adaptive chunking and context filtering influence the accuracy and efficiency of a Retrieval-Augmented Generation (RAG) system.

Four configurations are implemented and compared to understand the individual and combined effects of these techniques without additional model training.

## Research Objectives

- Compare fixed-size and adaptive chunking strategies.
- Evaluate the effect of context filtering on retrieved information.
- Measure answer accuracy and retrieval performance.
- Analyze prompt-token usage and response time.
- Study the trade-offs between answer quality and system efficiency.

## Technologies Used

| Component | Technology |
|---|---|
| Programming Language | Python |
| Development Environment | Google Colab |
| Dataset | SQuAD Validation Dataset |
| Embedding Model | all-MiniLM-L6-v2 |
| Language Model | google/flan-t5-small |
| Vector Index | FAISS |
| Deep Learning Framework | PyTorch |
| Libraries | Hugging Face Transformers, Sentence Transformers, Pandas, NumPy |

## Experimental Configuration

The experiment uses 300 questions from the SQuAD validation dataset.

| Parameter | Configuration |
|---|---|
| Fixed Chunk Size | 128 tokens |
| Fixed Chunk Overlap | 20 tokens |
| Adaptive Chunking | Content-based boundaries, maximum 128 tokens |
| Retrieval | Top-5 |
| Context Filtering Threshold | 0.35 |
| Maximum Generated Tokens | 64 |

## Four RAG Configurations

1. **Fixed + No Filter:** Fixed-size chunking without context filtering.
2. **Adaptive + No Filter:** Adaptive chunking without context filtering.
3. **Fixed + Filter:** Fixed-size chunking with context filtering.
4. **Adaptive + Filter:** Adaptive chunking with context filtering.

## Evaluation Metrics

- **Exact Match (EM):** Measures exact matching between generated and reference answers.
- **F1 Score:** Measures token-level overlap between generated and reference answers.
- **Faithfulness Proxy:** Uses lexical overlap to estimate answer support from retrieved context.
- **Retrieval Hit Rate:** Measures successful retrieval before context filtering.
- **Average Prompt Tokens:** Measures the average number of input tokens per question.
- **Average Response Time:** Measures the average time taken to generate an answer.

## Experimental Results

| Configuration | Exact Match (%) | F1 (%) | Faithfulness Proxy (%) |
|---|---:|---:|---:|
| Fixed + No Filter | 38.00 | 48.31 | 95.17 |
| Adaptive + No Filter | **51.33** | **60.82** | 95.93 |
| Fixed + Filter | 38.00 | 48.32 | 94.72 |
| Adaptive + Filter | 50.33 | 60.30 | **96.27** |

### Efficiency Comparison

| Configuration | Avg. Tokens | Response Time (s) |
|---|---:|---:|
| Fixed + No Filter | 603.26 | 0.143 |
| Adaptive + No Filter | 566.48 | 0.150 |
| Fixed + Filter | 589.23 | 0.151 |
| Adaptive + Filter | **541.27** | **0.138** |

### Key Findings

- Adaptive chunking without filtering achieved the highest Exact Match and F1 scores.
- Adaptive chunking with filtering achieved the highest faithfulness proxy score.
- Context filtering reduced average prompt-token usage.
- The adaptive configurations achieved higher retrieval hit rates than the fixed configurations.

## How to Run

1. Clone or download this repository.
2. Open `RAG_Experiment.ipynb` using Google Colab.
3. Install the required libraries if they are not already available.
4. Run the notebook cells in sequence.
5. View the generated results, tables, and graphs.

## Limitations

- The experiment uses a limited set of 300 SQuAD validation questions.
- Results depend on the selected embedding and language models.
- Faithfulness is measured using a lexical-overlap proxy rather than a dedicated semantic evaluation method.
- Only fixed and adaptive chunking with two filtering conditions are compared.

## Future Work

- Evaluate the approach using larger and more diverse datasets.
- Explore query refinement techniques.
- Compare advanced filtering methods such as cross-encoder reranking.
- Evaluate larger language and embedding models.
- Include human evaluation.

## Research Paper

**Title:** An Experimental Study of Adaptive Chunking and Context Filtering in Retrieval-Augmented Generation.

The research paper provides the detailed methodology, experimental setup, results, discussion, and conclusions.

## Author

Add your name, university affiliation, and contact information here.
