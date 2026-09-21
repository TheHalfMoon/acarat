# Acarat Source Qualification Ledger

**Status:** RESEARCH_LEDGER  
**Rule:** a source pin is research evidence, not automatic implementation admission.

## 1. Adoption policy

Every admitted source must eventually record:

- repository/source;
- exact revision/release;
- public/private disclosure status;
- license;
- NOTICE/attribution;
- target Acarat subsystem;
- capability sought;
- adoption mode;
- transitive dependencies;
- model/data/asset rights;
- security implications;
- privacy implications;
- tests;
- update strategy;
- rollback/exit strategy.

Allowed adoption modes:

- PRIMARY_AUTHORITY;
- REFERENCE;
- DEPENDENCY_CANDIDATE;
- ADAPT;
- COPY_SELECTIVE;
- PROCESS_REFERENCE;
- REJECT;
- RIGHTS_REQUIRED.

Founder permission to use a source does not erase third-party license, asset, model, dataset, trademark, or NOTICE obligations.

## 2. Founder-owned source priorities

| Source | Research pin | Candidate value | Posture |
|---|---|---|---|
| TheHalfMoon/Zyara | a7ef63d7c00151c6977437760d911533255f5e6d | PostGIS/MapLibre marketplace, search, trust/reviews, notifications, Saudi-aware platform patterns | HIGH_PRIORITY_REFERENCE / ADAPT_SELECTIVE |
| TheHalfMoon/Himsat | 8b6c619750646c454fa754671c9eb3d34114b28c | voice pipeline, Arabic/code-switch, ASR/VAD/model routing | HIGH_PRIORITY_REFERENCE |
| TheHalfMoon/Morize | 0c21cf314be701db56724b4df2de806a027ee58f | provenance, temporal facts, conflict/history concepts | REFERENCE / ADAPT_SEMANTICS |
| TheHalfMoon/MedScale | ae0441918296c2d1510a71061249c7e55e65d760 | Graphify/AFFiNE/Grist/Baserow/Superset source qualification, graph/data-workbench patterns | REFERENCE |
| TheHalfMoon/Kodac | 406b335277f2df1e3dedf24cdb45847dff919d44 | Go modular monolith, PostgreSQL-first, observability patterns | REFERENCE |
| TheHalfMoon/Qdrat | e2d288940aab52af881786678b2fc86dfa5c272a | reporting, workflow, workforce/task/dashboard patterns | SELECTIVE_REFERENCE |
| TheHalfMoon/Inercative | ff5bcbc3241d43fbb643d037ccb5967a20213af4 | product graph and AI/tool orchestration research | REFERENCE |
| TheHalfMoon/SpecGrain | 5de7d6499bb0a9e3a191fc0934399cf099d1980a | recursive bounded specifications and evidence | PROCESS_REFERENCE |
| TheHalfMoon/Diffcipline | reverify before implementation admission | Think -> Challenge -> Minimize -> Change -> Prove | PROCESS_REFERENCE |
| TheHalfMoon/Sentrdel | reverify before reuse | security/policy evidence | SECURITY_REFERENCE |
| TheHalfMoon/Tarif | reverify before reuse | deterministic agent authority and receipts | AI_ACTION_REFERENCE |
| TheHalfMoon/Ecra | reverify before reuse | browser/tool execution and receipts | LAST_MILE_AUTOMATION_REFERENCE |
| TheHalfMoon/Signthos | reverify before reuse | document/e-sign workflow patterns | DOCUMENT_REFERENCE |

Private founder-owned repositories may be inspected during authorized planning, but must not be named, disclosed, or copied into this public repository unless separately authorized for public disclosure.

## 3. Mapping and geospatial

| Source | Research pin | Capability | Posture |
|---|---|---|---|
| maplibre/maplibre-gl-js | 5ff9c166b080ab1161f6ccb1e90401474db836c5 | web map renderer, raster/satellite, terrain, 3D buildings, custom layers | DEPENDENCY_CANDIDATE |
| visgl/deck.gl | 8da751e185e8d1d7599ea48207962bd9faf939b8 | large-scale geospatial visualization | DEPENDENCY_CANDIDATE / REFERENCE |
| keplergl/kepler.gl | 16ed33961aa046ddcc5587df8ffd3af28597ec37 | analytical map interaction patterns | REFERENCE |
| uber/h3 | cd62033b337b128ea7c4749f2302143b424187fc | spatial aggregation/indexing | DEPENDENCY_CANDIDATE; pin Apache-2.0 upstream |
| postgis/postgis | exact implementation pin pending | geospatial truth/query | DEPENDENCY_CANDIDATE |
| bilawalsidhu/gods-eye-view | 0dbde1e36c0177b7664b47702d77ba50f11ddadc | map/layer state, entity selection, camera, shareable scenes, voice-map UX | REFERENCE / SELECTIVE_ADAPT |

God's Eye source code was observed under MIT at research time, but upstream explicitly separates third-party data and asset rights. Acarat must not import third-party data/assets through the code license.

## 4. 3D and photogrammetry

| Source | Research pin | Capability | Posture |
|---|---|---|---|
| nerfstudio-project/nerfstudio | 50e0e3c70c775e89333256213363badbf074f29d | NeRF/3D research and processing framework | WORKER_CANDIDATE; root Apache-2.0 observed |
| nerfstudio-project/gsplat | 512d366b67073d77ca099ede742683c165dfc23b | permissive Gaussian-splatting implementation candidate | DEPENDENCY/WORKER_CANDIDATE; exact dependency review |
| colmap/colmap | 7019dcc195c3db1946740fb6b85bdbe854741f5f | structure-from-motion/photogrammetry | WORKER_REFERENCE / DEPENDENCY_CANDIDATE |
| OpenDroneMap/ODM | 77439b1f45ceb4775b826f900916c64f03736331 | aerial photogrammetry patterns | REFERENCE |

Explicit reject-by-default:

- graphdeco-inria/gaussian-splatting direct production reuse while its relevant published implementation terms remain non-commercial/research constrained.

Algorithm publication does not imply production-code license compatibility.

## 5. Zillow research

| Source | Research pin | Capability | Posture |
|---|---|---|---|
| zillow/quantile-forest | 731dc5c8e5c20e51e6fbc3e2fcd7ef1065a1efc4 | quantile regression forest and interval estimation techniques | REFERENCE / DEPENDENCY_CANDIDATE after license pin |
| zillow/compliant-real-estate-chatbot | 1a2ccd9112184a9a07940e00ba232e69b5c97058 | real-estate domain LLM evaluation and safety architecture | REFERENCE |
| zillow/fair-housing-guardrail | exact pin pending | deterministic/classifier guardrail architecture | REFERENCE |
| zillow/zind | exact pin pending | 360/floor-plan/3D research | CODE_REFERENCE_ONLY by default |

ZInD warning:

- code is separately licensed;
- the dataset's published terms are not a general commercial-product grant;
- do not train/ship Acarat product features on the dataset without separate rights.

## 6. Notifications and communication

| Source | Research pin | Capability | Posture |
|---|---|---|---|
| novuhq/novu | 36c5c0cefa400e8edc6ec8b18ac4574288eabd03 | notification workflows, preferences, digests | REFERENCE / DEPENDENCY_CANDIDATE after license/dependency review |
| chatwoot/chatwoot | f7f7754511df38c33455d2a968f7541e82d15e5b | omnichannel inbox, assignment, notes, reports | REFERENCE / SELECTIVE_ADAPT |
| WhatsApp Business | external provider contract | official messaging channel | INTEGRATION; provider terms/cost/consent required |
| email/SMS/push providers | provider-specific | delivery channels | INTEGRATION |

Acarat's customer/deal/property model remains authoritative even when a communication platform is adopted.

## 7. Analytics

| Source | Research pin | Capability | Posture |
|---|---|---|---|
| ClickHouse/ClickHouse | de0734db65099d6544699a36dbed5096b63ae8bf | columnar analytics at scale | SCALE_GATE_CANDIDATE |
| apache/superset | c9fd9bf94f45163afd24f39f5ed9eec23a999150 | internal BI/semantic dashboard patterns | INTERNAL_REFERENCE / DEPENDENCY_CANDIDATE |
| metabase/metabase | exact pin pending | operational BI patterns | REFERENCE; exact license/embedding review |
| PostHog/posthog | f3a796954ee43e9e0029ae123833150e2f274965 | product analytics architecture patterns | REFERENCE_ONLY by default; license/path review required |
| OpenTelemetry | exact pin pending | observability contracts/collector | DEPENDENCY_CANDIDATE |
| Prometheus | exact pin pending | operational metrics | DEPENDENCY_CANDIDATE |
| Grafana | exact pin pending | operations dashboards | DEPENDENCY/REFERENCE subject to license review |

Acarat-owned metric semantics must not depend on one BI/product-analytics vendor.

## 8. Search

| Source | Capability | Posture |
|---|---|---|
| PostgreSQL FTS/trigram | launch search | PRIMARY |
| PostGIS | geo filtering | PRIMARY |
| OpenSearch | large-scale search/ranking | BENCHMARK_GATE |
| pgvector | semantic retrieval | BENCHMARK_GATE |
| model rerankers | candidate ranking | BENCHMARK_GATE; model rights separate |

The search system must prove improvement on held-out Saudi Arabic/English queries before a larger search stack is admitted.

## 9. Graph and knowledge

Candidate reference concepts:

- Graphify-Labs/graphify — explained edges, path/query/explain, local graph patterns.
- MedScale source ledger recorded Graphify as Apache-2.0 at its reviewed pin and suitable for reference/adaptation subject to exact path review.

Acarat does not start with a separate graph database.

Initial graph relationships are relational tables/projections in PostgreSQL unless query evidence proves otherwise.

Potential graph:

- property -> listing;
- property -> neighborhood;
- property -> POI;
- property -> market observation;
- agent -> agency;
- agent -> listing;
- customer -> requirement;
- customer -> viewing;
- viewing -> listing;
- offer -> listing;
- deal -> parties;
- contract -> deal;
- review -> verified interaction/deal.

## 10. Data-workbench references

From founder source research:

- Grist Community — relational spreadsheet/data-workbench patterns.
- Baserow OSE — field/view/API/database-builder patterns.
- AFFiNE — block/canvas/table UX research with path-sensitive mixed licensing.
- NocoDB — feature research only by default under observed restrictive current license posture.
- Teable — core app reference only unless exact permissive packages are separately qualified.

Agent Terminal should not become a fork of any of them.

## 11. Saudi official authorities and provider boundaries

Priority authorities/reference systems:

- Real Estate General Authority (REGA);
- Real Estate Indicators;
- Ejar;
- Real Estate Registry (RER);
- National Address / SPL;
- Balady / municipal urban-map services;
- Nafath through formally supported integration channels.

These are not code donors.

For each integration Acarat must capture:

- official capability;
- onboarding/partner process;
- authentication;
- data rights;
- transaction authority;
- rate limits;
- residency/retention conditions;
- test environment;
- error/reconciliation semantics;
- production approval.

No browser automation is allowed to impersonate an official API contract.

## 12. Async/workflow references

Candidates:

- PostgreSQL transactional outbox — baseline.
- riverqueue/river — Go/PostgreSQL jobs candidate after exact MPL/dependency review.
- ThreeDotsLabs/watermill — event-routing patterns.
- Redis queue systems — optional, not canonical.

Do not admit Temporal/Kafka simply for architectural fashion.

## 13. Voice

Founder source:

- TheHalfMoon/Himsat at 8b6c619750646c454fa754671c9eb3d34114b28c.

Relevant candidate engines from existing founder research:

- whisper.cpp;
- sherpa-onnx;
- NeMo-Speech.cpp;
- VAD/conditioning components.

Every selected model/weight/runtime is independently licensed and benchmarked for Saudi Arabic/code-switch, latency, resource use, and privacy.

## 14. Security and AI authority

Useful founder/reference sources:

- TheHalfMoon/Sentrdel;
- TheHalfMoon/Tarif;
- TheHalfMoon/Ascout;
- Tencent AI-Infra-Guard;
- OWASP GenAI Security Project.

Acarat-specific authority remains stricter than generic agent behavior.

## 15. Source admission gate

Before code transfer or dependency admission:

1. live source revision reverified;
2. exact path/release pinned;
3. license/NOTICE checked;
4. transitive dependencies reviewed;
5. models/data/assets independently reviewed;
6. security implications reviewed;
7. privacy/data-flow reviewed;
8. native/simple alternative compared;
9. behavior tests defined;
10. upgrade/exit strategy recorded;
11. owning SpecGrain authorizes adoption;
12. provenance record committed.

## 16. Source transfer record

~~~text
SourceTransfer
  source_repository
  source_revision
  source_path
  source_license
  source_notice
  founder_permission_reference?
  target_path
  adoption_mode
  modifications
  transitive_dependencies
  data_model_asset_rights
  security_review
  privacy_review
  behavior_tests
  provenance_record
  update_strategy
  rollback_strategy
  exit_strategy
~~~

No permission statement should be interpreted as permission to ignore a third party's rights.
