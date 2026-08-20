# Louisiana AI Signals — Public Ledger Schema

This document describes the public distribution schema for the **Louisiana AI Signals — Public Ledger**, published by **Louisiana AI Hub, LLC**.

**Dataset ID:** `louisiana-ai-signals-public-ledger`
**Canonical Ledger:** https://louisianaaihub.com/ledger
**Current dataset version:** `2026-08-18-r2`
**Current snapshot date:** `2026-08-18`

The Public Ledger at LouisianaAIHub.com remains the authoritative current system of record.

## Distribution formats

The dataset is distributed in:

* CSV
* JSON

The CSV and the records contained in the JSON use the same 27 record-level fields.

The JSON additionally contains dataset-level metadata outside the `records` array.

## Stable record identifier

### `signal_id`

Stable Louisiana AI Signals record identifier.

Format:

`LAIS-####`

Example:

`LAIS-0150`

The LAIS identifier is persistent and must not be renumbered for GitHub, Hugging Face, downstream analysis, or other approved distributions.

The canonical record URL is derived from this identifier:

`LAIS-0150` → `https://louisianaaihub.com/ledger#lais-0150`

---

# Governed Ledger fields

These fields describe the underlying Public Ledger record.

## `signal_id`

Stable Louisiana AI Signals identifier.

Example: `LAIS-0150`

## `source_date`

Date associated with the source record or documented event.

Format: `YYYY-MM-DD`

Example: `2026-08-18`

## `funding_type`

Louisiana AI Signals classification describing the type of funding, investment, procurement, public finance, or other economic signal represented by the record.

Examples in the current dataset include:

* `Private Capex`
* `Private Contract Value`
* `Public/Institutional Awards`
* `Public Procurement`
* `Local Public Finance`
* `Private Infrastructure-Enabling Investment`

Treat this as a governed classification, not as a substitute for the underlying source.

## `conversion_stage`

Governed stage describing the documented status of the underlying event or commitment.

Examples include:

* `Announced`
* `Approved`
* `Contracted`
* `Committed`
* `Completed`
* `Operational`
* `Adopted`
* `Ratified`
* `Appropriated`
* `Submitted`

Interpret the value together with the record title, source, and other fields.

## `signal_title`

Human-readable Louisiana AI Signals description of the public-record signal.

This field may include material qualifiers or limitations needed to accurately represent what the underlying source establishes.

## `source_url_or_path`

Public source-document or Louisiana AI Hub source-reference location associated with the record.

The field name is retained for schema continuity.

In dataset version `2026-08-18-r2`, Louisiana AI Hub-hosted source locations are expressed as absolute URLs.

Example:

`https://louisianaaihub.com/sources/2026-08-18_Amazon_NorthwestLouisiana_18B_SourceReference.pdf`

This field does not authorize publication of a separate Source Register dataset or preserved source archive.

## `source_type`

Governed description of the source category.

Examples include:

* `Primary (Official)`
* `Primary (Company)`
* `Primary (Company / Wire)`
* `Primary (Official municipal minutes)`

Source-type labels describe the evidence used for the Ledger record and should not be treated as independent factual claims.

## `geography_name`

Geographic area associated with the record as represented in the Public Ledger.

Examples may identify:

* Louisiana;
* a parish;
* multiple parishes;
* a city;
* a project site or campus;
* another documented Louisiana geography.

## `counterparty_name`

Named company, public body, institution, organization, or other counterparty associated with the Ledger record.

Some records may contain multiple counterparties.

## `counterparty_class`

Governed classification of the counterparty or counterparties.

Examples include:

* `Technology Company`
* `Utility/Energy`
* `Public Agency`
* `State Agency`
* `University/Research`
* `Private Infrastructure Operator`
* `Industrial Manufacturer`

## `primary_constraint`

Louisiana AI Signals classification identifying the primary infrastructure, capital, workforce, procurement, or other constraint represented by the record.

Examples include:

* `Power/Grid`
* `Capital`
* `Workforce`
* `Infrastructure`
* `Procurement`

## `amount_usd`

Dollar value associated with the record where applicable.

This field is distributed as text because not every record establishes a numeric monetary amount.

Depending on the record, the value may contain:

* a numeric amount;
* an em dash;
* or a blank value.

Do not assume this field is always numeric.

Use `amount_display`, `amount_usd_floor`, `amount_qualifier`, and `aggregation_role` together when interpreting monetary values.

## `signal_status`

Louisiana AI Signals record status.

Current values include:

* `LOGGED`
* `CORRECTED`

A corrected record remains identified by its original stable LAIS ID.

Consult the authoritative current Ledger for the current status of any record.

## `project_family`

Louisiana AI Signals project-family association where applicable.

This field may be blank when no project-family classification applies.

Project-family association does not turn this repository into a separate project-profile dataset.

## `amount_display`

Human-readable presentation of the monetary amount or monetary context.

This field may retain qualifiers such as:

* `Approximately`
* `More than`
* `Up to`
* `At least`
* `Undisclosed`
* `Not awarded`

Use this field together with the source and other amount fields.

## `amount_usd_floor`

Numeric lower-bound representation where a source-supported floor is applicable.

This field may be blank where:

* no lower bound is established;
* the amount is approximate without an explicit floor;
* the amount is an upper bound;
* no monetary amount is disclosed;
* or the field is otherwise not applicable.

## `amount_qualifier`

Source-sensitive qualifier associated with the monetary value.

Examples include:

* `Approximately`
* `More than`
* `Up to`
* `At least`
* `Exact`
* `Undisclosed`

The qualifier is material to interpretation and should not be discarded when analyzing the amount.

## `aggregation_role`

Governed instruction describing how the amount should be treated in Louisiana AI Signals aggregation.

Examples include treatment such as:

* additive current amount;
* current project amount;
* historical or superseded amount;
* non-additive amount;
* contextual amount;
* contingent threshold;
* no monetary amount;
* excluded from specified rollups.

Do not sum monetary fields without considering `aggregation_role`.

The dataset-level aggregation note also applies.

## `superseded_by`

Stable LAIS identifier of a later record that supersedes this record where applicable.

Example:

`LAIS-0009` may identify `LAIS-0150` as its superseding record.

Blank when no superseding record is identified.

## `supersedes`

Stable LAIS identifier of an earlier record superseded by this record where applicable.

Example:

`LAIS-0150` supersedes `LAIS-0009`.

Blank when the record does not supersede another LAIS record.

## `current_project_scope`

Governed project-scope treatment used by Louisiana AI Signals.

Current values include:

* `Yes`
* `No`
* `Not applicable`

Interpret this field according to the Public Ledger methodology and the individual record context.

---

# Provenance fields

These fields were added to make exported records materially self-identifying when copied, filtered, transformed, or separated from the full distribution package.

They identify the dataset and publisher. They do not add new underlying source facts.

## `publisher_name`

Publisher of the distributed record.

Current value:

`Louisiana AI Hub, LLC`

## `dataset_name`

Formal dataset name.

Current value:

`Louisiana AI Signals — Public Ledger`

## `dataset_version`

Version identifier of the public distribution containing the record.

Current value:

`2026-08-18-r2`

The dataset version identifies the distribution release and is distinct from the stable `signal_id`.

## `canonical_ledger_url`

Canonical authoritative Public Ledger URL.

Current value:

`https://louisianaaihub.com/ledger`

## `canonical_record_url`

Canonical Louisiana AI Hub URL for the individual LAIS record.

Format:

`https://louisianaaihub.com/ledger#lais-####`

Example:

`https://louisianaaihub.com/ledger#lais-0150`

## `citation_and_use_url`

URL for the governing Louisiana AI Hub Citation & Use policy.

Current value:

`https://louisianaaihub.com/citation-use`

---

# JSON dataset-level metadata

The JSON distribution contains a metadata envelope in addition to the `records` array.

Current top-level fields include:

## `dataset_id`

Stable machine-readable dataset identifier.

Current value:

`louisiana-ai-signals-public-ledger`

## `name`

Formal dataset name.

Current value:

`Louisiana AI Signals — Public Ledger`

## `publisher`

Publisher object identifying:

* publisher name;
* publisher URL.

Current publisher:

`Louisiana AI Hub, LLC`

## `canonical_ledger_url`

Canonical authoritative Public Ledger URL.

## `citation_and_use_url`

Governing Citation & Use URL.

## `dataset_version`

Version of the distributed dataset.

## `snapshot_date`

Data snapshot date represented by the distribution.

This is distinct from the date on which a particular file may have been generated or uploaded.

## `generated_from`

Louisiana AI Hub production/reconciliation context from which the export was generated.

This is operational provenance and is not a separate dataset identifier.

## `generated_date`

Date on which the export was generated.

## `record_count`

Number of records in the `records` array.

## `logged_signal_count`

Number of records carrying `LOGGED` status in the snapshot.

## `corrected_record_count`

Number of records carrying `CORRECTED` status in the snapshot.

## `terms_note`

Short system-of-record and distribution-use notice.

## `records`

Array containing the LAIS records described by this schema.

## `aggregation_note`

Dataset-level warning governing interpretation and aggregation of monetary values.

The current note explains that monetary values retain source qualifiers and aggregation roles and that historical, superseded, non-additive, contingent, requested, and unsupported amounts are excluded from the nominal cross-class reference.

Unlike value classes should not be treated as interchangeable.

---

# Missing and non-applicable values

Blank values are meaningful and should not automatically be converted into zero.

Likewise:

* an em dash does not mean zero;
* `Undisclosed` does not mean zero;
* `Not awarded` does not mean zero;
* `Not applicable` is not equivalent to `No`.

Downstream users should preserve these distinctions unless clearly documenting a transformation.

---

# Corrections and supersession

Louisiana AI Signals is designed to preserve historical record continuity.

A later record may supersede an earlier record without deleting or renumbering the earlier LAIS ID.

Use:

* `signal_status`
* `superseded_by`
* `supersedes`
* `aggregation_role`

together when evaluating record history.

For the authoritative current status of any record, consult:

https://louisianaaihub.com/ledger

---

# Distribution integrity

The official public snapshot package includes a machine-readable manifest and `SHA256SUMS.txt`.

SHA-256 values can be used to determine whether a downloaded file matches the official Louisiana AI Hub snapshot.

They do not prevent downstream modification.

For current integrity information, use the manifest and checksum files distributed with the applicable release.

---

# Citation and use

This schema describes the dataset. It does not grant a separate license.

Citation, attribution, republication, redistribution, commercial use, and other reuse are governed by:

https://louisianaaihub.com/citation-use

Repository-specific terms are also provided in:

`TERMS.md`

---

# Authoritative source

LouisianaAIHub.com remains the authoritative current system of record.

**Public Ledger:** https://louisianaaihub.com/ledger

**Citation & Use:** https://louisianaaihub.com/citation-use

**Publisher:** Louisiana AI Hub, LLC

**Website:** https://louisianaaihub.com/
