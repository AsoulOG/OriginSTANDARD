ORIGIN STANDARD
Activation Deliverable Specification
1. Deliverable Overview
Upon escrow confirmation, Licensor shall deliver:
Signed Activation Artifact
Registry Update Confirmation
Verification Instructions
No private keys are delivered.
2. Activation Artifact Structure
The Activation Artifact shall contain:
Text id="artifactstruct"
Copy code
entity_id
tier
issuer_public_key
profile
spec_commit
activation_timestamp
registry_anchor
signature
Artifact must:
Be immutable
Be signed by Authority Root or delegated Epoch Key
Bind to frozen specification commit
3. Registry Update Confirmation
Registry record must reflect:
Text id="registryspec"
Copy code
entity_id
tier
status = ACTIVE
issuer_public_key
activation_hash
activation_timestamp
Registry must be:
Publicly readable
Append-only
Cryptographically signed
4. Verification Method
Licensee may independently verify:
Artifact signature validity
Spec commit match
Registry ACTIVE status
Key binding consistency
Verification requires no Licensor interaction.
5. Activation Effect
Upon successful activation:
Entity gains issuance authority.
Verification remains public.
Authority persists unless registry status changes.
6. Security Boundaries
Activation does not include:
Authority Root private key
Epoch signing key
Session key material
Internal detection logic
All signing authority remains server-side.
7. Revocation Conditions
Registry status may be set to INACTIVE upon:
Non-payment of royalties
Documented key compromise
Contractual breach
Revocation does not invalidate prior issued artifacts.
8. Deterministic Invariant
If registry status = ACTIVE → issuance permitted.
If registry status ≠ ACTIVE → issuance denied.
No partial state exists.
