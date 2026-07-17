# Pick Our Night — Booking Button Feature Sketch

A static, self-contained visual mockup exploring how the "book this venue" action
button in [Pick Our Night](https://pickournight.com) should adapt to different kinds
of venues — including places that **don't** take reservations.

## What this is

An interactive design reference. Open `pickournight-booking-mockup.html` in any web
browser (no server, build step, or dependencies required) and use the three pills at
the top to switch between states.

## The three states

| State | When it applies | Primary action |
|-------|-----------------|----------------|
| 🍽️ **Reservable** | Venue has OpenTable / Resy inventory | **Reserve on OpenTable** |
| 🎟️ **Experience** | Ticketed activity (Viator / Tripadvisor / Fever) | **Get Tickets** |
| 🚶 **Walk-in only** | Bars, cafés, parks — no reservations | **"No reservation needed"** + Directions / Call / Menu |

## Design logic

The button is driven by two fields on each venue:

- `booking_type` — one of `opentable`, `experience`, or `walkin`
- `booking_url` — the partner deep-link (empty for walk-in)

The key principle: a place that can't be booked never shows a broken or greyed-out
button. Instead, "no reservations" is reframed as a perk ("walk-in friendly") and the
couple is given the actions they actually need.

### Edge cases handled in the sketch
- Reservable but **booked out tonight** → "See other times" + "spin a walk-in spot instead"
- Reservations **optional** → primary "Reserve", secondary "or just walk in"

## Status

⚠️ **Mockup only.** The buttons are non-functional placeholders. Colors and copy are
stand-ins to be replaced with real branding. This file is a reference for building the
feature, not the feature implementation.
