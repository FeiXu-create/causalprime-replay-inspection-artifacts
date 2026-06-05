# Case B Reduced Replay Inspection Artifact

This artifact package supports the reduced secondary cross-domain replay observation reported in Chapter 6 Section 6.9 of the CausalPrime manuscript.

Case B is not a full three-tier replay-stability artifact comparable to the Doc 834 primary case study. It supports inspection of a reduced W1-W3 observation over an economic statistical text.

## 1. Contents

```text
artifact/
  README.md
  session_config.json
  metric_definition.md
  comparison_sheet.csv
  deposited_outputs/
    caseB_W1_deposited_output.txt
    caseB_W2_deposited_output.txt
    caseB_W3_deposited_output.txt
```

This release is a minimal secondary inspection artifact. It does not include Tier C replay outputs, strict normalized JSONL streams, edge-list files, VOID-coordinate CSV files, automated alignment scripts, or manual worksheet spreadsheets.

## 2. Document

The replay observation is based on:

```text
Statistical Communiqué of the People's Republic of China on the 2025 National Economic and Social Development
```

The document is used as a secondary cross-domain observation case in Chapter 6 Section 6.9.

## 3. Artifact Boundary

This package is an inspection artifact, not a full executable reproduction pipeline.

It supports independent inspection of deposited W1-W3 session-level extraction outputs, session configuration, pairwise comparison records, and metric definitions.

It does not claim:

```text
full three-tier replay-stability evaluation
Tier C high-perturbation coverage
bit-level reproduction of upstream LLM extraction
independent regeneration of W1-W3 from the source document
automated JSONL parsing across all sessions
automated alignment verification
statistical significance
semantic correctness
ground-truth validation
universal cross-domain generalization
```

## 4. Deposited Output Format

The deposited output files preserve the original session-level extraction outputs. They are heterogeneous inspection logs rather than strict JSONL files.

Some sessions may include indicator-chain notes, quota notes, checklist content, or JSON-compatible records in different formats.

The reported MCU counts are the author-recorded registered MCU counts used in Chapter 6 Section 6.9. They should not be inferred by counting all lines or all records in the deposited output files.

## 5. Language Note

The source document is in Chinese. The extraction working language is Chinese.

The JSON-compatible schema elements, field names, and canonical runtime status flags remain aligned with the MCU Typed IR specification. The structure layer uses English canonical identifiers, while natural-language slot payloads may contain Chinese descriptions.

Replay comparison in this artifact is not based on surface-language similarity. It is based on structural coordinates, MCU counts, canonical runtime flags, evidence references, indicator-chain coverage, Relay/VOID/Collision distributions, and author-observed structural-coordinate alignment.

## 6. Sessions

| Session | Tier | Temperature | Role |
|---|---|---:|---|
| W1 | Tier A | 0.0 | Reference topology baseline |
| W2 | Tier A | 0.0 | Near-deterministic replay sample |
| W3 | Tier B | 0.5 | Moderate-perturbation observation sample |

The normalized deposited-output filenames are:

```text
caseB_W1_deposited_output.txt
caseB_W2_deposited_output.txt
caseB_W3_deposited_output.txt
```

## 7. How to Inspect

1. Open `session_config.json` to see the replay-session configuration and artifact boundary.
2. Open the files in `deposited_outputs/` to inspect the deposited session-level extraction outputs.
3. Open `comparison_sheet.csv` to see pairwise replay-observation results.
4. Open `metric_definition.md` to understand how the Case B metrics are interpreted.

The deposited outputs and comparison results should be inspected separately:

- `deposited_outputs/` contains the original session-level extraction outputs preserved for inspection.
- `comparison_sheet.csv` contains pairwise replay-observation judgments and manually observed structural-coordinate ranges.

## 8. Interpretation Boundary

This artifact supports case-study-level secondary replay observation. It does not provide statistical significance, ground-truth validation, semantic correctness scoring, automated JSONL parsing reproducibility, full three-tier replay stability, or universal benchmark results.

Case B should be interpreted as an inspection record of a domain-specific behavior pattern under reduced replay conditions: quota-induced path-selection drift in high-density economic statistical text.

## 9. Reproducibility Status

This package enables independent inspection of the deposited outputs and comparison records.

It does not claim bit-level reproducibility of upstream LLM extraction across environments. Exact replay outputs may vary with model version, runtime environment, context-boundary handling, sampling implementation, and prompt execution details.

Appendix C provides the MCU schema, adapter-facing structural terminology, and replay consistency criteria. It is not the executable extraction prompt used to generate the W1-W3 outputs.

## 10. License and Citation

License: not yet assigned.

The source document is a public statistical communiqué and is not relicensed by this artifact. The deposited outputs and comparison metadata are derived research artifacts generated by the author.

Please cite the associated CausalPrime manuscript when using this artifact.
