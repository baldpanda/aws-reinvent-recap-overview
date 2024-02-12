# aws-reinvent-recap-overview

### Overview

Attended an AWS Reinvent Recap day where they went through some of the major releases in this year's ReInvent. The day was split into multiple tracks including ML & AI, Data and Serverless. I attended the ML & AI Talks as it was the most relevant. This was the agenda:

![overview](https://github.com/baldpanda/aws-reinvent-recap-overview/assets/37364932/3b6f3d39-ec84-4c0b-b383-299bd1845277)

### Highlights

**Amazon Bedrock Knowledge Base**  - fully managed RAG workflow where the user can point to where the data is located in a bucket in S3, specify a vector database and AWS will build a RAG workflow for you. It handles the embedding of the data as well as the question answering aspect of the pipeline

**Amazon Q** - initially comes across as AWS’s version of ChatGPT, but it can be used in multiple areas within AWS management console and it looks like it is easy to use custom data easily as well as different URLs (currently max 100) to extend the underlying models capabilities to specific company use cases. It can respect access control so that if there are different user profiles who are interacting with a company’s instance of Q, the permissions of the users is respected by the model so that there isn’t accidental data leakage. It is a black box, so not sure what models are used underneath or the data used for the initial training. “Built on 17 years of Amazon experience“ 

**Amazon Bedrock Agents** - really good demo where the speaker built a multi-step agent which would use the Jira API for carrying out tasks on a Jira board. They eventually built a RAG system using a code base to pick up Jira tasks and suggest the required code changes to complete the task. The speaker made a blog post on it [here](https://makit.net/blog/bedrock-agents-and-knowledge-bases-part-2/)   



### General Notes - Bedrock



Models available in Bedrock





Bedrock - Model Evaluation





Bedrock - Knowledge Bases





Bedrock - Native Support Vector Databases



Bedrock - Agents



Bedrock - Using Agents to build workflows

Support for fine-tuning Claude coming soon

Agents automatically create prompts based on user input. This includes things like filtering out harmful content and queries

Agents can provide chain of thought reasoning on why they executed tasks in a certain way

AWS’s OpenSearch Vector DB is expensive (minimum $700 per month)

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

  - written by AWS CTO for building cost optimised applications

Accelerate - book on building lean software using DevOps principles
