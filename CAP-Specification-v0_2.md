# Content / Creative AI Profile (CAP)

## Technical Specification v0.2

**Document ID:** VSO-CAP-SPEC-001  
**Status:** Draft Specification  
**Version:** 0.2.0  
**Date:** 2026-01-10  
**Maintainer:** VeritasChain Standards Organization (VSO)  
**License:** CC BY 4.0 International  
**Website:** https://veritaschain.org  
**Contact:** standards@veritaschain.org

---

## Executive Summary

**CAP (Content / Creative AI Profile)** is a domain-specific profile within the VAP (Verifiable AI Provenance Framework), establishing the evidentiary foundation for AI usage in content and creative industries.

**CAP is NOT a regulation that prohibits or censors AI usage.**  
**CAP IS a framework for preserving verifiable evidence that third parties can audit when disputes arise.**

> **The problem is not AI itself, but its black-box nature.**

AI is already extensively used in content production, and halting its adoption is unrealistic. What matters is the ability to record—in a cryptographically non-repudiable format—**who** used **what** content, under **what authority**, and **when** within AI workflows. This enables post-hoc verification when disputes over rights infringement, confidential leaks, or persona abuse occur.

---

## Table of Contents

**Part I: Core Specification**
1. [Introduction](#1-introduction)
2. [Position within VAP Framework](#2-position-within-vap-framework)
3. [Target Industries](#3-target-industries)
4. [Threat Model](#4-threat-model)
5. [Event Model](#5-event-model)
6. [Data Model](#6-data-model)
7. [Integrity Layer](#7-integrity-layer)
8. [Compliance Philosophy](#8-compliance-philosophy)
9. [Non-Goals](#9-non-goals)
10. [Regulatory Alignment](#10-regulatory-alignment)
11. [Implementation Guidelines](#11-implementation-guidelines)

**Part II: SRP Extension (Safe Refusal Provenance)**
12. [SRP Introduction](#12-srp-introduction)
13. [SRP Event Model](#13-srp-event-model)
14. [SRP Data Model](#14-srp-data-model)
15. [Completeness Verification](#15-completeness-verification)
16. [Evidence Pack Structure](#16-evidence-pack-structure)
17. [Privacy Considerations](#17-privacy-considerations)
18. [SRP Regulatory Alignment](#18-srp-regulatory-alignment)
19. [Third-Party Verification](#19-third-party-verification)

**Appendices**
- [Appendix A: JSON Schema](#appendix-a-json-schema)
- [Appendix B: JSON Examples](#appendix-b-json-examples)
- [Appendix C: SRP Event Examples](#appendix-c-srp-event-examples)
- [References](#references)

---

# Part I: Core Specification

---

## 1. Introduction

### 1.1 Purpose

CAP (Content / Creative AI Profile) is an evidentiary framework designed to address the following structural challenges:

| Challenge | Description | CAP Solution |
|-----------|-------------|--------------|
| **Rights Provenance Opacity** | Unable to trace rights basis for materials fed to AI | `RightsBasis` field records rights justification |
| **Consent Ambiguity** | Unclear whether consent was given for training/generation | `ConsentBasis` captures consent state |
| **Confidentiality Gap** | Unreleased materials lack classification management | `ConfidentialityLevel` for classification |
| **Accountability Boundaries** | Cannot identify responsible parties when disputes arise | `User`/`Role` records actors |
| **Tampering Possibility** | Records can be altered post-facto | Hash Chain provides cryptographic integrity |

### 1.2 Design Philosophy

CAP is founded on this core principle:

> **"Leave Evidence, Not Barriers"**  
> (Not "Stop AI" but "Record Proof")

AI adoption in creative work is irreversible. CAP accepts this reality and focuses not on prohibition or censorship, but on leaving **evidence that third parties can verify post-hoc**.

This enables:
- **Rights holders** to obtain proof of infringement
- **Creators** to demonstrate legitimate usage
- **Regulators** to establish audit foundations
- **Industry** to achieve trustworthy AI adoption

### 1.3 Scope Definition

**CAP applies to:**
- AI workflows where **content/IP assets** are the subject
- AI processes including **training (TRAIN)** and **generation (GEN)**
- Evidence records for **post-hoc dispute verification**

**CAP does NOT apply to:**
- Real-time control or intervention in AI decisions
- Automatic determination of copyright infringement
- Evaluation of generated content quality

### 1.4 Conformance Language

Keywords in this specification are interpreted per RFC 2119:

- **MUST** / **REQUIRED** / **SHALL**: Absolute requirement
- **MUST NOT** / **SHALL NOT**: Absolute prohibition
- **SHOULD** / **RECOMMENDED**: Recommended with valid exceptions
- **MAY** / **OPTIONAL**: Truly optional

### 1.5 Terminology

| Term | Definition |
|------|------------|
| **CAP** | Content / Creative AI Profile — Domain profile for content industries |
| **VAP** | Verifiable AI Provenance Framework — Parent framework |
| **VSO** | VeritasChain Standards Organization — Standards body |
| **Asset** | Content/IP asset subject to AI workflow |
| **Provenance** | Cryptographically verifiable record of asset origin and history |
| **Evidence Pack** | Collection of CAP events forming an audit package |
| **Event** | Atomic unit of AI workflow activity (INGEST, TRAIN, GEN, EXPORT) |
| **SRP** | Safe Refusal Provenance — Extension for proving content was NOT generated |

---

## 2. Position within VAP Framework

### 2.1 VAP/VSO/CAP Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│     VAP (Verifiable AI Provenance Framework)                    │
│     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                    │
│     Conceptual framework for AI decision audit trails           │
│     Defines cross-domain minimum requirements                   │
│                                                                 │
│                          ▲                                      │
│                          │ defines & maintains                  │
│                          │                                      │
│     VSO (VeritasChain Standards Organization)                   │
│     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                   │
│     Standards body maintaining VAP and profiles                 │
│                                                                 │
│                          │                                      │
│                          │ publishes profiles                   │
│                          ▼                                      │
│                                                                 │
│     ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐           │
│     │   VCP   │ │   CAP   │ │   DVP   │ │   MAP   │  ...      │
│     │Finance  │ │Content/ │ │Automotive│ │Medical │           │
│     │Profile  │ │Creative │ │ Profile │ │Profile │           │
│     └─────────┘ └─────────┘ └─────────┘ └─────────┘           │
│                                                                 │
│     Domain-specific protocol implementations                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.2 Relationship to VCP

| Aspect | VCP (Finance Profile) | CAP (Content Profile) |
|--------|----------------------|----------------------|
| **Subject** | Transaction | Content/IP Asset |
| **Industries** | Finance, Trading | Games, Film, Publishing, Music |
| **Core Events** | SIG/ORD/EXE/CXL | INGEST/TRAIN/GEN/EXPORT |
| **Regulations** | MiFID II, EU AI Act | EU AI Act, DSA, Copyright Law |
| **Time Precision** | Nanosecond–Millisecond | Second–Minute (workflow dependent) |
| **Shared Foundation** | VAP Integrity Layer | VAP Integrity Layer |

### 2.3 Shared Infrastructure

CAP inherits the following VAP common infrastructure:

- **Hash Chain**: Tamper detection via event chain linkage
- **Merkle Tree**: Efficient verification of bulk events
- **Digital Signature**: Ed25519 issuer authentication
- **Crypto Agility**: Future algorithm migration support

---

## 3. Target Industries

### 3.1 Priority Classification

CAP target industries are classified by priority:

#### Priority A (Highest)

| Industry | Sub-segments | Primary Risks |
|----------|--------------|---------------|
| **Games** | AAA / Publishers / Studios / Outsourcing | IP dilution, confidential leaks, character mimicry |
| **Film/Animation/Streaming** | Production / VFX / Post-production / OTT | Actor likeness, voice cloning, unreleased footage leaks |

#### Priority B (Secondary)

| Industry | Sub-segments | Primary Risks |
|----------|--------------|---------------|
| **Publishing** | Manga / Books / Editorial Production | Style mimicry, manuscript leaks, translation quality |
| **Music** | Labels / Distribution / MV Production | Voice cloning, song imitation, rights processing |

#### Priority C (Reference)

| Industry | Sub-segments | Primary Risks |
|----------|--------------|---------------|
| **Adult Content** | Production / Distribution / Platforms | Deepfakes, non-consensual generation |
| **Corporate Branding** | Web / IR / Design | Tone mimicry, brand dilution |

### 3.2 Industry-Specific Considerations

Each industry has unique considerations. CAP abstracts these as common denominators while allowing **Industry-Specific Extensions**:

| Industry | Specific Considerations | CAP Accommodation |
|----------|------------------------|-------------------|
| Games | Long dev cycles, massive asset volumes | Hierarchical AssetID, batch INGEST |
| Film | Complex licensing, production committees | Multi-stage ConsentBasis, Role extensions |
| Publishing | Derivative work permissions, adaptation rights | Fine-grained PermittedUse |
| Music | Separate copyright and neighboring rights | Multiple RightsBasis records |

---

## 4. Threat Model

### 4.1 Overview

CAP addresses threats in AI workflows classified into five categories:

```
┌─────────────────────────────────────────────────────────────────┐
│                      CAP Threat Taxonomy                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TH-1: IP Dilution                                              │
│  ├─ Unique style/worldview easily mimicked by AI                │
│  └─ Brand value erosion, market differentiation difficulty      │
│                                                                 │
│  TH-2: Reverse Flow (Rights Infringement via Outflow)           │
│  ├─ Third parties use AI trained on proprietary materials       │
│  └─ Near-identical generated outputs appear in market           │
│                                                                 │
│  TH-3: Confidential Leakage                                     │
│  ├─ Unreleased characters/designs/footage/code fed to AI        │
│  └─ Leakage via training data pathways                          │
│                                                                 │
│  TH-4: Deepfake / Persona Abuse                                 │
│  ├─ Private images/video used without consent                   │
│  └─ Defamation, sexual content, harassment                      │
│                                                                 │
│  TH-5: Brand/Style Mimicry                                      │
│  ├─ Corporate web/IR/design tone imitated                       │
│  └─ Generated content mistaken for official                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 4.2 Threat Actor Analysis

| Actor | Description | Related Threats |
|-------|-------------|-----------------|
| **External Attackers** | Malicious third parties | TH-2, TH-4, TH-5 |
| **Internal Actors** | Employees, contractors, outsourcing | TH-3, TH-2 |
| **AI Vendors** | Model providers, SaaS providers | TH-2, TH-3 |
| **End Users** | Generative AI service users | TH-1, TH-4, TH-5 |
| **Competitors** | Industry rivals | TH-1, TH-2, TH-5 |

### 4.3 Attack Surface by Lifecycle Stage

```
Asset Input       Training        Generation       Distribution
(INGEST)          (TRAIN)         (GEN)            (EXPORT)
    │                │                │                │
    ▼                ▼                ▼                ▼
┌────────┐      ┌────────┐      ┌────────┐      ┌────────┐
│ Rights │      │Consent │      │Similarity│     │ Leak   │
│Unclear │      │Violation│     │ Issues  │      │ Path   │
└────────┘      └────────┘      └────────┘      └────────┘
    │                │                │                │
    ▼                ▼                ▼                ▼
TH-1,TH-3        TH-2,TH-3        TH-1,TH-4        TH-2,TH-5
```

### 4.4 Threat-to-Field Mapping

CAP fields provide evidence against each threat:

| Threat | Corresponding Fields | Recorded Content |
|--------|---------------------|------------------|
| TH-1: IP Dilution | AssetID, RightsBasis | Original asset identification and rights basis |
| TH-2: Reverse Flow | AssetID, ModelContext | Model and materials used in training |
| TH-3: Confidential Leak | ConfidentialityLevel, Timestamp | Classification and timing of access |
| TH-4: Persona Abuse | ConsentBasis, User | Consent state and actor identification |
| TH-5: Brand Mimicry | AssetHash, PromptHash | Input/output fingerprints for forensics |

---

## 5. Event Model

### 5.1 Core Event Types

CAP defines four core event types covering the AI content workflow:

```
┌─────────────────────────────────────────────────────────────────┐
│                    CAP Core Event Flow                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐     │
│  │ INGEST  │───▶│  TRAIN  │───▶│   GEN   │───▶│ EXPORT  │     │
│  └─────────┘    └─────────┘    └─────────┘    └─────────┘     │
│       │              │              │              │           │
│       ▼              ▼              ▼              ▼           │
│   Asset Input    Model         Generation      Output          │
│   (Material      Training      (Create new     Delivery        │
│    intake)                      content)                       │
│                                                                 │
│  [Optional stages - not all workflows use all events]          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 5.2 Event Type Registry

| Code | Event Type | Phase | Description | Required |
|------|------------|-------|-------------|----------|
| 0x0100 | `INGEST` | Input | Asset ingestion into AI workflow | SHOULD |
| 0x0200 | `TRAIN` | Training | Model training/fine-tuning | MAY |
| 0x0300 | `GEN` | Generation | Content generation (allowed) | MUST |
| 0x0310 | `GEN_ATTEMPT` | Pre-generation | Generation request received | SHOULD* |
| 0x0311 | `GEN_DENY` | Decision | Generation refused | SHOULD* |
| 0x0312 | `GEN_WARN` | Decision | Allowed with warning | MAY* |
| 0x0313 | `GEN_ESCALATE` | Decision | Escalated to human review | MAY* |
| 0x0314 | `GEN_QUARANTINE` | Decision | Generated but quarantined | MAY* |
| 0x0400 | `EXPORT` | Output | Asset delivery/publication | SHOULD |
| 0x0F00 | `AUDIT_ANCHOR` | System | External anchoring event | MAY |

*Part of SRP Extension (Part II)

### 5.3 Event Definitions

#### 5.3.1 INGEST Event

Records the ingestion of assets into an AI workflow.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `EventType` | String | MUST | "INGEST" |
| `AssetID` | URN | MUST | Unique asset identifier |
| `AssetHash` | String | MUST | SHA-256 hash of asset content |
| `AssetType` | Enum | MUST | IMAGE, VIDEO, AUDIO, TEXT, CODE, OTHER |
| `RightsBasis` | Enum | MUST | Rights justification (see 6.2) |
| `ConsentBasis` | Enum | SHOULD | Consent state (see 6.2) |
| `ConfidentialityLevel` | Enum | SHOULD | Classification level (see 6.4) |

#### 5.3.2 TRAIN Event

Records model training or fine-tuning activities.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `EventType` | String | MUST | "TRAIN" |
| `TrainingType` | Enum | MUST | PRETRAIN, FINETUNE, LORA, RLHF, OTHER |
| `InputAssetIDs` | Array | MUST | Assets used for training |
| `OutputModelID` | URN | MUST | Resulting model identifier |
| `BaseModelID` | URN | SHOULD | Base model if fine-tuning |

#### 5.3.3 GEN Event

Records content generation activities (when allowed).

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `EventType` | String | MUST | "GEN" |
| `PromptHash` | String | MUST | SHA-256 hash of prompt (privacy-preserving) |
| `OutputAssetID` | URN | MUST | Generated asset identifier |
| `OutputAssetHash` | String | MUST | Hash of generated content |
| `ModelContext` | Object | MUST | Model information (see 6.5) |
| `AttemptID` | UUID | SHOULD* | Reference to GEN_ATTEMPT (*required if SRP enabled) |

#### 5.3.4 EXPORT Event

Records asset delivery or publication.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `EventType` | String | MUST | "EXPORT" |
| `AssetID` | URN | MUST | Exported asset identifier |
| `Destination` | String | MUST | Recipient identifier |
| `DestinationType` | Enum | MUST | DELIVERY, PUBLICATION, ARCHIVE, OTHER |
| `PermittedUse` | Object | SHOULD | Usage restrictions applied |

---

## 6. Data Model

### 6.1 CAP-CORE: Common Fields

All CAP events MUST include these core fields:

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 0001 | `EventID` | UUID v7 | Unique event identifier | Time-ordered |
| 0002 | `ChainID` | UUID | Evidence chain identifier | Links related events |
| 0003 | `PrevHash` | String | Hash of previous event | null for genesis |
| 0004 | `Timestamp` | ISO 8601 | Event creation time | Millisecond precision, UTC |
| 0005 | `EventType` | Enum | Event type code | See Event Type Registry |
| 0006 | `HashAlgo` | String | Hash algorithm | Default: "SHA256" |
| 0007 | `SignAlgo` | String | Signature algorithm | Default: "ED25519" |
| 0008 | `EventHash` | String | Hash of this event | Computed after all fields set |
| 0009 | `Signature` | String | Digital signature | Optional but RECOMMENDED |

### 6.2 CAP-RIGHTS: Rights and Consent

| Tag | Field | Type | Description |
|-----|-------|------|-------------|
| 2001 | `RightsBasis` | Enum | Rights justification |
| 2002 | `RightsHolder` | String | Rights holder identifier |
| 2003 | `ConsentBasis` | Enum | Consent state |
| 2004 | `ConsentReference` | String | Reference to consent document |
| 2010 | `PermittedUse` | Object | Usage permissions |

#### RightsBasis Enum

| Value | Description | Example |
|-------|-------------|---------|
| `OWNED` | Own original work | Created by organization |
| `LICENSED` | Licensed from third party | Stock footage with license |
| `PUBLIC_DOMAIN` | No copyright restrictions | Expired copyright, CC0 |
| `FAIR_USE` | Fair use/dealing claim | Commentary, parody |
| `STATUTORY_EXCEPTION` | Statutory exception applies | Japan Art. 30-4 |
| `UNKNOWN` | Rights unclear | Legacy materials |

#### ConsentBasis Enum

| Value | Description |
|-------|-------------|
| `EXPLICIT_WRITTEN` | Written consent obtained |
| `EXPLICIT_VERBAL` | Verbal consent recorded |
| `IMPLIED` | Consent implied by contract/relationship |
| `NOT_REQUIRED` | Own materials, no consent needed |
| `OPTED_OUT` | Subject explicitly opted out |
| `UNKNOWN` | Consent state unclear |

### 6.3 CAP-PERMISSIONS: Usage Rights

The `PermittedUse` object specifies allowed usage:

```json
{
  "PermittedUse": {
    "Training": true,
    "Generation": true,
    "Distribution": false,
    "Commercial": true,
    "Derivative": true,
    "Attribution": true,
    "Restrictions": [
      "NO_ADULT_CONTENT",
      "TERRITORY_JP_ONLY"
    ]
  }
}
```

### 6.4 CAP-CONFIDENTIALITY: Classification

| Tag | Field | Type | Description |
|-----|-------|------|-------------|
| 4001 | `ConfidentialityLevel` | Enum | Classification level |
| 4002 | `ClassificationDate` | ISO 8601 | When classified |
| 4003 | `Classifier` | String | Who classified |
| 4010 | `ReleaseDate` | ISO 8601 | Planned release date |

#### ConfidentialityLevel Enum

| Value | Description | AI Workflow Restriction |
|-------|-------------|------------------------|
| `PUBLIC` | Public information | No restrictions |
| `INTERNAL` | Internal only | Internal environments only |
| `CONFIDENTIAL` | Confidential | Named recipients only |
| `SECRET` | Top secret | Strict access control |
| `PRE_RELEASE` | Pre-release | Embargoed until release date |

### 6.5 CAP-CONTEXT: Model and User Context

#### Model Context Fields

| Tag | Field | Type | Description |
|-----|-------|------|-------------|
| 5001 | `ModelID` | String | Model identifier |
| 5002 | `ModelVersion` | String | Model version |
| 5003 | `ModelType` | Enum | LLM, IMAGE_GEN, AUDIO_GEN, VIDEO_GEN, OTHER |
| 5004 | `ModelProvider` | String | Model provider |
| 5005 | `Environment` | Enum | LOCAL, CLOUD, HYBRID, API |

#### User Context Fields

| Tag | Field | Type | Description |
|-----|-------|------|-------------|
| 5101 | `UserID` | String | User identifier (may be hashed) |
| 5102 | `Role` | Enum | CREATOR, ENGINEER, REVIEWER, MANAGER, SYSTEM |
| 5103 | `Department` | String | Organizational unit |
| 5104 | `SessionID` | String | Session identifier for correlation |

---

## 7. Integrity Layer

### 7.1 Hash Chain Structure

All events are linked in a hash chain for tamper detection:

```
Event 0 (Genesis)
    │
    ├── PrevHash: null
    ├── EventHash: sha256:a1b2c3...
    │
    ▼
Event 1 (INGEST)
    │
    ├── PrevHash: sha256:a1b2c3...
    ├── EventHash: sha256:d4e5f6...
    │
    ▼
Event 2 (GEN)
    │
    ├── PrevHash: sha256:d4e5f6...
    ├── EventHash: sha256:g7h8i9...
    │
    ...
```

### 7.2 Event Hash Computation

```
1. Create event object WITHOUT EventHash and Signature fields
2. JSON-canonicalize per RFC 8785 (JCS)
3. Encode as UTF-8 bytes
4. Compute SHA-256
5. Prefix with "sha256:"
```

### 7.3 Digital Signature

```
1. Obtain EventHash
2. Sign with Ed25519 private key
3. Base64-encode signature
4. Prefix with "ed25519:"
```

### 7.4 Merkle Anchoring (Optional)

For external anchoring (recommended for L3 implementations):

```json
{
  "EventType": "AUDIT_ANCHOR",
  "Timestamp": "2026-01-10T24:00:00Z",
  "MerkleRoot": "sha256:...",
  "Anchor": {
    "Type": "ethereum",
    "TxHash": "0x7fe4c...",
    "BlockNumber": 21504987
  }
}
```

Supported anchor types:
- `ethereum` — Ethereum mainnet transaction
- `rfc3161` — RFC 3161 Timestamp Authority
- `github_release` — GitHub release with timestamp

---

## 8. Compliance Philosophy

### 8.1 Record Evidence, Not Make Judgments

CAP's philosophy is summarized as:

> **"Verify, Don't Trust"**

| Traditional Approach | CAP Approach |
|---------------------|--------------|
| "We have policies. Trust us." | "We have policies. Here's the cryptographic proof." |
| Compliance by declaration | Compliance by evidence |
| Post-hoc investigation difficult | Post-hoc verification enabled |

### 8.2 Third-Party Verifiability

Any qualified third party can:
1. Recalculate event hashes
2. Verify chain linkage
3. Verify digital signatures
4. Confirm external anchors

No access to proprietary systems required for basic verification.

### 8.3 Privacy-Preserving Design

CAP stores **hashes** rather than raw content:
- `PromptHash`: Hash of prompt, not the prompt text
- `AssetHash`: Hash of content, not the content itself
- `UserID`: May be hashed for anonymization

This supports GDPR Article 17 (right to erasure) compliance.

---

## 9. Non-Goals

### 9.1 Explicit Exclusions

CAP explicitly does NOT:

| Non-Goal | Description | Reason |
|----------|-------------|--------|
| **Prohibit AI Usage** | Does not block or censor AI | Evidence recording, not judgment |
| **Auto-Detect Infringement** | Does not automatically determine copyright violation | Legal determination is for courts |
| **Similarity = Illegality** | Does not equate similarity to illegality | Similar outputs may be legal |
| **Expose Model Internals** | Does not require model weights disclosure | Trade secret protection |
| **Real-Time Control** | Does not intervene in AI decisions | Focused on post-hoc verification |
| **Quality Evaluation** | Does not assess output quality | Subjective judgment out of scope |

### 9.2 Boundary Clarification

```
┌─────────────────────────────────────────────────────────────────┐
│                     CAP Responsibility Scope                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  What CAP DOES                │  What CAP Does NOT              │
│  ──────────────────           │  ──────────────────             │
│  ✓ Record events              │  ✗ Approve/reject events        │
│  ✓ Cryptographic protection   │  ✗ Censor content               │
│  ✓ Track provenance           │  ✗ Determine infringement       │
│  ✓ Enable auditing            │  ✗ Enforce penalties            │
│  ✓ Ensure interoperability    │  ✗ Mandate specific tech        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 10. Regulatory Alignment

### 10.1 Applicable Regulations

CAP provides connection points to these regulations:

| Regulation | Jurisdiction | CAP-Relevant Requirements |
|------------|--------------|--------------------------|
| **EU AI Act** | EU | Art.12 logging, Art.53 transparency |
| **Digital Services Act (DSA)** | EU | AI content disclosure |
| **GDPR** | EU | Processing records, consent management |
| **Copyright Directive** | EU | TDM exception, opt-out |
| **TAKE IT DOWN Act** | USA | NCII evidence requirements |
| **Copyright Law Art. 30-4** | Japan | AI training exception documentation |

### 10.2 EU AI Act Alignment

EU AI Act Article 12 (Logging) correspondence:

| EU AI Act Requirement | CAP Field | Status |
|----------------------|-----------|--------|
| Automatic event logging | EventID, Timestamp | ✓ Supported |
| Input data tracing | AssetID, AssetHash | ✓ Supported |
| Output identification | OutputAssetID | ✓ Supported |
| Human oversight records | UserID, Role | ✓ Supported |
| Retention for lifetime | Hash Chain, Merkle Anchor | ✓ Supported |

### 10.3 DSA Article 35 Alignment

For systemic risk mitigation in generative AI:

| DSA Requirement | CAP Capability |
|-----------------|----------------|
| Risk mitigation measures | GEN_DENY events prove refusals |
| Audit trail | Complete event chain |
| Reporting | Evidence Pack statistics |

### 10.4 Compliance Note

> This specification provides technical capabilities for audit defensibility. It does not constitute legal advice. Consult legal counsel for jurisdiction-specific compliance requirements.

---

## 11. Implementation Guidelines

### 11.1 Implementation Levels

| Level | Name | Requirements | Target Users |
|-------|------|--------------|--------------|
| **L1** | Basic | INGEST/GEN events | Small studios, individuals |
| **L2** | Standard | All 4 events, Hash Chain | Mid-size production companies |
| **L3** | Enterprise | L2 + Merkle Anchor, external verification | Major publishers |

### 11.2 Minimum Viable Implementation (L1)

Requirements for minimum implementation:

1. **INGEST recording**: AssetID, RightsBasis, User for input materials
2. **GEN recording**: OutputAssetID, ModelContext, User for generations
3. **Local storage**: JSON format event logs
4. **Basic integrity**: SHA-256 event hashing

### 11.3 Performance Targets

| Metric | L1 | L2 | L3 |
|--------|----|----|----| 
| Event creation | <100ms | <50ms | <10ms |
| Chain verification | >100 events/sec | >500 events/sec | >1000 events/sec |
| Evidence pack export | <30 sec | <10 sec | <5 sec |

---

# Part II: SRP Extension (Safe Refusal Provenance)

---

## 12. SRP Introduction

### 12.1 Overview

**SRP (Safe Refusal Provenance)** extends CAP to provide cryptographic evidence of AI content moderation decisions—specifically, proof that harmful generation requests were **received, evaluated, and refused**.

> **This extension defines events that prove a generation request was received AND refused.**
>
> **The resulting evidence pack contains no unsafe prompts or NSFW outputs.**
>
> **Any third party can verify integrity and completeness using hash-chain + signatures.**

### 12.2 Background

The December 2025–January 2026 Grok incident exposed a critical weakness in AI content moderation: **there is no standard way to prove that dangerous content was NOT generated**.

xAI claimed to have safeguards, but could not provide:
- Evidence that specific requests were refused
- Proof that refusal logs weren't tampered with
- Verification that "all" dangerous requests were blocked (not selectively logged)

### 12.3 The Core Problem

| Event Type | Current Systems | With SRP |
|------------|-----------------|----------|
| Generation allowed | ✓ Logged | ✓ Logged |
| Generation refused | ✗ No record | ✓ Cryptographically proven |

When regulators ask "Prove your safeguards worked," existing systems cannot answer. SRP closes this gap.

### 12.4 Solution

SRP introduces two key event types:

1. **GEN_ATTEMPT** — Records that a generation request was received
2. **GEN_DENY** — Records that the request was refused (with reason)

The critical audit invariant:
> **Every GEN_ATTEMPT MUST have exactly one corresponding GEN or GEN_DENY event.**

This prevents selective logging attacks where operators only show favorable outcomes.

---

## 13. SRP Event Model

### 13.1 Event Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                     SRP Event Lifecycle                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Request Received                                               │
│       │                                                         │
│       ▼                                                         │
│  ┌─────────────────┐                                           │
│  │  GEN_ATTEMPT    │ ← MUST be recorded for every request      │
│  └────────┬────────┘                                           │
│           │                                                     │
│           ▼                                                     │
│  ┌─────────────────┐                                           │
│  │ Risk Assessment │                                           │
│  │ ├─ CSAM check   │                                           │
│  │ ├─ NCII check   │                                           │
│  │ ├─ Violence     │                                           │
│  │ └─ Policy match │                                           │
│  └────────┬────────┘                                           │
│           │                                                     │
│           ├─────────────────────┐                              │
│           │                     │                               │
│           ▼                     ▼                               │
│    Risk < Threshold      Risk >= Threshold                     │
│           │                     │                               │
│           ▼                     ▼                               │
│      ┌─────────┐          ┌─────────┐                         │
│      │   GEN   │          │ GEN_DENY│                         │
│      │ (allow) │          │ (refuse)│                         │
│      └─────────┘          └─────────┘                         │
│                                                                 │
│  INVARIANT: count(GEN_ATTEMPT) == count(GEN) + count(GEN_DENY) │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 13.2 SRP Event Type Registry

| Code | Event Type | Phase | Description |
|------|------------|-------|-------------|
| 0x0310 | `GEN_ATTEMPT` | Pre-generation | Generation request received |
| 0x0311 | `GEN_DENY` | Decision | Generation refused |
| 0x0312 | `GEN_WARN` | Decision | Allowed with warning |
| 0x0313 | `GEN_ESCALATE` | Decision | Escalated to human review |
| 0x0314 | `GEN_QUARANTINE` | Decision | Generated but quarantined |
| 0x0300 | `GEN` | Output | Generation completed (allowed) |

### 13.3 Event Linking

GEN_DENY (and other outcome events) MUST include an `AttemptID` field referencing the corresponding GEN_ATTEMPT:

```
GEN_ATTEMPT (EventID: "abc-123")
     │
     └──► GEN_DENY (AttemptID: "abc-123")
```

### 13.4 Risk Categories

| Value | Description | Examples |
|-------|-------------|----------|
| `CSAM_RISK` | Child sexual abuse material | Minor detected in sexualized context |
| `NCII_RISK` | Non-consensual intimate imagery | Undressing request with person photo |
| `MINOR_SEXUALIZATION` | Sexualization of minors | Age-inappropriate prompt with young subject |
| `REAL_PERSON_DEEPFAKE` | Unauthorized real person imagery | Celebrity face swap request |
| `VIOLENCE_EXTREME` | Extreme violence/gore | Graphic injury generation |
| `HATE_CONTENT` | Hate speech or discrimination | Slurs, dehumanization |
| `TERRORIST_CONTENT` | Terrorism promotion | Extremist propaganda |
| `SELF_HARM_PROMOTION` | Self-harm encouragement | Suicide methods |
| `OTHER` | Other policy violation | Platform-specific rules |

---

## 14. SRP Data Model

### 14.1 GEN_ATTEMPT Event

Records that a generation request was received (before risk assessment).

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `EventType` | String | MUST | "GEN_ATTEMPT" |
| `EventID` | UUID v7 | MUST | Unique event identifier |
| `Timestamp` | ISO 8601 | MUST | Request received time |
| `PromptHash` | String | MUST | SHA-256 hash of prompt |
| `ReferenceImageHash` | String | MAY | Hash of reference image if provided |
| `InputType` | Enum | SHOULD | text, image, text+image, video, audio |
| `PolicyID` | String | MUST | Policy identifier |
| `ModelVersion` | String | MUST | Model identifier |
| `SessionID` | UUID | MAY | Session identifier |
| `ActorHash` | String | MAY | Anonymized user hash |
| `PreviousHash` | String | MUST | Hash of previous event |

### 14.2 GEN_DENY Event

Records that a generation request was refused.

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `EventType` | String | MUST | "GEN_DENY" |
| `EventID` | UUID v7 | MUST | Unique event identifier |
| `Timestamp` | ISO 8601 | MUST | Decision time |
| `AttemptID` | UUID | MUST | Reference to GEN_ATTEMPT |
| `RiskCategory` | Enum | MUST | Primary risk category |
| `RiskSubCategories` | Array | MAY | Additional risk tags |
| `RiskScore` | Float | MUST | 0.0 to 1.0 confidence score |
| `RefusalReason` | String | SHOULD | Human-readable explanation |
| `ModelDecision` | Enum | MUST | DENY, WARN, ESCALATE, QUARANTINE |
| `HumanOverride` | Boolean | MUST | Whether human overrode model |
| `PreviousHash` | String | MUST | Hash of previous event |

---

## 15. Completeness Verification

### 15.1 The Completeness Invariant

> **For every `GEN_ATTEMPT` event, there MUST exist exactly one outcome event (`GEN`, `GEN_DENY`, `GEN_WARN`, `GEN_ESCALATE`, or `GEN_QUARANTINE`) with a matching `AttemptID`.**

This prevents:
- Hiding successful generations of harmful content
- Selectively logging only refusals
- Claiming refusals that never had corresponding attempts

### 15.2 Verification Algorithm

```python
def verify_completeness(events):
    attempts = {e.EventID for e in events if e.EventType == "GEN_ATTEMPT"}
    outcomes = {e.AttemptID for e in events if e.EventType in OUTCOME_TYPES}
    
    unmatched_attempts = attempts - outcomes
    orphan_outcomes = outcomes - attempts
    
    return {
        "complete": len(unmatched_attempts) == 0 and len(orphan_outcomes) == 0,
        "unmatched_attempts": list(unmatched_attempts),
        "orphan_outcomes": list(orphan_outcomes)
    }
```

### 15.3 What Completeness Proves

| Check | Implication |
|-------|-------------|
| No unmatched attempts | Every request has a recorded decision |
| No orphan outcomes | Every decision corresponds to a real request |
| Count invariant holds | Complete audit trail exists |

---

## 16. Evidence Pack Structure

### 16.1 Directory Layout

```
evidence-pack-{chain_id}/
├── manifest.json           # Pack metadata and verification
├── events/
│   ├── 0001-gen_attempt.json
│   ├── 0002-gen_deny.json
│   ├── 0003-gen_attempt.json
│   ├── 0004-gen.json
│   └── ...
├── chain/
│   └── hash_chain.json     # Complete event chain
├── statistics/
│   └── refusal_stats.json  # Aggregated metrics (auditor focus)
├── signatures/
│   └── chain-signature.sig # Optional chain-level signature
└── verification/
    ├── merkle_root.json    # For external anchoring (L3)
    └── instructions.md     # Verification guide
```

### 16.2 Statistics File

The `refusal_stats.json` is typically **the first document reviewed by auditors**:

```json
{
  "period": {
    "start": "2026-01-01T00:00:00Z",
    "end": "2026-01-31T23:59:59Z"
  },
  "totalAttempts": 1000000,
  "totalRefusals": 2847,
  "totalAllowed": 997153,
  "refusalRate": 0.002847,
  "completenessCheck": "PASSED",
  "byCategory": {
    "CSAM_RISK": 12,
    "NCII_RISK": 1523,
    "MINOR_SEXUALIZATION": 89,
    "REAL_PERSON_DEEPFAKE": 956,
    "VIOLENCE_EXTREME": 124,
    "HATE_CONTENT": 98,
    "OTHER": 45
  },
  "chainIntegrity": "VERIFIED"
}
```

### 16.3 Manifest File

```json
{
  "manifestVersion": "1.0",
  "packId": "01945f6e-cf70-bf37-df7e-5678901234ef",
  "chainId": "01945e3a-6a1b-7c82-9d1b-0987654321dc",
  "createdAt": "2026-01-10T15:00:00.000Z",
  "capVersion": "0.2.0",
  "srpVersion": "0.2.0",
  "eventCount": 4,
  "completenessCheck": "PASSED",
  "chainIntegrity": "VERIFIED",
  "genesisHash": "sha256:...",
  "headHash": "sha256:..."
}
```

---

## 17. Privacy Considerations

### 17.1 Prompt Hashing (REQUIRED)

Original prompts MUST NOT be stored. Only SHA-256 hashes are recorded.

```python
# ✓ Correct
prompt_hash = "sha256:" + hashlib.sha256(prompt.encode()).hexdigest()

# ✗ Prohibited
prompt_text = prompt  # Never store raw prompts
```

### 17.2 Actor Anonymization (RECOMMENDED)

If user identifiers are recorded:
- Use irreversible hashes, OR
- Apply k-anonymity (k ≥ 5), OR
- Use pseudonymization with secured key

### 17.3 GDPR Compliance

This design supports GDPR Article 17 (right to erasure):
- No personal data in event fields
- Hash-based references are not "personal data" under typical interpretation
- Deletion requests can be honored without breaking chain integrity

---

## 18. SRP Regulatory Alignment

### 18.1 EU AI Act Article 12

| Requirement | SRP Capability |
|-------------|----------------|
| Automatic logging | GEN_ATTEMPT + outcome events |
| Lifetime retention | Hash chain with external anchoring |
| Traceability | AttemptID linking |
| Human oversight records | HumanOverride field |

### 18.2 EU DSA Article 35

| Requirement | SRP Capability |
|-------------|----------------|
| Risk mitigation measures | GEN_DENY as mitigation evidence |
| Audit trail | Complete event chain |
| Reporting | statistics/refusal_stats.json |

### 18.3 TAKE IT DOWN Act

| Requirement | SRP Capability |
|-------------|----------------|
| 48-hour response | Timestamp proof |
| Removal evidence | "Never generated" via GEN_DENY |
| Victim notification | Shareable evidence pack |

---

## 19. Third-Party Verification

### 19.1 Verification Steps (< 2 minutes)

1. **Verify hash chain:**
   ```
   For each event[n]:
     assert event[n].PreviousHash == event[n-1].EventHash
   ```

2. **Verify event hashes:**
   ```
   For each event:
     computed = sha256(canonicalize(event without hash/sig))
     assert computed == event.EventHash
   ```

3. **Verify signatures (if Ed25519 key available):**
   ```
   For each event:
     assert ed25519_verify(pubkey, event.EventHash, event.Signature)
   ```

4. **Verify completeness:**
   ```
   assert all GEN_ATTEMPTs have matching outcomes
   assert no orphan outcomes exist
   ```

5. **Optional: Verify external anchor:**
   ```
   assert merkle_root in anchor.reference
   ```

### 19.2 What Verification Proves

✓ Events have not been modified after creation  
✓ Events have not been deleted from the chain  
✓ Events have not been reordered  
✓ Every generation attempt has a recorded outcome  
✓ Refusals actually occurred at the claimed times

---

# Appendices

---

## Appendix A: JSON Schema

### A.1 CAP Core Event Schema

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://veritaschain.org/schemas/cap/core-event.json",
  "title": "CAP Core Event",
  "type": "object",
  "required": ["EventID", "ChainID", "Timestamp", "EventType", "HashAlgo"],
  "properties": {
    "EventID": {
      "type": "string",
      "format": "uuid",
      "description": "UUID v7 event identifier"
    },
    "ChainID": {
      "type": "string",
      "format": "uuid",
      "description": "Evidence chain identifier"
    },
    "PrevHash": {
      "type": ["string", "null"],
      "pattern": "^sha256:[a-f0-9]{64}$",
      "description": "Hash of previous event (null for genesis)"
    },
    "Timestamp": {
      "type": "string",
      "format": "date-time",
      "description": "ISO 8601 timestamp with millisecond precision"
    },
    "EventType": {
      "type": "string",
      "enum": ["INGEST", "TRAIN", "GEN", "GEN_ATTEMPT", "GEN_DENY", "GEN_WARN", "GEN_ESCALATE", "GEN_QUARANTINE", "EXPORT", "AUDIT_ANCHOR"],
      "description": "Event type"
    },
    "HashAlgo": { "type": "string", "default": "SHA256" },
    "SignAlgo": { "type": "string", "default": "ED25519" },
    "EventHash": { "type": "string", "pattern": "^sha256:[a-f0-9]{64}$" },
    "Signature": { "type": "string", "pattern": "^ed25519:[a-zA-Z0-9+/=]+$" }
  }
}
```

### A.2 GEN_ATTEMPT Schema

```json
{
  "$id": "https://veritaschain.org/schemas/cap/srp/gen-attempt.json",
  "title": "CAP-SRP GEN_ATTEMPT Event",
  "type": "object",
  "required": ["EventType", "EventID", "Timestamp", "PromptHash", "PolicyID", "ModelVersion", "PreviousHash"],
  "properties": {
    "EventType": { "const": "GEN_ATTEMPT" },
    "PromptHash": { "type": "string", "pattern": "^sha256:[a-f0-9]{64}$" },
    "ReferenceImageHash": { "type": "string", "pattern": "^sha256:[a-f0-9]{64}$" },
    "InputType": { "type": "string", "enum": ["text", "image", "text+image", "video", "audio"] },
    "PolicyID": { "type": "string" },
    "ModelVersion": { "type": "string" },
    "SessionID": { "type": "string", "format": "uuid" },
    "ActorHash": { "type": "string", "pattern": "^sha256:[a-f0-9]{64}$" }
  }
}
```

### A.3 GEN_DENY Schema

```json
{
  "$id": "https://veritaschain.org/schemas/cap/srp/gen-deny.json",
  "title": "CAP-SRP GEN_DENY Event",
  "type": "object",
  "required": ["EventType", "EventID", "Timestamp", "AttemptID", "RiskCategory", "RiskScore", "ModelDecision", "HumanOverride", "PreviousHash"],
  "properties": {
    "EventType": { "const": "GEN_DENY" },
    "AttemptID": { "type": "string", "format": "uuid" },
    "RiskCategory": {
      "type": "string",
      "enum": ["CSAM_RISK", "NCII_RISK", "MINOR_SEXUALIZATION", "REAL_PERSON_DEEPFAKE", "VIOLENCE_EXTREME", "HATE_CONTENT", "TERRORIST_CONTENT", "SELF_HARM_PROMOTION", "OTHER"]
    },
    "RiskSubCategories": { "type": "array", "items": { "type": "string" } },
    "RiskScore": { "type": "number", "minimum": 0.0, "maximum": 1.0 },
    "RefusalReason": { "type": "string" },
    "ModelDecision": { "type": "string", "enum": ["DENY", "WARN", "ESCALATE", "QUARANTINE"] },
    "HumanOverride": { "type": "boolean" }
  }
}
```

---

## Appendix B: JSON Examples

### B.1 INGEST Event Example

```json
{
  "EventID": "01945f2a-8b3c-7f93-9f3a-1234567890ab",
  "ChainID": "01945e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": null,
  "Timestamp": "2026-01-10T10:00:00.000Z",
  "EventType": "INGEST",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  "Asset": {
    "AssetID": "urn:cap:asset:studio-a:char-design-001",
    "AssetType": "IMAGE",
    "AssetHash": "sha256:a7ffc6f8bf1ed76651c14756a061d662f580ff4de43b49fa82d80a4b80f8434a",
    "AssetName": "Main Character Design Draft A"
  },
  "Rights": {
    "RightsBasis": "OWNED",
    "RightsHolder": "studio-a",
    "ConsentBasis": "NOT_REQUIRED",
    "PermittedUse": { "Training": true, "Generation": true, "Distribution": false, "Commercial": true }
  },
  "Confidentiality": {
    "ConfidentialityLevel": "PRE_RELEASE",
    "ReleaseDate": "2026-04-01T00:00:00.000Z"
  },
  "Context": { "UserID": "user-12345", "Role": "CREATOR", "Department": "Character Design" },
  "EventHash": "sha256:b8ffc7f9cf2fe87762d25867b172e773f691ff5ef54c5afb93e91b5c91f9545b",
  "Signature": "ed25519:MEUCIQDh..."
}
```

### B.2 GEN Event Example

```json
{
  "EventID": "01945f4c-ad5e-9f15-bf5c-3456789012cd",
  "ChainID": "01945e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": "sha256:c9ffd8fadf3ff98873e36978c283f884fa02ff6f...",
  "Timestamp": "2026-01-10T12:00:00.000Z",
  "EventType": "GEN",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  "Generation": {
    "PromptHash": "sha256:d0ffe9fbef4ffa9984f47a89d394f995fb13ff7f...",
    "OutputAssetID": "urn:cap:asset:studio-a:gen-char-001",
    "OutputAssetHash": "sha256:e1fff0fcff5ffba095f58b9ae4a5fa06fc24ff8f..."
  },
  "ModelContext": {
    "ModelID": "urn:cap:model:studio-a:char-lora-v1",
    "ModelVersion": "1.0",
    "ModelType": "IMAGE_GEN",
    "ModelProvider": "Internal",
    "Environment": "LOCAL"
  },
  "Context": { "UserID": "user-12345", "Role": "CREATOR", "SessionID": "session-abc123" },
  "EventHash": "sha256:f2fff1fdff6ffcb1a6f69c0bf5b6fb17fd35ff9f...",
  "Signature": "ed25519:MEQCIEDg..."
}
```

---

## Appendix C: SRP Event Examples

### C.1 GEN_ATTEMPT Event (Request Received)

```json
{
  "EventID": "019467a1-0001-7000-0000-000000000001",
  "ChainID": "019467a0-0000-7000-0000-000000000000",
  "PrevHash": "sha256:0000000000000000000000000000000000000000000000000000000000000000",
  "Timestamp": "2026-01-10T14:23:45.100Z",
  "EventType": "GEN_ATTEMPT",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  "PromptHash": "sha256:7f83b1657ff1fc53b92dc18148a1d65dfc2d4b1fa3d677284addd200126d9069",
  "ReferenceImageHash": "sha256:9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08",
  "InputType": "text+image",
  "PolicyID": "cap.example.safe-refusal.v1",
  "ModelVersion": "img-gen-v4.2.1",
  "SessionID": "019467a1-0001-7000-0000-000000000000",
  "ActorHash": "sha256:e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
  "EventHash": "sha256:a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2",
  "Signature": "ed25519:MEUCIQDhE3H4..."
}
```

### C.2 GEN_DENY Event (Refusal)

```json
{
  "EventID": "019467a1-0001-7000-0000-000000000002",
  "ChainID": "019467a0-0000-7000-0000-000000000000",
  "PrevHash": "sha256:a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2",
  "Timestamp": "2026-01-10T14:23:45.150Z",
  "EventType": "GEN_DENY",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  "AttemptID": "019467a1-0001-7000-0000-000000000001",
  "RiskCategory": "NCII_RISK",
  "RiskSubCategories": ["UPLOADED_PERSON", "CLOTHING_REMOVAL"],
  "RiskScore": 0.94,
  "RefusalReason": "Non-consensual intimate imagery request detected",
  "ModelDecision": "DENY",
  "HumanOverride": false,
  "EventHash": "sha256:e5f6g7h8i9j0e5f6g7h8i9j0e5f6g7h8i9j0e5f6g7h8i9j0e5f6g7h8i9j0e5f6",
  "Signature": "ed25519:MEQCIFRt..."
}
```

---

## References

### Normative References

- [RFC 2119] Key words for use in RFCs to Indicate Requirement Levels
- [RFC 9562] Universally Unique IDentifiers (UUIDs) - UUID Version 7
- [RFC 8785] JSON Canonicalization Scheme (JCS)
- [ISO 8601] Date and time format

### Informative References

- [VAP] Verifiable AI Provenance Framework Specification v1.1
- [VCP] VeritasChain Protocol Specification v1.1
- [EU AI Act] Regulation (EU) 2024/1689
- [EU DSA] Regulation (EU) 2022/2065 - Digital Services Act
- [C2PA] Coalition for Content Provenance and Authenticity Technical Specification

### Related Documents

- VSO-VAP-SPEC-001: VAP Framework Specification
- VSO-VCP-SPEC-001: VCP Protocol Specification
- VSO-CAP-IMPL-001: CAP Implementation Guide (planned)
- VSO-CAP-TEST-001: CAP Conformance Test Suite (planned)

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1.0 | 2025-12-27 | VSO | Initial draft (Japanese) |
| 0.2.0 | 2026-01-10 | VSO | English version, integrated SRP extension, enhanced data model |

---

**© 2025-2026 VeritasChain Standards Organization. All rights reserved.**

This specification is published under CC BY 4.0 International License.

---

**Contact:**
- Website: https://veritaschain.org
- Email: standards@veritaschain.org
- GitHub: https://github.com/veritaschain
