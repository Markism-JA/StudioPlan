# Studio Showcase & Golden Template Roadmap (4-Week Launch Plan)

> **Goal:** Build the `[Studio Name]` **Golden Starter Template**, deploy the **Studio Website + 4-Screen *PulseOps* Live Demo** on real production cloud infrastructure (`OpenTofu` + Hetzner + Cloudflare), and start closing Client #1 within 30 days.

---

## 1. Infrastructure & Launch Budget (~$10/mo Total)

* **Domain:** Custom `.dev` / `.io` domain via Cloudflare Registrar (**~$12/year**)
* **Cloud Compute:** Hetzner Cloud `CX22` (2 vCPU, 4GB RAM, 40GB NVMe) (**€3.79/mo / ~$4.15**)
* **DNS, CDN & SSL:** Cloudflare Free Tier (**$0**)
* **Studio Email:** Google Workspace (`$6/mo`) or Zoho Mail (`$1/mo`)
* **Transactional Email / Billing / Scheduling / Monitoring:** Resend (free tier), Stripe (test mode + live), Cal.com (free), BetterStack uptime alerts (free)

---

## 2. Target Architecture (Golden Template + *PulseOps* Demo)

Everything built for *PulseOps* becomes the **reusable Golden Template** forked for future Package A/B/C client sprints:

```text
[ studio.dev ] (Studio Landing Page + Offer Catalog + Cal.com Booking)
       │
       ▼
[ demo.studio.dev ] (*PulseOps* 4-Screen Live Demo)
  ├── /               (SSR SEO Landing + 3-Tier Pricing + FAQ)
  ├── /login          (Google OAuth + Email Magic Link + 1-Click Demo Login)
  ├── /dashboard      (KPIs, 7-Day Chart, Monitored Endpoints CRUD, SSE Live Feed)
  ├── /billing        (Real Stripe Test-Mode Checkout + Webhook -> Postgres Tier)
  └── /api/docs       (Interactive OpenAPI / Swagger Docs + /api/health)
       │
       ▼
[ OpenTofu IaC Module ] (modules/hetzner/ — later extended to DigitalOcean & AWS)
  ├── Ubuntu 24.04 + Docker Compose + Caddy (Auto-HTTPS)
  ├── PostgreSQL 16 + Redis (Locked to internal network)
  └── Daily encrypted pg_dump cron -> S3/R2 bucket
```

---

## 3. 4-Week Execution Schedule

### Week 1: Infra, OpenTofu Module & Golden Template

* **Accounts & Domain:** Buy `[studio.dev]`, configure Cloudflare DNS, set up `[hello@studio.dev]`, Stripe test mode, Resend, and Cal.com.
* **OpenTofu Module (`modules/hetzner`):** Provision `CX22` VPS, firewall (`80`/`443` open, `5432`/`6379` closed), Caddy reverse proxy, and automated daily `pg_dump` backup cron.
* **Golden Template Repo:**
  * Next.js + TypeScript + Tailwind/Shadcn UI + Drizzle/Prisma (or ASP.NET Core `.NET 10` backend variant)
  * Local `docker-compose.yml` (Postgres + Redis)
  * GitHub Actions CI/CD (unit/integration tests → Docker build → zero-downtime deploy)
  * `README_TEMPLATE.md` runbook

### Week 2: Build *PulseOps* (4-Screen Functional Demo)

* **Day 1–2:** Screen 1 (SSR Landing + Pricing) & Screen 2 (Auth + **1-Click Instant Demo Login**).
* **Day 3–4:** Screen 3 (KPI cards, 7-day area chart, real PostgreSQL CRUD table for Monitored Endpoints, SSE live latency/event feed).
* **Day 5:** Screen 4 (Stripe Test-Mode Checkout + webhook updating user plan in Postgres + `/api/docs` + `/api/health`).
* **Test Suite:** Add integration tests for Auth, Endpoint CRUD, and Stripe webhook handling.

### Week 3: Studio Website, QA & Sales Assets

* **Studio Landing Page (`[studio.dev]`):**
  * Hero (*"Production-Ready Web & Cloud MVPs Delivered in 30 Days"*)
  * Embedded preview + link to `demo.studio.dev`
  * Package A / B / C cards + Architecture Configurator summary + Cal.com booking widget
* **Deploy & Verify:** Run `tofu apply` to deploy both `[studio.dev]` and `demo.studio.dev` live; hook up BetterStack `/api/health` monitoring.
* **Record Loom Demo:** Record a crisp 2-minute walkthrough of *PulseOps* + OpenTofu provisioning for proposals and DMs.

### Week 4: Outreach Launch & Client #1 Pipeline

* **Channel 1 — Design Agency Partners:** Reach out to **5 boutique UI/UX / Figma studios per day** pitching the white-label engineering partnership (15–20% finder's fee).
* **Channel 2 — Upwork Sniper:** Send **3 tailored Loom video proposals per week** on `$3,000+` Fixed-Price MVP jobs (Payment Verified, `$10k+` client spend).
* **Channel 3 — Founder Communities:** Reply helpfully to stuck founders on X (`#buildinpublic`), Indie Hackers, and Reddit (`r/startups`, `r/SaaS`), offering a 15-min architecture scoping call.
* **Goal:** Book 3–5 discovery calls → close **Client #1** at `$3,000–$4,500` Founding Client rate.
