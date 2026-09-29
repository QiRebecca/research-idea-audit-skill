# Research Idea Review Template

Complete only the sections relevant to the current stage. Mark missing information **not checked**, **not run**, or **not applicable**, with a reason. Do not guess. Each source should directly support the claim beside it.

## A. Research case for user review

- **Version and status:** Date, idea version, proposed / user-approved / frozen.
- **One-sentence claim:** Under what conditions should which mechanism cause which observable change?
- **Background:** Problem, current approaches, setting, and significance.
- **Related work:** Closest studies, their actual contributions and evidential limits, and primary sources.
- **Research gap:** The gap derived from existing work and the finding that would invalidate it.
- **Meaning:** Scientific significance and practical value if the claim holds.
- **Idea:** Mechanism, necessary assumptions, scope, and failure modes.
- **Contribution:** Each proposed contribution ↔ the evidence needed to support it; identify unverified claims.
- **Story:** Background → gap → central question → mechanism → prediction → evidence → contribution.

### Link experiments to the claim

| Experiment | Precise purpose | Claim or mechanism tested | Discriminating prediction | Data and difficulty | Essential control | Metric and decision rule | Confounders | What it can and cannot establish |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

**Decision for the user's review:** Keep or revise the claim; identify any weak connection among background, gap, contribution, and experiments.

## B. Novelty and feasibility

### Increment over the closest work

| Study and primary source | What it actually proposed or established | Overlap | Smallest distinct increment | Evidence needed for that increment | Strongest novelty objection |
| --- | --- | --- | --- | --- | --- |

**Novelty judgment:** Sufficient / borderline / insufficient / undetermined; reasons and sources still to check. Describe prior contributions accurately.

### Data and implementation fit

| Data or code and source | Actual format, fields, labels, and splits | Experiment requirement served | Missing or mismatched elements | Access conditions and difficulty | Cost and risk |
| --- | --- | --- | --- | --- | --- |

**Theory chain:** Assumptions → mechanism → prediction. Identify the steps backed by theory or prior evidence and those supported only by intuition.

**Feasibility judgment:** Ready for a minimal pilot / resolve a specific gap first / currently infeasible; evidence that would change the judgment.

## C. Minimum-cost pre-experiment plan (before execution)

- **Original claim and prediction to test:**
- **Cheapest design with discriminating power:** Data slice, treatment, necessary baseline or control, and repetition or pairing.
- **Prespecified primary metric and decision rules:** Positive signal, no signal, failure, and continuation.
- **Reproducibility:** Applicable data, code, model, prompt, seed, and evaluator versions.
- **Information boundary and fairness:** Leakage, comparable controls, and evaluation protocol.
- **Budget and stop rule:** Time, compute, calls or tokens, and number of runs.
- **Interpretation by outcome:** How each possible result would support or weaken the idea; unresolved alternatives.
- **Status:** Plan only / authorized to execute / executed.

## D. Result of one experiment, interpreted against the idea

- **Run ID and provenance:** Plan version, time, configuration, and location of raw records.
- **Protocol deviations:** What changed and whether it affects interpretation.
- **Result:** Primary metrics, effect size, uncertainty, failures or missing data, and actual cost.
- **Conclusion about the original claim:** Supports / partly supports / does not support / inconclusive; identify the prediction and logical link.
- **Alternative explanations and limits:** What remains unresolved and what cannot be claimed.
- **Next decision:** Continue / repair and rerun / pause / stop; reason and incremental cost.
- **Idea revision log:** If a new claim is proposed, give it a new version and repeat the review. Preserve the original claim and results.
