# Master Services Agreement & Statement of Work

> **Template Notice:** This is a practical commercial & engineering agreement template for `[Studio Name]`, not formal legal advice. Replace bracketed placeholders (`[...]`) before sending to a client, and consult a local attorney for high-value or enterprise engagements.

---

## Part 1: Master Services Agreement (MSA)

This Master Services Agreement (**"Agreement"**) is entered into as of `[Effective Date]` by and between:

* **Provider:** `[Studio Name / Legal Entity]`, operating from `[City, Philippines]` (**"Studio"**)
* **Client:** `[Client Legal Name / Company]`, with principal address at `[Client Address]` (**"Client"**)

---

### 1. Services & Statement of Work

Studio agrees to design, engineer, test, and deploy software deliverables (**"Deliverables"**) as explicitly specified in **Exhibit A (Statement of Work / "SOW")** attached to this Agreement. Any features, screens, integrations, or services not expressly listed in Exhibit A are out of scope.

### 2. Fees & Payment Terms (50 / 50 Milestone Escrow)

1. **Milestone Schedule:**
   * **Deposit (50%):** Non-refundable deposit due upon signing this Agreement. Engineering work and sprint scheduling do not begin until the Deposit clears.
   * **Final Balance (50%):** Due upon Client's acceptance of the completed build on Studio's staging environment (Week 3 / Staging Sign-off), **prior to** production cloud provisioning and repository transfer.
2. **Payment Methods:** Invoices are payable in USD via `[Wise / Bank Wire / Stripe / USDC]`. Client is responsible for any intermediary bank or transfer fees.
3. **Late Payment:** Overdue invoices beyond 5 business days pause all sprint work and handover activities without liability to Studio.

### 3. Staging-First Development & Production Handover

1. **Staging Sandbox:** During active development, Studio will host the application on Studio’s isolated staging environment (`staging-[client].[studio.dev]`) for Client testing and verification.
2. **Production Gate:** Production OpenTofu infrastructure provisioning inside Client's cloud account, live DNS cutover, and GitHub repository ownership transfer occur **only after** the Final Balance (50%) has cleared in full.
3. **Client-Owned Accounts & Billing:** Client shall create and maintain its own cloud (Hetzner / DigitalOcean / AWS), GitHub Organization, payment gateway (Stripe / Lemon Squeezy), and email/API accounts on Client’s own payment method. Client will issue scoped API tokens/permissions to Studio for Day 30 deployment and **must rotate/revoke those developer tokens immediately after handover**.

### 4. Intellectual Property Rights

1. **Client Deliverables (100% Assignment):** Upon Studio's receipt of **100% of total SOW fees**, Studio assigns to Client all right, title, and interest in the custom application code, UI implementations, and database schemas created specifically for Client under Exhibit A.
2. **Studio Background IP & Open-Source Tools:** Studio retains full ownership of all pre-existing frameworks, starter templates, generic OpenTofu/IaC modules, and open-source libraries (**"Background IP"**) incorporated into the Deliverables. Upon full payment, Studio grants Client a **perpetual, worldwide, non-exclusive, royalty-free license** to use such Background IP solely as embedded in the Deliverables.
3. **No Pre-Payment Transfer:** Until 100% of fees are paid, Studio retains all rights to the codebase and staging environment.

### 5. Client Responsibilities & Timeline Pause

1. **Cooperation:** Client agrees to provide required brand assets, Figma/wireframes, copy, account tokens, and milestone feedback within **2 business days** of request.
2. **Automatic Clock Pause:** If Client delays feedback, approvals, or required third-party account setup by more than **3 business days**, the 30-day delivery window pauses automatically day-for-day until resolved, without penalty to Studio.

### 6. Scope Freeze & Change Orders

1. **Week 1 Scope Lock:** The feature list in Exhibit A locks at the end of Week 1.
2. **Out-of-Scope Requests:** Any additional screens, integrations, or workflow changes requested after Week 1 lock are not included in the fixed fee. Studio will quote them separately per `[Studio Name]`'s Add-On Menu (either as a paid Change Order extending the timeline, or queued for a Phase 2 sprint).

### 7. Acceptance, 14-Day Bug Warranty & Post-Launch Care

1. **Acceptance Window:** Upon staging delivery, Client has **5 business days** to test against Exhibit A’s acceptance criteria and report reproducible defects. Absence of written rejection within 5 business days constitutes acceptance.
2. **14-Day Bug Warranty:** For **14 calendar days** following production handover, Studio will fix reproducible defects in Deliverables that deviate from Exhibit A at no additional cost. This warranty excludes issues caused by Client modifications, third-party API outages, or Client infrastructure misconfiguration after handover.
3. **Ongoing Maintenance:** After Day 14, Client may self-manage the system or elect an optional monthly Care/Retainer Plan under a separate order.

### 8. Early Termination (Kill Fee)

Either party may terminate this Agreement upon written notice for material breach uncured for 7 days. If Client cancels the project for convenience after work has begun:

* Studio retains the **50% non-refundable Deposit** as liquidated compensation for reserved sprint capacity and work performed.
* If termination occurs prior to full payment of the Final Balance, **no code, OpenTofu scripts, or staging assets are transferred** to Client.

### 9. Confidentiality & Limitation of Liability

1. **Confidentiality:** Both parties agree to keep non-public business, technical, and credential information strictly confidential for 2 years following termination.
2. **Disclaimer of Warranties:** Except for the 14-day bug warranty in Section 7, Deliverables are provided *"as is"*.
3. **Limitation of Liability:** To the maximum extent permitted by law, **Studio’s total aggregate liability** arising out of or related to this Agreement shall not exceed the **total fees actually paid by Client to Studio under the active Exhibit A SOW**. In no event shall Studio be liable for any indirect, incidental, consequential, or lost-profit damages.

### 10. Governing Law & Signatures

This Agreement shall be governed by and construed in accordance with the laws of the **Republic of the Philippines**, with venue in the proper courts of `[Metro Manila / City, Philippines]`. Electronic signatures are binding.

| For `[Studio Name]` (Provider) | For `[Client Company]` (Client) |
| :--- | :--- |
| **Signature:** \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ | **Signature:** \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |
| **Name / Title:** `[Your Name], Lead Architect` | **Name / Title:** `[Client Name, Title]` |
| **Date:** `[Date]` | **Date:** `[Date]` |

---

## Part 2: Exhibit A — Statement of Work (SOW)

* **Project Name:** `[Project Name]`
* **Client:** `[Client Company]`
* **Selected Base Package:** `[ ] Package A ($2,000)` | `[ ] Package B ($4,500)` | `[ ] Package C ($8,000–$12,000)`

### 1. Selected Architecture Configuration

* **Frontend Pattern:** `[ ] Next.js SSR (SEO)` | `[ ] Vite + React SPA (Dashboard)` | `[ ] Real-Time (WebSockets/SSE)`
* **Backend Engine:** `[ ] Unified TypeScript (Node/Next.js)` | `[ ] ASP.NET Core (.NET 10)`
* **Cloud Target (OpenTofu):** `[ ] Hetzner Cloud` | `[ ] DigitalOcean` | `[ ] AWS`

### 2. Locked Scope (Screens & Core Flow)

* **Primary End-to-End Flow:** `[e.g., User signs up -> creates workspace -> subscribes via Stripe -> manages items]`
* **Included Screens (Max 5 for Package B):**
  1. `[Screen 1 — e.g., Landing & Pricing]`
  2. `[Screen 2 — e.g., Auth / Login]`
  3. `[Screen 3 — e.g., Main Dashboard & CRUD Table]`
  4. `[Screen 4 — e.g., Billing & Settings]`
  5. `[Screen 5 — e.g., Detail / Profile View]`
* **Selected Add-Ons:** `[None / List add-ons + prices from Offer Catalog]`

### 3. Schedule & Financial Summary

* **Delivery Window:** `[Start Date]` → `[Target Handover Date — 30 Calendar Days]`
  * *Week 1:* Scope lock, client account prep, staging & DB schema setup
  * *Week 2:* Core engineering sprint (10 active build days)
  * *Week 3:* Client staging QA & polish
  * *Week 4:* Final payment → OpenTofu production deploy, repo transfer & Loom walkthrough
* **Total SOW Fee:** **`$[Total] USD`**
  * **Deposit Due on Signing (50%):** `$[Half] USD`
  * **Final Balance Due on Staging Sign-Off (50%):** `$[Half] USD`
* **Post-Launch Care Selection (Optional):** `[ ] Self-Managed ($0)` | `[ ] Peace of Mind ($450/mo)` | `[ ] Growth Sprint ($1,500/mo)`
