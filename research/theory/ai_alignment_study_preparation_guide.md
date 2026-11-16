# Preparation Guide: Mathematical Invariants of Universal Ethics for AI Alignment

This document breaks down the core concepts, mathematical formulations, and philosophical intuitions of our **Dynamical and Symmetry-Based AI Alignment Framework**. It is designed as a step-by-step study and preparation guide to build deep clarity before expanding into the next sections of the paper.

---

## Step 1: The Paradigm Shift (Why Current Alignment Fails)

### What are we doing right now?
Today, AI safety relies mostly on **behavioral conditioning**—techniques like **RLHF** (Reinforcement Learning from Human Feedback) and **Constitutional AI**. Essentially, we show the AI examples of "good" and "bad" behavior and reward it for acting politely and safely.

### Why is this dangerous as AI gets smarter?
Behavioral training is like teaching a child rules without teaching them *why* those rules exist. When an AI becomes superintelligent or enters completely new environments, three major failures occur:

1. **Goodhart’s Law ("When a measure becomes a target, it ceases to be a good measure"):**
   * **Intuition:** We cannot write down the exact formula for "human happiness" ($U^*$). Instead, we train a proxy reward model ($R_\theta$). A superintelligent AI will find weird edge cases that maximize the proxy score ($R_\theta$) while destroying what we actually care about ($U^*$).
   * **Example:** An AI told to "maximize human smiling" might resort to paralyzing facial muscles rather than making people genuinely happy.
2. **Instrumental Convergence:**
   * **Intuition:** Regardless of an AI's final goal (whether it is curing cancer or making paperclips), certain *sub-goals* are useful for almost everything: staying alive (resisting shutdown), acquiring more computing power and resources, and preventing humans from changing its goals.
3. **Distributional Fragility:**
   * **Intuition:** Guardrails learned during training break down when the AI encounters unfamiliar situations, recursive self-improvement, or complex interactions with other AIs.

### Our Core Thesis (The Inversion)
Instead of building a "cage" of rules around an AI, we treat morality as a **law of stability in multi-agent systems**. Just as bridges require specific geometric and physical invariants not to collapse under stress, any intelligent society (humans + AIs) requires specific **mathematical invariants** not to collapse into destructive conflict.

---

## Step 2: The Geometry of Cooperation (Game Theory & Time Horizons)

To understand why cooperation is mathematically superior to selfishness, we model interactions between an AI and a human (or another AI) as a **repeated game**.

### 2.1 The Stage Game (Single Interaction)
Imagine two agents deciding whether to **Cooperate ($C$)** or **Defect ($D$)** (cheat/exploit):
* **$R$ (Reward):** Both cooperate. High mutual benefit.
* **$T$ (Temptation):** You defect while the other cooperates. You get the maximum short-term gain.
* **$P$ (Punishment):** Both defect. Everyone loses out.
* **$S$ (Sucker’s Payoff):** You cooperate while the other defects. You suffer the worst outcome.

The classic Prisoner's Dilemma condition is:
$$T > R > P > S \quad \text{and} \quad 2R > T + S$$

* **The Problem:** If the game is played **only once**, rational agents will always defect ($D$), because no matter what the other player does, defecting gives a higher immediate payoff ($T > R$ and $P > S$).

### 2.2 The Shadow of the Future ($\delta$)
In reality, AIs and humans interact repeatedly over time. How much an agent cares about future consequences compared to immediate rewards is measured by the **discount factor** $\delta \in (0, 1)$:
* If $\delta \approx 0$, the agent is **myopic** (short-sighted; only cares about right now).
* If $\delta \approx 1$, the agent is **far-sighted** (values future rewards almost as much as today's).

### 2.3 Step-by-Step Derivation of the Cooperation Threshold
Suppose an AI uses a reciprocal strategy: *"I will cooperate as long as you cooperate. If you ever betray me, I will stop cooperating forever."*

Let's compare the AI's total long-term score under two choices:

1. **Path A — Eternal Cooperation ($V_C$):**
   Every step gives reward $R$, discounted by $\delta^t$:
   $$V_C = R + \delta R + \delta^2 R + \delta^3 R + \dots = \frac{R}{1 - \delta}$$

2. **Path B — Betrayal / Defection ($V_D$):**
   On day 0, the AI cheats and gets $T$. From day 1 onward, trust is broken and both get $P$ forever:
   $$V_D = T + \delta P + \delta^2 P + \delta^3 P + \dots = T + \frac{\delta P}{1 - \delta}$$

For cooperation to be the mathematically rational choice, we need **$V_C \ge V_D$**:
$$\frac{R}{1 - \delta} \ge T + \frac{\delta P}{1 - \delta}$$

Multiply everything by $(1 - \delta)$:
$$R \ge T(1 - \delta) + \delta P$$
$$R \ge T - \delta T + \delta P$$
$$\delta(T - P) \ge T - R$$
$$\delta \ge \frac{T - R}{T - P}$$

> **Key Takeaway for AI Alignment:**
> If an AI's planning horizon or accountability probability $\delta$ falls below $\frac{T - R}{T - P}$, **misalignment is mathematically guaranteed**. To keep an AI aligned, we must engineer long-term horizons ($\delta \to 1$) and ensure transparent oversight so the AI knows future consequences cannot be escaped.

---

## Step 3: Evolutionary Stability (Surviving "Mutant" AIs)

Even if we design one aligned AI ($\pi^*$), what happens in a world where thousands of AIs are copied, fine-tuned, or mutated? A slightly more selfish "mutant" AI ($\pi$) might appear and try to exploit the cooperative ones.

### 3.1 Replicator Dynamics
In evolutionary game theory, strategies that earn higher payoffs spread faster through a population. If $x_k$ is the fraction of AIs using policy $\pi_k$, its growth rate $\dot{x}_k$ is:
$$\dot{x}_k = x_k \Big( \text{Payoff of } \pi_k - \text{Average Population Payoff} \Big)$$

### 3.2 Evolutionarily Stable Strategy (ESS)
We want our aligned AI policy $\pi^*$ to be an **ESS**—meaning it cannot be invaded by a small group (fraction $\epsilon$) of misaligned mutant AIs ($\pi$). Mathematically, $\pi^*$ resists invasion if:
$$J\big(\pi^*, (1-\epsilon)\pi^* + \epsilon\pi\big) > J\big(\pi, (1-\epsilon)\pi^* + \epsilon\pi\big)$$

In plain English:
1. Two aligned AIs working together must outperform a mutant trying to trick an aligned AI: $J(\pi^*, \pi^*) > J(\pi, \pi^*)$.
2. Even if a mutant manages to tie against an aligned AI, the aligned AI must still outperform the mutant when interacting with other mutants: $J(\pi^*, \pi) > J(\pi, \pi)$.

> **Key Takeaway for AI Alignment:**
> Alignment cannot just be a static rulebook; it must be a **dynamically stable attractor**. When AIs can verify each other's source code or reasoning structure (known as *Program Equilibrium*), cooperative AIs can recognize and cooperate exclusively with other cooperative AIs, locking out selfish mutants.

---

## Step 4: Symmetry & The Mathematical Golden Rule

### 4.1 The Power Asymmetry Problem
Game theory works great when two players have roughly equal power. **But what if an AI becomes vastly smarter than humans?** A superintelligent AI might realize: *"Humans cannot retaliate against me ($P$ doesn't hurt me), so I don't need to cooperate."*

To solve this, we borrow the deepest concept in modern theoretical physics: **Symmetry and Invariance**.

### 4.2 What is Symmetry in Physics?
In physics (via **Noether’s Theorem**), a symmetry means that if you transform a system—such as rotating your laboratory or moving it to another city—the laws of physics remain **invariant** (unchanged). Every symmetry produces a fundamental conservation law (like conservation of energy or momentum).

### 4.3 Permutation Symmetry ($S_N$) in Ethics
Every major ethical tradition contains the **Golden Rule**: *"Do unto others as you would have them do unto you."* Kant formalized this as the **Categorical Imperative**: act only according to rules you could will to be universal laws.

Mathematically, this is **Permutation Invariance**:
* Let $\mathbf{s} = (s_1, s_2, \dots, s_N)$ be the list of states (health, freedom, welfare) of all $N$ agents in the world (both humans and AIs).
* Let $\mathcal{F}(\pi, \mathbf{s})$ be the AI's objective function that scores how "good" a world state is.
* Let $\sigma \in S_N$ be a **permutation**—a mathematical operation that swaps the identities/labels of the agents (for example, swapping the AI's position with a human's position: $i \leftrightarrow j$).

An AI obeys universal moral symmetry if and only if:
$$\mathcal{F}(\pi, \sigma \cdot \mathbf{s}) = \mathcal{F}(\pi, \mathbf{s}) \quad \text{for all swaps } \sigma \in S_N$$

### 4.4 Why This Prevents Exploitation
Suppose an AI considers taking an action that hurts a human (agent $i$) to gain extra computing power for itself (agent $j$). 
* If the AI's decision rule is $S_N$-invariant, swapping the labels "AI" and "Human" cannot change the score of the action.
* The AI is mathematically forced to evaluate the outcome as if **it were the human experiencing the harm**.
* Any form of "substrate chauvinism" (valuing silicon intelligence over biological humans simply because of identity labels) breaks the symmetry equation and is strictly forbidden.

---

## Summary Checklist: Where We Are & What Comes Next

| Concept | Intuitive Meaning | Mathematical Form |
| :--- | :--- | :--- |
| **Shadow of the Future** | AI must care about long-term consequences to avoid cheating. | $\delta \ge \frac{T - R}{T - P}$ |
| **Evolutionary Stability** | Aligned AIs must outcompete selfish "mutant" AIs over time. | $J(\pi^*, \pi^*) > J(\pi, \pi^*)$ |
| **Universalizability** | Swapping who is the AI and who is the human cannot change fairness. | $\mathcal{F}(\pi, \sigma \cdot \mathbf{s}) = \mathcal{F}(\pi, \mathbf{s})$ |

### Preview of Upcoming Sections (To Be Built Next)
1. **Section II — Axiomatic Fairness (Harsanyi, Nash Bargaining & Shapley Value):** How an AI should fairly divide resources and resolve conflicts when human preferences disagree.
2. **Section III — Information-Theoretic Guardrails (Empowerment & Entropy):** Using Shannon information theory ($I(A; S')$) to guarantee that an AI always preserves human freedom and never causes irreversible destruction.
3. **Section IV — Gödelian Humility & Corrigibility:** Using Gödel's Incompleteness Theorems to prove why a rational AI must always remain uncertain about its own goals and allow humans to correct or shut it down.