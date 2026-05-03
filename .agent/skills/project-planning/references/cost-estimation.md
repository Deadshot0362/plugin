# Cost Estimation Framework

## Principles
- Always present as **ranges**, never false precision
- Quote in **monthly cost** (easier for clients to budget)
- Separate **development cost** (one-time) from **operational cost** (recurring)
- Include **tooling and SaaS** — often underestimated by 40–60%
- Apply **1.3× buffer** on all estimates (unknown unknowns)

---

## Development Cost Ranges by Project Type

### MVP (3–4 months, small team)
| Team Composition | Monthly Cost | 4-Month Total |
|-----------------|-------------|---------------|
| 1 senior full-stack (freelance) | $8K–$15K/mo | $32K–$60K |
| 2 engineers + 1 designer (agency) | $25K–$50K/mo | $100K–$200K |
| 3–4 engineers (small startup team) | $50K–$80K/mo | $200K–$320K |

### Full V1 Product (6–9 months)
| Team Composition | Monthly Cost | Total |
|-----------------|-------------|-------|
| Small team (4–6 people) | $60K–$120K/mo | $360K–$1.08M |
| Mid-size team (8–12 people) | $120K–$250K/mo | $720K–$2.25M |

*Note: Offshore/nearshore teams can reduce costs by 40–60% with quality trade-offs*

---

## Monthly Infrastructure Cost Ranges

### Stage 1: Early / MVP (< 1,000 users)
| Service | Monthly Cost |
|---------|-------------|
| Cloud hosting (1–2 servers) | $50–$200 |
| Database (managed PostgreSQL) | $20–$100 |
| CDN / bandwidth | $10–$50 |
| Redis (caching) | $15–$60 |
| Email service | $0–$30 |
| Monitoring (basic) | $0–$50 |
| **Total range** | **$100–$500/month** |

### Stage 2: Growth (1K–50K users)
| Service | Monthly Cost |
|---------|-------------|
| Cloud hosting (auto-scaling) | $300–$1,500 |
| Database (HA setup) | $150–$500 |
| CDN / bandwidth | $50–$300 |
| Redis cluster | $100–$400 |
| Monitoring / observability | $200–$800 |
| Storage (S3/GCS) | $20–$200 |
| **Total range** | **$800–$3,700/month** |

### Stage 3: Scale (50K–500K users)
| Service | Monthly Cost |
|---------|-------------|
| Cloud hosting (Kubernetes) | $2K–$10K |
| Database (multi-region) | $800–$3K |
| CDN / bandwidth | $500–$2K |
| Data/analytics pipeline | $500–$2K |
| Security tooling | $300–$1K |
| Monitoring / alerting | $500–$2K |
| **Total range** | **$4,600–$20,000/month** |

---

## SaaS Tooling Cost (Often Missed)

| Tool Category | Free Tier | Paid Start |
|--------------|-----------|------------|
| Error tracking (Sentry) | Yes (5K errors) | $26/mo |
| Auth (Auth0 / Clerk) | Yes (7.5K MAU) | $25–$200/mo |
| Feature flags (LaunchDarkly) | No | $200/mo |
| CI/CD (GitHub Actions) | 2,000 min/mo | $4/user/mo |
| Design (Figma) | Yes | $15/editor/mo |
| Analytics (Mixpanel) | Yes (20M events) | $28+/mo |
| Email (Postmark) | No | $15/10K emails |
| Payments (Stripe) | No fee | 2.9% + 30¢/transaction |
| SMS (Twilio) | No | ~$0.0079/SMS |
| Maps (Google Maps) | $200 credit/mo | ~$7/1K requests |

**Typical total SaaS tooling**: $300–$2,000/month for a growing startup

---

## Estimation Methodology (How to Estimate Dev Time)

### T-Shirt Sizing for Features
| Size | Days | Examples |
|------|------|---------|
| XS | 0.5–1 | Simple CRUD form, static page |
| S | 1–3 | User auth flow, basic API endpoint |
| M | 3–7 | Payment integration, complex form with validation |
| L | 7–14 | Real-time features, third-party deep integration |
| XL | 14–30 | ML feature, complex search, multi-step workflow |

### Overhead Multiplier
- Raw feature dev time × 1.5 = actual sprint time (meetings, code review, testing, bugs)
- Add 20% for project setup, infra, deployment pipeline
- Add 15% for documentation, technical debt, discovery spikes
- **Total multiplier: ~1.85× raw estimates**

### MVP Scope Heuristic
A well-scoped MVP typically contains:
- 3–5 core user flows
- 1 integration (payment, auth, or key API)
- Basic admin/ops tooling
- ~60–90 days of focused development (2–4 engineers)

---

## Red Flags That Indicate Underestimation
- "It's just like Airbnb but for X" — Airbnb has 3,000+ engineers
- "We just need a simple app" — nothing is simple in production
- No budget allocated for testing, monitoring, or security
- No runway/buffer beyond the initial estimate
- Timeline driven by investor demo, not scope
- Real-time features assumed to be easy
- "We'll do compliance/security after launch" — it will cost 3× more