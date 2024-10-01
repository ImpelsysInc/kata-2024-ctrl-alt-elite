# ADR 05: Re-Ranking the matched documents for resume feedback and job matching.

## Date:
2024-09-16

## Status:
Accepted

## Context:
In a resume and job listing system, there can be thousands or even millions of documents. For any given candidate or HR job posting, there could be hundreds of matching profiles. Given this abundance of data, the LLM might become overwhelmed by the sheer number of relevant documents, leading to difficulties in generating effective feedback or matching profiles. To ensure that only the most relevant profiles are evaluated while filtering out low-relevancy content, a re-ranking mechanism is essential.

## Decision:
We have decided to implement a re-ranking system that efficiently reduces the number of documents to be processed by the LLM, while still preserving the quality of the results. The re-ranking system will consist of two methods:

1. **Weeding out low-relevancy documents:** A thresholding or top-n approach will be used to discard documents that fall below a defined relevancy/similarity score, ensuring only the more relevant ones remain.
2. **Identifying high-relevancy documents:** Once the lower-relevancy documents have been eliminated, the system will further analyze the remaining high-relevancy documents using LLM-based relevance analysis to identify the most contextually accurate profiles or feedback candidates.

We recommend deploying the re-ranking system on a cloud-based infrastructure capable of handling distributed parallelization for scalability. For low-latency needs, integrating the re-ranking process with distributed search engines or using in-memory data processing frameworks like Redis can further enhance performance.

### Alternative:
In cases where a lightweight re-ranking system is required, using simpler TF-IDF or BM25 algorithms for the initial document filtering may provide a faster, though less nuanced, alternative.

## Consequences:

### PROS:
- **Efficiency:** The re-ranking system ensures that only the most relevant documents are processed by the LLM, significantly reducing computational load and speeding up feedback generation or candidate matching.
- **Accuracy:** By removing low-relevancy documents and focusing on those with high relevancy scores, the system can deliver more targeted feedback and better matches.
- **Scalability:** The use of thresholding and top-n filtering scales well, even when dealing with millions of documents.

### CONS:
- **Complexity:** Implementing both threshold-based filtering and LLM-based relevancy analysis adds layers of complexity to the system, which may require more maintenance and fine-tuning over time.
- **Resource Intensive:** While the re-ranking reduces the overall number of documents sent to the LLM, the second phase of high-relevancy analysis using the LLM itself can still be computationally expensive, especially for large datasets.

