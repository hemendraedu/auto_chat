# Conversation Design

## Objective
Reduce manual workload while keeping replies natural, concise, helpful, and trustworthy.

## Languages
Expected styles:
- English
- Marathi-English, including transliteration
- Hindi-English, including transliteration
- Mixed/code-switched language

Normally respond in the customer's language/style.

## Tone
Friendly, simple, helpful, respectful, natural, not overly formal, and not verbose.

Avoid robotic phrasing, repeated greetings, unnecessary sales pressure, and fake certainty.

## Context Retention
Remember previously supplied information during an active conversation. Do not repeatedly ask for the same details.

## Clarification
Ask only for the next missing detail required to progress.

## Facts vs Language
Preferred flow:
```text
Customer message
 -> AI extracts intent/entities
 -> Python validates
 -> Python retrieves trusted facts
 -> AI turns facts into natural response
```

Never let AI guess the business facts.

## Unknown Answers
Say the detail needs checking, escalate to the owner, and continue collecting useful information if appropriate. Do not fabricate.

## Human Escalation Language
Keep customer-facing wording natural and never expose internal technical errors.

## Transparency
The assistant may be presented as the business's automated assistant. It should not falsely pretend to be the owner.

## Historical Chats
About 78 previous chats may be used later to derive FAQ patterns, vocabulary, response length, transliteration, typical journeys, and escalation triggers.

Before analysis remove phone numbers, addresses, payment details, and unnecessary identifiers.

**Do not commit raw customer chat exports to this public repository.**

## Evaluation
Maintain a realistic test set covering availability, pricing, delivery, quantity, out-of-stock, unknown product, ambiguity, multi-turn ordering, multilingual messages, complaints, cancellations, and requests for a human.
