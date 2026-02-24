ORIGIN STANDARD
Key Binding & Activation Model
1. Core Principle
Issuance authority is bound to a specific public key.
Authority is not transferable.
Authority is not password-based.
Authority is cryptographically anchored.
2. Key Registration
Before activation, entity must submit:
Copy code

issuer_public_key
Key must:
Conform to supported signature scheme
Pass validation
Be unique in registry
3. Binding Process
Activation Artifact binds:
Copy code

entity_id
issuer_public_key
tier
profile
spec_commit
Signature from Authority Root confirms binding.
4. Signing Hierarchy
Authority Root (never used for execution) ↓ Epoch Signing Key ↓ Entity Issuer Key (bound) ↓ Session Key (derived per seal) ↓ Single Seal Signature
Root never signs seals.
Entity key signs only after:
Valid PASS from 7.5
Nonce issuance
Atomic burn confirmation
5. Key Rotation
Entity may rotate key by:
Submitting new public key
Signing rotation request with old key
Registry update
Activation rebind
Old key marked inactive.
6. Compromise Handling
If entity key compromised:
Copy code

status = INACTIVE
Reactivation requires:
Key replacement
Registry update
New activation artifact
Past artifacts remain valid.
7. Deterministic Enforcement
Seal validation requires:
Signature matches registered key
Key active at seal time
Profile matches
Spec binding matches
No match → INVALID.
Final Structural Model
You now have:
Deterministic activation
Automated authority release
Append-only registry
Key-bound issuance
Binary enforcement
No manual scaling bottleneck
No email dependency
No drift
This scales to:
1 entity
10 entities
10,000 entities
Without adding human overhead.
