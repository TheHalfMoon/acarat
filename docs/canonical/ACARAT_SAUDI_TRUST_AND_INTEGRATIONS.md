# Acarat Saudi Trust and Integration Matrix

**Status:** LIVE_RESEARCH_SNAPSHOT  
**Research date:** 2026-09-21  
**Rule:** public service evidence is not equivalent to an approved production API integration.

## 1. REGA electronic real-estate platform licensing

Official source:
- https://rega.gov.sa/en/rega-services/eservices/license-of-electronic-real-estate-platforms/

Observed requirements relevant to Acarat include:

- electronic real-estate platform licensing;
- valid commercial registration including real-estate brokerage activity code 682010;
- qualification requirements for the responsible manager;
- complaints mechanism;
- intellectual-property policy;
- privacy policy;
- platform terms and conditions;
- National Single Sign-On/Nafath integration for advertisers;
- electronic integration with REGA;
- Saudi Business Center authentication certification;
- technical integration completion before licensing flow completion.

Acarat planning implication:

- regulatory integration is P00/P02 work, not a launch-week afterthought;
- advertiser onboarding must support the required Nafath boundary;
- public-agent/listing trust cannot be implemented as a self-declared checkbox;
- production launch requires evidence of the actual Acarat entity/platform licensing status.

Current public REGA news also reports dozens of licensed electronic real-estate platforms and confirms technical integration as part of the licensed-platform regime. Competitor licensing status must be rechecked when used in market claims.

## 2. FAL and agent authority

REGA publicly describes FAL as the official authorization for real-estate brokerage/service activities under the brokerage regime.

Acarat should model:

~~~text
AgentAuthorityEvidence
  agent_subject_id
  authority_type
  authority_reference
  issuing_authority
  status
  effective_at?
  expires_at?
  checked_at
  evidence_receipt
  public_display_fields[]
~~~

Rules:

- do not display national ID publicly;
- retain only the identity data needed for lawful product/regulatory purposes;
- authority status can expire or be revoked;
- a cached verification must have a freshness policy.

## 3. Nafath

Required platform boundary:

- advertisers use Nafath where required by REGA's platform rules.

Acarat implementation remains adapter-based because exact onboarding, credentials, environments, callbacks, and production approval depend on the formal integration channel.

No fake Nafath stub may be enabled in production.

## 4. Ejar digital integration

Official source:
- https://www.ejar.sa/ar/page/136435

The official Ejar page describes direct digital integration between Ejar and real-estate marketing platforms.

Observed journey:

1. property and rental-unit information is registered in the real-estate platform;
2. the rental contract is registered in the platform;
3. the contract is automatically sent to Ejar for authentication by the parties.

This directly supports the Acarat target journey when a formal integration agreement/technical interface is available.

Acarat contract adapter must support:

- capability status;
- preflight validation;
- idempotent submission;
- external request ID;
- party-action state;
- reconciliation;
- rejection;
- cancellation where supported;
- unknown outcome;
- final confirmed external contract reference.

A local Acarat deal does not become a government-confirmed rental contract until Ejar confirmation is reconciled.

## 5. Ejar renewal lifecycle

Official Ejar documentation also exposes auto-renewal workflows for landlords/tenants and brokers.

Acarat should therefore treat renewal as a first-class contract lifecycle:

- renewal eligibility;
- renewal window;
- party notification;
- changed terms;
- external renewal action;
- completion/rejection;
- next renewal date.

The Agent Terminal renewal center can be useful even before direct renewal API admission by tracking known contract dates and required next actions.

## 6. Real Estate Registry

Official source:
- https://rer.sa/en

Observed public services include:

- First Registration;
- Ownership Transfer;
- Split and Merge;
- Rights, Restrictions, and Responsibilities Management.

Acarat planning implication:

- ownership transfer is a real public RER capability;
- the current public service page alone does not prove a general-purpose Acarat production API contract.

Therefore:

~~~text
RERAdapter.TransferOwnership = PARTNER_AGREEMENT_REQUIRED
~~~

until a supported integration/onboarding path is proven.

Acarat can still prepare a sale deal room and guide required readiness without claiming automated title transfer.

## 7. National Address API

Official source:
- https://api.address.gov.sa/

Official documentation currently exposes:

- Free Text Search;
- Fixed Search;
- Bulk Search;
- Verify an Address;
- Address Geocode;
- POI Free Text Search;
- POI Fixed Search;
- Nearest POIs;
- Regions;
- Cities;
- Districts;
- POI categories/subcategories;
- map APIs.

The portal describes business and developer access, with authenticated subscription/access-token use and package limits/approval.

Acarat uses this as a high-priority address/POI adapter candidate.

Potential product use:

- listing address validation;
- standardized district/city/region;
- map positioning;
- nearby schools/services where represented by available POI categories;
- distance-based enrichment;
- input auto-completion.

Acarat must benchmark category coverage and freshness before promising a complete school/hospital/service inventory.

## 8. Balady Urban Maps

Official service evidence:
- Balady Urban Maps is described as a governmental digital map consolidating urban geospatial data across Saudi cities.

Public description includes:

- detailed road networks;
- land-use classifications;
- land categories;
- plot sizes;
- building regulations;
- schools;
- mosques;
- restaurants;
- banks;
- hospitals;
- other services.

Acarat planning implication:

- this is a valuable land/property-intelligence authority surface;
- the public service description does not itself establish a commercial API/data-export grant.

Therefore Acarat defines a BaladyUrbanAdapter contract but does not scrape/redistribute the map as a substitute for formal rights.

Candidate fields:

~~~text
UrbanContextObservation
  source
  geometry_ref
  land_use?
  land_category?
  plot_size?
  road_context?
  building_regulation_ref?
  service_refs[]
  observed_at
  effective_at?
  source_url_or_record
  rights_policy_id
~~~

## 9. Real Estate Indicators

Official REGA indicators are a high-priority market-evidence authority.

Acarat should use formally accessible indicator data for:

- market context;
- benchmark ranges;
- trend;
- transaction counts;
- rental/sales evidence;
- model validation.

Official aggregate indicators do not automatically become exact-property comparables.

Every imported aggregate keeps:

- geography;
- property segment;
- period;
- sample count if provided;
- metric definition;
- source;
- retrieval date;
- methodology revision where available.

## 10. Integration capability status model

Every external adapter exposes:

~~~text
SUPPORTED
NOT_SUPPORTED
AUTH_REQUIRED
PARTNER_AGREEMENT_REQUIRED
SANDBOX_ONLY
TEMPORARILY_UNAVAILABLE
INVALID_REQUEST
REJECTED
UNKNOWN_OUTCOME
~~~

The UI must not flatten these into a generic error.

## 11. Reconciliation rule

Consequential external actions use:

- idempotency key;
- local immutable submission receipt;
- provider request ID;
- status history;
- webhook validation when available;
- bounded polling when required;
- manual reconciliation path;
- UNKNOWN_OUTCOME state.

If Acarat times out after submission, it does not retry blindly and create a duplicate external transaction.

## 12. Government-source freshness

External facts can expire.

Examples:

- agent authority;
- advertisement authority;
- contract state;
- address details;
- urban regulation;
- ownership/service status.

Each fact defines:

- fetched_at;
- effective_at when known;
- expires_at or refresh policy;
- stale-display behavior;
- failure behavior.

## 13. Privacy boundary

Government identity/integration data receives stronger handling than ordinary product metadata.

Requirements:

- data minimization;
- purpose limitation;
- encryption at rest/in transit;
- role-scoped access;
- audit;
- retention schedule;
- deletion/legal-hold semantics;
- no analytics use of raw national identifiers;
- no model training on government identity payloads.

## 14. Browser automation boundary

Browser automation is not a substitute for a government integration.

It may only be considered for:

- internal non-authoritative research;
- user-directed last-mile assistance where legally and contractually permitted;
- testing a public user journey.

It must not:

- bypass authentication;
- circumvent rate limits;
- impersonate API authority;
- automate a government transaction in violation of provider terms;
- become a hidden production dependency.

## 15. Launch blockers

The following are explicit blockers for claims that depend on them:

- REGA platform licensing not completed;
- required Nafath integration not approved;
- REGA technical integration not completed;
- Ejar production integration not approved for automated contract submission;
- imagery/geo provider rights not contracted;
- official/partner data rights not closed;
- privacy/retention requirements unresolved.

Acarat may launch narrower capability subsets only when marketing and UI accurately reflect unavailable integrations.
