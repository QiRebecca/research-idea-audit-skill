# Research Idea Audit

A reusable Codex skill for evaluating a research idea before investing in a full experimental program. It connects the proposed claim to background, related work, the research gap, contribution, novelty, feasibility, a minimum-cost pilot, and the interpretation of each result.

The skill asks for a coherent research case for the user's review before treating the idea as approved. Its pilot plan prioritizes a credible positive signal at low time, compute, and token cost. Negative results remain attached to the original claim rather than silently changing the idea.

## Install

Clone this repository into your Codex skills directory:

```bash
git clone https://github.com/QiRebecca/research-idea-audit-skill.git ~/.codex/skills/research-idea-audit
```

Invoke it with `$research-idea-audit`, or let Codex select it for a research idea review. The [review template](references/review-template.md) provides a consistent output format.

## License

MIT. See [LICENSE](LICENSE).
