# PP-SPEC-027: Proven Efficacy and the Third Axis

**Status:** Published **Author:** Craig Ellrod **Date:** September 18, 2026 **License:** CC BY-ND 4.0
**Document ID:** PP-SPEC-027 **Maintained by:** Proof Economy™ Standards Alliance (PESA)
**Specification URI:** proofprotocol.io **Repository:** github.com/proofprotocol/proven-efficacy

**Anchor:** This document is timestamped and anchored via Zenodo, DOI [10.5281/zenodo.22830948](https://doi.org/10.5281/zenodo.22830948), as of the publication date above, establishing public priority for the efficacy-verification distinction defined here, independent of and prior to any adoption by third-party standards bodies.

**NIST Randomness Beacon pulse, retrieved live at commit:**

```json
{
  "pulse": {
    "uri": "https://beacon.nist.gov/beacon/2.0/chain/2/pulse/1946151",
    "version": "2.0",
    "chainIndex": 2,
    "pulseIndex": 1946151,
    "timeStamp": "2026-09-18T01:57:00.000Z",
    "outputValue": "9D4EBEFE0CDA5E0858AB72592696583C1E82A27EFBA1A2766CA161290B4E046257B906723A085BC9D82299D4AC49EC83DBEE060E06DBEE1066080E433B811D9F"
  }
}
```

---

## Summary

An evidence-producing standard answers whether a record of execution is trustworthy: whether it was tampered with, whether it originated from a structurally independent party, whether it stayed consistent from the moment of capture forward. None of that answers a separate question: whether the thing being recorded actually worked. A system can produce evidence that is tamper-evident, structurally independent, and faithfully captured, and that evidence can still describe a control that failed the moment it was tested against a real adversary. This spec names that gap as a third axis, distinct from and orthogonal to the first two, and defines what closes it.

## The Gap

An evidence-producing standard, by construction, proves that a record exists and can be trusted. It does not, and structurally cannot, prove that the thing the record describes actually performed. A system can be shown to have stayed within whatever boundaries were set for it; whether those boundaries, or the results produced within them, were actually correct is a separate question no evidence-producing standard undertakes to answer, because answering it requires testing the underlying claim, not the integrity of the record about it. This is not a flaw in any particular framework. It is a structural ceiling on the category itself. No amount of additional rigor applied to record integrity — better signing, better anchoring, better custody of keys — moves an evidence-producing standard any closer to answering whether the thing it evidenced actually worked. That requires a different kind of evidence entirely, produced by a different method.

## Relation to the Prior Two Axes

Two axes are already established in this framework:

- **Consistency-of-data**: the evidence remains internally consistent and unaltered from the point of capture forward. (PP-SPEC-006 and prior.)
- **Fidelity-at-capture**: the evidence faithfully represents what the executor actually did, established through structural independence at the moment of capture. (PP-SPEC-023.)

Both axes describe properties of the *record*. Neither describes a property of the *thing the record is about*. A perfectly consistent, perfectly independent, perfectly faithful record of a control that did nothing under adversarial pressure is still a record of a control that did nothing. This spec defines the third axis:

**Proven Efficacy.** The control, product, or agent demonstrably performed its claimed function under adversarial conditions representative of the environment it will actually operate in, as established by a party with no outcome-contingent interest in the result.

Proven Efficacy is not downstream of the other two axes and does not subsume them. A system can satisfy consistency-of-data and fidelity-at-capture in full and still have no Proven Efficacy claim at all, because nothing in either axis tests whether the control works. Conversely, a Proven Efficacy claim without the other two axes is just a better-produced version of the self-attestation problem this framework already rejects: an efficacy result is only as trustworthy as the record of how it was produced, which is exactly what the first two axes exist to secure. The three axes compose. None substitutes for another.

## The Proven Efficacy Tier Ladder

Structured on a binary-threshold logic: does reaching the claim require trusting the party being assessed.

| Tier | Name | Who you must trust | Proven Efficacy? |
| :---: | --- | --- | :---: |
| E1 | Vendor-Asserted | The vendor's own claim, unverified | No |
| E2 | Vendor-Conducted, Disclosed | The vendor's own testing, methodology disclosed | No |
| E3 | Independently Conducted | A party with no outcome-contingent interest, adversarial method disclosed | **Yes** |
| E4 | Independently Conducted, Continuously Re-Verified | Same as E3, with claims re-tested on a recurring cadence rather than a point-in-time snapshot | **Yes** |

The line between E2 and E3 is the same structural-independence test already defined in PP-SPEC-023: not whether a fee changed hands, but whether the assessor's ongoing interest is tied to a favorable result for the assessed party. Tier placement is a claim about the assessor's structure, not about the assessor's competence, honesty, or the quality of any individual test. A structurally independent assessor can still run a bad test; that is a quality failure, not a tier failure, and this ladder does not grade it. Conflating the two is the most common way a tier system like this gets attacked, by pointing at one weak independently-run test and treating it as disproof of the tier itself, so the distinction is stated here explicitly rather than left implicit.

## What Qualifies as Evidence

An Efficacy claim at E3 or E4 requires:

1. Adversarial conditions representative of a real deployment environment, not a synthetic or vendor-controlled benchmark.
2. An assessing party structurally independent per the PP-SPEC-023 definition.
3. A disclosed method: what was attempted, under what constraints, against what baseline.
4. A result stated in terms of what was attempted versus what succeeded, not a summary characterization alone.

This spec does not prescribe a scoring formula, a case-classification taxonomy, a specific test harness, or a deployment methodology. Those are implementation, not doctrine, and are out of scope here by design. This is a deliberate boundary, not an omission: "adversarial conditions representative of the environment" and "outcome-contingent interest" are doctrine-level tests, not measurement procedures, and this document does not claim they are self-executing. An implementation making a Proven Efficacy claim must publish its own operational definition of representativeness and its own independence disclosure, and that published definition, not this document, is what a challenger attacks. This spec defines what must be true. It does not and cannot make any specific claim of Proven Efficacy true by itself.

## Distinguishing Note

This is not breach-and-attack simulation, red/blue/purple team exercises, or a bug bounty, as those terms are conventionally used. Those practices are open-ended: they test for the presence of *some* weakness, wherever it happens to be found, under best-effort conditions, and a null result proves only that this particular attempt didn't find one. Proven Efficacy is bound to a specific, prior, stated claim: the vendor asserts the control does X; the test is designed against X; the result is a pass or fail on X, not a general weakness inventory. This is the falsifiability requirement that separates the two: an open-ended exercise has no claim it could have falsified, so a clean result carries no evidentiary weight about the claim. A bound exercise does, because failure to falsify a specific, stated claim under adversarial pressure is itself the evidence. The two practices are complementary, not interchangeable, and a system can have a spotless red-team history with zero Proven Efficacy claims to show for it.

## Provenance

This document was first published September 18, 2026, and is anchored via Zenodo DOI [10.5281/zenodo.22830948](https://doi.org/10.5281/zenodo.22830948) and the NIST Randomness Beacon pulse recorded above (chain 2, pulse 1946151, timestamp 2026-09-18T01:57:00.000Z), together establishing public, third-party-verifiable priority for the efficacy-verification distinction and its position as a third axis, distinct from and orthogonal to consistency-of-data (PP-SPEC-006) and fidelity-at-capture (PP-SPEC-023), independent of and prior to any adoption of this distinction by third-party standards bodies. Subsequent revisions are recorded in the git commit history of the repository above, which constitutes the provenance chain for this document beyond its initial publication.
