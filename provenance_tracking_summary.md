# CDE Provenance Tracking Summary

## Overview
Added comprehensive provenance tracking to the standardized CDE file, enabling full traceability 
from original source values to standardized values.

## New Columns Added

| Column | Purpose | Populated |
|--------|---------|-----------|
| `original_item` | Original field name before renaming | 203 fields |
| `original_values` | Original Values before standardization | 322 fields |
| `value_mapping` | Transform mappings for non-NACC fields | 406 fields |

## Provenance Structure

### NACC Fields (202 total)
- `nacc_variable`: Original NACC field name (e.g., `NPSEX`)
- `nacc_mapping`: Full transform with `to_standard`, `from_standard`, `sentinel_handling`
- `Values`: Preserved original format showing both NACC codes and Path-ND text

Example (sex field):
```json
{
  "to_standard": {"1": "male", "2": "female", "Male": "male", "Female": "female", ...},
  "from_standard": {"male": "1", "female": "2", ...},
  "sentinel_handling": {...}
}
```

### Non-NACC Fields (1,414 total)
- `original_values`: Original values before snake_case standardization
- `value_mapping`: Transform with `to_standard`, `from_standard`, `pattern`
- `Values`: Standardized snake_case format

Example (path_braak_nft field):
```
Original Values: ["0","I","II","III","IV","V","VI","I/II","III/IV","IV/V","V/VI"]
Current Values:  [0, 1, 1.5, 2, 2.5, 3, 3.5, 4, 4.5, 5, 5.5, 6]

value_mapping.to_standard: {"I": "1", "II": "2", "I/II": "1.5", ...}
value_mapping.from_standard: {"1": "I", "2": "II", "1.5": "I/II", ...}
```

## Files Updated
- `cleaned_CDEs_with_provenance.csv`: 1,616 CDEs with full provenance
- `changelog_with_provenance.csv`: 603 entries documenting all changes

## Source Files Used
- Original: `unique_merged_CDEs.txt` (pre-standardization)
- Value mappings: `value_mappings.json` (non-NACC) + `nacc_value_mappings.json` (NACC)

## value_mappings.json Status
This file is now **redundant** - all mappings are captured in the CSV:
- NACC fields: `nacc_mapping` column
- Non-NACC fields: `value_mapping` column

The CSV is now fully self-contained for ETL operations.
