---
title: killcheck
slug: killcheck
tagline: Finds the bugs your tests would miss, and checks whether tests written by AI really catch them.
status: Open source
category: Developer tools and AI evaluation
stack:
  - Python
  - pytest
  - coverage.py
role: Solo
year: 2026
date: 2026-09-18
cover: /assets/killcheck/cover.svg
cover_alt: Abstract illustration of a grid of small squares, with a few highlighted squares standing out.
repo_visibility: public
public_repo_url: https://github.com/marvinoka4/killcheck
access_url: https://github.com/marvinoka4/killcheck
---

## What it is

killcheck is a Python tool and a research study, built for the micro1 Frontier Engineering Challenge 2026. It asks a simple question: when an AI agent writes tests, do those tests really catch bugs, or do they just pass?

## What it does

- Plants small, deliberate bugs in your code, one at a time. It flips a comparison, swaps a plus for a minus, changes a number, or turns an error into a silent pass.
- Runs your existing tests against each bug. Any bug the tests miss is a "survivor".
- Turns the survivors into a to-do list of tests worth writing.
- Keeps a new test only if it passes on the real code and fails on the bug it targets. No AI judges the result. The test run's pass or fail is the only evidence.

## How it works

The measuring tool came first. The bug generator and the test runner were frozen before any agent code existed, and the success measure was fixed before any experiment ran. Every change of plan is logged with the numbers that forced it.

Three approaches were compared on the same bugs:

- One prompt asking for tests, with no extra help.
- One test per request, with the same budget, still with no extra help.
- The agent: shown the bug, held to the pass-then-fail check, with one retry.

## Results

- 455 deliberate bugs across 12 widely used Python libraries. Only 53 sat in code the tests run but do not check. Most missed bugs were in code the tests never reach at all.
- On those 53, the agent caught 44 (83%). One prompt caught 9. One test per request caught 2.
- Of the 9 the agent missed, 7 cannot be caught by any test, because the change does not alter what the code does.
- The work is [written up publicly on dev.to](https://dev.to/marvinoka4/69-tests-all-passing-zero-bugs-caught-27k5), and reader reports are credited in the changelog.

## Who it is for

- Engineering teams using AI coding assistants who want to know if the tests are worth keeping.
- QA and test leads looking for gaps in an existing test suite.
- Researchers evaluating AI agents.

## What you get with access

- The full source code on GitHub, free to use under the MIT licence.
- A quickstart that gives you a score for one of your own files in about five minutes.
- The full method, the changelog and the raw results.
