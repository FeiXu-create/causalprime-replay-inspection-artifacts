# Metric Definition for Case B Reduced Replay Observation

## 1. Scope

This artifact supports the reduced secondary cross-domain replay observation reported in Chapter 6 Section 6.9.

Case B is based on the Statistical Communiqué of the People's Republic of China on the 2025 National Economic and Social Development. It is an economic statistical text, not a forensic legal filing.

This artifact is not a full three-tier replay-stability artifact comparable to Doc 834. It contains W1-W3 only and does not include a Tier C high-perturbation layer.

The metrics are operational observation criteria for case-study replay inspection. They are not statistical tests, semantic correctness scores, ground-truth validation metrics, or externally validated benchmark metrics.

## 2. Deposited Output Format Boundary

The deposited output files are preserved as session-level inspection logs rather than strict JSONL files.

Due to backend and output-format differences, sessions may record indicator-chain notes, quota notes, checklist information, or JSON-compatible records in different formats.

The replay comparison does not require byte-level, line-level, or parser-level uniformity across deposited outputs. Pairwise comparison is based on manually reviewed structural coordinates, MCU counts, canonical runtime flags, evidence references, indicator-chain coverage, Relay/VOID/Collision distributions, and author-observed structural-coordinate alignment.

The MCU counts reported in `session_config.json` and `comparison_sheet.csv` are the author-recorded registered MCU counts used in Chapter 6 Section 6.9. They should not be inferred by counting all lines or all records in the deposited output files.

## 3. Language Boundary

The source document is in Chinese. The extraction working language is Chinese.

The JSON-compatible schema elements, field names, and canonical runtime status flags remain aligned with the MCU Typed IR specification. The structure layer uses English canonical identifiers, while natural-language slot payloads may contain Chinese descriptions.

Replay comparison is not based on surface-language similarity. It is based on structural coordinates, MCU counts, canonical runtime flags, evidence references, indicator-chain coverage, Relay/VOID/Collision distributions, and author-observed structural-coordinate alignment.

## 4. MCU Count Variance

Baseline session: W1  
Baseline MCU count: 40

Formula:

```text
MCU Count Variance = |session_count - baseline_count| / baseline_count
```

For W1 vs W2:

```text
|39 - 40| / 40 = 2.5%
```

For W3 vs W1:

```text
|45 - 40| / 40 = 12.5%
```

MCU Count Variance measures extraction-density stability. It does not measure semantic correctness or factual accuracy.

## 5. Backbone Overlap

Backbone Overlap measures overlap between core economic indicator-chain routes across two sessions.

Operational interpretation:

```text
Backbone Overlap = shared_core_indicator_chain_routes / union_of_observed_core_indicator_chain_routes
```

The denominator is a union-style denominator across the compared sessions, not the route count of only one session.

This is an author-observed structural-coordinate range unless exact automated alignment output is included.

In Case B, backbone routes include major economic indicator chains such as GDP and output, population and employment, investment and real estate, industry and energy, consumption and trade, fiscal and financial indicators, science and innovation, livelihood and social security, and ecology or disaster-related indicators.

## 6. VOID Coverage

VOID Coverage measures whether structural gaps or unresolved coordinates remain visible at aligned indicator-chain coordinates across sessions.

Operational interpretation:

```text
VOID Coverage = consistent_void_or_gap_coordinates / reference_void_or_gap_coordinates
```

For baseline comparisons, W1 is used as the reference session.

In Case B, VOID coordinates include statistical-scope gaps, unexplained indicator residuals, missing intermediate explanations, unclosed absolute-value/growth-rate relations, and unresolved annual indicator-chain boundaries.

## 7. Domain-Specific Indicators

### Residual Localization Stability

Residual Localization Stability records whether unresolved or residual coordinates remain visible in the same indicator-chain neighborhood across sessions.

This label records neighborhood-level retention of unresolved indicator-chain residuals rather than exact coordinate identity.

Allowed labels:

```text
stable
partial
unstable
not_evaluated
```

### Temporal Dependency Preservation

Temporal Dependency Preservation records whether annual indicator chains, year-on-year relations, stock-flow relations, or increment-stock dependencies remain structurally visible across replay sessions.

The value may be reported as an author-observed range when exact automated alignment is not included.

This indicator is specific to Case B and is not part of the Doc 834 primary legal-factual replay artifact.

## 8. Tier Interpretation for Case B

Case B uses the same basic replay-observation metric family as Case A, but only as a reduced secondary observation.

| Metric | Tier A | Tier B |
|---|---:|---:|
| MCU Count Variance | <= 20% | <= 25% |
| Backbone Overlap | >= 80% | >= 70% |
| VOID Coverage | >= 80% | >= 75% |
| Temporal Dependency | >= 80% | >= 70% |

Tier C is not performed for Case B.

## 9. Judgment Labels

### PASS

The session pair satisfies the applicable tier-level replay observation thresholds in aggregate.

### NOT_REPLAY_STABLE

The session pair does not satisfy the applicable replay-stability threshold, but it does not necessarily indicate structural recognition collapse.

### SELECTIVE_PATH_DRIFT

The session does not satisfy the standard replay-stable threshold, but structural recognition remains active and the observed difference is caused by path-selection shift across candidate chains.

### QUOTA_COMPRESSION

The input contains more admissible MCU candidates than the configured quota or practical extraction budget, causing the session to preserve a selected subset rather than exhaustive coverage.

## 10. Limitations

The reported Backbone Overlap, VOID Coverage, Residual Localization, and Temporal Dependency values are manually observed structural-coordinate ranges unless otherwise marked.

This artifact does not claim statistical significance, semantic correctness, ground-truth validation, automated parsing reproducibility, full three-tier replay stability, or universal cross-domain generalization.

Case B should be interpreted as a secondary cross-domain inspection artifact showing a domain-specific behavior pattern: quota-induced path-selection drift in high-density economic statistical text.
