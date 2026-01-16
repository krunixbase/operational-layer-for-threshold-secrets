# Secret Recovery

This document defines the operational procedure for recovering a
threshold-protected secret.

Recovery is an exceptional operation performed under degraded or
adverse conditions. It MUST prioritize correctness, accountability,
and auditability over speed or convenience.

---

## Purpose

Secret recovery exists to:

- restore access to a critical secret
- respond to loss or unavailability of shares
- re-establish operational continuity
- document exceptional handling of sensitive material

Recovery is not a routine operation.

---

## Recovery Triggers

Recovery MAY be initiated only if at least one of the following
conditions is met:

- loss of one or more shares
- unavailability of custodians
- suspected compromise requiring immediate reconstitution
- legal or regulatory mandate

The trigger MUST be documented explicitly.

---

## Preconditions

Recovery MUST NOT proceed unless:

- the reconstruction threshold is achievable
- custodians involved are authenticated
- recovery authorization has been granted
- a recovery plan has been approved

If these conditions cannot be met, recovery MUST be aborted.

---

## Recovery Procedure

### 1. Authorization

- identify the recovery trigger
- obtain formal authorization
- define scope and objectives

Required artifacts:
- recovery authorization record
- incident or trigger description

---

### 2. Reconstruction

- collect the minimum required number of shares
- reconstruct the secret in a controlled environment
- limit exposure duration and surface

Required artifacts:
- reconstruction record
- custodian participation confirmations

---

### 3. Validation

- verify correctness of the reconstructed secret
- confirm operational functionality
- detect anomalies or inconsistencies

Required artifacts:
- validation record
- verification results

---

### 4. Post-Recovery Actions

Following successful recovery, one of the following MUST occur:

- immediate rotation of the secret
- controlled re-distribution of shares
- archival of the recovered secret

The chosen action MUST be justified and recorded.

Required artifacts:
- post-recovery decision record
- linkage to subsequent lifecycle state

---

## Failure Handling

If recovery fails:

- partial artifacts MUST be preserved
- failure MUST be documented
- operational dependency MUST be reassessed

Silent failure or undocumented retries are not permitted.

---

## Security Considerations

Recovery increases risk due to:

- active reconstruction of secret material
- concentration of sensitive data
- exceptional access paths

Risk mitigation relies on:
- minimal exposure time
- explicit authorization
- complete artifact retention

---

## Non-Goals

This procedure does not:

- guarantee successful recovery
- automate reconstruction
- override custody policies
- conceal operational failure

---

## Auditability

A recovery event MUST be fully reconstructible from retained artifacts,
including authorization, execution, and post-recovery decisions.

Exceptional handling MUST remain visible.
