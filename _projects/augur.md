---
title: Augur
slug: augur
tagline: Does a fast first step at the NFL Combine mean a fast first step on game day? A study that fixed its rules before looking at the answer.
status: Private, available to license
category: Sports analytics
stack:
  - Python
  - Polars
  - NumPy
  - matplotlib
role: Solo
year: 2026
date: 2026-10-16
cover: /assets/augur/cover.svg
cover_alt: Abstract illustration of data points rising along a dashed trend line.
repo_visibility: private
access_url: mailto:info@marvinoka4.com?subject=Access%20to%20Augur
---

## What it is

Augur is a sports science study built for the NFL Big Data Bowl 2027. It asks one question about defensive linemen: does a player's burst out of his stance in the Combine pass-rush drill tell you how quickly he gets off the ball in real games?

Scouts already have the 10-yard split. Augur asks whether the burst adds anything on top of it.

## What it does

- Measures each player's first-step burst from Combine tracking data, after removing what his 10-yard split already explains.
- Measures how quickly he gets off the ball on regular-season pass rushes.
- Tests whether the burst improves predictions of game-day get-off. The baseline it must beat already knows the split, body weight, draft position, whether he went undrafted, and whether he plays on the edge or the interior.
- Gives a plain verdict: supported, not supported or inconclusive.

## How it works

The rules came first. Before any Combine number was compared with any game outcome, I wrote and locked a pre-registration: the question, the data, the players, the test and the rule for the verdict. Every later change is logged with a date, what I had seen at the time and how it could affect the result.

The study uses regular-season tracking data for defensive linemen from the 2023, 2024 and 2025 draft classes. It keeps straight-ahead rushes and sets aside stunts and drops, using a simple rule based on the rusher's own path.

Each draft class takes a turn as the test group. The model learns from the other two classes and predicts the third, so every prediction is made on players it has not seen. A shuffle test sets the bar the burst has to clear, so the result is judged against chance and not against a threshold I picked.

## Results

- 25,278 regular-season rushes from 98 players in the 2023 to 2025 draft classes. 70 players meet the bar to enter the test.
- A pilot on made-up outcomes behaved as it should. Pure noise was rejected. A planted effect was found in all three test groups.
- Built-in checks: repeat builds give identical files, a deliberately meaningless "garbage" measure runs beside the real one, and every data join is counted.
- The test runs once, under the locked rules. The verdict cannot be tuned after the fact.

## Who it is for

- Scouting and player personnel departments deciding how much weight to give Combine drills.
- Sports science and analytics teams who want a template for an honest, pre-registered study.
- Researchers and data journalists covering player evaluation.

## What you get with access

- Read access to the private repository: the analysis code, tests, the pre-registration and the full changelog.
- The study notebook and the scripts behind the figures and checks.
- The NFL tracking data is not included. It comes from the Big Data Bowl under its own terms.
