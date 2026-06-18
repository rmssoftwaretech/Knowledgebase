# AWS Samples Knowledge Base Article

## Overview
`aws-samples` is a GitHub organization and ecosystem of reference implementations that demonstrate how to use AWS services in practical scenarios. These repositories are intended to accelerate learning, prototyping, and implementation.

## When to Use AWS Samples
- You need a working reference architecture for an AWS service.
- You want starter code for a proof of concept.
- You are validating best practices for infrastructure, security, or deployment patterns.
- You want to compare implementation approaches across languages and frameworks.

## How to Find Relevant Samples
1. Go to the AWS Samples GitHub organization.
2. Search by service or use case (for example: `serverless`, `lambda`, `cdk`, `analytics`, `generative-ai`).
3. Review repository activity, open issues, and README quality before adopting.
4. Prefer samples that include clear setup instructions and architecture diagrams.

## Evaluation Checklist Before Adoption
- **Maintenance**: Is the repository actively maintained?
- **Security**: Are dependencies current and are secrets excluded?
- **Cost Awareness**: Does the sample mention estimated AWS costs?
- **Operational Fit**: Does it match your runtime, region, and compliance requirements?
- **License**: Confirm license compatibility with your project.

## Recommended Adoption Process
1. Fork or clone the sample repository.
2. Read the full README and architecture notes.
3. Deploy first in a sandbox AWS account.
4. Replace placeholder credentials with secure IAM roles and parameter stores.
5. Add organization standards (logging, monitoring, tagging, CI/CD controls).
6. Document deviations from the original sample for future maintainers.

## Common Risks and Mitigations
- **Risk**: Copying sample code directly to production.  
  **Mitigation**: Treat samples as a baseline and perform security/performance reviews.
- **Risk**: Unexpected cloud cost during experimentation.  
  **Mitigation**: Apply budget alarms and clean up resources after testing.
- **Risk**: Outdated dependencies or patterns.  
  **Mitigation**: Run dependency scanning and align with current AWS guidance.

## Summary of LangChain, RAG, and LangGraph Projects in AWS Samples

### LangChain-focused Projects
- **[generative-ai-amazon-bedrock-langchain-agent-example](https://github.com/aws-samples/generative-ai-amazon-bedrock-langchain-agent-example)**  
  Demonstrates a production-style conversational agent using Amazon Bedrock, LangChain, Amazon Lex, DynamoDB memory, and Kendra-backed retrieval.
- **[langchain-agents](https://github.com/aws-samples/langchain-agents)**  
  Provides TypeScript-based LangChain agent examples and patterns for tool-enabled agents on AWS.

### RAG-focused Projects
- **[rag-using-langchain-amazon-bedrock-and-opensearch](https://github.com/aws-samples/rag-using-langchain-amazon-bedrock-and-opensearch)**  
  Shows end-to-end RAG with Bedrock, Titan embeddings, and OpenSearch vector engine, including ingestion and query flows.
- **[amazon-bedrock-rag-workshop](https://github.com/aws-samples/amazon-bedrock-rag-workshop)**  
  Hands-on workshop covering core RAG patterns such as semantic search, metadata filtering, summaries, and re-ranking.

### LangGraph-focused Projects
- **[langgraph-agents-with-amazon-bedrock](https://github.com/aws-samples/langgraph-agents-with-amazon-bedrock)**  
  Workshop with notebook labs on LangGraph agent design patterns including planning, tool use, memory, and human-in-the-loop.
- **[sample-agentic-frameworks-on-aws](https://github.com/aws-samples/sample-agentic-frameworks-on-aws)**  
  Collection of agentic reference implementations on AWS, including LangGraph examples and multi-agent orchestration patterns.

## References
- AWS Samples on GitHub: https://github.com/aws-samples
- AWS Documentation: https://docs.aws.amazon.com/
