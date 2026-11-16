# Moral Hive Simulation: Adaptive Multi-Agent Alignment & Rehabilitative Dynamics

[![Python 3.8+](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Research Prototype](https://img.shields.io/badge/status-active%20research-success.svg)]()

A rigorous, first-principles computational framework exploring AI alignment, evolutionary stability, and decentralized moral governance in multi-agent systems. This repository contains both the formal mathematical manuscript (`ai_alignment_invariants.tex`) and an interactive simulation script demonstrating how cooperative norms can be maintained against selfish defectors via a **Fuzzy-Logic Moral Middleware** and a **Rehabilitative Probation System**.

---

## 🏛️ Theoretical Overview

Traditional multi-agent simulations often rely on binary, punitive exclusion ("zero-tolerance") which leads to brittle systems and systemic collapse. This project implements a **rehabilitative governance model** inspired by game theory, axiomatic fairness, and informational guardrails:

1. **Moral Middleware:** An interceptor layer that evaluates agent actions against compliance metrics (harm, deception, resource delta) to generate continuous moral scores.
2. **Decentralized Peer Judgment:** Agents dynamically observe peer behaviors, compute a localized reputation score, and adapt their strategies accordingly.
3. **Probation & Strike System:** Instead of immediate termination, non-compliant agents receive warning strikes and enter a **probationary period**.
4. **Rehabilitative Effort Factor:** Probationary agents exert conscious behavioral adaptation to reform. Persistent defectors failing to reform after 4 strikes are systematically quarantined/terminated to preserve collective hive health.

---

## 📂 Repository Structure

```text
├── LICENSE.txt
├── README.md
├── repo_str.py
├── research/
│   ├── new_theory/
│   │   ├── final_ethical_framework.pdf
│   ├── theory/
│   │   ├── ai_alignment_study_preparation_guide.md
│   │   ├── morality_alignment.pdf
├── sim_exp/
│   ├── adaptive_rehabilitative_hive_analysis.png
│   ├── experiment_detials.md
│   ├── experiment_test.ipynb
│   ├── rehabilitative_hive_analysis.png
```

---

## 📄 Citation

If you use this framework or code in your research, please cite our paper draft:

```bibtex
@software{rehabilitative_hive_alignment,
  title={Moral Hive Simulation: Adaptive Multi-Agent Alignment & Rehabilitative Dynamics},
  author={Barış Can Tayiz},
  year={2026},
  publisher={Zenodo},
  doi={10.5281/zenodo.24268017},
  url={https://doi.org/10.5281/zenodo.24268017}
}

