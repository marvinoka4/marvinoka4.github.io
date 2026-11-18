---
title: vicinia
slug: vicinia
tagline: Neighbours in Lagos share solar and generator power during grid outages, and every transfer is settled fairly.
status: Open source
category: Energy and climate
stack:
  - Python
  - pvlib
  - pandas
  - NumPy
  - pytest
  - Hypothesis
role: Solo
year: 2026
date: 2026-10-29 21:00:00 +0100
cover: /assets/vicinia/cover.svg
cover_alt: Abstract illustration of a row of houses linked by power lines under a bright sun.
repo_visibility: public
public_repo_url: https://github.com/marvinoka4/vicinia
access_url: https://github.com/marvinoka4/vicinia
---

## What it is

vicinia simulates energy sharing between neighbours on Nigerian estates. It was built for HACK4EARTH 2.0, in the Resilient track.

When the grid goes down, homes with solar panels and batteries share their spare power with neighbours, critical needs first. Every transfer is recorded on a ledger that cannot be quietly edited.

## What it does

- Models a neighbourhood of 50 homes over a full year, in 15-minute steps. Homes have solar and batteries, batteries only, grid only, or a medical device that must stay on.
- Models grid supply using the regulator's (NERC) supply-hour bands, load shedding and multi-day blackouts.
- Compares three ways to run the neighbourhood: every home for itself, first come first served, and critical needs first.
- Records every transfer with its price in kobo, so the daily accounts balance to the last kobo.
- Runs pressure tests: a 72-hour blackout, a cloudy harmattan week, the biggest solar home dropping out, half the line capacity, and a communications failure.

## How it works

Solar output comes from standard solar models for Lagos, Abuja and Kano, with random cloud, rainy-season overcast and harmattan dust.

Every 15 minutes, spare solar goes first to neighbours' critical loads, such as lights, fans, fridges, phone charging and medical devices. Batteries keep a reserve for their own home's critical needs and share what is above it. Generators run only when nothing else can cover a home.

Each ledger entry is linked to the one before it by a SHA-256 fingerprint. Changing any past entry breaks the chain, and the check catches it. Automated tests on many randomly generated neighbourhoods confirm that every unit of energy is accounted for, line limits are respected and the ledger matches the real flows.

## Results

Lagos, 50 homes, one year. All inputs are synthetic, so these are model results, not field measurements.

- Critical power during outages rose from 68.4% to 98.1%.
- The worst-off household went from 0% to 93.8% of its critical needs covered.
- Generator fuel fell from 25,684 to 18,053 litres a year, about 30% less. That avoids about 17 tonnes of CO2 a year.
- No household ended up worse off than going it alone.

![Summary of the vicinia report: critical coverage 98.1%, worst-off household 93.8%, 7,631 litres of fuel avoided, and a verified ledger.](/assets/vicinia/report.png)

![Bar chart of critical-load coverage during outages: 68.4% when every home is on its own, 76.2% first come first served, 98.1% critical-first.](/assets/vicinia/coverage.png)

![Line chart of each household's critical coverage, worst to best. With critical-first sharing every home stays above 90%, while without sharing about 13 homes get none.](/assets/vicinia/households.png)

## Who it is for

- Solar installers and mini-grid developers in Nigeria and West Africa.
- Estate managers and residents' associations planning shared power.
- Energy policy researchers, NGOs and funders.

## What you get with access

- The full source code on GitHub, free to use under the Apache 2.0 licence.
- One command that reproduces every number and chart, in under ten minutes.
- A self-contained report you can open in any browser.
