# Acarat Trust, Safety, Privacy, and AI Authority Plan

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Principle:** Acarat may help users decide and act, but identity, money, contracts, property authority, and outbound actions require explicit deterministic authority.

## 1. Trust domains

Acarat trust is separated into:

- identity trust;
- agent/agency authority;
- listing/advertisement authority;
- property fact provenance;
- transaction authority;
- communication consent;
- review eligibility;
- model/AI trust;
- media authenticity;
- marketplace abuse prevention.

No single "verified" badge should collapse all of these.

## 2. Identity classes

Candidate subject classes:

- CUSTOMER;
- OWNER;
- LANDLORD;
- TENANT;
- BUYER;
- SELLER;
- AGENT;
- AGENCY_STAFF;
- AGENCY_ADMIN;
- DEVELOPER_STAFF;
- PROPERTY_MANAGER;
- ACARAT_STAFF;
- SERVICE_ACCOUNT.

A person can hold multiple roles.

Authentication identity is separate from domain role and external licensing authority.

## 3. Government identity

Where Saudi platform rules require Nafath for advertisers:

- Nafath proves the required authentication/identity interaction;
- Acarat maps the result to an internal opaque subject ID;
- raw government identifiers are minimized;
- national ID is not used as a public URL or profile ID;
- public agent profile displays only permitted verified attributes.

## 4. FAL/agent authority

Agent authority record includes:

- internal agent ID;
- external authority reference;
- status;
- issuing authority;
- effective/expiry dates where available;
- checked time;
- evidence receipt;
- agency relationship when supported;
- public display subset.

If authority becomes stale/expired:

- new regulated actions can fail closed;
- existing records retain historical provenance;
- public status reflects freshness policy.

## 5. Listing authority

Publishing can require:

- authenticated authorized advertiser;
- property/listing relationship;
- advertisement-license evidence where required;
- valid mandatory fields;
- media review;
- duplicate/fraud checks;
- policy compliance.

Listing authority and property ownership are not assumed to be the same fact.

## 6. Property provenance

Every source-backed fact has provenance and freshness.

Potential fact classes:

- official;
- licensed provider;
- agent verified;
- owner provided;
- Acarat observed;
- Acarat calculated;
- model inferred.

Inferred facts cannot overwrite authoritative facts.

## 7. Personal data classification

Suggested classes:

### PUBLIC

- published listing details;
- agent public profile fields;
- public reviews;
- published agency data.

### INTERNAL

- product operations metadata;
- non-sensitive internal IDs;
- aggregate metrics.

### CONFIDENTIAL

- customer search history;
- saved places;
- CRM notes;
- conversations;
- offers;
- contracts;
- financial preferences.

### RESTRICTED

- national/government identifiers;
- authentication secrets;
- identity verification payloads;
- highly sensitive documents;
- payment/escrow tokens;
- security logs containing secrets.

Access controls and retention depend on class.

## 8. Data minimization

Before storing any sensitive field, define:

- purpose;
- lawful/contractual basis;
- owner;
- readers;
- retention;
- deletion behavior;
- export behavior;
- analytics eligibility;
- model-training eligibility.

Default:

- do not store raw government payloads when a verification receipt/reference is sufficient;
- do not duplicate documents into multiple domains;
- do not collect sensitive attributes for ranking/recommendation.

## 9. Saved place privacy

Home/work/school saved places are private location data.

Rules:

- not public;
- not visible to agent unless explicitly shared;
- not included in aggregate demand below privacy threshold;
- not used to infer protected/sensitive characteristics;
- not retained after deletion beyond required backup policy.

## 10. Communication consent

Per channel record:

- user;
- channel;
- purpose/category;
- opt-in/opt-out;
- source;
- timestamp;
- quiet hours;
- legal/policy revision.

An existing customer relationship does not automatically authorize every marketing channel.

Transactional and marketing communication are distinct.

## 11. Agent CRM privacy

Agents see only customers assigned/shared within authorized tenancy.

Agency admins may have broader rights according to role.

Controls:

- object-level authorization;
- field-level restriction for sensitive content;
- access audit;
- export control;
- bulk action safeguards;
- customer merge audit.

Cross-agency data exposure is a critical severity event.

## 12. Review integrity

Review eligibility sources:

- verified completed interaction;
- verified viewing;
- verified deal/contract depending on review type.

Rules:

- no arbitrary anonymous rating;
- agent cannot review self;
- agency cannot manufacture verified customer reviews;
- one interaction/deal has bounded review eligibility;
- moderation preserves evidence;
- disputes/appeals are auditable;
- incentives, if ever offered, cannot depend on review sentiment.

## 13. Listing abuse and fraud

Candidate defenses:

- duplicate property/listing detection;
- duplicate media hashes;
- price anomaly;
- impossible location;
- contact-information policy checks;
- stolen-media detection where technically/legal possible;
- authority mismatch;
- mass-account behavior;
- suspicious rapid relisting;
- external complaint/review;
- manual escalation.

A fraud score is a triage signal, not automatic public accusation.

## 14. Scraping and marketplace extraction

Acarat should defend against:

- bulk personal-data harvesting;
- agent contact harvesting;
- listing database cloning;
- enumeration of private IDs;
- abuse of valuation APIs;
- automated spam inquiries.

Controls:

- rate limits;
- pagination limits;
- opaque IDs;
- authenticated higher-volume APIs;
- bot controls;
- abuse detection;
- contractual API terms.

SEO must remain accessible without exposing private data.

## 15. Media authenticity and privacy

Media processing includes:

- content-type validation;
- malware scan;
- EXIF policy;
- face/license-plate/private-document detection;
- duplicate/perceptual hash;
- edit/provenance receipt;
- public derivative.

AI alteration policy:

- basic photographic correction allowed if non-deceptive;
- generated staging or material editing must be labeled;
- structural/defect removal is prohibited;
- original evidence remains separate.

## 16. Document security

Documents can contain:

- identity;
- title/property evidence;
- contracts;
- bank/financial data;
- signatures.

Controls:

- private object storage;
- signed short-lived URLs;
- malware/file-type scanning;
- role-scoped access;
- watermarking/audit where appropriate;
- document retention;
- no public CDN cache for restricted documents.

## 17. Payment and escrow security

If payment/deposit integrations are added:

- use tokenized provider references;
- do not store raw card data;
- provider webhook signatures;
- ledger/reconciliation;
- idempotency;
- refund/dispute state;
- UNKNOWN_OUTCOME handling.

Acarat does not call a provider-held deposit "Acarat escrow" unless the legal arrangement supports that claim.

## 18. AI authority levels

### L0 — Read-only explanation

- answer questions;
- summarize;
- compare;
- explain metrics;
- explain valuation.

### L1 — Draft/proposal

- draft listing copy;
- draft message;
- propose task;
- propose shortlist;
- propose search relaxation;
- propose price scenario.

### L2 — User-confirmed reversible action

Examples:

- save search;
- create list;
- create task;
- update a non-sensitive note.

Requires explicit user confirmation or an approved narrow preference rule.

### L3 — Consequential domain action

Examples:

- publish listing;
- change price;
- send external message;
- submit offer;
- assign lead;
- submit contract.

Requires deterministic authorization, policy, validation, and receipt. Human confirmation is default unless a separately approved automation rule exists.

### L4 — External regulated/financial action

Examples:

- government contract submission;
- ownership transfer;
- payment/deposit release;
- regulated financing application.

Requires explicit external authority, strong user confirmation, deterministic workflow, reconciliation, and no model-only authority.

## 19. Prompt injection boundary

Untrusted content can include:

- listing description;
- uploaded document;
- customer message;
- webpage/provider text;
- image OCR;
- agent note.

AI system rules:

- content is data, not authority;
- external text cannot grant tools/permissions;
- tool calls are schema-bound;
- allowed tools are context-scoped;
- consequential calls require policy preflight;
- secrets are not put into model-visible context unless absolutely required and supported.

## 20. Grounding

For market/property answers:

- retrieve structured facts;
- bind exact evidence refs;
- calculate numbers deterministically;
- give LLM only authorized facts;
- generate explanation;
- verify cited numeric values against structured result.

If evidence is insufficient:

- say so;
- show missing information;
- abstain from unsupported numeric/factual claims.

## 21. Model data policy

User/customer private data is not automatically training data.

Before any training/evaluation use:

- purpose;
- consent/lawful basis;
- de-identification if appropriate;
- retention;
- dataset governance;
- deletion handling;
- access;
- model memorization risk;
- source rights.

Government identity data is excluded from model training by default.

## 22. Search/recommendation fairness

Recommendations are based on housing needs and property facts.

Prohibited ranking inputs include sensitive/protected personal traits and inferred proxies intended to steer people based on such traits.

Location requests directly made by the user are allowed as search intent, while the system should not infer sensitive identity and use it to select neighborhoods.

## 23. Audit log

Consequential audit events include:

- login/security changes;
- authority verification;
- listing publish/change/unpublish;
- price change;
- lead assignment;
- customer merge;
- outbound message;
- offer revision;
- deal stage;
- contract submission;
- external reconciliation;
- payment/deposit action;
- review moderation;
- privacy export/delete;
- admin access to restricted data.

Audit logs are tamper-resistant and access-controlled.

## 24. Security engineering

Required practices:

- secure coding;
- dependency pinning;
- SBOM;
- secret scanning;
- SAST;
- dependency vulnerability review;
- CodeQL where applicable;
- upload sandboxing;
- SSRF protections;
- SQL injection prevention;
- XSS/CSRF protection;
- CSP;
- webhook verification;
- API abuse protection;
- encryption;
- backup security;
- incident response.

## 25. Threat model categories

At minimum:

- account takeover;
- fake agent/authority;
- fraudulent listing;
- cross-tenant exposure;
- insecure direct object reference;
- payment fraud;
- malicious upload;
- data exfiltration;
- scraping;
- spam/lead abuse;
- review manipulation;
- prompt injection;
- model data leakage;
- government/provider spoofing;
- webhook replay;
- duplicate external transaction;
- insider misuse.

Each implementation phase identifies relevant threats and tests.

## 26. Privacy rights operations

Product should support applicable operations such as:

- access/export;
- correction;
- deletion where legally permitted;
- consent/preferences;
- account closure;
- retention lifecycle.

Backups and external copies require explicit policy; Acarat must not claim deletion from systems it does not control.

## 27. Security evidence gate

A consequential feature cannot be declared complete until required evidence exists, such as:

- authorization tests;
- negative tests;
- replay/idempotency;
- dependency review;
- threat-model update;
- privacy data-flow update;
- audit event tests;
- exact-head CI;
- independent review where high risk.

## 28. Trust UX

The UI should explain trust in plain language.

Examples:

- Government identity verified;
- Agent license verified on date X;
- Advertisement authority verified;
- Address verified;
- Owner/agent provided;
- Acarat calculated;
- AI inferred;
- Last checked X;
- Verification expired;
- Data unavailable.

Do not use green checks for fundamentally different claims without text.
