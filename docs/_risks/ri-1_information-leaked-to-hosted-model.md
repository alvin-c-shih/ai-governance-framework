---
sequence: 1
title: Information Leaked To Hosted Model
layout: risk
doc-status: Draft
type: RC
owasp-llm_references:
  - llm06-2025  # OWASP LLM: Excessive Agency
nist-ai-600-1_references:
  - 2-4    # NIST AI 600.1: Data Privacy
  - 2-9    # NIST AI 600.1: Information Security
ffiec_references:
  - ffiec_sec_ii-information-security-program-management
  - ffiec_sec_iii-security-operations
  - ffiec_ots_risk-management
eu-ai-act_references:
  - c3-s2-a10  # III.S2.A10 Data and Data Governance
  - c3-s2-a13  # III.S2.A13 Transparency and Provision of Information to Deployers
  - c5-s2-a53  # V.S2.A53 Obligations for Providers of General-Purpose AI Models
---
## Summary

Using third-party hosted large language models (LLMs) introduces a significant risk of sensitive information disclosure, as data transmitted for inference may be retained or exposed through model behaviors like overfitting, memorization, and prompt-based attacks. Without robust data sanitization, access controls, and clear terms of use, proprietary or personally identifiable information (PII) may be inadvertently leaked to unauthorized users. These risks are especially pronounced in free or inadequately governed LLM services, where data handling practices may lack transparency and safeguards.

## Description

With many GenAI applications using third-party hosted LLMs, there is the potential for sensitive data to be transmitted to the third-party platform for inference, posing a risk of information leakage. Sensitive organizational data, proprietary algorithms, and confidential information may be unintentionally exposed due to inadequate control measures within the hosted model. This can occur through several mechanisms unique to Large Language Models (LLMs), as outlined in OWASP's LLM06, such as [overfitting](https://aws.amazon.com/what-is/overfitting/), [memorization](https://arxiv.org/pdf/2310.18362), and [prompt-based attacks](https://owasp.org/www-project-llm-prompt-hacking/).

LLMs can retain data from training processes or user interactions, potentially recalling sensitive information during unrelated sessions, a phenomenon known as "memorization" When data such as Personally Identifiable Information (PII) or proprietary financial strategies enter the model, the risk of inadvertent disclosure rises, particularly when insufficient data sanitization or filtering mechanisms are in place. Additionally, adversarial actors could exploit prompt injection attacks to manipulate the model into revealing sensitive data. 

Furthermore, data retention policies or model fine-tuning can exacerbate these risks. When fine-tuning is done on proprietary data without strict access control, sensitive information may inadvertently be disclosed to lower-privileged users, violating principles of least privilege. Without clear Terms of Use, data sanitization, and input validation, the organization loses visibility into how sensitive information is processed by the LLM and where it may be disclosed.

It is, however, important to understand distinct risk vectors between commercial/enterprise-grade and free hosted LLMs. For instance, commercial LLMs like ChatGPT offer a "Memory" setting to manage what the system is allowed to memorize from your conversations and Data controls to restrict what can be used to train their models. Additionally, enterprise-grade LLMs will usually sanitize sensitive data when used in organizational environments and often include stringent terms of use related to the handling of your data inputs and outputs that must first be accepted before interacting with the model. Free hosted LLMs, on the other hand, may use your data to train their models without you explicitly knowing that it is happening. Thus, you must always exercise due diligence when interacting with hosted LLM services to better understand how your input and output data is being used behind the scenes.


### Key Risks 

- **Two-Way Trust Boundary**: The client-to-LLM interaction introduces a two-way trust boundary where neither input nor output can be fully trusted. This makes it critical to assume the output could leak sensitive information unintentionally, even when the input appears benign.
- **Model Overfitting and Memorization**: LLMs may retain sensitive data introduced during training, leading to unintentional data leakage in future interactions. This includes potential cross-user leakage, where one user's sensitive data might be disclosed to another.
- **External Inference Endpoint Risks**: Hosted models may not provide transparent mechanisms for how input data is processed, retained, or sanitized, increasing the risk of persistent exposure of proprietary data.

This risk is aligned with OWASP’s [LLM06: Sensitive Information Disclosure](https://genai.owasp.org/llmrisk/llm06-sensitive-information-disclosure/), which highlights the dangers of exposing proprietary or personally identifiable information (PII) through large-scale, externally hosted AI systems.

## Links

- [FFIEC IT Handbook](https://ithandbook.ffiec.gov/)
- [Scalable Extraction of Training Data from (Production) Language Models](https://arxiv.org/abs/2311.17035)
