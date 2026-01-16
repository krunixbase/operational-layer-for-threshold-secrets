# Secret Manifest

The secret manifest is the authoritative, human-readable record
describing a threshold-protected secret and its operational context.

It defines **what exists**, **who is responsible**, and **how the secret
is expected to be handled**, without containing the secret itself.

---

## Purpose

The manifest exists to:

- provide a single source of truth for a secret
- bind cryptographic parameters to operational responsibility
- enable audit and accountability
- prevent ambiguity or implicit assumptions

The manifest is not a runtime artifact.

---

## Scope

The manifest applies to:

- threshold-based secret sharing systems
- any cryptographic scheme with explicit reconstruction parameters

It does not depend on a specific implementation.

---

## Required Fields

A valid secret manifest MUST define the following fields.

### Identifier

- `manifest_id`
  - globally unique identifier
  - immutable once issued

---

### Secret Description

- `purpose`
  - concise description of what the secret protects
- `classification`
  - sensitivity or impact level (organizationally defined)

---

### Threshold Parameters

- `threshold`
  - minimum number of shares required for reconstruction
- `share_count`
  - total number of issued shares
- `scheme`
  - cryptographic scheme identifier (e.g. Shamir)

---

### Custody

- `custodians`
  - list of entities responsible for individual shares
  - each entry MUST include:
    - custodian identifier
    - share index
    - custody type (individual, organizational, escrow)

---

### Lifecycle State

- `state`
  - current lifecycle state
  - MUST correspond to a state defined in `docs/lifecycle.md`
- `created_at`
  - creation timestamp
- `last_updated_at`
  - timestamp of last state transition

---

### Lineage

- `previous_manifest`
  - reference to prior manifest (if rotated)
- `superseded_by`
  - reference to successor manifest (if applicable)

---

## Optional Fields

The following fields MAY be included:

- `rotation_policy`
- `retention_policy`
- `legal_constraints`
- `notes`

Optional fields MUST NOT alter the interpretation of required fields.

---

## Integrity and Authenticity

The manifest SHOULD be:

- signed by an authorized party
- version-controlled
- archived alongside related artifacts

The manifest MUST NOT contain:
- secret material
- share payloads
- reconstruction data

---

## Validation Rules

A manifest MUST be rejected if:

- required fields are missing
- threshold parameters are inconsistent
- custody assignments are ambiguous
- lifecycle state is undefined

---

## Auditability

A manifest MUST allow an independent reviewer to determine:

- what the secret is for
- how it is protected
- who is responsible
- what its current status is

No external context should be required.
