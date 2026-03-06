# Origin Standard — Honest Comparison
## Post-Hoc Detection vs. Layer 7.5 Execution Authority

**Origin Standard LLC**
**Engine Specification v1.3.4r5**
**February 2026**

---

This document exists because the people reading it are smart enough to ask the hard questions before their legal team does. These are the real differences — no spin, no vendor language. If something here makes PAEC look harder to sell, that is intentional. Incomplete honesty is just slow deception.

---

## 1. The Foundational Difference

Post-hoc detection operates after execution. The transaction occurred. The state mutated. Money moved or data changed. The system then evaluates whether that already-completed action was legitimate.

Layer 7.5 operates before execution. The state has not mutated. The system determines whether execution is permitted. If not permitted, execution does not occur.

This is not a better fraud tool. It is a different category of thing entirely.

Post-hoc detection answers: *Was that legitimate?*
Layer 7.5 answers: *Does this execute at all?*

These are not competing answers to the same question. They are answers to different questions at different points in time.

---

## 2. What Post-Hoc Does Well That Layer 7.5 Does Not

This section exists because pretending 7.5 replaces everything is dishonest.

Post-hoc detection is better at identifying patterns across historical execution data. It catches insider fraud where a valid human executed a bad action deliberately. It detects anomalies in legitimate user behavior over time. It builds compliance audit trails for regulators who want to see detection logic applied to a record of what happened. It scores risk across millions of past transactions for trend analysis. It catches fraud that passed through a legitimate human — coerced transactions, social engineering completions, authorized push payment fraud where the human genuinely clicked confirm.

Layer 7.5 does none of these things. It is a gate, not an analyst. It does not learn. It does not score. It does not adapt. It enforces one invariant: valid Seal or no execution.

If your primary threat model is insider fraud, social engineering completions, or pattern-based anomaly detection across legitimate user populations — post-hoc tooling is doing work that 7.5 is not designed to replace. Both can and should coexist. 7.5 reduces the volume that reaches your post-hoc stack. Your post-hoc stack handles what 7.5 cannot gate.

---

## 3. What Layer 7.5 Does That Post-Hoc Cannot

Post-hoc cannot prevent what has already occurred.

This sounds obvious. It is not treated as the structural problem it actually is.

Every post-hoc system — regardless of speed, accuracy, or AI sophistication — operates on a committed state. The execution already happened. The response is remediation, reversal, dispute, or writeoff. The cost exists. Detection only determines what you do about it afterward.

Layer 7.5 prevents execution. There is no committed state to remediate. There is no dispute. There is no reversal workflow. There is no writeoff. There is no incident. The attack ended at the gate before anything happened.

**Attack categories structurally stopped at 7.5 that post-hoc cannot prevent:**

Enumeration attacks require automated execution to validate credentials at scale. No Seal means no execution. The attack cannot run. Post-hoc can detect the pattern after thousands of test transactions have already occurred. 7.5 stops the first one.

Account takeover automation requires execution to mutate account state. A bot cannot generate a valid Seal. The takeover cannot commit. Post-hoc identifies the takeover after the account has already been accessed. 7.5 stops the commit.

Provisioning fraud requires execution to load compromised credentials into a wallet. No Seal means no provisioning. Post-hoc identifies suspicious provisioning patterns after provisioning has occurred. 7.5 stops provisioning.

Bot-driven transaction submission requires execution to submit. No Seal means the transaction never reaches the payment rail. Post-hoc flags suspicious transaction velocity after transactions have processed. 7.5 stops them from processing.

The common thread: every one of these categories depends on automation reaching the execution primitive at scale. Remove the primitive and the economic model of the attack collapses. One bot cannot generate one million valid Seals. The math does not work for the attacker.

---

## 4. The Questions Nobody Usually Asks

**Does Layer 7.5 create a new attack surface?**

Yes. The Seal generation endpoint becomes a target. If an attacker can compromise the entropy source, manipulate the nonce issuance, or find a path to mint a valid Seal without satisfying the cognitive floor — 7.5 is bypassed. This is why the architecture specifies boundary-local entropy, atomic nonce burn, and no root key signing. These are not preferences. They are requirements. A deployment that shortcuts any of these is not running 7.5. It is running something that looks like 7.5 and fails like nothing.

**What happens if integration is done wrong?**

Impact drops sharply. If the integrating entity leaves a direct database write path open, a legacy endpoint unprotected, an admin override channel, or a background job that mutates state without passing through 7.5 — the boundary is not complete. PAEC cannot enforce what it cannot see. Conformance liability transfers to the entity at joinder. Origin Standard does not monitor deployments. The spec defines what correct looks like. The verifier checks conformance. The hash determines authority. Wrong integration is the entity's problem contractually and operationally.

**Can a sophisticated attacker study the spec and find a bypass?**

The spec is public intentionally. Security through obscurity is not security. The invariant holds or it does not. If a bypass exists in the architecture, it exists whether or not the spec is published. Publishing the spec invites scrutiny. Scrutiny either finds a real weakness — which is useful — or confirms the architecture holds. The frozen spec with public hash means any claimed bypass can be evaluated against a fixed reference. There is no moving target to argue about.

**Does this work against AI-powered attacks?**

AI-powered attacks that require automated execution at scale are structurally stopped. AI that generates more convincing phishing, more realistic synthetic identities, or more persuasive social engineering — that is a human problem downstream of execution. If a human was deceived into completing a transaction, that transaction had a valid Seal. 7.5 passed it. That is correct behavior. The deception is outside the execution boundary. Post-hoc detection, fraud education, and social engineering defense handle that layer. 7.5 handles the automation layer.

**What if the attacker pays a human to complete executions?**

Then the execution cost per fraud attempt increases by approximately the cost of a human completing a transaction. Mass automation fraud at current scale costs fractions of a cent per attempt. Human-mediated fraud costs dollars to tens of dollars per attempt minimum. The economic model changes by orders of magnitude. Some fraud persists. Volume collapses. That is the claim — not elimination, but economic destruction of the scaling law.

**Why is the spec frozen? What if a vulnerability is found?**

If a vulnerability is found in the frozen spec, any entity running that spec is running a compromised version. A fix requires a new spec. Entities on the old spec are on a fork. This is correct behavior, not a flaw. The alternative — a spec that updates silently — means entities cannot verify what they are running. The hash would change without notice. Conformance would be impossible to audit. Frozen is harder to manage but architecturally honest. Updates are forks. Forks are explicit. Explicit is auditable.

---

## 5. The Honest Scorecard

| Capability | Post-Hoc Detection | Layer 7.5 |
|---|---|---|
| Prevent automated execution at scale | No | Yes |
| Detect patterns in historical data | Yes | No |
| Stop insider fraud | Partially | No |
| Eliminate execution ambiguity | No | Yes |
| Adapt to new fraud patterns over time | Yes | No — frozen |
| Reduce dispute volume before it starts | No | Yes |
| Catch social engineering completions | Partially | No |
| Collapse automation economics | No | Yes |
| Require downstream changes | No | No |
| Operate without contacting vendor | No | Yes |

Neither column wins. The question is whether you are currently missing the left column or the right column. Most enterprise payment infrastructure has spent the last decade building the left column. The right column has not existed until now.

---

## 6. Why This Was Built

Not for the business case. The business case is real but it was not the reason.

The reason is simpler and older than any of this.

There is a principle that has existed long before digital systems — that a thing done should be traceable to a person who chose to do it. That accountability is not a feature to be added later. It is the foundation of trust between people, institutions, and systems. When a person makes a decision, they should own that decision. When a system acts, something with standing should have authorized it.

Digital infrastructure broke that principle quietly and at scale. Execution became permissive. Anything that could reach the endpoint could commit. Bots became indistinguishable from people. Accountability became probabilistic. Attribution became a litigation strategy rather than a system property.

That is not a technical failure. It is a failure of design philosophy. Systems were built to be fast and open and scalable, and accountability was treated as something to retrofit afterward with detection layers and dispute processes and writeoffs and insurance.

This is the attempt to put accountability back where it belongs — at the moment of execution, before commit, as a hard requirement rather than a soft suggestion.

One person built this. No team. No funding. No institutional backing. A veteran who spent time thinking about the difference between analog systems where accountability is physical and unavoidable, and digital systems where accountability is optional and after the fact.

The patents exist to protect the work long enough for it to matter. The frozen spec exists because if it changes every six months it was never really a standard. The public repo exists because a standard that cannot be verified independently is not a standard.

The business model is straightforward because the work is real and should be compensated.

But the reason it exists is not the business model.

It exists because unauthorized execution at scale is a failure of human accountability in digital form. And fixing that is worth doing even if the economics had not worked out.

They did work out. That is a separate thing.

---

**Origin Standard LLC**
**github.com/AsoulOG/OriginSTANDARD**
**U.S. Patent Pending 63/971,633**
