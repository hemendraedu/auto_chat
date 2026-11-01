# Technical Decision Log

## D001 - Start with the mango business, not a generic AI product
Accepted. Real problem, users, order data, and measurable time savings.

## D002 - Use an existing AI model
Accepted. Do not build/train a foundation model.

## D003 - Use Codex in VS Code
Accepted. GitHub is the source of context so implementation can continue without the original chat.

## D004 - Python backend
Accepted. Good fit for AI/API work, prototyping, readability, and Lambda.

## D005 - No n8n initially
Accepted for initial phase. Codex + Python gives more control and learning value. Revisit only if useful.

## D006 - Google Sheets initially
Accepted because the business already uses it. Migrate only when it becomes a limitation.

## D007 - Build locally before WhatsApp
Accepted to reduce integration complexity, cost, debugging difficulty, and real-customer risk.

## D008 - Prefer AWS serverless production architecture
Accepted: API Gateway + Lambda + SQS + DynamoDB.

## D009 - Lambda preferred over EC2
Accepted for current seasonal low-volume workload.

## D010 - AI must not own business-critical decisions
Accepted and critical. AI may understand/draft; trusted data and deterministic logic decide price, stock, delivery, discounts, payments, and order status.

## D011 - Persist conversation state
Accepted. Production direction: DynamoDB.

## D012 - Use SQS between webhook and processing
Accepted architectural direction for retries, burst handling, quick webhook acknowledgement, and DLQ support.

## D013 - Historical customer chats are private reference data
Accepted. Anonymize before analysis; do not commit raw customer data to this public repo.

## D014 - Keep project low-cost
Accepted. Avoid unnecessary always-on servers and paid tools.

## D015 - Automation with human fallback
Accepted. Goal is not 100% autonomy; automate routine cases and escalate exceptions safely.
