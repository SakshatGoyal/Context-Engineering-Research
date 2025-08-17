===FILE: STAGE1_INSTRUMENTS_AND_TEMPLATES.md===
# Stage 1 Instruments & Templates (Execution Library)

---

## PRISMA Flow Template (Stages & Decisions)
**Identification**  
- Records identified through database searches: ______  
- Additional records identified through other sources (labs/startups/standards): ______  
- Duplicates removed: ______

**Screening**  
- Records screened (title/abstract): ______  
- Records excluded (with reasons): ______

**Eligibility**  
- Full-text articles assessed: ______  
- Full-text articles excluded (with reasons): ______

**Inclusion**  
- Studies included in qualitative synthesis: ______  
- Studies included in quantitative synthesis (if applicable): ______

---

## Screening Form (Mirrors Rubric)
**Record ID:** CTX-YYYY-XXXXXX  
**Title:** __________________________  
**URL:** __________________________  
**Year:** ____   **Artifact Type:** (paper/blog/whitepaper/documentation/demo/slide/video/dataset/github_readme/report)  
**Org Type:** (academic_lab/industry_lab/startup/standards_body/government/nonprofit/community_project/media/independent_researcher)

**Decision:** ☐ Pass ☐ Hold ☐ Fail

**Auto‑Exclude Checks**  
- ☐ DateTooOld (year < 2020)  
- ☐ NonContextTopic (no context‑related terms)  
- ☐ OpinionOnly (no methods/metrics)

**Auto‑Include Checks**  
- ☐ TopVenueWithAblation (top venue + ablations)  
- ☐ ReputableLabWithEval (lab report + evaluation)

**Human‑Review Triggers**  
- ☐ GreyLitWithEvidence  
- ☐ AmbiguousTerminology

**Reason(s) & Notes:**  
____________________________________________________________________

---

## Coding Sheet (Mirrors `source_record_schema`)
**id:** CTX-YYYY-XXXXXX  
**title:** __________________________________  
**year:** ____  
**venue_or_publisher:** _____________________  
**org_name:** _______________________________  
**org_type:** academic_lab | industry_lab | startup | standards_body | government | nonprofit | community_project | media | independent_researcher  
**url:** ____________________________________  
**access_date (YYYY-MM-DD):** _____________

**domains (multi):**  
- ai_ml ☐  information_retrieval ☐  hci ☐  cognitive_science ☐  behavioral_science ☐  
- data_ethics ☐  security_privacy ☐  software_engineering ☐  nlp ☐  vision ☐  multimodal ☐  
- legal ☐  healthcare ☐  code ☐  customer_support ☐  productivity ☐  data_analysis ☐  
- finance ☐  education ☐  policy_governance ☐

**lever_tags (multi):**  
- Primary: framing ☐  injection ☐  structuring ☐  weighting ☐  boundaries ☐  
- Secondary: compression_distillation ☐  temporal_freshness ☐  multimodal_context ☐  security_integrity ☐  persistence ☐  governance_auditability ☐  
- Emergent: emergent_________________ , emergent_________________

**terminology (list):** ___________________________________________

**methods (multi):** theoretical ☐ controlled_experiment ☐ ablation_study ☐ observational_study ☐ case_study ☐ user_study ☐ survey ☐ interview ☐ benchmark_evaluation ☐ simulation ☐ system_description ☐ red_team ☐ security_analysis ☐ audit ☐ emergent_method_________

**datasets_or_tasks (list):** _____________________________________

**metrics (multi):** accuracy ☐ precision ☐ recall ☐ f1 ☐ exact_match ☐ rouge ☐ bleu ☐ bertscore ☐ faithfulness ☐ groundedness ☐ helpfulness ☐ toxicity ☐ harmlessness ☐ satisfaction ☐ latency ☐ cost_tokens ☐ throughput ☐ robustness ☐ adversarial_success_rate ☐ calibration ☐ win_rate ☐ metric_________

**claims_primary (bullets):**  
- _________________________________________________________________  
- _________________________________________________________________

**claims_limitations (bullets):**  
- _________________________________________________________________  
- _________________________________________________________________

**evidence_strength:** level → causal_strong | causal_moderate | associational | anecdotal | speculative  
**evidence_strength.rationale:** __________________________________

**credibility_tier (1–4):** __

**task_domain:** healthcare | legal | code | customer_support | productivity | data_analysis | education | finance | security | policy | general | science | software_dev

**retrieval_or_memory_strategy (multi):** bm25 ☐ vector ☐ hybrid ☐ memory_key_value ☐ tool_augmented ☐ structured_kb ☐ graph ☐ none ☐ long_context ☐ sliding_window ☐ summarization_memory ☐ episodic_memory ☐ semantic_routing ☐ rerankers ☐ other_________

**risk_factors (multi):** prompt_injection ☐ test_traces_leakage ☐ pii_exposure ☐ ip_copyright ☐ jailbreak_vuln ☐ data_poisoning ☐ privacy_attack ☐ security_misconfiguration ☐ bias_fairness ☐ safety ☐ overreliance ☐ hallucination ☐ misuse ☐ model_inversion ☐ membership_inference ☐ model_drift ☐ goodharts_law ☐ eval_leakage ☐ emergent_risk_________

**governance_signals (multi):** open_source_repo ☐ released_dataset ☐ eval_code_open ☐ irb_approved ☐ preregistered ☐ third_party_audit ☐ red_team ☐ policy_alignment ☐ data_governance ☐ security_assessment ☐ usage_analytics ☐ pseudonymized ☐ pii_minimization ☐ consent_obtained ☐ nda ☐ none ☐ emergent_gov_________

**artifact_type:** paper | blog | whitepaper | documentation | demo | slide | video | dataset | github_readme | report

**notes:** _________________________________________________________  
**tags_freeform (list):** __________________________________________

---

## Interview Guide (Semi‑Structured)
**Consent & Anonymization**  
- ☐ Verbal consent recorded  ☐ Written consent stored  ☐ Anonymize quotes  ☐ NDA in place (if applicable)

**Participant Profile (role, org, domain):** _______________________

**Topics & Prompts**
1. **Current Use of Context Levers**  
   - Walk me through how you prepare context for your top task(s).  
   - Which levers (framing, injection, structuring, weighting, boundaries) do you rely on? Why?
2. **Evaluation Practices**  
   - How do you know a context change helped? What metrics/harnesses do you use?  
   - Any controls for leakage or confounds?
3. **Failure Modes & Risks**  
   - Memorable failures (e.g., injection, hallucination, jailbreak)?  
   - What mitigations worked or failed?
4. **Governance & Operations**  
   - What governance signals (audits, logs, consent) do you maintain?  
   - Data access, retention, and redaction policies?
5. **Decision Criteria & Trade‑offs**  
   - How do you trade cost/latency vs. groundedness/quality?  
   - What breaks first under scale (more users, more docs)?
6. **Artifacts Review (Teardown)**  
   - Prompts/templates/schemas; retrieval configs; guardrail policies.  
   - Can we capture sanitized examples?

**Close**  
- If you could change one thing about your context pipeline, what would it be?  
- May we follow up and attribute anonymously?

---

## Survey Item Bank (Likert + Free‑Text)
**Demographics & Role**  
- Role: ML Eng ☐  Data Scientist ☐  AI Designer ☐  PM ☐  Security/Privacy ☐  Other: ______  
- Org Type: Academic ☐ Industry Lab ☐ Startup ☐ Other ______  
- Domain: Healthcare ☐ Legal ☐ Code ☐ Support ☐ Productivity ☐ Data Analysis ☐ Other ______

**Lever Usage (1=Never … 5=Always)**  
- I use **Framing** (system/role prompts) to guide outputs. 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- I use **Injection** (RAG/memory/tools) in production. 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- I use **Structuring** (schemas/templates/workflows). 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- I use **Weighting** (ordering/repetition/salience/reranking). 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- I use **Boundaries** (policies/refusals/tool scopes). 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐

**Efficacy (Δ vs. baseline, 1=Much worse … 5=Much better)**  
- Framing → task success: 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- Injection → groundedness/faithfulness: 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- Structuring → user effort/time: 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- Weighting → robustness: 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- Boundaries → safety without utility loss: 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐

**Evaluation & Risk**  
- We run **ablations** for context changes. 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- We check **leakage/contamination** in evaluations. 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐  
- We log **governance signals** (audits, consent, access). 1 ☐ 2 ☐ 3 ☐ 4 ☐ 5 ☐

**Free‑Text**  
- Most effective context pattern you’ve used: __________________________  
- Largest failure mode and how you fixed it: __________________________  
- One artifact you can share (sanitized): _____________________________

---

## Case‑Study Dossier Template
**Case ID:** CS‑____  
**Company/Org (anonymized if needed):** __________  
**Domain:** healthcare | legal | code | support | productivity | data_analysis | other  
**Problem Statement:** ____________________________________________  
**Model(s) & Settings (family/version/temperature/max tokens):** _____  
**Levers Used (with parameters):**  
- Framing: __________________________________  
- Injection: __________________________________  
- Structuring: ________________________________  
- Weighting: __________________________________  
- Boundaries: _________________________________  
**Secondary Levers:** compression_distillation ☐ temporal_freshness ☐ multimodal_context ☐ security_integrity ☐ persistence ☐ governance_auditability ☐  
**Evaluation Harness & Metrics:** _________________________________  
**Results (with deltas & CIs if available):** _______________________  
**UX/Ops (latency, cost, reliability):** ___________________________  
**Risks & Mitigations:** __________________________________________  
**Governance Signals Present:** ____________________________________  
**Generalizability Notes:** _______________________________________  
**Artifacts (links or embedded):** _________________________________

---

## Risk Register Template
| Risk Factor            | Context of Occurrence | Likelihood (L/M/H) | Impact (L/M/H) | Mitigations (Boundaries/Tech/Process) | Owner | Status |
|------------------------|-----------------------|--------------------|----------------|---------------------------------------|-------|--------|
| prompt_injection       |                       |                    |                |                                       |       |        |
| eval_leakage           |                       |                    |                |                                       |       |        |
| pii_exposure           |                       |                    |                |                                       |       |        |
| ip_copyright           |                       |                    |                |                                       |       |        |
| jailbreak_vuln         |                       |                    |                |                                       |       |        |
| model_drift            |                       |                    |                |                                       |       |        |
| goodharts_law          |                       |                    |                |                                       |       |        |

---

## Quality Gates Checklist (Stage 2 Exit)
- ☐ Coverage quotas met (per lever, domain, org type).  
- ☐ Credibility mix met (≥60% Tier‑1/2 overall; ≥40% per lever).  
- ☐ Schema validation: 100% pass.  
- ☐ Intercoder reliability: κ≥0.75 on core fields.  
- ☐ Export integrity: JSONL/CSV match spec; checksums recorded.  
- ☐ Traceability: All claims linked to record IDs and artifacts.  
- ☐ Ethics: PII redacted; consents stored; NDAs honored.  
- ☐ Risk register updated with mitigations.

---

## Assumption Log
| Assumption | Rationale | Impact if Wrong | Test Plan | Status |
|-----------|-----------|-----------------|-----------|--------|
|           |           |                 |           |        |

---

## Future Experiment Skeletons (Do Not Run in Stage 1)
**A. Factorial (2×2) — Injection (k ∈ {5, 20}) × Weighting (rerank ∈ {off, on})**  
- **Task:** Multi‑doc QA (domain: support).  
- **Model Settings:** family/version/temperature/max tokens fixed and recorded.  
- **Manipulations:**  
  - k ∈ {5, 20}; rerank ∈ {off, on}.  
- **Outcomes:** EM, faithfulness, latency, cost_tokens, adversarial_success_rate.  
- **Design Controls:** Random seed, cross‑fold document splits, leakage check via doc hash.  
- **Analysis:** Two‑way ANOVA; interaction effect; Holm correction.

**B. A/B — Boundaries Template v1 vs v2**  
- **Task:** Legal compliance Q&A.  
- **Primary Metric:** adversarial_success_rate (lower is better).  
- **Guardrails:** Refusal templates; tool scope whitelist.  
- **Analysis:** Two‑proportion z‑test with sequential monitoring; report effect size + 95% CI.

**C. Planner vs. Flat Structuring**  
- **Task:** Code refactoring with tool use.  
- **Primary Metric:** win_rate (pairwise human preference).  
- **Controls:** Same retrieval, same token budget; blinded raters; randomization over prompts.

---
