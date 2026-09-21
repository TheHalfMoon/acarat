# Acarat Canonical Master Vision

**Status:** PLANNING_AUTHORITY_CANDIDATE  
**Scope:** Saudi-first real-estate marketplace, decision intelligence, agent operating system, and transaction rails  
**Repository:** TheHalfMoon/acarat  
**Planning branch:** codex/acarat-canonical-plan

## 1. Product thesis

Acarat is not a listing portal with AI attached. It is a real-estate decision and transaction system that keeps discovery, evidence, spatial context, valuation, customer/agent workflow, contracts, government rails, and post-transaction lifecycle in one coherent product model.

The product must help a customer answer:

- Is this property real and currently available?
- Is the advertiser authorized?
- Is the asking price reasonable?
- What is a defensible market range?
- What does the area actually offer?
- How does this property compare with alternatives?
- How long is the trip to places I care about?
- What is the historical and current market context?
- What are the risks, missing facts, and uncertainty?
- What should I do next to contact, visit, offer, contract, or monitor?

The product must help an agent answer:

- Who are my active, previous, and future customers?
- What does each customer want and how has that intent changed?
- Which listings best match each customer?
- Which customers need action now?
- Which contracts expire soon?
- Which listings underperform and why?
- Which leads came from which surfaces?
- How fast do I respond?
- What is my inquiry-to-viewing, viewing-to-offer, and offer-to-close conversion?
- Which customers are likely to renew, move, buy, sell, or need follow-up?
- What is the market doing around each listing?
- What work can Acarat safely automate?

## 2. Product surfaces

### 2.1 Marketplace

The customer-facing marketplace includes:

- verified property listings;
- property and unit passports;
- Saudi address and location context;
- map/list synchronized discovery;
- natural-language and voice search;
- saved searches;
- custom property lists;
- collaborative shortlists;
- notification center;
- comparison;
- viewing requests;
- agent contact;
- offer/application state;
- transaction/deal room;
- contract and renewal history where authorized;
- verified interaction/deal reviews.

### 2.2 Acarat Intelligence

Acarat Intelligence is a set of evidence-bound decision engines, not one LLM.

It includes:

- Fair Rent;
- Fair Sale Value;
- Fair Land Value;
- price-per-square-meter analysis;
- comparable-selection engine;
- market range and percentile position;
- listing premium/discount analysis;
- neighborhood trend analysis;
- demand and inventory signals;
- listing-performance diagnostics;
- match and ranking explanations;
- renewal and lifecycle forecasting;
- anomaly and duplicate detection;
- market and property Q&A grounded in evidence.

### 2.3 Acarat Spatial

Acarat Spatial includes:

- 2D map;
- 3D terrain;
- 3D buildings;
- satellite/aerial imagery adapters;
- hybrid map;
- property footprints;
- parcel/plot context where rights permit;
- neighborhood polygons;
- POIs;
- commute-time surfaces;
- route-aware search;
- heatmaps;
- H3 market cells;
- demand/supply layers;
- price layers;
- time playback for market movement;
- property digital twins and virtual tours when source media supports them.

### 2.4 Agent Terminal

The Agent Terminal is an operating system for an individual licensed agent or agency team.

It includes:

- customer 360;
- lead inbox;
- pipeline;
- tasks;
- conversations;
- notes;
- saved customer requirements;
- smart matching;
- calendar/viewings;
- offers;
- deal room;
- contract lifecycle;
- renewal queue;
- previous customers;
- current customers;
- future opportunities;
- listing inventory;
- listing analytics;
- customer analytics;
- agent performance;
- team routing;
- notification preferences;
- AI daily brief;
- auditable automations.

### 2.5 Trust and transaction rails

Trust is a first-class domain, not a badge.

Acarat must support explicit evidence for:

- subject identity;
- advertiser identity;
- agent/agency authority;
- FAL status where applicable;
- listing/ad authorization;
- property/address claims;
- government/provider integration receipts;
- interaction eligibility;
- completed-deal eligibility;
- source provenance;
- stale/expired facts;
- appeals/disputes.

Government or partner systems remain external authorities. Acarat never converts an unavailable or failed integration into a success claim.

## 3. Saudi-first requirements

Acarat is designed for Saudi Arabia before any international abstraction.

Required early concerns:

- Arabic and English;
- RTL and LTR parity;
- Arabic normalization and dialect-aware query understanding;
- SAR-native pricing;
- Hijri/Gregorian display where useful;
- Saudi National Address integration candidate;
- REGA platform/advertiser integration boundary;
- Nafath integration requirement for regulated advertiser flows;
- FAL and advertisement-license evidence;
- Ejar integration boundary for rentals;
- Real Estate Registry integration boundary for title-registered property services when formally available;
- Balady/urban-map data boundary where rights and interfaces permit;
- PDPL privacy minimization;
- Saudi-region data-residency procurement decisions where required.

Official sources are authorities for capability and policy claims. Acarat must not screen-scrape a government website and treat that as a stable integration contract.

## 4. Core decision principles

### 4.1 Evidence before inference

Every important displayed fact has a source class:

- GOVERNMENT_VERIFIED;
- PROVIDER_VERIFIED;
- AGENT_VERIFIED;
- OWNER_PROVIDED;
- ACARAT_OBSERVED;
- ACARAT_CALCULATED;
- MODEL_INFERRED.

The UI must distinguish them.

### 4.2 Uncertainty is product information

A valuation result is not:

> SAR 50,000.

A valid result is closer to:

> Estimated fair annual rent: SAR 48,000–53,000.  
> Central estimate: SAR 50,500.  
> Confidence: High.  
> Comparable transactions: 27.  
> Listing ask: SAR 60,000, about 18.8% above the central estimate.  
> Evidence period and freshness: shown.

Low evidence must produce a wider interval or abstention.

### 4.3 Canonical truth versus projections

Canonical transactional/property truth stays in PostgreSQL/PostGIS.

Rebuildable projections may include:

- full-text search;
- vector retrieval;
- H3 aggregates;
- ClickHouse analytics;
- graph projections;
- map vector tiles;
- 3D assets;
- recommendation features;
- model features;
- summaries.

Projection failure must never mutate canonical property, customer, contract, or authority state.

### 4.4 AI does not own consequential state

The LLM may interpret intent, explain, summarize, rank candidates, draft messages, and propose actions.

It does not silently:

- publish a listing;
- change a price;
- alter a customer requirement;
- accept an offer;
- submit a government transaction;
- expose sensitive identity data;
- send outbound messages without policy;
- mark a contract complete;
- create a verified review.

Consequential actions use deterministic commands, policy checks, authorization, idempotency, and receipts.

## 5. The Property Passport

Every property/unit should expose the richest permitted, source-backed view available.

Candidate sections:

- identity and address;
- property/unit type;
- dimensions and area;
- rooms and amenities;
- building and unit condition;
- floor/parking/elevator/accessibility;
- furnishing;
- media;
- floor plan;
- 360/3D;
- listing history;
- price history;
- asking-price analysis;
- comparable transactions;
- Acarat estimate and interval;
- price per square meter;
- neighborhood statistics;
- schools;
- hospitals;
- mosques;
- parks;
- groceries/retail;
- public services;
- roads;
- commute profiles;
- satellite/aerial context;
- plot/land-use/building-regulation context where legally sourced;
- agent/agency;
- authority evidence;
- freshness;
- missing facts;
- provenance.

## 6. Search as a decision compiler

Conversational search compiles user language into explicit constraints.

Example:

> I want a two-bedroom apartment under 40,000 SAR per year, no more than 15 minutes from the Ministry of Education, with parking and a primary school nearby.

The compiled intent can contain:

- transaction = RENT;
- unit_type = APARTMENT;
- bedrooms = 2;
- annual_rent <= 40000 SAR;
- travel_time(destination) <= 15 minutes;
- parking = REQUIRED;
- nearby(primary_school, radius) = REQUIRED.

The user can refine the same search conversationally:

> Raise the budget to 45k, but make the commute shorter.

The product must show active interpreted constraints and allow direct correction. LLM parsing must not hide the actual query.

## 7. Lists, watchlists, alerts, and comparison

Users can create:

- Favorites;
- custom named lists;
- shared lists;
- investment watchlists;
- land watchlists;
- saved searches.

Alert examples:

- new apartment at or below SAR 40,000 in a neighborhood;
- price drop above 5%;
- new land parcel within selected polygon and price/m² range;
- property returns to market;
- listing gains government verification;
- comparable market range changes materially;
- contract renewal window starts.

Comparison is evidence-based and can compare:

- price;
- fair-price range;
- percentage premium/discount;
- price/m²;
- size;
- age;
- amenities;
- commute;
- POIs;
- market trend;
- agent evidence;
- listing freshness;
- estimated ownership/rental costs when supported;
- investment yield scenarios;
- risk/missing-data flags.

## 8. Land intelligence

Land is a dedicated product mode, not an apartment form with fewer fields.

Land intelligence should support, where rights and evidence permit:

- plot geometry;
- area;
- price and price/m²;
- comparable land transactions;
- time-adjusted local price range;
- frontage;
- road width;
- corner status;
- number of street fronts;
- orientation;
- land-use classification;
- planning/building constraints;
- nearby services;
- development intensity;
- transaction liquidity;
- historical trend;
- confidence and evidence density.

No buildability claim is made from inferred map geometry alone.

## 9. Organic ranking and commercial model

Organic ranking must not be purchasable.

Candidate ranking signals include:

- query relevance;
- hard-constraint satisfaction;
- verified status;
- freshness;
- data completeness;
- location/commute fit;
- price fit;
- duplicate/fraud confidence;
- customer preferences;
- agent response quality;
- listing quality.

Paid promotion, if introduced, must be explicitly labeled and isolated from organic ranking.

Proposed future agent subscription direction:

- SAR 25/month: 20 active listings;
- SAR 50/month: 100 active listings;
- SAR 100/month: unlimited active listings subject to fair-use limits.

Paid external channels and expensive AI/media workloads require separate quota/economics analysis.

## 10. Completion definition

Acarat is not complete because pages render.

A capability is complete only when its owning specification proves:

- semantics;
- authorization;
- privacy;
- negative cases;
- accessibility;
- Arabic/RTL;
- observability;
- performance target where relevant;
- data-source rights;
- deterministic fallbacks;
- migration/rollback;
- tests;
- exact-head CI;
- evidence.

The implementation program is governed by SpecGrain decomposition and Diffcipline execution.
