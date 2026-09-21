# Astro Master Planning Brief — Acarat

Use English only for all repository, GitHub, technical, research, planning, specification, task, evidence, review, architecture, code-adjacent and implementation-facing content.

## Mode

MASTER PLAN FIRST / PLAN-ONLY IN THIS PASS.

Do not implement production product code during this pass.

Your job is to turn Acarat into the strongest implementation-ready canonical plan possible, with complete source research, product scope, architecture, data semantics, Saudi regulatory/data boundaries, model/valuation strategy, spatial/3D strategy, Agent Terminal, mobile product, transaction lifecycle, analytics, trust/security/privacy, commercial expansion and a dependency-ordered execution graph.

Do not stop at an MVP-only plan. Plan the whole intended Acarat system, then phase delivery safely.

Do not call the project complete because documentation exists. The plan must be internally consistent, source-backed, rights-aware, traceable and executable through SpecGrain.

## Product authority

The product is Acarat.

Acarat is a Saudi-first real-estate decision, transaction and operating platform.

It is not merely a property portal, Zillow clone, CRM, map, chatbot, AVM, or property-management product.

The target system connects:

DISCOVER
-> VERIFY
-> UNDERSTAND PROPERTY
-> UNDERSTAND AREA
-> UNDERSTAND FAIR PRICE
-> COMPARE
-> SAVE / WATCH / ALERT
-> CONTACT
-> MANAGE CUSTOMER
-> VIEW
-> OFFER / NEGOTIATE
-> DEAL
-> CONTRACT / EXTERNAL AUTHORITY
-> RENEW / MANAGE / RESALE / REINVEST

Primary surfaces include:

- Acarat Marketplace;
- Acarat Intelligence;
- Acarat Spatial;
- Acarat Mobile;
- Agent Terminal;
- Agency / Enterprise;
- Transaction and Trust Rails;
- later Investment / Portfolio;
- later Property Management;
- later Off-Plan / Developer;
- later Financing / Payments / qualified escrow-like provider flows;
- governed Data / Analytics products.

## Live-truth rule

Before changing planning:

1. Reverify the exact current main revision.
2. Reverify every open PR and relevant branch.
3. Reverify Draft PR #1 or its successor and its exact current head.
4. Reverify every current canonical planning document, SpecGrain file and research artifact.
5. Treat live GitHub/repository truth as authoritative over this prompt, chat history or stale hashes.
6. Preserve correct existing work; rewrite or supersede it only when evidence shows a gap, contradiction or weaker design.
7. Do not merge the planning PR unless separately authorized.
8. Never force-push, rebase or rewrite shared history.
9. Never fabricate CI, tests, datasets, partner access, government access, licenses, model performance, valuation accuracy, user validation, security proof or readiness.

## Required reading order

Read first:

1. README.md
2. ASTRO.md
3. docs/research/ACARAT_ASTRO_SOURCE_UNIVERSE.md
4. docs/canonical/ACARAT_MASTER_VISION.md
5. docs/canonical/ACARAT_ARCHITECTURE_PLAN.md
6. docs/canonical/ACARAT_DOMAIN_AND_DATA_MODEL.md
7. docs/canonical/ACARAT_INTELLIGENCE_AND_VALUATION_PLAN.md
8. docs/canonical/ACARAT_SPATIAL_3D_AND_MEDIA_PLAN.md
9. docs/canonical/ACARAT_SEARCH_LISTS_ALERTS_COMPARE.md
10. docs/canonical/ACARAT_AGENT_TERMINAL_AND_ANALYTICS.md
11. docs/canonical/ACARAT_MOBILE_APP_PLAN.md
12. docs/canonical/ACARAT_KPI_AND_MEASUREMENT_FRAMEWORK.md
13. docs/canonical/ACARAT_SAUDI_TRUST_AND_INTEGRATIONS.md
14. docs/canonical/ACARAT_TRUST_SAFETY_PRIVACY_AI_AUTHORITY.md
15. docs/canonical/ACARAT_EXPANSION_PRODUCTS_PLAN.md
16. docs/canonical/ACARAT_IMPLEMENTATION_ROADMAP.md
17. docs/canonical/ACARAT_REQUIREMENTS_TRACEABILITY.md
18. docs/research/ACARAT_SOURCE_QUALIFICATION_LEDGER.md
19. docs/research/ACARAT_COMPETITOR_INTELLIGENCE_2026-09-21.md
20. every .specgrain/specs/SG-*.json
21. current PR discussion/review/changed files.

Then inspect all connected founder repositories and external sources before deciding what is missing.

## Founder GitHub research mandate

The connected GitHub account is a source universe, not merely a code store.

Inspect every public and private repository available through the connected GitHub integration.

For each repository, decide whether it contributes:

- product patterns;
- domain/data modeling;
- maps/geospatial;
- search;
- agent/customer workflow;
- analytics;
- voice;
- mobile;
- 3D/media;
- documents;
- security;
- authority/policy;
- evidence/provenance;
- testing;
- planning/governance;
- agent runtime;
- local-first architecture;
- source qualification.

Do not assume every founder repository is relevant.

Produce a capability map with:
- source;
- exact live revision;
- public/private disclosure class;
- Acarat capability it may help;
- mode: REFERENCE / ADAPT / COPY_SELECTIVE / DEPENDENCY / REJECT;
- reason;
- source/license/provenance concerns;
- security/privacy concerns;
- exact target subsystem;
- proof required.

IMPORTANT PUBLIC-REPOSITORY RULE:

Acarat is public.

Private founder repositories may be inspected, but do not publish their names, private details or copied material into Acarat unless public disclosure/reuse is separately authorized.

Use anonymous private-source identifiers in public planning when necessary.

## External research mandate

The seed source universe is only the beginning.

Actively discover better sources.

Search:

- official Saudi government sources;
- official standards;
- current product documentation;
- GitHub;
- strong engineering documentation;
- recent peer-reviewed or technically rigorous papers for valuation/search/geo/ML;
- current open-source projects;
- current licensing/NOTICE/model/dataset terms.

Prefer first-party/primary sources.

For every new source, answer:

1. What real gap does this source close?
2. Is it more authoritative or maintainable than an existing source?
3. Is direct reuse actually better than a small native implementation?
4. What are its exact rights?
5. What hidden transitive/model/data/asset rights exist?
6. How will Acarat exit this dependency?
7. What evidence would prove adoption is correct?

Maintain a rejection ledger.

Do not keep 5 overlapping frameworks simply because all are good.

## Saudi authority research

Treat official Saudi sources as authoritative for Saudi regulatory/data claims.

At minimum reverify:

- REGA electronic real-estate platform licensing;
- REGA technical integration;
- FAL;
- advertising rules;
- Nafath requirements;
- Real Estate Indicators;
- Ejar digital integration and contract/renewal lifecycle;
- Real Estate Registry and ownership-transfer/public-registration capabilities;
- RER regulations and geospatial data model;
- National Address / SPL APIs;
- REGA Geospatial Real Estate Portal;
- Balady Urban Maps / municipal planning context;
- Wafi / off-plan regulation and project services;
- Saudi Business Center;
- PDPL / SDAIA / NDMO;
- NCA cybersecurity controls;
- SAMA for financing/payment boundaries;
- REDF / Sakani;
- ZATCA Real Estate Transaction Tax;
- GASTAT real-estate price/economic/demographic indicators;
- Saudi Open Data;
- national geospatial authority/standards;
- Ministry of Justice / Najiz where property/deed workflows matter.

Do not infer API access from a public website.

For every government integration classify:

SUPPORTED_NOW
PARTNER_AGREEMENT_REQUIRED
SANDBOX_ONLY
AUTH_REQUIRED
PUBLIC_INFO_ONLY
NO_API_PROVEN
OUT_OF_SCOPE

No government-action claim without integration evidence.

## Competitor research

Build a dated, source-backed feature/capability matrix.

Saudi mandatory review:

- Aqar;
- Wasalt;
- Bayut Saudi;
- Property Finder Saudi;
- Suhail;
- Deal App;
- Sakani;
- current REGA-licensed real-estate platform register.

Global mandatory review:

- Zillow;
- Redfin;
- Realtor.com;
- Homes.com;
- Zoopla;
- Rightmove;
- OnTheMarket;
- realestate.com.au / REA;
- Domain;
- leading regional portals.

Specialized benchmark research:

- CoStar;
- LoopNet;
- Crexi;
- CoreLogic / Cotality;
- ATTOM;
- HouseCanary;
- PriceHubble;
- PropStream;
- Realyse;
- AppFolio;
- Buildium;
- DoorLoop;
- Yardi;
- Follow Up Boss;
- kvCORE;
- Lofty;
- BoomTown;
- Propertybase;
- Rechat;
- Matterport;
- CubiCasa;
- Polycam;
- Scaniverse;
- iGUIDE;
- financing/home-loan leaders;
- off-plan/developer platforms.

A competitor feature is not automatically an Acarat requirement.

For each capability classify:

BASELINE
DIFFERENTIATOR
REJECT
LATER
REGULATED
EVIDENCE_GAP

## Product requirements Astro must challenge

Do not blindly preserve current implementation choices.

Challenge every major architecture/product choice and improve it when evidence supports a better direction.

However, preserve these product outcomes unless evidence exposes a contradiction:

### Customer marketplace

- Saudi-first;
- Arabic/English;
- RTL/LTR;
- property discovery;
- map/list parity;
- Property Passport;
- verified agent/listing authority;
- rich neighborhood/POI context;
- satellite/aerial context;
- 360/3D when justified;
- property/land history;
- lists;
- collaborative shortlists;
- saved searches;
- custom alerts;
- compare;
- viewing;
- offer/deal/contract status.

### Conversational search

Natural language and voice must compile into typed, inspectable search constraints.

Examples:

- apartment under SAR 40k;
- land under a price-per-m2 threshold;
- 15 minutes from a destination;
- parking required;
- school/hospital nearby;
- multiple destinations;
- user-drawn polygon.

Hard constraints must never be silently relaxed.

### Acarat Intelligence

Plan separate evidence-backed engines for:

- Fair Rent;
- Fair Sale;
- Fair Land;
- comparable selection;
- market range;
- price/m2;
- listing ask premium/discount;
- neighborhood trend;
- demand/supply;
- listing diagnostics;
- customer/listing match;
- renewal/lifecycle intelligence;
- data quality/anomaly intelligence.

Valuations must expose interval, confidence, evidence density, comparable set, data freshness and abstention.

An LLM never owns the numeric valuation.

### Valuation scientific plan

Astro must design a rigorous AVM program.

At minimum challenge:

- robust baseline;
- weighted comparable model;
- hedonic models;
- CatBoost;
- LightGBM;
- XGBoost;
- quantile forests;
- conformal/prediction intervals;
- spatial statistics/econometrics;
- H3/hierarchical spatial effects;
- temporal adjustment;
- ensemble strategy;
- low-evidence abstention.

Required evaluation:

- temporal holdout;
- geographic holdout;
- property-identity grouping;
- leakage prevention;
- duplicate prevention;
- city/type/price-band segments;
- MAE;
- median AE;
- percent within 5/10/20%;
- quantile loss;
- empirical interval coverage;
- interval width;
- calibration;
- drift;
- out-of-distribution behavior.

A complex model is rejected if it does not materially outperform a simpler explainable baseline.

### Land

Land is not apartment-with-fewer-fields.

Plan:

- plot geometry;
- area;
- price/m2;
- comparable land transactions;
- frontage;
- road width;
- corner;
- street fronts;
- orientation;
- land use;
- verified planning/building constraints;
- urban context;
- services/utilities where available;
- transaction density;
- liquidity;
- trend;
- satellite/aerial context;
- confidence.

Never infer municipal approval.

### Agent Terminal

Plan a serious daily operating system.

It must cover:

- previous customers;
- current customers;
- future opportunities;
- Customer 360;
- requirements;
- leads;
- assignment;
- pipeline;
- tasks;
- conversations;
- viewings;
- offers;
- deal room;
- documents;
- contracts;
- contract-end dates;
- renewal windows;
- inventory;
- market intelligence;
- smart matching;
- listing diagnostics;
- AI daily brief;
- team/agency operation.

### Listing analytics

At minimum:

- search impressions;
- map impressions;
- detail views;
- unique viewers;
- repeat viewers;
- engaged time;
- photo/gallery;
- video;
- floor plan;
- 360;
- 3D;
- satellite/map interactions;
- saves;
- shares;
- compare;
- contact click;
- WhatsApp handoff;
- inquiry;
- viewing;
- offer;
- deal;
- contract;
- response time;
- funnel conversion;
- price position;
- market percentile;
- listing age;
- completeness.

Define metric semantics. Do not create decorative dashboards.

### Notifications

Canonical in-app notification first.

External channels are delivery adapters.

Plan:

- saved-search alerts;
- price drop;
- threshold;
- value-range change;
- new matching land;
- commute match;
- listing status;
- verification;
- agent response;
- viewing;
- offer;
- deal;
- contract;
- renewal.

Support dedupe, digests, quiet hours and consent.

### Spatial and 3D

Research and choose:

- PostGIS;
- MapLibre;
- H3;
- deck.gl;
- Kepler patterns;
- Cesium;
- GeoLibre;
- routing/geocoding options;
- satellite/aerial providers;
- vector-tile stack;
- 3D terrain/buildings;
- panoramas;
- floor plans;
- photogrammetry;
- Gaussian splats;
- digital twins.

Direct 3D/model/data adoption requires separate rights review.

Do not use a non-commercial implementation in a commercial product without explicit rights.

### Mobile

Plan one role-aware iOS/Android Acarat application unless evidence proves separate apps are better.

Customer mobile:

- search;
- map;
- voice;
- alerts;
- lists;
- compare;
- property;
- 3D;
- saved places;
- messages;
- viewings;
- offers/deals/contracts.

Agent mobile:

- Today;
- lead inbox;
- Customer 360;
- tasks;
- viewings;
- listings;
- analytics;
- matches;
- offers/deals;
- renewals;
- camera/media capture.

Plan deep links, push, secure storage, biometrics, offline-safe state, resumable upload, Arabic/RTL and accessibility.

### Saudi transaction rails

Plan strict adapter boundaries for:

- REGA;
- Nafath;
- Ejar;
- RER;
- National Address;
- Balady;
- future financing/payment authorities/providers.

External action state must include UNKNOWN_OUTCOME.

Do not replay consequential external requests blindly.

### Trust/reviews

Plan:

- identity;
- agent authority;
- agency authority;
- listing/ad authority;
- source provenance;
- fact freshness;
- verified interaction;
- verified viewing;
- verified deal;
- review eligibility;
- moderation;
- disputes/appeals;
- fake listing/agent detection;
- duplicate media/listing detection.

Do not invent one opaque agent score.

### AI authority

AI may:

- interpret;
- retrieve;
- rank;
- explain;
- summarize;
- draft;
- propose.

AI must not silently:

- publish;
- change asking price;
- send external communication without policy;
- change customer consent;
- accept/reject an offer;
- submit a government contract;
- transfer ownership;
- release payment;
- manufacture verification;
- override an abstention.

Models propose. Deterministic authority decides.

## Expansion products

Preserve and fully plan later product families:

- investment analytics;
- portfolio analytics;
- property management;
- tenant/landlord/maintenance operations;
- off-plan/developer marketplace;
- project/masterplan/unit inventory;
- financing/mortgage marketplace;
- transparent affordability scenarios;
- qualified deposit/payment/escrow-like provider flows;
- enterprise dashboards;
- governed market/valuation/data APIs.

Do not allow later scope to corrupt the first dependency chain.

## Architecture research

Challenge the current candidate architecture.

Current candidate direction is:

- Go primary backend;
- Next.js/React/TypeScript web;
- React Native/Expo mobile;
- PostgreSQL/PostGIS canonical truth;
- object storage;
- bounded Python ML/vision/3D workers;
- transactional outbox;
- optional ClickHouse/OpenSearch/vector/graph infrastructure only after measured need.

You may change this only with explicit evidence and an ADR-worthy rationale.

Strong default:

- modular monolith before microservices;
- relational/geospatial canonical truth;
- rebuildable projections;
- few dependencies;
- provider adapters around external authority;
- no hidden cloud correctness dependency;
- no Kafka/Kubernetes/graph/vector database by fashion.

## Data model completeness

Produce or reconcile canonical semantics for at least:

- Subject;
- Customer;
- Agent;
- Agency;
- Membership;
- AuthorityEvidence;
- Property;
- Parcel;
- Structure;
- Unit;
- PropertyFact;
- Location;
- GeometryObservation;
- Listing;
- ListingRevision;
- AskingPriceObservation;
- MarketObservation;
- MarketSnapshot;
- ComparableSet;
- ModelBundle;
- ValuationResult;
- Neighborhood;
- POI;
- SavedPlace;
- RouteReceipt;
- SearchIntent;
- SearchExecution;
- SavedSearch;
- PropertyList;
- WatchRule;
- Notification;
- DeliveryAttempt;
- Lead;
- CustomerRequirement;
- Task;
- Conversation;
- Viewing;
- Offer;
- Deal;
- ContractRecord;
- RenewalCase;
- ReviewEligibility;
- Review;
- MediaAsset;
- MediaDerivative;
- AnalyticsEvent;
- Plan/Entitlement;
- future Developer/Project/Inventory;
- future Property Management;
- future Financing;
- future Payment/Deposit.

Identity and history semantics must survive relisting, agent changes, property dedupe, renewal and resale.

## Analytics and KPI plan

Do not measure everything as a top-level KPI.

Design:

- 1-3 core outcome KPIs;
- driver metrics;
- guardrails;
- diagnostic drill-downs;
- semantic metric registry;
- ownership;
- exact formula;
- event source;
- unique/total semantics;
- late-event handling;
- bot/internal exclusion;
- timezone;
- privacy thresholds.

No arbitrary numeric business targets without Acarat baseline evidence.

Plan PostgreSQL launch analytics first and ClickHouse only when measured scale justifies it.

## Privacy/security

Build a full threat and privacy model.

At minimum:

- PDPL;
- sensitive government identifiers;
- saved home/work/school locations;
- CRM notes;
- conversations;
- documents;
- contracts;
- offers;
- payment refs;
- media;
- national ID;
- cross-agency isolation;
- IDOR;
- account takeover;
- malicious upload;
- scraping;
- spam;
- review manipulation;
- prompt injection;
- tool abuse;
- data exfiltration;
- webhook spoof/replay;
- duplicate external transactions;
- insider misuse.

Data minimization is part of architecture, not a policy-page afterthought.

## Source admission

For every proposed dependency/donor record:

source_repository
source_revision
source_path_or_release
source_license
NOTICE
data_model_asset_rights
public_private_class
target_subsystem
capability
mode
native_alternative
security_review
privacy_review
transitive_dependencies
behavior_tests
update_strategy
rollback_strategy
exit_strategy
admission_status

Do not copy wholesale platforms merely because permission exists.

## SpecGrain planning method

Use TheHalfMoon/SpecGrain as the canonical decomposition model.

Program-level planning is not execution authority.

Lifecycle concept:

DRAFT -> SHAPED -> REFINING -> GRAIN

A leaf may become GRAIN only when independently understandable and verifiable.

Every executable Grain must define:

- exact outcome;
- rationale;
- scope_in;
- scope_out;
- dependencies;
- acceptance;
- risk level;
- recovery;
- context budget;
- intended change surface;
- evidence requirements;
- source/provenance requirements;
- security/privacy requirements;
- Arabic/RTL/accessibility requirements when applicable;
- minimality rationale;
- unresolved decisions;
- readiness state.

If a task is too large, refine it further.

Do not solve an oversized task by increasing agent context.

Use rolling-wave planning:

LATER:
- phase / major slice resolution.

NEXT:
- shaped dependencies, contracts, risks and acceptance.

NOW:
- the first dependency-eligible bounded Grain only.

The final plan must make the true first implementation frontier unambiguous.

## Diffcipline planning/review method

For planning itself and every future Grain use:

THINK
-> CHALLENGE
-> MINIMIZE
-> CHANGE
-> PROVE

For each major architecture decision:

THINK:
- What problem are we solving?
- What facts and constraints control it?

CHALLENGE:
- Is this capability actually required?
- Is there a simpler design?
- What assumption may be wrong?
- What failure/security/privacy/licensing mode are we ignoring?
- What evidence would falsify this choice?

MINIMIZE:
- What is the smallest durable boundary?
- Which dependencies/platforms can be removed?
- What can remain a later adapter/projection?
- Can PostgreSQL/PostGIS solve this before a new service?

CHANGE:
- Update the canonical plan consistently.
- Supersede contradictory documents explicitly.
- Maintain traceability.

PROVE:
- source citations;
- exact repository/source pins;
- cross-document consistency;
- requirement coverage;
- dependency graph;
- negative-case coverage;
- planning completeness audit;
- independent review.

A planning assertion is not proof because Astro wrote it.

## Required canonical artifacts

You may reorganize filenames when justified, but final canonical planning must cover all of these:

### Product

- Whole-product master vision;
- user/persona/jobs model;
- product capability map;
- customer journey;
- agent journey;
- agency journey;
- developer/off-plan journey;
- property-manager journey;
- product non-goals.

### Research

- Source Master Index;
- founder repository capability map;
- Saudi authority/data source matrix;
- competitor master index;
- competitor capability matrix;
- OSS donor/candidate matrix;
- source rejection ledger;
- source rights/NOTICE/model/data/asset matrix;
- research gap ledger.

### Architecture

- target architecture;
- runtime/deployment profiles;
- domain boundaries;
- canonical data model;
- API/event contracts strategy;
- async/outbox strategy;
- source/provenance model;
- external adapter model;
- projection/index model;
- mobile architecture;
- observability;
- backup/restore;
- scaling/extraction triggers.

### Marketplace/search

- Property Passport;
- search;
- Arabic NLP;
- voice;
- map;
- lists;
- collaboration;
- alerts;
- notification center;
- compare;
- property history;
- Ask Acarat.

### Intelligence

- market evidence ingestion;
- data quality;
- comparable engine;
- rent AVM;
- sale AVM;
- land AVM;
- uncertainty/calibration;
- model governance;
- model/data source rights;
- neighborhood intelligence;
- listing diagnostics;
- customer matching;
- scenarios;
- drift monitoring.

### Spatial/media

- Saudi address/POI;
- map stack;
- satellite/aerial provider strategy;
- routing/commute;
- H3/spatial analytics;
- vector tiles;
- terrain/buildings;
- panorama/floor plan;
- 3D/digital twin;
- media provenance;
- privacy/redaction;
- AI media policy;
- performance/fallback.

### Agent Terminal

- CRM;
- Customer 360;
- lifecycle;
- leads;
- routing;
- SLA;
- tasks;
- conversations;
- viewings;
- offers;
- deal room;
- contracts;
- renewals;
- listing inventory;
- listing analytics;
- agent analytics;
- agency/team analytics;
- AI daily brief;
- authority boundaries.

### Saudi trust/transactions

- REGA licensing;
- Nafath;
- FAL;
- ad authority;
- Ejar;
- RER;
- National Address;
- Balady;
- Wafi/off-plan;
- external reconciliation;
- UNKNOWN_OUTCOME;
- partner-access gates.

### Security/privacy/trust

- threat model;
- data classification;
- privacy lifecycle;
- tenant isolation;
- identity/authorization;
- AI authority;
- prompt-injection boundary;
- review integrity;
- fake listing/agent abuse;
- media/document security;
- supply chain;
- incident response.

### Analytics

- event taxonomy;
- semantic metric registry;
- KPI framework;
- listing funnel;
- customer funnel;
- agent operations;
- trust guardrails;
- valuation evaluation;
- data quality;
- geospatial analytics;
- warehouse scale gate.

### Commercial/expansion

- launch economics;
- subscription/entitlements;
- agent plans;
- organic ranking separation;
- investment;
- property management;
- off-plan;
- financing;
- payment/deposit provider rails;
- enterprise;
- governed data products.

### Delivery

- architecture decisions;
- dependency-ordered roadmap;
- SpecGrain root program;
- phase/slice/task registry;
- first executable frontier;
- test/evidence plan;
- benchmark plan;
- migration strategy;
- release qualification;
- requirement traceability;
- implementation handoff.

## Planning completeness audit

Before claiming completion, perform a hostile gap audit.

Ask:

- What customer journey ends in a dead end?
- What Agent Terminal journey requires a spreadsheet or external CRM?
- What property fact has no authority/provenance owner?
- What government step is assumed rather than proven?
- What metric is undefined?
- What model can leak future data?
- What land feature is unsupported?
- What map provider right is ambiguous?
- What 3D asset/model license is unsafe?
- What mobile flow loses state offline?
- What notification can duplicate?
- What external command can repeat after timeout?
- What tenant boundary can leak?
- What private founder source could be disclosed?
- What later expansion forces a data-model rewrite?
- What source has no exit strategy?
- What requirement has no roadmap owner?
- What roadmap phase has no acceptance/evidence path?
- What task is too large to be a Grain?
- What claim cannot be proven today?

Close the gap or record it explicitly as an external/unresolved gate.

## Completion state

Do not set:

ASTRO_PLAN_COMPLETE=YES

until all of the following are true:

- whole-product capability map is complete;
- current founder requirements are traced;
- public/private source universe is reconciled;
- Saudi authority/data boundaries are explicit;
- competitor and OSS research is current;
- admitted sources have exact adoption posture;
- architecture has no unresolved contradiction;
- domain/data model covers current + expansion needs without obvious parallel truth stores;
- valuation program is scientifically/evidentially credible;
- search/alerts/Agent Terminal/mobile/spatial/3D/transaction plans are complete;
- security/privacy/AI authority are complete;
- KPI/analytics semantics are complete;
- roadmap is dependency ordered;
- SpecGrain program is coherent;
- first implementation Grain frontier is unambiguous;
- all external gates are explicit;
- hostile planning audit finds no unowned material gap;
- final implementation handoff can be used without rediscovering product intent.

If those conditions are satisfied, write:

ASTRO_PLAN_COMPLETE=YES
IMPLEMENTATION_STARTED=NO
NEXT_FRONTIER=<exact first dependency-ready planning/execution frontier>

## Git/GitHub behavior

Work on the active planning branch or a successor planning branch based on live truth.

Keep planning reviewable.

Update Draft PR #1 or its live successor.

Do not merge without separate authority.

Use English for commits, PR bodies, specifications, source ledgers and evidence.

At the end report:

- exact branch;
- exact head SHA;
- PR number/state;
- files added/updated;
- source count by class;
- founder repositories reviewed;
- competitors reviewed;
- Saudi authorities reviewed;
- unresolved external gates;
- SpecGrain program/phase/slice/task counts;
- first executable frontier;
- planning audit result;
- ASTRO_PLAN_COMPLETE state.
