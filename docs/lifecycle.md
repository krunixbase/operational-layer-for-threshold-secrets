# Secret Lifecycle

This document defines the operational lifecycle of a threshold-protected
secret.

The lifecycle describes **procedural states and transitions**, not
implementation details. It applies regardless of the underlying
cryptographic scheme, provided that threshold reconstruction semantics
are preserved.

---

## Purpose

The lifecycle exists to ensure that:

- every secret has a clearly defined state
- transitions between states are explicit and auditable
- no secret exists in an undefined or ambiguous condition
- operational responsibility is clearly attributable

This document does not prescribe automation or tooling.

---

## Lifecycle States

A secret progresses through the following states:

Created → Distributed → Active → Rotated → Revoked → Archived


Not all secrets must pass through every state, but transitions MUST be
explicitly recorded.

---

## State Definitions

### Created

The secret has been generated but not yet distributed.

Properties:
- secret exists in a single location
- no shares have been issued
- no operational dependency exists

Required artifacts:
- creation record
- initial secret manifest

---

### Distributed

The secret has been split into threshold shares and distributed.

Properties:
- shares exist in independent custody
- reconstruction parameters are fixed
- the original secret SHOULD be destroyed

Required artifacts:
- distribution record
- custody assignments
- updated secret manifest

---

### Active

The secret is in operational use.

Properties:
- threshold reconstruction is possible
- shares are expected to be available
- operational dependency exists

Required artifacts:
- custody confirmations
- periodic availability attestations (optional)

---

### Rotated

The secret has been replaced by a new secret.

Properties:
- old and new secrets may coexist temporarily
- operational dependency transitions to the new secret
- old shares SHOULD be scheduled for revocation

Required artifacts:
- rotation record
- linkage between old and new manifests

---

### Revoked

The secret is no longer valid for operational use.

Properties:
- reconstruction SHOULD be prevented
- shares SHOULD be destroyed or invalidated
- operational dependency MUST cease

Required artifacts:
- revocation record
- custody destruction attestations (if applicable)

---

### Archived

The secret is retained solely for historical or legal reasons.

Properties:
- no operational dependency
- reconstruction MAY be impossible or prohibited
- artifacts are preserved for audit purposes

Required artifacts:
- archive record
- retention policy reference

---

## Transitions

All transitions between states MUST:

- be intentional
- be recorded
- reference the previous state
- identify responsible parties

Implicit transitions are not permitted.

---

## Failure Modes

The lifecycle explicitly acknowledges the following failure modes:

- loss of shares
- unavailability of custodians
- incomplete transitions
- conflicting records

These conditions MUST be documented rather than concealed.

---

## Non-Goals

This lifecycle does not:

- enforce timing or scheduling
- mandate specific cryptographic algorithms
- define access control mechanisms
- automate decision-making

---

## Auditability

A complete lifecycle MUST be reconstructible from retained artifacts
without reliance on institutional memory or undocumented procedures.
