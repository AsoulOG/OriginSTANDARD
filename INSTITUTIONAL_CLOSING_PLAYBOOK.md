ORIGIN STANDARD
Institutional Closing Playbook
Phase 1 — Pre-Close
Licensor provides:
License Agreement
Escrow Clause
Frozen Specification Reference
Activation Deliverable Description
Registry Verification Instructions
Licensee provides:
Entity identification
Issuer public key
Tier selection
Escrow agent confirmation
Phase 2 — Escrow Setup
Escrow agent appointed.
Escrow instructions executed.
License Fee deposited.
Escrow agent confirms cleared funds.
No activation occurs before confirmation.
Phase 3 — Activation
Upon escrow confirmation:
Id="zzcslg"
Copy code
escrow_confirmed
      ↓
validate_entity
      ↓
bind_issuer_key
      ↓
generate_activation_artifact
      ↓
update_registry(ACTIVE)
      ↓
publish_checkpoint
Licensor delivers:
Activation Artifact
Registry link
Verification instructions
Phase 4 — Verification
Licensee independently verifies:
Artifact signature
Spec commit binding
Registry ACTIVE status
Key binding correctness
Verification does not require Licensor involvement.
Phase 5 — Escrow Release
Upon successful verification:
Escrow Agent releases funds.
License considered fully executed.
Post-Close
Licensee may:
Deploy drop-in capsule
Begin issuance under ACTIVE status
Verify independently at any time
Licensor retains:
Registry authority
Spec freeze control
Key management authority
Deterministic Guarantees
If escrow confirmed → activation occurs.
If escrow not confirmed → activation does not occur.
No discretionary states.
