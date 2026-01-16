# Secret Rotation

This document defines the operational procedure for rotating a
threshold-protected secret.

Rotation replaces an existing secret with a new one while preserving
operational continuity and auditability.

This document describes **process and artifacts**, not tooling.

---

## Purpose

Secret rotation exists to:

- limit the lifetime of sensitive material
- reduce exposure from partial compromise
- allow controlled transition between secrets
- preserve historical accountability

Rotation is a deliberate, high-risk operation and MUST be treated as
such.

---

## Preconditions

Rotation MUST NOT begin unless:

- the current secret is in the `Active` state
- the reconstruction threshold is currently achievable
- custodians are reachable and responsive
- a rotation plan has been approved

Failure to meet these conditions MUST abort the rotation.

---

## Rotation Model

Rotation is modeled as a **two-secret overlap**:

Old Secret (Active) ──┐
├── Transition Period
New Secret (Active) ──┘

At no point should operational dependency be ambiguous.

---

## Rotation Procedure

### 1. Preparation

- generate a new secret
- define new threshold parameters (if changed)
- prepare a new secret manifest
- identify custodians for the new shares

Required artifacts:
- rotation plan
- draft new secret manifest

---

### 2. Distribution

- split the new secret into shares
- distribute shares to designated custodians
- confirm custody and availability

Required artifacts:
- distribution records
- custody confirmations
- finalized new secret manifest

---

### 3. Activation

- transition operational dependency to the new secret
- verify successful use of the new secret
- declare the new secret `Active`

Required artifacts:
- activation record
- dependency transition confirmation

---

### 4. Deactivation

- declare the old secret `Revoked`
- schedule destruction or invalidation of old shares
- prevent further operational use

Required artifacts:
- revocation record
- destruction attestations (if applicable)

---

## Failure Handling

If rotation fails at any stage:

- operational dependency MUST remain on the old secret
- partial artifacts MUST be preserved
- failure MUST be documented explicitly

Silent rollback is not permitted.

---

## Security Considerations

Rotation increases risk temporarily due to:

- coexistence of two valid secrets
- increased handling of sensitive material
- expanded operational surface

These risks are mitigated through:
- limited overlap duration
- explicit state transitions
- complete artifact retention

---

## Non-Goals

This procedure does not:

- automate rotation
- enforce timing or frequency
- mandate cryptographic parameters
- manage custodian behavior

---

## Auditability

A completed rotation MUST be reconstructible from retained artifacts
without reliance on undocumented decisions or implicit knowledge.
