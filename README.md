# 📘 VeritasChain Standards Organization – Official Documentation Hub

> **Status correction — 25 October 2026; archive scope clarified 30 October 2026**
>
> - The VCP v1.0 and VC-Certified v1.0 documents in this repository are historical materials, not current assessment or onboarding instructions. VCP v1.0 is superseded by VCP v1.2 (Released, tag `v1.2.0`). On 2 November 2026, the three editable Word templates were replaced in the current tree by PDFs with a dated notice and **SAMPLE / HISTORICAL ARCHIVE / NOT VALID** on every source page. Original wording remains visible only as historical context; earlier Git commits and downloaded copies are not erased.
> - VSO does not issue certifications itself. The certification scheme requires a Conformity Assessment Body (CAB) independent of the scheme owner; the only registered CAB, VeritasChain Co., Ltd., is not independent (VAP v1.2 ERRATA E-2026-10-21). No independent CAB is listed in the [current scheme registry](https://veritaschain.org/certified/cab/).
> - VSO is operated by VeritasChain Co., Ltd. (kabushiki kaisha); its neutrality rests on published mechanisms, not on its legal form. Conformance is not compliance (VAP v1.2 §1.6).
> - These archived documents do not establish an implementation's conformance to any VCP tier or to VAP. VSO's [published disclosure dated 25 October 2026](https://github.com/veritaschain/vap-spec#implementation-status-mandatory-disclosure) reports zero external implementations of VAP or any of its profiles.
> - The CAP drafts here (v0.1, v0.2) are superseded by CAP v1.0 in [veritaschain/cap-spec](https://github.com/veritaschain/cap-spec). The VAP-AT charter in `vap-at/` is a dated draft (v0.6a); see the notes at the top of each file.

> **Publication review — 1 November 2026:** The report marked “CONFIDENTIAL — LEGAL REVIEW” has been removed from the current tree pending a separate decision on publication clearance and any redaction. This does not remove copies from Git history, existing clones, caches or downloads. The report is not current substantiation for a “world's first” claim. Internal research and AI-assisted searches are not independent third-party validation.

This repository preserves historical documents published by the **VeritasChain Standards Organization (VSO)**.  
It contains historical documents related to **VC-Certified** (v1.0), **VCP v1.0 conformance**, and the **Early Adopter Program** (see the status correction above).

VSO’s mission:

> **Encoding Trust in the Algorithmic Age**  
> Providing open, cryptographically verifiable audit standards for AI-driven and algorithmic trading systems.

---

## 📂 Document Index

### 1. Self-Assessment & Certification Documents

| Document | File | Description |
|----------|------|-------------|
| **VCP Silver Tier – Self-Assessment Checklist (SAC)** | [Historical sample PDF](VCP_Silver_Tier_SAC_v1_HISTORICAL_SAMPLE.pdf) | Historical v1.0 checklist, invalid for current assessment. Document ID: **VSO-CERT-SILVER-SAC-v1.0**. |
| **VC-Certified Silver Tier – Certificate Template** | [Historical sample PDF](VC_Certified_Silver_Certificate_v1_HISTORICAL_SAMPLE.pdf) | Blank historical template, not an issued or valid certificate. VSO does not issue certifications itself (see the status correction above). |

### 2. Early Adopter Program Documents

| Document | File | Description |
|----------|------|-------------|
| **Early Adopter Participation Agreement** | [Historical sample PDF](VCP_Early_Adopter_Agreement_v1_HISTORICAL_SAMPLE.pdf) | Historical blank v1.0 participation-agreement draft, invalid for current use and not an agreement to sign. Document ID: **VSO-EA-AGREE-v1.0**. |

---

## 🏛️ Historical v1.0 Certification Overview

### VC-Certified Silver Tier

Silver Tier is designed for **retail and prop-style environments** where full HFT-grade infrastructure is not available, but baseline transparency and dispute resolution are critical.

Typical targets:

- Retail / MT4/MT5 white-label environments  
- Proprietary trading firms (challenge-based / funded accounts)  
- Non-HFT brokers and small exchanges

The historical Silver Tier design aimed to provide a **tamper-evident transparency layer** for:

- Dispute resolution  
- Internal and external audits  
- Preparing evidence for emerging algorithmic trading regulations (compliance is not determined by VCP conformance)

---

## 🔎 Historical Silver Tier Certification Criteria

The archived v1.0 materials described the following criteria for **VC-Certified – Silver Tier**. They are preserved as historical context and are not current application criteria:

1. **Mandatory Requirements:**  
   - 100% of Mandatory checklist items implemented (SAC Sections 1–5).  
2. **Overall Checklist Score:**  
   - ≥ **85%** overall checklist score (Mandatory + Recommended).  
3. **Evidence Submission:**  
   - The historical evidence-submission criterion in SAC Section 6 listed:  
     - 10–20 event log sample showing hash-chain continuity  
     - At least one Merkle proof  
     - Architecture diagram showing VCP integration point (Sidecar / Shadow logging)

---

## 🧭 VSO Core Policies

VSO is operated by VeritasChain Co., Ltd.; its neutrality rests on published mechanisms.

**Key principles:**

- **Technical Conformance Only**  
  The archived VC-Certified v1.0 materials described technical conformance assessment. The documents themselves do not establish that an implementation has been certified.

- **Non-Endorsement**  
  VSO does not endorse or guarantee:
  - Financial stability or solvency  
  - Business performance or profitability  
  - Regulatory licensing status  
  - Investment products, strategies, or services  

  > **VC-Certified never implies any guarantee of financial solvency, profitability, or regulatory licensing.**

- **Independence & Neutrality**  
  VSO publishes a non-endorsement policy. The certification scheme requires decisions by a CAB independent of the scheme owner; the only registered CAB is not independent (VAP v1.2 ERRATA E-2026-10-21).

- **Open Standards & Interoperability**  
  VCP is designed around well-known standards including:  
  - RFC 9562 (UUIDv7)  
  - RFC 8785 (Canonical JSON / JCS)  
  - RFC 6962 (Merkle Trees)  
  - Ed25519 signatures  
  - SHA-256 hash chains  

---

## 🔧 Using This Archive

- **For Implementers**  
  - Read the checklist and agreement as records of the historical v1.0 program design. They are not current application or onboarding forms.  
  - Consult the [current VCP specification and implementation status](https://github.com/veritaschain/vcp-spec) and the [current CAB registry](https://veritaschain.org/certified/cab/) before relying on certification-related descriptions.

- **For Regulators / Auditors / Researchers**  
  - Use the marked archive copies to trace the historical criteria and wording.
  - Read them with the dated corrections above; the archive does not establish current certification, implementation conformance or regulatory compliance.

> This repository is a historical archive of VC-Certified documentation for VCP v1.0 Silver Tier. It is not current guidance.

---

## 🔗 Related Resources

- [Current VCP specification and implementation status](https://github.com/veritaschain/vcp-spec) — VCP v1.2, specification GA; see its known issues.
- [Current VAP framework](https://github.com/veritaschain/vap-spec/blob/main/spec/v1.2/VAP_Framework_Specification.md) — v1.2, Draft 3.
- [Current CAB registry and independence disclosure](https://veritaschain.org/certified/cab/).
- [Historical VCP v1.0 release](https://github.com/veritaschain/vcp-spec/tree/v1.0.0).
- [VCP Sidecar Integration Guide](https://github.com/veritaschain/vcp-sidecar-guide) — illustrative legacy v1.0 code; consult its status notice.

---

## 📨 Contact

**VeritasChain Standards Organization (VSO)** – Historical documentation inquiries

- Email: `certification@veritaschain.org`  
- Web: `https://veritaschain.org`  

---

## 📄 License & Usage

Documentation © 2025 **VeritasChain Standards Organization (VSO)**.  
Reuse is governed by [LICENSE](LICENSE). Permission to reuse an archived document does not establish conformance, authorize certification, or make the historical forms current assessment instructions.

## Archive publication correction — 2 November 2026

The editable v1.0 certificate, agreement and self-assessment checklist have been replaced by marked reference PDFs. Historical reuse permissions do not authorize use in current assessment, certification or contracting. No current certificate or independent assessment is created by this change.

編集可能な旧版の認証書・参加契約書・自己評価チェックリストを、各ページに「歴史的資料・無効」と表示した参照用PDFへ置き換えました。現在の審査・認証・契約には使用できません。Git履歴の削除は行っていません。
