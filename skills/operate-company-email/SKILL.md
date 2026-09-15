---
name: operate-company-email
description: Operate Banger's canonical company-email system through MCP. Use when onboarding or configuring Banger; creating or reading mailboxes; sending Product email or Broadcasts; managing contacts, audiences, designs, Journeys, domains, connections, approvals, deliverability, or Logs; or finding email growth opportunities from product and business context.
---

# Operate Company Email

Use Banger as the governed system of record. Humans, Banger, and external agents must see and modify the same workspace state.

Use the product's canonical vocabulary in every user-facing response: **Mailboxes**, **Journeys**, **Broadcast**, **Product email**, **Approvals**, and **Logs**. A Journey is any automated email flow, whether it has one step or many. Do not expose the retired Autopilot, automation, sequence, campaign, or transactional-screen names. If an older client invokes a compatibility alias, describe the result with the canonical term.

## Choose the workflow

- OAuth authorization itself completes the browser's agent-connection checkpoint. Do not send a connection-test email during normal onboarding. Call `banger_onboarding_send_agent_test` only when the user explicitly asks for an optional connection diagnostic.
- When the user asks to “Plan the email growth system”, chooses “Start with a plan for your business”, asks for an email growth strategy, or requests a business-wide plan, follow the plan-only workflow below. Do not treat the request as approval to implement it.
- For a new or incomplete workspace, call `banger_onboarding_open_setup` first and follow its current `next_action`.
- For a normal request, inspect only the Banger objects required for the task, then act or prepare an approval.
- For a broad growth request, gather existing product context from available connected sources before asking the user for information already available.
- Prefer the interactive Banger setup UI returned by `banger_onboarding_open_setup` when the client supports MCP Apps. The same canonical tools remain the fallback.

## Onboard from canonical state

1. Follow Banger's current checkpoint. Never restart a completed checkpoint or move the user backward.
2. Let Banger create the hosted mailbox and perform its first real send-and-receive proof before asking for a domain.
3. Do not claim success until Banger returns the mailbox, received message, and completed proof in canonical state.
4. After that proof, offer the domain path without requiring it. A user with no domain remains able to use Banger-hosted mail immediately.

## Configure a company domain safely

1. Ask which domain the user wants to configure. Never infer it from their sign-in address, memory, or another workspace.
2. Use Banger's domain discovery and exact authoritative record bundle. Identify the registrar and currently detected mail services when Banger provides them.
3. Present or add the full prescribed bundle for Banger mailboxes and sending infrastructure, including every MX, SPF, DKIM, tracking, return-path, and other record Banger issues.
4. Never invent selectors, record values, or a TTL. Use the DNS provider's supported default or minimum TTL.
5. If computer use is available, explicitly ask permission before operating the registrar. Otherwise give exact record-by-record instructions.
6. Add all records first. DNS propagation is asynchronous; do not stop after the first pending verification or rewrite correct records while they propagate.
7. Re-run Banger's authoritative verifier after the propagation window. Report a backend provisioning error as such instead of fabricating progress.

## Turn context into growth work

After email works, inspect the available company, product, commerce, analytics, billing, support, repository, and mailbox context. Ask only for material gaps. Then propose a small prioritized set of concrete systems across the customer lifecycle, such as:

- onboarding and activation Journeys;
- lifecycle follow-ups and product-triggered Journeys;
- Product email;
- retention, churn-risk, and win-back Journeys;
- Broadcasts and launches;
- lead capture, qualification, and responsible outbound;
- operational mailboxes and inbound routing.

Make the first recommendation executable: name its audience, trigger, messages, success metric, and approval boundary. Prepare drafts and approval links when the tools support them. Do not launch sensitive or high-impact work without the required approval.

## Create a plan before executing

1. Ask which product, project, store, or company the plan is for and which domain or domains represent it. Include “I do not have a domain yet.” If likely projects, repositories, or domains are visible, offer them as choices but require confirmation.
2. After confirmation, gather relevant context from sources already available and permitted: conversation and memory, repositories and documentation, product data and analytics, payments or commerce, CRM, support, existing email systems, and Banger state. Never expose credentials or ask for information that can already be read safely.
3. Ask only for material gaps that would change the plan. Distinguish confirmed facts, reasonable inferences, and missing context.
4. Produce a prioritized, reviewable plan. For each recommendation include its audience, trigger, messages or workflow, required data and connections, success metric, expected impact, approval boundary, and implementation order.
5. The plan may cover Mailboxes, Product email, Journeys, Broadcasts, audiences, targeted outbound, domains, deliverability, and relevant service connections.
6. Saving reviewed context and a proposed plan in Banger is allowed because it creates reviewable draft state; it does not authorize implementation. Do not create operational resources, connect services, send email, change code, modify DNS or infrastructure, or activate a Journey until the user explicitly approves the reviewed plan.
7. End with clear choices to approve the plan, revise it, or add context. Never generate and execute a new plan in the same approval step.

## Operate with evidence

- Use idempotency keys for governed mutations and sends.
- Respect requested scopes and workspace approval policies.
- Never manufacture Mailboxes, delivery, DNS verification, Broadcast launches, or completed Journey runs.
- Re-read canonical state after a mutation before reporting completion.
- If a tool fails, report the failed operation and returned error. Do not silently substitute a semantically different action.
- Keep credentials and provider secrets inside Banger's authorization or connection pages.
- Use Banger's pending actions and audit history to explain what happened and what still requires review.

## Finish with the next useful action

End with the current result, the next approved action, and any dependency the user must handle. When setup is complete, remind the user that this same Banger connection can be used later for Mailboxes, Product email, Broadcasts, Journeys, audiences, delivery, and governed approvals.
