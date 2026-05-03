# Risk Patterns by Industry Vertical

## E-Commerce / Marketplace
- Payment fraud and chargebacks (High impact)
- Inventory sync failures across channels
- Cart abandonment at checkout (UX/performance)
- PCI-DSS compliance scope creep
- Third-party shipping API reliability
- Flash sale traffic spikes (infrastructure)
- Returns/refunds logic complexity
- Seller onboarding fraud

## Healthcare / MedTech
- HIPAA compliance (USA) / MDR (EU) — very high stakes
- PHI data breach — regulatory and reputational catastrophe
- Integration with EHR systems (HL7, FHIR) — extreme complexity
- Clinical workflow disruption during rollout
- FDA software device classification risk
- Offline/low-connectivity clinical environments
- Audit trail completeness requirements

## FinTech / Payments
- KYC/AML compliance requirements (varies by country)
- PCI-DSS Level 1 if processing cards directly
- Fraud model accuracy — false positives hurt users, false negatives cost money
- Banking API reliability (Plaid, Open Banking)
- Real-time settlement latency requirements
- Regulatory sandbox vs production licensing
- Currency and tax calculation complexity

## SaaS / B2B
- Enterprise SSO integration complexity (SAML, OIDC)
- Multi-tenancy data isolation bugs
- Customer data portability requirements
- SLA commitments driving infrastructure costs up
- Long enterprise sales cycle vs runway
- SOC 2 Type II timeline (6+ months of audit evidence needed)
- Pricing model complexity (seats, usage, feature tiers)

## Consumer Mobile Apps
- App store review delays and rejections
- Push notification deliverability
- Device fragmentation (iOS/Android version spread)
- Cold start performance on low-end devices
- Viral growth infrastructure not ready
- App store 30% commission impact on business model
- User data privacy (ATT on iOS, consent frameworks)

## EdTech
- COPPA compliance if serving under-13s
- FERPA compliance for student data
- Accessibility requirements (Section 508 for US public schools)
- Content moderation at scale
- Teacher/student dual-role complexity
- LMS integration (Canvas, Google Classroom, Blackboard)
- Engagement and retention — edtech has notoriously low completion rates

## Logistics / Supply Chain
- Real-time tracking data volume and latency
- Third-party carrier API reliability
- Address validation and geocoding accuracy
- Cross-border regulatory complexity
- Warehouse system integration (WMS) complexity
- Proof of delivery and chain of custody requirements
- Fuel/cost volatility affecting pricing models

## Social / Community Platforms
- Content moderation at scale (the hardest unsolved problem)
- CSAM and illegal content detection obligations
- DSA (EU Digital Services Act) compliance
- Viral traffic spikes — infrastructure must auto-scale
- User-generated content copyright exposure
- Network effects — product worthless without users (cold start)
- Algorithm transparency requirements growing

## AI / ML Products
- Model hallucination and accuracy drift
- Training data licensing and copyright
- AI Act (EU) compliance and risk classification
- Explainability requirements in regulated industries
- GPU/inference cost at scale (can be shocking)
- Bias and fairness testing requirements
- Model versioning and rollback strategy