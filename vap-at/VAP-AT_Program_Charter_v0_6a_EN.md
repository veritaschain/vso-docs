# VAP-AT Program Charter

**Document ID:** VSO-VAP-AT-001  
**Version:** 0.6a (Draft, revised)  
**Status:** Draft for Internal Review  
**Date:** 2025-12-28  
**Maintainer:** VeritasChain Standards Organization (VSO)  
**License:** CC BY 4.0

---

## Executive Summary

**VAP-AT (Verifiable AI Provenance – Assessment Test)** is a measurement-based scoring framework that evaluates AI systems for **Auditability, Verifiability, and Regulatory Readiness**.

Unlike individual skill certification programs (e.g., CISSP), VAP-AT evaluates **AI systems themselves** rather than individuals. The framework employs a **score-based design** that produces assessment scores and improvement evidence, rather than binary Pass/Fail determinations, enabling continuous trust-building.

> **Core Design Principle (Score-Based Assessment):**
> 
> VAP-AT is fundamentally a **score-based** assessment framework. Threshold Designations are **optional interpretive labels** provided to accommodate practical needs such as procurement requirements and regulatory reporting. They are distinct from Pass/Fail certifications. Scores promote continuous improvement and provide granular information to markets and regulators.

**Market Opportunity:**
- **Strong regulatory tailwinds**: EU AI Act, MiFID II, SEC 17a-4 enforcement
- **Established willingness-to-pay benchmarks**: SOC 2 / ISO 27001 / FedRAMP price ranges demonstrate market acceptance
- RegTech market: **$83B (2023) → $200B (2028), 124% growth**
- EU AI Act violation penalties: Up to **€35M or 7% of global revenue**

> **Note**: Detailed market size data (AI Governance $15.8B/2030, Generative AI Audit $2.7B/2033, etc.) are provided in Section 1.3. Figures originate from different research firms with varying methodologies.

**Core Philosophy:**
> "Verify, Don't Trust" — Evaluating that audit trails for AI systems exist in a mathematically verifiable form.

---

## 1. Program Objectives

### 1.1 What VAP-AT Measures

VAP-AT measures three core properties:

| Property | Definition | Regulatory Alignment |
|----------|------------|---------------------|
| **Auditability** | Whether audit trails are tamper-resistant and independently verifiable by third parties | EU AI Act Art.12/19, MiFID II RTS 25 |
| **Verifiability** | Whether records are complete with proper observability, schema, and event granularity | SEC 17a-4, GDPR Art.17 |
| **Regulatory Readiness** | Whether evidence is packaged and ready for audit submission | EU AI Act Annex IV |

### 1.2 What VAP-AT Does NOT Do

| ❌ Out of Scope | Rationale |
|----------------|-----------|
| AI model accuracy evaluation | Out of scope (ML performance is a separate domain) |
| Business logic validity | Out of scope (business decisions not evaluated) |
| Security vulnerability assessment | Out of scope (penetration testing is separate) |
| "Safety guarantee" | Assessment confirms conformance to criteria, not infallibility |

> **Critical Distinction:**
> 
> VAP-AT does not assess the correctness or legality of AI decisions, only the verifiability and auditability of the decision process.

### 1.3 Market Demand Signals

**Regulatory Drivers:**

| Regulation | Requirements | Violation Penalties |
|------------|--------------|---------------------|
| **EU AI Act** | Automatic event logging for high-risk AI (Art.12), log retention (Art.19), 6+ months retention | €35M or 7% revenue |
| **MiFID II RTS 25** | Annual algo trading self-assessment, 100μs time synchronization | FCA fines, business suspension |
| **NYC Local Law 144** | Mandatory bias audits for hiring AI | $500-$1,500/violation |
| **GDPR Art.17** | Right to erasure (Crypto-Shredding support) | €20M or 4% revenue |

> **Note (VAP-AT Value Proposition):** EU AI Act Art.12/19 mandates automatic logging and retention but does not explicitly require tamper-proof/tamper-evidence. VAP-AT provides **evidentiary robustness** through cryptographic tamper-evidence, delivering defensibility beyond baseline compliance.

**Willingness to Pay Evidence:**

| Market Segment | Price Acceptance Range | Rationale |
|----------------|----------------------|-----------|
| B2B SaaS (SOC 2 equivalent) | $30,000-$100,000/year | De facto B2B contract requirement |
| Financial Institutions (MiFID II) | $50,000-$150,000/year | Regulatory violation risk mitigation |
| Government Procurement (FedRAMP equivalent) | $250,000-$3,000,000 | Federal contract requirement |
| RegTech spending growth | $83B→$200B (2023-2028) | 124% growth, regulatory complexity |
| AI Governance market | $15.8B (2030) | 30% CAGR |

**Price Sensitivity Analysis:**
- **Small enterprises**: $5,000-$15,000 acceptable range
- **Mid-size enterprises**: Up to $50,000 "expensive but acceptable"
- **Large enterprises**: $100,000+ feasible
- **Resistance threshold**: ROI justification required above $50,000

---

## 2. Comparative Program Analysis

### 2.1 Existing Program Comparison

| Program | Operator Type | Scope | Revenue Model | Neutrality Mechanism | Credibility | Known Criticism |
|---------|---------------|-------|---------------|---------------------|-------------|-----------------|
| **CISSP (ISC²)** | Non-profit membership | Individual knowledge (InfoSec) | Exam $749, AMF $125, training | Independent exam development, ANSI/ISO 17024 | DoD IA required, broad recognition | Theory-heavy, brain dump issues, high cost |
| **CCSP (ISC²)** | Non-profit membership | Individual knowledge (Cloud Security) | Exam $599, renewal fees | Accreditation, zero-tolerance fraud policy | Cloud compliance recognition | Exam rigor, cost |
| **CISA (ISACA)** | Non-profit professional | Individual knowledge (IT Audit) | Exam $575-$760, membership, training | ISACA committee exam development | High IT audit reputation | Preparation cost burden |
| **CISM (ISACA)** | Non-profit professional | Individual knowledge (Security Mgmt) | Exam $575-$760, renewal | Score verification, ethics code | 48,000+ holders, $149K salary premium | None significant |
| **ISO/IEC 27001** | Standard: ISO (NGO), Cert: Independent CB | Organizational ISMS | Audit $5K-$35K, surveillance $3K-$10K/yr | ISO→AB→CB three-layer separation, ISO 17021 | High international trust, EU/APAC accepted | Checkbox criticism, implementation cost |
| **SOC 2 (AICPA)** | Standard: AICPA, Audit: CPA firms | Organizational systems (Trust Principles) | Audit $7K-$100K, tools $10K-$80K/yr | CPA license, peer review, independence rules | Near-mandatory for B2B SaaS (US) | Auditor interpretation inconsistency |
| **FedRAMP** | Government program (GSA/PMO) | Cloud service security | Total cost $250K-$3M | 3PAO accreditation (ISO 17020), JAB multi-layer review | Gold standard for federal cloud | High cost, long delays |

### 2.2 Key Lessons

**Individual Certifications (CISSP, CISA, etc.):**
- Operated by non-profits or professional associations; revenue from exams and training
- Neutrality established through independent exam development and specialization
- **Challenges:** Value erosion from brain dumps, theory-heavy content

**System Audits (ISO 27001, SOC 2):**
- Separation of standard-setting and assessment execution is key to trust
- Third-party auditors maintain objectivity
- **Challenges:** Conflict of interest where auditors are paid by auditees; "Audit Shopping" for lenient auditors

**High-Assurance Programs (FedRAMP):**
- Government oversight + accredited assessors provide high trust
- **Challenges:** High cost and long timelines exclude SMEs

**AI Auditing (Emerging):**
- Moving toward institutionalization with EU AI Act
- Currently fragmented with no unified standards
- **Opportunity:** First-mover establishing a robust framework can become market leader

---

## 3. Governance Structure (4-Layer Separation)

### 3.1 Structural Independence Principles

**Common Factor in Successful Certification Programs: Separation of Standard-Setting and Assessment Execution**

> "Clear separation between standard-setting and certification processes is critical for maintaining independence and objectivity" — GOTS (Global Organic Textile Standard)

Research-based failure analysis:

| Failure Case | Cause | Lesson |
|--------------|-------|--------|
| **Credit Rating Agencies (2008 Financial Crisis)** | Issuer-pays model conflict of interest | Separate payer from subject of assessment |
| **TRUSTe (FTC Sanction)** | Self-monitoring model, no external oversight | Independent external oversight required |
| **Boeing 737 MAX (FAA Certification Issues)** | Excessive delegation of certification authority | Maintain appropriate oversight |
| **FSC/RSPO (Environmental Certification)** | Certifier financial dependence on certified entities | Revenue diversification requirements |
| **ISO Certificate Mills** | Quality degradation from price competition | Minimum quality standards and audits |
| **Safe Harbor / Privacy Shield** | Misalignment with regulatory requirements | Continuous alignment with regulators |
| **VW Emissions Scandal** | Test regime vulnerability to deception | Real-world verification importance |
| **CEH (EC-Council)** | Exam predictability, "Pay-to-Pass" perception | Exam integrity maintenance |
| **CMMC 1.0** | Excessive complexity excluding SMEs | Graduated, proportional design |
| **Texas Teacher Certifications** | Proxy cheating resulting in 200+ unqualified teachers | Strict exam proctoring, identity verification |
| **U.S. Job Corps** | $1.7B program with poor outcomes | Outcome measurement, avoid government over-dependence |

### 3.2 Five Organizational Models Comparison

| Model | Standard-Setting | Assessor Qualification | Assessment Execution | Oversight | Example | Conflict Mitigation |
|-------|-----------------|----------------------|---------------------|-----------|---------|---------------------|
| **Non-profit Standard + Independent CAB** | NGO (ISO, etc.) | AB accredits CB | Independent accredited CB | National AB | ISO 27001, PCAF | Independent auditors |
| **Non-profit + Commercial Subsidiary** | Non-profit parent | Subsidiary provides training | Parent provides accreditation | Internal firewall | ISC² | Revenue stream separation |
| **Consortium + Licensed Assessors** | Industry body | Body certifies | Certified QSAs | Body QA checks | PCI DSS | Disclosure policies |
| **Government-led + Accredited Private Auditors** | Government agency | Accreditation (ISO 17020) | Accredited 3PAOs | Government PMO review | FedRAMP | Multi-layer review |
| **Licensed Assessment Methodology** | Central organization | Individual certification | Licensed assessors | Central QA | CMMI | Disclosure requirements |

**VAP-AT Selection:** Base model of "Non-profit Standard + Independent CAB" combined with quality management elements from "Consortium + Licensed Assessors" and revenue separation from "Non-profit + Commercial Subsidiary."

### 3.3 VAP-AT 4-Layer Structure (Dual Accreditation Model)

```
┌─────────────────────────────────────────────────────────────────┐
│  Layer 0: National Accreditation Bodies                         │
│  ─────────────────────────────────────────────────              │
│  • Accredit CABs per ISO/IEC 17020/17021/17065 (ISO Accreditation)│
│  • Enable global acceptance via IAF MLA mutual recognition      │
│  • Examples: UKAS (UK), DAkkS (DE), ANAB (US), JAB (JP)        │
│  • Required from Phase 2 onwards                                │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ ISO Accreditation (Phase 2+)
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 1: Standard-Setting / Scheme Owner (VSO)                 │
│  ─────────────────────────────────────────                      │
│  • Maintains VAP-AT criteria (scoring, evidence, terminology)   │
│  • Does NOT perform assessments (conflict of interest avoidance)│
│  • Provides "Scheme Accreditation" to CABs (VSO Accredited CAB) │
│  • Revenue: CAB accreditation fees, membership, document sales  │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ Scheme Accreditation (Phase 1+)
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 2: Advisory Board                                        │
│  ─────────────────────────────────────────                      │
│  • Technical advisory, regulatory monitoring, conflict checks   │
│  • Regulator observer seats                                     │
│  • Accreditation criteria revision proposals                    │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ Oversight
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 3: Assessment Execution (Conformity Assessment Body/CAB) │
│  ─────────────────────────────────────────────────              │
│  • Multiple independent CABs conduct VAP-AT and issue reports   │
│  • Independence rules: no consulting to auditees, etc.          │
│  • Assessment fees are CAB revenue (VSO does not collect)       │
│  • Competitive market optimizes price and quality               │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ Assessment
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 4: Commercial Enablers                                   │
│  ─────────────────────────────                                  │
│  • Tools, training, preparation support                         │
│  • Separated from Assessment                                    │
│  • Prevents "standard body selling passes" scenario             │
│  • Provided by VSO commercial subsidiary or certified partners  │
└─────────────────────────────────────────────────────────────────┘
```

**Dual Accreditation Model Clarification:**

| Accreditation Type | Accrediting Body | Subject | Purpose | Phase |
|-------------------|------------------|---------|---------|-------|
| **Scheme Accreditation** | VSO | CAB | VAP-AT scheme-specific assessment capability and QMS | Phase 1+ |
| **ISO Accreditation** | National AB | CAB | ISO/IEC 17065, etc. international standard conformance | Phase 2+ |

**Phase-based Rollout:**
- **Phase 1 (Launch):** VSO Scheme Accreditation only (rapid market entry)
- **Phase 2 (Maturity):** Priority accreditation for ISO-accredited CABs (institutional trust)
- **Phase 3 (Scale):** ISO Accreditation mandatory + Mutual Recognition Agreement (MRA)

### 3.4 VSO Role (Scheme Owner)

| Responsibility | Content |
|----------------|---------|
| Standard-setting | VAP-AT Scoring Criteria, Evidence Requirements |
| CAB Accreditation | Accreditation review, maintenance, audit (annual surveillance) |
| Rulebook | VAP-AT Scheme Rulebook management |
| Dispute Resolution | Final decision on assessment-related appeals |
| Impartiality Committee | External stakeholder committee (ISO 17021 compliant) |
| Quality Assurance | Spot-check review of CAB assessment reports (PCI QSA model) |

| What VSO Does NOT Do | Rationale |
|----------------------|-----------|
| Conduct assessments | CAB responsibility; conflict avoidance |
| Collect assessment fees | CAB revenue |
| Provide consulting | Commercial activities via separate entity (BSI model) |

### 3.5 CAB Requirements (ISO/IEC 17065 Aligned)

| Category | Requirement | Basis |
|----------|-------------|-------|
| **Independence** | No capital relationship with assessed entities | ISO 17021 |
| **Consulting Prohibition** | Same organization cannot provide assessment and consulting (2-year rule) | EU AI Act Notified Body requirements |
| **Expertise** | Employ cryptography and audit specialists | Technical competence |
| **Insurance** | Professional liability insurance ($1-5M+) | SOC 2 model compliance |
| **Oversight** | Accept VSO annual audits | Quality maintenance |
| **Revenue Diversification** | Max 10% revenue from single client | Financial independence |
| **Report Review** | Accept spot-check VSO review of assessment reports | Quality consistency |

**CAB Rotation Rules (Rotation Policy):**

| Rule | Limitation | Rationale |
|------|-----------|-----------|
| **Same CAB consecutive assessments** | Maximum 3 years | Wirecard/Enron-type relationship corruption risk mitigation |
| **Lead Assessor** | 2-year rotation | Individual-level familiarity prevention |
| **CAB return after change** | Minimum 2-year cooling-off | Formal rotation gaming prevention |

> **Operating Principle:** When an assessed entity reaches 3 consecutive years with the same CAB, they must select a different VSO-accredited CAB for the next assessment. Lead Assessors may serve a maximum of 2 years for the same assessed entity.

### 3.6 Reference Model Comparison

| Model | Standard-Setting | Assessor Qualification | Assessment Execution | Enforcement |
|-------|-----------------|----------------------|---------------------|-------------|
| **PCI-DSS** | PCI SSC | QSA certification | Independent QSA | Payment brands |
| **ISO 27001** | ISO TC27 | CB accreditation | Accredited CB | Market |
| **FedRAMP** | NIST/PMO | 3PAO accreditation | Independent 3PAO | Federal agencies |
| **SOC 2** | AICPA | CPA license | CPA firms | Market |
| **VAP-AT** | VSO | CAB accreditation | Accredited CAB | Regulators/Market |

---

## 4. Assessment Modalities (3-Level Structure)

Referencing CSA STAR, Singapore CLS, and US CMMC, VAP-AT adopts a three-tier structure: **Self → Third-party → Continuous**.

### 4.1 Level 1: VAP-AT Self (Self-Assessment)

**Target: Low-risk AI (recommendation engines, internal efficiency tools)**

| Item | Content |
|------|---------|
| **Purpose** | Organizations identify gaps and prepare |
| **Executor** | Assessed organization (using VAP Scorecard Explorer) |
| **Deliverable** | Evidence Pack (Preliminary) |
| **Price Range** | Free – $5,000 (tools/templates for adoption promotion) |
| **Validity Period** | None (self-declaration) |
| **Status** | `assessment_status: "Self-Assessment"` |
| **Verification** | Automated scan tools + self-attestation |

### 4.2 Level 2: VAP-AT Verified (Third-Party Assessment)

**Target: Medium-risk, general business AI (HR Tech, financial underwriting support)**

| Item | Content |
|------|---------|
| **Purpose** | Produce deliverables for procurement, customer audits, regulatory response |
| **Executor** | VSO-accredited CAB |
| **Deliverable** | CAB-signed Score Report + Evidence Pack (Verified) |
| **Price Range** | $15,000 – $150,000 (varies by organization size and complexity) |
| **Validity Period** | 1 year (renewal assessment required) |
| **Status** | `assessment_status: "Verified by [CAB Name]"` |
| **Verification** | Accredited CAB |

**Type I / Type II Classification (SOC 2 Model):**

| Type | Content | Use Case |
|------|---------|----------|
| **Type I (Point-in-time)** | Evaluates design appropriateness at a specific date | Initial deployment, model development stage |
| **Type II (Period audit)** | Verifies 6-12 months of operational performance | Ongoing operations, regulatory compliance |

### 4.3 Level 3: VAP-AT Continuous (Continuous Monitoring)

**Target: High-risk AI (medical diagnosis, autonomous driving, critical infrastructure control)**

| Item | Content |
|------|---------|
| **Purpose** | Solve "stale assessment" problem for AI that updates, learns, or changes configuration |
| **Executor** | VSO-accredited CAB + automated tools + spot-check verification |
| **Deliverable** | Monthly/quarterly Delta Reports, Performance Dashboard |
| **Price Range** | Annual subscription (20-50% of initial assessment) |
| **Validity Period** | Duration of subscription (auto-renewal) |
| **Status** | `assessment_status: "Continuous Monitoring Active"` |
| **Feature** | Operational status automatically moves to "Suspended" if performance falls below thresholds |

**Assessment Status Definitions (Operational Status):**

| Status | Definition | Trigger | Recovery Condition |
|--------|------------|---------|-------------------|
| **Active** | Valid assessment state | Assessment complete and threshold reached, subscription active | — |
| **Suspended** | Temporarily halted (issue detected) | Below threshold, critical log gaps, fraud detection | Remediation complete + score recovery via re-assessment |
| **Pending Review** | Awaiting review | Spot-check flag, complaint filed | VSO/CAB review completion |
| **Expired** | Validity ended | Validity period ended, subscription cancelled | New assessment required |

> **Automatic Suspension Mechanism:** If thresholds are breached during Continuous monitoring, the assessed entity is notified within 24 hours. If not remediated within 30 days, status automatically transitions to `Suspended`. Public Registry status updates immediately.

### 4.4 Level Selection Guidelines

| Risk Level | Examples | Recommended Level | Cost Estimate |
|------------|----------|-------------------|---------------|
| **Low risk** | Internal chatbots, recommendation engines | Level 1 (Self) | $0-$5,000 |
| **Medium risk** | Hiring AI, credit scoring, customer service AI | Level 2 (Verified) | $15,000-$60,000 |
| **High risk** | Medical diagnosis, autonomous driving, critical infrastructure | Level 3 (Continuous) | $100,000+ |

---

## 5. Scoring Criteria

### 5.1 Scoring System

Aligned with VAP Scorecard: **10 criteria × 0–2 points = maximum 20 points**.

| Score | Meaning | Color |
|-------|---------|-------|
| **0** | Not implemented or fundamentally inadequate | 🔴 Red |
| **1** | Partially implemented with gaps | 🟡 Yellow |
| **2** | Fully implemented, required outcomes achieved | 🟢 Green |

### 5.2 Grade Thresholds

| Score Range | Grade | Interpretation |
|-------------|-------|----------------|
| 16–20 | **Strong** | Demonstrates robust auditability |
| 11–15 | **Moderate** | Auditable but room for improvement |
| 6–10 | **Limited** | Significant auditability deficiencies |
| 0–5 | **Inadequate** | Fundamentally insufficient auditability |

> **Note:** Grades are descriptive states, not endorsements. They should not be misinterpreted as regulatory approval.

### 5.3 Assessment Criteria (10 Criteria)

| # | Criterion | Key Question | Regulatory Mapping |
|---|-----------|--------------|-------------------|
| 1 | **Third-Party Verifiability** | Can external parties independently verify audit trails? | EU AI Act Art.12/19, MiFID II |
| 2 | **Tamper Evidence** | Can unauthorized modifications be detected? | SEC 17a-4 |
| 3 | **Sequence Fixation** | Is chronological order immutably recorded? | MiFID II RTS 25 |
| 4 | **Decision Provenance** | Can decision inputs and rationale be traced? | EU AI Act Art.12 |
| 5 | **Responsibility Boundaries** | Are approvers and overriders for each action clear? | EU AI Act Art.14 |
| 6 | **Documentation Completeness** | Is technical documentation complete and current? | EU AI Act Annex IV |
| 7 | **Retention & Availability** | Is evidence retained and retrievable for required periods? | EU AI Act Art.19, GDPR, MiFID II |
| 8 | **Time Synchronization** | Is system time synchronized with trusted sources? | MiFID II RTS 25 |
| 9 | **Failure & Recovery Logging** | Are system failures and recoveries logged? | DORA |
| 10 | **Right to Erasure Compatibility** | Can GDPR erasure rights be supported while maintaining auditability? | GDPR Art.17 |

### 5.4 Hybrid Model (Score + Optional Threshold Labels)

**Challenge:** Markets are accustomed to binary certification (Pass/Fail) vs. score-based systems provide more information

**Solution:** Score as primary deliverable, with threshold labels as an optional interpretive layer

| Deliverable | Content | Use Case |
|-------------|---------|----------|
| **Assessment Score** | 0–20 detailed evaluation result | Improvement planning, risk evaluation |
| **Threshold Designation** | Score-threshold-based label (optional interpretive layer) | Procurement requirements, regulatory reporting reference |

**Threshold Designation Examples:**
- "VAP-AT Auditability Threshold – EU AI Act Art.12/19 aligned" (Score 16+)
- "VAP-AT Auditability Threshold – MiFID II RTS 25 aligned" (Score 14+)
- "VAP-AT Baseline Auditability Threshold" (Score 11+)

> **Critical Disclaimer:**
> 
> Threshold Designation is an **interpretive label within the VAP-AT scheme** and is **not a guarantee of legal compliance**.
> - "EU AI Act Art.12/19 aligned" indicates "a VAP-AT score aligned with auditability levels sought by those articles"
> - Legal compliance determination is the assessed entity's responsibility and ultimately depends on regulatory interpretation
> - CABs do not provide legal advice; Score Reports must include this disclaimer

**UL IoT Security Rating Model Reference:**
UL's IoT Security Rating uses 5 tiers (Bronze→Silver→Gold→Platinum→Diamond) to indicate security control strength, providing consumers detailed information while incentivizing manufacturers toward higher levels.

### 5.5 Score-Based vs Binary Certification Strategic Analysis

| Aspect | Score-Based | Binary (Pass/Fail) | VAP-AT Hybrid |
|--------|-------------|-------------------|---------------|
| **Information richness** | High (granular) | Low (binary) | High + optional threshold labels |
| **Improvement incentive** | High (aim for higher scores) | Low (meet minimum threshold only) | High |
| **Regulatory acceptance** | Lower (interpretation required) | High (clear) | High (threshold labels provided) |
| **Market understanding** | Lower (education required) | High (simple) | Medium-High |
| **Risk assessment utility** | High (insurance pricing, etc.) | Low | High |
| **Financial sector fit** | Data trail builds trust | Regulations prefer binary | Compatible with both |

**Key Insight (External Research):**

> "Score-based assessments can build granular trust through data trails, but in sectors dominated by binary regulations such as finance, adoption may lag behind binary certifications."

**VAP-AT Strategic Response:**
- **For regulated sectors:** Provide Threshold Designations to accommodate procurement and reporting needs
- **For insurance/risk evaluation:** Provide detailed scores to support risk-based decision-making
- **For voluntary improvement:** Present graduated score improvement roadmaps

---

## 6. Price Benchmarks

### 6.1 Comparable Program Pricing

**Individual Certifications:**

| Certification | Exam Fee | Annual Maintenance | Training (Optional) | Notes |
|--------------|----------|-------------------|---------------------|-------|
| **CISSP (ISC²)** | $749 | $125 | $1,000-$3,000 | ANSI/ISO 17024 accredited |
| **CISA (ISACA)** | ~$575 (member) | ~$100 | $1,000+ | IT audit standard |
| **CCNA (Cisco)** | $300+ | N/A (3-year validity) | $500-$2,000 | Vendor certification |
| **GIAC (SANS)** | $1,000+ | $469/4 years | $5,000+ | Advanced security |

**Organizational Audits:**

| Program | Initial Audit | Annual Surveillance | Preparation Cost | Total First Year (SME) |
|---------|--------------|--------------------|-----------------|-----------------------|
| **ISO/IEC 27001** | $5,000-$35,000 | $3,000-$10,000/year | $5,000-$75,000 | ~$20,000-$50,000 |
| **SOC 2 Type I** | $10,000-$20,000 | — | $5,000-$15,000 | ~$15,000-$35,000 |
| **SOC 2 Type II** | $20,000-$50,000+ | (annual) | $5,000-$15,000 | ~$25,000-$65,000 |

**High-Assurance Programs:**

| Program | Total Cost | Duration | Breakdown |
|---------|-----------|----------|-----------|
| **FedRAMP Moderate** | $800,000-$2,000,000 | 18-24 months | 3PAO $150K-$400K, consulting $200K-$500K, tools/effort remainder |
| **HITRUST CSF** | $50,000-$200,000+ | 6-12 months | Assessment + certification fees |

### 6.2 VAP-AT Pricing Design

| Tier | Target | Initial Assessment | Annual Renewal | Notes |
|------|--------|-------------------|----------------|-------|
| **Bronze** | Startup / SME | $5,000 – $20,000 | $2,000 – $8,000 | Level 1-2 |
| **Silver** | Mid-size Enterprise | $15,000 – $50,000 | $5,000 – $15,000 | Level 2 |
| **Gold** | Large Enterprise / HFT | $50,000 – $150,000 | $15,000 – $40,000 | Level 2-3 |
| **Platinum** | Critical Infrastructure | $100,000 – $300,000 | $30,000 – $100,000 | Level 3 |

**Price Drivers:**
- System complexity (single system vs distributed)
- Data volume (events/day)
- Regulatory stringency (MiFID II, EU AI Act, etc.)
- Assessment scope (single environment vs multi-region)
- Assessment type (Type I vs Type II)

### 6.3 Revenue Distribution

| Recipient | Revenue Source | Notes |
|-----------|----------------|-------|
| **VSO** | CAB accreditation fees, membership, document sales, training licenses | ~$29,000/year per CAB (PCI SSC reference) |
| **CAB** | Assessment fees | Primary revenue source |
| **Tool Vendors** | Tool/template sales (Layer 4) | Optional partners |

> **Critical:** VSO does not directly collect assessment fees. This structurally prevents "Pay-to-Pass" suspicions.

---

## 7. Assessor Qualification Program (Certified AI Systems Assessor)

### 7.1 Overview

To ensure VAP-AT quality, an individual assessor qualification program is established (CISSP/ISACA model).

**Objectives:**
- Build qualified assessor pool
- Standardize assessment quality
- Maintain current technology competency through continuing education
- Offset standard development costs through membership fees

### 7.2 Qualification Tiers

| Qualification | Requirements | Authority |
|---------------|--------------|-----------|
| **VAP-AT Associate (VAP-ATA)** | Pass exam + 1 year experience | Level 1 assessment support |
| **VAP-AT Professional (VAP-ATP)** | Pass exam + 3 years experience + 3 assessments | Level 1-2 assessment execution |
| **VAP-AT Expert (VAP-ATE)** | Pass advanced exam + 5 years experience + 10 assessments | Level 3 assessment, CAB technical lead |

### 7.3 Fee Structure

| Item | Fee | Notes |
|------|-----|-------|
| Exam fee | $600-$800 | CISA/CISM reference |
| Annual Maintenance Fee (AMF) | $85-$135 | ISC²/ISACA reference |
| Continuing Professional Education (CPE) | 20 hours/year, 120 hours/3 years | Qualification maintenance requirement |

### 7.4 Exam Integrity

**Brain Dump Countermeasures:**
- Regular exam question pool updates
- Practical elements (scenario-based assessment)
- Fraud monitoring and revocation system
- Exam question confidentiality maintenance

> **Lesson:** Brain dump issues with CEH, CISSP, and others have degraded credential value. Exam integrity is the lifeblood of certification programs.

---

## 8. Success Principles and Red Flags

### 8.1 Principles for Success

| Principle | Content | Implementation |
|-----------|---------|----------------|
| **1. Independent Accreditation** | Structural separation of assessors and assessed | 4-layer separation, consulting prohibition, revenue diversification |
| **2. Transparent Revenue** | Public revenue model and fee structure | Published fee schedules, disclosed CAB accreditation fees |
| **3. Regulatory Alignment** | Address current and future regulatory requirements | EU AI Act, MiFID II, SEC 17a-4 mapping |
| **4. Ecosystem Partnerships** | Insurance, audit firms, tool vendor collaboration | Munich Re partnership, Big Four cooperation |
| **5. Fraud Policies** | Prevent fraud in exams and assessments | Identity verification, spot audits, zero-tolerance policy |
| **6. Clear, Transparent Standards** | Public measurement targets and methodology | Published scoring criteria, methodology documents, guidelines |
| **7. Demonstrated Value (Effectiveness)** | Build trust through outcomes | Incident tracking, compliance success of assessed entities |

### 8.2 Red Flags (Failure Triggers)

| Red Flag | Symptom | Countermeasure |
|----------|---------|----------------|
| **1. Unverified Outputs** | No third-party verification of assessment results | Spot reviews, cross-checks |
| **2. High Costs without Value** | High fees with unclear ROI | Price transparency, published success cases |
| **3. Vendor Lock-in** | Dependence on specific vendors | Open standards, multi-CAB structure |
| **4. Oversight Gaps** | Lack of CAB quality management | Annual audits, accreditation revocation system |
| **5. Pay-to-Pass Model** | Perception that "money buys passes" | VSO assessment prohibition, revenue structure monitoring |
| **6. Conflict of Interest / Commercial Exploitation** | 100% pass rates | Published pass rates |
| **7. Lack of Accountability / Enforcement** | Certification maintained despite violations | Automatic suspension mechanism, public revocation list |
| **8. Opaque or Overly Complex System** | "Bureaucratic," "paperwork only" criticism | 10-criterion simple design, continuous simplification |
| **9. Negative Market Feedback** | Criticism from key stakeholders | Feedback loops, rapid improvement |
| **10. Misalignment with Regulatory Evolution** | Fails to meet regulatory requirements | Continuous regulatory dialogue, flexible updates |

---

## 9. Insurance Industry Integration

### 9.1 Market Opportunity

**Current State:**
- Berkley and Hamilton have introduced "absolute AI exclusion clauses"
- Meanwhile, Munich Re "aiSure" and Coalition cover AI risks
- AI insurance premiums projected to reach $4.8B by 2032

**VAP-AT Value Proposition:**
- VAP-AT assessment results function as a "proxy" for insurance underwriting
- Premium discounts (10-15%) based on assessment scores
- Ecosystem where only high-score entities qualify for AI insurance

### 9.2 Proposed Integration Scheme

```
┌─────────────────────────────────────────────────────────────┐
│  AI Insurance Companies (Munich Re, Coalition, etc.)        │
│  ─────────────────────────────────────────────────          │
│  • Require VAP-AT "Verified" status for coverage            │
│  • Premium discounts based on Assessment Score              │
└─────────────────────────────────────────────────────────────┘
                                │
                                │ Underwriting Reference
                                ▼
┌─────────────────────────────────────────────────────────────┐
│  VAP-AT Assessment Results                                  │
│  ─────────────────────────────────────────────────          │
│  • Assessment Score (0-20)                                  │
│  • Threshold Designations                                   │
│  • Evidence Pack                                            │
└─────────────────────────────────────────────────────────────┘
                                │
                                │ Assessment
                                ▼
┌─────────────────────────────────────────────────────────────┐
│  Assessed Entities (AI Operators)                           │
│  ─────────────────────────────────────────────────          │
│  • Receive assessment                                       │
│  • Improve based on Score Report                            │
│  • Access insurance coverage                                │
└─────────────────────────────────────────────────────────────┘
```

---

## 10. Failure Avoidance

### 10.1 Anti-Patterns to Avoid

| Anti-Pattern | Manifestation | Prevention Measure |
|--------------|---------------|-------------------|
| **Certificate Mills** | Form-only certification | CAB annual audits, accreditation revocation, Public Registry |
| **Pay-to-Pass** | "Money buys passes" | VSO assessment prohibition, revenue monitoring, pass rate disclosure |
| **Audit Shopping** | Shopping for lenient CABs | VSO oversight, whistleblower system, Public Registry comparison |
| **Brain Dump** | Exam question leaks | Question pool rotation, practical exams, proctoring |
| **Greenwashing** | Certification misuse | Trademark protection, usage guidelines, violations list |

### 10.2 Monitoring Metrics

| Metric | Warning Threshold | Response |
|--------|------------------|----------|
| **Pass rate (Level 2)** | >95% | CAB audit, criteria review |
| **Score distribution** | Concentrated at threshold +1 point | Score inflation investigation |
| **CAB concentration** | Single CAB >50% market share | Competition promotion, incentives |
| **Complaint volume** | >5% of assessments | Root cause analysis, remediation |

---

## 11. EU AI Act Alignment

### 11.1 Article Mapping

| EU AI Act Article | VAP-AT Alignment | Evidence |
|-------------------|------------------|----------|
| **Art.9 (Risk Management)** | Level 2-3 assessment scope | Score Report |
| **Art.12 (Logging)** | Criterion 1-4 | Evidence Pack |
| **Art.14 (Human Oversight)** | Criterion 5 | Documentation |
| **Art.17 (QMS)** | CAB ISO 17065 alignment | Accreditation |
| **Art.19 (Log Retention)** | Criterion 7 | Retention verification |
| **Annex IV (Documentation)** | Criterion 6 | Technical documentation review |

### 11.2 Notified Body Path

**Objective:** Position VSO-accredited CABs as potential EU AI Act Notified Bodies

**Requirements:**
- ISO/IEC 17065 accreditation
- EU AI Act expertise
- Regulatory authority approval

**Roadmap:**
- Phase 1: Align with harmonized standards
- Phase 2: UKAS/DAkkS accreditation
- Phase 3: Notified Body application

---

## 12. Assessment Deliverables

### 12.1 Four-Document Set

| Deliverable | Format | Content | Distribution |
|-------------|--------|---------|--------------|
| **Score Report** | PDF | Assessment ID, Assessment Score (0-20), Grade, Threshold Designation (optional label), improvement recommendations, disclaimers | Assessed entity |
| **Machine-Readable Score** | JSON | Structured data, API integration ready | System integration |
| **Evidence Pack** | ZIP | checksums.sha256, log samples, config dumps, test reports | CAB retention |
| **Public Registry Entry** | Web | Company name, Grade, validity period, CAB name (optional publication) | Public (CSA STAR model) |

**Public Registry Disclosure Granularity Matrix:**

| Information | Public (General) | NDA Viewers (Contracted) | Assessed & Regulators |
|-------------|-----------------|-------------------------|----------------------|
| **Assessment conducted** | ○ | ○ | ○ |
| **Grade (Strong, etc.)** | ○ | ○ | ○ |
| **Detailed score (0-20)** | — | ○ | ○ |
| **Evidence Pack** | — | — | ○ |

> **Legend:** ○ = Information provided to this viewer class, — = Not provided

**Disclosure Level Selection:**
- Assessed entities select disclosure level (Public / Semi-public / Private) at assessment application
- Default is **Semi-public** (only assessment conducted + grade publicly visible)
- **Private** selection: Not publicly disclosed, but available to assessed entity, regulators, and designated audit recipients. The fact that assessment was conducted is still listed in Public Registry (complete non-disclosure not permitted)
- Disclosure level changes permitted once per year (upgrades take effect immediately)

**Evidence Pack Minimum Required Set:**

```
evidence_pack_v1.zip
├── checksums.sha256      [REQUIRED] Hash values for all files
├── score.json            [REQUIRED] Structured score data
├── report.pdf            [REQUIRED] Signed Score Report
├── evidence_index.json   [REQUIRED] Evidence file inventory and references
└── sample_logs/          [OPTIONAL] Log samples (with assessed entity written consent)
    ├── decision_log_sample.jsonl
    └── execution_log_sample.jsonl
```

> **Operating Principle:** Evidence Pack is complete with the 4 required files. sample_logs is optional and included only with assessed entity written consent. CABs may include additional files, but missing required files is not permitted.

### 12.2 Score Report Structure

```
1. Assessment Summary
   - Assessment ID (UUID)
   - Date / Validity Period
   - Assessed System(s)
   - CAB Name & Assessor(s)

2. Score Overview
   - Total Score (0-20) [PRIMARY OUTPUT]
   - Grade (Strong/Moderate/Limited/Inadequate)
   - Threshold Designation(s) [OPTIONAL INTERPRETIVE LABEL]

3. Criterion-by-Criterion Scores
   - Score (0/1/2)
   - Evidence Summary
   - Gap Analysis (if applicable)

4. Recommendations
   - Priority Improvements
   - Timeline Suggestions

5. Disclaimers [MANDATORY]
   - Assessment limitations
   - Threshold Designation is an interpretive label, not legal compliance certification
   - Not a guarantee of security or regulatory compliance
```

---

## 13. Roadmap

### Phase 0: Foundation (2025 Q4)
- [ ] VAP-AT Program Charter finalization
- [ ] Scoring Criteria v1.0 publication
- [ ] Evidence Pack Template publication
- [ ] Self-Assessment Tool (VAP Scorecard Explorer) release
- [ ] CAB Accreditation Requirements (VSO-CAB-REQ-001) development

### Phase 1: Pilot (2026 Q1–Q2)
- [ ] Pilot CAB #1 (VeritasChain株式会社) accreditation
- [ ] Pilot Assessment 3–5 cases
- [ ] Feedback collection and improvements
- [ ] VAP-AT Associate qualification program launch
- [ ] ISO/IEC 17065 accreditation preparation (DAkkS, UKAS)

**Pilot CAB Impartiality Safeguards:**

Pilot CAB #1 (VeritasChain株式会社) is legally related to VSO, requiring the following additional safeguards:

| Safeguard | Content |
|-----------|---------|
| **Independent CAB Cross-Check** | All assessment reports during Pilot phase undergo dual review by a VSO-designated independent third-party CAB (or external auditor) |
| **Impartiality Committee External Majority** | Pilot CAB's impartiality committee must have external members as the majority |
| **VSO Spot Audits** | VSO conducts random spot audits on 20%+ of Pilot CAB-issued reports |
| **Conflict Disclosure** | Pilot CAB-VSO relationship disclosed in writing to assessed entities before assessment commencement |
| **Phase 2 Transition Condition** | Pilot CAB solo operation does not continue until 2+ independent CABs are accredited |

> **Design Intent:** Having a related entity serve as Pilot CAB during program launch is rational for rapid framework validation. However, to proactively address "effectively the same entity" concerns from external parties, stricter independence assurance measures than regular CABs are applied.

### Phase 2: Launch (2026 Q3–Q4)
- [ ] VAP-AT Verified official launch
- [ ] Public Registry launch
- [ ] Additional CAB accreditation (2–3)
- [ ] EU AI Act Notified Body application
- [ ] Insurance company partnership pilot

### Phase 3: Scale (2027+)
- [ ] Continuous Monitoring launch
- [ ] International CAB accreditation (Europe, North America, Asia)
- [ ] IAF MLA participation consideration
- [ ] Expansion of insurance underwriting condition adoption
- [ ] AI Auditor qualification international expansion

---

## 14. Related Documents

| Document ID | Title |
|-------------|-------|
| VSO-BENCHMARK-SCORE-001 | VAP Scorecard Scoring Criteria v2.0 |
| VSO-VAP-SPEC-001 | VAP Framework Specification v1.1 |
| VSO-GOV-SCHEME-001 | VC-Certified Scheme Governance v1.0 |
| VSO-SPEC-001 | VCP Specification v1.0 |
| VSO-EXPLORER-001 | VAP Scorecard Explorer Reference |
| VSO-CAB-REQ-001 | CAB Accreditation Requirements (Planned) |
| VSO-SCHEME-RULE-001 | VAP-AT Scheme Rulebook (Planned) |
| VSO-AUDITOR-001 | Certified AI Systems Assessor Program (Planned) |

---

## 15. Glossary

| Term | Definition |
|------|------------|
| **VAP-AT** | Verifiable AI Provenance – Assessment Test |
| **Assessment Score** | Detailed evaluation score from 0-20 (VAP-AT primary deliverable) |
| **Assessment Status** | Operational state of assessment (Active/Suspended/Pending Review/Expired) |
| **VSO** | VeritasChain Standards Organization (standard-setting body) |
| **CAB** | Conformity Assessment Body |
| **AB** | Accreditation Body |
| **3PAO** | Third-Party Assessment Organization |
| **QSA** | Qualified Security Assessor (PCI DSS certified assessor) |
| **Evidence Pack** | ZIP package containing assessment results and evidence |
| **Score Report** | PDF report containing assessment score and improvement recommendations |
| **Type I** | Point-in-time audit (design appropriateness evaluation) |
| **Type II** | Period audit (operational performance verification) |
| **Preliminary** | Status based on self-assessment |
| **Verified** | Third-party assessment status by CAB |
| **AMF** | Annual Maintenance Fee |
| **CPE** | Continuing Professional Education |
| **Certificate Mills** | Problematic certification bodies mass-issuing hollow certifications |
| **Brain Dump** | Unauthorized exam question leaks/sharing |
| **Audit Shopping** | Seeking lenient CABs for assessments |
| **Threshold Designation** | Score-threshold-based label (optional interpretive layer, not legal guarantee) |

---

## 16. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1 | 2025-12-28 | VSO | Initial draft |
| 0.2 | 2025-12-28 | VSO | Integrated Gemini/PPLX/Claude research: market data, price benchmarks, failure analysis, auditor qualifications, insurance integration |
| 0.3 | 2025-12-28 | VSO | Integrated GPT research: detailed program comparison, 5 organizational models, expanded failure cases (Safe Harbor/VW/CEH/CMMC), 5 success principles/5 red flags, Score vs Pass/Fail strategy (UL IoT Rating reference), market data update (RegTech 124% growth), EU AI Act Art.19 |
| 0.4 | 2025-12-28 | VSO | Integrated GROK research: AI Governance market $15.8B (2030), added CCSP/CISM/BABL AI/IIA/ORCAA to program comparison, added Texas Teacher Certifications/U.S. Job Corps failure cases, expanded to 7 success principles/10 red flags, price sensitivity analysis ($50K resistance threshold), Score vs Pass/Fail regulatory sector strategy insights |
| 0.5 | 2025-12-28 | VSO | Quality review: (1) EU AI Act article correction (Art.19→Art.12, tamper-evidence as enhancement), (2) Market size figures moved to footnotes, (3) Dual accreditation model (Scheme/ISO) clarification, (4) Threshold Designation disclaimer (scheme label ≠ legal compliance), (5) 4-state certification status definition, (6) Evidence Pack minimum required set |
| 0.6 | 2025-12-28 | VSO | Additional enhancements: (1) VAP-AT non-scope clarification ("AI decision correctness ≠ assessment target"), (2) CAB rotation rules fixed (same CAB max 3 years, Lead Assessor 2 years, cooling-off 2 years), (3) Public Registry disclosure granularity matrix |
| 0.6a | 2025-12-28 | VSO | External presentation quality: (1) Score-based principle explicit (Executive Summary), Threshold Designation as "optional interpretive layer", (2) EU AI Act article alignment (Art.12=logging, Art.19=retention), tamper-evidence as "evidentiary robustness", (3) Threshold Designation wording risk removal ("Meets..."→"aligned"), (4) Public Registry matrix restructured to viewer-based columns, (5) Roadmap/status alignment, (6) Pilot CAB impartiality safeguards (dual review, external majority, spot audits), (7) Assessment Status terminology unified, binary language removed |

---

*Copyright © 2025 VeritasChain Standards Organization. Licensed under CC BY 4.0.*
