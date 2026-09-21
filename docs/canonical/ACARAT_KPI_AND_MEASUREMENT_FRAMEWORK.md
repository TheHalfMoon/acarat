# Acarat KPI and Measurement Framework

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Principle:** analytics must change a decision. A metric with no owner, calculation contract, or action is not a KPI.

## 1. Measurement model

Acarat separates:

- outcome KPIs — whether customers/agents achieve real progress;
- driver metrics — why the outcome moved;
- guardrails — whether apparent progress damaged trust, quality, privacy, reliability, or economics;
- diagnostics — useful drill-downs that are not promoted to top-level KPIs.

Targets are not frozen until Acarat has trustworthy baseline data or a defensible external anchor.

## 2. Customer marketplace primary KPI

### Qualified Marketplace Progression Rate

Definition:

Distinct active property seekers who progress from discovery to at least one qualifying intent/action within the measurement window divided by distinct active property seekers.

Qualifying progression events are versioned and may include:

- verified contact/inquiry;
- viewing request;
- viewing confirmation;
- offer creation;
- deal-room creation.

A raw page view, map pan, favorite, or AI chat message does not by itself count as qualified progression.

Why it matters:

- closer to real customer intent than page views;
- responds to search quality, property trust, price intelligence, and agent availability;
- cannot be improved simply by generating more impressions.

Main drivers:

- Exact-or-Useful Search Rate;
- Property Passport Completeness/Trust Coverage;
- Detail-to-Qualified-Action Rate;
- alert-to-qualified-action progression.

Guardrails:

- stale/unavailable listing rate;
- complaint/report rate;
- customer contact spam/duplicate rate;
- search hard-constraint violation rate.

## 3. Transaction outcome KPI

### Verified Transaction Completion Rate

Definition:

Deals entering a transaction-ready state that reach externally confirmed/qualified completion within the appropriate cohort window divided by deals entering that state.

This metric is segmented by:

- rental;
- sale;
- off-plan when later admitted;
- integration/provider path.

Why it matters:

Acarat's long-term value is not sending a user away after a contact click. It is completing a trustworthy lifecycle.

Drivers:

- deal-room completeness;
- time to missing-party information;
- external submission success;
- reconciliation latency;
- contract/authority exception rate.

Guardrails:

- duplicate external submission rate;
- UNKNOWN_OUTCOME rate;
- transaction dispute rate;
- external reconciliation mismatch.

## 4. Agent primary KPI

### Active Customer Advancement Rate

Definition:

Distinct agent-managed active customers who move to a meaningfully later lifecycle stage during the measurement window divided by distinct active customers with an actionable requirement.

Meaningful progression may include:

- searching -> shortlist;
- shortlist -> viewing;
- viewing -> negotiation/offer;
- negotiation -> deal;
- deal -> contract;
- renewal window -> renewal/completed move.

Rules:

- stage changes need evidence;
- an agent cannot inflate this metric by toggling a stage back and forth;
- terminal lost/no-fit states are measured separately rather than hidden.

Drivers:

- lead first-response time;
- tasks completed on time;
- customer-to-listing match coverage;
- viewing completion;
- offer progression;
- renewal follow-up.

Guardrails:

- customer complaint/opt-out;
- unauthorized outbound message rate;
- assignment churn;
- duplicate customer rate.

## 5. Search quality metrics

### Exact-or-Useful Search Rate

A search is:

- EXACT when results satisfy all hard constraints;
- USEFUL_RELAXED only when the user explicitly accepts a proposed relaxation;
- ZERO_VALID when no qualifying result exists;
- FAILURE when parser/execution violates stated constraints or cannot execute a supported request.

Do not count silent relaxation as success.

### Intent Parse Fidelity

Held-out precision/recall or exact-field accuracy for:

- transaction type;
- location;
- budget;
- rooms;
- area;
- POI;
- commute;
- required amenities;
- exclusions;
- land-specific fields.

Segment by:

- Saudi Arabic;
- Modern Standard Arabic;
- English;
- code-switch;
- voice transcript.

### Hard-Constraint Violation Rate

Search results violating a user-declared hard condition / total results surfaced under hard constraints.

Target direction: as close to zero as technically possible.

## 6. Alert metrics

Outcome:

- Alert Qualified Engagement Rate: alerts resulting in a meaningful property interaction.

Drivers:

- match precision;
- time from listing event to canonical in-app notification;
- external delivery success;
- notification open rate;
- saved-search freshness.

Guardrails:

- duplicate notification rate;
- user mute/disable rate;
- alert complaint rate;
- false-match rate.

## 7. Listing performance metrics

Core listing funnel:

~~~text
SEARCH/MAP IMPRESSION
-> DETAIL VIEW
-> ENGAGED VIEW
-> QUALIFIED CONTACT
-> VIEWING
-> OFFER
-> DEAL
-> CONTRACT
~~~

Recommended product metrics:

- unique search impressions;
- unique map impressions;
- detail unique viewers;
- repeat viewers;
- engaged detail viewers;
- saves;
- compare additions;
- contact intents;
- confirmed inquiries;
- viewing requests;
- completed viewings;
- offers;
- deals;
- confirmed contracts.

Conversion ratios use clearly defined cohorts and unique semantics.

## 8. Agent response metrics

### Time to First Meaningful Response

Start:

earliest qualifying inbound lead/inquiry event.

End:

first confirmed meaningful agent response on a channel where response evidence is available.

Do not treat opening WhatsApp or clicking a link as a confirmed response.

Report:

- median;
- p75;
- p90;
- SLA breach rate.

## 9. Listing quality metrics

### Property Passport Evidence Completeness

Weighted evidence coverage across required/important fields for the property/listing type.

Separate:

- present;
- verified;
- stale;
- inferred;
- missing.

Do not allow AI-generated copy to improve verified completeness.

### Listing Freshness

Time since last verified availability and last material source refresh.

### Duplicate/Suspicion Rate

Listings suppressed or flagged by duplicate/anomaly rules / active listing candidates.

## 10. Valuation KPI family

Technical outcome:

### Calibrated Interval Coverage

For each declared interval level, measure the fraction of held-out outcomes inside the interval.

Example:

A nominal 90% interval should empirically approach 90% coverage in each sufficiently large segment.

Pair with:

- median interval width;
- MAE;
- median absolute error;
- percentage within 5/10/20%;
- quantile loss;
- confidence-bin calibration.

Guardrails:

- low-evidence forced-estimate rate;
- stale-evidence valuation rate;
- out-of-distribution rate;
- segment under-coverage.

Never improve point-error KPI by hiding uncertainty.

## 11. Comparable-engine metrics

- qualifying comparable count;
- effective weighted sample size;
- median comparable distance;
- median comparable age;
- authority-source distribution;
- rejected-anomaly count;
- comparable-set reproducibility.

Customer/agent dashboards can show a simplified subset.

## 12. Land intelligence metrics

- land valuation coverage;
- comparable density;
- price/m2 interval calibration;
- official urban-context coverage;
- source freshness;
- unsupported-buildability-claim rate.

The final guardrail should be zero by contract.

## 13. Trust KPIs

Recommended trust/quality operating metrics:

- verified advertiser/agent coverage;
- verified listing authority coverage;
- stale authority rate;
- expired authority still-public rate;
- reported listing rate;
- confirmed-invalid listing rate;
- verified-review eligibility integrity;
- dispute rate;
- external reconciliation mismatch;
- privacy/security incidents.

Trust metrics are not subordinate to growth.

## 14. Review metrics

Measure:

- eligible interactions/deals;
- review invitation;
- submitted review;
- moderation;
- disputed review;
- removed review;
- verified interaction vs verified deal.

Do not optimize raw review count at the expense of eligibility integrity.

## 15. Retention and lifecycle

Customer:

- saved-search 30/90-day retention;
- return-to-search rate;
- repeat transaction lifecycle;
- alert subscriber retention.

Agent:

- weekly active agents with meaningful work;
- customers actively managed;
- repeat customers;
- renewals;
- listing renewal/republication;
- plan retention after monetization.

## 16. Renewal operations

Primary operational metric:

### Renewal Resolved Before Expiry Rate

Contracts entering the configured renewal window that reach an explicit resolved state before expiration.

Resolved can mean:

- renewed;
- moving/non-renewal confirmed;
- owner decision confirmed;
- another legitimate terminal state.

Do not count repeated reminders as progress.

Drivers:

- 90-day contact rate;
- customer response;
- missing terms;
- external renewal state.

## 17. Agency metrics

Manager scorecards:

- lead distribution;
- unassigned leads;
- SLA;
- active customers;
- pipeline;
- viewing/offer/deal conversion;
- contracts;
- renewals;
- listing health;
- agent workload;
- compliance tasks;
- customer complaints.

Do not collapse these into one opaque ranking of agents.

## 18. Marketplace supply metrics

- active verified listings;
- unique verified properties;
- city/neighborhood coverage;
- property-type coverage;
- new supply;
- expired/stale supply;
- median listing age;
- price-change rate;
- fair-range coverage;
- 3D/floor-plan/media completeness.

## 19. Market liquidity metrics

When evidence supports calculation:

- transaction count;
- listing-to-transaction ratio;
- median days on market;
- inventory months;
- absorption rate;
- price dispersion;
- rent/sale transaction density.

Definitions and source limitations are displayed.

## 20. Product analytics architecture

Event requirements:

- immutable event ID;
- occurred_at;
- received_at;
- schema version;
- actor class;
- session;
- surface;
- entity refs;
- tenant/agency scope where applicable;
- experiment/config revision where applicable;
- privacy classification.

Late/duplicate events have defined handling.

## 21. Semantic metric registry

Every KPI stores:

~~~text
MetricDefinition
  metric_id
  name
  owner
  purpose
  formula
  numerator
  denominator
  entity_grain
  time_grain
  timezone
  filters
  exclusions
  source_events
  source_tables
  version
  effective_at
  deprecated_at?
  privacy_class
~~~

Dashboards do not redefine formulas independently.

## 22. Analytics tools

### PostgreSQL

Launch operational metrics and small-scale rollups.

### ClickHouse

Scale candidate for high-volume event and analytical workloads when measured Postgres query/volume pressure justifies it.

### Apache Superset

Internal analytical exploration and governed BI candidate.

### deck.gl / Kepler patterns

Geospatial analytical visualization.

### OpenTelemetry / Prometheus / Grafana

Operational reliability telemetry, not business KPI truth.

Acarat customer/agent KPI APIs remain Acarat-owned.

## 23. Targets

No fixed numeric business targets are canonical at planning foundation because Acarat has no trustworthy live baseline yet.

Target-setting gate:

1. production instrumentation validated;
2. 4–8 weeks of representative baseline or sufficient launch cohort evidence;
3. bot/internal traffic excluded;
4. metric definitions frozen for the target period;
5. segment distribution inspected;
6. target anchored by observed baseline plus planned product/operating leverage.

Reliability/security zero-tolerance invariants can be set before baseline where appropriate.

## 24. Dashboard design rule

Every top-level card answers at least one of:

- Is this healthy?
- Did it change?
- Why?
- What needs action?
- What entity should I inspect?

Avoid decorative dashboards.

## 25. Metric ownership

Suggested owners:

- Marketplace/Search: product/search owner;
- Trust/Authority: trust/compliance owner;
- Agent Terminal: agent product owner;
- Transaction: transaction/integration owner;
- Valuation: market intelligence owner;
- Reliability: platform owner;
- Privacy/Security: security/privacy owner.

A metric without an accountable owner remains diagnostic until ownership is assigned.

## 26. Data quality guardrails

Before an executive/agent metric is trusted:

- freshness;
- completeness;
- duplicate event rate;
- event-order issues;
- identity merge behavior;
- source coverage;
- time-zone correctness;
- metric backfill/recomputation;
- known gaps.

Dashboards must display material data-quality warnings.
