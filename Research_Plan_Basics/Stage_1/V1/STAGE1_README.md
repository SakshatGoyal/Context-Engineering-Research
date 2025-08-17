===FILE: STAGE1_README.md===
# Stage 1 — Approach to Gathering Data (Master Plan)

## Executive Summary
**Purpose.** Build an interdisciplinary, LLM-era map of “context engineering”—what it is, what adjacent communities call it, how it works, and when/why it works—then translate that into actionable design patterns and evaluation playbooks.

**Payoff.** A shared vocabulary, an evidence-backed framework, and field-tested guidance for practitioners (product, research, data, and design).

**Scope.** 2020–present sources spanning AI/ML, Information Retrieval (IR), HCI, cognitive/behavioral science, data ethics, security/privacy, and industry practice. Evidence types include peer‑reviewed papers, preprints, reputable lab reports/whitepapers, open demos/code, practitioner interviews/surveys, startup case studies, and comparative analyses (labs vs. academic). Stage 1 produces specifications, screening rules, sampling plans, and instruments that Stage 2 consumes directly.

---

## Research Questions (verbatim) → Operational Questions → Intended Evidence
**RQ1.** *How is “context” defined and operationalized across AI/ML, IR, HCI, cognitive/behavioral science, and data ethics (LLM era)?*  
• Operational: Extract formal and informal definitions; identify unit(s) of context (tokens, documents, schemas, tools, memory entries); note operational proxies (e.g., retrieved chunk, system prompt).  
• Evidence: Literature definitions; method sections; evaluation harness descriptions; architecture diagrams; interview claims from academics/practitioners.

**RQ2.** *What terminological variants map to “context engineering” (e.g., RAG, in-context learning, system prompting, memory, long-context optimization, attention steering, tool use, instruction following, guardrails)?*  
• Operational: Build a term crosswalk; record co-occurrence with tasks, models, levers; capture synonyms/antonyms and boundary terms.  
• Evidence: Keywords, taxonomies in papers, lab docs, repos; industry blog terminology; interview/survey vocab.

**RQ3.** *Which context levers (framing, injection, structuring, weighting, boundaries) measurably improve performance, faithfulness, safety, and UX? Under what conditions?*  
• Operational: Identify manipulations and dosage parameters; capture reported effect sizes and confidence; note dataset/task, model, temperature, context length.  
• Evidence: Ablations, A/B tests, controlled experiments, red-teaming, user studies; start‑up case dossiers.

**RQ4.** *How do these levers interact (synergies/trade‑offs) and how sensitive are outcomes to model family, temperature, context length, retrieval quality, or domain?*  
• Operational: Record factorial designs; interactions; sensitivity analyses; error taxonomies; robustness under adversarial content.  
• Evidence: Factorial/blocked studies; multi-model comparisons; robustness and adversarial evaluations; practitioner postmortems.

**RQ5.** *What metrics, experimental designs, and evaluation harnesses can causally attribute gains to context choices (vs. confounds like model size or leakage)?*  
• Operational: Catalog metrics and causal designs; tag leakage controls, blinding, preregistration; identify counterfactual setups and negative controls.  
• Evidence: Methods and appendix details; eval code; prereg and IRB notes; interview descriptions of eval practice.

**RQ6.** *How are labs (OpenAI, Anthropic, Databricks, IBM, others) and startups applying these levers? Which patterns generalize by domain (health, legal, code, support, productivity, data analysis)?*  
• Operational: Extract deployment patterns, guardrails, and operational workflows; map to domains; identify reusable templates.  
• Evidence: Lab/industry whitepapers, product docs, demos, talks; case‑study artifacts; practitioner interviews/surveys.

**RQ7.** *What are the security, privacy, IP, and safety implications of different context strategies (e.g., prompt injection, PII leakage, copyright)?*  
• Operational: Enumerate threat models, risk factors, and mitigations; capture incident reports and red‑team outcomes.  
• Evidence: Security analyses, audits, red-team writeups; policy/standards guidance; legal analyses.

**RQ8.** *What guidelines and guardrails best mitigate these risks without crushing utility?*  
• Operational: Identify governance signals (audits, policy alignment, data governance); record utility–safety trade‑offs and best‑practice recipes.  
• Evidence: Governance frameworks, compliance checklists, lab policies; measurable utility/safety deltas; expert recommendations.

---

## Lever Taxonomy (Primary & Secondary) — Operational Definitions with Examples/Non‑Examples
**Primary Levers**
1. **Framing** — Intent-setting language (system prompts, role, tone) that conditions model behavior without adding external facts.  
   • *Example:* “You are a careful tax analyst…” + instructions clarifying citation style.  
   • *Non‑Example:* Adding retrieved IRS documents (that’s Injection).
2. **Injection (RAG/Memory/Tools/KBs)** — Supplying external information (retrieved chunks, stored memory, tool outputs, structured KBs).  
   • *Example:* Top‑k hybrid retrieval feeding a summarizer.  
   • *Non‑Example:* Reordering already‑present context tokens (that’s Weighting).
3. **Structuring (Schemas/Templates/Workflows/Planners)** — Constraining input/output format and orchestration.  
   • *Example:* JSON schema for output + multi‑step planner calling tools.  
   • *Non‑Example:* Merely increasing context length with no format constraints.
4. **Weighting (Ordering/Repetition/Salience/Reranking)** — Changing token/document prominence (order, duplication, salience markers, scores).  
   • *Example:* Reranking retrieved chunks by cross‑encoder score; repeating critical constraints.  
   • *Non‑Example:* Filtering low‑quality documents out entirely (that’s Selection, under Injection).
5. **Boundaries (Constraints/Scopes/Policies)** — Explicit limits, policy bindings, scopes, and refusal criteria applied via prompt or guard system.  
   • *Example:* Policy‑bound refusal lists; tool‑scope whitelists.  
   • *Non‑Example:* Security scanners running **after** generation (post‑hoc moderation only).

**Secondary Levers**
- **Compression & Distillation** — Summarization, map‑reduce, and elision strategies that compress context while preserving utility.  
- **Temporal Freshness** — Recency cutoffs, re‑crawl cadence, time‑aware retrieval, temporal decay.  
- **Multimodal Context** — Non‑text context (images, audio, tables, diagrams) normalized into model‑usable form.  
- **Security & Integrity** — Prompt‑injection defenses, content signing, provenance chains, sandboxing.  
- **Persistence** — Long‑lived memory stores, session continuity, recall policies.  
- **Governance & Auditability** — Logging, consent, access controls, audit trails, policy alignment.

> **Emergent categories** are permitted (*emergent_* tags) when a repeated, coherent mechanism appears that is not covered above.

---

## Constructs & Variables (with Measurement Notes)
**Independent Variables (manipulations)**  
• Presence/absence of each lever; dosage (e.g., # retrieved chunks k; # repetitions r); position (top/bottom/segmented); format (table/prose/JSON); explicit priority statements; compression ratio; recency cutoff.  
• *Measurement:* Encode as structured parameters; log seed, temperature, max tokens; store retrieval stats (precision/recall, MRR).

**Dependent Variables (outcomes)**  
• Task success; groundedness/faithfulness; factual precision/recall; robustness to adversarial content; user effort/time; satisfaction; token/cost efficiency.  
• *Measurement:* Standard metrics (e.g., EM/F1/precision/recall), groundedness/faithfulness scores, adversarial success rate, SUS/UMUX‑Lite for UX, latency, $/1K tokens.

**Covariates/Controls**  
• Model family/version; temperature; max tokens; domain difficulty; retrieval recall/precision; dataset familiarity.  
• *Measurement:* Record exact model identifiers; document dataset/source overlap checks and leakage controls.

---

## Method Overview & Roles (What Stage 2 Will Collect)
- **Systematic Literature Review:** Harvest, screen, code according to the Stage 1 schema/rubric.  
- **Practitioner Studies:** Semi‑structured interviews and targeted surveys; artifact teardowns (prompts, configs, dashboards).  
- **Experiments:** Factorial/A–B manipulations of levers on representative tasks; causal attribution harnesses.  
- **Case Studies (12–18 startups):** End‑to‑end dossiers.  
- **Comparative Analyses:** Lab vs. academic practice patterns.

**Triggers:**  
• Launch interviews after initial taxonomy saturation (≥60 coded sources).  
• Launch surveys after term crosswalk stabilizes (κ≥0.75 on terminology codes).  
• Launch experiments when at least two strong candidates per lever are identified from lit+practice.

---

## Inclusion/Exclusion Criteria & Credibility Tiers
**Inclusion**  
- Date ≥ 2020‑01‑01; pertains to LLMs or transformer context control.  
- Contains at least one of: lever description, evaluation, method detail, or artifact (prompt/config/code).  
- For grey literature: must include methods and observable evidence (data, code, demo).

**Exclusion**  
- Pure opinion/marketing without methods/evidence.  
- Non‑LLM or non‑context topics (e.g., generic model scaling without context implications).  
- Duplicates/superseded versions (keep latest with strongest evidence).

**Credibility Tiers (1–4)**  
1. **Tier‑1:** Peer‑reviewed top venues; preregistered or audited lab studies with open code/data.  
2. **Tier‑2:** Reputable lab/industry reports with methods + partial openness; major standards bodies.  
3. **Tier‑3:** Detailed practitioner write‑ups/demos with measurements but limited rigor.  
4. **Tier‑4:** Opinion pieces, marketing pages; minimal or no methods.

**Evidence Weighting Guidance**  
- Prefer Tier‑1/2 for causal claims; allow Tier‑3 for hypothesis generation; Tier‑4 only as context/terminology signals. Maintain a mixed‑tier portfolio per lever (see Sampling).

---

## Sampling Strategy (Systematic + Snowball + Stratified + Theoretical)
- **Systematic Search:** Time window 2020‑present; prioritized venues/sources per Stage 1 Search Plan.  
- **Backward/Forward Snowballing:** From anchor works; stop when three consecutive iterations yield <10% new inclusions.  
- **Stratified Purposeful Sampling:** By *lever*, *domain*, *org type*, *credibility tier*.  
- **Theoretical Sampling:** Expand in directions showing novelty (e.g., new defense pattern against injection).  
- **Diversity Quotas (minimums for Stage 2 corpus):**  
  - Per primary lever: ≥40 unique sources each.  
  - Per secondary lever: ≥20 unique sources each.  
  - Domains: ≥10 per major domain (healthcare, legal, code, support, productivity, data analysis).  
  - Org type: ≥30 academic; ≥30 industry labs; ≥30 startups; ≥10 standards/policy.  
  - Per‑org cap: ≤20 items from any single org to reduce dominance.

---

## Screening & Coding Workflow (PRISMA‑style)
1. **Identification:** Collect records from search feeds; de‑dup (DOI/URL/title‑fuzzy/semantic).  
2. **Title/Abstract Screen:** Two reviewers independently; decisions: Pass/Hold/Fail.  
3. **Full‑Text Review:** Extract artifacts; verify lever relevance; record methods/metrics.  
4. **Coding:** Apply schema; ≥20% double‑coded; compute Cohen’s κ per major code family (target κ≥0.75).  
5. **Adjudication:** Resolve disagreements; log rationale and final codes.  
6. **Synthesis Staging:** Validate exports (JSONL/CSV); update dashboards.

---

## Quality Gates
- **Coverage:** Meets diversity quotas and lever minimums.  
- **Credibility Mix:** ≥60% Tier‑1/2 overall; ≥40% Tier‑1/2 per lever.  
- **Schema Validity:** 100% of coded records validate against Stage 1 JSON Schema.  
- **Intercoder Reliability:** κ≥0.75 on *lever_tags*, *methods*, *metrics*, *risk_factors*.  
- **Export Integrity:** JSONL/CSV field orders and null handling per spec; reproducible checksums.  
- **Traceability:** Every claim linked to record IDs and passages/artifacts.

---

## Ethics & Governance (Concrete Do/Don’t)
**Do**  
- Respect IP/TOS; cite sources; store only what’s permitted.  
- Obtain informed consent for interviews; honor NDAs; anonymize practitioner data.  
- Secure storage; role‑based access; redact PII; log access dates and retrieval paths.  
- Preregister experimental protocols when feasible; record leakage checks and risk mitigations.

**Don’t**  
- Don’t scrape behind paywalls or bypass access controls.  
- Don’t store secrets/credentials in datasets or prompts.  
- Don’t share identifiable practitioner quotes without written consent.  
- Don’t publish evaluation artifacts that could enable misuse without appropriate safeguards.

---

## Assumptions & Limitations
- Public artifacts sufficiently represent core practices; some private configs may remain unavailable.  
- Reported metrics can be noisy across labs; we will normalize where possible but avoid over‑aggregation.  
- Model versions/weights evolve rapidly; we will timestamp configurations and access dates.  
- Some domains (e.g., health/legal) impose stronger governance; sampling may skew toward public exemplars.

---

## Versioning & Traceability
- **Semantic Versioning:** `MAJOR.MINOR.PATCH` (e.g., 1.0.0 for Stage 1 release).  
- **Change Log:** Each update lists schema/rubric/search changes and migration notes.  
- **Timestamps:** All records include `access_date`; exports stamped with generation datetime and commit hash.

---

## Discovery Hooks (for Stage 2 exploration; ≤12)
1. Where do compression ratios start to harm groundedness per domain?  
2. Which boundary patterns measurably reduce jailbreak success without lowering task success?  
3. How does retrieval precision vs. recall trade off under strict token budgets?  
4. Do planner‑based structures outperform flat prompts at equal token count?  
5. Are instruction hierarchies more brittle at higher temperatures?  
6. Which recency strategies (decay vs. pinning) best serve news‑sensitive tasks?  
7. Can salience weighting substitute for increased k (dosage) in RAG?  
8. What interaction effects appear between tool use and boundaries?  
9. Which governance signals predict fewer incidents in production?  
10. How does domain difficulty moderate lever efficacy?  
11. What failure modes cluster with long‑context optimization?  
12. Which evaluation harnesses most reliably detect leakage and contamination?

