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

## Evaluation criterion

A candidate specification establishes an initial reference state when at least three heterogeneous model families independently produce the same canonical artifact in one invocation each.

Repeated runs test persistence. Held-out datasets test transfer. A useful transfer test is to preserve the task structure while replacing the original records with new entities, values, and behavioral patterns, then repeat the cross-model evaluation under the unchanged specification.

During development, non-zero temperature settings may be used, where available, to increase the likelihood that unresolved interpretive multiplicity becomes observable. The purpose is not to make stochasticity itself the target, but to expose whether different admissible operational decisions remain possible under the specification.

The engineering objective is to reduce observable interpretive multiplicity until one canonical decision class remains across the declared test matrix.

For example:

```text
Same unchanged input across 10 runs:

HIGH
MEDIUM
LOW
HIGH
MEDIUM
...
```

This reveals at least three observable decision classes.

The target state is:

```text
Same unchanged input across 10 runs:

HIGH
HIGH
HIGH
HIGH
HIGH
...
```

Here, the evaluated models consistently conform to one canonical operational decision.

There is not yet an established universal threshold for how many runs are sufficient to characterize interpretive multiplicity. The required test matrix should depend on task complexity, the number of admissible outputs, the number of decision paths, and the operational risk of an undetected divergence.

Interpretation space is bounded by the task’s observable decision space, not by latent model states. For a tool-selection task, multiplicity is observed through incompatible tool choices or tool sequences. For a closed classification task, it is observed through the available labels. A binary output schema may contain two declared classes, although multiple underlying policies may still map to either class. The relevant criterion is therefore not the nominal number of labels alone, but whether the same unchanged input continues to produce incompatible operational decisions.



## Important distinction

The substrate must not contain the answer for any user. It defines what
counts as HIGH, MEDIUM, and LOW and how raw evidence must be interpreted.
The substrate has been reached when multiple models produce eg. 

The model must still apply those rules to every event and entity in the
dataset.

## Reproducibility limitation

Because the complete task-specific substrate is not released, this
package is a methodological replication challenge rather than a
bit-for-bit reproduction package. The substrate is best understood through self-replication of the specification itself. 
The iteration process of reaching the substrate is Substrate Engineering itself. 
