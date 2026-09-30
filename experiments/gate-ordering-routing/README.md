# Impact of Gate Ordering on Quantum Routing

A controlled exploratory experiment on whether **logically equivalent gate orderings can lead to different physical compilation costs**.

## Research Question

**Can different orderings of equivalent commuting CZ gates produce different physical circuits after compilation?**

The logical operation is kept unchanged, while the ordering of the commuting CZ gates is varied before transpilation.

## Experimental Setup

| Component | Setting |
|---|---|
| Logical circuit | 6 qubits, 10 CZ gates |
| Orderings | 1 original + 20 random + 1 simple heuristic |
| Random-order seed | 42 |
| Hardware topology | 6-qubit line |
| Initial layout | `[0, 1, 2, 3, 4, 5]` |
| Routing method | SABRE |
| Qiskit optimization level | 1 |
| Transpiler seeds | 0, 1, 2, 3, 4 |
| Native basis | `rz`, `sx`, `x`, `cx` |

The gate set, hardware topology, initial layout, and compiler settings are fixed. The variable being changed is the **ordering of the CZ gates**.

The experiment evaluates 22 orderings over 5 transpiler seeds, giving **110 routing-stage compilation runs**. The same 22 × 5 evaluation is repeated after translation to the native basis.

## Metrics

The experiment compares:

- routing-stage depth;
- SWAP count;
- final native circuit depth;
- final CX count.

## Results

### Routing-stage results

| Ordering group | Mean depth | Mean SWAP count |
|---|---:|---:|
| Original | 17.60 | 12.00 |
| Random orderings (average) | 14.37 | 10.91 |
| Simple heuristic | 17.00 | 10.00 |

Across individual random orderings, the mean SWAP count ranged from **8 to 13**.

Two random orderings reached a mean SWAP count of 8, while several required 13, even though all orderings represented the same commuting CZ gate set.

### Native-basis results

For the original ordering:

- mean native depth: **60.8**
- mean CX count: **46.0**

Across the random orderings:

- mean native depth ranged from **43.0 to 68.6**;
- mean CX count ranged from **34.0 to 49.0**;
- average native depth across random orderings: **54.65**;
- average CX count across random orderings: **42.73**.

The heuristic ordering produced:

- mean native depth: **57.0**
- mean CX count: **40.0**

## Main Observation

The experiment provides a small controlled example where changing the ordering of commuting logical gates changes the routing decisions and the resulting physical cost.

The point is **not** that the simple heuristic is optimal. Rather, the experiment shows that logical equivalence alone does not guarantee equal physical compilation cost.

## Limitations

This is intentionally a small exploratory experiment.

- Only one synthetic 6-qubit circuit is tested.
- Only a line topology is used.
- Only SABRE routing is evaluated.
- Only five transpiler seeds are used.
- The heuristic is a simple proof of concept, not a validated optimization algorithm.
- Noise, calibration data, scheduling duration, and real-hardware execution are not considered.

The results should therefore be interpreted as a controlled observation, not as a general benchmark claim.

## Files

- `Impact_of_Gate_Ordering_on_Quantum_Routing.ipynb` — cleaned, reproducible notebook for the experiment.

## Connection to Later Work

This experiment helped motivate a broader interest in how compiler-level choices affect **physical execution cost**, including later work on qubit reuse, routing, and hardware-aware quantum compilation.
