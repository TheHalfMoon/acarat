# Acarat Architecture Plan

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Architecture rule:** start as a modular monolith with strict domain boundaries; extract services only from measured pressure.

## 1. Deployment shape

Initial production shape:

- apps/web — Next.js/React/TypeScript public marketplace and authenticated web product.
- apps/mobile — React Native/Expo TypeScript application with customer and role-authorized agent workspaces; custom native modules are admitted where MapLibre, voice, camera, secure storage, notifications, or government deep-link flows require them.
- apps/api — Go API and domain application service.
- apps/worker — Go asynchronous worker from the same backend codebase.
- services/intelligence — isolated Python model/feature worker admitted only for ML workloads that materially benefit from Python.
- packages/contracts — versioned API/event schemas and generated clients.
- packages/design-system — shared accessible Arabic/English UI primitives.
- PostgreSQL + PostGIS — canonical operational and geospatial truth.
- object storage — property media, documents, derived 3D assets, exports.
- optional Redis-compatible cache — ephemeral cache/rate-limit only; never canonical state.
- OpenTelemetry — traces/metrics/log correlation.

Do not begin with Kafka, Kubernetes, a graph database, a vector database, or a separate analytics warehouse unless a bounded benchmark proves the need.

## 2. Language selection

### Go

Go is the primary backend because Acarat is dominated by transactional workflows, government/provider integrations, geospatial queries delegated to PostGIS, high-concurrency API traffic, asynchronous jobs, notification fan-out, search orchestration, and low operational complexity.

### TypeScript

TypeScript owns web and mobile presentation concerns: Next.js server-rendered marketplace and SEO, React Native/Expo mobile surfaces, Arabic/RTL, agent/customer dashboards, native/web map rendering, client state, deep links, push-notification UX, camera/media capture, and accessible interaction.

Business authority must not live only in Next.js server actions or mobile client state. Web and mobile call the same authorized domain commands.

### Python

Python is an optional bounded worker for valuation training/inference, feature engineering, offline evaluation, computer vision, 3D reconstruction pipelines, and ranking experiments.

The Python worker never becomes the canonical property/customer/contract database.

### Rust

Rust is optional for a measured hotspot or native/media component. It is not the default backend language.

## 3. Canonical bounded contexts

| Context | Owns | Does not own |
|---|---|---|
| Identity | subject IDs, authentication linkage, sessions, verification references | agent licensing truth |
| Regulatory Trust | FAL/ad-license evidence, platform verification receipts, authority freshness | user profile preferences |
| Agency | agencies, branches, agent memberships, roles | customer intent |
| Property | property identity, parcels/structures/units, source-backed facts | listing commercial state |
| Listing | listing lifecycle, price, availability, media references, publication | property legal truth |
| Geo | normalized locations, polygons, POIs, commute requests, spatial projections | source rights |
| Market Evidence | transaction/market observations, imported official indicators, provenance | valuation result authority |
| Valuation | model versions, comparable sets, estimate/range/confidence/explanation | canonical transaction records |
| Search | parsed intent, search execution, ranking receipts, saved search queries | property truth |
| Customer | customer profile, preferences, lifecycle, saved requirements | agent task state |
| CRM | leads, assignments, tasks, pipeline, activities, follow-up | messaging provider truth |
| Conversation | channel/thread metadata, message references, consent/preferences | contract state |
| Viewing | appointment/viewing requests, attendance/outcome | offer terms |
| Offer | offer/negotiation state and revisions | government contract completion |
| Deal | deal room, checklist, parties, documents, transaction stage | external authority state |
| Contract | local contract reference/lifecycle, renewal dates, external receipt links | external authoritative contract record |
| Reviews | eligibility, review, moderation, dispute state | arbitrary public commentary |
| Alerts | durable watch rules, delivery state, digest preferences | canonical listing state |
| Analytics | event taxonomy, aggregates, metric definitions | operational mutation authority |
| Subscription | plan, entitlements, usage counters | organic ranking |
| Media | media identity, transformations, quality, privacy checks, 3D derivatives | listing authorization |
| AI Assist | prompts/policies, tool calls, proposals, explanations, receipts | silent consequential mutations |

## 4. Primary data model

Every durable top-level entity uses opaque stable IDs, created/updated timestamps, revision/version where concurrent mutation matters, tenant/agency ownership where applicable, provenance links for imported/derived facts, and explicit effective dates for time-sensitive external facts.

Property identity and listing identity are separate.

A single physical property may have multiple historical listings, different agents over time, price changes, rental and sale campaigns at different times, unit-level records, government/source identifiers, and derived market evidence.

## 5. Provenance model

Source-backed facts carry:

- source_kind;
- source_id;
- source_record_id where available;
- observed_at;
- effective_at;
- retrieved_at;
- expires_at where applicable;
- raw_digest or evidence receipt;
- verification_class;
- confidence only for inferred facts;
- supersedes/contradicts relations when needed.

Source classes:

- GOVERNMENT;
- LICENSED_PROVIDER;
- AGENT;
- OWNER;
- USER;
- ACARAT_OBSERVED;
- ACARAT_MODEL.

This borrows the useful provenance/temporal principles from Morize without importing its memory ontology as the Acarat domain model.

## 6. Geospatial architecture

PostGIS is canonical for point/polygon geometry, distance, containment, nearest-neighbor, bounding-box queries, geofences, neighborhoods, parcels where licensed, routes/isochrones returned by routing adapters, and spatial joins.

H3 is a derived aggregation key for price heatmaps, demand/supply density, market trend cells, notification prefiltering, and feature engineering.

H3 cells are not property identity and never replace exact geometry.

## 7. Search architecture

Phase 1:

- PostgreSQL full-text search;
- Arabic-normalized search fields;
- trigram/fuzzy matching;
- PostGIS spatial predicates;
- structured filters;
- deterministic ranking.

Phase 2 benchmark candidates:

- OpenSearch for large search/relevance workloads;
- pgvector or a bounded vector service for semantic retrieval if it materially improves held-out Arabic/English intent evaluation.

The LLM compiles conversation into a typed SearchIntent. Search execution uses deterministic query/filter/ranking code.

Search result receipts should retain interpreted constraints, relaxed constraints, rank features, model/ranker version, evidence timestamp, and explanation fields.

## 8. Saved-search and alert architecture

A saved search stores normalized intent, not only the original sentence.

On relevant listing events:

1. listing transaction commits;
2. outbox records listing.published, listing.price_changed, listing.status_changed, or another explicit event;
3. worker obtains spatial/category candidate watch rules;
4. exact predicate evaluation runs;
5. user preference/dedupe/quiet-hour rules apply;
6. in-app notification is created;
7. optional push/email/WhatsApp/SMS adapters deliver according to policy;
8. callbacks update delivery state only.

A channel failure never removes the in-app notification.

## 9. Async work

Required properties:

- durable;
- idempotent;
- retryable;
- observable;
- dead-letter/reconciliation path;
- transactional enqueue for changes that require follow-up work.

Candidate implementation:

- PostgreSQL outbox + Go worker;
- evaluate riverqueue/river for transactional jobs before admission;
- Watermill patterns may inform event routing;
- Redis queues are optional later and must not become the only record of consequential work.

## 10. Analytics architecture

### Operational metrics

Start with PostgreSQL materialized/rollup tables for low-volume launch analytics.

### Event stream

Canonical event taxonomy includes:

- listing impression;
- search impression;
- map impression;
- property detail view;
- media engagement;
- compare add/remove;
- save/unsave;
- share;
- contact click;
- WhatsApp handoff;
- inquiry;
- viewing request;
- viewing completed;
- offer created;
- offer state change;
- deal stage;
- contract state;
- alert match;
- notification delivery;
- agent response;
- renewal milestone.

Raw events are append-only and privacy-minimized.

### Columnar scale-out

ClickHouse is the preferred warehouse candidate when measured event volume/query latency justify separation.

Internal BI candidates:

- Apache Superset for governed internal exploration;
- Metabase as an alternative subject to license/embedding review.

Customer and agent dashboards use Acarat-owned product APIs and metric definitions. They do not embed an unrestricted BI tool.

### Geospatial analytics

Use deck.gl/Kepler patterns for hex/heatmap layers, large point sets, temporal playback, demand/supply layers, price surfaces, and route/flow visualization.

## 11. Market intelligence data flow

External/official observations enter through ingestion adapters:

SOURCE -> RAW EVIDENCE -> VALIDATION -> NORMALIZATION -> CANONICAL OBSERVATION -> QUALITY CHECKS -> MARKET AGGREGATE -> VALUATION FEATURES

Never:

WEB PAGE -> LLM SUMMARY -> PRICE ESTIMATE

Every model training set binds dataset snapshot ID, source coverage, date range, filters/outlier rules, feature schema, train/validation/test split, model artifact digest, and evaluation report.

## 12. Government and external adapter contract

Every adapter exposes explicit capabilities such as:

- CapabilityStatus;
- ValidateSubject;
- ValidateAgentAuthority;
- ValidateAdvertisement;
- SubmitRentalContract;
- GetTransactionStatus;
- TransferOwnership;
- ResolveAddress;
- ResolvePOI;
- ResolveUrbanConstraint.

An adapter can return:

- SUPPORTED;
- NOT_SUPPORTED;
- AUTH_REQUIRED;
- PARTNER_AGREEMENT_REQUIRED;
- TEMPORARILY_UNAVAILABLE;
- INVALID_REQUEST;
- REJECTED;
- UNKNOWN_OUTCOME.

UNKNOWN_OUTCOME is never converted to success.

Acarat must not claim that RER sale transfer or another government action is automated until a formally supported integration is proven.

## 13. Identity and privacy

Advertiser flows subject to Saudi platform rules must support Nafath integration as required by REGA.

Sensitive government identifiers are not public profile fields. They are minimized, encrypted/tokenized where retention is required, purpose-limited, retention-governed, and access logged.

Public agent identity is represented by product ID plus verified public attributes and authority references that are safe to display.

## 14. Media architecture

Original uploads are immutable media objects.

Derived assets include thumbnails, optimized formats, blur/redaction variants, floor-plan previews, panorama tiles, 3D/digital-twin assets, and quality scores.

Every derived asset binds the source media digest and transform version.

AI-enhanced or staged imagery must be clearly labeled and must never silently replace evidentiary property media.

## 15. Reliability and security

Required cross-cutting controls:

- tenant isolation;
- object-level authorization;
- CSRF/XSS/SSRF protections;
- upload scanning and file-type verification;
- signed object URLs;
- API rate limits;
- secrets outside source control;
- outbound network allowlists for high-risk workers;
- webhook signature validation;
- idempotency keys;
- audit log for consequential actions;
- model/tool allowlists;
- prompt-injection isolation from authoritative commands;
- backup/restore tests;
- dependency/SBOM review.

## 16. Repository shape

Proposed structure:

~~~text
/apps
  /web
  /mobile
  /api
  /worker
/services
  /intelligence
/packages
  /contracts
  /design-system
  /geo-contracts
/docs
  /adr
  /canonical
  /research
  /evidence
  /governance
/.specgrain
~~~

Exact build tooling remains an implementation-gate decision.

## 17. Mobile architecture

Acarat ships one role-aware mobile application first rather than duplicating customer and agent apps.

Customer mobile capabilities include:

- conversational/voice search;
- native map/list discovery;
- saved searches and push alerts;
- lists and compare;
- property/passport/media/3D access;
- contact/viewing/offer/deal state;
- contract notifications;
- private saved places.

Authorized agent mobile capabilities include:

- Agent Terminal home;
- lead inbox;
- customer 360;
- tasks;
- listing inventory;
- viewing calendar;
- offers/deals;
- renewal queue;
- push alerts;
- media capture/upload.

Mobile requirements:

- secure token/credential storage;
- biometric unlock option for sensitive workspaces;
- deep-link and universal-link routing;
- offline-safe read cache for lists/tasks and an explicit queued-command policy;
- push-notification dedupe with canonical in-app notification IDs;
- upload resume/background behavior;
- location permission minimization;
- camera/gallery permission minimization;
- Arabic/RTL parity;
- accessibility;
- no hidden business rule divergence from web.

Property 3D can initially reuse a hardened shared web renderer inside an isolated view when that provides better fidelity, while the map/search/navigation path should use native-capable rendering where benchmarks justify it.

## 18. Extraction triggers

Do not create a microservice until one of these is proven:

- independent scaling materially reduces cost/latency;
- separate security boundary is required;
- separate release cadence is required;
- specialized runtime/hardware is required;
- data-residency contract requires isolation;
- failure isolation has measurable value.

The first likely extraction candidate is the ML/3D worker, not the core property/listing/CRM transaction model.
