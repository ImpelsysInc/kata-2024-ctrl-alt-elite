# ADR 03: Use of Vector Database

## Date:
2024-09-30

## Status:
Accepted

## Context:
In a resume feedback system, users provide details about their experiences, skills, personal achievements, or projects. To offer targeted feedback and enhance a candidate’s chance of success in job applications, we aim to reference the best resumes within a given domain. This requires efficient semantic search at scale to ensure high accuracy when matching relevant documents across various roles like IT, Design, and Engineering, each of which follows different resume structures and sections.

## Decision:

We have decided to implement a [Vector Database](https://doi.org/10.48550/arXiv.2005.11401) integrated with a Retrieval-Augmented Generation (RAG) system. This decision allows for efficient retrieval of semantically similar resumes through vector embeddings, ensuring close matches are identified. The RAG system, supported by large language models (LLMs) with a deep understanding of job openings and hiring processes, facilitates context-aware feedback generation and candidate matching to job descriptions.


![vector-db-data-store.png](images/Kata_ML%20-%20Document%20Storage%20Processing.png)
*Resume or Job Description data can be stored in the Vector Database*


The system should enable easy addition, updating, and deletion of resumes. By chunking resumes, we ensure they fit within the token limits of the LLM while maintaining the context. The Vector Database retrieves data in real time, utilizing distributed parallelization and [similarity calculation](https://dl.acm.org/doi/10.5555/645925.671516), which can be seamlessly integrated into any LLM downstream task. This will provide real-time, streaming data responses, significantly enhancing user experience on the platform.

![candidate-resume-feedback-item.png](images/Kata_ML%20-%20Resume%20Creation%20Feedback.png)
*Integrating the Vector DB in a RAG based feedback architechture*

We expect the system to process resumes with clearly defined sections (e.g., Experience, Skills, Achievements) and job descriptions divided into segments like Role Description, Experience, and Responsibilities.


## Consequences:
### PROS:

- **High Responsiveness**: Real-time matching of candidates and streaming feedback responses make the system suitable for near-instantaneous interactions.
- **Personalized Feedback**: The system provides feedback tailored to individual resumes, aligning suggestions with industry expectations and examples of successful resumes.
- **Scalability**: The vector database can handle large-scale datasets, making it efficient for serving numerous candidates and resumes simultaneously.
- **Data Consistency**: By using current LLM tokenization, the system maintains context-rich documents, ensuring data consistency.

### CONS:
- **Computational Intensity**: The vector search process and LLM-driven RAG inference are resource-intensive, especially when operating at scale.
- **Versioning and Embedding Consistency**: Managing different versions of embeddings—particularly when a superior model emerges—and ensuring consistency across updated or recalculated vectors (resumes) can present challenges.
