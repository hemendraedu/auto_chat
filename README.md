# Auto Chat - AI Assistant for Mango Business

## Purpose
This repository is the source of truth for building an AI-assisted customer conversation and order-management system for a seasonal mango business.

The project started from a practical problem: customer conversations are handled mainly through WhatsApp Business, and managing replies, questions, orders, stock checks, and delivery updates manually is difficult alongside a full-time job.

The first goal is not to build a generic chatbot product. The first goal is to build and validate a useful assistant for the mango business itself. If it works well, the same architecture may later be adapted for other small businesses.

## Current Direction
The assistant should eventually be able to:
- Receive customer messages from WhatsApp.
- Understand English, Marathi-English, Hindi-English, and natural mixed-language messages.
- Answer routine questions naturally.
- Check product price, stock, delivery availability, and other business data before replying.
- Collect order details.
- Record orders.
- Maintain conversation context.
- Send order confirmations and delivery-related updates.
- Escalate uncertain, exceptional, or sensitive situations to a human.
- Avoid inventing prices, stock, delivery promises, or business rules.

## Key Design Principle
**AI handles language and conversation. Deterministic code and trusted business data handle facts and transactions.**

## Planned Technology Direction
### Prototype
- Python
- Codex in VS Code
- Simple local chat interface
- Google Sheets for initial product/order data
- Existing AI model through API
- No WhatsApp integration at the very beginning

### Production Direction
- WhatsApp Business Platform
- Amazon API Gateway
- AWS Lambda
- Amazon SQS
- Amazon DynamoDB
- Google Sheets initially, with the option to migrate later
- AI model API
- CloudWatch
- AWS Budgets / cost alerts

## Development Strategy
1. Build a local chatbot using sample mango-business data.
2. Make business rules reliable before adding more AI behavior.
3. Add order capture and Google Sheets integration.
4. Analyze historic customer chats to improve conversation behavior.
5. Add multilingual handling and human escalation.
6. Deploy the backend to AWS.
7. Connect WhatsApp only after the core workflow is reliable.
8. Test with a small number of real conversations before wider use.

## Important Project Context
- Seasonal business: roughly three months per year.
- Peak volume: around 50 WhatsApp messages/day, often across ongoing conversations rather than 50 unique customers.
- WhatsApp Business is the primary channel; some customers call.
- Orders are currently managed in Google Sheets.
- About 78 historic customer chats are available for later analysis.
- Keep the solution low-cost and simple enough to maintain.
- AWS is preferred partly for practical interview preparation.
- No plan to train a custom foundational model.

## Repository Role
This repository should contain enough context that the project can continue even if the original ChatGPT conversation is lost.

Start with:
- [Project context](docs/PROJECT_CONTEXT.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Roadmap](docs/ROADMAP.md)
- [Business rules](docs/BUSINESS_RULES.md)
- [Conversation design](docs/CONVERSATION_DESIGN.md)
- [AWS deployment](docs/AWS_DEPLOYMENT.md)
- [Technical decisions](docs/DECISIONS.md)

For Codex working guidance, see [AGENTS.md](AGENTS.md).

## Current Status
**Phase 0 - Planning and repository setup**

No production code has been implemented yet.
