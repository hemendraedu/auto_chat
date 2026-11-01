# Roadmap

## Phase 0 - Project Setup
Status: In progress

Goal: GitHub contains enough context to restart without the original chat.

## Phase 1 - Local Conversation Prototype
Build Python project, local chat UI, sample product data, one AI API integration, structured intent schema, product lookup, response generation, env config, and initial tests.

Exit: answers routine product questions using trusted sample data without inventing facts.

## Phase 2 - Business Rules
Define product, pricing, stock, delivery, minimum-order, discount, order-state, and escalation rules. Add unit tests.

Potential states: inquiry, collecting_details, awaiting_confirmation, confirmed, packed, dispatched, delivered, cancelled.

Exit: core transaction logic works without the AI model.

## Phase 3 - Google Sheets Integration
Create Products, Delivery Areas, Orders sheets. Implement read/write repository and safe failure handling.

Exit: chatbot reads real product data and can store test orders.

## Phase 4 - Order Collection
Support conversational collection of product, quantity, customer name, location, address, contact, delivery timing, payment method/status as needed. Confirm before creation and prevent duplicates.

Exit: complete test order can be created from a multi-turn conversation.

## Phase 5 - Historical Conversation Analysis
Analyze about 78 anonymized customer chats for FAQs, language patterns, owner response patterns, edge cases, and escalation categories.

Do not fine-tune initially. Prefer prompt examples, FAQ knowledge, guidelines, and derived test cases.

## Phase 6 - Multilingual Quality
Test English, Marathi-English, Hindi-English, transliteration, and code-switching. Avoid overly formal machine-translated replies.

## Phase 7 - AWS Deployment
Create personal AWS account if needed, enable MFA and Budgets, deploy Lambda/API Gateway/SQS/DynamoDB/CloudWatch/secrets, and test end to end.

## Phase 8 - WhatsApp Business Platform
Configure Meta/WhatsApp, webhooks, inbound messages, outbound replies, retries/idempotency, template requirements, and current pricing.

## Phase 9 - Pilot
Measure automation rate, incorrect replies, escalation rate, order accuracy, response time, customer confusion, owner time saved, and total cost.

## Phase 10 - Production Improvements
Possible later features: payment links, delivery updates, customer segmentation, repeat-customer recognition, follow-ups, reopening messages, analytics, admin UI, voice support, reusable multi-business version.
