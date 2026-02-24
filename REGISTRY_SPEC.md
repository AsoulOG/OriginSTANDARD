ORIGIN STANDARD
Authority Registry Specification
1. Registry Purpose
The Authority Registry defines issuance rights.
It is:
Publicly readable
Cryptographically signed
Append-only
Deterministic
2. Registry Record Structure
Each entity record contains:
Copy code

entity_id
tier
status (ACTIVE | INACTIVE)
issuer_public_key
profile
activation_hash
activation_timestamp
revocation_timestamp (if any)
spec_commit_binding
3. Registry Invariants
Records are append-only.
Status transitions are logged.
Historical states remain visible.
Registry updates are signed by Authority Root.
4. Verification Dependency
Seal verification requires:
Issuer exists in registry
Status = ACTIVE at seal timestamp
Issuer key matches registry key
Profile matches registry profile
Spec binding matches frozen spec
Failure of any → INVALID.
5. Revocation
Revocation sets:
Copy code

status = INACTIVE
revocation_timestamp = now
Effects:
New issuance prohibited
Old artifacts remain valid
Verification unaffected
6. Transparency Model
Registry checkpoints may be:
Merkle-root anchored
Publicly mirrored
Timestamped
Registry integrity must be independently verifiable.
