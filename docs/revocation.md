# Secret Revocation

This document defines the operational procedure for revoking a
threshold-protected secret.

Revocation permanently terminates the operational validity of a secret.
After revocation, the secret MUST NOT be used, reconstructed, or relied
upon for any purpose.

---

## Purpose

Secret revocation exists to:

- permanently disable a secret
- respond to compromise or loss of trust
- enforce end-of-life decisions
- establish a clear operational boundary

Revocation is irreversible.

---

## Revocation Triggers

Revocation MUST be initiated if any of the following occur:

- confirmed or suspected compromise
- loss of sufficient shares preventing safe operation
- supersession by a rotated secret
- organizational or legal mandate
- end of defined retention period

The trigger MUST be explicitly recorded.

---

## Preconditions

Revocation MUST NOT proceed unless:

- the secret is clearly identified
- operational dependencies are known
- revocation authorization has been granted

If dependencies cannot be identified, revocation MUST still proceed,
and the uncertainty MUST be documented.

---

## Revocation Procedure

### 1. Declaration

- formally declare the secret revoked
- record the revocation trigger
- identify affected systems and processes

Required artifacts:
- revocation declaration
- authorization record

---

### 2. Dependency Termination

- cease all operational use of the secret
- disable access paths and integrations
- notify dependent parties if applicable

Required artifacts:
- dependency termination record
- notification log (if applicable)

---

### 3. Share Invalidation

- destroy, invalidate, or render unusable all known shares
- document custodian actions
- acknowledge unknown or unreachable shares

Required artifacts:
- destruction or invalidation attestations
- custodian confirmations
- exception records for missing shares

---

### 4. Finalization

- update the secret manifest state to `Revoked`
- prevent future reconstruction attempts
- archive all related artifacts

Required artifacts:
- updated secret manifest
- archival record

---

## Failure Handling

If revocation cannot be fully completed:

- partial completion MUST be documented
- residual risk MUST be acknowledged
- revocation status MUST still be declared

Incomplete revocation MUST remain visible.

---

## Security Considerations

Revocation reduces risk by:

- eliminating operational reliance
- preventing further exposure
- enforcing finality

Residual risk may remain due to:
- unknown copies
- delayed dependency termination
- incomplete share destruction

These risks MUST be documented, not assumed away.

---

## Non-Goals

This procedure does not:

- guarantee destruction of all copies
- retroactively secure past exposure
- automate enforcement
- conceal operational failure

---

## Auditability

A revoked secret MUST remain auditable.

An independent reviewer MUST be able to determine:
- why revocation occurred
- how it was executed
- what residual risks remain

Finality MUST be explicit.
