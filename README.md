# Human Root of Trust — Schemas

JSON Schema definitions for the Human Root of Trust framework.

**Every agent must trace to a human.**

These schemas are the machine-readable expression of the [HRT framework](https://humanrootoftrust.org). They define the canonical data structures for the three foundational concepts: the human principal, the agent action receipt, and the authorization chain that connects them.

Public domain. No rights reserved.

---

## Schemas

### `schemas/v1/receipt`
**AgentActionReceipt** — The atomic trust artifact. A cryptographic receipt proving that an autonomous agent took a specific action on behalf of a human principal. Every agent action must produce one.

→ `https://humanrootoftrust.org/schemas/v1/receipt`

### `schemas/v1/principal`
**Principal** — A human who serves as the root of trust for one or more AI agents. The ultimate authorizing entity. No agent acts without tracing back to a Principal's authorization.

→ `https://humanrootoftrust.org/schemas/v1/principal`

### `schemas/v1/authorization-chain`
**AuthorizationChain** — A verifiable record of how a human principal's intent flows through one or more agents to produce an action. Every link in the chain is traceable and cryptographically bound.

→ `https://humanrootoftrust.org/schemas/v1/authorization-chain`

---

## The Three Pillars

These schemas embody the three pillars of the HRT framework:

1. **Proof of Humanity** — the `principal` schema captures the human root. Every agent traces to one.
2. **Hardware-Rooted Device Identity** — the `keyId` and `signingAlgorithm` fields in `receipt` bind authorization to specific hardware.
3. **Action Attestation** — the `receipt` schema is the signed, verifiable record of every agent action.

---

## Usage

These schemas are hosted at `humanrootoftrust.org/schemas/v1/` and are designed to be extended by product implementations. To build on HRT, reference the base receipt schema in your own schema:

```json
{
  "$ref": "https://humanrootoftrust.org/schemas/v1/receipt",
  "@context": [
    "https://humanrootoftrust.org/schemas/v1/receipt"
  ]
}
```

A conforming receipt must include the HRT context in `@context`. Implementations may add their own context alongside it. This ensures receipts are independently verifiable against the HRT base schema regardless of which system produced them.

---

## Public Domain

This framework and all schemas in this repository are dedicated to the public domain under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/).

No rights reserved. Build freely.

> *"Every agent must trace to a human."*
> — Human Root of Trust, February 2026
