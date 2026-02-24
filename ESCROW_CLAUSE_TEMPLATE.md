ORIGIN STANDARD
Standard Escrow Clause Template
1. Escrow Appointment
The Parties agree to appoint a mutually acceptable independent escrow agent (“Escrow Agent”) to administer settlement of the License Fee under this Agreement.
Escrow Agent must be:
Regulated or bonded
Legally authorized to administer escrow transactions
Capable of handling enterprise-scale settlement
2. Escrow Deposit
Licensee shall deposit the full License Fee into escrow pursuant to written escrow instructions executed by all Parties.
Funds must be:
Fully received
Cleared
Irrevocably committed
Not subject to reversal
Escrow Agent shall provide written confirmation of deposit receipt.
3. Release Conditions
Escrow Agent shall release funds to Licensor only upon satisfaction of all of the following:
Delivery of a signed Activation Artifact by Licensor.
Confirmation that Licensee status is reflected as ACTIVE in the Origin Standard Authority Registry.
Successful independent verification of the Activation Artifact under the frozen specification referenced in this Agreement.
Escrow Agent shall not evaluate technical implementation beyond objective verification of the above items.
4. Activation Definition
“Activation Artifact” means a cryptographically signed object containing:
entity_id
tier
issuer_key_binding
profile
spec_commit_binding
activation_timestamp
registry_anchor
signature
The Activation Artifact must verify under the frozen specification referenced in this Agreement.
5. Failure to Activate
If Licensor fails to deliver a valid Activation Artifact within the agreed activation window following escrow confirmation:
Escrow Agent shall return funds to Licensee.
If Licensee fails to deposit funds:
Activation shall not occur.
No authority shall be granted.
6. Finality of Settlement
Upon escrow release:
License Fee is final.
Non-refundable.
Irrevocable.
Escrow release constitutes full satisfaction of License Fee obligation.
7. Non-Retroactivity
Activation, once delivered and registry status set to ACTIVE, shall not be retroactively revoked except for:
Documented fraud
Key compromise
Contractual breach
8. Governing Reference
Escrow agreement shall reference:
Frozen specification commit hash
Tier structure
Authority Registry model
Verification methodology
No escrow clause may modify technical invariants.
