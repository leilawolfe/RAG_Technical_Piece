# Intelligent Chunking Strategies For Document Extraction
<p align="center">
  <strong>August 11, 2026</strong> &nbsp;|&nbsp; 
  <strong>Leila Wolfe</strong> &nbsp;|&nbsp; 
  <strong>5-minute read</strong>
</p>

## Introduction
Document extraction is the process of pulling structured information from a body of text. Typically, a body of text will be processed into raw text and passed through an LLM to obtain specific terms. In the case of a legal document, these terms can include termination date and effective date. However, these documents can span hundreds of pages. When passed to an LLM, may get truncated due to token limits, and extraction may be incorrect or incomplete.

To prevent truncation, a document can be chunked into smaller sections and passed to the llm.

<figure align="center">
  <img src="./assets/Screenshot 2026-08-11 213526.png" alt="view cloud traces" width="800"/>
  <figcaption><em>Figure 1: Overview of LLM Document Extraction</em></figcaption>
</figure>

## 
