# ADR 04: Use of Knowledge Graph

## Date:
2024-09-30

## Status:
Accepted

## Context:
In the resume feedback or candidate matching system to Job Descriptions (JD), we plan to leverage a Large Language Model (LLM) with strong knowledge of the hiring domain. However, LLMs often suffer from hallucinations or may fail to detect relationships that are not explicitly mentioned but require inference, particularly after a candidate’s resume or an HR job posting has been submitted.

## Decision:
We have decided to implement a [Knowledge Graph](https://doi.org/10.1109/TNNLS.2021.3070843) (KG) for identifying and leveraging the entities, attributes, and relationships present in resumes and job descriptions. A KG can be used in conjunction with a Retrieval-Augmented Generation (RAG) system as the data source. This ensures efficient retrieval, defining relationships between experiences, skills, and job roles. The embeddings and relational mappings in the KG enable a deeper understanding of resumes and job postings.

![storing-data-in-kg.png](images/Kata_ML%20-%20Document%20Storage%20Processing.png)
*Storing data in entity-relation format to Knowledge Graph(KG)*

We will extract keywords and relations to create a richer context for entity-based resume matching, leading to more precise, context-driven feedback generation via RAG. 

![job-matching-phase.png](images/Kata_ML%20-%20Candidate%20Matching%20Flow.png)
*Use of KG with LLM and Vector DB to provide matching profiles*

We recommend utilizing cloud-based Neo4j instances, distributed across multiple deployment zones, to accommodate the exponential growth of graph data. Additionally, cloud storage resources can be optimized using context-dense embeddings to efficiently manage space.

We expect the system to extract and batch various entities and relationships from resume sections and job descriptions, which will then be saved as KG embeddings.

## Consequences:

### PROS:
- **High Accuracy:** The KG is grounded in real-world knowledge, minimizing hallucinations from the LLM and boosting accuracy.
- **Observability:** The KG models explicit relationships (e.g., job-required skills) and infers implicit ones (e.g., certain skills could imply leadership), leading to more personalized feedback and relevant matching.
- **Performance:** A graph database can handle large-scale data with low latency, delivering high performance for multiple requests.
- **Explainability:** The KG's outputs provide real-time data for clear understanding of LLM downstream tasks, reducing the "black box" nature of AI and offering performance metrics.

### CONS:
- **Data Consistency:** Maintaining an up-to-date KG requires ongoing updates since relationships between skills, industries, and job roles evolve.
- **Resource Requirements:** As data is added, the KG grows exponentially. In large-scale systems with millions of resumes and job descriptions, the cloud resources required can significantly increase overall costs.
