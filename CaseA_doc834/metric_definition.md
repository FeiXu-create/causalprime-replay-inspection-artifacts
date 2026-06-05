# Metric Definition for Doc 834 Replay Observation

## 1. Scope

This artifact supports the Doc 834 replay observation reported in Chapter 6 Section 6.8.

These metrics are operational observation criteria for case-study replay inspection. They are not statistical tests, semantic correctness scores, or externally validated benchmark metrics.

The purpose of these metrics is to make the replay-observation procedure inspectable at the level of MCU count, relay-backbone preservation, VOID-coordinate retention, and collision-coordinate stability.

Unless exact automated alignment output is included, Backbone Overlap and VOID Coverage values should be read as author-observed structural-coordinate ranges.

## 2. Deposited Output Format Boundary

The deposited output files are preserved as session-level inspection logs rather than strict JSONL files.

Due to backend and output-format differences, some sessions may record T/P5 checklist information as a human-readable preamble, while other sessions may encode comparable T/P5 information inside JSON-compatible records.

The replay comparison does not require byte-level, line-level, or parser-level uniformity across deposited outputs. Pairwise comparison is based on manually reviewed structural coordinates, MCU counts, canonical runtime flags, evidence references, Relay/VOID/Collision distributions, and author-observed structural-coordinate alignment.

The MCU counts reported in `session_config.json` and `comparison_sheet.csv` are the author-recorded registered MCU counts used in Chapter 6 Section 6.8. They should not be inferred by counting all lines or all records in the deposited output files.

## 3. Language Boundary

The source filing is in English. The author-defined extraction procedure used Chinese as the working language for some MCU slot contents.

The JSON-compatible schema elements, field names, and canonical runtime status flags remain aligned with the MCU Typed IR specification. In other words, the structure layer uses English canonical identifiers, while natural-language slot payloads may contain Chinese descriptions.

Replay comparison is not based on surface-language similarity. It is based on structural coordinates, MCU counts, canonical runtime flags, evidence references, Relay/VOID/Collision distributions, and author-observed structural-coordinate alignment.

The use of Chinese as the extraction working language does not imply translation-based semantic evaluation and does not change the inspection boundary of this artifact.

## 4. MCU Count Variance

Baseline session: W1  
Baseline MCU count: 26

Formula:

```text
MCU Count Variance = |session_count - baseline_count| / baseline_count
```

For direct non-baseline pairwise comparison:

```text
Pairwise MCU Count Variance = |count_A - count_B| / max(count_A, count_B)
```

MCU Count Variance measures extraction-density stability. It does not measure semantic correctness or factual accuracy.

## 5. Backbone Overlap

Backbone Overlap measures overlap between verified relay-backbone edges across two sessions.

Operational definition:

```text
Backbone Overlap = shared_backbone_edges / total_backbone_edges
```

Where:

```text
shared_backbone_edges = relay edges observed in both sessions
total_backbone_edges = relay edges observed in either session
```

This corresponds to a union-style denominator, not the edge count of only one session.

Relay edges are aligned using:

```text
source evidence_ref
target evidence_ref
inheritance slot type
```

If exact automated edge alignment was not used, the value is reported as an author-observed structural-coordinate range.

Backbone Overlap is intended to observe preservation of major relay routes. It is not a claim that the generated text is semantically identical across sessions.

## 6. VOID Coverage

VOID Coverage measures whether structural gaps marked by `void_context_flag` remain visible at aligned coordinates across sessions.

Operational definition:

```text
VOID Coverage = consistent_void_coordinates / reference_void_coordinates
```

For baseline comparisons, W1 is used as the reference session. For non-baseline pairwise comparison, the first session listed in the pair is used as the reference unless otherwise noted.

A coordinate is considered aligned when the following tuple matches or is judged structurally equivalent under manual coordinate review:

```text
evidence_ref.source
evidence_ref.offset or paragraph/section coordinate
slot_index
```

VOID Coverage is used to inspect whether unresolved structural gaps remain visible across replay sessions. It does not evaluate whether the underlying claim is legally or factually correct.

## 7. Collision Localization

Collision Localization records whether major conflict coordinates remain stable across sessions.

Allowed labels:

```text
absolute_stable
core_stable
stable
regional_stable
unstable
not_evaluated
```

Interpretation:

- `absolute_stable`: The collision appears at the same local structural coordinate.
- `core_stable`: The same core collision is preserved, although some secondary coordinates may be compressed or omitted.
- `stable`: The collision remains in the same local section or relay neighborhood.
- `regional_stable`: The collision remains in the same broad structural region, but exact local coordinates may shift.
- `unstable`: The collision migrates to an unrelated region or disappears.
- `not_evaluated`: The pair was not evaluated for collision localization.

## 8. Tier Thresholds

| Metric | Tier A | Tier B | Tier C |
|---|---:|---:|---:|
| MCU Count Variance | <= 20% | <= 25% | <= 35% |
| Backbone Overlap | >= 80% | >= 70% | >= 60% |
| VOID Coverage | >= 80% | >= 75% | >= 65% |
| Collision Localization | absolute stable | stable | regional stable |

Boundary failure for Tier C:

```text
Backbone Overlap < 50%
or
VOID Coverage < 55%
```

The tier thresholds are operational criteria used for this case-study replay observation. They are not universal benchmark thresholds.

## 9. Judgment Labels

### PASS

The session pair satisfies the applicable tier-level replay observation thresholds in aggregate.

### STRONG_PASS

The session pair exceeds the applicable tier-level thresholds with strong preservation of core structural observation patterns.

### BOUNDARY_FAILURE

The session falls below Tier C boundary conditions and is not included in the replay-stability claim.

### SELECTIVE_PATH_DRIFT

The session does not satisfy the standard replay-stable threshold, but structural recognition remains active and the observed difference is caused by path-selection shift across candidate chains.

### QUOTA_COMPRESSION

The input contains more admissible MCU candidates than the configured quota or practical extraction budget, causing the session to preserve a selected subset rather than exhaustive coverage.

### NOT_REPLAY_STABLE

The session pair does not satisfy the applicable replay-stability threshold, but it does not necessarily indicate boundary failure unless boundary-failure conditions are met.

## 10. Limitations

The reported Backbone Overlap and VOID Coverage ranges in this package are manually observed structural-coordinate ranges unless otherwise marked. They should be read as inspection records supporting the Chapter 6 case study, not as automated benchmark scores.

This artifact does not claim statistical significance, semantic correctness, ground-truth validation, automated parsing reproducibility, or universal reproducibility. It supports independent inspection of the deposited outputs and the corresponding pairwise replay-observation worksheet.

Exact upstream LLM extraction may not be bit-level reproducible across environments, model versions, runtime settings, or context-boundary conditions.
