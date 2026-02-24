ORIGIN STANDARD
Escrow Settlement Model — Deterministic Activation
1. Settlement Principle
Origin Standard licenses are settled exclusively through independent third-party escrow.
Authority is released only upon escrow confirmation of funds received under executed escrow agreement.
No card processing.
No direct wire settlement.
No provisional activation.
Escrow confirmation is the sole settlement trigger.
2. Parties
Each transaction involves:
Licensor — Origin Standard
Licensee — Purchasing Entity
Escrow Agent — Independent regulated escrow provider
Escrow agent must be:
Legally recognized
Regulated or bonded
Capable of handling enterprise-scale settlement
Mutually accepted by both parties
3. Escrow Deposit
Licensee deposits the full License Fee into escrow pursuant to executed escrow instructions.
Funds must be:
Fully received
Cleared
Irrevocably committed
Not subject to reversal
Escrow agent confirms receipt in writing.
4. Activation Trigger
Upon escrow confirmation of cleared funds:
Plain text
Copy code
escrow_confirmed
        ↓
validate_entity
        ↓
generate_activation_artifact
        ↓
update_registry_status(ACTIVE)
        ↓
publish_registry_checkpoint
Activation is deterministic and automatic upon escrow confirmation.
No discretionary approval process exists.
5. Activation Artifact
Licensor delivers:
Signed Activation Artifact
Registry update confirmation
Verification instructions
Artifact includes:
entity_id
tier
issuer_key_binding
profile
spec_commit_binding
activation_timestamp
registry_anchor
signature
Artifact is cryptographically verifiable and immutable.
6. Registry Update
Upon activation:
Entity status is set to ACTIVE
Issuance authority is enabled
Verification remains public and permissionless
Registry is publicly readable and append-only.
7. Escrow Release Condition
Escrow agent releases funds to Licensor only after:
Delivery of Activation Artifact
Confirmation that registry status reflects ACTIVE
Artifact verifies under frozen specification
Escrow agent does not evaluate technical architecture.
Escrow agent verifies objective deliverables only.
8. Failure Conditions
If Activation Artifact:
Fails signature validation
Does not bind to frozen spec
Does not reflect registry ACTIVE status
Escrow agent shall not release funds.
If escrow deposit is not completed:
Activation does not occur
Registry remains unchanged
Binary enforcement.
9. No Refund Policy
Upon successful activation and registry update:
License Fee is final
Non-refundable
Irrevocable
Escrow release constitutes final settlement.
10. Liability Allocation
Escrow model ensures:
No payment reversal risk to Licensor
No activation without payment
No unilateral fund access
No chargeback exposure
Balanced risk between parties
Escrow agent holds funds until conditions satisfied.
11. Withdrawal After Activation
If Licensee withdraws participation:
Registry status set to INACTIVE
Issuance authority removed
Verification of prior artifacts remains valid
No refund issued
12. Deterministic Invariant
Settlement Model Guarantees:
If funds are confirmed in escrow → Activation occurs.
If funds are not confirmed → Activation does not occur.
There is no provisional authority state.
13. Governing Integration
Escrow agreement must reference:
Frozen specification commit
Tier license structure
Registry authority model
Activation artifact definition
Non-retroactivity principle
Escrow agreement must not modify technical invariants.
14. Final Statement
Origin Standard licenses are settled exclusively through independent escrow to ensure:
Institutional-grade transaction security
Deterministic authority release
Mutual protection
Elimination of payment-layer dispute risk
Escrow controls funds.
Origin Standard controls authority.
Registry enforces issuance.
Verifier enforces validity.
