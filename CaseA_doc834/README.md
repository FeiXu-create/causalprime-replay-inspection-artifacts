# CausalPrime Doc 834 Replay Inspection Artifact

This artifact package supports the replay observation reported in Chapter 6 Section 6.8 of the CausalPrime manuscript.

This package is an inspection artifact, not a full executable reproduction pipeline. It supports independent inspection of deposited session-level extraction outputs, session configuration, pairwise comparison records, and metric definitions. It does not claim bit-level reproduction of upstream LLM extraction or independent regeneration of W1-W8 from the source document.

## 1. Contents

```text
artifact/
  README.md
  session_config.json
  metric_definition.md
  comparison_sheet.csv
  deposited_outputs/
    doc834_W1_deposited_output.txt
    doc834_W2_deposited_output.txt
    doc834_W3_deposited_output.txt
    doc834_W4_deposited_output.txt
    doc834_W5_deposited_output.txt
    doc834_W6_deposited_output.txt
    doc834_W7_deposited_output.txt
    doc834_W8_deposited_output.txt
```

This release is a minimal inspection artifact. It does not include strict normalized JSONL streams, edge-list files, VOID-coordinate CSV files, automated alignment scripts, or manual worksheet spreadsheets. Future releases may add these optional inspection materials.

## 2. Document

The replay observation is based on Doc 834 from United States v. Kwok, case number 1:23-cr-00118-AT.

Doc 834 is used as the primary replay case study in the manuscript.

The document is identified in this artifact as:

```text
Doc 834 — Reply Sentencing Memorandum Submitted on Behalf of Miles Guo
```

## 3. Deposited Output Format

The deposited output files preserve the original session-level extraction outputs. They are heterogeneous inspection logs rather than strict JSONL files.

Some sessions may include a T/P5 checklist, quota notes such as `N = 21`, or other human-readable preamble content before JSON-compatible records. Other sessions may encode comparable T/P5 information inside JSON-compatible records.

The artifact supports independent inspection of deposited outputs and pairwise comparison records. It does not support automated JSONL parsing across all sessions or full replay reproduction.

The reported MCU counts are the author-recorded registered MCU counts used in Chapter 6 Section 6.8. They should not be inferred by counting all lines or all records in the deposited output files.

## 4. Language Note

The source filing is in English. The author-defined extraction procedure used Chinese as the working language for some MCU slot contents.

The JSON-compatible schema elements, field names, and canonical runtime status flags remain aligned with the MCU Typed IR specification. The structure layer uses English canonical identifiers, while natural-language slot payloads may contain Chinese descriptions.

Replay comparison in this artifact is not based on surface-language similarity. It is based on structural coordinates, MCU counts, canonical runtime flags, evidence references, Relay/VOID/Collision distributions, and author-observed structural-coordinate alignment.

## 5. Sessions

The artifact includes eight independent replay sessions:

| Session | Tier | Temperature | Role |
|---|---|---:|---|
| W1 | Tier A | 0.0 | Reference topology baseline |
| W2 | Tier A | 0.0 | Near-deterministic replay |
| W3 | Tier A | 0.0 | Near-deterministic replay |
| W4 | Tier B | 0.5 | Moderate perturbation |
| W5 | Tier B | 0.5 | Moderate perturbation |
| W6 | Tier C | 0.8 | High perturbation |
| W7 | Tier C | 0.8 | High perturbation |
| W8 | Tier C | 1.0 | Maximum perturbation |

The normalized deposited-output filenames are:

```text
doc834_W1_deposited_output.txt
doc834_W2_deposited_output.txt
doc834_W3_deposited_output.txt
doc834_W4_deposited_output.txt
doc834_W5_deposited_output.txt
doc834_W6_deposited_output.txt
doc834_W7_deposited_output.txt
doc834_W8_deposited_output.txt
```

Original working filenames may differ from the normalized artifact filenames.

## 6. How to Inspect

1. Open `session_config.json` to see the replay-session configuration and artifact boundary.
2. Open the files in `deposited_outputs/` to inspect the deposited session-level extraction outputs.
3. Open `comparison_sheet.csv` to see pairwise replay-observation results.
4. Open `metric_definition.md` to understand how MCU Count Variance, Backbone Overlap, VOID Coverage, and Collision Localization are interpreted.

The deposited outputs and comparison results should be inspected separately:

- `deposited_outputs/` contains the original session-level extraction outputs preserved for inspection.
- `comparison_sheet.csv` contains pairwise replay-observation judgments and manually observed structural-coordinate ranges.

## 7. Interpretation Boundary

This artifact supports case-study-level replay observation. It does not provide statistical significance, ground-truth validation, semantic correctness scoring, automated JSONL parsing reproducibility, or universal benchmark results.

Backbone Overlap and VOID Coverage may be reported as author-observed structural-coordinate ranges unless exact automated alignment output is included.

The artifact is intended to support independent inspection of the replay observation record. It should not be interpreted as a fully executable reproduction pipeline.

## 8. Reproducibility Status

This package enables independent inspection of the deposited outputs and comparison records.

It does not claim bit-level reproducibility of upstream LLM extraction across environments. Exact replay outputs may vary with model version, runtime environment, context-boundary handling, sampling implementation, and prompt execution details.

Appendix C provides the MCU schema, adapter-facing structural terminology, and replay consistency criteria. It is not the executable extraction prompt used to generate the W1-W8 outputs.

## 9. License and Citation

License: not yet assigned.

Source legal filings are public court records and are not relicensed by this artifact. The deposited outputs and comparison metadata are derived research artifacts generated by the author.

Please cite the associated CausalPrime manuscript when using this artifact.
