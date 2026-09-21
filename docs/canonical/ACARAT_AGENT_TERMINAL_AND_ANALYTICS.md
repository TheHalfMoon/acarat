# Acarat Agent Terminal and Analytics Plan

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Goal:** make Acarat the daily operating system for a Saudi real-estate agent, not another place where the agent manually republishes inventory.

## 1. Terminal home

The default Agent Terminal is an action surface, not a generic dashboard.

It answers:

- What needs my attention now?
- Which new leads are waiting?
- Which customers have gone cold?
- Which viewings are today?
- Which offers need action?
- Which contracts expire soon?
- Which listings are underperforming?
- Which listings are priced above/below their local evidence range?
- Which customers now have new matching inventory?
- Which tasks can be safely automated?
- How am I performing this week/month?

The home should contain:

- Today;
- Inbox;
- Tasks;
- New Leads;
- Upcoming Viewings;
- Offers;
- Deals;
- Renewals;
- Alerts;
- Listing Performance;
- Market Movement;
- AI Daily Brief.

## 2. Customer 360

Every customer has one durable timeline.

Customer profile includes:

- identity/contact information permitted for the agent;
- preferred language;
- communication consent/preferences;
- lifecycle status;
- assigned agent/team;
- first interaction;
- last interaction;
- next action;
- notes;
- tags;
- source/campaign;
- property requirements;
- saved searches;
- saved properties;
- comparisons;
- messages;
- calls/contact handoffs;
- viewings;
- offers;
- deals;
- contracts;
- renewal dates;
- previous properties;
- documents where authorized;
- notification preferences.

## 3. Customer lifecycle

Suggested lifecycle:

~~~text
PROSPECT
NEW_LEAD
CONTACTED
QUALIFIED
SEARCHING
SHORTLISTED
VIEWING
NEGOTIATING
UNDER_CONTRACT
ACTIVE_CUSTOMER
RENEWAL_WINDOW
COMPLETED
LOST
DORMANT
DO_NOT_CONTACT
~~~

Lifecycle and pipeline stage are not identical.

A past customer can become a new active opportunity without destroying history.

## 4. Previous, current, and future customers

### Previous customers

Agent can filter:

- completed rental;
- completed sale;
- lost;
- expired;
- no response;
- past landlord/seller;
- past tenant/buyer.

Useful actions:

- follow-up;
- request verified review when eligible;
- renewal monitoring;
- new-property match;
- referral note.

### Current customers

Views:

- needs contact;
- actively searching;
- viewing scheduled;
- negotiating;
- contract pending;
- active contract;
- renewal window.

### Future opportunities

Derived opportunity views can include:

- contract expires in 120/90/60/30 days;
- previous buyer may own a property suitable for resale;
- previous tenant is searching again;
- new listing matches a dormant requirement;
- landlord listing likely needs renewal/repricing;
- customer requested future notification.

Derived opportunities are suggestions, not automatic outreach permission.

## 5. Customer requirements

Requirements are structured and versioned.

Candidate fields:

- rent/buy;
- property types;
- city;
- neighborhoods;
- custom polygons;
- min/max budget;
- payment period;
- bedrooms;
- bathrooms;
- min/max area;
- furnished;
- parking;
- elevator;
- floor preferences;
- age/condition;
- POI requirements;
- saved commute destinations;
- max travel times;
- land-specific requirements;
- must-have;
- nice-to-have;
- excluded features.

The original natural-language request is preserved, but matching uses the normalized requirement set.

Requirement changes create history so the agent can understand how the search evolved.

## 6. Smart matching

For each customer:

- exact matches;
- near matches;
- new today;
- price drops;
- newly verified;
- back on market;
- strong value;
- high match but one relaxed criterion.

Each match explains:

- hard constraints;
- budget fit;
- commute fit;
- neighborhood fit;
- space fit;
- amenities;
- value position;
- missing facts.

The agent can create a shortlist and send it through an authorized channel.

## 7. Lead inbox

Every qualifying inbound action can create/attach a lead:

- in-app inquiry;
- contact agent;
- WhatsApp handoff;
- email;
- call request;
- viewing request;
- offer/application;
- property question;
- listing-specific chat.

Deduplication attempts to associate the event with an existing customer.

No event should create duplicate customers blindly.

## 8. Lead routing

For agencies:

- round robin;
- branch;
- neighborhood;
- property owner;
- listing agent;
- language;
- workload;
- specialty;
- team availability.

Routing produces a receipt:

- reason;
- rule revision;
- assignment time;
- previous assignment;
- override.

## 9. SLA and response analytics

Measure:

- time to first agent response;
- time to meaningful response;
- unanswered leads;
- SLA breach;
- response distribution;
- after-hours volume.

Do not fake response performance from a click that merely opened WhatsApp. Where provider callbacks are unavailable, distinguish HANDOFF_STARTED from MESSAGE_CONFIRMED/REPLIED.

## 10. Task engine

Tasks can originate from:

- user-created task;
- lead SLA;
- viewing follow-up;
- offer follow-up;
- missing listing data;
- government verification expiry;
- contract expiry;
- renewal window;
- customer inactivity;
- new smart match;
- price anomaly;
- incomplete deal room.

Task fields:

- owner;
- customer;
- property/listing/deal link;
- due date;
- priority;
- source rule;
- action type;
- status;
- completion evidence.

## 11. Conversations

Unified conversation timeline can reference:

- in-app chat;
- WhatsApp Business;
- email;
- SMS;
- call event;
- notes.

Candidate source patterns:

- Chatwoot for omnichannel inbox/assignment/reporting concepts.
- Novu for notification workflow/preferences/digests.

Acarat should own its customer/property/deal semantics even if it adopts an external communication component.

## 12. Viewing operations

Agent views:

- requested;
- awaiting confirmation;
- confirmed;
- today;
- completed;
- cancelled;
- no-show;
- follow-up due.

After a completed verified viewing:

- customer requirement may be updated with explicit user/agent confirmation;
- feedback can be captured;
- listing/agent review eligibility can be considered according to policy;
- task is created for next action.

## 13. Offers and negotiation

Offer records support:

- amount;
- rent/sale context;
- payment terms;
- conditions;
- attachments;
- revision history;
- expiry;
- participants;
- agent notes;
- customer-visible status.

Every material change creates a revision.

No LLM changes offer terms.

## 14. Deal room

A deal room collects:

- parties;
- property/listing;
- selected offer;
- checklist;
- documents;
- external authority references;
- approvals;
- payment state where supported;
- contract state;
- issues;
- audit trail.

Deal state is explicit:

~~~text
PREPARING
AWAITING_PARTY_INFORMATION
AWAITING_VERIFICATION
READY_FOR_EXTERNAL_SUBMISSION
SUBMITTED
AWAITING_EXTERNAL_PARTIES
CONFIRMED
REJECTED
CANCELLED
UNKNOWN_OUTCOME
CLOSED
~~~

Unknown external outcome blocks closure.

## 15. Rental contract lifecycle

Where an authorized Ejar integration is available:

- prepare contract data;
- validate local prerequisites;
- submit via the supported integration;
- retain request/response receipt;
- track external state;
- show required party action;
- reconcile final confirmation;
- record contract reference;
- schedule lifecycle/renewal milestones.

Acarat never simulates Ejar confirmation.

## 16. Renewal center

Dedicated renewal queues:

- 120 days;
- 90 days;
- 60 days;
- 30 days;
- 14 days;
- 7 days;
- expires today;
- expired;
- renewal started;
- renewed;
- customer moving;
- landlord changing terms.

Agent can bulk filter but consequential outbound messages remain consent/policy governed.

## 17. Listing inventory

Views:

- draft;
- verification required;
- ready to publish;
- live;
- paused;
- expired;
- rented/sold;
- stale;
- low quality;
- high performance;
- needs repricing;
- missing media;
- missing 3D/floor plan;
- authority expiring.

## 18. Listing analytics

Every listing should expose a funnel.

### Discovery

- search impressions;
- map impressions;
- recommendation impressions;
- alert impressions;
- neighborhood-page impressions;
- agent-profile impressions.

### Engagement

- property page views;
- unique viewers;
- repeat viewers;
- average engaged time;
- photo opens;
- gallery completion;
- video views/completion;
- 360 starts/completion;
- 3D tour starts/engagement;
- floor-plan opens;
- map interactions;
- satellite view opens;
- compare adds;
- saves;
- shares.

### Intent

- contact clicks;
- WhatsApp handoffs;
- call requests;
- email;
- chat starts;
- viewing requests;
- qualified leads;
- offers.

### Outcome

- viewing completed;
- offer accepted;
- contract submitted;
- contract confirmed;
- closed.

### Efficiency

- view-to-contact;
- contact-to-qualified;
- qualified-to-viewing;
- viewing-to-offer;
- offer-to-close;
- median response time;
- cost per lead if paid promotion exists.

## 19. Listing diagnostics

Diagnostics must be evidence-driven.

Examples:

- high impressions + low detail click: weak first image/title/price position;
- high detail views + low contact: price/value mismatch or missing trust facts;
- high saves + low viewings: customer interest but friction/availability issue;
- high 3D engagement + low contact: investigate price or agent responsiveness;
- low impressions: incomplete metadata, narrow search eligibility, location problem, or low demand;
- many inquiries + slow agent response: operational issue.

The product should show contributing facts and avoid claiming causal certainty from correlation alone.

## 20. Price-position analytics

For every listing with sufficient evidence:

- asking price;
- Acarat fair range;
- central estimate;
- ask-vs-center percentage;
- neighborhood percentile;
- price/m2 percentile;
- confidence;
- comparable count;
- trend.

Agent may simulate:

- what if rent is SAR 55k?;
- what if sale price drops 3%?;
- how many saved-search audiences become eligible?;

Scenario output is not an automatic price change.

## 21. Audience analytics

An agent can see privacy-safe aggregate demand:

- number of active saved searches matching listing;
- budget distribution;
- bedroom demand;
- neighborhood demand;
- commute-interest clusters;
- alert subscribers;
- property-type demand.

Never expose another customer's identity merely because their saved search matches a listing.

## 22. Market dashboard

Agent market intelligence:

- local median/range;
- new supply;
- rental/sale trend;
- days on market;
- price changes;
- transaction density;
- demand;
- popular search constraints;
- land price/m2;
- comparable explorer.

All metrics display period, geography, sample count, and source class.

## 23. Agent profile analytics

Agent sees:

- active listings;
- verified listings;
- profile views;
- listing views;
- leads;
- qualified leads;
- response time;
- viewings;
- offers;
- closed deals;
- verified reviews;
- rating distribution;
- repeat customers;
- renewal success;
- conversion funnel.

Acarat should not invent a single opaque "agent score" that could unfairly govern livelihood.

## 24. Agency analytics

For team/office roles:

- agent workload;
- lead assignment;
- SLA;
- listing inventory;
- team conversion;
- pipeline;
- renewals;
- geography;
- source/campaign;
- quality/compliance tasks.

Access is role-scoped.

## 25. AI daily brief

Acarat can create a daily brief from deterministic facts.

Example:

> 7 new leads need action.  
> 3 viewings are today.  
> 5 customers entered a 60-day renewal window.  
> 2 listings are more than 15% above their current Acarat fair center.  
> 9 new listings match existing customer requirements.  
> Listing AC-123 has strong views but zero inquiries after 6 days.

The LLM can summarize facts but cannot invent events or silently perform actions.

## 26. AI copilot actions

Permitted proposal examples:

- draft follow-up;
- summarize conversation;
- suggest next task;
- build shortlist;
- explain listing performance;
- explain market movement;
- draft listing description from verified facts;
- compare properties;
- prepare a contract checklist.

Actions requiring explicit policy/human authority:

- send message;
- publish;
- change price;
- assign agent;
- submit contract;
- modify customer consent;
- close deal.

## 27. Notifications

Agent notification center supports:

- new lead;
- lead SLA warning;
- viewing request;
- viewing reminder;
- offer;
- deal update;
- contract update;
- renewal window;
- authority expiry;
- listing quality issue;
- listing price-position shift;
- new customer match;
- task due;
- team assignment.

Preferences support immediate, digest, muted category, and quiet hours.

## 28. Analytics implementation

Launch:

- append-only privacy-minimized events;
- PostgreSQL operational aggregates/materialized rollups;
- stable metric definitions;
- event schema versioning.

Scale:

- ClickHouse candidate for high-volume events;
- derived Acarat metric APIs;
- Apache Superset candidate for internal BI;
- deck.gl/Kepler-style geospatial visualization.

Product UI does not expose a raw internal warehouse.

## 29. Analytics correctness

Every metric defines:

- numerator;
- denominator;
- time window;
- timezone;
- unique-vs-total semantics;
- bot/internal traffic exclusion;
- event version;
- late event handling;
- deleted/merged entity behavior.

Example:

DETAIL_TO_CONTACT_RATE = unique listing visitors with a qualifying contact intent / unique listing visitors with a detail view in the selected period.

## 30. Privacy

Analytics must avoid:

- exposing customer identity in aggregate demand;
- cross-agent leakage;
- retaining unnecessary raw IP/device data;
- deriving sensitive personal characteristics;
- using private customer messages as training data without explicit lawful basis.

## 31. Initial implementation order

1. customer 360;
2. leads and assignment;
3. task engine;
4. listing inventory;
5. event taxonomy;
6. listing funnel analytics;
7. viewing lifecycle;
8. offers;
9. deal room;
10. contract/renewal lifecycle;
11. smart matching;
12. notification center;
13. market intelligence;
14. AI daily brief;
15. agency/team analytics.
