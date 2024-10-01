# ADR 06: Fine-Tuning LLM for Resume Feedback and Candidate Matching

## Date:
2024-09-16

## Status:
Accepted

## Context:

The current LLM, although effective in providing general feedback and matching, lacks specificity when addressing domain-specific knowledge, such as reasons for resume selection or rejection provided by HR professionals. Additionally, the system requires mechanisms to address data drift and ensure it adapts to evolving industry feedback. Regular updates via a survey feedback loop will help maintain relevance and prevent model degradation over time.

## Decision:

In order to enhance both the resume feedback system and the candidate-job profile matching process, fine-tuning the existing LLM is crucial. 

To achieve this, we will fine-tune the LLM on datasets that include HR feedback on selected and rejected resumes. This will allow the model to offer more relevant and tailored feedback based on real-world insights. Moreover, fine-tuning with datasets from job descriptions and successfully matched candidate profiles will enhance the accuracy of candidate-job matching.

Anonymized resumes and HR feedback, including reasons for acceptance or rejection, will be collected as the training datasets. Fine-tuning will be carried out using Supervised Fine-Tuning (SFT) for smaller LLMs or QLoRA for larger LLMs. Cloud services like Azure (for OpenAI models) or AWS (for Claude models) will be leveraged to optimize resource efficiency and scalability.

## Consequences:

### PROS:
  - Improved accuracy by mitigating model drift.
  - Greater understanding of industry-specific nuances.
  - More tailored feedback and candidate recommendations, aligning with actual hiring standards.
  
### CONS:
  - Fine-tuning LLMs can be computationally intensive and time-consuming, requiring significant resources.
  - There is a risk of overfitting, particularly if the model becomes too focused on a specific set of profiles or job roles.
  
### RISKS:
  - Anonymization of data is critical to ensure compliance with GDPR/CCPA regulations during model training. Stringent measures must be in place to protect personal and sensitive information.
