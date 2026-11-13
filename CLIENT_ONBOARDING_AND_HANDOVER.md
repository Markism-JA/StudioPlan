# Client Onboarding & Production Handover Checklist

> Operational playbook for `[Studio Name]`. Send **Part 1** to the client immediately after signing `MSA_SOW_TEMPLATE.md` and paying the 50% deposit. Use **Part 2** and **Part 3** internally + on the Day 30 handover call.

---

## Part 1: Day 1 Client Onboarding (Send to Client)

Welcome to `[Studio Name]`! To keep your accounts secure and hit our 30-day delivery target, please complete these steps during **Week 1 (Days 1–3)**.

> **Security Rule:** Never email us your root passwords or credit card details. You own 100% of your accounts and will issue temporary, scoped developer access only when needed.

### 1. Project Assets & Scope Lock
- [ ] Signed **MSA + Exhibit A (SOW)** returned
- [ ] **50% Deposit** cleared
- [ ] Brand assets shared (Logo SVG/PNG, primary hex colors, domain name)
- [ ] Figma designs / wireframes / copy shared *(or UI/UX Design Pack confirmed)*
- [ ] **30-minute Kickoff Call** completed — Week 1 scope locked

### 2. Accounts to Create on Your Company Card
Create these accounts under your company email so all billing stays in your name:

- [ ] **GitHub Organization** *(Free tier)* — We will transfer the production repo here on Day 30.
- [ ] **Cloud Provider** *(Pick your SOW target)*:
  - **Hetzner Cloud** *(~$5–$20/mo)* — Create a dedicated Project for this app.
  - **DigitalOcean** *(~$15–$40/mo)* — Create a dedicated Team/Project.
  - **AWS** *(~$60–$150/mo)* — Create a dedicated AWS account or IAM sub-account.
- [ ] **Domain & DNS** — Point domain nameservers to **Cloudflare** *(Free tier)* for SSL and DDoS protection.
- [ ] **Payments** — **Stripe** *(or Lemon Squeezy)* account activated and business-verified.
- [ ] **Transactional Email** — **Resend** *(Free tier up to 3,000 emails/mo)* with your domain DNS verified.

*(Note: You do **not** need to hand over cloud tokens on Day 1. We build on our isolated staging server first and only request your scoped deployment token on Day 30 after final sign-off.)*

---

## Part 2: Staging QA & Acceptance (Days 16–22)

- [ ] Studio deploys completed sprint build to `staging-[client].[studio.dev]`
- [ ] Studio sends client test login credentials + Swagger/OpenAPI URL
- [ ] Client tests all Exhibit A screens and core user flow (**5-business-day acceptance window**)
- [ ] Team resolves any reproducible bugs or minor UI tweaks
- [ ] Client signs off on staging build → **Final 50% invoice issued**

---

## Part 3: Day 30 Production Handover (45-Minute Live Sequence)

**Gate:** Do **not** begin Step 1 until the **final 50% payment** has cleared.

### 1. Scoped Token Setup (10 mins)
Client generates temporary, scoped credentials and pastes them into **GitHub Repository Secrets** (never in chat/email):
- [ ] **Cloud Token:**
  - *Hetzner:* Project API Token (`Read & Write`)
  - *DigitalOcean:* Scoped Personal Access Token (`Write`)
  - *AWS:* Dedicated IAM user (`studio-deployer`) with `AWS_ACCESS_KEY_ID` & `AWS_SECRET_ACCESS_KEY`
- [ ] **Production App Secrets:** Live `STRIPE_SECRET_KEY`, `STRIPE_WEBHOOK_SECRET`, `RESEND_API_KEY`, `OAUTH_CLIENT_ID/SECRET`

### 2. OpenTofu Production Provisioning (15 mins)
- [ ] Transfer private GitHub repository to Client’s **GitHub Organization**
- [ ] Trigger production **OpenTofu (`tofu apply`)** + GitHub Actions deploy pipeline
- [ ] Verify VPC/firewall rules (ports `80`/`443` open, DB/Redis ports locked private)
- [ ] Verify automated daily `pg_dump` backup cron job to encrypted bucket
- [ ] Verify `/api/health` returns `200 OK`

### 3. DNS Cutover & Live Smoke Test (10 mins)
- [ ] Client updates Cloudflare DNS `A` record to the new production server IP
- [ ] Confirm HTTPS/SSL certificate is active
- [ ] Run 1 live end-to-end smoke test (Sign up → Core CRUD flow → Stripe checkout webhook)

### 4. Handover Artifacts & Token Rotation (10 mins)
- [ ] Confirm `README.md` runbook + `/swagger` OpenAPI docs are up to date in the repo
- [ ] Record & send **10-minute Loom walkthrough** (codebase tour, local Docker run, CI/CD deploy, DB restore)
- [ ] **Client Security Action:** Client revokes/rotates the temporary Cloud API Token / IAM user used during handover
- [ ] **14-day bug warranty** clock starts *(Day 30 → Day 44)*
- [ ] Confirm post-launch choice: **Self-Managed ($0/mo)** or **Peace of Mind Care Plan ($450/mo)**
