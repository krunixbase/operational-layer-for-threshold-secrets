# Rotation Record

The rotation record is the authoritative artifact documenting the
replacement of one threshold-protected secret with another.

It provides a verifiable, auditable link between two secret manifests
and records the operational decision to transition dependency.

---

## Purpose

The rotation record exists to:

- document the execution of a secret rotation
- bind an old secret to its successor
- establish temporal and procedural continuity
- prevent ambiguity about which secret is authoritative

The rotation record does not contain secret material.

---

## Scope

This record applies to:

- any rotation involving threshold-protected secrets
- transitions where operational dependency changes

It is independent of cryptographic implementation.

---

## Required Fields

A valid rotation record MUST define the following fields.

---

### Record Identifier

- `rotation_record_id`
  - globally unique identifier
  - immutable once issued

---

### Manifest Linkage

- `previous_manifest`
  - reference to the revoked or superseded secret manifest
- `new_manifest`
  - reference to the newly issued secret manifest

Both references MUST be resolvable.

---

### Rotation Context

- `rotation_reason`
  - justification for rotation
- `initiated_at`
  - timestamp when rotation began
- `completed_at`
  - timestamp when rotation was finalized

---

### Authorization

- `authorized_by`
  - entity or role approving the rotation
- `authorization_reference`
  - reference to approval artifact

---

### Execution Summary

- `distribution_confirmed`
  - confirmation that new shares were distributed
- `activation_confirmed`
  - confirmation that operational dependency transitioned
- `revocation_scheduled`
  - confirmation that old shares are scheduled for revocation

---

## Optional Fields

The following fields MAY be included:

- `overlap_duration`
- `exceptions`
- `notes`

Optional fields MUST NOT contradict required fields.

---

## Integrity and Authenticity

The rotation record SHOULD be:

- signed by an authorized party
- stored alongside both referenced manifests
- retained for the lifetime of the system

The record MUST NOT include:
- secret material
- share payloads
- reconstruction data

---

## Validation Rules

A rotation record MUST be rejected if:

- manifest references are missing or ambiguous
- timestamps are inconsistent
- authorization is undefined
- execution confirmation is incomplete

---

## Auditability

A rotation record MUST allow an independent reviewer to determine:

- which secret was replaced
- which secret became authoritative
- when the transition occurred
- who approved the operation

No external explanation should be required.
