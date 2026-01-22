# Path-ND Common Data Elements (CDEs)

Standardized data element definitions for neurodegenerative disease research, harmonizing fields from NACC, Path-ND, ASAP, SEA-AD, BDR, BDSA, Answer ALS, and PARTS.

## Files

| File | Description |
|------|-------------|
| `pathnd_cdes.csv` | **Primary CDE reference** — standardized field definitions with embedded value mappings |
| `changelog.csv` | Audit trail of all modifications (renames, merges, type changes) |
| `archive/` | Original source files (historical reference only) |

> ⚠️ **Important:** Always use `pathnd_cdes.csv` as the source of truth. Files in `archive/` are preserved for provenance but should not be used directly.

## CDE Schema

The `pathnd_cdes.csv` contains the following columns:

| Column | Description |
|--------|-------------|
| `Source` | Data source(s), pipe-separated if multiple (e.g., `NACC\|Path-ND`) |
| `Collection` | Logical grouping of related fields |
| `Item` | Standardized field name (snake_case) |
| `Description` | Field definition |
| `ItemType` | Data type (string, numeric, binary, enum) |
| `ItemDescription` | Detailed type specification |
| `Required` | Whether field is required |
| `Values` | Standardized allowed values |
| `Comments` | Implementation notes |
| `AlternateItemNames` | Original field names from source systems |
| `AlternateDescription` | Original descriptions |
| `Priority` | Data priority level |
| `Related_CDEs` | Cross-references to related fields |
| `nacc_mapping` | Original NACC field name (for NACC-sourced fields) |
| `original_values` | Pre-standardization value formats |
| `value_mapping` | Bidirectional value transformations (JSON) |

## Conventions

### Field Names
- All names use `snake_case` (lowercase with underscores)
- Original names preserved in `AlternateItemNames` for traceability
- NACC field names tracked separately in `nacc_mapping` (must match source exactly)

### Value Standardization
- **Booleans:** `true` / `false`
- **Enums:** snake_case (e.g., `none`, `mild`, `moderate`, `severe`)
- **Nulls:** Sentinel values (8, 9, 88, 99, etc.) map to `null` with reason documented

### NACC Fields
NACC field names are **immutable** — they cannot be renamed as they must match source data exactly. Standardization is handled through:
- `nacc_mapping`: Links the clean CDE to the original NACC field name
- `value_mapping`: Documents bidirectional value transformations

## Usage

### Reading the CDE List
```python
import pandas as pd
cdes = pd.read_csv('pathnd_cdes.csv')
```

### Value Transformations
The `value_mapping` column contains JSON with `to_standard` and `from_standard` mappings:
```python
import json
mapping = json.loads(row['value_mapping'])
standardized = mapping['to_standard'].get(original_value)
```

## Changelog

All modifications are logged in `changelog.csv` with:
- Original and new field names/values
- Change type (rename, merge, type_change, value_standardization)
- Source system affected
- Priority changes

## Contributing

When modifying CDEs:
1. Check for existing duplicates across all sources
2. Use standardized naming and value conventions
3. Add entry to `changelog.csv`
4. Never rename NACC fields — use `nacc_mapping` instead