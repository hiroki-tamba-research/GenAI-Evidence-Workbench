# GenAI Evidence Workbench

**Local-first evidence engineering for exported LLM interaction data.**

GenAI Evidence Workbench is a consulting-oriented methodology for inspecting large ChatGPT and LLM data exports without sending source material to an API or external AI service. It focuses on reproducibility, evidence boundaries, safe handling, and defensible reporting.

> **Status:** Public capability brief. Raw exports, customer data, proprietary detection logic, thresholds, and production adapters are intentionally not included.

## What it is for

- Export integrity and chain-of-custody manifests
- Streaming inspection of large JSON and ZIP exports
- Deterministic candidate extraction and rerun comparison
- Reappearance-candidate and cross-conversation-lineage review
- Safe-stop handling when data may belong to another person
- Sanitized audit reports containing locations, types, counts, and SHA-256 values instead of sensitive text

## Reference case

An offline examination of a large ChatGPT export produced the following reproducible audit stages:

| Stage | Count | Meaning |
|---|---:|---|
| Messages in the audited input set | 53,203 | Parsed message records under documented counting rules |
| Reappearance candidates | 1,091 | Candidate matches after normalization and exclusion rules |
| Cross-conversation lineage candidates | 219 | Candidate relationships spanning conversation boundaries |

The export contained 448 conversations. One conversation was excluded under the safe-stop policy after indicators suggested that it might contain another person's data; its contents were not investigated.

These figures are **candidate counts**. They do not establish training use, data leakage, model memorization, wrongdoing, or causal provenance.

## Evidence model

The workbench defines **no unexplained data loss** as a verifiable reconciliation, not an unconditional claim. A completed engagement can include:

1. SHA-256 of every input byte stream
2. ZIP entry inventory and per-entry hashes
3. JSON record counts and schema observations
4. Processed, excluded, safe-stopped, and failed counts
5. Before/after normalization identifiers
6. Deterministic rerun manifests and output hashes

Time zones, character encoding, Unicode normalization, duplicates, missing fields, branched conversations, tool/system messages, and attachment references are treated as explicit audit dimensions.

## Operating boundaries

- Offline by default; no source data is sent to an API or external AI
- Original ZIP, JSON, and attachments are read-only inputs
- Sensitive text and honeypot values are not copied into reports
- Suspected third-party data triggers a safe stop
- Findings remain candidates until supported by independent evidence

## Public versus private components

This repository is intentionally a non-operational public overview.

| Public | Kept private or engagement-scoped |
|---|---|
| Architecture and evidence model | Raw exports and attachments |
| Sanitized aggregate examples | Detection rules and thresholds |
| Reporting boundaries | Production parsers and adapters |
| Safe-stop policy | Customer-specific findings |
| Reproducibility requirements | Investigation workpapers |

## Consulting engagements

Typical deliverables include an input manifest, data dictionary, counting-rule specification, exclusion ledger, deterministic run manifest, sanitized findings register, and an executive audit report. Engagements can cover export integrity, internal LLM governance, evaluation reproducibility, insider-risk review, and defensible evidence preparation.

## Research provenance

Maintained by [Hiroki Tamba](https://github.com/hiroki-tamba-research), an independent researcher working on AI evaluation infrastructure, narrative intelligence, and LLM grader reliability.

Selected public evidence:

- [Merged contribution to UK AISI's Inspect evaluation framework (PR #4170)](https://github.com/UKGovernmentBEIS/inspect_ai/pull/4170)
- [ORCID 0009-0004-7635-0741](https://orcid.org/0009-0004-7635-0741)
- [Open Science Framework profile](https://osf.io/rzwtf/)

## License

Except where otherwise noted, the original documentation and written material published in this repository are licensed under the [Creative Commons Attribution-NoDerivatives 4.0 International License (CC BY-ND 4.0)](https://creativecommons.org/licenses/by-nd/4.0/).

You may share the licensed material, including commercially, provided that appropriate attribution is given and the material is distributed unchanged. Adaptation, translation, modification, or redistribution of derivative versions requires prior permission.

This license does **not** grant rights to any source data, customer data, private implementation, detection logic, thresholds, adapters, workpapers, trademarks, or other material not actually included in this repository. Software code, if added later, will carry its own explicit license.

For commercial engagements, collaboration, derivative permissions, or methodology licensing, contact [Hiroki Tamba](https://github.com/hiroki-tamba-research).

## Responsible use

Do not use this material to make unsupported allegations about model training, leakage, authorship, or misconduct. Preserve evidence boundaries, document uncertainty, and obtain appropriate legal or privacy review for high-stakes investigations.
