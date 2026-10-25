# 📘 VeritasChain Standards Organization – Official Documentation Hub

> **Status correction — 25 October 2026**
>
> - The VCP v1.0 and VC-Certified v1.0 documents in this repository are superseded. VCP v1.0 is superseded by VCP v1.2 (Released, tag `v1.2.0`). The `.docx` files (`VCP_Silver_Tier_SAC_v1.docx`, `VC_Certified_Silver_Certificate_v1.docx`, `VCP_Early_Adopter_Agreement_v1.docx`) are historical records and are not edited.
> - VSO does not issue certificates. The certification scheme requires a Conformity Assessment Body (CAB) independent of the scheme owner; the only registered CAB, VeritasChain Co., Ltd., is not independent (VAP v1.2 ERRATA E-2026-10-21). No VC-Certified certificate described below can currently be issued by an independent CAB.
> - VSO is operated by VeritasChain Co., Ltd. (kabushiki kaisha); its neutrality rests on published mechanisms, not on its legal form. Conformance is not compliance (VAP v1.2 §1.6).
> - Conformance to any VCP tier, or to VAP, has not been independently established for any implementation, and there are zero external implementations of VAP or any of its profiles.
> - The CAP drafts here (v0.1, v0.2) are superseded by CAP v1.0 in [veritaschain/cap-spec](https://github.com/veritaschain/cap-spec). The VAP-AT charter in `vap-at/` is a dated draft (v0.6a); see the notes at the top of each file.

This repository serves as the authoritative document archive for the **VeritasChain Standards Organization (VSO)**.  
It contains historical documents related to **VC-Certified** (v1.0), **VCP v1.0 conformance**, and the **Early Adopter Program** (see the status correction above).

VSO’s mission:

> **Encoding Trust in the Algorithmic Age**  
> Providing open, cryptographically verifiable audit standards for AI-driven and algorithmic trading systems.

---

## 📂 Document Index

### 1. Self-Assessment & Certification Documents

| Document | File | Description |
|----------|------|-------------|
| **VCP Silver Tier – Self-Assessment Checklist (SAC)** | `VCP_Silver_Tier_SAC_v1.docx` | Official self-assessment checklist for Silver Tier conformance. Includes Mandatory/Recommended requirements, RFC references (UUIDv7, RFC 8785, RFC 6962), and evidence submission criteria. Document ID: **VSO-CERT-SILVER-SAC-v1.0**. |
| **VC-Certified Silver Tier – Certificate Template** | `VC_Certified_Silver_Certificate_v1.docx` | Historical template for a Silver Tier certificate. VSO does not issue certificates (see the status correction above). Includes VSO Non-Endorsement Policy language. |

### 2. Early Adopter Program Documents

| Document | File | Description |
|----------|------|-------------|
| **Early Adopter Participation Agreement** | `VCP_Early_Adopter_Agreement_v1.docx` | Formal participation agreement for organizations joining the VCP Silver Tier Early Adopter Program. Covers confidentiality, deliverables, IP rights, disclaimers, and jurisdiction. Document ID: **VSO-EA-AGREE-v1.0**. |

---

## 🏛️ Certification Overview

### VC-Certified Silver Tier

Silver Tier is designed for **retail and prop-style environments** where full HFT-grade infrastructure is not available, but baseline transparency and dispute resolution are critical.

Typical targets:

- Retail / MT4/MT5 white-label environments  
- Proprietary trading firms (challenge-based / funded accounts)  
- Non-HFT brokers and small exchanges

Silver Tier provides a **tamper-evident transparency layer** for:

- Dispute resolution  
- Internal and external audits  
- Preparing evidence for emerging algorithmic trading regulations (compliance is not determined by VCP conformance)

---

## 🔎 Silver Tier Certification Criteria

To obtain **VC-Certified – Silver Tier** status, an Adopter must meet all of the following:

1. **Mandatory Requirements:**  
   - 100% of Mandatory checklist items implemented (SAC Sections 1–5).  
2. **Overall Compliance Rate:**  
   - ≥ **85%** overall checklist score (Mandatory + Recommended).  
3. **Evidence Submission:**  
   - All required artifacts in SAC Section 6 submitted for validation (historical v1.0 criterion; validation would now be by a CAB independent of the scheme owner):  
     - 10–20 event log sample showing hash-chain continuity  
     - At least one Merkle proof  
     - Architecture diagram showing VCP integration point (Sidecar / Shadow logging)

---

## 🧭 VSO Core Policies

VSO is operated by VeritasChain Co., Ltd.; its neutrality rests on published mechanisms.

**Key principles:**

- **Technical Conformance Only**  
  VC-Certified attests **only** that a system correctly implements VCP v1.0 technical requirements.

- **Non-Endorsement**  
  VSO does not endorse or guarantee:
  - Financial stability or solvency  
  - Business performance or profitability  
  - Regulatory licensing status  
  - Investment products, strategies, or services  

  > **VC-Certified never implies any guarantee of financial solvency, profitability, or regulatory licensing.**

- **Independence & Neutrality**  
  VSO does not promote specific vendors, platforms, or firms. Certification decisions belong to a CAB independent of the scheme owner; the only registered CAB is not independent (VAP v1.2 ERRATA E-2026-10-21).

- **Open Standards & Interoperability**  
  VCP is designed around well-known standards including:  
  - RFC 9562 (UUIDv7)  
  - RFC 8785 (Canonical JSON / JCS)  
  - RFC 6962 (Merkle Trees)  
  - Ed25519 signatures  
  - SHA-256 hash chains  

---

## 🔧 How These Documents Are Used

- **For Adopters (Prop Firms / Brokers / Exchanges)**  
  - Use `VCP_Silver_Tier_SAC_v1.docx` to prepare your internal assessment.  
  - Review and sign `VCP_Early_Adopter_Agreement_v1.docx` before joining the Early Adopter Program.  
  - ~~Upon successful verification, VSO issues a certificate based on `VC_Certified_Silver_Certificate_v1.docx`.~~ Superseded: VSO does not issue certificates (status correction, 25 October 2026).

- **For Regulators / Auditors / Investors**  
  - Use these documents to understand how VSO defines Silver Tier conformance and how certification is granted.  
  - SAC and Agreement provide a clear view of technical and legal boundaries of VC-Certified.

> This repository is a historical archive of VC-Certified documentation for VCP v1.0 Silver Tier. It is not current guidance.

---

## 🔗 Related Resources

- **VCP Specification v1.0**  
  - Protocol-level specification (EN/JA/ZH)  
- **VCP Sidecar Integration Guide (Silver Tier)**  
  - Technical implementation guide for MT4/MT5 / white-label environments  
- **VCP Explorer API & GUI**  
  - Event search, Merkle proof verification, and certificate verification  
- **VC-Certified Program Page**  
  - Public description of tiers, scope, and FAQs: `https://veritaschain.org/certified/`

---

## 📨 Contact

**VeritasChain Standards Organization (VSO)** – Certification Division  

- Email: `certification@veritaschain.org`  
- Web: `https://veritaschain.org`  

---

## 📄 License & Usage

Documentation © 2025 **VeritasChain Standards Organization (VSO)**.  
May be used for **VCP conformance, VC-Certified assessments, and related certification processes.**
