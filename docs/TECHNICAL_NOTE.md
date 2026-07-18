# GenAI Evidence Workbench

## A Local-First Methodology for Reproducible LLM Export Forensics

**Public Capability and Evidence-Boundary Note - Version 0.1.0**

**Hiroki Tamba - Tamba Research Academy**

**ORCID:** 0009-0004-7635-0741

**Release date:** 2026-07-18

## Abstract

GenAI Evidence Workbench is a local-first evidence-engineering methodology for examining large exports of interactions with generative AI systems. It is designed for cases where confidentiality, provenance, reproducibility, and defensible reporting matter more than convenience. The method treats original archives, JSON records, and attachments as read-only evidence; records processing boundaries and exclusions; and separates screening candidates from findings.

This public note fixes the scope and evidentiary claims of version 0.1.0. It describes the evidence contract, safe-stop policy, sanitized aggregate results from a reference case, known source limitations, and the requirements for a controlled reproducibility engagement. It does not publish source exports, conversation text, attachments, honeypot values, proprietary decision logic, thresholds, or production adapters. Consequently, the aggregate candidate counts reported here cannot be independently regenerated from the public deposit alone.

## 1. Purpose and scope

The workbench is intended to support:

- input integrity and chain-of-custody manifests;
- streaming inspection of large ZIP and JSON exports;
- deterministic processing under a fixed implementation and configuration;
- screening for reappearance and cross-conversation lineage candidates;
- explicit handling of missing, duplicate, branched, tool, and system records;
- safe-stop exclusion when content may belong to another person; and
- sanitized reporting using locations, types, counts, and cryptographic hashes instead of sensitive text.

The public repository is a capability and evidence-boundary release. It is not an operational scanner, a public benchmark dataset, or a disclosure of production detection logic.

## 2. Reference case

An offline examination of a large ChatGPT export produced the following audited stages.

| Stage | Count | Public interpretation |
|---|---:|---|
| Messages in the audited input set | 53,203 | Parsed message records under documented internal counting rules |
| Reappearance candidates | 1,091 | Screening records produced after normalization and exclusions |
| Cross-conversation lineage candidates | 219 | Candidate relations spanning distinct conversation identifiers |

The export contained 448 conversations. One additional conversation was excluded under the safe-stop policy after indicators suggested that it might contain another person's data. The excluded conversation's content was not investigated.

The aggregate unit changes between stages. The first stage counts message records, the second counts screening candidate records, and the third counts candidate relations between conversations. These figures must not be read as unique strings, unique conversations, confirmed incidents, or confirmed causal links.

## 3. Evidence contract

The methodology separates evidence preservation from interpretation. A controlled engagement can produce the following artifacts:

1. an input byte-stream manifest with SHA-256 values;
2. a ZIP entry inventory, including complete, partial, excluded, and failed entries;
3. JSON record and schema observations;
4. a ledger linking pre-normalization and post-normalization record identifiers;
5. counts of processed, excluded, safe-stopped, and failed records;
6. candidate registers that do not reproduce sensitive source text; and
7. a deterministic run manifest containing implementation, configuration, environment, and output hashes.

"No unexplained data loss" is therefore a reconciliation claim, not an unconditional promise. It means that the available input bytes, enumerated archive entries, parsed records, transformations, exclusions, failures, and outputs reconcile under the declared rules. It does not mean that missing source bytes were recovered or that an upstream export was complete.

## 4. Normalization and record boundaries

A reproducible examination must declare how it handles:

- character encoding and decoding failures;
- Unicode normalization;
- timestamps, time zones, and missing time-zone information;
- exact duplicates and near-duplicates;
- missing or malformed fields;
- branched conversation graphs;
- user, assistant, tool, and system messages;
- attachment references and unavailable attachment bytes; and
- stable identifiers before and after normalization.

The exact production decision functions and thresholds used to generate candidates are engagement-scoped and are not part of this release. Public disclosure of the evidence contract should not be confused with public disclosure of the detector.

## 5. Known source limitation

The reference archive was truncated. Its ZIP central directory was unavailable, the final local entry was partial, and 2,142,448 compressed bytes were missing. The examination therefore reconciled recoverable complete entries and recorded the partial entry explicitly. It did not claim complete recovery of the original archive.

This limitation is material. Any record count applies to the audited, recoverable input set under the declared rules, not to hypothetical bytes absent from the supplied archive.

## 6. Safe-stop governance

Potential third-party data triggers a safe stop. The examiner does not continue reading the suspected content to improve a classification. The audit record is limited to the minimum identifier, location, type, reason code, and cryptographic hash needed to demonstrate that an exclusion occurred.

Safe-stop is intentionally asymmetric: it preserves uncertainty rather than resolving it through deeper inspection. No conclusion is drawn about the excluded content, its owner, its provenance, or the reason it appeared.

## 7. Candidate status and explicit non-claims

The workbench produces screening candidates. The following conclusions are outside the evidence supplied by textual similarity or metadata alone:

- model training or training-set membership;
- model memorization;
- data leakage or cross-account exposure;
- authorship, identity, or ownership;
- intentional misconduct or wrongdoing; and
- causal lineage between messages or conversations.

A metadata field such as `real_author_id` cannot authenticate identity or ownership without an independently verified account or workspace baseline. Candidate classifications require independent corroboration before they can support a higher-confidence finding.

## 8. Public reproducibility status

This release is reproducible as a fixed public record: the deposited files, release commit, and file hashes can be independently verified. It is not a complete public reproduction package for the reference case because the source archive, sensitive records, production implementation, and decision thresholds are withheld.

A third-party controlled reproduction would require:

- lawful access to an authorized input export;
- a read-only copy with a verified input hash;
- the engagement-scoped implementation and configuration;
- an isolated offline execution environment;
- the counting and exclusion specification;
- a safe-stop authority and escalation route; and
- comparison of run manifests and output hashes.

This distinction prevents a DOI from being misread as proof that every reported aggregate can be regenerated from public materials.

## 9. Provider-neutral evaluation roadmap

The evidence contract can support provider-neutral evaluation of model-assisted review. A future evaluation layer may run synthetic, sanitized, or explicitly authorized benchmark cases against multiple model providers while retaining the deterministic evidence pipeline as the system of record.

Such comparisons should record model and provider identifiers, dates, parameters, prompt hashes, repetition counts, raw-output hashes, agreement rates, abstentions, costs, and latency. Model-assisted judgments remain measurements, not ground truth. This roadmap builds on prior work demonstrating that LLM-as-judge graders can remain non-deterministic even under nominally deterministic settings.

## 10. Availability, license, and responsible use

The public capability repository is available at:

https://github.com/hiroki-tamba-research/GenAI-Evidence-Workbench

The documentation and written material in version 0.1.0 are licensed under Creative Commons Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0), except where otherwise stated. The license does not grant rights to source data, customer data, private implementations, thresholds, adapters, workpapers, trademarks, or other material not included in the release.

Do not use this note to make unsupported allegations about model training, leakage, authorship, identity, or misconduct. High-stakes investigations require appropriate legal, privacy, incident-response, and subject-matter review.

## References

1. Tamba, H. (2026). *Non-determinism in LLM-as-Judge Graders*. Zenodo. https://doi.org/10.5281/zenodo.20674090
2. Tamba, H. GenAI Evidence Workbench public repository. https://github.com/hiroki-tamba-research/GenAI-Evidence-Workbench
3. UK Government. Inspect AI contribution PR 4170. https://github.com/UKGovernmentBEIS/inspect_ai/pull/4170

## Citation

Tamba, Hiroki. (2026). *GenAI Evidence Workbench: A Local-First Methodology for Reproducible LLM Export Forensics* (Version 0.1.0). Tamba Research Academy.
