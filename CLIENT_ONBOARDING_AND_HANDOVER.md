# Client Onboarding & Staged Production Handover Checklist

> Operational playbook for `[Studio Name]`. Send **Stage 0 & Stage 1** to the client upon signing `MSA_SOW_TEMPLATE.md`. Use **Stage 2, Stage 3, and Stage 4** internally and during the Day 30 handover call.

---

## Stage 0 & Stage 1: Onboarding & Skeleton Gate (Days 1–5)

Welcome to `[Studio Name]`! To keep your accounts secure and hit our 30-day delivery target, please complete these steps during **Days 1–3**.

> **Security Rule:** Never email us your root passwords or credit card details. You own 100% of your accounts and will issue temporary, scoped developer access only during Stage 4 handover.

### 1. Stage 0 Entry Gate (Pre-Sprint Lock)
- [ ] Signed **MSA + Exhibit A (SOW)** returned (with 5-Screen Complexity Budget locked)
- [ ] **50% Deposit** cleared *(Wise / Bank Wire / USDC at 0% fee, or Stripe Card at +3.5%)*
- [ ] Brand assets shared (Logo SVG/PNG, primary hex colors, domain name)
- [ ] Figma designs / wireframes / copy shared *(or UI/UX Design Pack confirmed)*

### 2. Accounts to Create on Your Company Card (Days 1–3)
Create these accounts under your company email so all billing stays in your name:
- [ ] **GitHub Organization** *(Free tier)* — We transfer the production repo here at Stage 4.
- [ ] **Cloud Provider** *(Pick your SOW target)*:
  - **Hetzner Cloud** *(~$5–$20/mo)* — Create a dedicated Project + S3/R2 bucket for state & backups.
  - **DigitalOcean** *(~$15–$40/mo)* — Create a dedicated Project + Spaces bucket.
  - **AWS** *(~$60–$150/mo)* — Create a dedicated AWS account + S3 bucket.
- [ ] **Domain & DNS** — Point domain nameservers to **Cloudflare** *(Free tier)* for SSL and DDoS protection.
- [ ] **Payments** — **Stripe** *(or Lemon Squeezy)* account created (note: third-party business KYC reviews run on Stripe's timeline and do not delay staging delivery).
- [ ] **Transactional Email** — **Resend** *(Free tier up to 3,000 emails/mo)* with your domain DNS verified.

### 3. Stage 1 Exit Gate: Day 5 Skeleton Sign-Off
- [ ] Studio Lead approves 1-page DB Schema & API Brief
- [ ] Studio deploys clickable route skeleton to `staging-[client].[studio.dev]`
- [ ] **Client signs off on Stage 1 Scope Freeze** (locking routes and fields before Stage 2 core build)

---

## Stage 2 & Stage 3: Build & Staging Acceptance Gate (Days 6–22)

> **⚠️ Ephemeral Staging Warning:** `staging-[client].[studio.dev]` is a temporary test sandbox running on **test-mode Stripe/API keys**. All data entered on staging is **wiped and not migrated to production**. Do not enter real customer records or live payments until Stage 4 production cutover.

### 1. Stage 2 Exit Gate (Internal — Day 15)
- [ ] All Exhibit A screens, primary user flow, and Stripe test-mode webhooks implemented
- [ ] Automated CI unit & integration tests passing (`ci.yml` green)
- [ ] Lead Architect PR & QA sign-off completed *(Triggers Builder Tranche 1 — 40% payout)*

### 2. Stage 3 Acceptance Gate (Client — Days 16–22)
- [ ] Studio sends client staging login credentials + `/swagger` OpenAPI URL
- [ ] Client tests all Exhibit A screens using sandbox/test-mode credentials (**5-business-day acceptance window**)
- [ ] Team completes **up to 2 consolidated rounds** of in-scope UI/copy revisions
- [ ] **Stage 3 Exit Gate:** Client signs off on staging build → **Final 50% invoice issued & cleared**

---

## Stage 4: Production Cutover & Warranty Gate (Days 23–30)

**Hard Gate:** Do **not** begin Step 1 until the **final 50% payment** has cleared in the studio account.

### 1. Scoped Token & Remote State Setup (10 mins)
Client pastes temporary credentials into **GitHub Repository Secrets** (never in chat/email):
- [ ] **Cloud Provisioning Token (for `provision-infra.yml`):**
  - *Hetzner:* Project API Token (`Read & Write`)
  - *DigitalOcean:* Scoped Personal Access Token (`Write`)
  - *AWS:* Dedicated IAM user (`studio-deployer`)
- [ ] **Remote OpenTofu State & Backup Bucket Keys:** S3 / Cloudflare R2 bucket credentials (`TF_STATE_BUCKET`, `R2_ACCESS_KEY_ID`, `R2_SECRET_ACCESS_KEY`) so `terraform.tfstate` and daily `pg_dump` backups live inside Client's account.
- [ ] **App Deploy Key (for `deploy-app.yml`):** Scoped SSH deploy key / webhook secret for zero-downtime `ghcr.io` container updates.
- [ ] **Production App Secrets:** Live `STRIPE_SECRET_KEY`, `STRIPE_WEBHOOK_SECRET`, `RESEND_API_KEY`, `OAUTH_CLIENT_ID/SECRET`.

### 2. OpenTofu Provisioning & App Rollout (15 mins)
- [ ] Transfer private GitHub repository to Client’s **GitHub Organization**
- [ ] Run **`provision-infra.yml`** (`tofu apply` backed by Client’s remote S3/R2 state bucket)
- [ ] Run **`deploy-app.yml`** (builds image to `ghcr.io` and rolls out production containers)
- [ ] Verify VPC/firewall (`80`/`443` open, DB/Redis locked private), daily `pg_dump` cron, and `/api/health` (`200 OK`)

### 3. DNS Cutover & Live Smoke Test (10 mins)
- [ ] Client updates Cloudflare DNS `A` record to the new production server IP
- [ ] Confirm HTTPS/SSL certificate is active and run 1 live smoke test

### 4. Handover Artifacts, Token Rotation & Warranty Start (10 mins)
- [ ] Confirm `README.md` runbook + `/swagger` OpenAPI docs are live in the repo
- [ ] Deliver **10-minute Loom walkthrough** (codebase tour, local Docker run, `provision-infra.yml` vs `deploy-app.yml`, DB restore)
- [ ] **Client Security Action:** Client **revokes the temporary Cloud Provisioning API Token** (`HCLOUD_TOKEN` / `DIGITALOCEAN_TOKEN` / `studio-deployer`).
  - * Note:* Because `deploy-app.yml` uses the scoped SSH/container deploy key rather than the cloud admin token, normal code pushes to `main` continue deploying smoothly!
  - *If on Peace of Mind ($450/mo) or Growth Retainer ($1,500/mo):* Client retains the studio's scoped monitoring & deploy access.
  - *If Self-Managed ($0/mo):* Client removes studio team from GitHub Org after the **14-day bug warranty** closes on Day 44 *(post-warranty emergency support billed at $100/hr, 4h min)*.
