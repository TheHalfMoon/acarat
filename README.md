# Acarat

Acarat is a Saudi-first real-estate decision and transaction platform.

The product is being designed around five connected surfaces:

1. **Marketplace** — verified listings, property passports, maps, comparison, saved lists, alerts, and conversational search.
2. **Acarat Intelligence** — explainable rent, sale, and land valuation with comparable transactions, market ranges, confidence, and neighborhood context.
3. **Acarat Spatial** — 2D/3D maps, satellite/aerial imagery adapters, terrain/buildings, commute analysis, nearby services, and property digital-twin workflows.
4. **Agent Terminal** — customer CRM, listing analytics, tasks, conversations, contract lifecycle, renewals, pipeline management, and AI assistance.
5. **Saudi Trust & Transaction Rails** — regulatory identity, advertisement verification, government-integration adapters, auditability, and privacy-by-design.

## Planning state

This repository is at the canonical planning foundation. No production integration, government API, valuation accuracy claim, imagery right, or automated transaction capability is implied until the owning specification is implemented and proven.

## Engineering principles

- Saudi-first domain semantics and Arabic/RTL from the first implementation slice.
- PostgreSQL/PostGIS as durable transactional and geospatial truth.
- Go for the primary backend unless a bounded benchmark proves another runtime is materially better.
- Next.js/TypeScript for the web product and SEO surfaces.
- Python workers only for justified ML/data workloads behind versioned contracts.
- Explainable estimates with uncertainty; never present an unsupported point estimate as truth.
- Government/provider integrations remain adapters with explicit authority and failure states.
- Search, analytics, graph, vector, and 3D projections are rebuildable derivatives, not canonical property truth.
- Saved searches and notifications are durable user intent, not best-effort client state.
- Every consequential AI recommendation is grounded in source data and can abstain.
- SpecGrain and Diffcipline govern decomposition, implementation, and proof.

## Commercial direction

The initial marketplace can launch free. The currently proposed future agent tiers are:

- SAR 25/month — up to 20 active listings.
- SAR 50/month — up to 100 active listings.
- SAR 100/month — unlimited active listings subject to fair-use limits.

Subscription status must not buy organic ranking.

## Status

Planning foundation only. See the canonical planning documents on the planning branch for architecture, intelligence, geospatial, analytics, Agent Terminal, source qualification, and staged implementation gates.


## Canonical planning index

- [Master Vision](docs/canonical/ACARAT_MASTER_VISION.md)
- [Architecture Plan](docs/canonical/ACARAT_ARCHITECTURE_PLAN.md)
- [Intelligence and Valuation](docs/canonical/ACARAT_INTELLIGENCE_AND_VALUATION_PLAN.md)
- [Spatial, 3D, and Media](docs/canonical/ACARAT_SPATIAL_3D_AND_MEDIA_PLAN.md)
- [Consumer Search, Lists, Alerts, and Compare](docs/canonical/ACARAT_SEARCH_LISTS_ALERTS_COMPARE.md)
- [Agent Terminal and Analytics](docs/canonical/ACARAT_AGENT_TERMINAL_AND_ANALYTICS.md)
- [Mobile App Plan](docs/canonical/ACARAT_MOBILE_APP_PLAN.md)
- [KPI and Measurement Framework](docs/canonical/ACARAT_KPI_AND_MEASUREMENT_FRAMEWORK.md)
- [Saudi Trust and Integrations](docs/canonical/ACARAT_SAUDI_TRUST_AND_INTEGRATIONS.md)
- [Trust, Safety, Privacy, and AI Authority](docs/canonical/ACARAT_TRUST_SAFETY_PRIVACY_AI_AUTHORITY.md)
- [Expansion Products Plan](docs/canonical/ACARAT_EXPANSION_PRODUCTS_PLAN.md)
- [Implementation Roadmap](docs/canonical/ACARAT_IMPLEMENTATION_ROADMAP.md)
- [Source Qualification Ledger](docs/research/ACARAT_SOURCE_QUALIFICATION_LEDGER.md)
- [SpecGrain root program](.specgrain/specs/SG-000001.json)

## Planning governance

The canonical plan is deliberately broader than an MVP and deliberately narrower than implementation authority.

Program-level SpecGrain specifications remain DRAFT until refined into bounded executable Grains. Each implementation Grain must prove scope, sources/rights, security/privacy, negative cases, tests, rollback, and exact-head evidence before acceptance.
