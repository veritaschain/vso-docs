# Content / Creative AI Profile (CAP)

## Basic Specification v0.1

**Document ID:** VSO-CAP-SPEC-001  
**Status:** Draft Specification  
**Version:** 0.1.0  
**Date:** 2025-12-27  
**Maintainer:** VeritasChain Standards Organization (VSO)  
**License:** CC BY 4.0 International  
**Website:** https://veritaschain.org  
**Contact:** standards@veritaschain.org

---

## Executive Summary

**CAP（Content / Creative AI Profile）** は、VAP（Verifiable AI Provenance Framework）の新規ドメインプロファイルとして、コンテンツ・クリエイティブ産業におけるAI利用の証跡基盤を規定する。

CAPは「AIの利用を禁止・検閲する規制」ではない。  
CAPは「争点発生時に第三者が検証可能な証跡（Evidence）を残す枠組み」である。

**問題の本質はAIそのものではなく、そのブラックボックス性にある。**

コンテンツ産業においてAIは既に広範に利用されており、その利用を停止することは現実的ではない。重要なのは、権利侵害・機密漏洩・人格侵害などの争点が発生した際に、「誰が」「何を」「どのような権限で」「いつ」AIワークフローに投入・学習・生成・出力したかを、暗号学的に否認不可能な形式で記録し、事後検証を可能にすることである。

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

CAP（Content / Creative AI Profile）は、以下の構造的課題を解消するために設計された証跡フレームワークである：

| 課題 | 説明 | CAPによる解決 |
|------|------|---------------|
| **権利来歴の不透明性** | AIに投入された素材の権利根拠が追跡不能 | RightsBasis フィールドによる権利根拠の記録 |
| **同意の曖昧性** | 学習・生成への同意有無が不明確 | ConsentBasis による同意状態の固定 |
| **機密区分の欠落** | 未発表素材の機密性が管理されていない | ConfidentialityLevel による機密分類 |
| **責任境界の不明確性** | 争点発生時の責任主体が特定不能 | User/Role による実行者の記録 |
| **改ざん可能性** | 事後的な記録書き換えが可能 | Hash Chain による暗号的保証 |

### 1.2 Design Philosophy

CAPは以下の基本理念に基づく：

> **「AIを止める」思想ではなく「証拠を残す」思想**

AIの創作活動への活用は不可逆的に進行している。CAPはこの現実を前提とし、利用の禁止や検閲ではなく、「事後に第三者が検証できる証跡」を残すことに焦点を当てる。

これにより：
- 権利者は侵害発生時に立証根拠を得られる
- 制作者は正当な利用を証明できる
- 規制当局は監査・検査の基盤を得られる
- 業界全体として信頼性のあるAI活用が可能になる

### 1.3 Scope Definition

CAPは以下を対象とする：

- **コンテンツ/IP資産**を主語とするAIワークフロー
- **学習（TRAIN）・生成（GEN）** を含むAI利用プロセス
- **争点発生時の事後検証**を目的とした証跡記録

CAPは以下を対象としない：

- AI判断のリアルタイム制御・介入
- 著作権侵害の自動判定
- 生成物の「良し悪し」の評価

### 1.4 Conformance Language

本仕様書において、以下のキーワードは RFC 2119 に準拠して解釈される：

- **MUST** / **REQUIRED** / **SHALL**: 絶対的な要件
- **MUST NOT** / **SHALL NOT**: 絶対的な禁止
- **SHOULD** / **RECOMMENDED**: 推奨事項（正当な理由がある場合は逸脱可能）
- **MAY** / **OPTIONAL**: 任意事項

### 1.5 Terminology

| Term | Definition |
|------|------------|
| **CAP** | Content / Creative AI Profile - コンテンツ産業向けVAPプロファイル |
| **VAP** | Verifiable AI Provenance Framework - 上位フレームワーク |
| **VSO** | VeritasChain Standards Organization - 標準化団体 |
| **Asset** | AIワークフローの対象となるコンテンツ/IP資産 |
| **Provenance** | 資産の出所・由来・履歴の暗号学的に検証可能な記録 |
| **Evidence Pack** | CAPイベントの集合体として構成される証跡パッケージ |

---

## 2. Position within VAP Framework

### 2.1 VAP/VSO/CAP Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│     VAP (Verifiable AI Provenance Framework)                    │
│     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                    │
│     AI判断証跡の「概念・上位フレームワーク」                      │
│     全ドメイン共通の最低要件・抽象レイヤーを定義                   │
│                                                                 │
│                          ▲                                      │
│                          │ defines & maintains                  │
│                          │                                      │
│     VSO (VeritasChain Standards Organization)                   │
│     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━                   │
│     VAPを策定・維持・認証する「標準化団体」                        │
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
│     ドメイン固有の「具体プロトコル実装」                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.2 Relationship to VCP

| 観点 | VCP (Finance Profile) | CAP (Content Profile) |
|------|----------------------|----------------------|
| **主語** | 取引（Transaction） | コンテンツ/IP資産（Asset） |
| **対象業界** | 金融・取引 | ゲーム・映像・出版・音楽 |
| **主要イベント** | SIG/ORD/EXE/CXL | INGEST/TRAIN/GEN/EXPORT |
| **規制参照** | MiFID II, EU AI Act | EU AI Act, DSA, 著作権法 |
| **時刻精度要件** | ナノ秒〜ミリ秒 | 秒〜分（業務依存） |
| **共通基盤** | VAP Integrity Layer | VAP Integrity Layer |

### 2.3 Shared Infrastructure

CAPは以下のVAP共通基盤を継承する：

- **Hash Chain**: イベント連鎖の改ざん検知
- **Merkle Tree**: 大量イベントの効率的検証
- **Digital Signature**: Ed25519による発行者認証
- **Crypto Agility**: 将来のアルゴリズム移行対応

---

## 3. Target Industries

### 3.1 Priority Classification

CAPの適用対象業界を以下の優先度で分類する：

#### Priority A（最優先）

| 業界 | サブセグメント | 主要リスク |
|------|---------------|-----------|
| **ゲーム** | AAA/パブリッシャー/スタジオ/外注 | IP希薄化、機密漏洩、キャラクター模倣 |
| **映画・アニメ・配信** | 制作会社/VFX/ポスプロ/OTT | 俳優肖像権、声優音声、未発表映像漏洩 |

#### Priority B（次点）

| 業界 | サブセグメント | 主要リスク |
|------|---------------|-----------|
| **出版** | 漫画/書籍/編集プロダクション | 作風模倣、原稿流出、翻訳品質 |
| **音楽** | レーベル/配信/MV制作/管理団体 | 声紋クローン、楽曲模倣、権利処理 |

#### Priority C（参考）

| 業界 | サブセグメント | 主要リスク |
|------|---------------|-----------|
| **成人向け** | 制作/配信/プラットフォーム | ディープフェイク、同意なき生成 |
| **企業ブランド** | Web/IR/決算資料/デザイン | トーン模倣、ブランド毀損 |
| **教育・研修** | 大学/研究機関/企業研修/教材制作 | 論文盗用、教材の無断学習、研修資料流出 |

### 3.2 Industry-Specific Considerations

各業界には固有の考慮事項が存在する。CAPはこれらを最小共通項として抽象化しつつ、業界固有拡張（Industry-Specific Extensions）の余地を残す：

| 業界 | 固有考慮事項 | CAP対応 |
|------|-------------|---------|
| ゲーム | 長期開発サイクル、大量アセット | AssetID階層化、バッチINGEST |
| 映像 | ライセンス複雑性、制作委員会 | ConsentBasis多段階、Role拡張 |
| 出版 | 二次創作許諾、翻案権 | PermittedUse粒度細分化 |
| 音楽 | 著作権/著作隣接権分離 | RightsBasis複数記録 |

---

## 4. Threat Model

### 4.1 Overview

CAPが対象とする脅威は、AIワークフローにおける以下の5類型に分類される：

```
┌─────────────────────────────────────────────────────────────────┐
│                      CAP Threat Taxonomy                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TH-1: IP Dilution (IP希薄化)                                   │
│  ├─ 独自の表現様式・世界観がAIにより安易に模倣される             │
│  └─ ブランド価値の希釈、市場における差別化困難                   │
│                                                                 │
│  TH-2: Reverse Flow (逆流による権利侵害)                         │
│  ├─ 自社素材を学習したAIを第三者が使用                          │
│  └─ 自社製品に酷似した生成物が市場に流出                        │
│                                                                 │
│  TH-3: Confidential Leakage (機密情報漏洩)                      │
│  ├─ 未発表キャラ/設定資料/映像素材/コードがAIに投入             │
│  └─ 学習データ経由で外部に流出                                  │
│                                                                 │
│  TH-4: Deepfake / Persona Abuse (人格侵害)                      │
│  ├─ 私的画像・動画を無断利用した生成                            │
│  └─ 名誉毀損、性的コンテンツ、いじめ                            │
│                                                                 │
│  TH-5: Brand/Style Mimicry (ブランド・表現様式模倣)             │
│  ├─ 企業HP/IR/決算資料のデザイン・トーン模倣                    │
│  └─ 公式と誤認させる生成物                                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 4.2 Threat Actor Analysis

| Actor | 説明 | 関連脅威 |
|-------|------|---------|
| **外部攻撃者** | 悪意を持つ第三者 | TH-2, TH-4, TH-5 |
| **内部関係者** | 従業員、契約者、外注先 | TH-3, TH-2 |
| **AIベンダー** | モデル提供者、SaaSプロバイダー | TH-2, TH-3 |
| **エンドユーザー** | 生成AIサービス利用者 | TH-1, TH-4, TH-5 |
| **競合他社** | 業界内競争者 | TH-1, TH-2, TH-5 |

### 4.3 Attack Surface by Lifecycle Stage

```
素材投入        学習            生成            配布
(INGEST)       (TRAIN)         (GEN)          (EXPORT)
   │              │              │              │
   ▼              ▼              ▼              ▼
┌──────┐     ┌──────┐      ┌──────┐      ┌──────┐
│権利  │     │同意  │      │類似性│      │流出  │
│不明確│     │逸脱  │      │問題  │      │経路  │
└──────┘     └──────┘      └──────┘      └──────┘
   │              │              │              │
   ▼              ▼              ▼              ▼
TH-1,TH-3     TH-2,TH-3      TH-1,TH-4      TH-2,TH-5
```

### 4.4 Threat-to-Field Mapping

CAPのフィールドは各脅威に対応する証跡を提供する：

| 脅威 | 対応フィールド | 記録内容 |
|------|---------------|---------|
| TH-1: IP希薄化 | AssetID, RightsBasis | 原資産の特定と権利根拠 |
| TH-2: 逆流 | AssetID, ModelContext | 学習に使用されたモデルと素材 |
| TH-3: 機密漏洩 | ConfidentialityLevel, User | 機密区分と投入者 |
| TH-4: 人格侵害 | ConsentBasis, AssetID | 同意状態と対象資産 |
| TH-5: ブランド模倣 | RightsBasis, PermittedUse | 許諾範囲と利用態様 |

---

## 5. Event Model

### 5.1 Core Event Types

CAPは以下の4つの必須イベントタイプを定義する：

```
┌─────────────────────────────────────────────────────────────────┐
│                    CAP Event Lifecycle                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   INGEST ──────► TRAIN ──────► GEN ──────► EXPORT              │
│     │              │            │            │                  │
│     ▼              ▼            ▼            ▼                  │
│  素材投入       学習実行      生成実行     外部出力              │
│                                                                 │
│  ・画像/動画    ・フル学習    ・画像生成   ・納品               │
│  ・音声/音楽    ・追加学習    ・動画生成   ・配布               │
│  ・文章/台本    ・LoRA/PEFT   ・音声合成   ・公開               │
│  ・コード       ・Embedding   ・文章生成   ・社内共有           │
│  ・3Dモデル                   ・コード生成                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 5.2 Event Type Definitions

#### 5.2.1 INGEST (素材投入)

| 属性 | 値 |
|------|-----|
| **EventType** | INGEST |
| **Code** | 1 |
| **Description** | 素材・データ・参照情報のAIワークフローへの投入 |
| **Trigger** | ユーザーまたはシステムによるアセット入力 |
| **Required Fields** | EventID, Timestamp, AssetID, RightsBasis, ConfidentialityLevel, User |

INGESTイベントは以下を記録する：
- 投入されたアセットの識別情報
- 権利根拠（自社制作/ライセンス取得/パブリックドメイン/不明）
- 機密区分（公開/社外秘/極秘/発表前）
- 投入者の識別情報

#### 5.2.2 TRAIN (学習)

| 属性 | 値 |
|------|-----|
| **EventType** | TRAIN |
| **Code** | 2 |
| **Description** | モデルの学習・追加学習・ファインチューニング |
| **Trigger** | 学習ジョブの開始または完了 |
| **Required Fields** | EventID, Timestamp, ModelContext, TrainingType, InputAssetIDs, User |

TRAINイベントは以下を記録する：
- 学習対象モデルの識別情報
- 学習タイプ（フル学習/追加学習/LoRA/PEFT等）
- 入力として使用されたアセットID群
- 学習実行者の識別情報

#### 5.2.3 GEN (生成)

| 属性 | 値 |
|------|-----|
| **EventType** | GEN |
| **Code** | 3 |
| **Description** | AIによるコンテンツ生成 |
| **Trigger** | 生成リクエストの実行 |
| **Required Fields** | EventID, Timestamp, ModelContext, OutputAssetID, PromptHash, User |

GENイベントは以下を記録する：
- 使用されたモデルの識別情報
- 生成された出力アセットのID
- プロンプト/入力のハッシュ値（プライバシー保護）
- 生成実行者の識別情報

#### 5.2.4 EXPORT (外部出力)

| 属性 | 値 |
|------|-----|
| **EventType** | EXPORT |
| **Code** | 4 |
| **Description** | 生成物の外部出力・配布・納品 |
| **Trigger** | コンテンツの組織外への移動 |
| **Required Fields** | EventID, Timestamp, AssetID, Destination, PermittedUse, User |

EXPORTイベントは以下を記録する：
- 出力されたアセットの識別情報
- 出力先（納品先/公開先/配布先）
- 許諾された利用範囲
- 出力実行者の識別情報

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
| 1001 | **EventID** | UUID | 一意のイベント識別子 | MUST use UUID v7 or v4 |
| 1002 | **ChainID** | UUID | イベントチェーン識別子 | 同一ワークフロー内で共通 |
| 1003 | **PrevHash** | String | 直前イベントのハッシュ | Hash Chain形成用 |
| 1010 | **Timestamp** | ISO 8601 | イベント発生時刻 | UTC必須、秒精度以上 |
| 1011 | **EventType** | Enum | イベント種別 | See Section 5.3 |
| 1020 | **HashAlgo** | Enum | ハッシュアルゴリズム | SHA256 (default) |
| 1021 | **SignAlgo** | Enum | 署名アルゴリズム | ED25519 (default) |

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
| 2001 | **AssetID** | String | 資産識別子 | 組織内で一意、URN形式推奨 |
| 2002 | **AssetType** | Enum | 資産種別 | IMAGE/VIDEO/AUDIO/TEXT/CODE/3D/OTHER |
| 2003 | **AssetHash** | String | 資産コンテンツのハッシュ | SHA-256、改ざん検知用 |
| 2004 | **AssetName** | String | 資産名（任意） | 人間可読な識別名 |
| 2010 | **ParentAssetID** | String | 親資産ID（任意） | 派生関係の記録 |

#### 6.2.2 AssetType Enum

| Value | Description | Examples |
|-------|-------------|----------|
| **IMAGE** | 静止画像 | PNG, JPEG, PSD, AI, SVG |
| **VIDEO** | 動画 | MP4, MOV, AVI, ProRes |
| **AUDIO** | 音声/音楽 | WAV, MP3, FLAC, AAC |
| **TEXT** | テキスト/文書 | TXT, MD, DOCX, PDF, Script |
| **CODE** | ソースコード | Python, C++, Shader, Config |
| **3D** | 3Dモデル/アセット | FBX, OBJ, GLTF, USD |
| **OTHER** | その他 | 複合、未分類 |

### 6.3 CAP-RIGHTS: Rights and Consent

#### 6.3.1 Rights Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 3001 | **RightsBasis** | Enum | 権利根拠 | See RightsBasis Enum |
| 3002 | **RightsHolder** | String | 権利者識別子 | 自社/第三者/複数 |
| 3003 | **LicenseID** | String | ライセンス識別子（任意） | 契約番号等 |
| 3010 | **ConsentBasis** | Enum | 同意根拠 | See ConsentBasis Enum |
| 3011 | **ConsentScope** | Array | 同意範囲 | 学習/生成/配布等 |
| 3012 | **ConsentExpiry** | ISO 8601 | 同意有効期限（任意） | UTC |
| 3020 | **PermittedUse** | Object | 許諾利用範囲 | See PermittedUse Object |

#### 6.3.2 RightsBasis Enum

| Value | Description | 証跡要件 |
|-------|-------------|---------|
| **OWNED** | 自社制作/著作権保有 | 制作記録、著作権登録 |
| **LICENSED** | 第三者からライセンス取得 | 契約書、許諾書面 |
| **PUBLIC_DOMAIN** | パブリックドメイン | 根拠の明示 |
| **CREATIVE_COMMONS** | CCライセンス | ライセンス種別の明示 |
| **FAIR_USE** | フェアユース主張 | 根拠の文書化 |
| **UNKNOWN** | 権利関係不明 | リスク受容の記録 |

#### 6.3.3 ConsentBasis Enum

| Value | Description | 法的根拠例 |
|-------|-------------|-----------|
| **EXPLICIT_WRITTEN** | 明示的書面同意 | 契約書、同意書 |
| **EXPLICIT_DIGITAL** | 明示的電子同意 | 電子署名、クリック同意 |
| **IMPLIED** | 黙示的同意 | 業務慣行、契約範囲内 |
| **STATUTORY** | 法定許容 | 著作権法例外規定 |
| **NOT_REQUIRED** | 同意不要 | パブリックドメイン |
| **NONE** | 同意なし | リスク受容の記録 |
| **REVOKED** | 同意撤回済 | 撤回日時の記録 |

#### 6.3.4 PermittedUse Object

```json
{
  "PermittedUse": {
    "Training": true,           // 学習利用可否
    "Generation": true,         // 生成利用可否
    "Distribution": false,      // 配布可否
    "Commercial": true,         // 商用利用可否
    "Derivative": true,         // 二次的著作物作成可否
    "Attribution": true,        // クレジット表示要否
    "Restrictions": [           // その他制限事項
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
| 4001 | **ConfidentialityLevel** | Enum | 機密区分 | See ConfidentialityLevel Enum |
| 4002 | **ClassificationDate** | ISO 8601 | 区分設定日 | UTC |
| 4003 | **Classifier** | String | 区分設定者 | User ID |
| 4010 | **ReleaseDate** | ISO 8601 | 公開予定日（任意） | 発表前素材用 |
| 4011 | **HandlingInstructions** | String | 取扱注意事項（任意） | 自由テキスト |

#### 6.4.2 ConfidentialityLevel Enum

| Value | Description | AIワークフロー制限 |
|-------|-------------|------------------|
| **PUBLIC** | 公開情報 | 制限なし |
| **INTERNAL** | 社内限定 | 社内環境のみ |
| **CONFIDENTIAL** | 社外秘 | 指定者のみ、外部送信禁止 |
| **SECRET** | 極秘 | 厳格なアクセス制御 |
| **PRE_RELEASE** | 発表前 | 公開日まで厳格管理 |

### 6.5 CAP-CONTEXT: Model and User Context

#### 6.5.1 Model Context Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 5001 | **ModelID** | String | モデル識別子 | ベンダー提供または内部ID |
| 5002 | **ModelVersion** | String | モデルバージョン | セマンティックバージョニング推奨 |
| 5003 | **ModelType** | Enum | モデル種別 | LLM/IMAGE_GEN/AUDIO_GEN/VIDEO_GEN/OTHER |
| 5004 | **ModelProvider** | String | モデル提供者 | ベンダー名または内部 |
| 5010 | **Environment** | Enum | 実行環境 | LOCAL/CLOUD/HYBRID |
| 5011 | **EnvironmentID** | String | 環境識別子（任意） | テナントID、インスタンスID等 |

#### 6.5.2 User Context Fields

| Tag | Field | Type | Description | Requirements |
|-----|-------|------|-------------|--------------|
| 6001 | **UserID** | String | ユーザー識別子 | 組織内で一意、匿名化可 |
| 6002 | **Role** | Enum | 役割 | See Role Enum |
| 6003 | **Department** | String | 所属部門（任意） | 組織構造に依存 |
| 6010 | **SessionID** | String | セッション識別子（任意） | 一連の操作の追跡用 |

#### 6.5.3 Role Enum

| Value | Description |
|-------|-------------|
| **CREATOR** | コンテンツ制作者（アーティスト、デザイナー等） |
| **ENGINEER** | 技術者（MLエンジニア、開発者等） |
| **MANAGER** | 管理者（プロデューサー、ディレクター等） |
| **REVIEWER** | 審査者（法務、コンプライアンス等） |
| **SYSTEM** | システム自動処理 |
| **EXTERNAL** | 外部関係者（外注、パートナー等） |

### 6.6 Integrity Layer

#### 6.6.1 Hash Chain Structure

各イベントは直前イベントのハッシュを含み、改ざん不可能なチェーンを形成する：

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

CAPは **Comply-or-Explain（遵守または説明）** を基本原則とする。

これは：
- CAP準拠を**強制**するものではない
- 準拠しない場合は**その理由を説明可能**にすることを求める
- 規制当局・監査人・権利者への**説明責任**を果たす枠組みを提供する

### 7.2 Evidence-Based Accountability

CAPは以下の「証拠に基づく説明責任」を実現する：

| 場面 | CAPなし | CAPあり |
|------|--------|--------|
| 権利侵害疑義 | 「使っていない」と主張するのみ | INGESTログで使用/不使用を証明 |
| 機密漏洩調査 | 流出経路の特定困難 | EXPORT先とタイミングを追跡 |
| 同意確認 | 口頭での曖昧な確認 | ConsentBasisの暗号学的記録 |
| 監査対応 | 事後的な記録作成 | リアルタイムのEvidence Pack |

### 7.3 Negative Proof Capability

CAPの重要な機能の一つは、**Negative Proof（否定証明）**の提供である。

> **CAP enables not only proof of use, but also negative proof — the ability to demonstrate that specific assets were NOT ingested, trained on, or referenced.**

従来の監査手法では「使用した」ことの証明は可能でも、「使用していない」ことの証明は極めて困難であった。CAPのHash Chain構造により、特定の期間内に記録されたすべてのINGESTイベントを網羅的に提示し、「当該資産がワークフローに投入されていない」ことを暗号学的に証明できる。

これにより：
- 権利者からの「無断使用」疑義に対し、ログの完全性を根拠に反証可能
- 競合他社からの「模倣」主張に対し、独立した創作プロセスを立証可能
- 内部調査において「機密資産の非使用」を証明可能

### 7.3 Disclosure Template

CAP準拠組織は以下の開示テンプレートを使用できる：

```
【CAP Compliance Statement】

Organization: [組織名]
CAP Version: 0.1
Compliance Level: [FULL / PARTIAL / ASPIRING]
Scope: [対象システム/プロジェクト]

Covered Events:
☑ INGEST  ☑ TRAIN  ☑ GEN  ☐ EXPORT

Deviations from Specification:
- [逸脱項目1]: [理由]
- [逸脱項目2]: [理由]

Evidence Retention Period: [保存期間]
Audit Contact: [監査連絡先]
Last Updated: [更新日]
```

---

## 8. Non-Goals

### 8.1 Explicit Exclusions

CAPは以下を**明示的に対象外**とする：

| 非ゴール | 説明 | 理由 |
|---------|------|------|
| **AI利用の事前禁止** | 特定のAI利用を禁止・検閲しない | 証跡記録に専念、判断は人間が行う |
| **著作権侵害の自動判定** | 侵害の有無を自動判定しない | 法的判断は専門家・裁判所の領域 |
| **類似度＝違法性の判断** | 生成物の類似度を違法性に変換しない | 類似していても合法な場合あり |
| **モデル内部構造の開示強制** | モデルの重み等の開示を要求しない | 営業秘密保護、実装中立性 |
| **リアルタイム制御** | AI判断への介入・制御を行わない | 事後検証に特化 |
| **品質評価** | 生成物の品質・価値を評価しない | 主観的判断は範囲外 |

### 8.2 Boundary Clarification

```
┌─────────────────────────────────────────────────────────────────┐
│                     CAPの責任範囲                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  CAPが行うこと                 │  CAPが行わないこと              │
│  ─────────────────────         │  ─────────────────────          │
│  ✓ イベントの記録              │  ✗ イベントの承認/拒否           │
│  ✓ 証跡の暗号学的保護          │  ✗ コンテンツの検閲              │
│  ✓ 来歴（Provenance）の追跡    │  ✗ 侵害の判定                    │
│  ✓ 監査可能性の提供            │  ✗ 罰則の執行                    │
│  ✓ 相互運用性の確保            │  ✗ 特定技術の強制                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 8.3 Note on Similarity Metrics (Non-Normative)

**CAP does not define similarity thresholds for legality or compliance.**

生成物と既存著作物の「類似度（Similarity Score）」は、調査の端緒として参考にされる場合があるが、CAPはこれを規範的要件として定義しない。

> Similarity metrics MAY be used as investigative signals, but MUST NOT be treated as determinative evidence without provenance records.

類似度の高低のみでは、以下を判定することはできない：
- 著作権侵害の有無（法的判断は複合的要素による）
- 学習データへの包含（類似していても独立創作の可能性）
- 意図的な模倣（偶然の一致の可能性）

CAPは類似度判定ツールと**併用**されることを想定するが、最終的な判断根拠は常に**Provenanceレコード**（INGEST/TRAIN/GEN/EXPORTの証跡）に基づくべきである。

---

## 9. Regulatory Alignment

### 9.1 Applicable Regulations

CAPは以下の規制・ガイドラインへの接続点を提供する：

| 規制/ガイドライン | 管轄 | CAP関連要件 |
|-----------------|------|-----------|
| **EU AI Act** | EU | Art.12 ログ記録、Art.53 透明性 |
| **Digital Services Act (DSA)** | EU | 生成AIコンテンツの開示 |
| **GDPR** | EU | 処理記録、同意管理 |
| **Copyright Directive** | EU | TDM例外、オプトアウト |
| **著作権法** | 日本 | 30条の4、AI学習例外 |
| **AI事業者ガイドライン** | 日本 | 透明性、説明責任 |

### 9.2 EU AI Act Alignment

EU AI Act Article 12（ログ記録）との対応：

| EU AI Act要件 | CAPフィールド | 対応状況 |
|--------------|--------------|---------|
| イベントの自動記録 | EventID, Timestamp | ✓ 対応 |
| 入力データの追跡 | AssetID, AssetHash | ✓ 対応 |
| 出力の識別 | OutputAssetID | ✓ 対応 |
| 人間による監視の記録 | UserID, Role | ✓ 対応 |

### 9.3 Japan Copyright Law Alignment

著作権法30条の4（情報解析のための複製等）との関係：

| 論点 | CAP対応 |
|------|--------|
| 学習利用の証跡 | TRAINイベントで記録 |
| 享受目的の有無 | PermittedUse.Generation で明示 |
| 特定作風への集中学習 | InputAssetIDs の分析で検証可能 |

---

## 10. Implementation Guidelines

### 10.1 Implementation Levels

| Level | 名称 | 要件 | 想定対象 |
|-------|------|------|---------|
| **L1** | Basic | INGEST/GEN の記録 | 小規模スタジオ、個人 |
| **L2** | Standard | 全4イベント、Hash Chain | 中規模制作会社 |
| **L3** | Enterprise | L2 + Merkle Anchor、外部検証 | 大手パブリッシャー |

### 10.2 Minimum Viable Implementation

最小実装（L1）の要件：

1. **INGEST記録**: 投入素材のAssetID、RightsBasis、User
2. **GEN記録**: 生成出力のAssetID、ModelContext、User
3. **ローカル保存**: JSON形式でのイベントログ保存
4. **基本整合性**: SHA-256によるイベントハッシュ

### 10.3 Evidence Pack Structure

```
evidence-pack-{ChainID}/
├── manifest.json           # パック概要、検証情報
├── events/
│   ├── 001-ingest.json     # INGESTイベント
│   ├── 002-train.json      # TRAINイベント
│   ├── 003-gen.json        # GENイベント
│   └── 004-export.json     # EXPORTイベント
├── signatures/
│   └── chain-signature.sig # チェーン全体の署名
└── anchors/
    └── merkle-root.json    # Merkle Root（L3のみ）
```

---

## 11. Appendix A: JSON Examples (Non-Normative)

**注記**: 以下の例は説明目的であり、規範的（normative）ではない。実装者は本仕様書の要件に基づき、適切な形式を採用すること。

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
    "AssetName": "主人公キャラクターデザイン案A"
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
