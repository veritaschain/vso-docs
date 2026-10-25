# VAP-AT: Verifiable AI Provenance – Assessment Test

[![Status: Draft](https://img.shields.io/badge/Status-Draft-yellow.svg)](./VAP-AT_Program_Charter_v0_6a_EN.md)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Version: 0.6a](https://img.shields.io/badge/Version-0.6a-blue.svg)](./VAP-AT_CHANGELOG.md)

**VAP-AT** is a measurement-based assessment framework that evaluates AI systems for **Auditability**, **Verifiability**, and **Regulatory Readiness**.

> *"Verify, Don't Trust"* — Evaluating that audit trails for AI systems exist in a cryptographically verifiable form.

> **Status correction — 25 October 2026:** This is a dated draft (Charter v0.6a, 2025-12-28). VSO is operated by VeritasChain Co., Ltd. VSO does not issue certifications itself. A CAB must be independent of the scheme owner; the only registered CAB, VeritasChain Co., Ltd. (the planned "Pilot CAB #1"), is not independent (VAP v1.2 ERRATA E-2026-10-21). "Accredited" in the charter means "VSO-approved": VSO approval is not accreditation in the ISO/IEC 17000 sense. Scores and Threshold Designations do not determine regulatory compliance (VAP v1.2 §1.6). The current VAP-AT program description is in [veritaschain/vap-spec `programs/vap-at/`](https://github.com/veritaschain/vap-spec/tree/main/programs/vap-at).

---

## Overview

VAP-AT addresses a critical gap in AI governance: while regulations like the EU AI Act mandate logging and audit capabilities for high-risk AI systems, no standardized framework exists to **measure and verify** these capabilities.

### Key Differentiators

| Feature | VAP-AT Approach |
|---------|-----------------|
| **Assessment Target** | AI systems (not individuals) |
| **Output** | Score-based (0-20) with optional threshold labels |
| **Design Philosophy** | Continuous improvement over binary pass/fail |
| **Independence** | 4-layer separation of standard-setting and assessment |

### What VAP-AT Measures

| Property | Key Question |
|----------|--------------|
| **Auditability** | Can third parties independently verify audit trails? |
| **Verifiability** | Are records complete with proper observability? |
| **Regulatory Readiness** | Is evidence packaged for audit submission? |

### What VAP-AT Does NOT Do

- ❌ Evaluate AI model accuracy or performance
- ❌ Assess business logic validity
- ❌ Conduct security vulnerability testing
- ❌ Guarantee AI decision correctness or legality

---

## Documents

| Document | Description |
|----------|-------------|
| [**Program Charter (EN)**](./VAP-AT_Program_Charter_v0_6a_EN.md) / [**(JA)**](./VAP-AT_Program_Charter_v0_6a_JA.md) | Draft v0.6a: governance, scoring criteria, and roadmap |
| [**Changelog**](./VAP-AT_CHANGELOG.md) | Version history and changes |

---

## Assessment Levels

```
┌─────────────────────────────────────────────────────────────┐
│  Level 1: VAP-AT Self                                       │
│  • Self-assessment using VAP Scorecard Explorer             │
│  • Target: Low-risk AI (chatbots, recommendation engines)   │
│  • Cost: Free – $5,000                                      │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│  Level 2: VAP-AT Verified                                   │
│  • Third-party assessment by VSO-approved CAB               │
│  • Target: Medium-risk AI (HR Tech, credit scoring)         │
│  • Cost: $15,000 – $150,000                                 │
└─────────────────────────────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│  Level 3: VAP-AT Continuous                                 │
│  • Ongoing monitoring with automated verification           │
│  • Target: High-risk AI (medical, autonomous systems)       │
│  • Cost: $100,000+                                          │
└─────────────────────────────────────────────────────────────┘
```

---

## Scoring System

**10 Criteria × 0-2 Points = Maximum 20 Points**

| Score Range | Grade | Interpretation |
|-------------|-------|----------------|
| 16–20 | **Strong** | Demonstrates robust auditability |
| 11–15 | **Moderate** | Auditable but room for improvement |
| 6–10 | **Limited** | Significant auditability deficiencies |
| 0–5 | **Inadequate** | Fundamentally insufficient auditability |

### Threshold Designations (Optional)

Threshold Designations are **interpretive labels** for procurement and regulatory reporting convenience:

- "VAP-AT Auditability Threshold – EU AI Act Art.12/19 aligned" (Score 16+)
- "VAP-AT Auditability Threshold – MiFID II RTS 25 aligned" (Score 14+)
- "VAP-AT Baseline Auditability Threshold" (Score 11+)

> ⚠️ **Important:** Threshold Designations are scheme-internal labels, not guarantees of legal compliance.

---

## Regulatory Alignment

| Regulation | VAP-AT Coverage |
|------------|-----------------|
| **EU AI Act** | Art.12 (Logging), Art.14 (Human Oversight), Art.19 (Retention), Annex IV |
| **MiFID II RTS 25** | Time synchronization, algo trading audit trails |
| **SEC 17a-4** | Tamper-evidence, record retention |
| **GDPR Art.17** | Right to erasure compatibility (Crypto-Shredding) |
| **DORA** | Failure and recovery logging |

---

## Current Status

| Milestone | Status |
|-----------|--------|
| Program Charter | 📝 Draft (v0.6a) |
| Scoring Criteria v1.0 | 🔜 Planned |
| Evidence Pack Template | 🔜 Planned |
| Pilot CAB approval | 🔜 2026 Q1 (original target; status not updated here). The only registered CAB, VeritasChain Co., Ltd., is not independent (VAP v1.2 ERRATA E-2026-10-21) |
| Public Registry | 🔜 2026 Q3 (original target; status not updated here) |

---

## Related Resources

### VAP Framework
- [VAP Framework Specification v1.2 (Draft 3)](https://github.com/veritaschain/vap-spec/blob/main/spec/v1.2/VAP_Framework_Specification.md) (v1.1 is superseded for new work)
- [VAP Scorecard](https://github.com/veritaschain/vap-spec/tree/main/scorecard) (question set only)

### VeritasChain Protocol (VCP)
- [VCP Specification](https://github.com/veritaschain/vcp-spec) (current release: v1.2)
- [VCP Sidecar Integration Guide](https://github.com/veritaschain/vcp-sidecar-guide)

### External Links
- [VeritasChain Standards Organization](https://veritaschain.org)
- [Individual Internet-Draft: draft-kamimura-scitt-vcp](https://datatracker.ietf.org/doc/draft-kamimura-scitt-vcp/) (not adopted by any IETF WG)

---

## Contributing

VAP-AT is currently in draft stage. We welcome feedback through:

- **Issues:** For questions, suggestions, or bug reports
- **Discussions:** For broader conversations about the framework
- **Pull Requests:** For proposed changes to documentation

Please read our [Contributing Guidelines](https://github.com/veritaschain/.github/blob/main/CONTRIBUTING.md) before submitting.

---

## Contact

| Purpose | Contact |
|---------|---------|
| General Inquiries | info@veritaschain.org |
| Technical Questions | technical@veritaschain.org |
| Certification | certification@veritaschain.org |
| Standards | standards@veritaschain.org |

---

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

---

*Copyright © 2025 VeritasChain Standards Organization*
