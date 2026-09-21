# Acarat Mobile App Plan

**Status:** CANONICAL_PLANNING_CANDIDATE  
**Product:** one role-aware Acarat mobile application for iOS and Android.

## 1. Product strategy

Acarat mobile is not a reduced copy of the website.

Mobile is the primary surface for:

- instant property alerts;
- location-aware discovery;
- voice search;
- property visits;
- agent/customer messaging;
- viewing coordination;
- camera/media capture;
- task work;
- deal/contract notifications.

The public web remains primary for SEO, broad discovery, shareable pages, deep analytics, and desktop Agent Terminal work.

## 2. Technology direction

Candidate stack:

- React Native + Expo;
- TypeScript shared with web contracts;
- Expo Router or equivalent route layer after benchmark/qualification;
- MapLibre Native-compatible path for native map surfaces;
- native secure storage;
- platform push notification adapters;
- camera/media APIs;
- deep/universal links;
- local SQLite/cache only for bounded offline state, not independent business truth.

Use an Expo custom development client/native build when required native modules cannot run inside a generic managed shell.

Flutter remains a research alternative, but the default candidate is React Native because Acarat already uses TypeScript contracts/design tokens and the team benefits from one presentation language.

## 3. One app, two workspaces

The same authenticated app can expose:

### Customer workspace

- Home/discovery;
- map/list;
- conversational/voice search;
- saved searches;
- notifications;
- lists;
- compare;
- property page;
- 360/3D;
- saved places;
- messages;
- viewing requests;
- offers/deals;
- contracts;
- account/privacy.

### Agent workspace

Only when agent authority and membership permit:

- Today;
- leads;
- customer 360;
- tasks;
- viewings;
- conversations;
- listings;
- listing analytics;
- matches;
- offers/deals;
- contracts/renewals;
- market insights;
- camera/media capture;
- profile;
- team surfaces where authorized.

Workspace switching never changes server-side authorization.

## 4. Customer mobile home

Candidate cards:

- Continue your search;
- New matches;
- Price drops;
- Saved-list updates;
- Nearby properties;
- Upcoming viewing;
- Agent reply;
- Deal/contract status;
- Market change in watched neighborhood.

The home is personalized from explicit product state, not opaque demographic inference.

## 5. Native search and voice

Voice/search flow:

1. tap microphone;
2. local/qualified VAD;
3. ASR;
4. show transcript;
5. compile SearchIntent;
6. show interpreted constraints;
7. execute;
8. render map/list;
9. allow conversational refinement.

User correction is always available before consequential actions.

## 6. Map experience

Mobile map requirements:

- smooth map/list switching;
- clustering;
- selected property card;
- draw/search area where usable;
- nearby/POI layers;
- commute overlay;
- market heat layer;
- 3D building/terrain mode when device capability supports it;
- offline-safe graceful failure.

Do not download unrestricted tile regions unless provider terms explicitly allow it.

## 7. Push notifications

Push is a delivery channel for canonical Acarat notifications.

Push payload carries:

- notification ID;
- category;
- entity reference;
- deep-link route;
- minimal non-sensitive preview.

Sensitive deal/contract information should require app authentication before display.

Push deduplication keys back to canonical notification ID.

## 8. Deep links

Supported deep-link concepts:

- property;
- listing;
- saved search;
- notification;
- conversation;
- viewing;
- offer;
- deal;
- contract;
- task;
- customer for authorized agents.

Unknown/unauthorized links fail safely.

## 9. Property visit mode

During an in-person viewing, the customer can:

- open property passport;
- see checklist;
- add private notes;
- capture user photos if allowed;
- rate aspects privately;
- compare with shortlist;
- ask grounded questions;
- confirm viewing outcome.

Agent can:

- check in/out where policy permits;
- capture notes;
- complete viewing outcome;
- create next task;
- propose follow-up.

Location access is optional and purpose-limited.

## 10. Agent media capture

Agent mobile is the best source for listing capture.

Capture workflow can guide:

- required rooms;
- photo orientation;
- blur;
- exposure;
- duplicates;
- missing spaces;
- 360 sequence;
- floor-plan upload;
- document separation;
- privacy review.

Media uploads are resumable and bind to a listing draft.

## 11. Offline behavior

Offline-safe reads:

- saved lists;
- recently viewed;
- upcoming viewings;
- selected customer/task summaries for agents;
- draft notes;
- media upload queue.

Offline writes are classified.

Safe-to-queue examples:

- private note;
- local draft;
- media upload.

Never blindly queue and replay:

- offer acceptance;
- price change;
- listing publish;
- contract submission;
- agent assignment;
- authority change.

Consequential commands require fresh server preconditions.

## 12. Secure storage

Store only what is needed.

Candidate secure local data:

- refresh/session secrets;
- biometric unlock material;
- local encryption key references.

Do not persist raw national-ID data in ordinary app storage.

Remote logout/revocation invalidates sessions.

## 13. Biometrics

Biometric unlock can protect the Agent workspace or sensitive customer/deal areas.

Biometrics unlock local session access; they do not replace server authorization or government authentication.

## 14. Privacy

Mobile permissions are just-in-time:

- location only for map/nearby/commute when needed;
- microphone only for voice;
- camera/photos only for upload/capture;
- notifications only after explaining value.

No background location tracking by default.

## 15. 3D on mobile

Initial strategy:

- native map for core discovery;
- shared hardened 3D property viewer when appropriate;
- progressive loading;
- device capability detection;
- static/video/floor-plan fallback;
- low-power mode.

A 3D feature must never make basic listing facts inaccessible on a low-end device.

## 16. Accessibility

Requirements:

- VoiceOver/TalkBack labels;
- logical focus;
- dynamic text;
- contrast;
- reduced motion;
- non-map list alternatives;
- Arabic screen-reader testing;
- RTL gesture/layout validation.

## 17. Analytics

Mobile events use the same canonical event taxonomy as web with:

- platform;
- app version;
- surface;
- session ID;
- entity context.

Do not create incompatible mobile-only definitions for listing view or contact conversion.

## 18. Release quality

Before mobile production:

- iOS/Android device matrix;
- Arabic/RTL;
- push reliability;
- deep-link security;
- background upload;
- cold/warm start;
- map memory;
- 3D memory/thermal;
- offline/reconnect;
- permission denial;
- biometric failure;
- accessibility;
- crash monitoring;
- privacy disclosure.

## 19. Future tablet mode

Tablet can become an enhanced Agent Terminal for:

- customer meeting;
- map presentation;
- comparison;
- floor plan/3D;
- offer/deal review;
- media capture.

It remains the same domain/API surface.

## 20. Initial implementation order

1. app shell + auth;
2. customer home;
3. search/map;
4. property/list/compare;
5. saved searches + push;
6. conversations/viewings;
7. Agent workspace;
8. task/customer/listing mobile operations;
9. camera/media workflow;
10. voice;
11. deal/contract mobile workflow;
12. advanced 3D.
