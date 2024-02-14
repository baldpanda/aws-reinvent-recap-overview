# aws-reinvent-recap-overview

### Overview

Attended an AWS Reinvent Recap day where they went through some of the major releases in this year's ReInvent. The day was split into multiple tracks including ML & AI, Data and Serverless. I attended the ML & AI Talks as it was the most relevant. This was the agenda:

![overview](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/3b6f3d39-ec84-4c0b-b383-299bd1845277)

### Highlights

**Amazon Bedrock Knowledge Base**  - fully managed RAG workflow where the user can point to where the data is located in a bucket in S3, specify a vector database and AWS will build a RAG workflow for you. It handles the embedding of the data as well as the question answering aspect of the pipeline

**Amazon Q** - initially comes across as AWS’s version of ChatGPT, but it can be used in multiple areas within AWS management console and it looks like it is easy to use custom data easily as well as different URLs (currently max 100) to extend the underlying models capabilities to specific company use cases. It can respect access control so that if there are different user profiles who are interacting with a company’s instance of Q, the permissions of the users is respected by the model so that there isn’t accidental data leakage. It is a black box, so not sure what models are used underneath or the data used for the initial training. “Built on 17 years of Amazon experience“ 

**Amazon Bedrock Agents** - really good demo where the speaker built a multi-step agent which would use the Jira API for carrying out tasks on a Jira board. They eventually built a RAG system using a code base to pick up Jira tasks and suggest the required code changes to complete the task. The speaker made a blog post on it [here](https://makit.net/blog/bedrock-agents-and-knowledge-bases-part-2/)   


### General Notes - Bedrock

AWS have partnered with some of the leaders in the LLM space including Anthropic with Claude and Meta with Llama 2 providing a diverse suite of models. Models available in Bedrock:

![244A742E-DA8E-4622-B860-82F4A405578D](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/5c24590a-e692-456f-bebb-629d887425c8)


**Bedrock - Model Evaluation**

It is possible to evaluate the results of the foundational models against suitable metrics for a given task to do a comparison to decide which model performs best. Example metrics for a task such as text generation could include fairness, toxicity and accuracy. Model evaluation in Bedrock can be carried out automatically against open-source datasets including [Gigaword](https://huggingface.co/datasets/gigaword) and [BoolQ](https://huggingface.co/datasets/google/boolq) or through human workers such as SMEs or fellow employees

![B4388DC8-C23D-4047-9581-F0001151172B](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/ec4860eb-3e90-4688-9a68-c5bc32330736)

**Bedrock - Knowledge Bases**

Bedrock offers a managed RAG system abstracting away some of the operational complexity like setting up the embedding and inference pipelines, hosting the system and some of the maintenance overhead associated with such applications. 

![1869FFC6-EA65-49A4-A5C0-2D24C68EDAF3](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/261436b3-71d7-442b-b20d-df77b37345dc)

* It can be configured to collect data from an S3 bucket in one of the following formats:
  * Plain text (.txt)
  * Markdown (.md)
  * HyperText Markup Language (.html)
  * Microsoft Word document (.doc/.docx)
  * Comma-separated values (.csv)
  * Microsoft Excel spreadsheet (.xls/.xlsx)
  * Portable Document Format (.pdf)
 
* The data can be then be chunked, where the text is split into smaller chunks (common technique for improving the performance of such systems)

* A vector database must be configured for storing the embedded data. Supported vector databases:
  * Amazon OpenSearch Serverless
  * Amazon Aurora
  * Pinecone
  * Redis Enterprise Cloud

![D066CEB8-F165-4E90-B22E-069F829693D6](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/14231e1b-9b69-4311-aab9-f0e99d72f8da)

* The data can be ingested into the vector database (creating the knowledge base) using one of the following models for the embedding:
  * Titan G1 Embeddings - Text
  * Cohere Embed English
  * Cohere Embed Multilingual
 
* The data can then be updated through incremental syncing

* The RAG system can be called and through the AWS Management Console or through an API. Note that the models supported to query the knowledge base are:
  * Anthropic Claude Instant v1
  * Anthropic Claude v2.0
  * Anthropic Claude v2.1

The pricing of Bedrock Knowledge base is based on the cost of the individual components which it is made up of (hosting the vector DB, storage costs in S3, embedding the data and the token based pricing for the question answering LLM,...)

Overall, Knowledge base looks like a powerful tool to get a RAG system up and running quickly with minimal operational work. A potential downside is that it isn't model or vector DB agnostic. An example of where this might be detrimental is that if a more performant LLM was to come along, it might not be possible to use it. Similarly for the vector DB, it limits the options for different vendors and potentially locks the user in to certain technologies

Bedrock - Agents:

![CE641DF6-8009-4029-AAE5-3D81AFDB51BA](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/91e0f66f-f40b-4221-a318-be7cfcfc50c1)

Bedrock - Using Agents to build workflows:

![A39D6237-D655-48F7-82D6-7FB1A46AEAB5](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/07c6367f-a4ee-42c8-b60d-f4fffdf50e51)

Support for fine-tuning Claude coming soon

Agents automatically create prompts based on user input. This includes things like filtering out harmful content and queries

Agents can provide chain of thought reasoning on why they executed tasks in a certain way

AWS’s OpenSearch Vector DB can be expensive

### General Notes - Amazon Code Whisperer

Is similar to GitHub Copilot

Used in combination with Code Guru for identifying vulnerabilities in code base

Can be used directly in SageMaker and Lambda

Can run scans directly in IDE such as VS Code as well as CI pipeline

### General Notes - SageMaker

Host multiple models on a single inference endpoints for cost optimisation

Can productionise notebooks using pipelines and construct DAGs using them. Could be useful for things like data pre-processing

Canvas - no/low code tooling now supports Foundational models. Can use natural language for manipulating data

Clarify - supports explainability for foundational models such as metrics such as toxicity (responsible AI)

Can use decorators in AWS Python SDK for helping to productionise Data Science projects in SageMaker

Referenced Resources Mentioned 

[Frugal Architect](https://www.thefrugalarchitect.com/) - written by AWS CTO for building cost optimised applications

[Accelerate](https://www.amazon.co.uk/Accelerate-Software-Performing-Technology-Organizations/) - book on building lean software using DevOps principles
