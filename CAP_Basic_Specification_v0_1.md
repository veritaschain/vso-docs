# Content / Creative AI Profile (CAP)

## Basic Specification v0.1

**Document ID:** VSO-CAP-SPEC-001  
**Status:** Draft Specification  
**Version:** 0.1.0  
**Date:** 2025-12-27  
**Maintainer:** VeritasChain Standards Organization (VSO)  
**License:** CC BY 4.0 International  
**Website:** https://veritaschain.org/vap/cap  
**Repository:** https://github.com/veritaschain/vso-docs  
**Contact:** standards@veritaschain.org

---

## Executive Summary

**CAP (Content / Creative AI Profile)** is a new domain profile within the VAP (Verifiable AI Provenance Framework), defining the evidentiary infrastructure for AI usage in content and creative industries.

CAP is NOT a regulation that prohibits or censors AI usage.  
CAP IS a framework for leaving third-party verifiable evidence when disputes arise.

**The fundamental problem is not AI itself, but its black-box nature.**

AI is already extensively used in content industries, and halting its use is unrealistic. What matters is the ability to record—in a cryptographically non-repudiable format—"who," "what," "under what authority," and "when" assets were ingested, trained, generated, or exported in AI workflows, enabling post-hoc verification when disputes over rights infringement, confidential leaks, or persona abuse arise.

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Position within VAP Framework](#2-position-within-vap-framework)
3. [Target Industries](#3-target-industries)
4. [Threat Model](#4-threat-model)
5. [Event Model](#5-event-model)
6. [Data Model](#6-data-model)
7. [Compliance Philosophy](#7-compliance-philosophy)
8. [Non-Goals](#8-non-goals)
9. [Regulatory Alignment](#9-regulatory-alignment)
10. [Implementation Guidelines](#10-implementation-guidelines)
11. [Appendix A: JSON Examples (Non-Normative)](#appendix-a-json-examples-non-normative)
12. [References](#12-references)

---

## 1. Introduction

### 1.1 Purpose

CAP (Content / Creative AI Profile) is an evidentiary framework designed to address the following structural challenges:

| Challenge | Description | CAP Solution |
|-----------|-------------|--------------|
| **Opacity of Rights Provenance** | Rights basis of materials ingested into AI is untraceable | RightsBasis field for recording rights basis |
| **Ambiguity of Consent** | Consent status for training/generation is unclear | ConsentBasis for fixing consent state |
| **Lack of Confidentiality Classification** | Confidentiality of unreleased materials is unmanaged | ConfidentialityLevel for classification |
| **Unclear Responsibility Boundaries** | Responsible parties cannot be identified when disputes arise | User/Role for recording executors |
| **Possibility of Tampering** | Post-hoc record modification is possible | Hash Chain for cryptographic assurance |

### 1.2 Design Philosophy

CAP is based on the following fundamental principle:

> **"Leave evidence, don't stop AI"**

The use of AI in creative activities is irreversibly progressing. CAP takes this reality as a premise and focuses not on prohibition or censorship, but on leaving "evidence that third parties can verify post-hoc."

This enables:
- Rights holders to obtain evidentiary basis when infringement occurs
- Creators to prove legitimate use
- Regulatory authorities to obtain a foundation for audits and inspections
- The industry as a whole to achieve trustworthy AI utilization

### 1.3 Scope Definition

CAP covers:

- AI workflows with **content/IP assets** as the subject
- AI usage processes including **training (TRAIN) and generation (GEN)**
- Evidence recording for **post-hoc verification** when disputes arise

CAP does NOT cover:

- Real-time control or intervention in AI decisions
- Automatic determination of copyright infringement
- Evaluation of the "quality" of generated outputs

### 1.4 Conformance Language

In this specification, the following keywords are interpreted in accordance with RFC 2119:

- **MUST** / **REQUIRED** / **SHALL**: Absolute requirement
- **MUST NOT** / **SHALL NOT**: Absolute prohibition
- **SHOULD** / **RECOMMENDED**: Recommended (deviation acceptable with valid reason)
- **MAY** / **OPTIONAL**: Optional

### 1.5 Terminology

| Term | Definition |
|------|------------|
| **CAP** | Content / Creative AI Profile - VAP profile for content industries |
| **VAP** | Verifiable AI Provenance Framework - Parent framework |
| **VSO** | VeritasChain Standards Organization - Standards body |
| **Asset** | Content/IP asset that is the subject of AI workflows |
| **Provenance** | Cryptographically verifiable record of asset origin, source, and history |
| **Evidence Pack** | Evidence package composed as a collection of CAP events |

---

## 2. Position within VAP Framework

### 2.1 VAP/VSO/CAP Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│     VAP (Verifiable AI Provenance Framework)                    │
│     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                    │
│     "Concept / Parent Framework" for AI decision evidence       │
│     Defines minimum requirements and abstract layer common      │
│     to all domains                                              │
│                                                                 │
│                          ▲                                      │
│                          │ defines & maintains                  │
│                          │                                      │
│     VSO (VeritasChain Standards Organization)                   │
│     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                   │
│     "Standards Body" that develops, maintains, and              │
│     certifies VAP                                               │
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
│     Domain-specific "Concrete Protocol Implementations"         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.2 Relationship to VCP

| Aspect | VCP (Finance Profile) | CAP (Content Profile) |
|--------|----------------------|----------------------|
| **Subject** | Transaction | Content/IP Asset |
| **Target Industry** | Finance, Trading | Gaming, Film, Publishing, Music |
| **Primary Events** | SIG/ORD/EXE/CXL | INGEST/TRAIN/GEN/EXPORT |
| **Regulatory Reference** | MiFID II, EU AI Act | EU AI Act, DSA, Copyright Law |
| **Time Precision Requirements** | Nanoseconds to milliseconds | Seconds to minutes (business-dependent) |
| **Common Foundation** | VAP Integrity Layer | VAP Integrity Layer |

### 2.3 Shared Infrastructure

CAP inherits the following VAP common infrastructure:

- **Hash Chain**: Tamper detection for event chains
- **Merkle Tree**: Efficient verification of large numbers of events
- **Digital Signature**: Issuer authentication via Ed25519
- **Crypto Agility**: Support for future algorithm migration

---

## 3. Target Industries

### 3.1 Priority Classification

Target industries for CAP are classified by the following priorities:

#### Priority A (Highest Priority)

| Industry | Sub-segments | Primary Risks |
|----------|--------------|---------------|
| **Gaming** | AAA/Publishers/Studios/Outsourcing | IP dilution, confidential leaks, character mimicry |
| **Film/Animation/Streaming** | Production/VFX/Post-production/OTT | Actor likeness rights, voice actor audio, unreleased footage leaks |

#### Priority B (Secondary)

| Industry | Sub-segments | Primary Risks |
|----------|--------------|---------------|
| **Publishing** | Manga/Books/Editorial Production | Style mimicry, manuscript leaks, translation quality |
| **Music** | Labels/Distribution/MV Production/PROs | Voice cloning, song mimicry, rights processing |

#### Priority C (Reference)

| Industry | Sub-segments | Primary Risks |
|----------|--------------|---------------|
| **Adult Content** | Production/Distribution/Platforms | Deepfakes, non-consensual generation |
| **Corporate Branding** | Web/IR/Financial Materials/Design | Tone mimicry, brand damage |
| **Education/Training** | Universities/Research Institutions/Corporate Training/Educational Materials | Thesis plagiarism, unauthorized material learning, training document leaks |

### 3.2 Industry-Specific Considerations

Each industry has unique considerations. CAP abstracts these as minimum common denominators while leaving room for industry-specific extensions:

| Industry | Specific Considerations | CAP Response |
|----------|------------------------|--------------|
| Gaming | Long development cycles, large asset volumes | AssetID hierarchy, batch INGEST |
| Film | License complexity, production committees | Multi-stage ConsentBasis, Role extensions |
| Publishing | Derivative work permissions, adaptation rights | Fine-grained PermittedUse |
| Music | Separation of copyright/neighboring rights | Multiple RightsBasis recording |

---

## 4. Threat Model

### 4.1 Overview

Threats addressed by CAP are classified into the following five categories within AI workflows:

```
┌─────────────────────────────────────────────────────────────────┐
│                      CAP Threat Taxonomy                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TH-1: IP Dilution                                              │
│  ├─ Unique expression styles/worldviews easily mimicked by AI   │
│  └─ Dilution of brand value, difficulty in market               │
│      differentiation                                            │
│                                                                 │
│  TH-2: Reverse Flow (Rights Infringement via Backflow)          │
│  ├─ Third parties using AI trained on company's own materials   │
│  └─ Generated outputs closely resembling company's products     │
│      entering the market                                        │
│                                                                 │
│  TH-3: Confidential Leakage                                     │
│  ├─ Unreleased characters/design documents/footage/code         │
│      ingested into AI                                           │
│  └─ Leaked externally via training data                         │
│                                                                 │
│  TH-4: Deepfake / Persona Abuse                                 │
│  ├─ Generation using private images/videos without consent      │
│  └─ Defamation, sexual content, harassment                      │
│                                                                 │
│  TH-5: Brand/Style Mimicry                                      │
│  ├─ Mimicry of corporate website/IR/financial material          │
│      design and tone                                            │
│  └─ Generated outputs misidentified as official                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 4.2 Threat Actor Analysis

| Actor | Description | Related Threats |
|-------|-------------|-----------------|
| **External Attackers** | Malicious third parties | TH-2, TH-4, TH-5 |
| **Internal Parties** | Employees, contractors, outsourcers | TH-3, TH-2 |
| **AI Vendors** | Model providers, SaaS providers | TH-2, TH-3 |
| **End Users** | Generative AI service users | TH-1, TH-4, TH-5 |
| **Competitors** | Industry competitors | TH-1, TH-2, TH-5 |

### 4.3 Attack Surface by Lifecycle Stage

```
Asset Ingestion    Training         Generation       Distribution
(INGEST)          (TRAIN)          (GEN)            (EXPORT)
   │                 │                │                │
   ▼                 ▼                ▼                ▼
┌──────┐        ┌──────┐         ┌──────┐        ┌──────┐
│Rights│        │Consent│        │Simila-│        │Leak  │
│Unclea│        │Violat-│        │rity   │        │Routes│
│r     │        │ion    │        │Issues │        │      │
└──────┘        └──────┘         └──────┘        └──────┘
   │                 │                │                │
   ▼                 ▼                ▼                ▼
TH-1,TH-3        TH-2,TH-3        TH-1,TH-4        TH-2,TH-5
```

### 4.4 Threat-to-Field Mapping

CAP fields provide evidence corresponding to each threat:

| Threat | Corresponding Fields | Recorded Content |
|--------|---------------------|------------------|
| TH-1: IP Dilution | AssetID, RightsBasis | Original asset identification and rights basis |
| TH-2: Reverse Flow | AssetID, ModelContext | Models and materials used in training |
| TH-3: Confidential Leak | ConfidentialityLevel, User | Confidentiality classification and ingester |
| TH-4: Persona Abuse | ConsentBasis, AssetID | Consent status and target asset |
| TH-5: Brand Mimicry | RightsBasis, PermittedUse | Permission scope and usage mode |

---

## 5. Event Model

### 5.1 Core Event Types

CAP defines the following four mandatory event types:

```
┌─────────────────────────────────────────────────────────────────┐
│                    CAP Event Lifecycle                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   INGEST ──────► TRAIN ──────► GEN ──────► EXPORT              │
│     │              │            │            │                  │
│     ▼              ▼            ▼            ▼                  │
│  Asset          Training      Generation   External             │
│  Ingestion      Execution     Execution    Output               │
│                                                                 │
│  • Images       • Full        • Image      • Delivery           │
│  • Videos         Training      Generation • Distribution       │
│  • Audio        • Fine-tuning • Video      • Publication        │
│  • Text         • LoRA/PEFT     Generation • Internal           │
│  • Code         • Embedding   • Audio        Sharing            │
│  • 3D Models                    Synthesis                       │
│                               • Text Gen                        │
│                               • Code Gen                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 5.2 Event Type Definitions

#### 5.2.1 INGEST (Asset Ingestion)

| Attribute | Value |
|-----------|-------|
| **EventType** | INGEST |
| **Code** | 1 |
| **Description** | Ingestion of materials, data, or reference information into AI workflow |
| **Trigger** | Asset input by user or system |
| **Required Fields** | EventID, Timestamp, AssetID, RightsBasis, ConfidentialityLevel, User |

INGEST events record:
- Identification information of ingested assets
- Rights basis (self-produced/licensed/public domain/unknown)
- Confidentiality classification (public/internal/confidential/secret/pre-release)
- Ingester identification information

#### 5.2.2 TRAIN (Training)

| Attribute | Value |
|-----------|-------|
| **EventType** | TRAIN |
| **Code** | 2 |
| **Description** | Model training, additional training, or fine-tuning |
| **Trigger** | Start or completion of training job |
| **Required Fields** | EventID, Timestamp, ModelContext, TrainingType, InputAssetIDs, User |

TRAIN events record:
- Identification information of model being trained
- Training type (full training/additional training/LoRA/PEFT, etc.)
- Asset IDs used as input
- Trainer identification information

#### 5.2.3 GEN (Generation)

| Attribute | Value |
|-----------|-------|
| **EventType** | GEN |
| **Code** | 3 |
| **Description** | Content generation by AI |
| **Trigger** | Execution of generation request |
| **Required Fields** | EventID, Timestamp, ModelContext, OutputAssetID, PromptHash, User |

GEN events record:
- Identification information of model used
- ID of generated output asset
- Hash value of prompt/input (for privacy protection)
- Generator identification information

#### 5.2.4 EXPORT (External Output)

| Attribute | Value |
|-----------|-------|
| **EventType** | EXPORT |
| **Code** | 4 |
| **Description** | External output, distribution, or delivery of generated content |
| **Trigger** | Movement of content outside the organization |
| **Required Fields** | EventID, Timestamp, AssetID, Destination, PermittedUse, User |

EXPORT events record:
- Identification information of output asset
- Destination (delivery destination/publication destination/distribution destination)
- Permitted usage scope
- Exporter identification information

### 5.3 Event Type Registry

```
Content Events (1-19):
1  = INGEST   // Asset ingestion
2  = TRAIN    // Model training
3  = GEN      // Content generation
4  = EXPORT   // External output
5-9           // Reserved for future content events

Consent Events (10-19):
10 = CONSENT_GRANT    // Consent granted
11 = CONSENT_REVOKE   // Consent revoked
12-19                 // Reserved for future consent events

Governance Events (20-29):
20 = POLICY_UPDATE    // Policy change
21 = AUDIT_REQUEST    // Audit request
22-29                 // Reserved for future governance events

System Events (90-99):
98 = HBT      // Heartbeat
99 = ERR      // Error

Extension Events (100-255):
100-255       // Reserved for industry-specific extensions
```

---

## 6. Data Model

### 6.1 CAP-CORE: Standard Header

#### 6.1.1 Required Header Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 1001 | **EventID** | UUID | Unique event identifier | MUST use UUID v7 or v4 |
| 1002 | **ChainID** | UUID | Event chain identifier | Common within same workflow |
| 1003 | **PrevHash** | String | Hash of previous event | For Hash Chain formation |
| 1010 | **Timestamp** | ISO 8601 | Event occurrence time | UTC required, second precision or higher |
| 1011 | **EventType** | Enum | Event type | See Section 5.3 |
| 1020 | **HashAlgo** | Enum | Hash algorithm | SHA256 (default) |
| 1021 | **SignAlgo** | Enum | Signature algorithm | ED25519 (default) |

#### 6.1.2 JSON Schema Example (Header)

```json
{
  "EventID": "01934f2a-8b3c-7f93-9f3a-1234567890ab",
  "ChainID": "01934e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": "a7ffc6f8bf1ed76651c14756a061d662f580ff4de43b49fa82d80a4b80f8434a",
  "Timestamp": "2025-12-27T10:30:00.000Z",
  "EventType": "INGEST",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519"
}
```

### 6.2 CAP-ASSET: Asset Identification

#### 6.2.1 Asset Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 2001 | **AssetID** | String | Asset identifier | Unique within organization, URN format recommended |
| 2002 | **AssetType** | Enum | Asset type | IMAGE/VIDEO/AUDIO/TEXT/CODE/3D/OTHER |
| 2003 | **AssetHash** | String | Hash of asset content | SHA-256, for tamper detection |
| 2004 | **AssetName** | String | Asset name (optional) | Human-readable identification name |
| 2010 | **ParentAssetID** | String | Parent asset ID (optional) | For recording derivative relationships |

#### 6.2.2 AssetType Enum

| Value | Description | Examples |
|-------|-------------|----------|
| **IMAGE** | Still images | PNG, JPEG, PSD, AI, SVG |
| **VIDEO** | Video | MP4, MOV, AVI, ProRes |
| **AUDIO** | Audio/Music | WAV, MP3, FLAC, AAC |
| **TEXT** | Text/Documents | TXT, MD, DOCX, PDF, Script |
| **CODE** | Source code | Python, C++, Shader, Config |
| **3D** | 3D models/assets | FBX, OBJ, GLTF, USD |
| **OTHER** | Other | Composite, uncategorized |

### 6.3 CAP-RIGHTS: Rights and Consent

#### 6.3.1 Rights Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 3001 | **RightsBasis** | Enum | Rights basis | See RightsBasis Enum |
| 3002 | **RightsHolder** | String | Rights holder identifier | Self/third party/multiple |
| 3003 | **LicenseID** | String | License identifier (optional) | Contract number, etc. |
| 3010 | **ConsentBasis** | Enum | Consent basis | See ConsentBasis Enum |
| 3011 | **ConsentScope** | Array | Consent scope | Training/generation/distribution, etc. |
| 3012 | **ConsentExpiry** | ISO 8601 | Consent expiration (optional) | UTC |
| 3020 | **PermittedUse** | Object | Permitted usage scope | See PermittedUse Object |

#### 6.3.2 RightsBasis Enum

| Value | Description | Evidence Requirements |
|-------|-------------|----------------------|
| **OWNED** | Self-produced/copyright held | Production records, copyright registration |
| **LICENSED** | Licensed from third party | Contract, permission document |
| **PUBLIC_DOMAIN** | Public domain | Explicit statement of basis |
| **CREATIVE_COMMONS** | CC license | Explicit statement of license type |
| **FAIR_USE** | Fair use claim | Documentation of basis |
| **UNKNOWN** | Rights relationship unknown | Record of risk acceptance |

#### 6.3.3 ConsentBasis Enum

| Value | Description | Legal Basis Examples |
|-------|-------------|---------------------|
| **EXPLICIT_WRITTEN** | Explicit written consent | Contract, consent form |
| **EXPLICIT_DIGITAL** | Explicit digital consent | Electronic signature, click consent |
| **IMPLIED** | Implied consent | Business practice, within contract scope |
| **STATUTORY** | Statutory permission | Copyright law exception provisions |
| **NOT_REQUIRED** | Consent not required | Public domain |
| **NONE** | No consent | Record of risk acceptance |
| **REVOKED** | Consent revoked | Record of revocation date/time |

#### 6.3.4 PermittedUse Object

```json
{
  "PermittedUse": {
    "Training": true,           // Training use permitted
    "Generation": true,         // Generation use permitted
    "Distribution": false,      // Distribution permitted
    "Commercial": true,         // Commercial use permitted
    "Derivative": true,         // Derivative work creation permitted
    "Attribution": true,        // Credit display required
    "Restrictions": [           // Other restrictions
      "NO_ADULT_CONTENT",
      "TERRITORY_JP_ONLY"
    ]
  }
}
```

### 6.4 CAP-CONFIDENTIALITY: Confidentiality Classification

#### 6.4.1 Confidentiality Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 4001 | **ConfidentialityLevel** | Enum | Confidentiality classification | See ConfidentialityLevel Enum |
| 4002 | **ClassificationDate** | ISO 8601 | Classification date | UTC |
| 4003 | **Classifier** | String | Classifier | User ID |
| 4010 | **ReleaseDate** | ISO 8601 | Scheduled release date (optional) | For pre-release materials |
| 4011 | **HandlingInstructions** | String | Handling instructions (optional) | Free text |

#### 6.4.2 ConfidentialityLevel Enum

| Value | Description | AI Workflow Restrictions |
|-------|-------------|-------------------------|
| **PUBLIC** | Public information | No restrictions |
| **INTERNAL** | Internal only | Internal environment only |
| **CONFIDENTIAL** | Confidential | Designated persons only, no external transmission |
| **SECRET** | Top secret | Strict access control |
| **PRE_RELEASE** | Pre-release | Strict management until release date |

### 6.5 CAP-CONTEXT: Model and User Context

#### 6.5.1 Model Context Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 5001 | **ModelID** | String | Model identifier | Vendor-provided or internal ID |
| 5002 | **ModelVersion** | String | Model version | Semantic versioning recommended |
| 5003 | **ModelType** | Enum | Model type | LLM/IMAGE_GEN/AUDIO_GEN/VIDEO_GEN/OTHER |
| 5004 | **ModelProvider** | String | Model provider | Vendor name or Internal |
| 5010 | **Environment** | Enum | Execution environment | LOCAL/CLOUD/HYBRID |
| 5011 | **EnvironmentID** | String | Environment identifier (optional) | Tenant ID, instance ID, etc. |

#### 6.5.2 User Context Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 6001 | **UserID** | String | User identifier | Unique within organization, anonymization possible |
| 6002 | **Role** | Enum | Role | See Role Enum |
| 6003 | **Department** | String | Department (optional) | Depends on organizational structure |
| 6010 | **SessionID** | String | Session identifier (optional) | For tracking series of operations |

#### 6.5.3 Role Enum

| Value | Description |
|-------|-------------|
| **CREATOR** | Content creator (artist, designer, etc.) |
| **ENGINEER** | Engineer (ML engineer, developer, etc.) |
| **MANAGER** | Manager (producer, director, etc.) |
| **REVIEWER** | Reviewer (legal, compliance, etc.) |
| **SYSTEM** | Automated system processing |
| **EXTERNAL** | External party (outsourcer, partner, etc.) |

### 6.6 Integrity Layer

#### 6.6.1 Hash Chain Structure

Each event contains the hash of the previous event, forming a tamper-proof chain:

```
Event N-1                    Event N                      Event N+1
┌──────────────┐            ┌──────────────┐            ┌──────────────┐
│ EventID      │            │ EventID      │            │ EventID      │
│ Payload      │            │ Payload      │            │ Payload      │
│ PrevHash: ───┼────────────│►PrevHash: ───┼────────────│►PrevHash     │
│ Hash: H(N-1) │            │ Hash: H(N)   │            │ Hash: H(N+1) │
└──────────────┘            └──────────────┘            └──────────────┘
```

#### 6.6.2 Signature Structure

```json
{
  "Signature": {
    "Algorithm": "ED25519",
    "PublicKey": "MCowBQYDK2VwAyEA...",
    "Value": "MEUCIQD...",
    "SignedAt": "2025-12-27T10:30:00.000Z"
  }
}
```

---

## 7. Compliance Philosophy

### 7.1 Comply-or-Explain Principle

CAP adopts **Comply-or-Explain** as its fundamental principle.

This means:
- It does NOT **mandate** CAP compliance
- It requires the ability to **explain reasons** when not complying
- It provides a framework for fulfilling **accountability** to regulatory authorities, auditors, and rights holders

### 7.2 Evidence-Based Accountability

CAP achieves the following "evidence-based accountability":

| Situation | Without CAP | With CAP |
|-----------|-------------|----------|
| Rights infringement allegation | Can only claim "we didn't use it" | Prove use/non-use with INGEST logs |
| Confidential leak investigation | Difficult to identify leak route | Track EXPORT destination and timing |
| Consent verification | Ambiguous verbal confirmation | Cryptographic record of ConsentBasis |
| Audit response | Post-hoc record creation | Real-time Evidence Pack |

### 7.3 Negative Proof Capability

One of CAP's important capabilities is providing **Negative Proof**.

> **CAP enables not only proof of use, but also negative proof — the ability to demonstrate that specific assets were NOT ingested, trained on, or referenced.**

With traditional audit methods, proving "something was used" is possible, but proving "something was NOT used" is extremely difficult. CAP's Hash Chain structure allows comprehensive presentation of all INGEST events recorded within a specific period, enabling cryptographic proof that "the asset in question was not ingested into the workflow."

This enables:
- Refutation based on log completeness against "unauthorized use" allegations from rights holders
- Proof of independent creative process against "copying" claims from competitors
- Proof of "non-use of confidential assets" in internal investigations

### 7.4 Disclosure Template

CAP-compliant organizations can use the following disclosure template:

```
【CAP Compliance Statement】

Organization: [Organization Name]
CAP Version: 0.1
Compliance Level: [FULL / PARTIAL / ASPIRING]
Scope: [Target Systems/Projects]

Covered Events:
☑ INGEST  ☑ TRAIN  ☑ GEN  ☐ EXPORT

Deviations from Specification:
- [Deviation Item 1]: [Reason]
- [Deviation Item 2]: [Reason]

Evidence Retention Period: [Retention Period]
Audit Contact: [Audit Contact]
Last Updated: [Update Date]
```

---

## 8. Non-Goals

### 8.1 Explicit Exclusions

CAP **explicitly excludes** the following:

| Non-Goal | Description | Reason |
|----------|-------------|--------|
| **Prior Prohibition of AI Use** | Does not prohibit or censor specific AI uses | Focus on evidence recording; judgment made by humans |
| **Automatic Copyright Infringement Determination** | Does not automatically determine infringement | Legal judgment is domain of experts and courts |
| **Equating Similarity with Illegality** | Does not convert similarity of generated outputs to illegality | Similar outputs may be legal |
| **Forced Disclosure of Model Internals** | Does not require disclosure of model weights, etc. | Trade secret protection, implementation neutrality |
| **Real-time Control** | Does not intervene in or control AI decisions | Specialized for post-hoc verification |
| **Quality Evaluation** | Does not evaluate quality or value of generated outputs | Subjective judgment is out of scope |

### 8.2 Boundary Clarification

```
┌─────────────────────────────────────────────────────────────────┐
│                     CAP's Scope of Responsibility               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  What CAP Does                  │  What CAP Does NOT Do         │
│  ─────────────────────          │  ─────────────────────        │
│  ✓ Record events                │  ✗ Approve/reject events      │
│  ✓ Cryptographic protection     │  ✗ Censor content             │
│    of evidence                  │                               │
│  ✓ Track provenance             │  ✗ Determine infringement     │
│  ✓ Provide auditability         │  ✗ Enforce penalties          │
│  ✓ Ensure interoperability      │  ✗ Mandate specific           │
│                                 │    technologies               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 8.3 Note on Similarity Metrics (Non-Normative)

**CAP does not define similarity thresholds for legality or compliance.**

The "similarity score" between generated outputs and existing works may be referenced as a starting point for investigation, but CAP does not define this as a normative requirement.

> Similarity metrics MAY be used as investigative signals, but MUST NOT be treated as determinative evidence without provenance records.

High or low similarity alone cannot determine:
- Whether copyright infringement exists (legal judgment depends on multiple factors)
- Inclusion in training data (independent creation possible even if similar)
- Intentional mimicry (possibility of coincidental similarity)

CAP is intended to be **used in conjunction** with similarity detection tools, but the final basis for judgment should always be **provenance records** (evidence of INGEST/TRAIN/GEN/EXPORT).

---

## 9. Regulatory Alignment

### 9.1 Applicable Regulations

CAP provides connection points to the following regulations and guidelines:

| Regulation/Guideline | Jurisdiction | CAP-Related Requirements |
|---------------------|--------------|-------------------------|
| **EU AI Act** | EU | Art.12 Logging, Art.53 Transparency |
| **Digital Services Act (DSA)** | EU | Disclosure of generative AI content |
| **GDPR** | EU | Processing records, consent management |
| **Copyright Directive** | EU | TDM exceptions, opt-out |
| **Copyright Law** | Japan | Article 30-4, AI learning exceptions |
| **AI Business Guidelines** | Japan | Transparency, accountability |

### 9.2 EU AI Act Alignment

Correspondence with EU AI Act Article 12 (Logging):

| EU AI Act Requirement | CAP Field | Compliance Status |
|----------------------|-----------|-------------------|
| Automatic event recording | EventID, Timestamp | ✓ Supported |
| Input data tracking | AssetID, AssetHash | ✓ Supported |
| Output identification | OutputAssetID | ✓ Supported |
| Recording of human oversight | UserID, Role | ✓ Supported |

### 9.3 Japan Copyright Law Alignment

Relationship with Copyright Law Article 30-4 (Reproduction for Information Analysis):

| Issue | CAP Response |
|-------|--------------|
| Evidence of learning use | Recorded in TRAIN events |
| Presence/absence of enjoyment purpose | Explicit in PermittedUse.Generation |
| Concentrated learning on specific styles | Verifiable through InputAssetIDs analysis |

---

## 10. Implementation Guidelines

### 10.1 Implementation Levels

| Level | Name | Requirements | Target Users |
|-------|------|--------------|--------------|
| **L1** | Basic | INGEST/GEN recording | Small studios, individuals |
| **L2** | Standard | All 4 events, Hash Chain | Mid-size production companies |
| **L3** | Enterprise | L2 + Merkle Anchor, external verification | Major publishers |

### 10.2 Minimum Viable Implementation

Requirements for minimum implementation (L1):

1. **INGEST Recording**: AssetID, RightsBasis, User of ingested materials
2. **GEN Recording**: AssetID, ModelContext, User of generated outputs
3. **Local Storage**: Event log storage in JSON format
4. **Basic Integrity**: Event hashing with SHA-256

### 10.3 Evidence Pack Structure

```
evidence-pack-{ChainID}/
├── manifest.json           # Pack overview, verification info
├── events/
│   ├── 001-ingest.json     # INGEST event
│   ├── 002-train.json      # TRAIN event
│   ├── 003-gen.json        # GEN event
│   └── 004-export.json     # EXPORT event
├── signatures/
│   └── chain-signature.sig # Chain-wide signature
└── anchors/
    └── merkle-root.json    # Merkle Root (L3 only)
```

---

## 11. Appendix A: JSON Examples (Non-Normative)

**Note**: The following examples are for explanatory purposes and are not normative. Implementers should adopt appropriate formats based on the requirements in this specification.

### A.1 INGEST Event Example

```json
{
  "EventID": "01934f2a-8b3c-7f93-9f3a-1234567890ab",
  "ChainID": "01934e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": null,
  "Timestamp": "2025-12-27T10:00:00.000Z",
  "EventType": "INGEST",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  
  "Asset": {
    "AssetID": "urn:cap:asset:studio-a:char-design-001",
    "AssetType": "IMAGE",
    "AssetHash": "a7ffc6f8bf1ed76651c14756a061d662f580ff4de43b49fa82d80a4b80f8434a",
    "AssetName": "Hero Character Design Draft A"
  },
  
  "Rights": {
    "RightsBasis": "OWNED",
    "RightsHolder": "studio-a",
    "ConsentBasis": "NOT_REQUIRED",
    "PermittedUse": {
      "Training": true,
      "Generation": true,
      "Distribution": false,
      "Commercial": true
    }
  },
  
  "Confidentiality": {
    "ConfidentialityLevel": "PRE_RELEASE",
    "ReleaseDate": "2026-04-01T00:00:00.000Z"
  },
  
  "Context": {
    "UserID": "user-12345",
    "Role": "CREATOR",
    "Department": "Character Design"
  }
}
```

### A.2 TRAIN Event Example

```json
{
  "EventID": "01934f3b-9c4d-8f04-af4b-2345678901bc",
  "ChainID": "01934e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": "b8ffc7f9cf2fe87762d25867b172e773f691ff5ef54c5afb93e91b5c91f9545b",
  "Timestamp": "2025-12-27T11:00:00.000Z",
  "EventType": "TRAIN",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  
  "Training": {
    "TrainingType": "LORA",
    "InputAssetIDs": [
      "urn:cap:asset:studio-a:char-design-001",
      "urn:cap:asset:studio-a:char-design-002",
      "urn:cap:asset:studio-a:char-design-003"
    ],
    "OutputModelID": "urn:cap:model:studio-a:char-lora-v1"
  },
  
  "ModelContext": {
    "ModelID": "stable-diffusion-xl-base-1.0",
    "ModelVersion": "1.0",
    "ModelType": "IMAGE_GEN",
    "ModelProvider": "Stability AI",
    "Environment": "LOCAL"
  },
  
  "Context": {
    "UserID": "user-67890",
    "Role": "ENGINEER",
    "Department": "AI Research"
  }
}
```

### A.3 GEN Event Example

```json
{
  "EventID": "01934f4c-ad5e-9f15-bf5c-3456789012cd",
  "ChainID": "01934e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": "c9ffd8fadf3ff98873e36978c283f884fa02ff6fg65d6bfc04fa2c6da2fa656c",
  "Timestamp": "2025-12-27T12:00:00.000Z",
  "EventType": "GEN",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  
  "Generation": {
    "PromptHash": "d0ffe9fbef4ffa9984f47a89d394f995fb13ff7fh76e7cfd15fb3d7eb3fb767d",
    "OutputAssetID": "urn:cap:asset:studio-a:gen-char-001",
    "OutputAssetHash": "e1fff0fcff5ffba095f58b9ae4a5fa06fc24ff8fi87f8dfe26fc4e8fc4fc878e"
  },
  
  "ModelContext": {
    "ModelID": "urn:cap:model:studio-a:char-lora-v1",
    "ModelVersion": "1.0",
    "ModelType": "IMAGE_GEN",
    "ModelProvider": "Internal",
    "Environment": "LOCAL"
  },
  
  "Context": {
    "UserID": "user-12345",
    "Role": "CREATOR",
    "SessionID": "session-abc123"
  }
}
```

### A.4 EXPORT Event Example

```json
{
  "EventID": "01934f5d-be6f-af26-cf6d-4567890123de",
  "ChainID": "01934e3a-6a1b-7c82-9d1b-0987654321dc",
  "PrevHash": "f2fff1fdff6ffcb1a6f69c0bf5b6fb17fd35ff9fj98f9eff37fd5f9fd5fd989f",
  "Timestamp": "2025-12-27T14:00:00.000Z",
  "EventType": "EXPORT",
  "HashAlgo": "SHA256",
  "SignAlgo": "ED25519",
  
  "Export": {
    "AssetID": "urn:cap:asset:studio-a:gen-char-001",
    "Destination": "client-publisher-x",
    "DestinationType": "DELIVERY",
    "Format": "PNG",
    "Resolution": "4096x4096"
  },
  
  "Rights": {
    "PermittedUse": {
      "Training": false,
      "Generation": false,
      "Distribution": true,
      "Commercial": true,
      "Attribution": true,
      "Restrictions": ["TERRITORY_JP_ONLY"]
    }
  },
  
  "Context": {
    "UserID": "user-11111",
    "Role": "MANAGER",
    "Department": "Business Development"
  }
}
```

---

## 12. References

### 12.1 Normative References

- [RFC 2119] Key words for use in RFCs to Indicate Requirement Levels
- [RFC 4122] A Universally Unique IDentifier (UUID) URN Namespace
- [RFC 9562] Universally Unique IDentifiers (UUIDs) - UUID Version 7
- [RFC 8785] JSON Canonicalization Scheme (JCS)
- [ISO 8601] Date and time format

### 12.2 Informative References

- [VAP] Verifiable AI Provenance Framework Specification v1.1
- [VCP] VeritasChain Protocol Specification v1.0
- [EU AI Act] Regulation (EU) 2024/1689
- [C2PA] Coalition for Content Provenance and Authenticity Technical Specification

### 12.3 Related Documents

- VSO-VAP-SPEC-001: VAP Framework Specification
- VSO-VCP-SPEC-001: VCP Protocol Specification
- VSO-CAP-IMPL-001: CAP Implementation Guide (TBD)
- VSO-CAP-TEST-001: CAP Conformance Test Suite (TBD)

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1.0 | 2025-12-27 | VSO | Initial draft |

---

**© 2025 VeritasChain Standards Organization. All rights reserved.**

This specification is published under CC BY 4.0 International License.
