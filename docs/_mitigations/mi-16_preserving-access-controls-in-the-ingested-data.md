---
sequence: 16
title: Preserving Access Controls in the Ingested Data
layout: mitigation
doc-status: Draft
type: DET
mitigates:
 - ri-3
---

When ingesting data to be queried using RAG architecture, the source may have defined different access levels boundaries that are lost in the destination vector storage.

The vector storage may support different access controls, which you should verify that they replicate the original source data ones.

Source data can be segregated in different replicated RAG architectures corresponding to different access level boundaries. Users of a specific domain can then only be permissioned to access the instance of the RAG that holds the data that they should have access to. If there are many different access levels, and resource consumption is a concern, you should consider concentrating them to a few flat levels that still serve the original security restrictions.

System prompt access control techniques are available, whereby a system prompt may be designed to build access controls into the RAG. This is ineffecient and has been to proved to be easily bypassed. So this should be avoided as a mechanism of developing access controls into the RAG architecture.

- segregating storage into diffent stores
- future integration points that may come in foundation model or vector store
- access control restrictions on the application


- If the vector storage supports access controls, you should verify that they replicate the original source data ones.
- Source data can be segregated in different repliacted RAG arquitectures, where users of a specific access domain only can access the version of the RAG that holds the data they should have access to.
- System prompt is an inneficient access control that can be bypassed, and should be avoided.
- In any case, a review of data ingested in the RAG and match with the users that have access to the RAG should yield there is no exfiltration possible.

In trying to preserve access controls in the ingested data the corporate access control should be replicated.
