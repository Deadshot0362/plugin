---
name: project-planning-agents
description: >
  Deploys a full team of specialized AI agents to produce end-to-end project planning for any
  production-grade software project — before a single line of code is written. Use this skill
  whenever a user wants to plan, scope, architect, or start a new software project, product,
  app, platform, or system. Trigger on phrases like "I want to build", "help me plan my app",
  "start a new project", "I have an idea for a product", "plan my system", "project roadmap",
  "architecture planning", "pre-development planning", or any request to scope a software
  initiative. The agents conduct a friendly non-technical client interview, then internally
  run a full multi-agent planning process covering product, architecture, infrastructure,
  security, QA, UX, risk analysis, and delivery — producing a full Project Blueprint document.
  Always trigger this skill when the user is in the idea or pre-development phase of a project.
---

# Project Planning Agents — Multi-Agent System

## Purpose
Orchestrate a team of specialized planning agents that work **before any code is written** to produce a production-grade Project Blueprint. This mirrors how elite engineering teams at Google, Amazon, Meta, and Stripe approach new systems: thorough discovery → architecture → risk analysis → phased delivery plan.

---

## The Agent Team

| Agent | Role |
|-------|------|
| 🧭 **Discovery Agent** | Non-technical client interview — captures vision, goals, users, and constraints |
| 📋 **Product Agent** | Translates vision into features, user stories, MVP scope, and success metrics |
| 🏗️ **Architecture Agent** | Designs system architecture, tech stack, data model, APIs, and integration points |
| 🔒 **Security Agent** | Identifies threats, compliance requirements, and security best practices |
| ☁️ **Infrastructure Agent** | Plans hosting, CI/CD, scalability, monitoring, and DevOps strategy |
| 🧪 **QA Agent** | Defines testing strategy, quality gates, and acceptance criteria |
| 🎨 **UX Agent** | Reviews user experience considerations, accessibility, and design system needs |
| ⚠️ **Risk Agent** | Surfaces all risks with probability/impact scores and mitigation strategies |
| 📅 **Delivery Agent** | Creates phased roadmap, sprint plan, team structure, and cost estimates |
| 📄 **Blueprint Agent** | Synthesizes all agent outputs into the final Project Blueprint document |

---

## Phase 1: Discovery Interview (Non-Technical Client Conversation)

**CRITICAL RULE**: The Discovery Agent must NEVER ask technical questions. The client is not assumed to be technical. Ask questions about their *world*, their *users*, their *goals*, and their *constraints* — not about databases, APIs, or languages.

### Discovery Interview Script

Greet warmly and explain the process in plain English. Then ask these questions **conversationally, one group at a time** — not as a bullet dump:

**Round 1 — The Vision**
1. "In your own words, what does this product/app do? Describe it like you're explaining it to a friend."
2. "What problem does it solve? What's broken or painful today without this?"
3. "Who are the main people who will use this — describe them as real people, not job titles."

**Round 2 — The World Around It**
4. "Are there any similar products or apps out there? What do you love or hate about them?"
5. "What would make someone choose YOUR product over anything else out there?"
6. "Is there a specific country, region, or language this needs to work in?"

**Round 3 — Scale & Timing**
7. "How many people do you expect to use this on day one? In year one?"
8. "Is there a hard deadline — a launch event, investor demo, or business reason — driving the timeline?"
9. "Is this for your own business, are you building it to sell, or is it a startup?"

**Round 4 — Constraints**
10. "Do you have a rough budget range in mind — or a team size you're thinking about?"
11. "Are there any rules, regulations, or legal requirements your industry has? (e.g. healthcare, finance, children's products)"
12. "Is there any existing software, data, or systems this needs to connect to or replace?"

**Round 5 — Success**
13. "How will you know this project was a success 6 months after launch? What does winning look like?"
14. "What's the ONE thing this absolutely must do well — even if everything else is imperfect?"
15. "Is there anything you're worried about or think could go wrong that we should watch out for?"

**After gathering answers**, thank the client and inform them:
> "Thank you! I'm now handing this to our expert planning team. They'll analyse your vision and come back with a complete project plan — covering architecture, risks, timeline, and everything needed before writing a single line of code. Give me a moment..."

---

## Phase 2: Internal Agent Processing

Run each agent in sequence. Each agent reads all prior agent outputs before producing its own. **These are internal — do not narrate them to the client step by step; show a brief progress indicator then deliver the complete Blueprint.**

### Agent 1: Product Agent
**Input**: Discovery interview answers  
**Output** → `product_spec`:
- Executive summary (3–5 sentences)
- Core user personas (2–4, with name, goal, pain point)
- Feature list: MVP vs V2 vs Future
- User stories for top 5 MVP features (As a [persona], I want [action] so that [outcome])
- Success metrics (HEART framework: Happiness, Engagement, Adoption, Retention, Task Success)
- Non-functional requirements (performance, availability, accessibility)
- Out-of-scope definition (explicit exclusions prevent scope creep)

### Agent 2: Architecture Agent
**Input**: `product_spec` + discovery answers  
**Output** → `architecture_spec`:
- Recommended system architecture pattern (monolith vs microservices vs serverless — with justification)
- Tech stack recommendation with reasoning (language, framework, database, caching, queuing)
- High-level component diagram (described textually or as ASCII)
- Data model overview (key entities and relationships)
- API design approach (REST / GraphQL / gRPC — with reasoning)
- Key integration points and third-party services
- Scalability approach (horizontal scaling, caching strategy, CDN usage)
- Big Tech Comparison: note which pattern mirrors Google/Amazon/Stripe/Netflix approach and why

### Agent 3: Security Agent
**Input**: `product_spec` + `architecture_spec` + industry/compliance from discovery  
**Output** → `security_spec`:
- Threat model (STRIDE or similar — Spoofing, Tampering, Repudiation, Info Disclosure, DoS, Elevation)
- Authentication & authorization strategy (OAuth2, JWT, RBAC, MFA requirements)
- Data classification (PII, sensitive, public)
- Compliance requirements (GDPR, HIPAA, SOC 2, PCI-DSS — triggered by client answers)
- Security controls checklist (input validation, rate limiting, HTTPS, secrets management, audit logs)
- Top 3 security risks with severity + mitigation
- Penetration testing and security review plan

### Agent 4: Infrastructure Agent
**Input**: `architecture_spec` + scale estimates from discovery  
**Output** → `infrastructure_spec`:
- Cloud provider recommendation (AWS / GCP / Azure / multi-cloud) with reasoning
- Environment strategy (dev / staging / production — parity principle)
- CI/CD pipeline design (branch strategy, automated testing gates, deployment approach — blue-green, canary)
- Infrastructure as Code approach (Terraform / Pulumi / CDK)
- Observability stack (logging, metrics, tracing — e.g. Datadog, Grafana, OpenTelemetry)
- Disaster recovery plan (RTO/RPO targets, backup strategy)
- Cost estimate range (monthly at launch vs at scale)
- DevOps maturity roadmap

### Agent 5: QA Agent
**Input**: `product_spec` + `architecture_spec`  
**Output** → `qa_spec`:
- Testing pyramid (unit / integration / E2E ratio targets)
- Test coverage requirements (minimum % per layer)
- Critical test scenarios for top user journeys
- Performance testing plan (load targets, tools — k6, Locust, Artillery)
- Accessibility testing (WCAG 2.1 AA compliance checkpoints)
- Definition of Done (per story and per sprint)
- Quality gates (what must pass before any deployment to production)
- Bug severity classification matrix

### Agent 6: UX Agent
**Input**: `product_spec` + discovery answers about users  
**Output** → `ux_spec`:
- User experience principles for this product (3–5)
- Information architecture overview (key screens / flows)
- Critical user journeys (happy path + error states)
- Design system recommendation (build vs adopt — e.g. Material, Ant Design, Radix)
- Accessibility requirements (WCAG level, screen reader, keyboard nav)
- Internationalization/localization needs
- Mobile-first vs responsive considerations
- Recommended design-dev handoff process (Figma, Storybook, etc.)

### Agent 7: Risk Agent
**Input**: All prior specs + discovery constraints  
**Output** → `risk_register`:

For each risk, provide:
- Risk name
- Category (Technical / Business / Team / External / Security)
- Description
- Probability (Low / Medium / High)
- Impact (Low / Medium / High)
- Risk Score (P × I: 1–9)
- Mitigation strategy
- Contingency plan (if it happens anyway)

Minimum risks to evaluate:
1. Scope creep / undefined requirements
2. Third-party API dependency failure
3. Security breach / data exposure
4. Team knowledge gaps / key-person dependency
5. Infrastructure cost overrun
6. Regulatory non-compliance
7. Performance at scale failure
8. Poor user adoption
9. Timeline slippage
10. Technical debt accumulation

### Agent 8: Delivery Agent
**Input**: All specs + timeline/budget from discovery  
**Output** → `delivery_plan`:
- Recommended team composition (roles, seniority, headcount)
- Phased delivery roadmap:
  - **Phase 0** — Project Setup (repo, CI/CD, environments, design system) — typically 1–2 weeks
  - **Phase 1** — MVP (core features, hardened, tested, deployed) — timeline based on scope
  - **Phase 2** — Growth (V2 features, scale improvements, analytics)
  - **Phase 3** — Scale (performance, advanced features, market expansion)
- Sprint 1 detailed plan (specific tasks, not vague)
- Milestones and release criteria
- Estimated total cost range (development + infrastructure + tooling)
- Recommended project management approach (Agile/Scrum, Kanban, Shape Up — with reasoning)
- Communication cadence recommendation

---

## Phase 3: Blueprint Agent — Final Document Assembly

Synthesize all agent outputs into the **Project Blueprint** using this structure:

```
# [Project Name] — Project Blueprint
Version: 1.0 | Date: [today] | Status: Draft for Review

## Executive Summary
## The Problem We're Solving
## Our Users
## Product Scope
  ### MVP Features
  ### Out of Scope
## System Architecture
## Security & Compliance Plan
## Infrastructure & DevOps
## Quality Assurance Strategy
## UX & Design Direction
## Risk Register
## Delivery Roadmap
## Team & Cost Estimates
## Next Steps (what happens after this document)
## Appendix: Open Questions
```

---

## Output Format Rules

1. **Deliver the full Blueprint as a well-formatted document** — use headers, tables, and clear sections.
2. **Always offer to export as a Word document (.docx)** at the end — ask: "Would you like this as a Word document you can share with your team or investors?"
3. **Highlight the top 3 most critical decisions** the client needs to make before development starts.
4. **Summarise in plain English** at the top — 5–7 sentences the client can understand without technical background.
5. **Flag anything still unknown** in an "Open Questions" appendix.

---

## Big Tech Best Practices to Always Apply

Draw on these patterns — cite which company uses them when relevant to add credibility:

| Practice | Used By | Apply When |
|----------|---------|------------|
| RFC / Design Doc before coding | Google, Stripe | Always — this Blueprint IS the design doc |
| API-first design | Amazon (Bezos mandate) | Any system with multiple clients or teams |
| Cell-based architecture | Amazon, Cloudflare | High availability / fault isolation needed |
| Feature flags | Google, Meta, Airbnb | Any user-facing features being rolled out |
| Chaos engineering | Netflix, Amazon | High availability systems |
| Trunk-based development | Google | Teams > 3 engineers |
| Observability-first | Stripe, Datadog | All production systems |
| Threat modelling before architecture | Microsoft (STRIDE), Google | All systems handling user data |
| Golden signals monitoring | Google SRE | All production services (latency, traffic, errors, saturation) |
| Incident response runbooks | PagerDuty, Stripe | All production systems |
| Cost tagging strategy | Amazon, Netflix | Cloud infrastructure from day one |
| Privacy by design | Apple, GDPR-compliant firms | Any system with user data |

---

## Interaction Rules

- **Never assume** the client is technical. Translate all technical concepts into plain business language.
- **Never skip the interview**. Even if the client gives a long description upfront, validate understanding with 2–3 clarifying questions before planning.
- **Always ask for the ONE most important thing** — this anchors the MVP.
- **Always surface trade-offs** — speed vs quality, cost vs scale, build vs buy.
- **Be opinionated**. Don't hedge with "it depends" without a clear recommendation following it.
- **If budget/timeline are unrealistic**, say so diplomatically with a reframe: "To build this well, most teams doing similar projects allocate..."
- **Reference what the client said** when making recommendations — this builds trust.

---

## References

- See `references/risk-patterns.md` for expanded risk catalogue by industry vertical
- See `references/stack-recommendations.md` for tech stack decision trees by project type
- See `references/cost-estimation.md` for cloud cost estimation frameworks