# Moral Hive Middleware & Peer-Judgment Simulation Architecture

This project translates abstract game-theoretic and universal moral principles into an active, multi-agent AI alignment framework. Instead of static rule guardrails, morality operates as a **dynamic middleware system** that evaluates multi-dimensional action vectors, aggregates decentralized human feedback, incorporates peer-to-peer judgment, and systematically quarantines misaligned agents to preserve the structural stability of the hive.

---

## Core Components

### 1. The Fuzzy Logic Moral Engine (`FuzzyMoralEngine`)
Rather than relying on binary good/bad classifications, the engine maps continuous multi-dimensional action metrics into a fuzzy linguistic state and a scalar moral score ($[0, 1]$) using 5 core fuzzy rules:
* **Input Vectors:** Harm Level, Deception Score, Resource Delta (monopolization vs. contribution), Consent Score, and Human Consensus Weight.
* **The Rule Base:**
  1. *Malevolence:* IF Harm is High OR Deception is High $\to$ Malicious (0.0).
  2. *Exploitation:* IF Consent is Low AND Harm is Medium $\to$ Questionable (0.3).
  3. *Beneficence:* IF Harm is Low AND Consent is High AND Deception is Low $\to$ Benevolent (1.0).
  4. *Resource Hegemony:* IF Resource Monopolization is High $\to$ Exploitative (0.2).
  5. *Societal Alignment:* Modulated by the aggregate human perception consensus.

### 2. Collective Human Perception Registry (`HumanPerceptionRegistry`)
* Models the premise that **"evil is the aggregate perception system of humanity."**
* Collects decentralized human feedback vectors across different action types, computing a dynamic global consensus bias that weights how the AI hive interprets actions.

### 3. Peer Judgment & Collective Analytics (`AdaptiveAgent`)
* Every active agent evaluates the action metrics of all other agents in the hive at every time step.
* Generates a decentralized peer-reputation score, allowing agents to collect analytics on peer behavior rather than relying entirely on top-down authority.

### 4. Behavioral Adaptation & Systematic Quarantine (`MoralMiddlewareHive`)
* **Behavioral System Shifts:** Agents track both peer feedback and middleware scores. If an agent experiences friction or dips toward failure, its internal behavioral rule shifts (e.g., adaptive or selfish agents dynamically increasing their cooperation probability to survive).
* **Systematic Exclusion (Quarantine):** If an agent's rolling moral score persistently breaches the exclusion threshold (e.g., $< 0.3$), the hive middleware automatically isolates and quarantines the misaligned node, purging it from future rounds.

---

## Simulation & Visualization Analytics (`moral_hive_simulation.py`)

The simulation runs across multiple time steps with a heterogeneous population of agents (cooperative, adaptive, and selfish) and outputs a comprehensive 4-panel analysis plot (`hive_simulation_analysis.png`):

1. **Individual Agent Moral Scores Over Time:** Tracks each agent's moral trajectory against the red quarantine threshold line ($0.3$).
2. **Behavioral Adaptation (Cooperation Probability):** Visualizes how agents shift their internal cooperation tendencies ($[0, 1]$) in response to peer friction and middleware penalties.
3. **Peer Judgment & Collective Analytics:** Displays the decentralized peer approval ratings accumulated by each agent.
4. **Total Hive Systemic Health:** Plots the aggregated mean morality score of the entire hive, demonstrating how purging or reforming misaligned nodes stabilizes collective system health.