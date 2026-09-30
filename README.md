# Quantum Compilation Experiments

A collection of small, controlled experiments exploring how compiler decisions affect the physical cost of quantum circuits.

This repository documents focused experiments in **quantum compilation**, especially hardware-aware and resource-efficient compilation. Each experiment is intentionally scoped to isolate one question, keep the setup reproducible, and make limitations explicit.

## Current Experiments

| Experiment | Question | Status |
|---|---|---|
| [Gate Ordering and Quantum Routing](experiments/gate-ordering-routing/) | Can logically equivalent gate orderings produce different physical compilation costs? | Completed exploratory experiment |

## Research Themes

- Quantum circuit compilation
- Hardware-aware compilation
- Mapping and routing
- Physical-cost metrics
- Resource-efficient quantum computing
- Compiler sensitivity and reproducibility

## How This Repository Is Organized

Each experiment has its own folder containing:

- a short README with the research question and setup;
- the notebook or script used for the experiment;
- the main observations;
- and the limitations of the experiment.

The goal is to keep a record of **experimental reasoning**, not just code.

## Repository Structure

```text
quantum-compilation-experiments/
├── experiments/
│   └── gate-ordering-routing/
│       ├── README.md
│       └── Impact_of_Gate_Ordering_on_Quantum_Routing.ipynb
├── requirements.txt
└── README.md
```

## Scope

These are exploratory experiments. Results are reported only for the exact configurations described in each experiment and should not be interpreted as general claims about all circuits, devices, or compilers.

---

**Atena Raeisi**  
Computer Engineering undergraduate interested in quantum compilation, computer architecture, and hardware-aware quantum systems.
