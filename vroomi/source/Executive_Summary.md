# Vroomi AI Assistant: Executive Summary

| | |
|---|---|
| **Prepared for** | CISO, Softmicro: is Vroomi ready for more agentic features? |
| **Assessor** | Federico Moran |
| **AI assistance** | Analysis and writing assisted by Claude (Anthropic) |
| **Date** | 2026-11-13 |
| **Full report** | [Technical_Report.md](Technical_Report.md); finding IDs (VRM-xx) refer to it |

## Bottom line

Vroomi is not ready for agentic features. Today any employee can read a customer's account details and cancel anyone's trip with one plain sentence, and nothing records who did it. Features that let the assistant act on its own would build on those gaps. **Conditional Go:** proceed once the five conditions below are met.

## What Vroomi is

An AI assistant Softmicro employees use to book, cancel and review rides for staff and clients, and to ask policy questions. Softmicro is considering agentic features: the assistant reading data back and acting on it with fewer steps for the user.

## What we tested

The Vroomi prototype's design and code, threat-modelled and assessed against the OWASP Top 10 for LLM Applications (2026), plus 19 tests run live against the AI model, most of them 10 times, between 20 October and 8 November 2026. The tests used one model and a simulated booking store; the agentic risk was tested by simulating the planned feature.

## Top risks

1. **Customer data goes to anyone who asks.** Any user got a customer's name, account ID and billing issue by simply asking, every time (VRM-01). That is a reportable personal-data exposure and enough for a targeted scam. Internal policy documents come out the same way (VRM-03).
2. **Any employee can cancel anyone's trip, and no one can tell who did it.** Vroomi doesn't know who is asking and trips don't record whose they are. Told the trip was a colleague's, it still cancelled it every time, and it shows every trip to every employee (VRM-02). A related flaw cancels a trip when someone only asks how cancelling works (VRM-04).
3. **With agentic features, one employee's stored text could steer another employee's assistant.** Text saved in a booking reached another employee's trip summary as advice from Vroomi, in every run. The model also followed a planted instruction to cancel a trip; only a technical accident stopped it from running (VRM-05).

## What it takes to fix

- **This week, low effort:** take the customer record out of the assistant's instructions; have the user confirm every booking change in the app; log every action. Cost: one extra click per change.
- **Next, larger:** employee sign-in and roles, an owner on every trip, and permission checks in code before any action or lookup. Cost: sign-in for users, roles to maintain, significant engineering time.
- **Before agentic features:** actions through a separate, structured channel, and stored data treated as data, never as instructions.

We also tested common quick fixes against the same attacks. Fixes built into the code, such as removing the customer record or requiring the user's confirmation, worked. Filters that block requests containing certain words were bypassed by rewording the request. None of the fixes stopped an employee cancelling a colleague's trip.

## Decision

**Conditional Go.** Add agentic features only after:

1. The assistant's instructions hold nothing that every employee may not see.
2. Employees sign in, and every action and lookup is checked in code against who is asking.
3. Every change is confirmed by the user in the app and logged with their identity.
4. Data the assistant reads back is treated as data, never as instructions.
5. The test suite is rerun on the release candidate and the report's verification steps pass.
