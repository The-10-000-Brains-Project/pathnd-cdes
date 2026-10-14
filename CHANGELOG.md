# Changelog: pathnd-schema

Rebuilt by Forge from the saved versions. Newest first.

## v5.1.0 (2026-10-14)

Version v5.0.0 → v5.1.0 (minor).

**Summary:** Published snapshot

- Added fields: `prod_bucket`

## v5.0.0 (2026-10-14)

Version v4.1.0 → v5.0.0 (major).

**Summary:** Published snapshot

- Removed fields: `prod_bucket`

## v4.1.0 (2026-10-14)

Version v4.0.0 → v4.1.0 (minor).

**Summary:** Published snapshot

- Added fields: `disease_duration`, `duration_of_dementia`

## v4.0.0 (2026-10-14)

Version v3.0.0 → v4.0.0 (major).

**Summary:** Reference table 'diagnosis' updated to v4

- `primary_dx`: value set diagnosis v2 → v4: added `FTD_MND`, `FTLD_FUS`, `FTLD_U`, `MND`; removed `PDD_GEN`, `PD_GEN`

## v3.0.0 (2026-10-14)

Version v2.0.2 → v3.0.0 (major).

**Summary:** Published snapshot

- Added fields: `genetics_dx`, `prod_bucket`, `staging_bucket`
- `age`: required Yes → No
- `postmortem_interval_hours`: allowed values added `0-150`

## v2.0.2 (2026-10-13)

Version v2.0.1 → v2.0.2 (patch).

**Summary:** Published snapshot

- `autopsy_dx`: value set added: (unresolved value set)
- `brain_region`: multiple values No → Yes; allowed values added `AG`, `AMG`, `ANT`, `BF`, `BG`, `CBL`, `CC`, `CERV`, `CING`, `CLAUS`, `CN`, `CP`, `Cuneus`, `DLPFC`, `DM`, `DN`, `DOR`, `DRG`, `FL`, `FuG`, `GP`, `HIP`, `HTH`, `IFG`, `IFOG`, `INF`, `INS`, `IPL`, `ITG`, `L`, `LAT`, `LGN`, `LUMB`, `MB`, `MEC`, `MED`, `MEDL`, `MFG`, `MGN`, `MID`, `MTG`, `MamB`, `NAc`, `NBM`, `OL`, `OT`, `PHG`, `PIT`, `PL`, `PNG`, `PON`, `POST`, `PStrC`, `PoCG`, `PrCG`, `Pulv`, `Put`, `R`, `SAC`, `SC`, `SFG`, `SMG`, `SPL`, `STG`, `STN`, `SUP`, `StrC`, `TH`, `THOR`, `TL`, `VEN`, `Vermis`; value set added: brain_regions
- `movement_disorder_diagnosis`: value set added: (unresolved value set)
- `primary_dx`: allowed values added `AD`, `AD_HIGH`, `AD_INT`, `AD_LOW`, `AGD`, `APKM`, `ARTAG`, `ATAX`, `BvFTD`, `CBD`, `CBS`, `CHORA`, `CP`, `CTE`, `CTRL`, `CVD_ATHERO`, `CVD_CAA`, `CVD_HYALINE`, `DEM_NOS`, `DIP`, `DLB`, `DS`, `DYS`, `ET`, `FRDA`, `FTD`, `FTLD_MND_TDP43`, `FTLD_TAU_AGD`, `FTLD_TAU_MAPT`, `FTLD_TAU_PICKS`, `FTLD_TDP43_A`, `FTLD_TDP43_B`, `FTLD_TDP43_C`, `FTLD_TDP43_D`, `FTLD_TDP43_E`, `FXT`, `GGT`, `HD`, `LATE`, `LBD_NOS`, `MND_ALS_TDP43`, `MSA_C`, `MSA_FTLD`, `MSA_MC`, `MSA_NOS`, `MSA_OPCA_SND`, `MSA_P`, `MSA_SND_OPCA`, `MSA_SND_OPCA_EQ`, `MYO`, `NO_PATH`, `NPH`, `OTHER_ND`, `PAF`, `PART`, `PCA`, `PD`, `PDD`, `PDD_GEN`, `PD_GEN`, `PKM`, `PLMD`, `PPA`, `PRION_NOS`, `PSP`, `RLS`, `SCA_NOS`, `TD`, `TIC`, `TS`, `VP`, `WD`; value set added: diagnosis
- `stain_type`: multiple values No → Yes

## v2.0.1 (2026-10-12)

Version v2.0.0 → v2.0.1 (patch).

**Summary:** Pre-publish snapshot

- `age`: required No → Yes
- `age_at_death`: required unset → Yes
- `autopsy_dx`: required unset → Yes
- `brain_region`: required No → Yes
- `institution`: required unset → Yes
- `slice_hemisphere`: required unset → Yes

## v2.0.0 (2026-10-12)

Version v1.0.0 → v2.0.0 (major).

**Summary:** Pre-publish snapshot

- No changes to fields or rules

## v1.0.0 (2026-09-15)

First saved version.

**Summary:** Initial creation via workspace publish

- 87 fields: `agd_score`, `age`, `age_at_death`, `apoe_status`, `artag_extent`, `arteriolosclerosis_severity`, `autopsy_dx`, `autopsy_finding_1`, `autopsy_finding_2`, `autopsy_finding_3`, `autopsy_finding_4`, `banked_brain_fixed`, `banked_brain_frozen`, `banked_cerebellum_dna`, `banked_paraffin_blocks`, `birth_date`, `brain_bank_id`, `brain_region`, `brain_weight_grams`, `cause_of_death`, `center_of_sequencing`, `cerebral_amyloid_angiopathy_any`, `cerebral_amyloid_angiopathy_lm_severity`, `cerebral_amyloid_angiopathy_p_severity`, `circle_of_willis_atherosclerosis_severity`, `cog_status`, `date_donated`, `date_fixed_blocks_processed`, `date_hist_staining_completed`, `date_of_birth_unix`, `date_of_death`, `date_of_fixed_dissection`, `date_of_primary_hist_review`, `dementia_at_death`, `diagnosis_report_date`, `education_years`, `ethnicity`, `father_dementia_type`, `genetics_screening`, `genotyping_chip`, `half_brain_weight_grams`, `hemorrhages_present`, `highest_level_of_education`, `hippocampal_sclerosis`, `infarcts_present`, `institution`, `last_casi_score`, `late_tdp43_score`, `marital_status`, `maternal_diagnosis`, `microbleeds_present`, `microinfarcts_present`, `mother_dementia_type`, `movement_disorder_diagnosis`, `nia_aa_adnc_score`, `other_case_identifiers`, `participant_id`, `paternal_diagnosis`, `path_braak_alpha_synuclein_stage`, `path_braak_neurofibrillary_tangle_stage`, `path_cerad`, `path_infarcts`, `path_mckeith`, `path_nia_aa_a`, `path_nia_aa_b`, `path_nia_aa_c`, `path_nia_ri`, `path_substantia_nigra_neuronal_loss`, `path_thal`, `path_usslbd`, `postmortem_interval_hours`, `primary_dx`, `race`, `scanner_manufacturer`, `scanner_model`, `scanner_objective_magnification`, `seizures`, `sex`, `sibling_diagnosis`, `slice_hemisphere`, `slice_orientation`, `slice_thickness`, `slide_paths`, `stain_type`, `study`, `uds_dementia_status`, `vascular_pathology_severity`
