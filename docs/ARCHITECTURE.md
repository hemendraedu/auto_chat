# Architecture

## Principles
1. AI handles language, not authoritative business facts.
2. Business-critical facts come from trusted data and deterministic code.
3. External systems are accessed through service/repository layers.
4. Keep the initial implementation simple.
5. Production infrastructure should be event-driven and low-cost.
6. Failures must be observable and recoverable.
7. Human escalation must remain possible.

## Phase A - Local Prototype
```text
Local Chat UI
      |
      v
Python Application
      |
      +--> AI intent / structured extraction
      +--> Business-rule layer
      +--> Product / delivery data
      |
      v
AI response generation
      |
      v
Local Chat UI
```

### Chat UI
Possible choices: Streamlit, Gradio, minimal web UI, or CLI.

### Python Application
Responsible for input handling, AI calls, business services, validation, response context, and reply generation.

### Product Repository
Initial data source may be local JSON/CSV, then Google Sheets.
Suggested methods:
- `get_product()`
- `get_price()`
- `get_stock()`
- `get_delivery_rule()`

### AI Service
May handle:
- Intent detection
- Entity extraction
- Language/style recognition
- Natural response generation

Must not independently decide price, stock, discounts, delivery eligibility, payment state, or final order status.

## Phase B - Google Sheets
Suggested sheets:

### Products
- product_id
- product_name
- variety
- pack_size
- price
- available_quantity
- active
- notes

### Delivery Areas
- area
- city
- delivery_available
- delivery_charge
- minimum_order
- expected_delivery_window
- notes

### Orders
- order_id
- customer_reference
- created_at
- product
- quantity
- amount
- delivery_area
- address
- contact
- payment_status
- order_status
- notes

## Phase C - AWS Backend
```text
WhatsApp Business Platform
          |
          | webhook
          v
Amazon API Gateway
          |
          v
Ingress Lambda
          |
          v
Amazon SQS
          |
          v
Processing Lambda
       /     |      \
      v      v       v
DynamoDB  Business  AI Model API
            Data
             |
             v
        Google Sheets
             |
             v
WhatsApp Business Platform
             |
             v
          Customer
```

### API Gateway
Public HTTPS webhook endpoint.

### Ingress Lambda
Validate/normalize incoming events and enqueue quickly.

### SQS
Decouple ingestion and processing; support retries and dead-letter handling.

### Processing Lambda
Load state, parse message, perform lookups, execute deterministic rules, call AI model, validate result, send response, save state.

### DynamoDB
For conversation/session state, idempotency, temporary order state, and processing metadata.

### Google Sheets
Initially stores product master, inventory, delivery information, and orders.

### CloudWatch
Logs, errors, duration, retry visibility, basic metrics.

### AWS Budgets
Configure before production deployment.

## Conversation Processing Pattern
1. Understand: convert natural message into structured intent.
2. Validate: Python checks product, quantity, stock, delivery.
3. Decide: deterministic code produces factual outcome.
4. Respond: AI turns validated facts into natural language.

## Failure Handling
- AI unavailable: retry, then alert/escalate.
- Sheets unavailable: do not invent facts; state that details are being checked.
- Unknown question: clarify or escalate.
- Duplicate webhook: use idempotency/message IDs.
- Invalid AI output: schema validation, limited retry, then fallback.

## Security
- Secrets only in environment variables or AWS secret stores.
- Never commit API keys.
- Minimize stored personal data.
- Apply least-privilege IAM.
- Sanitize logs.
