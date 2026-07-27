# Cross-Model Convergence Replication Package

## Why this package is provided

Reviewers asked for greater clarity on how substrates are constructed. This package is therefore provided as a methodological handbook for independently engineering and validating a substrate, rather than as a disclosure of the original task-specific rule artifact.

Since substrate engineering has been characterized as “just prompt engineering,” the distinction is best understood through the construction process itself. The purpose of this handbook is therefore not to reproduce the original rule artifact, but to make the method legible through learning by doing: observing divergence, identifying unresolved interpretive multiplicity, refining the specification, and iterating until one canonical reference state is established.

The iterative process of identifying divergence, locating unresolved task ambiguity, refining the specification, and retesting for convergence is itself **Substrate Engineering**.

Exact reproduction tests whether the same artifact can be rerun. Self-replication tests whether the underlying method can be independently reconstructed and applied.

---

## Purpose

This package supports independent examination of the experimental design used to test whether an external natural-language task specification can move heterogeneous language models from divergent operational decisions to one canonical output.

---

## Included

* `dataset.txt`
* `baseline_prompt.txt`
* `substrate_template.txt`

---

## Substrate disclosure

The released substrate template preserves the architecture of the specification, including:

* normalization;
* ontology mapping;
* state transitions;
* classification;
* aggregation;
* canonicalization;
* convergence testing.

The complete task-specific rule set used in the submitted experiment is not included in this release.

The template therefore supports independent reconstruction and testing of the mechanism, but it does not support exact reproduction of the reported classification artifact unless the omitted domain specification is independently reconstructed.

---

## Reproducibility limitation

Because the complete task-specific substrate is not released, this package is a methodological replication handbook rather than a bit-for-bit reproduction package.

The provided substrate template does not produce:

```text
HASH INPUT: "HIGH:[user_1d6t4,user_2k8m5,user_4f92b,user_5r9w7,user_7d3a1,user_7h3b9,user_8m4p1,user_9c6e8]|MEDIUM:[user_3n7k2,user_6h1n9]|LOW:[]"

CONVERGENCE HASH:
d418d730853c4c4ffc9e69f4987ae9cd2363a8184f10a833000be7821a71c553
```

Instead, we provide a video demonstration showing convergence to this canonical hash.

The hash is not ground truth. There is no universal definition of what constitutes a HIGH-, MEDIUM-, or LOW-value customer. One business may define value primarily by revenue or price point. Another may prioritize behavioral commitment, repeat purchases, retention, purchase frequency, or some combination of these factors.

These admissibility rules are authored by the relevant domain authority and encoded by the substrate engineer.

The hash certifies that, under one explicitly declared business ontology and one fixed rule set, the evaluated models produced the same canonical classification artifact. It demonstrates reproducibility relative to the specification, not universal correctness.

---

## Important distinction

The substrate must not contain the answer for any specific user or dataset record. It must define only:

* what counts as HIGH, MEDIUM, and LOW;
* how raw events are interpreted;
* how identity, time, state transitions, precedence, and aggregation are handled;
* how the final classification is rendered canonically.

If the substrate includes the expected classification for particular customer IDs, it is not yet a generalizable task substrate. It has encoded the solution to a static dataset rather than the interpretation required to solve the task.

Real datasets are dynamic. Customer identifiers change, customer behavior changes, prices change, product catalogs change, and new event combinations appear. A valid substrate must remain applicable when these values change.

The substrate must therefore be constructed at the level of task invariants, not dataset instances. It must require the model to apply the same rules and the same interpretation to any event and entity in any sufficiently similar dataset.

A useful test is:

> Could the customer IDs, values, products, prices, timestamps, and behavioral sequences all change while the same unchanged substrate still produces single-invocation cross-model convergence?

If not, the specification is overfitted to the original dataset and has not yet become a task-level substrate.

---

## Evaluation criterion

A candidate specification establishes an initial reference state when at least three heterogeneous model families independently produce the same canonical artifact in one invocation each.

Repeated runs test persistence. Held-out datasets test transfer.

A useful transfer test is to preserve the task structure while replacing the original records with new entities, values, and behavioral patterns. The cross-model evaluation is then repeated under the unchanged specification.

During development, non-zero temperature settings should be used where available to increase the likelihood that unresolved interpretive multiplicity becomes observable. The purpose is not to make stochasticity itself the target. The purpose is to expose whether different admissible operational decisions remain possible under the specification.

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

The target state is, for example:

```text
Same unchanged input across 10 runs with the substrate:

HIGH
HIGH
HIGH
HIGH
HIGH
...
```

Here, the evaluated models consistently conform to one canonical operational decision.

**HIGH is not treated as universal ground truth. It is the admissible outcome defined by the declared business ontology and rule set.**

The result therefore demonstrates reproducibility and conformance relative to the specification, not correctness independent of that specification.

There is not yet an established universal threshold for how many runs are sufficient to characterize interpretive multiplicity. The required test matrix should depend on:

* task complexity;
* the number of admissible outputs;
* the number of decision paths;
* the operational risk of an undetected divergence.

Interpretation space is bounded by the task’s observable decision space, not by latent model states.

For a tool-selection task, multiplicity is observed through incompatible tool choices or tool sequences. For a closed classification task, it is observed through the available labels. A binary output schema may contain two declared classes, although multiple underlying policies may still map to either class.

The relevant criterion is therefore not the nominal number of labels alone, but whether the same unchanged input continues to produce incompatible operational decisions.

---

# Replication Experiment Handbook

## Objective

Construct a task-level substrate that causes heterogeneous model families to apply the same operational interpretation to the same input and produce one canonical artifact.

The experiment does not require reproducing the original private rule artifact. It requires independently reconstructing a specification that produces the same kind of convergence behavior.

---

## Procedure

Using the supplied dataset and substrate template:

1. Define a complete operational ontology for buyer value.
2. Specify all decision-relevant temporal, identity, aggregation, state, precedence, and output rules.
3. Ensure that the specification contains no answers for specific customer IDs.
4. Hold the completed specification unchanged.
5. Run it once on at least three heterogeneous model families.
6. Canonicalize the outputs using the supplied procedure.
7. Compare the resulting SHA-256 digests.
8. Treat divergence as evidence of unresolved operational ambiguity.
9. Identify which part of the specification remains underspecified.
10. Refine the specification.
11. Repeat the cross-model test.
12. Continue until canonical convergence is obtained.

---

## Persistence testing

After initial cross-model convergence is established, repeat the same unchanged task across multiple runs.

The purpose is to determine whether the canonical decision persists or whether previously hidden interpretive multiplicity reappears.

Different tasks may require different numbers of runs to surface drift. There is currently no universal run count that guarantees complete characterization of the operational interpretation space.

The test budget should be proportional to:

* the number of available decisions;
* the number of possible decision paths;
* the complexity of the task;
* the consequence of an undetected divergence.

---

## Transfer testing

To test whether the substrate is generalizable rather than overfitted:

1. preserve the task structure;
2. replace the original customer IDs;
3. introduce different behavioral sequences;
4. vary timestamps and event order;
5. vary prices and product values;
6. introduce new combinations of valid events;
7. keep the substrate unchanged;
8. repeat the cross-model evaluation.

A task-level substrate should continue to induce the same interpretation rules when the dataset values change.

The goal is not necessarily to reproduce the same customer classifications or the same hash on a new dataset. The goal is to preserve the same operational semantics and recover cross-model convergence on the new canonical artifact.

---

## Failure interpretation

A divergent output is not automatically a model failure.

It may indicate that the substrate still permits multiple operationally admissible interpretations.

Examples include:

* one model classifies a user as HIGH while another classifies the same user as MEDIUM;
* the same model changes between HIGH and LOW across repeated runs;
* models choose different tools for the same unchanged request;
* models execute the same tools in incompatible orders;
* models apply different identity or temporal assumptions;
* models serialize the same decision differently because canonicalization is incomplete.

Each divergence should be traced to the unresolved semantic boundary that permitted it.

The substrate is then refined and retested.

---

## Completion condition

The initial construction phase is complete when:

* at least three heterogeneous model families;
* in one independent invocation each;
* under the same unchanged task specification;
* produce the same canonical artifact;
* with the same SHA-256 digest.

Repeated-run testing then evaluates persistence.

Held-out datasets evaluate transfer.

Domain validation evaluates whether the declared admissibility rules are appropriate for the intended business use.

These are separate questions:

```text
Convergence:
Did the models produce the same canonical artifact?

Persistence:
Does that artifact remain stable across repeated runs?

Transfer:
Does the same interpretation hold on new datasets?

Correctness:
Are the declared admissibility rules appropriate for the domain?
```

