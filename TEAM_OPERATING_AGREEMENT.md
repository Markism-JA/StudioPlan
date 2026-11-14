# [Studio Name] — Internal Team Operating Agreement (4-Person Team)

> **Purpose:** Clear, written rules on roles, revenue splits, payout timing, and engineering standards—agreed to *before* Client #1 signs so there is zero ambiguity or friction later.

---

## 1. Team Structure & Roles

| Role | Primary Responsibilities |
| :--- | :--- |
| **Founder / Lead Architect / Closer** | Client acquisition, discovery calls, MSA/SOW scoping, Day 1 architecture brief, OpenTofu/CI/CD setup, PR reviews, Day 30 production handover. |
| **Active Builders (2–3 Members)** | Daily full-stack implementation from the Golden Template, UI/UX polish, database migrations, unit & integration tests, staging bug fixes. |

*(Note: Not every member needs to be assigned to every sprint. Smaller sprints run faster with 2 Active Builders + 1 Lead Reviewer, freeing other members to work on parallel sprints or internal products.)*

---

## 2. Revenue Split Formula (`20 / 25 / 55`)

All percentages are calculated on **Net Project Revenue** *(Gross Client Payment minus external payment processing fees, Wise/Stripe fees, and any third-party design-agency finder’s fee)*.

| Bucket | Share | Purpose |
| :--- | :---: | :--- |
| **Studio Treasury** | **20%** | Domains, Hetzner/staging servers, Google Workspace, AI/dev tools, tax reserve, and studio emergency runway. |
| **Founder / Closer / Architect** | **25%** | Compensation for closing the deal, managing client communication, system architecture, OpenTofu provisioning, and final liability/QA. |
| **Active Builders Pool** | **55%** | Divided equally (or by pre-agreed sprint weight) among the developers actively writing application code on that specific sprint. |

> **If the Founder also writes application code on a sprint:** They receive a proportional share from the 55% Active Builders Pool in addition to the 25% Closer/Architect share, agreed upon before Week 1 starts.
> **If another teammate brings & closes a client:** That teammate receives **15%** from the Closer share (and the Lead Architect retains **10%** for architecture/OpenTofu/QA), incentivizing everyone to bring in leads.

### Worked Example: $4,000 USD (~₱232,000 PHP @ ₱58) Net Sprint *(2 Builders + Lead)*

* **Studio Treasury (20%):** $800 (**₱46,400**)
* **Founder / Closer / Architect (25%):** $1,000 (**₱58,000**)
* **Builder 1 (27.5%):** $1,100 (**₱63,800**)
* **Builder 2 (27.5%):** $1,100 (**₱63,800**)

### Monthly Care Retainers ($450/mo Peace of Mind)

* **20% → Studio Treasury**
* **80% → Assigned Maintainer** *(whoever monitors alerts, verifies backups, and applies monthly patches for that client)*.

---

## 3. Staged Payout & Vesting Rules (Cash-Cleared & Gate-Verified)

1. **No Uncollected Payouts:** Team payouts are distributed **only after** client funds have cleared in the studio’s Wise/Bank/USDC account.
2. **Staged Builder Vesting (`40% / 50% / 10%` — Protects Against Mid-Sprint Dropouts):**
   While the client pays 50% upfront (Stage 0) and 50% at Staging Acceptance (Stage 3), **Active Builder payouts vest on verified engineering gates**, never on Day 1 before code is written:
   * **Tranche 1 — 40% at Stage 2 Gate (Day 15):** Paid after the client’s 50% deposit has cleared **AND** the builder’s assigned screens, APIs, and integration tests pass Lead Architect PR review and deploy cleanly to Staging.
   * **Tranche 2 — 50% at Stage 4 Gate (Day 30):** Paid when the client’s **Final 50% Balance** clears and production handover completes.
   * **Tranche 3 — 10% Warranty Release (Day 44):** Paid at the close of the **14-day post-launch bug warranty** once all reproducible in-scope warranty bugs in the builder's modules are resolved.
   * *(Founder/Closer/Architect 25% share and Studio Treasury 20% share release 50% upon Stage 0 deposit clearance and 50% upon Stage 4 final balance clearance.)*
3. **Mid-Sprint Abandonment / Reassignment Rule:**
   If an assigned builder becomes unresponsive for `>48 hours` during an active sprint or fails to deliver their assigned module by Stage 2, the Lead Architect may reassign the module to another builder. Any unvested payout tranches (`40%`, `50%`, `10%`) for that module transfer directly to the replacement builder who completes the work.

---

## 4. Engineering & Training Standards

To maintain "terrifying velocity" while leveling up every teammate:

1. **Use the Golden Template:** Every sprint starts from the studio’s pre-configured boilerplate (Auth, DB, Docker, CI/CD, OpenTofu) — never from an empty folder.
2. **30-Minute Architecture Brief:** Before writing application code in Week 1, the assigned builder(s) draft a 1-page DB schema + core API endpoint list for Lead approval.
3. **Mandatory PR Reviews:** Direct pushes to `main` are disabled. Every feature merges via Pull Request reviewed by the Lead Architect (used as both a quality gate and a coaching moment).
4. **Tests Required for Staging:** Core user flows (auth, billing webhooks, primary CRUD) must have passing unit/integration tests before staging handover.
5. **AI-Assisted Velocity:** Builders are encouraged to use AI coding tools for speed, **provided they understand, test, and can explain every line they submit in a PR**.

---

## 5. IP Boundaries & Confidentiality

* **Client Work:** Upon final payment, client custom code belongs to the client per `MSA_SOW_TEMPLATE.md`. Team members may not reuse client-specific business logic or leak client data.
* **Studio Assets:** Reusable OpenTofu modules, Golden Templates, and internal tooling remain `[Studio Name]` property.
* **External / Personal IP:** Pre-existing personal projects and open-source libraries (including *Echoes of Bathala* and its extracted `.NET` libraries) remain strictly separate from studio client deliverables unless explicitly licensed as open-source.

---

## 6. Team Sign-Off

| Member Name | Role | Signature / Handle | Date |
| :--- | :--- | :--- | :--- |
| `[Your Name]` | Founder / Lead Architect / Closer | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | `[Date]` |
| `[Member 2]` | Builder | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | `[Date]` |
| `[Member 3]` | Builder | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | `[Date]` |
| `[Member 4]` | Builder | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | `[Date]` |
