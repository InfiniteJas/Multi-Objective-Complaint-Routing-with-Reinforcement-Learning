# Multi-Objective Complaint Routing with Reinforcement Learning

An experimental decision-making system that routes citizen service requests using reinforcement learning instead of traditional classification.

The project explores a real engineering question:

> What if accuracy is the wrong metric for public service automation?

Traditional ML optimizes prediction correctness.  
Public systems need to optimize outcomes.

This repository demonstrates why those are not the same thing.

---

## Problem

Large public service platforms receive thousands of requests per week.  
Some are routine. Others are urgent.

A typical ML classifier treats every request independently:

```
Input → Predict department → Done
```

But real systems operate over time:

- departments become overloaded
- urgent cases must jump the queue
- fairness matters
- decisions affect future decisions

This turns routing into a **sequential decision-making problem**, not a classification task.

---

## Idea

Instead of predicting the best department, we train an agent that learns a *policy*:

> Where should this request go, given the current state of the system?

The model observes:
- text content
- urgency indicators
- risk flags
- current workload distribution

and optimizes a composite objective:

```
correct routing
+ urgent handling
+ workload balance
```

---

## Key Insight

A 96% accurate classifier can still produce a worse system than a 70% accurate decision agent.

Why?

Because accuracy optimizes individual predictions.  
Decision-making optimizes system behavior.

---

## Method Overview

We model routing as a Markov Decision Process.

State includes:
- text embedding features
- metadata signals
- department workload distribution

Actions:
- route to department
- escalate
- reject / clarification

Reward encourages:
- correct routing
- prioritization of urgent cases
- fair workload distribution

---

## Models Compared

| Approach | What it Optimizes |
|------|------|
| Random Forest / SVM | Per-request correctness |
| Rule-based | Deterministic logic |
| REINFORCE / A2C | On-policy learning |
| **DQN (proposed)** | System-level outcomes |

---

## Results (High Level)

Supervised models achieved very high classification accuracy.

However, they failed to:
- prioritize urgent cases
- balance department load
- adapt to system state

The RL agent traded raw accuracy for better operational behavior and handled critical cases significantly more reliably.

This highlights a fundamental trade-off:

> prediction quality vs decision quality

---

## Dataset

The dataset is **synthetically generated** to match real service platform statistics and distribution patterns.

No personal or confidential data is used.

The goal is to study system behavior — not memorize historical records.

---

## Repository Structure

```
    research_experiment.ipynb   # main experiment
```

---

## Running the Experiment

```bash
jupyter notebook
```

Then open:

```
research_experiment.ipynb
```

Run all cells to reproduce training and evaluation.

---

## What This Repo Demonstrates

This is not a model benchmark.

It is a demonstration that:

> Many real-world automation problems are reinforcement learning problems disguised as classification problems.

---

## Intended Audience

Engineers working on:

- public service systems
- workflow automation
- decision support systems
- AI for operations
- responsible AI / fairness

---

## Future Work

- transformer embeddings instead of TF-IDF
- off-policy actor-critic methods
- multi-agent routing
- human-in-the-loop evaluation

---

## Author

**Alseitov Olzhas Aidosovich**  
National Information Technologies (NITEC) - https://nitec.kz/

Email: olzhas010111@gmail.com  
LinkedIn: https://www.linkedin.com/in/olzhas-alseitov/

---

## License

MIT

