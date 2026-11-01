# AWS Deployment Plan

## Why AWS
- Seasonal/event-driven workload
- Serverless services can keep idle cost low
- Useful AWS interview practice
- Laptop does not need to stay on

## Initial AWS Components
- API Gateway
- Lambda
- SQS
- DynamoDB
- CloudWatch
- IAM
- Secrets Manager or SSM Parameter Store
- AWS Budgets

## Proposed Flow
```text
WhatsApp webhook
      |
      v
API Gateway
      |
      v
Ingress Lambda
      |
      v
SQS
      |
      v
Processing Lambda
      |
      +--> DynamoDB conversation state
      +--> Google Sheets business data
      +--> AI model API
      |
      v
WhatsApp send-message API
```

## Lambda vs EC2
Current decision: use Lambda by default because the workload does not justify an always-running server. Revisit EC2 only for a clear technical reason.

## Why SQS
Fast webhook acknowledgement, retry handling, burst protection, decoupling, dead-letter queue support.

## DynamoDB
Initial use cases: conversation state, WhatsApp idempotency, temporary order state, processing state.

## IAM
Apply least privilege. Avoid AdministratorAccess for runtime components.

## Secrets
Never store WhatsApp tokens, Meta secrets, AI API keys, Google private keys, or AWS keys in GitHub.

Local: `.env` ignored by Git.
AWS: Secrets Manager or SSM Parameter Store.

## Monitoring
Minimum: CloudWatch logs, Lambda errors/duration, SQS depth, DLQ alerts.

## Cost Control
Before production: enable AWS Budgets and review current pricing for AWS, AI API, and WhatsApp. Do not assume a fixed cost before actual configuration.

## Infrastructure as Code
Recommended later: AWS SAM as the simplest serverless fit. CDK or Terraform are valid alternatives.

## Environments
Suggested: local, dev, prod.

## AWS Learning Opportunities
Event-driven architecture, serverless compute, REST/webhooks, queues, NoSQL, IAM, secrets, observability, cost management, IaC, retries/idempotency.
