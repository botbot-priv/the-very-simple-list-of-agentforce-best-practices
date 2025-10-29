# Design Patterns

Reusable solutions and gotchas for Agentforce architecture. Each entry follows a simple template: **Intent → Context → Forces → Solution → Trade-offs → Anti-patterns → Metrics**.

---

## Pattern: Flex Credit Governance Guideline (link-out)

**Intent**  
Keep Agentforce costs predictable and aligned to value.

**Reference**  
- [Agentforce Flex Credit Governance Guideline](https://github.com/botbot-priv/botbot-priv.github.io/blob/master/agentforce-flex-credit-governance-guideline.md)

---

## Pattern: Narrow, Curated Knowledge beats “Index Everything”

**Intent**  
Improve answer quality and reduce costs by scoping retrieval to a **small, curated** knowledge set aligned to a **specific question set**.

**Context**  
Teams often ask: *“Can we just give an Agent access to all enterprise knowledge and let AI answer anything?”*

**Forces**  
- **Quality**: stale, unreviewed docs create noise and hallucinations.  
- **Cost**: wide recall → more tokens → higher flex credit burn.  
- **Latency**: larger search space slows response.  
- **Governance**: access control and provenance get messy at scale.

**Solution**  
- **Be specific. Frame the challenge.**  
  *Example:* “Answer our 10 most-asked customer questions, at the right time, using relevant knowledge.”
- Start with **small, curated** sets (e.g., one FAQ object) over giant unreviewed corpora.
- Add **pre-/post-filters** (metadata, recency, role) before/after retrieval.
- Expand scope **incrementally** only when quality data and ownership exist.

**What Works** ✅  
- Focused use-case → scoped corpus.  
- Curated sources with owners and recency.  
- Guardrails + filters to control recall.

**What Breaks** ⚠️  
- Treating the Agent as an all-knowing oracle.  
- Ingesting massive, unreviewed, unstructured data.  
- Skipping pre/post filtering.

**Trade-offs**  
- Narrow scope may miss edge cases (mitigate via escalation to human or secondary search).  
- Requires content ownership and hygiene (but that’s a feature, not a bug).

**Metrics**  
- **Answer accuracy** on top-N intents.  
- **Cost per resolved question** (credits per answer).  
- **Coverage** of FAQs without human fallback.  
- **Time-to-answer** (p50/p95).

**Guiding Principle** 📌  
If you wouldn’t train a human on that messy knowledge base, don’t expect an AI Agent to succeed either.
