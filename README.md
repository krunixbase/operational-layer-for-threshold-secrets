# Operational Layer for Threshold Secrets

This repository defines a **reference operational layer** for managing
threshold-protected secrets.

It specifies **procedures, artifacts, and accountability boundaries**
without implementing cryptography, storage, or automation.

---

## Purpose

The purpose of this project is to:

- define auditable lifecycle procedures for threshold secrets
- establish normative operational artifacts
- separate cryptographic mechanisms from responsibility and governance
- prevent ambiguity in high-risk secret handling

This repository is **specification-first** and **implementation-agnostic**.

---

## Scope

This project covers:

- secret lifecycle definition
- rotation, recovery, and revocation procedures
- custody accountability
- formal artifact specifications

It does **not** provide code, services, or runtime components.

---

## Non-Goals

This project does not:

- implement cryptographic algorithms
- store or transport secret material
- manage access control or authentication
- automate operational decisions
- replace KMS, HSM, or key management platforms

---

## Repository Structure

docs/      Procedural specifications
formats/   Normative artifact definitions

---

## Normative References

The following documents are normative:

- `docs/lifecycle.md`
- `docs/rotation.md`
- `docs/recovery.md`
- `docs/revocation.md`
- `docs/threat-model.md`
- `formats/secret-manifest.md`
- `formats/rotation-record.md`
- `formats/custody-log.md`

---

## Design Principles

This project prioritizes:

- explicit state transitions
- documented failure over silent success
- accountability over convenience
- auditability over automation
- governance over tooling

---

## Intended Audience

This repository is intended for:

- security architects
- compliance and audit teams
- organizations managing high-impact secrets
- engineers designing threshold-based systems

---

## Status

This repository is a **reference specification**.

Changes are expected to be deliberate, reviewed, and versioned.
