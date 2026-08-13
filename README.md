# Intelligent Chunking Strategies For Document Extraction
<p align="center">
  <strong>August 15, 2026</strong> &nbsp;|&nbsp; 
  <strong>Leila Wolfe</strong> &nbsp;|&nbsp; 
  <strong>5-minute read</strong>
</p>

## Introduction
Document extraction is the process of pulling structured information from a body of text. Typically, a body of text will be processed into raw text and passed through an LLM to obtain specific terms. In the case of a legal document, these terms can include termination date and effective date. However, these documents can span hundreds of pages. When passed to an LLM, may get truncated due to token limits, and extraction may be incorrect or incomplete.

To prevent truncation, a document can be chunked into smaller sections. However, randomly chunking documents can result in missing critical information. For example, if a legal clause spans 5 pages but the chunk size is only 4 pages long, the entire context will be missed when the LLM is inferring or summarizing during extraction. Additionally, legal documents can sometimes contain multiple types of language that should be treated differently. For example, legal language and pricing tables could exist within the same document. If the same prompt is utilized for two different types of language, the extraction process could result with hallucinations. For instance, a pricing table will not have a termination date entity, but the model may hallucinate a date regardless. Instead of setting a hard page per chunk cut off, we can apply other chunking strategies to avoid LLM token limits, truncation, and missing context.

<figure align="center">
  <img src="./assets/Screenshot 2026-08-11 213526.png" alt="view cloud traces" width="800"/>
  <figcaption><em>Figure 1: Overview of LLM Document Extraction</em></figcaption>
</figure>

## Strategies

### Overlapping Chunks
When setting a hard chunk size, the full context required to infer or summarize may be lost. One way to circumvent this is to allow for a certain amount of text overlap between chunks. This may result in redundant information and higher cost.

```python
add python code that shows example of how to add overlapping chunk code

```

### Chunking by Type
A document can contain multiple types of information such as legal language, tables or signed off emails. When the LLM is provided a schema for extraction - the instructions for terms that must be pulled - it is particularly susceptible to hallucinations, even if the prompts states to fill in NA values for information not found in the source. It is best to omit terms not present in a document to avoid false extractions. 
