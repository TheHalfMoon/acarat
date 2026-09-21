# Acarat Domain and Data Model

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Rule:** this document defines semantic ownership and identity. Exact SQL schema is refined by implementation SpecGrains.

## 1. Identity rules

Every canonical entity receives an opaque stable Acarat ID.

External identifiers are attributes/evidence, never primary application identity.

Do not use:

- national ID;
- FAL number;
- advertisement-license number;
- Ejar contract number;
- address key;
- provider listing ID;

as the internal primary key.

External identifiers may change, expire, collide across namespaces, or require restricted visibility.

## 2. Time model

Important records distinguish:

- created_at — when Acarat created the record;
- updated_at — last Acarat mutation;
- observed_at — when Acarat/provider observed an external fact;
- effective_from/effective_to — when a fact is valid in the domain;
- retrieved_at — when external data was fetched;
- expires_at — when evidence must no longer be treated as fresh.

Historical price, authority, listing, contract, and market facts are append/history-oriented.

## 3. Actor model

### Subject

Represents one authenticated person/service identity.

Fields conceptually include:

- subject_id;
- identity-provider bindings;
- locale;
- timezone;
- status;
- created_at.

### CustomerProfile

Represents customer-domain preferences and contact relationship.

A subject can have a customer profile without being an agent.

### AgentProfile

Represents professional public/private agent state.

It links to authority evidence rather than embedding licensing truth.

### Agency

Represents a brokerage/organization.

### AgencyMembership

Links:

- subject/agent;
- agency;
- branch;
- role;
- effective dates;
- status.

Membership history is preserved.

## 4. Regulatory authority model

### AuthorityEvidence

Generic external verification receipt.

Candidate fields:

- authority_evidence_id;
- subject/entity ref;
- authority_type;
- issuer;
- namespace;
- external_reference;
- status;
- effective_from;
- expires_at;
- checked_at;
- receipt_digest;
- raw_evidence_ref when retention is allowed;
- public_display_policy.

Authority types can include:

- identity verification;
- agent/FAL authority;
- advertisement authority;
- agency authority;
- developer/project authority;
- property/contract external evidence.

## 5. Property hierarchy

Acarat distinguishes physical/legal concepts.

### Property

Long-lived identity for a real-estate asset/location.

Possible property categories:

- LAND;
- BUILDING;
- COMPOUND;
- PROJECT;
- OTHER.

### Parcel

Plot/parcel geometry and land-specific attributes when source-backed.

### Structure

Building/structure identity.

### Unit

Independently marketable/occupiable unit such as:

- apartment;
- villa;
- floor;
- office;
- shop;
- showroom;
- warehouse;
- room;
- other supported unit.

Relationships:

~~~text
PROPERTY
  -> PARCEL*
  -> STRUCTURE*
       -> UNIT*
~~~

The model supports standalone land without a structure.

## 6. Property facts

Facts are not a single mutable JSON blob.

Conceptual PropertyFact:

~~~text
PropertyFact
  fact_id
  entity_ref
  fact_type
  value
  unit?
  source_evidence_ref
  verification_class
  confidence?
  effective_from?
  effective_to?
  observed_at
  supersedes?
  contradicts?
~~~

High-value fact types include:

- area;
- bedrooms;
- bathrooms;
- floor;
- floors;
- age/year built;
- parking;
- elevator;
- furnishing;
- condition;
- frontage;
- road width;
- orientation;
- land use;
- building regulation reference.

Implementation may denormalize current projections while preserving source history.

## 7. Location model

### Location

Contains:

- normalized point;
- accuracy/precision;
- country/region/city/district;
- address representation;
- address authority reference;
- entrance point where available.

### GeometryObservation

For:

- parcel polygon;
- building footprint;
- neighborhood polygon;
- service area.

Every geometry binds source and accuracy.

## 8. Listing model

A Listing is a marketing campaign, not the property itself.

Fields conceptually:

- listing_id;
- property/unit ref;
- transaction kind;
- agent/agency;
- advertiser subject;
- status;
- availability;
- asking price;
- rent period;
- publication dates;
- authority evidence;
- description;
- source;
- quality/completeness state.

Listing status:

~~~text
DRAFT
VERIFICATION_REQUIRED
READY
LIVE
PAUSED
UNDER_OFFER
RENTED
SOLD
EXPIRED
WITHDRAWN
REJECTED
~~~

Exact states are later refined.

## 9. Listing revision

Material listing changes create revision/evidence history.

Examples:

- asking price;
- availability;
- description;
- property facts;
- media set;
- agent assignment;
- authority state.

Price history must not depend on analytics event logs.

## 10. Price model

### AskingPriceObservation

Fields:

- listing;
- amount;
- currency;
- period/unit;
- effective_at;
- ended_at;
- source;
- revision.

### MarketObservation

Separate evidence from completed/official market sources.

Do not merge asking prices and completed transaction prices into one unlabeled table.

## 11. Market observation

Conceptual fields:

- observation_id;
- source;
- source record;
- transaction kind;
- property type;
- location/geometry;
- time;
- amount;
- area;
- price/m2;
- attributes;
- quality flags;
- evidence digest.

Observations can be individual or aggregate, but the grain is explicit.

## 12. Market snapshot

A MarketSnapshot binds the exact evidence frontier used by analytics/valuation.

Fields:

- snapshot_id;
- geography;
- segment;
- as_of;
- source snapshots;
- filters;
- quality-rule version;
- aggregate version;
- digest.

## 13. Comparable set

A ComparableSet is immutable after issuance.

Fields:

- comparable_set_id;
- subject;
- valuation kind;
- market snapshot;
- selection policy version;
- candidate count;
- selected comparable refs;
- weights;
- rejected reasons;
- summary;
- digest.

This makes displayed estimates reproducible.

## 14. Valuation model

### ModelBundle

Binds:

- model family;
- code revision;
- feature schema;
- training snapshot;
- artifact digest;
- calibration policy;
- deployment status.

### ValuationResult

Binds:

- subject;
- estimate low/center/high;
- confidence;
- comparable set;
- market snapshot;
- model bundle;
- explanation facts;
- caveats;
- as-of;
- abstention.

Never overwrite old valuations when market evidence changes.

## 15. Neighborhood model

A Neighborhood is a spatial entity with source-backed geometry.

Derived NeighborhoodSnapshot may contain:

- rent distributions;
- sale distributions;
- land distributions;
- transaction count;
- inventory;
- days on market;
- demand;
- services;
- trend.

Snapshots are time-versioned.

## 16. POI model

POI facts include:

- POI ID;
- source namespace;
- category;
- name;
- geometry;
- source freshness;
- rights policy.

The same school/hospital may appear from multiple sources and require identity reconciliation.

## 17. Routing and commute

### SavedPlace

Private user destination:

- owner;
- label;
- geometry;
- privacy policy;
- source.

### RouteReceipt

Binds:

- origin;
- destination;
- mode;
- provider;
- requested_at;
- travel time;
- distance;
- traffic/time assumptions;
- expires_at.

Search ranking should not rely indefinitely on stale route receipts.

## 18. Search model

### SearchIntent

Versioned structured requirement compiled from filters/text/voice/map.

### SearchExecution

Binds:

- intent version;
- index/source frontier;
- query policy;
- ranking version;
- result IDs/scores;
- relaxed constraints;
- timestamp.

### SavedSearch

References one normalized intent version plus notification policy.

## 19. User lists

### PropertyList

Fields:

- owner;
- title;
- visibility;
- collaborators;
- created_at.

### PropertyListItem

- property/listing;
- note;
- tags;
- user status;
- added price snapshot;
- added_at.

List identity survives listing price changes.

## 20. Alert model

### WatchRule

Derived from:

- saved search;
- property;
- list;
- market condition.

### AlertMatch

Records deterministic match:

- rule;
- triggering event;
- entity;
- matched conditions;
- evaluated policy version;
- timestamp.

### Notification

Canonical user notification.

### DeliveryAttempt

External channel attempt.

Notification and delivery are separate so provider failure does not erase the product event.

## 21. Lead/customer model

### Lead

An inbound opportunity/event requiring assignment/qualification.

A Lead can be associated with an existing CustomerProfile.

### CustomerRequirement

Versioned structured property requirement.

### CustomerLifecycle

Current projection from immutable/history events.

Do not destroy previous customer history when a new requirement begins.

## 22. CRM activity

Activity types:

- inquiry;
- note;
- task;
- message reference;
- call reference;
- viewing;
- offer;
- deal;
- contract;
- lifecycle transition.

CRM timeline is a projection over domain records, not a free-form source of truth.

## 23. Task model

Task fields:

- task_id;
- owner;
- tenant/agency;
- source type/ref;
- customer;
- listing/property/deal;
- due;
- priority;
- status;
- completion evidence.

Automation-created tasks identify the rule/version that created them.

## 24. Conversation model

### Conversation

Links customer/agent/agency and optional property/listing/deal context.

### MessageReference

Stores:

- channel;
- external provider ID;
- direction;
- sender;
- recipient scope;
- timestamp;
- consent/purpose;
- body/content reference according to privacy policy.

Provider delivery/read state is separate from CRM task state.

## 25. Viewing model

Viewing:

- listing/property;
- customer;
- agent;
- proposed/confirmed times;
- location;
- status;
- attendance;
- outcome;
- evidence.

Viewing completion may create review eligibility according to policy.

## 26. Offer model

Offer:

- listing/property;
- customer;
- amount/terms;
- version;
- status;
- effective/expiry;
- attachments;
- author;
- acceptance/rejection evidence.

Material term changes create a new revision.

## 27. Deal model

Deal coordinates a transaction process.

Fields:

- deal_id;
- listing/property;
- parties;
- selected offer;
- transaction kind;
- stage;
- checklist;
- external adapters;
- status;
- audit.

Deal state and external contract state remain separate.

## 28. Contract model

ContractRecord is Acarat's lifecycle/reference record.

It can point to an authoritative external contract.

Fields:

- contract_id;
- deal;
- external authority/provider;
- external reference;
- status;
- start;
- end;
- renewal policy;
- checked_at;
- evidence.

Acarat does not reproduce external legal truth beyond what the integration/rights permit.

## 29. Renewal model

RenewalCase:

- contract;
- customer/landlord;
- window opened;
- current state;
- proposed terms;
- tasks;
- external renewal ref;
- resolution.

History is retained across renewals.

## 30. Review model

### ReviewEligibility

Source:

- viewing;
- service interaction;
- completed deal;
- contract.

### Review

- author;
- target agent/agency/listing/property as policy allows;
- eligibility;
- rating dimensions;
- text;
- status;
- submitted_at.

### ReviewModeration

Separate record for moderation/dispute/appeal.

## 31. Media model

### MediaAsset

Original upload identity.

### MediaDerivative

References source asset and transform pipeline.

Types:

- optimized image;
- thumbnail;
- redacted public image;
- video transcode;
- panorama;
- floor plan;
- mesh;
- Gaussian splat;
- 3D viewer package.

## 32. Analytics event

Business event and analytics event are separate concepts.

AnalyticsEvent includes:

- event ID;
- schema version;
- occurred/received time;
- actor/session;
- surface;
- entity refs;
- tenant scope;
- privacy class;
- properties.

Consequential domain actions emit their own audit/domain records independently of analytics success.

## 33. Subscription/entitlement

### Plan

Defines commercial product.

### Entitlement

Examples:

- active listing count;
- team seats;
- advanced analytics;
- automation quota;
- media processing quota.

Subscription status must never alter organic search rank.

## 34. Developer/off-plan model

Future domain:

- Developer;
- DevelopmentProject;
- ProjectPhase;
- Building;
- ProjectUnit;
- InventoryState;
- PaymentSchedule;
- ConstructionProgress;
- Reservation.

These reference canonical property/location concepts.

## 35. Property management model

Future domain:

- ManagedProperty;
- ManagementMandate;
- Tenancy;
- RentSchedule;
- PaymentReference;
- MaintenanceRequest;
- Inspection;
- VendorWorkOrder;
- OwnerStatement.

Do not build separate tenant/property identity systems.

## 36. Financing model

Future domain:

- FinancingProvider;
- FinancingProductSnapshot;
- AffordabilityScenario;
- FinancingInquiry;
- PreApprovalReference;
- FinancingApplicationReference.

Provider result is external authority; Acarat calculator is not a credit decision.

## 37. Payment/deposit model

Future domain:

- PaymentIntent;
- DepositCase;
- ProviderLedgerReference;
- Refund;
- Dispute;
- ReconciliationReceipt.

Raw card/payment secrets are not part of the Acarat domain store.

## 38. Audit model

AuditEvent records:

- principal;
- action;
- target;
- authorization/policy revision;
- request ID;
- before/after digest when appropriate;
- timestamp;
- result;
- external receipt.

Audit records are not editable ordinary CRM notes.

## 39. Merge and deduplication

Acarat needs merge semantics for:

- duplicate subject;
- duplicate customer;
- duplicate property;
- duplicate POI;
- duplicate listing.

Merge never silently deletes provenance.

Record:

- canonical target;
- aliases;
- merged refs;
- reason;
- actor;
- timestamp;
- undo/recovery policy.

## 40. Deletion/redaction

Each entity defines:

- customer deletion effect;
- regulatory retention;
- contract retention;
- audit retention;
- analytics deletion/anonymization;
- derived projection cleanup;
- backup handling;
- external-system limitations.

Acarat must not promise deletion from providers it does not control.

## 41. Projection rule

Derived systems include:

- search index;
- H3 aggregates;
- analytics warehouse;
- graph projection;
- valuation feature store;
- 3D derivatives;
- summaries.

Every projection binds a source frontier/version and is rebuildable.

Projection loss cannot destroy canonical domain truth.

## 42. Schema evolution

Persistent schemas require:

- migration ID;
- forward/backward compatibility decision;
- rollback/recovery;
- data backfill plan;
- validation;
- zero/low-downtime strategy when applicable.

API/events are versioned separately from DB representation.

## 43. Implementation gate

Exact tables, indexes, constraints, enums, and API field names are owned by future executable SpecGrains.

They must preserve this semantic separation unless an ADR revises the model with evidence.
