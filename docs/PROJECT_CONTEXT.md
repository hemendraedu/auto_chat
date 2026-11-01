# Project Context

## Why This Project Exists
The mango business receives most inquiries and orders through WhatsApp Business. Manual conversation handling is difficult alongside a full-time job. The core problem is the need to remain continuously available, not simply raw message volume.

Typical conversations include:
- Product availability
- Price questions
- Quantity questions
- Delivery location and timing
- Order placement and confirmation
- Follow-up questions and status updates

## Business Characteristics
- Seasonal operation: about three months/year.
- Peak message volume: up to around 50 messages/day.
- Many messages are part of ongoing conversations, not unique customers.
- WhatsApp Business is the primary channel.
- Some customers call.
- Google Sheets is currently used for orders.
- About 78 customer chats from the previous season are available for future analysis.

Historic chats should later be used to understand:
- Common questions
- Reply patterns
- Marathi-English, Hindi-English, and English usage
- Customer expectations
- Escalation situations
- Opportunities to improve the customer experience

## Long-Term Vision
A customer should be able to message the business and receive useful support without the owner continuously monitoring the phone.

Future production flow:
1. Customer sends a message.
2. Message reaches cloud backend.
3. System identifies intent.
4. Trusted business data is retrieved.
5. AI produces a natural response using only validated facts.
6. If ordering, system collects required information.
7. Order is recorded.
8. Conversation state is saved.
9. Routine follow-ups can be automated.
10. Exceptions are escalated.

## Out of Scope Initially
- Training a custom LLM
- Full CRM
- Voice-call automation
- Mobile app
- Large database platform
- Full payment automation
- Logistics optimization
- Multi-tenant SaaS
- Advanced analytics dashboards
- Generic chatbot platform

## Why Existing AI Models
Existing models already handle language understanding, code-switching, intent extraction, structured output, and response generation. The project value is in business integration, rules, workflow automation, and reliability.

## Why AWS
AWS fits the seasonal, low-volume, event-driven workload and provides useful hands-on experience for technical interview preparation.

## Why Lambda Over EC2 Initially
The workload is low-volume, bursty, and seasonal. Lambda avoids paying for and managing an always-on server. EC2 can be revisited only if long-running processes or other technical constraints emerge.

## Why WhatsApp Comes Later
WhatsApp integration adds Meta setup, webhooks, credentials, messaging rules/costs, and customer-facing risk. First prove business logic locally.

## Prototype Question
Can the system reliably understand a mango customer request, retrieve correct business data, and produce an appropriate response without inventing facts?

## Possible Future Business Opportunity
If the mango-business prototype works, it may later be adapted into a reusable assistant for other growers or small businesses. This is not assumed; usefulness must be proven first.
