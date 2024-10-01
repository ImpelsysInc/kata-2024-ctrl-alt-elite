# ADR 02: Anonymizing the Resume for LLM Use and Candidate Matching

## Date:
2024-09-16

## Status:
Accepted

## Context

In the recruitment process, biases can impact both the AI-driven decision-making systems and human evaluators, ADR-04-LLM Fine tuningpotentially skewing the selection of candidates. To minimize such biases, it is essential to remove personal information (PI) from candidate resumes. This PI would be fenced off from any interaction with the LLM during the matching process and would only be revealed post-payment or upon explicit approval. This ensures a fairer evaluation based on skills and experience rather than identifiable characteristics.

## Decision:
To ensure anonymization of data, any resume uploaded or created through the system will contain PI that is tagged as metadata and never exposed to the LLM. Only non-PI data such as experience, skills, projects, and achievements will be processed for inference or fine-tuning tasks. A stateless, privacy-preserving LLM will be used to detect and filter out any personally identifiable information (PII), ensuring that only sanitized data reaches the AI engine. The stateless LLM will identify PII, which will then be redacted from the original resume. The redacted data will only be unlocked or accessed when required, such as during profile selection or payment.

![anonymizing-resume-flow.pg](images/Kata_ML%20-%20Resume%20Anonymization.png)
*Anonymization workflow for Candidate's Resume*

## Consequences
### Pros:
- **Increased Security and Privacy**: By using a stateless LLM, we can maintain compliance with regulations like GDPR and CCPA. The anonymization ensures that personal details are protected during the recruitment process.
- **Reduced Bias**: Removing PI data prevents potential biases in AI inference and human selection, leading to a fairer assessment of candidate skills and experience.
- **Scalability**: Using cloud-based stateless LLM services and integrating third-party redaction tools like [idox](https://www.idox.ai/products/redact) or [MarkLogic](https://docs.marklogic.com/guide/app-dev/redaction) ensures that the system can handle large-scale resume processing with minimal manual intervention.

### Cons:
- **Manual Oversight Required**: There is a risk that some sensitive information might not be correctly anonymized, leading to compliance issues. To address this, a moderation system is recommended for manually reviewing anonymized resumes. Feedback from this process can be used to improve the LLM's performance.
- **Additional Costs**: Using third-party redaction services and implementing a moderation layer might increase overall operational costs, especially if a high level of accuracy and compliance is needed across all resumes.
