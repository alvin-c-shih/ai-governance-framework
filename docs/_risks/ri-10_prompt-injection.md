---
sequence: 10
title: Prompt Injection
layout: risk
doc-status: Draft
type: SEC
external_risks:
  - LLM01
  - LLM04
  - LLM06
  - LLM10
---

Users of the application or malitious internal agents can craft prompts that are sent to the SaaS-based LLM and potentially cause damaging responses. This is one of the most popular attack vectors as privilage requirements for this attach vector are the lowest [^1][^2]. Unlike SQL injection the scope of attack in prompt injection is wider and can result in incorrect answers, toxic responses, information disclosure, denial of service, unethical and biased responses. A good example of an incident in public is the DPD chatbot [^3]. 

There are two popular approachs of **Direct Prompt Injection** (also known as "Jailbreaking") where a user tries to escape the underlying behaviour of the system to get access to data store or inappropriate responses putting the reputation of the company at risk. **Indirect Prompt Injection** seeks to hijack other user's sessions and direct them or other systems (if part of a component) to actions or impact critical decision making that might result in other attack vectors including privilage esculation. Please note that this risk exists even without an active prompt injection attack as badly designed systems hallucinate directing users to actions that can be harmful to the organization. This is particlally invisible if the prompt is part of a component of the decision making system and not directly interacting with users where there is no human in the loop. 

Additionally attacks can profile systems due to access to internal data and inner working with a model inversion to reveal the model's internal workings, which can be used to steal the model's training or RAG data.

References
* [^1] OWASP Top 10 for LLM Applications - https://owasp.org/www-project-top-10-for-large-language-model-applications/assets/PDF/OWASP-Top-10-for-LLMs-2023-v1_1.pdf
* [^2] Mitre Prompt Injection - https://attack.mitre.org/techniques/T1055/
* [^3] DPD Chatbot Swears at Customer - BBC - https://www.bbc.co.uk/news/technology-68025677
