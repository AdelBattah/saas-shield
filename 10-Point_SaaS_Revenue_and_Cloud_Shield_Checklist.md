# The 10-Point Solo Founder & SaaS Shield Checklist (Free Edition)

Stop losing thousands to bad client contracts, ghosting payers, broken Stripe webhooks, and runaway AWS bills.
Run through these 10 production checks before signing a client, launching billing, or deploying to the cloud.

---

## Part 1: Client Contracts & Cash Flow (Checks 1-4)

- [ ] **1. Pre-Existing IP Carve-Out:** Does your contract explicitly state that your starter kits, boilerplates, and reusable libraries remain *your* property? *(Without this, "Work Made for Hire" can legally transfer your own toolkit to your client.)*
- [ ] **2. Payment-Triggered IP Transfer:** Does ownership of deliverables transfer *only upon receipt of full, cleared payment* -- never upon delivery? *(This single sentence is your #1 lever if a client ghosts you.)*
- [ ] **3. Liability Cap & Deemed Acceptance:** Is your total liability capped at the fees paid under the SOW (not uncapped damages), and are deliverables automatically "deemed accepted" after 5-10 business days of client silence?
- [ ] **4. Automated Overdue Escalation Ladder:** Do you have pre-written Day 1, Day 14, Day 30, and Day 45+ escalation templates (including statutory late-interest calculations and an IP License Revocation Notice) ready before an invoice goes cold?

---

## Part 2: Stripe & Payment Webhooks (Checks 5-7)

- [ ] **5. Raw Body Before Signature Verification:** Does your webhook route pass the exact raw byte buffer to `stripe.webhooks.constructEvent()` *before* any JSON body parser runs? *(Parsing JSON first breaks HMAC signatures in production.)*
- [ ] **6. Atomic Database Idempotency Gate:** Are you storing every processed `event.id` in a `UNIQUE`-constrained database table inside an ACID transaction? *(Stripe guarantees "at-least-once" delivery -- without idempotency, retries grant double credits or duplicate orders.)*
- [ ] **7. Sub-2-Second Acknowledgment:** Does your webhook return HTTP `200 OK` within 2 seconds by offloading emails, PDF generation, and external API calls to a background queue? *(Slow handlers trigger Stripe retry storms and endpoint deactivation.)*

---

## Part 3: AWS Cloud Security & Bill-Shock Prevention (Checks 8-10)

- [ ] **8. Free VPC Gateway Endpoints for S3 & DynamoDB:** Are your private subnets routing S3/DynamoDB traffic through a **$0 VPC Gateway Endpoint** instead of paying ~$0.045/GB through a NAT Gateway?
- [ ] **9. IAM Region Lock & GPU Block:** Does your IAM Permissions Boundary or SCP deny deployments outside your 1-2 active regions and block high-cost `p*`/`g*`/`*.metal` GPU instances? *(Stops compromised keys from generating $30k cryptojacking bills overnight.)*
- [ ] **10. AWS Budgets + Cost Anomaly Detection + Lambda Concurrency Cap:** Do you have an `ACTUAL` (50%) and `FORECASTED` (80%) AWS Budget alert, an immediate Cost Anomaly alert, and `reserved_concurrent_executions` set on every Lambda triggered by S3 or SQS?

---

## Automate All 10 Audits in 60 Seconds

Get **The Solo Founder & SaaS Revenue Shield** -- 4 plug-and-play AI auditor skills (`SKILL.md` + 1-command installer for Claude Code, Cursor, Antigravity & ChatGPT) that audit your real contracts, unpaid invoices, Stripe code, and AWS Terraform files and output exact drop-in fixes:

- **Complete 4-Skill Bundle ($39 one-time, Save $40.96 vs. retail):** https://adelbattah.github.io/#pricing
- **Interactive Browser Checklist:** https://adelbattah.github.io/checklist.html
