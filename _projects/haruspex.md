---
title: Haruspex
slug: haruspex
tagline: An AI model that reads a knee MRI and scores twelve common findings, from torn ligaments to fractures.
status: Private, available to license
category: Medical imaging AI
stack:
  - Python
  - PyTorch
  - timm
  - EfficientNet
role: Solo
year: 2026
date: 2026-10-26
cover: /assets/haruspex/cover.svg
cover_alt: Abstract illustration of stacked scan slices with the outline of a knee joint.
repo_visibility: private
access_url: mailto:info@marvinoka4.com?subject=Access%20to%20Haruspex
---

## What it is

Haruspex is an AI model for knee MRI, built for the RSNA Knee Abnormality Detection 2026 challenge. Given one knee scan, it estimates how likely each of twelve findings is:

ACL and MCL injury, medial and lateral meniscus tears, osteoarthritis in three parts of the knee, joint fluid, inflamed joint lining (synovitis), Baker's cyst, bone bruising and fracture.

*Haruspex is a research model. It is not a medical device and is not for diagnosis.*

## What it does

- Reads scans straight from the scanner's own file format.
- Picks the right image series by itself: a side view, a front view and a top view.
- Scores all twelve findings for each scan.
- Handles about 1,300 scans in under 10 minutes on two standard cloud GPUs, with no internet connection.

## How it works

An MRI is a stack of thin image slices, taken from several directions. Haruspex looks at three neighbouring slices at a time. That gives it a sense of depth without the cost of a full 3D model.

The model is told which direction each slice comes from. For each finding, it learns which slices matter most. A meniscus tear and a fracture can therefore draw on different parts of the scan.

Three models of different sizes, some with the top view and some without, are combined with equal weight. During training, front and top views are also shown mirrored, because a mirrored knee is still a real-looking knee. This helps the models cope with new scans.

It is a clean build. It uses only the challenge data and openly licensed general-purpose image weights. No outside MRI data.

## Results

- Macro AUC of 0.919 on the public leaderboard and 0.909 on the private leaderboard. AUC measures how well the model ranks scans with a finding above scans without it. 1.0 is perfect and 0.5 is a coin toss.
- Under 10 minutes for the full test set of about 1,300 scans.
- Each design choice was tested one change at a time, including the top view, image size and model size.

## Who it is for

- Medical imaging researchers and teams building musculoskeletal AI.
- Health tech startups that want a working, documented starting point for knee MRI.
- Educators teaching applied medical computer vision.

## What you get with access

- Read access to the private repository: the code for preparing scans, the model, training and inference, with tests.
- The notebooks used for training, comparisons and the final ensemble.
- No patient data is included. Scans come from the challenge under its own terms.
