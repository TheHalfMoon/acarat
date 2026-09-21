# Acarat Consumer Search, Lists, Alerts, and Compare Plan

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Goal:** make property discovery conversational, explainable, spatial, persistent, and action-oriented.

## 1. Search surfaces

Acarat supports the same canonical search intent through:

- search bar;
- conversational search;
- voice;
- map drawing;
- filters;
- saved-search editing;
- customer-agent shared requirement;
- direct property comparison refinement.

All surfaces compile to one typed SearchIntent.

## 2. SearchIntent

Conceptual contract:

~~~text
SearchIntent
  transaction_kind
  property_types[]
  city?
  districts[]
  polygons[]
  budget
  rent_period?
  bedrooms?
  bathrooms?
  min_area?
  max_area?
  land_area?
  furnished?
  parking?
  elevator?
  property_age?
  floor_preferences?
  amenities[]
  exclusions[]
  destinations[]
  commute_constraints[]
  nearby_constraints[]
  price_value_preference?
  sort_intent?
  hard_constraints[]
  soft_preferences[]
  relaxed_constraints[]
  source_language
  original_utterance
  parser_version
~~~

The user can inspect and edit interpreted constraints.

## 3. Arabic-first conversational understanding

Search evaluation must include:

- Modern Standard Arabic;
- Saudi conversational Arabic;
- English;
- Arabic/English code-switching;
- Arabic numerals and Western numerals;
- colloquial money expressions;
- annual/monthly rent expressions;
- abbreviations;
- misspellings;
- voice transcription errors.

Examples:

- أبي شقة غرفتين بحي النرجس تحت ٤٠ ألف.
- دور لي ارض 500 متر شمال الرياض وسعر المتر ما يتجاوز 2500.
- شقة قريبة من وزارة التعليم، 15 دقيقة بالكثير.
- furnished studio near KAFD under 55k.
- أبي بيت قريب من دوام زوجتي ومدرسة العيال.

Search must not require exact portal vocabulary.

## 4. Deterministic execution

The LLM/parser may extract intent.

The search engine performs:

- exact filters;
- PostGIS predicates;
- travel-time predicates;
- POI predicates;
- text retrieval;
- value-range predicates;
- structured ranking.

If a hard constraint has zero results, Acarat does not silently relax it.

The product may propose:

> No exact matches. I can show 8 properties if annual rent is raised from SAR 40k to SAR 43k.

The user chooses whether to relax.

## 5. Search ranking

Candidate ranking factors:

- hard constraint satisfaction;
- structured relevance;
- location fit;
- commute fit;
- POI fit;
- budget fit;
- space/room fit;
- verified status;
- listing freshness;
- property/listing completeness;
- price-value fit;
- user soft preferences;
- availability confidence;
- duplicate/fraud suppression.

The ranking receipt stores the feature/reason set.

No paid subscription changes organic ranking.

## 6. Result explanation

Every result can answer:

- Why did this match?
- Which criteria are exact?
- Which are soft?
- What is missing?
- What is the price position?
- How far/long to my saved destinations?

Example:

> 94% match  
> 2 bedrooms ✓  
> SAR 38,000/year ✓  
> 11-minute drive to work ✓  
> Primary school 420 m ✓  
> Parking ✓  
> Rent is inside the Acarat fair range ✓  
> Building age is unknown

## 7. Search refinement

Conversation changes structured state.

Example:

User:
> Two bedrooms under 40k in Al Narjis.

Then:
> Closer to KAFD.

Then:
> I can go to 45k if it has parking.

The UI shows the current constraint chips after every turn.

Users can remove a condition manually.

## 8. Map search

Supported patterns:

- search this map;
- draw polygon;
- select neighborhood;
- radius around a place;
- commute-time area;
- multiple destinations;
- exclude area;
- land-only mode.

Map/list parity is mandatory: every map result is accessible in a list.

## 9. Saved places

A user can store private destinations:

- Home;
- Work;
- School;
- Family;
- custom label.

Saved destinations are private and must not appear in public analytics or agent views without explicit sharing.

## 10. Lists

List types:

- Favorites;
- custom list;
- shortlist;
- investment watchlist;
- land watchlist;
- shared household list;
- agent-shared shortlist.

List item metadata can include:

- user note;
- personal rating;
- tags;
- status;
- added date;
- snapshot of asking price when saved;
- current price;
- price change;
- current availability.

## 11. Collaborative lists

A shared list can support:

- invite members;
- comments;
- reactions;
- private note vs shared note;
- compare selected items;
- poll/favorite;
- change history.

Collaboration permissions are explicit.

An agent cannot automatically see a private household list.

## 12. Saved searches

A saved search stores:

- normalized SearchIntent;
- original phrase;
- map geometry;
- destinations;
- alert policy;
- created time;
- last evaluated;
- result count;
- new-result count;
- owner.

The user can save a conversational search in one action.

## 13. Alert rules

Alerts can trigger on:

- new matching listing;
- asking price below threshold;
- price drop;
- fair-price position enters a chosen range;
- listing becomes verified;
- listing returns to market;
- new land listing in polygon;
- new property within commute limit;
- saved-list item price/status change;
- market range changes materially;
- new comparable evidence changes an Acarat valuation;
- agent replies;
- viewing status changes;
- offer/deal/contract update.

## 14. Example alert

> Notify me when a two-bedroom apartment in Al Yasmin or Al Narjis appears at SAR 40,000/year or less, with parking and within 20 minutes of KAFD.

The saved rule is stored as structured predicates plus original text.

## 15. Notification center

In-app notification center is canonical.

Categories:

- Search Alerts;
- Price Changes;
- Saved Properties;
- Messages;
- Viewings;
- Offers;
- Deals;
- Contracts;
- Reviews;
- Account/Trust.

Channels can include:

- in-app;
- push;
- email;
- WhatsApp;
- SMS.

Channel availability depends on consent, provider policy, cost, and product configuration.

A failed external delivery does not delete the in-app notification.

## 16. Notification preferences

Users control:

- immediate;
- daily digest;
- weekly digest;
- muted;
- quiet hours;
- channel;
- category;
- saved-search-specific preferences.

Deduplication prevents notification storms.

## 17. Comparison

Users can compare multiple properties.

Comparison dimensions:

- asking price;
- Acarat fair range;
- ask premium/discount;
- price/m2;
- property size;
- bedrooms/bathrooms;
- age;
- floor;
- parking/elevator;
- furnishing;
- amenities;
- listing freshness;
- verification;
- comparable evidence count;
- neighborhood trend;
- commute to each saved destination;
- nearby schools/services;
- map context;
- satellite context;
- floor plan;
- 360/3D availability;
- missing facts.

## 18. Compare explanations

Acarat can summarize structured comparison facts.

Example:

> Property A is SAR 7,000 cheaper per year and has the shortest commute. Property B has 18 m2 more space and stronger parking evidence. Property C is the only one priced below its current Acarat fair center.

No hidden overall winner is required.

## 19. Land compare

Land comparison has dedicated dimensions:

- total price;
- area;
- price/m2;
- Acarat land range;
- local transaction density;
- frontage;
- road width;
- corner status;
- number of street fronts;
- orientation;
- land use;
- building constraints where official;
- utilities/service context;
- satellite/aerial context;
- nearby development;
- liquidity/trend;
- confidence.

## 20. Property history

Where lawful and reliable, users can see:

- listing first seen;
- price changes;
- previous Acarat listing campaigns;
- availability changes;
- verification history;
- fair-range history;
- market context changes.

A historical listing event is not automatically a completed transaction.

## 21. Ask Acarat

On any property:

- Is this expensive for the area?
- Why is it more expensive than the other one?
- What is the local range?
- Show me similar properties.
- How far is it from my work?
- What is missing from this listing?
- What changed in the price?
- What should I verify before viewing?
- Compare this with my saved shortlist.

Answers must cite Acarat evidence objects and current property facts.

## 22. Voice

Voice flow:

1. audio capture;
2. VAD;
3. ASR;
4. transcript shown/correctable;
5. intent extraction;
6. structured constraint preview;
7. deterministic search;
8. spoken or visual explanation.

Himsat research informs the ASR/model-router architecture.

Research reference:
- TheHalfMoon/Himsat
- observed revision: 8b6c619750646c454fa754671c9eb3d34114b28c

Arabic/code-switch evaluation is mandatory before production voice claims.

## 23. Recommendation boundary

Acarat can recommend based on:

- user-declared property needs;
- price;
- geography;
- commute;
- property features;
- saved behavior;
- quality/value evidence.

The system must not infer or use sensitive personal characteristics for discriminatory housing steering.

## 24. Privacy

Private search intent can reveal life patterns.

Protect:

- saved destinations;
- household collaboration;
- private notes;
- detailed search history;
- conversation;
- financial preferences beyond what is required.

Agent access to a customer's requirements must be explicit and scoped to the relationship.

## 25. Search evaluation

Held-out corpus should measure:

- constraint extraction precision/recall;
- hard-constraint preservation;
- Arabic dialect performance;
- code-switch performance;
- geospatial correctness;
- commute correctness;
- numerical parsing;
- zero-result behavior;
- relaxation safety;
- ranking relevance;
- explanation fidelity;
- latency.

Every failure sample is retained for regression testing.

## 26. Initial implementation order

1. typed SearchIntent;
2. structured/filter search;
3. PostGIS map/list parity;
4. saved lists;
5. saved searches;
6. in-app notification center;
7. alert matcher;
8. compare;
9. conversational parser;
10. commute search;
11. Ask Acarat grounded property Q&A;
12. voice;
13. collaborative lists;
14. advanced recommendation experiments.
