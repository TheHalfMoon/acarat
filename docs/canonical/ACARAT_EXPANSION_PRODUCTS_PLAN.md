# Acarat Expansion Products Plan

**Status:** CANONICAL_FUTURE_SCOPE  
**Rule:** these products are part of the Acarat long-term product system but must not destabilize the marketplace, trust, transaction, and intelligence foundation.

## 1. Purpose

Acarat is designed to expand beyond listing discovery into a full Saudi real-estate operating system.

The following founder-approved capability families remain in the canonical direction:

- financing/mortgage marketplace;
- investment and portfolio analytics;
- property management;
- deposits/escrow-like transaction workflows;
- off-plan/developer marketplace;
- enterprise dashboards and data platform.

Each capability has separate regulatory, financial, licensing, and authority gates.

## 2. Financing and mortgage marketplace

### Customer surface

Potential capabilities:

- mortgage affordability calculator;
- down-payment scenarios;
- monthly payment scenarios;
- financing product comparison;
- rate/fee comparison;
- eligibility precheck where supported;
- pre-approval handoff/application where formally integrated;
- financing status;
- document checklist;
- bank/financier offers;
- property-to-financing fit.

### Rules

- calculator assumptions are explicit;
- financial products are sourced from authorized providers;
- rate freshness is displayed;
- no hidden lead-selling behavior;
- no credit decision is invented by Acarat;
- application/pre-approval claims require provider integration;
- regulated financial activity requirements are separately assessed.

### Intelligence

A property comparison can include:

- estimated payment;
- total financing cost under chosen assumptions;
- down-payment amount;
- financing-to-price ratio;
- scenario sensitivity to rate/term.

These are scenarios, not personalized financial advice.

## 3. Investment analytics

Investment mode should support transparent assumptions.

Candidate property metrics:

- gross rental yield;
- net rental yield;
- cap-rate style measure where applicable;
- operating-cost assumptions;
- vacancy assumptions;
- maintenance assumptions;
- cash flow;
- financing scenario;
- price-to-rent;
- market liquidity;
- local rent trend;
- local sale trend;
- Acarat value range;
- downside/upside scenario ranges.

Portfolio view:

- properties;
- acquisition basis;
- current Acarat range;
- rent;
- occupancy;
- contracts;
- expenses;
- cash flow;
- yield;
- concentration by city/neighborhood/type;
- upcoming renewals;
- maintenance;
- documents.

No investment return guarantee is permitted.

## 4. Property management

Acarat can extend Agent Terminal into a landlord/property-manager workspace.

Domains:

- owner;
- managed property;
- managed unit;
- tenant;
- lease/contract reference;
- rent schedule;
- payment status where integrated;
- maintenance request;
- vendor;
- inspection;
- notice;
- document;
- renewal;
- handover;
- deposit record.

Operational surfaces:

- rent/lease calendar;
- vacancies;
- tenant communication;
- renewal queue;
- maintenance inbox;
- task assignment;
- vendor coordination;
- property-level P&L when financial data is available;
- owner statements;
- occupancy analytics.

Ejar remains an external authority for contracts where applicable.

## 5. Deposit and escrow-like workflows

Acarat must distinguish:

- reservation deposit;
- application fee;
- earnest money;
- security deposit;
- escrow;
- platform-held funds;
- provider-held funds.

Holding or moving customer funds can create separate regulated obligations.

Default architecture:

~~~text
PaymentOrEscrowAdapter
  capability_status
  provider
  transaction_type
  amount
  currency
  payer
  beneficiary
  external_reference
  state
  captured_at?
  released_at?
  refunded_at?
  disputed_at?
  reconciliation_receipt
~~~

Acarat should prefer a licensed provider/regulated rail rather than becoming the custodian of funds by accident.

No "escrow" label is used unless the legal/payment structure actually qualifies.

## 6. Off-plan and developer marketplace

Off-plan is a dedicated product domain.

Developer/project model:

- developer;
- project;
- project authority/permit evidence;
- location;
- master plan;
- buildings;
- phases;
- unit inventory;
- unit type;
- unit price;
- reservation status;
- payment schedule;
- construction progress;
- expected completion;
- media;
- 3D/master-plan assets;
- documents;
- sales agent/team.

Customer capabilities:

- project comparison;
- unit comparison;
- payment-plan comparison;
- map/master-plan navigation;
- construction-progress timeline;
- alerts when a unit type/price becomes available;
- reservation/application flow where authorized.

Agent/developer terminal:

- inventory;
- reservations;
- leads;
- pipeline;
- conversion;
- campaign;
- unit velocity;
- price changes;
- demand by unit type;
- payment-plan interest.

Government/project authority evidence is separately qualified.

## 7. Enterprise dashboards

Enterprise roles can include:

- agency executive;
- developer executive;
- operations;
- compliance;
- sales manager;
- marketing;
- finance;
- property-management operator;
- analyst.

Dashboards are role-specific.

Examples:

### Executive

- inventory;
- pipeline;
- closed value;
- renewal book;
- conversion;
- market share proxy where defensible;
- listing health;
- response SLA;
- forecast with confidence.

### Sales

- leads by source;
- assignment;
- pipeline stage;
- follow-up;
- viewing;
- offer;
- close;
- agent/team conversion.

### Marketing

- impressions;
- qualified traffic;
- saved searches reached;
- alert engagement;
- campaign attribution;
- listing-level conversion.

### Compliance

- agent authority;
- listing authority;
- expiring evidence;
- complaints;
- disputes;
- policy exceptions;
- external reconciliation.

### Finance

- subscriptions;
- provider costs;
- payment/escrow adapter reconciliation;
- property-management financial reports when in scope.

## 8. Acarat Data Platform

Acarat's data platform is not a public raw-data dump.

Layers:

1. operational truth — PostgreSQL/PostGIS;
2. append-only product events;
3. market evidence snapshots;
4. derived spatial aggregates;
5. valuation features/artifacts;
6. analytics warehouse when justified;
7. governed semantic metrics;
8. privacy-safe external APIs/products when separately approved.

Potential enterprise data products:

- market trend API;
- neighborhood indicators;
- valuation API;
- comparable API;
- listing-performance API;
- demand insights;
- agent/agency operational exports.

Every external data product requires:

- source redistribution rights;
- privacy assessment;
- aggregation threshold;
- freshness;
- SLA;
- metric/version semantics.

## 9. Forecasting

Forecasts must show uncertainty.

Potential forecasts:

- local rent trend;
- local sale trend;
- inventory;
- demand;
- days on market;
- contract renewals;
- agency pipeline.

Forecasts are planning aids and cannot be presented as guaranteed future price appreciation.

## 10. Cross-product identity

The same canonical entities should power expansion products:

- property;
- unit;
- listing;
- customer;
- agent;
- agency;
- developer;
- deal;
- contract;
- market observation.

Do not create parallel property/customer tables for mortgage, property management, or off-plan modules.

## 11. Cross-product analytics

Shared events and metrics enable lifecycle understanding:

~~~text
DISCOVERY
-> SAVE
-> CONTACT
-> VIEW
-> OFFER
-> DEAL
-> CONTRACT
-> OCCUPANCY / OWNERSHIP
-> MANAGEMENT
-> RENEWAL / RESALE
~~~

This lifecycle is a strategic advantage over a portal that loses the customer after contact.

## 12. Expansion sequencing

These products begin only after their prerequisites are proven.

Recommended later sequence:

1. investment analytics using existing market evidence;
2. property management using existing customer/contract lifecycle;
3. off-plan/developer marketplace using property/listing/Agent Terminal foundations;
4. financing marketplace after provider/regulatory qualification;
5. deposit/payment/escrow rails after legal/provider qualification;
6. enterprise data products after source redistribution/privacy rights.

## 13. Explicit non-authority

This plan does not authorize:

- Acarat to act as a bank;
- Acarat to make credit decisions;
- Acarat to hold escrow funds;
- Acarat to guarantee investment returns;
- Acarat to advertise unverified off-plan inventory;
- Acarat to resell government/provider data without rights.

Each requires separate implementation and regulatory authority.
