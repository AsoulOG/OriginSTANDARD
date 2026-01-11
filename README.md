# OriginSTANDARD Reference Verifier (`qs-verify`)

**Status:** Stable · Spec-locked · Deterministic  
**Output Discipline:** `PASS | FAIL | INVALID` only

---

## Overview

This repository contains the **OriginSTANDARD Reference Verifier** — a deliberately boring,
spec-locked implementation used to verify OriginSTANDARD artifacts.

The verifier **does not decide truth**.  
It **only decides conformance**.

Truth belongs to the Engine.  
The verifier checks the locks.

---

## What This Verifier Is

- A mechanical validator of OriginSTANDARD artifacts
- A reference implementation frozen to **OriginSTANDARD Engine Spec v1.3.2**
- A tool for deterministic, offline, reproducible verification
- A public enforcement mechanism for invariant rules

If an artifact verifies, it conforms.  
If it does not, it fails.  
No interpretation is applied.

---

## What This Verifier Is Not

- Not an issuer
- Not an engine
- Not an oracle
- Not a reputation system
- Not a scoring, confidence, or probabilistic tool
- Not a judge of truth, intent, or authorship

The verifier **never**:
- Infers authenticity
- Assigns confidence
- Explains failures beyond machine reason codes
- Produces any output other than `PASS`, `FAIL`, or `INVALID`

---

## Invariants (Hard-Locked)

This verifier is frozen to the following invariants:

- Receipt schema (strings and `null` only; **no JSON numbers at any depth**)
- Deterministic JCS-style canonicalization
- Merkle v2 content root computation
- Ed25519 signature verification
- Glow payload extraction and validation
- Constant-time field comparison
- Strict output discipline

Any deviation from these rules results in `FAIL` or `INVALID`.

---

## Trust Model

- **Verification is public and permissionless**
- **Issuance is sovereign and licensed**
- **Signing authority is exclusive to Origin Standard LLC**

Possession of:
- the specification
- the source code
- the verifier binary

does **not** grant issuance rights.

---

## Output Discipline

Standard output is **strictly limited** to:

```
PASS
FAIL
INVALID
```

No qualifiers.  
No explanations.  
No metadata.

This discipline is enforced by design.

---

## Machine-Only Reporting (Reference Build)

The reference/debug build supports an optional machine-readable report:

```
--report out.json
```

This report may include structured reason codes for CI, auditing, or telemetry.

The **pure/hard build disables reporting entirely**.

---

## Build Variants

### Reference / Debug Build
- Binary: `qs-verify`
- Supports `--report`
- Intended for CI, testing, and interoperability

### Pure / Hard Build
- Binary: `qs-verify-pure`
- No reporting
- No auxiliary output
- Intended for hostile or high-assurance environments

---

## Build Requirements

- Go 1.21 or newer

### Commands

```bash
make build   # builds qs-verify
make pure    # builds qs-verify-pure
make test    # runs unit tests and fixtures
```

---

## CLI Usage

### Reference Build

```bash
qs-verify \
  --in path/to/media \
  --receipt path/to/receipt.json \
  --roots path/to/trust_roots.json \
  [--report out.json]
```

### Pure Build

```bash
qs-verify-pure \
  --in path/to/media \
  --receipt path/to/receipt.json \
  --roots path/to/trust_roots.json
```

---

## Exit Codes

| Code | Meaning |
|------|---------|
| 0    | PASS    |
| 1    | FAIL    |
| 2    | INVALID |

---

## License

This repository is governed by the **OriginSTANDARD License (OSL-1.0)**.

- Verifiers are free and irrevocable
- Issuance is licensed and restricted
- Engine recreation or emulation is prohibited

See `LICENSE` for full terms.

---

## Governing Principle

> Verification is public.  
> Issuance is sovereign.  
> Truth is not negotiable.

---

## Contributions

This repository is **spec-locked**.

Pull requests must:
- Preserve all invariants
- Avoid semantic expansion
- Remain mechanically auditable
- Prefer minimal, explicit changes

If a change alters meaning, it will be rejected.

---

## Contact

Commercial licensing, issuance access, and engine integration:

---

## 🧾 Patent & Legal Notice

This project and all related works are protected under **U.S. Patent Pending** status.

Filed by **Angelo F. Quintos (Inventor)** and assigned to **Origin Standard LLC** under
the OriginSTANDARD License (OSL-1.0).

These filings cover invariant verification, sealed authenticity frameworks,
and deterministic proof validation architectures as described in the OriginSTANDARD
Engine and Verifier specifications.

All rights reserved © 2026 Origin Standard LLC.

**Origin Standard LLC**
⸻
