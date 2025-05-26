---
sequence: 14
title: Encrypt Data at Rest
layout: mitigation
doc-status: Draft
type: PREV
mitigates:
  - ri-12
---

Encrypting data at rest involves converting stored information into a secure format using encryption algorithms, making it inaccessible without the proper decryption key. This process protects sensitive data from unauthorized access or breaches, even if the storage medium is compromised. It is considered standard practice, with many tools and organizations turning this feature on by default across their IT estate and third-party tools.

Despite this being standard practice, it is still a notable control within the context of LLM applications. New technologies and techniques move at pace, driven initially by features. Sometimes suitable security measures are lacking. More specifically, vector data stores, which are a relatively recent area of research and development, may lack this feature. 

#### Potential Tools and Approaches

This can be done in many ways, either as part of an existing cloud infrastructure utilising tools like Azure’s [AI Search](https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search) vector store or [AWS OpenSearch](https://aws.amazon.com/opensearch-service/). Both provide an extensive range of services well suited to the implementation of a RAG system.

It is also possible to turn this from an issue of managing secure access at rest to utilising a service that turns the problem into making a secure API call such as with [Pinecone](https://docs.pinecone.io/home). Which provides high level security and authentication services alongside serverless, low latency hosting. 

In a case where you don’t want to introduce a cloud infrastructure service or use an API system you could use a self hosted system like FTP using a service such as [Redis](https://redis.io/docs/latest/develop/get-started/rag/) to create the vector database for your RAG system to access. In such a setup it is important to make sure that your private server is set up securely, e.g, using adequate authentication through ssh keys. In the case of using a larger cloud service you are able to delegate this responsibility.

Another tool available is [FAISS](https://faiss.ai/) which provides in runtime storage and access to various algorithms which provide efficient similarity searches across your vectors. Even though FAISS runs in-memory and is limited to the system's available memory, it also offers persistence export options as well. However, If FAISS is used in-memory mode only without persistence, this reduces the data breach risk significantly.
