# Tech Stack Recommendations by Project Type

## Decision Principles
1. **Choose boring technology** (Dan McKinley) — proven > novel for production
2. **Match team expertise** — a great team with familiar tools beats a perfect stack with unfamiliar ones
3. **Buy vs build** — use managed services for undifferentiated heavy lifting (auth, email, payments)
4. **One new thing at a time** — don't adopt multiple new technologies simultaneously

---

## Web Application (Content-heavy, SEO important)
**Frontend**: Next.js (React) — SSR/SSG for SEO, large ecosystem
**Backend**: Node.js (TypeScript) or Python (FastAPI/Django)
**Database**: PostgreSQL (primary) + Redis (caching/sessions)
**Auth**: Auth0 or Clerk (buy, don't build)
**Hosting**: Vercel (frontend) + Railway/Render or AWS/GCP (backend)
**CDN**: Cloudflare
**Used by**: Vercel, Linear, Cal.com

## SaaS B2B Platform
**Frontend**: Next.js or Remix
**Backend**: Node.js/TypeScript or Go (for performance)
**Database**: PostgreSQL + Redis
**Queue**: BullMQ (Node) or Celery (Python) for async jobs
**Auth**: Auth0, WorkOS (for enterprise SSO/SCIM)
**Payments**: Stripe (always Stripe for SaaS billing)
**Monitoring**: Datadog or Grafana + OpenTelemetry
**Hosting**: AWS (ECS Fargate or EKS for scale) or GCP
**Used by**: Stripe, Linear, Notion (conceptually)

## Mobile App (iOS + Android)
**Cross-platform**: React Native (Expo) — faster iteration, good for most apps
**Native**: Swift/SwiftUI + Kotlin (when performance/platform features critical)
**Backend**: Same as SaaS above
**Push Notifications**: Firebase Cloud Messaging (FCM)
**Analytics**: Mixpanel + Amplitude
**Crash Reporting**: Sentry
**OTA Updates**: Expo EAS (React Native only)
**Used by**: Shopify, Discord (React Native for parts)

## High-Scale Consumer Platform (millions of users)
**Frontend**: Next.js with edge rendering
**Backend**: Go or Java (Spring Boot) for core services — performance matters
**Database**: PostgreSQL (primary) + Cassandra or DynamoDB (for write-heavy workloads) + Redis Cluster
**Message Queue**: Apache Kafka (event streaming at scale)
**Search**: Elasticsearch or Algolia
**CDN**: Cloudflare or AWS CloudFront
**Infra**: Kubernetes (EKS/GKE) — terraform-managed
**Observability**: Datadog or Grafana + Prometheus + OpenTelemetry
**Used by**: Uber, Airbnb, Netflix (conceptually)

## Data / Analytics Platform
**Ingestion**: Apache Kafka or AWS Kinesis
**Processing**: Apache Spark or dbt + Airflow for orchestration
**Warehouse**: Snowflake, BigQuery, or Redshift
**BI / Dashboards**: Metabase (internal) or Tableau/Looker (enterprise)
**API Layer**: FastAPI (Python) or GraphQL
**ML Serving**: FastAPI + BentoML or AWS SageMaker
**Used by**: Airbnb (Minerva), Spotify (Luigi)

## AI / LLM-powered Product
**Framework**: LangChain / LlamaIndex (orchestration) — or custom if control needed
**LLM Provider**: Anthropic Claude API or OpenAI — multi-provider abstraction recommended
**Vector Database**: Pinecone, Weaviate, or pgvector (simpler — Postgres extension)
**Backend**: Python (FastAPI) — Python owns the AI ecosystem
**Streaming**: Server-Sent Events (SSE) for streaming responses to frontend
**Observability**: LangSmith or Langfuse for LLM tracing
**GPU Inference**: Modal, Replicate, or AWS SageMaker (for custom models)

## Marketplace / Two-sided Platform
**Same as SaaS stack PLUS:**
**Payments**: Stripe Connect (marketplace payments — handles payouts to sellers)
**Search**: Algolia or Elasticsearch (faceted search is critical)
**Image Storage**: Cloudinary (managed image transforms + CDN)
**Maps**: Google Maps API or Mapbox
**Trust & Safety**: Sift Science or custom ML fraud detection
**Used by**: Airbnb, Etsy, Upwork (architecturally)

---

## Buy vs Build Decision Matrix

| Function | Always Buy | Consider Building |
|----------|-----------|------------------|
| Authentication | Auth0, Clerk, Supabase Auth | Never |
| Payments | Stripe, Braintree | Never (unless > $1B GMV) |
| Email delivery | SendGrid, Postmark, Resend | Never |
| SMS | Twilio, AWS SNS | Never |
| Search | Algolia, Typesense | If data never leaves your infra |
| PDF generation | Puppeteer/hosted service | Simple cases |
| Video processing | Cloudinary, Mux | Rarely |
| Feature flags | LaunchDarkly, Unleash | Small teams OK |
| Error tracking | Sentry | Never |
| Monitoring | Datadog, Grafana Cloud | Large teams, cost control |
| Analytics | Mixpanel, Amplitude, PostHog | PostHog self-hosted is great |
| Internal admin | Retool, Appsmith | If very custom |

---

## Database Selection Guide

| Need | Recommendation | Why |
|------|---------------|-----|
| Default / most apps | PostgreSQL | ACID, flexible, extensions (pgvector, PostGIS) |
| Simple key-value | Redis | Speed, TTL, pub/sub built in |
| Massive write scale | DynamoDB or Cassandra | Horizontal scale, eventual consistency OK |
| Full-text search | Elasticsearch or Postgres FTS | Depends on scale |
| Graph relationships | Neo4j or Amazon Neptune | Social graphs, recommendations |
| Time series | TimescaleDB (Postgres ext) or InfluxDB | Metrics, IoT, financial data |
| Document / flexible schema | MongoDB | Only if schema truly unknown upfront |
| Analytics / OLAP | BigQuery, Snowflake | Never use OLTP DB for analytics at scale |