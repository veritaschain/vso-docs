# External reproduction notes

> **Status — 5 November 2026**
>
> Notes for independent **reproduction and critique** of public Evidence Pack materials. This page is not a certification kit. It is not an independent CAB assessment. It is not an endorsement of any implementation, laboratory, or result.
>
> A reviewer's findings stay the reviewer's. VeritasChain Co., Ltd. and the VeritasChain Standards Organization (VSO) must not cite those findings as certification, a conformity determination, or an endorsement.

VSO is operated by VeritasChain Co., Ltd. (Tokyo, Japan). Conformance to VAP or VCP is not compliance with any law (VAP v1.2 §1.6).

---

## Fixed versions

Judge published packs against these texts. "GA" on this page means the specification text is published. It does not mean that any implementation has been assessed for production use.

| Item | Fixed text | What that status means |
|------|------------|------------------------|
| **VAP** | [VSO-VAP-SPEC-001 v1.2.0, Draft Specification (Draft 3)](https://github.com/veritaschain/vap-spec/blob/main/spec/v1.2/VAP_Framework_Specification.md) | Current framework draft in [veritaschain/vap-spec](https://github.com/veritaschain/vap-spec). Not adopted by the IETF, ISO, or ITU. The individual Internet-Draft [`draft-kamimura-vap-framework`](https://datatracker.ietf.org/doc/draft-kamimura-vap-framework/) (revision 02, as cited by the VAP repository) is not an IETF Working Group document. |
| **VCP** | [v1.2 specification, GA declared 2026-07-06, tag `v1.2.0`](https://github.com/veritaschain/vcp-spec/tree/v1.2.0/spec/v1.2) (commit `b23acb2`, 2026-10-09) | Published specification in [veritaschain/vcp-spec](https://github.com/veritaschain/vcp-spec). The canonical text is `spec/v1.2/`. [Known issues](https://github.com/veritaschain/vcp-spec/blob/v1.2.0/spec/v1.2/README.md#known-issues-in-v12-informative) remain open. Alignment with VAP v1.2 is under review; conformance is not established. |
| **vcp-sdk** | Package **0.1.0 pre-release** in [veritaschain/vcp-sdk](https://github.com/veritaschain/vcp-sdk) | First-party library. Not an external implementation. Not a conformance result. Install from that GitHub repository only; it is not published to PyPI or npm. The historical tag `v0.1.0` (2026-10-25) is not the later snapshot named in the SDK README. Follow the commit pin printed in that README, and identify the snapshot by commit. Package metadata still reports 0.1.0. |
| **vcp-rta-reference** | [veritaschain/vcp-rta-reference](https://github.com/veritaschain/vcp-rta-reference) | First-party proof of concept. Archived evidence is a **VCP v1.1 legacy** format. No VCP tier or VAP conformance result is established by that repository. |

CAP v1.0 and CPP v1.4 are published specifications in their own repositories. VAP v1.2 conformance is not established for either profile. They are outside the reproduction steps on this page.

A few sentences inside the `v1.2.0` tag are older than later public corrections. When they disagree with the list below, follow the later text:

- The status line in tagged [`spec/v1.2/README.md`](https://github.com/veritaschain/vcp-spec/blob/v1.2.0/spec/v1.2/README.md) is stronger than the [current vcp-spec README](https://github.com/veritaschain/vcp-spec/blob/main/README.md). Follow the current README, VAP v1.2 errata of 27 October 2026, and this page. GA means the specification text is published.
- Sentences in that tagged file about who may perform assessment are superseded by VAP v1.2 ERRATA E-2026-10-21. The only registered CAB is VeritasChain Co., Ltd., and it is not independent of the scheme owner.
- The tagged overview says every v1.0 and v1.1 event remains valid under v1.2. The current vcp-spec README is narrower: historical records keep their signed bytes, and failing a v1.2 schema check is not a reason to rewrite them. This page follows the current README.
- The [known-issues list](https://github.com/veritaschain/vcp-spec/blob/v1.2.0/spec/v1.2/README.md#known-issues-in-v12-informative) on the tag is still the list to read. Those issues remain open.

---

## Result vocabulary

Current **VAP §4.1.3** (Sequence Verifiability Mechanisms) is **two-valued**. Both normative algorithms return only `VALID` or `INVALID`.

`VALID` / `INVALID` / `INDETERMINATE` appears in an **unadopted Discussion draft** only: [proposals/three-valued-verification](https://github.com/veritaschain/vap-spec/blob/main/proposals/three-valued-verification/README.md) (draft revision 0.2, 2026-10-25). That draft has no formal proposal number and no target release. Repository publication is not adoption. It adds no VAP v1.2 requirement, event type, field, wire format, or conformance level. Read it as a text to critique. Do not treat it as the algorithm VAP currently specifies.

Where a published first-party tool reports three values, it is following that unadopted draft, not a change to §4.1.3. In that draft, and in those tools, combination order is `INVALID`, then `INDETERMINATE`, then `VALID`. `INDETERMINATE` is not a pass. Do not report a check that was not performed as `VALID`.

**`UNVERIFIABLE` is prototype vocabulary.** It is used in some internal kit notes. It is not a value adopted in VAP or VCP. In new writing, the corresponding label in the unadopted draft is `INDETERMINATE`. The published vcp-sdk verifier and the current vcp-rta-reference verifier report `INDETERMINATE`, not `UNVERIFIABLE`.

A separate machine exit code for "conditionally detectable" is not defined. Published tools use their own codes (vcp-sdk and the vcp-rta-reference historical replay use exit 2 when the overall verdict is `INDETERMINATE`). Record the three review classes below in the written report. Do not invent a code and call it part of the specification.

---

## Public repositories only

Use material already published under [github.com/veritaschain](https://github.com/veritaschain). For this review, start from:

| Material | Public location | Limit |
|----------|-----------------|--------|
| VAP Draft 3 | [spec/v1.2](https://github.com/veritaschain/vap-spec/tree/main/spec/v1.2) | Draft specification text |
| Three-valued discussion | [proposals/three-valued-verification](https://github.com/veritaschain/vap-spec/tree/main/proposals/three-valued-verification) | Unadopted text. Not a program to run |
| VCP v1.2 | [tag `v1.2.0`](https://github.com/veritaschain/vcp-spec/tree/v1.2.0) | Published specification. Not an implementation assessment |
| Archived trading evidence | [vcp-rta-reference](https://github.com/veritaschain/vcp-rta-reference), directory `evidence/` | 40-event v1.1 legacy corpus (20 SIG and 20 EXE). First-party CI on 26 October 2026 reported an overall **`INDETERMINATE`** verdict. That is one published result, not a result the reviewer is required to reproduce unchanged |
| Reproduction notes for that corpus | [26 October 2026 checkpoint](https://github.com/veritaschain/vcp-rta-reference/blob/main/docs/REPRODUCTION_CHECKPOINT_2026-10-26.md), [reproducing guide](https://github.com/veritaschain/vcp-rta-reference/blob/main/tools/verifier/REPRODUCING.md), [reviewer report template](https://github.com/veritaschain/vcp-rta-reference/blob/main/docs/REVIEWER_REPORT_TEMPLATE.md) | The checkpoint pins commit `cc695fe1698250878fbbc5f0c5461591ac8e0954`. Counts in that note describe that commit |
| Offline SDK and published vectors | [vcp-sdk](https://github.com/veritaschain/vcp-sdk), including `examples/explorer-demo/` | Pre-release. The explorer demo is a first-party batch with intact, tampered, and missing-key cases. Its intact local checks still leave the full batch `INDETERMINATE` when no external-anchor proof is supplied |

If a scenario is not in those published files, leave it out. Do not replace it with an unpublished demonstration, a private archive, or an unmerged branch. That includes any unmerged three-valued verifier branch: do not check one out and do not treat it as a current tool. Use the default branch and the tags named above.

Signed historical records stay as published. Do not rewrite them so that a newer schema accepts them. A v1.1 legacy record that fails a v1.2 schema check is a version difference. It is not, by itself, evidence of tampering. The vcp-spec README states the same limit: historical records keep their original validation context and signed bytes.

---

## Reviewer steps

1. **Choose the verification keys yourself.** Do not rely only on keys shipped in a pack. An embedded public key is not an identity claim. In vcp-rta-reference, pass a public key to the default verifier only after you have decided to trust it. The published `--compare-reference-key` path is a mathematical comparison with the published reference key, not an identity assertion.
2. **Verify on a machine you control**, separate from the system that produced the pack. Follow the reproduction guide in the repository you cloned. Record the commit or tag you actually ran.
3. **Write these items into the output**, each time:
   - the keys you trusted, and why you trusted them
   - the external anchor you checked, or the reason you could not check it
   - the time range and the event range under review
   - the scope you observed, and the scope you did not observe
4. **Classify each finding** as one of the three labels in the next section. Missing evidence is not an acceptable result, and it is not `VALID`.
5. **Keep version and construction differences out of the tampering class.** Rules for legacy Merkle trees and a missing `.ots` file are below.

Completeness, where it can be argued at all, is limited to omission-evidence at anchor granularity (VAP v1.2 §4.1.7 and the completeness scope note under §4.1). Do not write that every action was observed.

### How to classify a finding

| Class | Use it when | Do not use it when |
|-------|-------------|-------------------|
| **Detectable** | A check you actually ran shows a mismatch: a broken hash or inclusion path, a signature that fails against a key you established, or an anchor proof that commits to a different value. | The only problem is that an input was absent. |
| **Conditionally detectable** | A mismatch would be decidable only with material you state (a trusted key, an anchor proof, a declared batch scope) and you record that condition. | You want a short word for "passed". |
| **Cannot judge** | The check could not be run with the material on hand, or the difference is a version or construction gap rather than a demonstrated mismatch. | You did not look, and you would like the pack to count as acceptable. |

Map these words to tool output only as a convenience. Under current VAP §4.1.3, a demonstrated mismatch is `INVALID`. In the unadopted draft, and in the published first-party verifiers that follow it, a check that cannot be performed is `INDETERMINATE` (prototype notes may say `UNVERIFIABLE`). Absence of one input must not hide a mismatch that another check has already shown. The unadopted draft's combination order is `INVALID` over `INDETERMINATE` over `VALID`.

### Legacy Merkle construction

VCP v1.2 §6.2.1 requires RFC 6962 Merkle hashing (leaf prefix `0x00`, internal-node prefix `0x01`). The v1.2 specification's own example code also duplicates an odd node. Those two constructions differ whenever the leaf count is not a power of two.

The archived RTA evidence uses the historical duplicate-odd tree, not the strict RFC 6962 Merkle tree hash. Published vcp-sdk reports that shape as `INDETERMINATE` with the reason `LEGACY_MERKLE_CONSTRUCTION`. It does not report it as `INVALID`. Follow that boundary here: **a legacy Merkle construction, by itself, is not a tampering finding.**

### Missing external anchor (`.ots`)

VAP v1.2 INT-006 requires an external anchor at every conformance level. The original OpenTimestamps file named `merkle_root.ots` is not in the archived vcp-rta-reference pack. A producer field that names an anchor is not confirmation that the proof was checked.

When the `.ots` file or another external-anchor proof is missing:

- the anchor check **cannot be judged**
- do not report the anchor check as `VALID`
- do not report tampering, and do not report `INVALID`, solely because the proof file is absent

The same boundary applies to a pending anchor, an anchor target you cannot reach, or a key you have not established. Those are "cannot judge" unless a separate check shows a real mismatch.

---

## What to publish with a critique

Publish enough for another person to repeat the run:

- repository URL, tag or commit, and tool version
- the separate environment (operating system and language version are enough)
- trusted keys, external-anchor check or the reason it was skipped, time range, event range, observed scope, and unobserved scope
- one class — detectable, conditionally detectable, or cannot judge — for each finding, with the tool's raw status beside it
- a statement that the note is the reviewer's own reproduction or critique, not a VSO certification, conformity determination, or endorsement

An overall pass is appropriate only when every required check was performed and matched. A pack that omits a proof, a key, or a segment of the log does not become acceptable by omission.

---

## Disclosures

Figures below are the published VSO disclosures. This page does not add a new count.

| Item | Published statement |
|------|---------------------|
| External implementations of VAP or any VAP profile | **0**, as of the [25 October 2026 disclosure](https://github.com/veritaschain/vap-spec#implementation-status-mandatory-disclosure). vcp-sdk and vcp-rta-reference are first-party. They do not change that count. |
| Evidence Packs accepted in any proceeding | **0**, same disclosure. Counting rules are in the [proposed criteria](https://github.com/veritaschain/vap-spec/blob/main/disclosures/2026-10-24-counting-criteria.md). |
| Registered CAB | [VeritasChain Co., Ltd. only](https://veritaschain.org/certified/cab/). That company operates VSO and is not independent of the scheme owner (VAP v1.2 ERRATA E-2026-10-21). No independent CAB is listed. |
| Contract and customer counts | Withdrawn on 24 October 2026. Do not cite them. The withdrawal is not a claim that the count is zero. See the [commercial-disclosure correction](https://github.com/veritaschain/vap-spec/blob/main/disclosures/2026-10-24-commercial-contracts.md). |
| Independent third-party reproduction | Not established. |

---

## Contact

| Item | Detail |
|------|--------|
| Organization | VeritasChain Co., Ltd., which operates VSO |
| Headquarters | Tokyo, Japan |
| Email | [info@veritaschain.org](mailto:info@veritaschain.org) |
| Web | [https://veritaschain.org](https://veritaschain.org) |

---

## License

Documentation © 2026 VeritasChain Standards Organization (VSO).
Reuse is governed by [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Permission to copy this note does not create a certification, a conformity result, or an endorsement.
