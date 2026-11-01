# Business Rules

This is the authoritative specification for non-AI business behavior. Unknown values remain TODO until supplied by the business.

## Fundamental Rule
The LLM must never invent:
- Product availability
- Pack size
- Price
- Stock quantity
- Discount
- Delivery availability/charge/date
- Payment status
- Order status
- Refund/cancellation decisions

## Product Rules
TODO: define actual products, variety/grade, pack size, price, available quantity, active state, and notes.

Unknown product: do not invent it; offer only real alternatives from trusted data.

## Stock Rules
TODO:
- Tracking unit?
- Real-time or manual?
- Waitlist allowed?
- When is stock reserved?

Safe default: if stock data is unavailable or stale, do not promise availability.

## Price Rules
TODO:
- Fixed per pack?
- Grade/size variants?
- Delivery included?
- Bulk discounts?
- Repeat-customer discounts?
- Who approves discounts?

Default: AI cannot negotiate or invent discounts.

## Delivery Rules
TODO:
- Supported cities/areas?
- Pune zones?
- Delivery charge?
- Minimum quantity?
- Fixed delivery days?
- Delivery-date logic?

Default: if delivery eligibility cannot be determined, escalate.

## Order Information
Candidate fields:
- Customer name
- Platform identifier
- Product
- Quantity
- Delivery area
- Full address
- Contact number
- Preferred delivery date
- Payment method
- Notes

Collect only necessary information.

## Order Confirmation
1. Collect required details.
2. Calculate amount deterministically.
3. Present concise order summary.
4. Ask customer to confirm.
5. Record order.
6. Send order ID/confirmation.

## Changes/Cancellations
Until rules are defined, escalate.

## Payment
Initial prototype: payment automation out of scope.
AI must never claim payment was received unless verified by trusted source.

## Human Escalation
Escalate for exceptions, missing data, complaints, unusual questions, low confidence, technical failures, or explicit requests for a person.

## Calls
Calls stay manual initially. Manual orders should still enter the same order source of truth.

## Data Accuracy
Where practical, show/update timestamps for product/order data. If stale data could lead to a wrong promise, do not answer as if current.
