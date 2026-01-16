# Threat Model

This document defines the operational threat model for managing
threshold-protected secrets.

It focuses on **procedural, organizational, and human risks**, not on
cryptographic weaknesses or algorithmic attacks.

---

## Scope

This threat model applies to:

- operational handling of threshold-protected secrets
- custody, lifecycle, and procedural artifacts
- human and organizational failure modes

It does not analyze cryptographic primitives.

---

## Assets

The following assets are considered in scope:

- secret manifests
- custody assignments
- lifecycle records
- rotation, recovery, and revocation artifacts
- institutional trust and accountability

The secret material itself is intentionally excluded.

---

## Trust Assumptions

The model assumes:

- custodians act independently
- no single custodian is fully trusted
- documentation is authoritative
- procedures are followed intentionally

Violations of these assumptions are treated as incidents.

---

## Threat Actors

The following threat actors are considered:

- negligent custodians
- malicious insiders
- compromised custodians
- organizational failure
- legal or regulatory pressure
- loss of institutional memory

External attackers are considered only insofar as they influence
operational behavior.

---

## Threat Categories

### Custody Failure

- loss or destruction of shares
- unavailability of custodians
- ambiguous custody responsibility

Mitigation:
- explicit custody records
- lifecycle state enforcement
- documented exceptions

---

### Procedural Drift

- undocumented changes
- informal shortcuts
- deviation from defined lifecycle

Mitigation:
- mandatory artifacts
- explicit state transitions
- auditability requirements

---

### Silent Failure

- unrecorded incidents
- implicit recovery attempts
- undocumented partial operations

Mitigation:
- failure documentation requirements
- prohibition of silent rollback
- retention of partial artifacts

---

### Over-Centralization

- concentration of authority
- excessive trust in individuals
- informal escalation paths

Mitigation:
- threshold enforcement
- separation of responsibility
- explicit authorization records

---

### Legal and Organizational Pressure

- forced disclosure
- emergency access demands
- policy overrides

Mitigation:
- documented decision points
- explicit authorization
- preserved audit trail

---

## Out of Scope Threats

The following are explicitly out of scope:

- cryptographic algorithm compromise
- side-channel attacks
- hardware-level attacks
- nation-state adversaries
- runtime exploitation

These threats must be addressed elsewhere.

---

## Residual Risk

The model acknowledges that:

- no procedure eliminates all risk
- documentation does not prevent malice
- some failures are unavoidable

Residual risk MUST be documented, not denied.

---

## Security Philosophy

This threat model prioritizes:

- visibility over concealment
- accountability over convenience
- documentation over automation
- explicit failure over silent success

Operational security is treated as a governance problem, not a purely
technical one.

