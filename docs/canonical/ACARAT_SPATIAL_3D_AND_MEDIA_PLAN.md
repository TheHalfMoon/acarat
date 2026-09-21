# Acarat Spatial, 3D, and Media Plan

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Principle:** spatial context is decision evidence. Rendering, imagery, and 3D assets are provider-bound derivatives with explicit rights and provenance.

## 1. Three spatial layers

Acarat Spatial is divided into three independent layers:

1. **Decision Map** — 2D/3D map, terrain, buildings, POIs, market layers, routes, commute surfaces, polygons, and property context.
2. **Aerial Context** — satellite/aerial imagery from qualified providers under explicit commercial terms.
3. **Property Digital Twin** — floor plans, panoramas, photogrammetry, Gaussian splats, meshes, and virtual-tour derivatives generated from rights-cleared property media.

No one provider is allowed to become the canonical location model.

## 2. Map rendering

Primary candidate:

- MapLibre GL JS for map rendering.

Research pin:
- repository: maplibre/maplibre-gl-js
- observed revision: 5ff9c166b080ab1161f6ccb1e90401474db836c5

Useful current capabilities include raster/satellite layers, terrain, 3D buildings, globe, custom 3D layers, and integration with custom renderers.

Acarat-owned map state should be serializable:

- camera;
- zoom/pitch/bearing;
- selected listing/property;
- active layers;
- filters;
- time window;
- comparison set;
- route/commute destination.

This enables shareable map links and restores a user's exact decision context.

## 3. High-volume geospatial visualization

Candidate:

- deck.gl for large analytical layers.

Research pin:
- repository: visgl/deck.gl
- observed revision: 8da751e185e8d1d7599ea48207962bd9faf939b8

Reference:

- kepler.gl for analytical interaction patterns.
- observed revision: 16ed33961aa046ddcc5587df8ffd3af28597ec37

Candidate Acarat layers:

- asking-price heatmap;
- fair-price heatmap;
- price/m2;
- rent/m2;
- land price/m2;
- supply;
- demand;
- transaction density;
- days on market;
- price changes;
- new inventory;
- verified-listing coverage;
- agent coverage;
- commute surfaces;
- temporal market playback.

## 4. Spatial aggregation

Use uber/h3 only as a derived spatial aggregation/indexing candidate.

Research pin:
- repository: uber/h3
- observed revision: cd62033b337b128ea7c4749f2302143b424187fc

Rules:

- exact property location remains PostGIS geometry;
- H3 is not property identity;
- aggregation resolution is metric-specific;
- public metrics require cohort thresholds;
- pin the Apache-2.0 upstream release/revision selected by implementation governance;
- do not silently substitute unrelated forks with different licenses.

## 5. Satellite and aerial imagery

The product requirement is provider-agnostic:

~~~text
AerialImageryAdapter
  capability_status
  provider
  imagery_type
  requested_geometry
  capture_date?
  retrieved_at
  attribution
  license_policy_id
  cache_policy
  static_snapshot_allowed
  interactive_tiles_allowed
  export_allowed
  asset_ref
~~~

A property page may show:

- top-down context;
- hybrid labels;
- property outline;
- nearby roads;
- adjacent parcels where lawfully sourced;
- scale;
- north;
- imagery date when the provider exposes it.

Every screenshot/export must respect the selected provider's attribution, storage, derivative, and caching terms.

Acarat must not copy a satellite tile into permanent storage merely because it rendered in the browser.

## 6. Provider procurement rule

Map renderer rights are separate from:

- tiles;
- satellite imagery;
- geocoding;
- routing;
- traffic;
- elevation;
- parcel data;
- urban regulation data.

Each provider receives its own source/rights record.

A free development endpoint is not automatically a production SLA or commercial grant.

## 7. Saudi address and POI integration

National Address is the preferred official adapter candidate for supported Saudi address/geocoding/POI capabilities.

Conceptual capabilities:

- validate address;
- geocode;
- reverse geocode;
- resolve region/city/district;
- search POIs;
- nearest POIs.

Exact commercial/production access terms are implementation gates.

## 8. Urban and land context

Balady/municipal sources are research candidates for:

- roads;
- land-use classification;
- plot information;
- building regulations;
- schools;
- mosques;
- hospitals;
- retail/services.

Acarat may display a source-backed urban constraint only when the source grants suitable access and the data is fresh enough for the claim.

Map-derived inference and official regulation are visually distinct.

## 9. Property footprint and parcel context

Acarat should support:

- property centroid;
- building footprint;
- unit point;
- parcel polygon where available;
- entrance point;
- parking/garage point when verified;
- source geometry precision;
- geometry provenance.

Low-accuracy coordinates must not be drawn as a false precise footprint.

## 10. Commute intelligence

Users can save personal destinations such as:

- Work;
- School;
- Family;
- University;
- Hospital;
- custom place.

The search engine can evaluate:

- drive time;
- walking time;
- transit when a qualified provider exists;
- distance;
- multi-destination weighted commute.

Acarat stores a normalized destination reference and routing receipt, not the user's free-text query alone.

Example:

> Two-bedroom apartment under SAR 45,000, within 12 minutes of my work and 10 minutes of my child's school.

A match explanation shows the computed travel times.

## 11. Isochrones

The map can render travel-time polygons:

- 10 min;
- 15 min;
- 20 min;
- 30 min.

Isochrone provider, timestamp, mode, and assumptions must be recorded.

Routing results expire according to provider and traffic semantics.

## 12. Property digital twin maturity levels

### Level 0 — Standard media

- photos;
- video;
- verified floor plan if supplied.

### Level 1 — Panorama tour

- linked 360 panoramas;
- room hotspots;
- floor-plan navigation.

### Level 2 — Structured 3D

- camera poses;
- sparse/dense reconstruction;
- mesh/point cloud;
- floor-plan alignment where possible.

### Level 3 — Neural representation

- Gaussian splat or another qualified representation;
- performant web viewer;
- optional generated walkthrough path.

A property does not need Level 3 to be a high-quality listing.

## 13. Reconstruction candidates

### Nerfstudio

- repository: nerfstudio-project/nerfstudio
- observed research revision: 50e0e3c70c775e89333256213363badbf074f29d
- observed root license: Apache-2.0

Candidate posture: REFERENCE / ISOLATED_WORKER / selective dependency after exact dependency and model review.

### gsplat

- repository: nerfstudio-project/gsplat
- observed research revision: 512d366b67073d77ca099ede742683c165dfc23b
- observed posture: Apache-2.0 project candidate

Candidate posture: REFERENCE / DEPENDENCY_CANDIDATE after exact transitive review.

### COLMAP

- repository: colmap/colmap
- observed research revision: 7019dcc195c3db1946740fb6b85bdbe854741f5f

Candidate posture: photogrammetry/SfM reference or worker dependency after exact LICENSE/dependency qualification.

### OpenDroneMap

- repository: OpenDroneMap/ODM
- observed research revision: 77439b1f45ceb4775b826f900916c64f03736331

Candidate posture: aerial/photogrammetry research reference. Drone capture and imagery rights remain separate operational/legal questions.

## 14. Explicit Gaussian-splatting license guard

The original graphdeco-inria Gaussian Splatting implementation is not a default production donor because its published license posture includes non-commercial restrictions.

Acarat must not import a restrictive implementation into a commercial product merely because the algorithm is academically published.

Prefer permissive implementations that survive exact dependency, patent, asset, and model-rights review.

## 15. Visual feature matching candidates

LightGlue-class matching can be evaluated for reconstruction pipelines, but the selected pipeline must exclude or separately qualify any restrictive pretrained component such as a model with non-commercial terms.

Code license and model-weight license are separate gates.

## 16. Media ingestion pipeline

Every upload passes:

1. identity;
2. content type verification;
3. malware/file safety scan;
4. metadata extraction;
5. EXIF handling;
6. privacy detection;
7. quality analysis;
8. duplicate/perceptual hash;
9. transform generation;
10. evidence/provenance binding.

## 17. Privacy transformations

Potentially sensitive visual content includes:

- faces;
- license plates;
- identity documents;
- private correspondence;
- family photographs;
- screens;
- mirrors exposing people;
- geolocation metadata beyond what the product needs.

Acarat supports review/redaction.

Original evidentiary media must not be destructively replaced by the redacted public derivative.

## 18. AI-enhanced media

AI may assist:

- exposure correction;
- denoise;
- white balance;
- perspective correction;
- panorama stitching;
- floor-plan cleanup.

AI may not silently:

- add furniture;
- remove structural damage;
- change a view;
- widen a room;
- alter windows/doors;
- fabricate landscaping;
- hide defects.

Materially generated/staged imagery must be labeled.

## 19. Floor plans

Floor plans have provenance classes:

- VERIFIED_PROVIDED;
- MEASURED_CAPTURE;
- RECONSTRUCTED;
- APPROXIMATE;
- AI_GENERATED_DRAFT.

An approximate or reconstructed floor plan cannot be displayed as an official plan.

## 20. God’s Eye View research

Source:

- repository: bilawalsidhu/gods-eye-view
- observed revision: 0dbde1e36c0177b7664b47702d77ba50f11ddadc
- root code license observed: MIT
- third-party data/assets: separate rights documented upstream

Adopt/reimplement patterns:

- real-time layer architecture;
- entity selection;
- camera state;
- shareable scene state;
- voice-to-map tools;
- contextual side panel;
- smooth global-to-local navigation.

Reject:

- military/spy visual language as the Acarat product identity;
- third-party restricted datasets without explicit rights;
- dependencies whose commercial terms do not fit Acarat.

## 21. 3D customer experience

Property page spatial modes:

- Photos;
- Floor plan;
- 360;
- 3D Tour;
- Map;
- Satellite;
- Neighborhood.

Comparison mode can synchronize two or more properties by:

- top-down context;
- commute destinations;
- local market layer;
- property scale;
- nearby POIs.

## 22. Agent 3D tools

Agent Terminal can expose:

- media completeness;
- missing room warnings;
- floor-plan status;
- 360/3D processing status;
- privacy-review status;
- 3D engagement analytics;
- view-to-contact conversion for users who entered the tour.

## 23. Derived-asset receipts

Every 3D/derived artifact binds:

- source media IDs;
- source digests;
- pipeline revision;
- model IDs;
- model licenses;
- parameters;
- creation timestamp;
- worker environment;
- output digest;
- quality metrics;
- privacy status.

## 24. Performance

Map/3D UX should progressively enhance.

Requirements:

- usable list fallback;
- low-bandwidth mode;
- delayed heavy 3D loading;
- mobile thermal/memory budget;
- WebGL/WebGPU compatibility strategy;
- accessibility alternative for map-only facts;
- no SEO dependency on client-side map rendering.

## 25. Initial implementation order

1. PostGIS property/location model;
2. MapLibre 2D map/list parity;
3. source-backed POIs;
4. satellite/aerial adapter contract;
5. terrain/3D buildings;
6. H3 analytical layers;
7. commute/isochrone adapter;
8. panorama/floor-plan media;
9. reconstruction benchmark;
10. permissive 3D digital-twin pipeline if proven;
11. temporal/spatial market playback.
