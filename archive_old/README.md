# Path-ND Common Data Elements (CDEs)

Standardized data element definitions for neurodegenerative disease research, harmonizing fields from NACC, Path-ND, ASAP, SEA-AD, BDR, BDSA, Answer ALS, and PART data.

**Current Version:** See `VERSION` file

## Files

| File | Description |
|------|-------------|
| `pathnd_cdes.csv` | **Primary CDE reference** — standardized field definitions with embedded value mappings |
| `changelog.csv` | Audit trail of all modifications (renames, merges, type changes) |
| `VERSION` | Current schema version (semantic versioning) |
| `archive/` | Original source files (historical reference only) |

> ⚠️ **Important:** Always use `pathnd_cdes.csv` as the source of truth. Files in `archive/` are preserved for provenance but should not be used directly.

## Versioning

This project uses [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`

| Change Type | Version Bump | Examples |
|-------------|--------------|----------|
| **MAJOR** | Breaking changes | Field removed or renamed, type changed, value encoding changed |
| **MINOR** | Backwards-compatible additions | New field added, new source integrated, new enum values |
| **PATCH** | Non-functional fixes | Description typo, documentation clarification, metadata correction |

When citing these CDEs in publications or pinning to a specific version in pipelines, reference the version number from the `VERSION` file.

## Release Process

Batch changes into releases rather than bumping the version on every edit.

### Workflow

1. **Make changes** to `pathnd_cdes.csv`
2. **Log each change** in `changelog.csv` as you go
3. **When ready to release:** bump `VERSION` once based on the most significant change type

### Determining Version Bump

If a release includes multiple change types, use the highest precedence:

```
MAJOR > MINOR > PATCH
```

Example: A release with 3 typo fixes (patch) + 2 new fields (minor) + 1 field rename (major) = **MAJOR** bump

### Release Checklist

- [ ] All changes logged in `changelog.csv`
- [ ] `VERSION` file updated
- [ ] Git tag created (if using version control): `git tag v1.2.0`

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

### Checking Version
```python
with open('VERSION') as f:
    version = f.read().strip()
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
5. Follow the [Release Process](#release-process) when ready to publish changes
