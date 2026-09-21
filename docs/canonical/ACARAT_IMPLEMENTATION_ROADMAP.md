# Acarat Canonical Implementation Roadmap

**Status:** PLANNING_CANDIDATE  
**Method:** SpecGrain decomposition + Diffcipline execution  
**Rule:** no phase is complete from prose or UI alone. Every phase must close its exact acceptance/evidence gates.

## 1. Program structure

The roadmap is organized as dependency-ordered phases. Each phase is later decomposed into bounded executable SpecGrains.

~~~text
P00 Governance and source rights
P01 Repository and engineering foundation
P02 Identity, tenancy, privacy, regulatory trust
P03 Property, land, unit, and listing truth
P04 Saudi geo/address and map foundation
P05 Marketplace discovery and property passport
P06 Lists, saved searches, alerts, notifications
P07 Agent Terminal CRM and task foundation
P08 Viewings, offers, deal room
P09 Rental contract/Ejar adapter
P10 Analytics event model and Agent dashboards
P11 Market evidence ingestion and comparable engine
P12 Fair Rent / Fair Sale baseline
P13 Fair Land intelligence
P14 Conversational and voice search
P15 Advanced geospatial analytics and commute
P16 360/3D/digital-twin pipeline
P17 Reviews, reputation, and trust graph
P18 Intelligence expansion and scenario tools
P19 Agency/team operations and subscription
P20 Production hardening and launch qualification
P21 Post-launch scale gates
P22 Investment and portfolio intelligence
P23 Property management operating system
P24 Off-plan and developer marketplace
P25 Financing, deposits, and regulated payment rails
P26 Enterprise dashboards and governed data products
~~~

## 2. P00 — Governance and source rights

Outcome:

Acarat has explicit planning authority, source adoption rules, Saudi authority boundaries, risk register, data classification, and no hidden donor assumptions.

Required outputs:

- master vision;
- architecture plan;
- source qualification ledger;
- Saudi authority/integration matrix;
- privacy/data classification;
- AI authority model;
- risk register;
- licensing strategy decision;
- security baseline;
- SpecGrain root and child graph;
- evidence directory conventions.

Exit gate:

- every currently proposed external dependency is dependency/reference/candidate/rejected, never implicitly admitted;
- government capabilities distinguish public evidence from actual production integration authority;
- private donor details are not disclosed into the public repo without authority.

## 3. P01 — Repository and engineering foundation

Outcome:

Runnable monorepo foundation with no product overreach.

Scope:

- Go API;
- Go worker;
- Next.js web;
- versioned contracts;
- PostgreSQL/PostGIS local stack;
- migrations;
- CI;
- lint/typecheck/test;
- SBOM/dependency audit;
- OpenTelemetry foundation;
- structured errors;
- configuration/secrets boundary;
- Arabic/English design-system primitives.

Exit gate:

- clean bootstrap;
- one health/readiness path;
- database migrations reversible;
- exact-head CI;
- no production secret;
- dependency licenses recorded.

## 4. P02 — Identity, tenancy, privacy, regulatory trust

Outcome:

Acarat can represent users, agents, agencies, memberships, authority evidence, and sensitive identifiers without unsafe shortcuts.

Scope:

- customer identity;
- agent identity;
- agency;
- roles;
- sessions;
- consent/preferences;
- audit;
- regulatory verification record;
- Nafath adapter contract;
- FAL/ad-license evidence model;
- PDPL minimization/retention rules.

Exit gate:

- unauthorized cross-tenant access fails;
- national ID is never a public profile identifier;
- expiry/revocation semantics work;
- missing external authority fails closed where required.

## 5. P03 — Property, land, unit, and listing truth

Outcome:

Durable property/listing model that can survive relisting, price change, agent change, and transaction history.

Scope:

- property;
- parcel/land;
- building;
- unit;
- address reference;
- listing;
- listing revision;
- asking price;
- availability;
- property facts;
- provenance;
- media references;
- listing lifecycle;
- duplicate candidate detection.

Exit gate:

- property identity is separate from listing identity;
- historical listing versions preserved;
- no destructive overwrite of source-backed facts;
- land receives dedicated fields rather than apartment defaults.

## 6. P04 — Saudi geo/address and map foundation

Outcome:

Searchable map/list product with reliable geospatial truth.

Scope:

- PostGIS;
- MapLibre;
- map/list parity;
- National Address adapter contract;
- district/neighborhood geometry;
- POIs;
- coordinate precision;
- satellite/aerial provider contract;
- tile attribution/rights;
- map state serialization.

Exit gate:

- list contains every eligible map result;
- low-accuracy coordinate cannot render as precise footprint;
- provider outage has defined fallback;
- map is not required for accessibility/SEO.

## 7. P05 — Marketplace discovery and Property Passport

Outcome:

Customers can browse, filter, inspect, and understand a verified property record.

Scope:

- SEO listing/property pages;
- search filters;
- neighborhood pages;
- agent page;
- Property Passport;
- provenance labels;
- freshness;
- local context;
- contact actions;
- verified/public agent information.

Exit gate:

- no LLM-generated factual field without evidence;
- property pages disclose missing facts;
- Arabic/English parity;
- mobile/accessibility qualification.

## 8. P06 — Lists, saved searches, alerts, notifications

Outcome:

A customer can persist intent and receive reliable new-listing/price/status alerts.

Scope:

- favorites;
- custom lists;
- saved searches;
- watch rules;
- notification center;
- dedupe;
- quiet hours;
- in-app delivery;
- optional external channels behind adapter/policy.

Exit gate:

- structured saved intent;
- deterministic matcher;
- event replay does not duplicate notifications;
- external delivery failure does not lose canonical notification.

## 9. P07 — Agent Terminal CRM and tasks

Outcome:

Agent has a usable daily operating system.

Scope:

- customer 360;
- previous/current/future lifecycle;
- leads;
- assignments;
- pipeline;
- tasks;
- requirements;
- notes;
- conversations;
- activity timeline;
- inventory.

Exit gate:

- duplicate lead/customer reconciliation;
- auditable assignment;
- explicit task completion evidence;
- customer requirements versioned.

## 10. P08 — Viewings, offers, and deal room

Outcome:

Acarat manages the journey from interest to transaction-ready state.

Scope:

- viewing lifecycle;
- attendance/outcome;
- offer revisions;
- negotiation;
- deal room;
- checklist;
- documents;
- party state;
- external submission readiness.

Exit gate:

- concurrent offer revisions safe;
- unknown outcomes explicit;
- no silent contract closure;
- full audit history.

## 11. P09 — Rental contract and Ejar adapter

Outcome:

Where formal integration authority exists, Acarat can prepare and hand off/submit rental contract data and reconcile external outcome.

Scope:

- capability detection;
- Ejar adapter;
- request validation;
- idempotency;
- submission receipt;
- status polling/webhook;
- party-action state;
- final reconciliation;
- contract reference;
- renewal schedule.

Exit gate:

- sandbox/approved environment evidence;
- unknown/rejected states preserved;
- no production capability claim without production agreement/credentials;
- retry cannot duplicate external contract.

## 12. P10 — Analytics event model and Agent dashboards

Outcome:

Every important marketplace and agent funnel can be measured correctly.

Scope:

- event schema;
- listing impressions;
- detail views;
- unique users;
- media engagement;
- saves;
- shares;
- compare;
- contacts;
- WhatsApp handoff;
- inquiries;
- viewings;
- offers;
- deals/contracts;
- response times;
- dashboard APIs;
- metric definitions.

Exit gate:

- bot/internal filtering defined;
- unique semantics defined;
- metric recomputation deterministic;
- privacy thresholds for aggregate demand;
- page UI cannot spoof analytics events.

## 13. P11 — Market evidence ingestion and comparable engine

Outcome:

Acarat can form auditable local price evidence sets before ML.

Scope:

- MarketObservation;
- official/provider adapters;
- source snapshots;
- quality rules;
- anomaly flags;
- outlier policy;
- time normalization;
- PostGIS comparable retrieval;
- H3 preaggregation;
- comparable-set receipts.

Exit gate:

- listing ask and completed transaction are distinguishable;
- source rights proven;
- exact valuation evidence snapshot reproducible;
- sparse evidence behavior defined.

## 14. P12 — Fair Rent and Fair Sale baseline

Outcome:

Customers/agents see transparent fair ranges and market position.

Scope:

- weighted median/robust baseline;
- percentiles;
- price/m2;
- temporal adjustment;
- interval;
- confidence;
- market-position card;
- comparable explorer;
- evaluation corpus.

Exit gate:

- time/geographic holdout;
- segment metrics;
- calibration;
- low-evidence abstention;
- no LLM numeric authority.

ML model admission occurs only after baseline evidence exists.

## 15. P13 — Fair Land intelligence

Outcome:

Land buyers/agents get dedicated price and constraint intelligence.

Scope:

- land comparable engine;
- plot geometry;
- price/m2;
- frontage/road/corner/street-front features where sourced;
- urban/land-use context;
- building-regulation evidence where official;
- satellite context;
- liquidity/trend;
- land confidence model.

Exit gate:

- no inferred buildability is presented as official permission;
- land benchmark independent from apartment/villa model;
- source freshness visible.

## 16. P14 — Conversational and voice search

Outcome:

Natural-language/voice intent compiles to safe deterministic search.

Scope:

- SearchIntent parser;
- Arabic dialect corpus;
- English/code-switch;
- numeric/budget/time parsing;
- conversational refinement;
- constraint preview;
- relaxation proposals;
- voice VAD/ASR;
- correction flow.

Exit gate:

- hard constraints never silently dropped;
- Arabic/code-switch benchmark;
- transcript correction;
- search result explanation fidelity;
- no sensitive-characteristic steering.

## 17. P15 — Advanced geospatial intelligence

Outcome:

Acarat supports commute and large-scale market map analysis.

Scope:

- saved places;
- routing adapter;
- isochrones;
- multi-destination fit;
- H3 layers;
- deck.gl analytical rendering;
- price/demand/supply heatmaps;
- temporal playback.

Exit gate:

- provider rights/attribution;
- map/list accessibility fallback;
- performance on representative dense city dataset;
- private saved places protected.

## 18. P16 — 360/3D/digital twin

Outcome:

Listings can optionally provide high-quality spatial inspection.

Scope:

- panorama tour;
- floor-plan links;
- media privacy;
- photogrammetry benchmark;
- permissive Gaussian-splat candidate;
- web viewer;
- progressive loading;
- digital-twin receipt.

Exit gate:

- commercial-compatible source path;
- model/dependency rights;
- privacy review;
- fidelity/quality benchmark;
- no deceptive AI image alteration;
- mobile performance.

## 19. P17 — Reviews, reputation, and trust graph

Outcome:

Reviews are linked to real interactions/deals and authority evidence is inspectable.

Scope:

- review eligibility;
- verified interaction;
- verified deal;
- moderation;
- dispute;
- agent/agency public stats;
- property/listing history graph;
- trust projection.

Exit gate:

- arbitrary unauthenticated review blocked;
- agent cannot generate own verified review;
- dispute/appeal flow;
- rating aggregation resists small-sample disclosure/manipulation.

## 20. P18 — Intelligence expansion

Outcome:

Acarat adds proven model-based value beyond the robust baseline.

Candidates:

- quantile forest;
- CatBoost/LightGBM;
- spatial residual model;
- calibrated ensemble;
- customer matching;
- listing diagnostics;
- scenario simulation;
- renewal prioritization.

Exit gate per model:

- model card;
- exact training snapshot;
- artifact digest;
- calibration;
- segment metrics;
- drift thresholds;
- baseline comparison;
- rollback;
- no protected/sensitive feature leakage.

## 21. P19 — Agency/team operations and subscription

Outcome:

Multi-agent offices can operate safely and future commercial plans are enforceable.

Scope:

- branch/team;
- lead routing;
- role-scoped dashboards;
- team workload;
- agency analytics;
- entitlements;
- active-listing quotas;
- fair-use;
- billing adapter.

Exit gate:

- subscription cannot affect organic ranking;
- quota enforcement tested;
- billing failure does not corrupt listing truth;
- team privacy boundaries.

## 22. P20 — Production hardening

Outcome:

Acarat is deployable as a reliable Saudi production system.

Required proof:

- security review;
- threat model;
- penetration findings disposition;
- backup/restore;
- disaster recovery;
- migrations;
- performance/load;
- accessibility;
- Arabic/RTL;
- SEO;
- observability;
- privacy export/delete;
- incident runbooks;
- third-party SLA/fallback;
- Saudi regulatory checklist;
- exact source/NOTICE/SBOM;
- release evidence.

## 23. P21 — Post-launch scale gates

Candidates only when metrics justify:

- ClickHouse;
- OpenSearch;
- dedicated vector retrieval;
- dedicated graph store;
- separate media/ML service;
- Kafka/event streaming;
- Kubernetes;
- multi-region;
- mobile native apps.

Each requires a measured trigger and ADR.

## 24. Cross-phase mandatory gates

Every executable task must define:

- scope;
- exclusions;
- dependency authority;
- source/provenance;
- security/privacy;
- Arabic/RTL if user-facing;
- accessibility;
- tests;
- negative tests;
- observability;
- migration/rollback if stateful;
- acceptance evidence.

## 25. Program success metrics

The product should eventually track:

### Marketplace quality

- verified listing coverage;
- stale listing rate;
- duplicate rate;
- search success;
- saved-search activation;
- alert-to-detail engagement;
- customer time-to-qualified-shortlist.

### Decision quality

- valuation coverage;
- interval calibration;
- comparable evidence density;
- user engagement with market-position/comparable tools;
- compare-to-contact progression.

### Agent value

- lead response time;
- qualified-lead rate;
- viewing conversion;
- offer conversion;
- close conversion;
- renewal completion;
- repeat customers;
- task SLA;
- listing performance improvement after evidence-backed action.

### Trust

- successful authority verification;
- external reconciliation errors;
- review eligibility integrity;
- dispute rate;
- privacy/security incidents.

Do not optimize raw engagement at the expense of decision quality or trust.


## 26. P22 — Investment and portfolio intelligence

Outcome:

Acarat extends existing market evidence into transparent property and portfolio decision analytics.

Scope:

- gross/net yield scenarios;
- cash-flow assumptions;
- vacancy/maintenance scenarios;
- acquisition basis;
- current Acarat range;
- portfolio concentration;
- contract/renewal exposure;
- market trend and liquidity.

Exit gate:

- all assumptions explicit;
- no guaranteed-return claim;
- no hidden financial-advice framing;
- scenario calculations reproducible.

## 27. P23 — Property management operating system

Outcome:

Landlords/property managers can manage units, tenants, leases, maintenance, renewals, tasks, and owner reporting over the same property/customer/contract identities.

Exit gate:

- no duplicate property/customer truth;
- tenant privacy and role boundaries;
- maintenance/task lifecycle;
- payment/contract status only from qualified sources;
- owner statements reproducible.

## 28. P24 — Off-plan and developer marketplace

Outcome:

Verified developers/projects can publish structured projects, unit inventory, payment schedules, progress, and authorized reservation flows.

Exit gate:

- project/developer authority evidence;
- inventory concurrency safety;
- reservation state machine;
- progress provenance;
- no unverified completion/permit claims.

## 29. P25 — Financing, deposits, and regulated payment rails

Outcome:

Acarat can compare financing scenarios and connect to qualified financing/payment/escrow providers without silently becoming a bank, lender, or custodian.

Exit gate:

- provider/regulatory authority proven;
- rate/fee freshness;
- no invented credit decision;
- funds are not held by Acarat unless separately authorized;
- reconciliation and dispute/refund semantics proven.

## 30. P26 — Enterprise dashboards and governed data products

Outcome:

Agencies, developers, operators, and approved partners can use role-scoped executive/operations/sales/marketing/compliance/finance analytics and rights-cleared data APIs.

Exit gate:

- semantic metric registry;
- source redistribution rights;
- aggregation/privacy thresholds;
- API versioning;
- tenant isolation;
- export/audit controls;
- no raw government/provider redistribution without rights.
