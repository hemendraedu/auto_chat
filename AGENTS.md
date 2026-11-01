# AGENTS.md

## Project Mission
Build a reliable, low-cost AI assistant for a seasonal mango business.

The system should reduce the need for the owner to manually monitor WhatsApp throughout the day while preserving a natural customer experience.

## Read Before Coding
1. `README.md`
2. `docs/PROJECT_CONTEXT.md`
3. `docs/ARCHITECTURE.md`
4. `docs/ROADMAP.md`
5. `docs/BUSINESS_RULES.md`
6. `docs/CONVERSATION_DESIGN.md`
7. `docs/DECISIONS.md`

## Core Engineering Rules
- Do not allow the LLM to invent price, stock, delivery availability, order status, payment status, or discounts.
- Use deterministic Python logic for business-critical decisions.
- Keep business data behind explicit interfaces/functions.
- Separate conversation logic from transaction logic.
- Prefer simple architecture over unnecessary frameworks.
- Keep the first prototype runnable locally.
- Do not add WhatsApp integration until the local workflow is stable.
- Do not hard-code credentials, tokens, phone numbers, or API keys.
- Use environment variables for secrets.
- Add tests for business rules before expanding functionality.
- Log failures and exceptional states clearly.
- Design every external integration so it can be replaced later.

## Initial Build Goal
First milestone:
1. User enters a customer-style message in a local chat interface.
2. Application detects intent.
3. It retrieves trusted product/delivery data.
4. It generates a natural response.
5. It does not yet place a real WhatsApp order.

Example customer message:
`2 peti Hapus pahije. Pune delivery hoil ka?`

Expected behavior:
- Detect product/quantity/delivery intent.
- Look up product availability.
- Look up Pune delivery rules.
- Generate a natural reply.
- If required information is missing, ask a concise follow-up.
- Never fabricate availability or timing.

## Coding Style
- Python 3.12+ preferred unless compatibility requires otherwise.
- Use type hints.
- Keep functions small and testable.
- Prefer `src/` layout.
- Use `pytest` for tests.
- Use `.env.example` only for variable names, never real credentials.
- Avoid introducing infrastructure before it is needed.

## Suggested Initial Structure
```text
src/
  app.py
  config.py
  models/
  services/
    ai_service.py
    product_service.py
    order_service.py
    conversation_service.py
  repositories/
    product_repository.py
    order_repository.py
tests/
sample-data/
```

This is a guideline, not a requirement. Keep the implementation as small as practical.
