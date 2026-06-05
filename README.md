# CausalPrime Replay Inspection Artifacts

This repository provides supplementary inspection artifacts for the CausalPrime manuscript.

The artifacts support case-study-level replay observations reported in Chapter 6. They are inspection artifacts, not full executable reproduction pipelines.

## Repository Contents

```text
causalprime-replay-inspection-artifacts/
  README.md
  LICENSE_STATUS.md

  caseA_doc834/
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

  caseB_statistical_communique/
    README.md
    session_config.json
    metric_definition.md
    comparison_sheet.csv
    deposited_outputs/
      caseB_W1_deposited_output.txt
      caseB_W2_deposited_output.txt
      caseB_W3_deposited_output.txt
```

## Case A: Doc 834

`caseA_doc834/` contains the primary replay inspection artifact for Doc 834.

It supports the replay observation reported in Chapter 6 Section 6.8 of the manuscript. It includes W1-W8 deposited session-level extraction outputs, session configuration, pairwise comparison records, and metric definitions.

Case A is the primary replay case study in the manuscript.

## Case B: Statistical Communiqué

`caseB_statistical_communique/` contains the reduced secondary cross-domain inspection artifact for Case B.

It supports the reduced replay observation reported in Chapter 6 Section 6.9 of the manuscript. It includes W1-W3 deposited session-level extraction outputs, session configuration, pairwise comparison records, and metric definitions.

Case B is not a full three-tier replay-stability artifact comparable to Doc 834. It is a secondary cross-domain inspection artifact for observing quota-induced path-selection drift in high-density economic statistical text.

## Artifact Boundary

These artifacts support independent inspection of:

```text
deposited session-level extraction outputs
replay-session configuration
pairwise comparison records
metric definitions
author-observed structural-coordinate ranges
```

These artifacts do not claim:

```text
bit-level reproduction of upstream LLM extraction
independent regeneration of replay outputs from source documents
full executable reproduction of the replay pipeline
automated JSONL parsing across all deposited outputs
automated alignment verification
statistical significance
semantic correctness evaluation
ground-truth validation
universal cross-domain generalization
```

## Deposited Output Format

The deposited output files preserve the original session-level extraction outputs.

They are heterogeneous inspection logs rather than strict normalized JSONL streams. Some deposited outputs may contain human-readable checklist notes, T/P5 notes, indicator-chain notes, quota notes, or JSON-compatible records in different formats.

The reported MCU counts in the artifact configuration and comparison sheets are author-recorded registered MCU counts used in the manuscript. They should not be inferred by counting all lines or all records in the deposited output files.

## Language Note

Some deposited outputs use Chinese as the extraction working language while retaining English canonical schema fields and runtime status flags.

Replay comparison is not based on surface-language similarity. It is based on structural coordinates, MCU counts, canonical runtime flags, evidence references, Relay/VOID/Collision distributions, indicator-chain coverage where applicable, and author-observed structural-coordinate alignment.

## Reproducibility Status

This repository enables independent inspection of deposited outputs and comparison records.

It does not provide a full executable reproduction pipeline. It does not claim bit-level reproducibility of upstream LLM extraction across environments. Exact replay outputs may vary with model version, runtime environment, context-boundary handling, sampling implementation, and prompt execution details.

Appendix C of the manuscript provides the MCU schema, adapter-facing structural terminology, and replay consistency criteria. It is not the executable extraction prompt used to generate the deposited replay outputs.

## How to Inspect

1. Open `caseA_doc834/README.md` for the primary Doc 834 artifact.
2. Open `caseB_statistical_communique/README.md` for the reduced Case B artifact.
3. Inspect each case's `session_config.json` for session metadata and artifact boundaries.
4. Inspect each case's `comparison_sheet.csv` for pairwise replay-observation records.
5. Inspect each case's `metric_definition.md` for metric interpretation.
6. Inspect the files under each `deposited_outputs/` directory for the deposited session-level extraction outputs.

## License Status

License: not yet assigned.

See `LICENSE_STATUS.md` for the current licensing boundary.

Source legal filings and public statistical documents are not relicensed by this repository. Deposited outputs and comparison metadata are derived research artifacts generated by the author.

## Citation

Please cite the associated CausalPrime manuscript when using this repository.
