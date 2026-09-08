# Breaking NexaPay — Threat Model & Attack Surface Assessment

**House of Practice — Round One — Cybersecurity Track ("Break the Fintech")**
Author: Semekor Collins

## What this is

A threat model and security assessment of **NexaPay**, a fictional mobile-money
aggregator platform that routes customer transactions across four partner
providers (ApexMoney, KasaPay, SwiftCash, MobiLink) over five channels
(Mobile App, USSD, Web, POS, API).

Rather than list generic OWASP-style weaknesses, NexaPay's vulnerabilities are
grounded in patterns found in a real transaction sample — a stored `risk_score`
that correlates with fraud-adjacent behaviour but never actually blocks a
transaction, transaction amounts that don't reconcile against the ledger, and
colliding transaction IDs. The dataset came first; the attack scenarios were
built to explain what it showed.

## Contents

| File | What it is |
|---|---|
| `Break_the_Fintech_Submission_SemekorCollins.docx` | Full submission: threat model, risk register, attack scenarios, risk prioritisation, security recommendations, proposed architecture, incident-response plan |
| `risk_matrix.png` | Likelihood vs. impact chart for all 11 identified vulnerabilities |
| `architecture.png` | Proposed security architecture — where enforcement should sit in the transaction path |
| `house_of_practice_financial_transactions.csv` | The transaction sample used as grounding evidence throughout |

## Headline finding

The dataset's `risk_score` field correlates with real behavioural signals
(velocity, device changes, failed attempts) but shows almost no relationship
with transaction outcome — **82% of the riskiest 10% of transactions still
completed successfully.** A score that doesn't gate anything isn't a minor
gap; it's a false sense of control. That single finding drives the three
top-priority recommendations in the submission.

## Scope note

This is a paper threat model against a fictional platform, built for a
challenge submission. No real systems, real companies, or third-party
infrastructure were tested or targeted.
