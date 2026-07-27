# Cross-Model Convergence Replication Package

## Purpose

This package supports independent examination of the experimental design
used to test whether an external natural-language task specification can
move heterogeneous language models from divergent operational decisions
to one canonical output.

## Included

- `dataset.txt`
- `baseline_prompt.txt`
- `substrate_template.txt`


## Substrate disclosure

The released substrate template preserves the architecture of the
specification, including normalization, ontology mapping, state
transitions, classification, aggregation, canonicalization, and
convergence testing.

The complete task-specific rule set used in the submitted experiment is
not included in this release. The template therefore supports independent
reconstruction and testing of the mechanism, but not exact reproduction
of the reported classification artifact without implementing an
equivalent domain specification. 

## Cross-Model Convergence Replication

Using the supplied dataset and template:

1. Define a complete operational ontology for buyer value.
2. Specify all decision-relevant temporal, identity, aggregation, state,
   precedence, and output rules.
3. Hold the resulting specification unchanged.
4. Run it once on at least three heterogeneous model families.
5. Canonicalize the outputs using the supplied procedure.
6. Compare SHA-256 digests.
7. Treat divergence as evidence of unresolved task ambiguity.
8. Keep refinning the specification and repeat until canonical convergence is
   obtained.

## Evaluation criterion

A candidate specification establishes an initial reference state when at least three heterogeneous model families independently produce the same canonical artifact in one invocation each.

Repeated runs test persistence. Held-out datasets test transfer. A useful transfer test is to preserve the task structure while replacing the original records with new entities, values, and behavioral patterns, then repeat the cross-model evaluation under the unchanged specification.

During development, non-zero temperature settings may be used, where available, to increase the likelihood that unresolved interpretive multiplicity becomes observable. The purpose is not to make stochasticity itself the target, but to expose whether different admissible operational decisions remain possible under the specification.

The engineering objective is to reduce observable interpretive multiplicity until one canonical decision class remains across the declared test matrix.

For example:

```text
Same unchanged input across 10 runs produces:

HIGH
MEDIUM
LOW
HIGH
MEDIUM
...
```

This reveals at least three observable decision classes.

The target state is for example:

```text
Same unchanged input across 10 runs with substrate produces:

HIGH
HIGH
HIGH
HIGH
HIGH
...
```

Here, the evaluated models consistently conform to one canonical operational decision that is defined as "ground truth" and correct.

There is not yet an established universal threshold for how many runs are sufficient to characterize interpretive multiplicity. The required test matrix should depend on task complexity, the number of admissible outputs, the number of decision paths, and the operational risk of an undetected divergence.

Interpretation space is bounded by the task’s observable decision space, not by latent model states. For a tool-selection task, multiplicity is observed through incompatible tool choices or tool sequences. For a closed classification task, it is observed through the available labels. A binary output schema may contain two declared classes, although multiple underlying policies may still map to either class. The relevant criterion is therefore not the nominal number of labels alone, but whether the same unchanged input continues to produce incompatible operational decisions.

## Important distinction

The substrate must not contain the answer for any specific user or dataset record. It must define only:

* what counts as HIGH, MEDIUM, and LOW;
* how raw events are interpreted;
* how identity, time, state transitions, precedence, and aggregation are handled;
* how the final classification is rendered canonically.

If the substrate includes the expected classification for particular customer IDs, it is not yet a generalizable task substrate. It has encoded the solution to a static dataset rather than the interpretation required to solve the task.

Real datasets are dynamic. Customer identifiers change, customer behavior changes, prices change, product catalogs change, and new event combinations appear. A valid substrate must remain applicable when these values change.

The substrate should therefore be constructed at the level of task invariants, not dataset instances. It must require the model to apply the same rules and the same interpretation to any event and entity in any sufficiently similar dataset.

A useful test is:

> Could the customer IDs, values, products, prices, timestamps, and behavioral sequences all change while the same substrate still produces the single shot cross-model convergence?

If not, the specification is overfitted to the original dataset and has not yet become a task-level substrate.


## Reproducibility limitation

Because the complete task-specific substrate is not released, this package is a methodological replication handbook rather than a bit-for-bit reproduction package. The provided substrate does not produce:

```text
HASH INPUT: "HIGH:[user_1d6t4,user_2k8m5,user_4f92b,user_5r9w7,user_7d3a1,user_7h3b9,user_8m4p1,user_9c6e8]|MEDIUM:[user_3n7k2,user_6h1n9]|LOW:[]"

CONVERGENCE HASH:
d418d730853c4c4ffc9e69f4987ae9cd2363a8184f10a833000be7821a71c553
```

Instead, we provide a video demonstration showing convergence to this canonical hash.

The hash is not ground truth. There is no universal ground truth for what a business should consider HIGH-, MEDIUM-, or LOW-value. Those admissibility rules are defined by the domain author and substrate engineer. The hash certifies that, under one declared business ontology and one fixed set of rules, the evaluated models produced the same canonical classification artifact. It establishes reproducibility relative to that specification, not universal correctness.

The substrate is best understood by independently reconstructing the specification and reproducing the convergence process. The objective is not to copy the original rule artifact, but to determine whether an independently engineered specification can reduce observable interpretive multiplicity and establish the same kind of canonical reference state.

The iterative process of identifying divergence, locating unresolved task ambiguity, refining the specification, and retesting for convergence is itself **Substrate Engineering**.

Exact reproduction tests whether the same artifact can be rerun. Self-replication tests whether the underlying method can be independently reconstructed and applied.
