---
name: research-idea-audit
description: Evaluate a research idea's core claim, background, related work, novelty, feasibility, minimum-cost pilot, and experimental evidence. Use when proposing, screening, reproducing, or advancing a research idea; not for routine paper copyediting or a standalone literature summary.
---

# Research Idea Audit

Treat a research idea as a scientific claim to test, not a collection of attractive experiments. The review must answer: **What exactly is new, why does it matter, what evidence would support or refute it, and what is the cheapest credible first test?**

Respect the user's field, task, resources, data, methods, and research stage. State assumptions when these are unspecified; ask only when a consequential gap cannot reasonably be resolved. Deliver in the user's language unless asked otherwise. A review or experiment plan does not itself authorize execution.

## 1. Build a coherent research case for the user's review

Prepare an idea dossier that addresses each item explicitly:

1. **Background:** Define the concrete problem, current approaches, relevant setting, and why the problem matters. Avoid generic claims of importance.
2. **Related work:** Organize the closest work by problem, mechanism, and evidence. For each paper, state what it actually proposed and established, what it did not establish, and a verifiable source. Do not diminish or exaggerate another paper's contribution to make this idea look stronger.
3. **Research gap:** Derive the unresolved question from the limits of existing work. State when the gap exists, why current methods do not already cover it, and what finding would close or invalidate it.
4. **Meaning of the idea:** Explain what new understanding, capability, or decision value would follow if the claim held. Distinguish scientific significance from practical usefulness.
5. **Idea:** State one falsifiable central claim, its proposed mechanism, scope, necessary assumptions, and plausible failure modes. An implementation is a means of testing the claim; it is not automatically a contribution.
6. **Contribution:** List the proposed increments in knowledge or method and the evidence each would require. Separate proposed contributions, supported contributions, and unverified claims. A positive score alone need not be a meaningful contribution.
7. **Story:** Build one progressive chain: background → related work → gap → claim and mechanism → testable predictions → evidence → contribution. Each step should justify the next; experiments should not form a disconnected list.
8. **Experiments in detail:** For every experiment, specify its precise purpose, the part of the claim or mechanism it tests, a discriminating prediction, variables and controls, data and sample, metrics and analysis, success and failure criteria, likely confounders, and what its result could and could not establish. If it does not support the main line, explain its auxiliary role or remove it.

Submit this case for the user's review, marking unverified facts, assumptions, and open choices. If the user requests a complete review in one pass, include the later checks in the same document while clearly distinguishing a **proposed** research line from one the user has **approved**. Do not approve or freeze it on the user's behalf.

Maintain the dossier as a living, versioned research record. Keep its background and related-work papers current, with primary sources, the claims actually checked, and the date checked. When new literature or evidence changes the background, gap, novelty, contribution, story, or experiment rationale, update the affected sections and log what changed and why. Preserve earlier versions, user decisions, and contrary evidence rather than silently rewriting the research line.

## 2. Audit novelty against the closest work

Find the studies most likely to anticipate the claim. Check original papers, official code, and formal appendices when available, including versions and dates. Do not rely on titles, search snippets, or memory in place of the source. Compare, paper by paper: overlap, the prior contribution's actual boundary, this idea's precise increment, the evidence needed to establish that increment, and the strongest counterexample.

Judge whether the increment is substantial and nontrivial. A new task, model, dataset, component, or routine ablation does not by itself establish novelty. If prior work already covers the central claim, say so. A possible alternative direction must be treated as a **new idea** and reviewed anew, rather than silently substituted for the original claim.

## 3. Audit feasibility

Separate what seems possible from what the available evidence supports:

- **Data:** Identify publicly obtainable datasets and access conditions. Inspect actual files or representative records for format, fields, labels, granularity, size, splits, license, and task difficulty. Map these properties to the experiment's required inputs, interventions, supervision, outcomes, and evaluation. A dataset description or repository listing alone does not establish fit.
- **Implementation:** Identify reusable code, baselines, and evaluators. Estimate preparation, training or inference, compute, time, and token cost. Name dependencies, permissions, and likely engineering bottlenecks.
- **Theory and intuition:** Explain why the proposed mechanism could produce the prediction under the stated assumptions, what theory or prior evidence actually supports, and what remains intuition. Consider counterexamples. Theoretical possibility, intuitive plausibility, and empirical success are distinct judgments.

Conclude with **ready for a minimal pilot**, **specific gap to resolve first**, or **currently infeasible**. State what evidence would change that judgment. Mark unknowns as unknown; never invent data or results.

## 4. Design the lowest-cost pre-experiment

The first objective is to look for a **credible positive signal for the fixed idea**, while specifying in advance what would count against it. Use the smallest data slice, simplest working implementation, and essential controls that still distinguish the proposed mechanism from cheap alternative explanations. Reduce time, compute, and API or token cost without removing the comparison needed to answer the question.

Before execution, write a reproducible experiment card: fixed claim and prediction; data version and sample selection; treatment, control, and budget; code and model versions; primary metric; thresholds for positive signal and failure; analysis; stop rule; estimated cost; and criteria for continuation. Set decision rules before seeing outcomes. Explain how qualitative criteria will be judged. Check for leakage, unequal information access, unfair baselines, and incompatible evaluation protocols.

A positive pilot justifies further testing; it does not by itself prove the mechanism, novelty, or a paper-level contribution. If the pilot has no positive signal, report that the current evidence does not support the idea. Diagnose implementation or measurement errors when warranted, but preserve the original result and claim. Do not change the target, metric, sample, or story after seeing results to manufacture success.

### Confirm every run and verify correctness before scaling

Before every experiment launch, present the complete resolved configuration to the user and wait for explicit confirmation. This includes validation runs, pilots, reruns after fixes, and larger experiments. Include the purpose; code and environment versions; data, split, sample selection and size; arms and baselines; model/provider routes; prompt versions; hyperparameters, seeds and repetitions; evaluator and metrics; concurrency, timeouts and retry policy; cost limits, stop rules, and output location. Resolve implicit defaults and omit secret values. Record the configuration snapshot and the user's confirmation. Approval covers only that run or an explicitly enumerated batch; a new launch or configuration change requires fresh confirmation. Execution within an already approved run does not require repeated approval for each internal step.

Before any increase beyond the smallest validation scale, verify the entire planned experiment with minimal end-to-end runs. Cover every planned arm, baseline, model/provider route, dataset format, and evaluation path using the intended execution stack and representative real inputs. Check both successful execution and semantic correctness: the intended method and settings were actually used, inputs and labels align, treatments and controls follow the protocol, outputs are valid, scoring and aggregation are correct, and saved records allow reproduction. Inspect raw traces and independently check representative scores; a successful exit, mock run, or plausible aggregate metric alone is insufficient.

Maintain a coverage table with the evidence and pass/fail/not-checked status of each required path. All required checks must pass, with no unresolved correctness issues, before even a moderately larger run. After a change, recheck affected paths and confirm the new configuration. Present the validation evidence together with the proposed larger-run configuration for the user's confirmation before launch; positive pilot results do not bypass either gate.

## 5. Interpret every result against the original idea

Preserve the planned protocol, deviations, configuration, data and code versions, raw outputs, and actual cost. For each run, answer:

1. Did the result match the preregistered prediction? Report effect size, variability, uncertainty, and negative, invalid, or missing outcomes separately.
2. Which link in the claim's logic does it support or challenge? Is it mechanism evidence, phenomenon-level evidence, or only evidence about implementation or measurement?
3. Which confounders, alternative explanations, or protocol problems remain? What cannot be inferred from this result?
4. Should work continue, be repaired and rerun, narrow the claim, pause, or stop? What additional evidence and cost would that decision require?

State **whether the result supports the idea, how, and within what limits**. Do not let a disappointing result silently move the idea. Number any revised claim separately, record its difference from the original, and repeat the related-work, novelty, feasibility, and experiment-design review. Never present a mock run, dry run, partial check, or unexecuted plan as a real experimental result.

## Deliverable

Use the [review template](references/review-template.md) when a stable structure would help. Adapt it to the actual project without filling irrelevant sections mechanically. Give the user reviewable conclusions, sources, and decisions; identify concrete blockers when evidence is insufficient.
