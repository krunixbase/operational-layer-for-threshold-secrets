# Custody Log

The custody log is the authoritative, append-only record documenting
custodial responsibility for threshold secret shares over time.

It records **who was responsible**, **for what**, and **during which
period**, without containing secret material or share payloads.

---

## Purpose

The custody log exists to:

- establish continuous accountability for secret shares
- document custody assignment and transfer
- support audit, investigation, and legal review
- prevent ambiguity about responsibility

The custody log is a historical record, not a control mechanism.

---

## Scope

The custody log applies to:

- all custodians holding threshold secret shares
- all custody changes, including temporary or exceptional assignments

It is independent of cryptographic implementation.

---

## Log Structure

The custody log consists of **chronologically ordered entries**.

Entries MUST be append-only and MUST NOT be altered or removed.

---

## Required Fields

Each custody log entry MUST define the following fields.

---

### Entry Identifier

- `custody_entry_id`
  - globally unique identifier
  - immutable once recorded

---

### Manifest Reference

- `manifest_id`
  - reference to the associated secret manifest

---

### Custodian Information

- `custodian_id`
  - identifier of the responsible entity
- `share_index`
  - index of the share under custody
- `custody_type`
  - individual, organizational, escrow, or equivalent

---

### Custody Period

- `custody_start`
  - timestamp when responsibility began
- `custody_end`
  - timestamp when responsibility ended (if applicable)

If `custody_end` is undefined, custody is considered active.

---

### Custody Event

- `event_type`
  - assignment
  - transfer
  - return
  - loss
  - destruction
- `event_reason`
  - justification for the event

---

### Authorization

- `authorized_by`
  - entity or role approving the custody event
- `authorization_reference`
  - reference to approval artifact

---

## Optional Fields

The following fields MAY be included:

- `location`
- `handling_constraints`
- `notes`

Optional fields MUST NOT contradict required fields.

---

## Integrity and Authenticity

The custody log SHOULD be:

- signed or sealed periodically
- version-controlled
- retained for the lifetime of the system

The log MUST NOT contain:
- secret material
- share payloads
- reconstruction data

---

## Validation Rules

A custody log entry MUST be rejected if:

- required fields are missing
- custody periods overlap inconsistently
- authorization is undefined
- manifest reference is ambiguous

---

## Auditability

The custody log MUST allow an independent reviewer to determine:

- who was responsible for each share at any point in time
- when custody changed
- why the change occurred
- who authorized the change

Continuity of responsibility MUST be demonstrable.

