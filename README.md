# Implementation of Reinforcement Learning in Chemical Reaction Networks: Application to Phototaxis

This repository contains the official code and data for the paper: **"Implementation of reinforcement learning in chemical reaction networks: application to phototaxis as curiosity-driven exploration"** (Submitted to ALIFE).

## 📌 Overview
This project bridges the gap between abstract Reinforcement Learning (RL) and physically realizable biochemical processes. We formulate algal phototaxis as a Partially Observable Markov Decision Process (POMDP) driven by active exploration (curiosity), and demonstrate how this subjective inference can be computed using modular Chemical Reaction Network ODEs (CRN-ODEs).

## 🚀 Quick Reproducibility for Reviewers
To save time on computationally heavy Neural Network training (Phase 1) and Inverse Reinforcement Learning (Phase 2), we provide a pre-trained checkpoint and a quick-evaluation notebook.

**1. Clone the repository and install dependencies:**
```bash
git clone https://github.com/giveyourselfaTRY/phototaxis-pomdp-crn.git
cd phototaxis-pomdp-crn
pip install -r requirements.txt

I couldn't upload the colab file directly so here is the link to the numerical + CRN simulation part with different scenarios:
[https://colab.research.google.com/drive/1I7OxYxdNzgFryDHiB2El9uksJqijiCkj?usp=sharing
](https://colab.research.google.com/drive/1I7OxYxdNzgFryDHiB2El9uksJqijiCkj?usp=sharing)
