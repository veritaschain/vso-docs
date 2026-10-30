# VAP-AT Program Charter

> **ステータス訂正 — 2026年10月25日、範囲明確化 — 2026年10月30日**
>
> - 本書は日付付きのドラフト（v0.6a、2025-12-28、"Draft for Internal Review"）であり、現行のプログラム説明ではありません。現行の説明は [veritaschain/vap-spec `programs/vap-at/`](https://github.com/veritaschain/vap-spec/tree/main/programs/vap-at) を参照してください。
> - §3 の「非営利標準策定 + 独立CAB」モデルは、本ドラフトが参考にした構造モデルであり、VSO が非営利であることを示すものではありません。VSO の運営主体は VeritasChain株式会社です。VSO は、中立性を法人形態ではなく公開された仕組みに基づくものと説明しています。
> - 本書の「認定」（accreditation、VSO Accredited CAB 等）は「VSO による承認（VSO-approved）」と読み替えてください。VSO による CAB の承認は ISO/IEC 17000 の意味での認定（accreditation）ではありません。[現行 CAB 登録簿と役割の説明](https://veritaschain.org/certified/cab/)を参照してください。
> - VSO は認証を直接発行しません。CAB はスキームオーナーから独立していることが要件ですが、登録済みの唯一の CAB である VeritasChain株式会社（下記の Pilot CAB #1）は独立していません（VAP v1.2 ERRATA E-2026-10-21）。独立した CAB は登録されていません。
> - スコアや Threshold Designation は法令適合を判定するものではありません（VAP v1.2 §1.6）。本書が参照する VAP v1.1 は、新規作業については VAP v1.2（Draft 3）に置き換えられています。
> - 下記の歴史資料に含まれる市場規模、規制日程、ロードマップの記述は変更していません。[Regulation (EU) 2026/1744 第1条(40)(b)](https://eur-lex.europa.eu/eli/reg/2026/1744/oj)は AI Act 第113条(c)を改正しています。対象は第III章第1～3節（第6条(5)を除く）で、第6条(2)・附属書IIIに基づく高リスクシステムは2027年12月2日から、第6条(1)・附属書Iに基づく高リスクシステムは2028年8月2日から適用されます。AI Act 全体の延期を意味するものではなく、他の条項や経過措置には別の適用日があります。[欧州委員会の現行日程説明](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)も参照してください。

**Document ID:** VSO-VAP-AT-001  
**Version:** 0.6a (Draft, revised)  
**Status:** Draft for Internal Review  
**Date:** 2025-12-28  
**Maintainer:** VeritasChain Standards Organization (VSO)  
**License:** CC BY 4.0

---

## Executive Summary

**VAP-AT（Verifiable AI Provenance – Assessment Test）** は、AIシステムの**監査可能性（Auditability）・検証可能性（Verifiability）・規制対応準備度（Regulatory Readiness）**を測定ベースでスコア化する評価制度である。

個人スキルを測る資格試験（CISSP型）ではなく、**AIシステムそのもの**を評価対象とする点で本質的に異なる。バイナリ判定（Pass/Fail）ではなく、**スコアと改善エビデンス**を残す設計により、継続的な信頼構築を可能にする。

> **Core Design Principle（スコアベース原則）：**
> 
> VAP-ATは原則**スコアベース**の評価制度である。Threshold Designation（閾値判定ラベル）は、調達要件や規制報告等の実務要請に対応するための**任意の解釈レイヤ**であり、Pass/Fail認証とは異なる。スコアは被評価者の継続的改善を促進し、市場・規制当局に粒度の高い情報を提供することを目的とする。

**市場機会：**
- **強力な規制追い風（Strong regulatory tailwinds）**: EU AI Act、MiFID II、SEC 17a-4等の規制強化
- **確立された支払意思ベンチマーク**: SOC 2 / ISO 27001 / FedRAMP の価格帯が市場受容性を実証済み
- RegTech市場：**$830億（2023年）→ $2,000億（2028年）、124%成長**
- EU AI Act違反罰則：最大**€3,500万または売上高の7%**

> **注記**: 市場規模の詳細データ（AI Governance $158億/2030年、Generative AI監査 $27億/2033年等）は Section 1.2 に記載。出典はそれぞれ異なる調査機関による推計値であり、方法論の差異に留意。

**Core Philosophy:**
> "Verify, Don't Trust" — AIシステムの監査証跡が、数学的に検証可能な形で存在することを評価する。

---

## 1. 制度の目的

### 1.1 What VAP-AT Measures

VAP-ATは以下の3つの特性を測定する：

| 特性 | 定義 | 規制整合 |
|------|------|----------|
| **Auditability** | 監査証跡が改ざん耐性を持ち、第三者が独立に検証できるか | EU AI Act Art.12/19, MiFID II RTS 25 |
| **Verifiability** | 記録の欠落がなく、観測性・スキーマ・イベント粒度が整備されているか | SEC 17a-4, GDPR Art.17 |
| **Regulatory Readiness** | 証拠が「パッケージ化」され、監査提出可能な形になっているか | EU AI Act Annex IV |

### 1.2 What VAP-AT Does NOT Do

| ❌ 範囲外 | 理由 |
|----------|------|
| AIモデルの精度評価 | スコープ外（ML性能評価は別領域） |
| ビジネスロジックの妥当性 | スコープ外（業務判断は対象外） |
| セキュリティ脆弱性診断 | スコープ外（ペネトレーションテスト等は別） |
| 「安全性の保証」 | 認証は「基準への適合」であり「100%無謬」の保証ではない |

> **重要な区別（Critical Distinction）：**
> 
> VAP-AT does not assess the correctness or legality of AI decisions, only the verifiability and auditability of the decision process.
> 
> （VAP-ATは、AI判断の正しさや合法性を評価するものではない。評価対象は、意思決定プロセスの**検証可能性**と**監査可能性**のみである。）

### 1.3 市場需要シグナル

**規制ドライバー：**

| 規制 | 要件 | 違反罰則 |
|------|------|----------|
| **EU AI Act** | 高リスクAIの自動イベント記録（Art.12）、自動生成ログの保持（Art.19）、6ヶ月以上保持 | €3,500万 or 売上7% |
| **MiFID II RTS 25** | アルゴ取引の年次自己評価、100μs時刻同期 | FCA罰金・業務停止 |
| **NYC Local Law 144** | 採用AIのバイアス監査義務化 | $500-$1,500/違反 |
| **GDPR Art.17** | 忘れられる権利（Crypto-Shredding対応） | €2,000万 or 売上4% |

> **注記（VAP-AT提供価値）：** EU AI Act Art.12/19は自動ログ記録と保持を義務付けるが、tamper-proof / tamper-evidenceを明示的に要求していない。VAP-ATは**証拠強化（evidentiary robustness）**として暗号学的改ざん証拠を提供し、ベースライン・コンプライアンスを超える防御力を実現する。

**支払意思の証拠（Willingness to Pay）：**

| 市場セグメント | 価格受容帯 | 根拠 |
|---------------|-----------|------|
| B2B SaaS（SOC 2相当） | $30,000-$100,000/年 | B2B契約の事実上の必須条件 |
| 金融機関（MiFID II対応） | $50,000-$150,000/年 | 規制違反リスク回避 |
| 政府調達（FedRAMP相当） | $250,000-$3,000,000 | 連邦契約の必須条件 |
| RegTech支出成長 | $830億→$2,000億（2023-2028） | 124%成長、規制複雑化対応 |
| AI Governance市場 | $158億（2030年） | 30% CAGR |
| コンプライアンスツール | $12億節約 | RegTech導入効果 |

**価格感度分析：**
- **小規模企業**: $5,000-$15,000 が受容可能帯
- **中規模企業**: $50,000まで「高いが許容範囲」
- **大規模企業**: $100,000超も対応可能
- **抵抗ライン**: $50,000超はROI説明が必須

---

## 2. 比較プログラム分析

### 2.1 既存プログラム比較表

既存のセキュリティ・IT監査プログラムを、運営形態・測定対象・収益モデル・中立性メカニズム・信頼性・批判の観点で比較する。

| Program | Operator Type | Scope | Revenue Model | Neutrality Mechanism | Credibility | Known Criticism |
|---------|---------------|-------|---------------|---------------------|-------------|-----------------|
| **CISSP (ISC²)** | 非営利会員団体 | 個人知識・経験（InfoSec全般） | 試験料$749、年間維持費$125、研修 | 独立試験開発、ANSI/ISO 17024認定、倫理規定 | DoD IA必須、業界広範認知 | 理論偏重、Brain Dump問題、高コスト |
| **CCSP (ISC²)** | 非営利会員団体 | 個人知識（クラウドセキュリティ） | 試験料$599、更新料 | 認定、不正行為ゼロ容認ポリシー | クラウドコンプライアンスで評価 | 試験の厳格さ、コスト |
| **CISA (ISACA)** | 非営利専門協会 | 個人知識（IT監査・統制） | 試験料$575-$760、年会費、研修 | ISACA委員会による試験開発、不正対策ポリシー | IT監査で高評価、2025 Best Certification最終候補 | 準備コストが負担 |
| **CISM (ISACA)** | 非営利専門協会 | 個人知識（セキュリティ管理） | 試験料$575-$760、更新料 | スコア検証、倫理規定 | 48,000名以上保持、平均給与$149K上昇 | 特になし |
| **Cisco CCNA** | 営利ベンダー | Cisco製品スキル | 試験料$300-$400、認定研修 | 独立テストセンター（但しベンダー管理） | ネットワーク技術で評価 | ベンダーロックイン、陳腐化が早い |
| **ISO/IEC 27001** | 標準：ISO（NGO）、認証：独立CB | 組織のISMSプロセス・統制 | 監査料$5K-$35K、サーベイランス$3K-$10K/年 | ISO→認定機関→CBの三層分離、ISO 17021準拠 | 国際的に高い信頼、EU/APAC規制で証拠として受容 | チェックボックス批判、実装コスト、官僚主義 |
| **SOC 2 (AICPA)** | 基準：AICPA、監査：CPA事務所 | 組織システム・統制（Trust Principles） | 監査料$7K-$100K、コンプライアンスツール$10K-$80K/年 | CPA免許要件、ピアレビュー、独立性ルール | B2B SaaS調達で準必須（特に米国） | 監査人解釈の一貫性欠如 |
| **FedRAMP** | 政府プログラム（GSA/PMO） | クラウドサービスセキュリティ | 総コスト$250K-$3M | 3PAO認定（ISO 17020）、JAB多層審査 | 連邦クラウドで金字塔 | 高コスト、長期遅延 |
| **BABL AI Certificate** | 営利企業 | AI risk assessment | プログラム料金 | フレームワークベース | 規制当局との早期信頼構築 | 標準化の欠如 |
| **IIA AI Auditing** | 非営利（IIA） | 個人知識（AI監査） | コース料金 | 教育ベース | 内部監査コミュニティで認知 | 実務スキル検証なし |
| **ORCAA** | 非営利 | システム監査（害悪防止） | 評価料金 | 独立フレームワーク | 新興、規制当局と連携中 | 標準化ギャップ |

### 2.2 主要な教訓

**個人資格（CISSP, CISA等）：**
- 非営利または専門協会が運営、試験料と研修で収益
- 中立性は独立した試験開発と専門化により確立
- **課題：** Brain Dump（試験問題流出）による価値低下、理論偏重

**システム監査（ISO 27001, SOC 2）：**
- 標準策定と評価実行の分離が信頼の鍵
- 第三者監査人が客観性を維持
- **課題：** 監査人が顧客に支払われる利益相反、甘い監査人への「Audit Shopping」

**高保証プログラム（FedRAMP）：**
- 政府監視 + 認定評価者で高い信頼性
- **課題：** 高コスト・長期間により中小企業が参入困難

**AI監査（新興）：**
- EU AI Actにより制度化の方向
- 現時点では断片的、統一基準なし
- **機会：** 先行して堅牢な制度を確立すれば市場リーダーになれる

---

## 3. ガバナンス構造（4レイヤ分離）

### 3.1 構造的独立性の原則

**成功する認証制度の共通点：標準策定と評価実行の分離**

> "標準策定プロセスと認証プロセスの明確な分離は、独立性と客観性を維持する上で極めて重要な資産である" — GOTS（Global Organic Textile Standard）

研究に基づく失敗原因分析：

| 失敗事例 | 原因 | 教訓 |
|----------|------|------|
| **信用格付機関（2008年金融危機）** | 発行者負担モデルによる利益相反 | 支払者と評価対象の分離 |
| **TRUSTe（FTC制裁）** | 自己監視モデル、外部監視なし | 独立した外部監視が必須 |
| **Boeing 737 MAX（FAA認証問題）** | 認証権限の過度な委任 | 適切な監督維持 |
| **FSC/RSPO（環境認証）** | 認証機関の被認証者への財務依存 | 収益分散要件 |
| **ISO Certificate Mills** | 価格競争による品質劣化 | 最低品質基準と監査 |
| **Safe Harbor / Privacy Shield** | 規制要件との不整合 | 規制当局との継続的整合 |
| **VW Emissions Scandal** | テスト体制の欺瞞脆弱性 | 実環境検証の重要性 |
| **CEH（EC-Council）** | 試験の予測可能性、「Pay-to-Pass」認識 | 試験の完全性維持 |
| **CMMC 1.0** | 過度な複雑性で中小企業排除 | 段階的・比例的設計 |
| **Texas Teacher Certifications** | 代理受験（proxy cheating）で200名以上の不適格教師 | 試験監督の厳格化、本人確認 |
| **U.S. Job Corps** | $17億プログラムが低い成果で失敗 | アウトカム測定、政府過度依存の回避 |

**失敗パターン分析：**

| 失敗事例 | 問題の本質 | シグナル | 回避策 |
|----------|-----------|----------|--------|
| **Texas Teacher Certs** | 代理受験（Proxy cheating） | 高い不合格→合格パターン | 厳格な試験監督 |
| **U.S. Job Corps** | 非効果的な訓練 | 低い成果指標 | 政府過度依存の回避 |

### 3.2 5つの組織モデル比較

| モデル | 標準策定 | 評価資格 | 評価実行 | 監督 | 事例 | 利益相反回避策 |
|--------|----------|---------|----------|------|------|---------------|
| **非営利標準策定 + 独立CAB** | NGO（ISO等） | 認定機関がCB認定 | 独立認定CB | 国家認定機関 | ISO 27001, PCAF | 独立監査人 |
| **非営利 + 商業子会社** | 非営利本体 | 子会社が研修 | 本体が認定 | 内部ファイアウォール | ISC² | 収益ストリーム分離 |
| **コンソーシアム + ライセンス評価者** | 業界団体 | 団体が認定 | 認定QSA | 団体がQAチェック | PCI DSS | 開示ポリシー |
| **政府主導 + 認定民間監査人** | 政府機関 | 認定（ISO 17020） | 認定3PAO | 政府PMO審査 | FedRAMP | 多層審査 |
| **ライセンス評価方法論** | 中央組織 | 個人認定 | ライセンス評価者 | 中央QA | CMMI | 開示要件 |

**VAP-ATの選択：** 「非営利標準策定 + 独立CAB」をベースに、「コンソーシアム + ライセンス評価者」の品質管理要素と「非営利 + 商業子会社」の収益分離モデルを組み合わせる。

### 3.3 VAP-AT 4レイヤ構造（二段階認定モデル）

```
┌─────────────────────────────────────────────────────────────────┐
│  Layer 0: 国家認定機関（National Accreditation Bodies）          │
│  ─────────────────────────────────────────────────               │
│  ・CABをISO/IEC 17020/17021/17065等に沿って認定（ISO認定）       │
│  ・国際相互承認（IAF MLA）により認証のグローバル受容を実現       │
│  ・例：UKAS (UK), DAkkS (DE), ANAB (US), JAB (JP)               │
│  ・Phase 2以降で必須化                                          │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ ISO Accreditation (Phase 2+)
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 1: 標準策定 / スキームオーナー（VSO）                     │
│  ─────────────────────────────────────────                       │
│  ・VAP-ATの基準（スコア基準・証拠要件・用語・レポート仕様）を管理 │
│  ・審査業務は行わない（利益相反回避）                            │
│  ・CABの「スキーム認定」（VSO Accredited CAB）を行う             │
│  ・収益源：CAB認定料、会員費、規格文書販売、研修ライセンス       │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ Scheme Accreditation (Phase 1+)
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 2: 諮問委員会（Advisory Board）                           │
│  ─────────────────────────────────────────                       │
│  ・技術諮問・規制動向監視・利益相反チェック                      │
│  ・規制当局オブザーバー席設置                                    │
│  ・認定基準の改訂提案                                            │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ Oversight
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 3: 評価実行（Conformity Assessment Body / CAB）           │
│  ─────────────────────────────────────────────────               │
│  ・複数の独立CABがVAP-ATを実施しスコアレポート発行               │
│  ・被評価者へのコンサル禁止等の独立性ルール必須                   │
│  ・認証料はCABの収益（VSOは徴収しない）                          │
│  ・競争市場により価格・品質が最適化                               │
└─────────────────────────────────────────────────────────────────┘
                                │
                                │ Assessment
                                ▼
┌─────────────────────────────────────────────────────────────────┐
│  Layer 4: 商用イネーブル（Enablers）                             │
│  ─────────────────────────────                                   │
│  ・ツール、教育、準備支援                                        │
│  ・評価（Assessment）とは切り離す                                │
│  ・「標準団体が合否を売る」状態を作らない                        │
│  ・VSOの営利子会社または認定パートナーが提供                     │
└─────────────────────────────────────────────────────────────────┘
```

**二段階認定モデル（Dual Accreditation）の明確化：**

| 認定タイプ | 認定主体 | 対象 | 目的 | フェーズ |
|-----------|---------|------|------|---------|
| **Scheme Accreditation** | VSO | CAB | VAP-ATスキーム固有の評価能力・品質管理を認定 | Phase 1〜 |
| **ISO Accreditation** | 国家認定機関 | CAB | ISO/IEC 17065等の国際規格適合を認定 | Phase 2〜 |

**フェーズ別展開：**
- **Phase 1（Launch）**: VSO Scheme Accreditationのみで開始（迅速な市場投入）
- **Phase 2（Maturity）**: ISO Accreditation取得CABを優先的に認定（制度的信頼性強化）
- **Phase 3（Scale）**: ISO Accreditation必須化 + Mutual Recognition Agreement（MRA）

### 3.4 VSOの役割（Scheme Owner）

| 責務 | 内容 |
|------|------|
| 基準策定 | VAP-AT Scoring Criteria, Evidence Requirements |
| CAB認定 | 認定審査・維持・監査（年次サーベイランス） |
| ルールブック | VAP-AT Scheme Rulebook の管理 |
| 紛争解決 | 評価に関する異議申立ての最終判断 |
| 公平性委員会 | 外部利害関係者を含む委員会設置（ISO 17021準拠） |
| 品質保証 | CABの評価レポートの抜き打ちレビュー（PCI QSAモデル） |

| 行わないこと | 理由 |
|--------------|------|
| 評価の実施 | CABの役割。利益相反回避 |
| 評価料の徴収 | CABの収益 |
| コンサルティング | 営利事業は別法人で（BSIモデル準拠） |

### 3.5 CABの要件（ISO/IEC 17065準拠）

| カテゴリ | 要件 | 根拠 |
|----------|------|------|
| **独立性** | 評価対象企業との資本関係がないこと | ISO 17021 |
| **コンサル禁止** | 同一組織が評価とコンサルを兼ねない（2年ルール） | EU AI Act Notified Body要件 |
| **専門性** | 暗号技術・監査の専門家を擁すること | 技術的適格性 |
| **保険** | 専門職業賠償責任保険（$1-5M以上） | SOC 2モデル準拠 |
| **監督** | VSOによる年次監査を受け入れること | 品質維持 |
| **収益分散** | 単一顧客からの収益10%以下 | 財務的独立性 |
| **レポート審査** | 抜き打ちで評価レポートのVSOレビューを受け入れ | 品質一貫性 |

**CABローテーション・ルール（Rotation Policy）：**

| ルール | 制限 | 根拠 |
|--------|------|------|
| **同一CAB連続評価** | 最大3年 | Wirecard/Enron型の関係性腐敗リスク回避 |
| **主要評価責任者（Lead Assessor）** | 2年でローテーション | 個人レベルの馴れ合い防止 |
| **CAB変更後の復帰** | 最低2年間のクーリングオフ | 形式的ローテーション防止 |

> **運用原則**: 被評価者は、同一CABによる連続評価が3年目に達した場合、次回評価で別のVSO認定CABを選定しなければならない。主要評価責任者は、同一被評価者に対して最大2年間のみ担当可能。

### 3.6 参照モデル比較

| モデル | 標準策定 | 評価者資格 | 評価実行 | 執行 |
|--------|----------|-----------|----------|------|
| **PCI-DSS** | PCI SSC | QSA資格 | 独立QSA | 決済ブランド |
| **ISO 27001** | ISO TC27 | CB認定 | 認定CB | 市場 |
| **FedRAMP** | NIST/PMO | 3PAO認定 | 独立3PAO | 連邦機関 |
| **SOC 2** | AICPA | CPA免許 | CPA事務所 | 市場 |
| **VAP-AT** | VSO | CAB認定 | 認定CAB | 規制当局/市場 |

---

## 4. 評価形態（3レベル構成）

CSA STAR、シンガポールCLS、米国CMMCを参考に、**Self → Third-party → Continuous**の三段構成を採用する。

### 4.1 Level 1: VAP-AT Self（自己評価）

**対象：低リスクAI（推薦エンジン、社内効率化ツール）**

| 項目 | 内容 |
|------|------|
| **目的** | 導入企業がギャップ把握・準備を行う |
| **実施者** | 被評価組織自身（VAP Scorecard Explorer使用） |
| **成果物** | Evidence Pack (Preliminary) |
| **価格帯** | 無償〜$5,000（ツール/テンプレ提供で普及促進） |
| **有効期間** | なし（自己宣言） |
| **ステータス** | `assessment_status: "Self-Assessment"` |
| **検証主体** | 自動スキャンツール + 自己申告 |

### 4.2 Level 2: VAP-AT Verified（第三者評価）

**対象：中リスク・汎用業務AI（HR Tech、金融審査支援）**

| 項目 | 内容 |
|------|------|
| **目的** | 調達・顧客監査・規制当局対応の「提出物」として成立 |
| **実施者** | VSO認定CAB |
| **成果物** | CAB署名付きScore Report + Evidence Pack (Verified) |
| **価格帯** | $15,000 – $150,000（組織規模・複雑性に応じる） |
| **有効期間** | 1年間（更新審査必要） |
| **ステータス** | `assessment_status: "Verified by [CAB Name]"` |
| **検証主体** | 認定CAB |

**Type I / Type II 区分（SOC 2モデル）：**

| 区分 | 内容 | 用途 |
|------|------|------|
| **Type I（時点監査）** | 特定日時点での設計の適切性を評価 | 初期導入、モデル開発段階 |
| **Type II（期間監査）** | 6-12ヶ月の運用実績を検証 | 継続運用、規制対応 |

### 4.3 Level 3: VAP-AT Continuous（継続モニタリング）

**対象：高リスクAI（医療診断、自動運転、重要インフラ制御）**

| 項目 | 内容 |
|------|------|
| **目的** | AIが更新・学習・設定変更される環境で「評価が古くなる問題」を解決 |
| **実施者** | VSO認定CAB + 自動化ツール + 抜き打ち検証 |
| **成果物** | 月次/四半期のDelta Report、Performance Dashboard |
| **価格帯** | 年額サブスク（初回評価の20〜50%が目安） |
| **有効期間** | サブスク継続中（自動更新） |
| **ステータス** | `assessment_status: "Continuous Monitoring Active"` |
| **特徴** | 性能指標が閾値を下回った場合、運用ステータスが自動的に「保留」 |

**Assessment Status 定義（Operational Status Definitions）：**

| Status | 定義 | トリガー | 復帰条件 |
|--------|------|---------|---------|
| **Active** | 有効な評価状態 | 評価完了・閾値到達、サブスク継続中 | - |
| **Suspended** | 一時停止（問題発生） | 閾値を下回る、重大なログ欠落、不正検知 | 是正措置完了 + 再評価でスコア回復 |
| **Pending Review** | 審査待ち | 抜き打ち検証でのフラグ、苦情申立 | VSO/CAB審査完了 |
| **Expired** | 期限切れ | 有効期間終了、サブスク解約 | 新規評価の実施 |

> **自動停止メカニズム**: Continuousモニタリング中に閾値を下回った場合、24時間以内に被評価者に通知し、30日以内に是正されない場合は自動的に`Suspended`へ移行。公開レジストリのステータスも即時更新。

### 4.4 レベル選択ガイドライン

| リスクレベル | 例 | 推奨レベル | コスト感 |
|-------------|-----|-----------|----------|
| **低リスク** | 社内チャットボット、推薦エンジン | Level 1 (Self) | $0-$5,000 |
| **中リスク** | 採用AI、与信審査、顧客対応AI | Level 2 (Verified) | $15,000-$60,000 |
| **高リスク** | 医療診断、自動運転、重要インフラ | Level 3 (Continuous) | $100,000+ |

---

## 5. スコアリング基準

### 5.1 スコア体系

VAP Scorecard と整合し、**10項目 × 0–2点 = 最大20点**を採用する。

| Score | Meaning | 色 |
|-------|---------|-----|
| **0** | 未実装または根本的に不十分 | 🔴 Red |
| **1** | 部分的に実装、ギャップあり | 🟡 Yellow |
| **2** | 完全実装、必要なOutcomeを達成 | 🟢 Green |

### 5.2 グレード閾値

| Score Range | Grade | Interpretation |
|-------------|-------|----------------|
| 16–20 | **Strong** | 堅牢な監査可能性を実証 |
| 11–15 | **Moderate** | 監査可能だが改善余地あり |
| 6–10 | **Limited** | 重大な監査可能性の欠陥 |
| 0–5 | **Inadequate** | 監査可能性が根本的に不十分 |

> **Note:** グレードは「ラベル」ではなく「状態の説明」として扱う。規制当局に「お墨付き」と誤認させない。

### 5.3 評価基準（10 Criteria）

| # | Criterion | Key Question | 規制マッピング |
|---|-----------|--------------|---------------|
| 1 | **Third-Party Verifiability** | 外部者が独立して監査証跡を検証できるか？ | EU AI Act Art.12/19, MiFID II |
| 2 | **Tamper Evidence** | 不正な変更を検知できるか？ | SEC 17a-4 |
| 3 | **Sequence Fixation** | 時系列順序が不変に記録されているか？ | MiFID II RTS 25 |
| 4 | **Decision Provenance** | 意思決定の入力と根拠を追跡できるか？ | EU AI Act Art.12 |
| 5 | **Responsibility Boundaries** | 各アクションの承認者・オーバーライド者が明確か？ | EU AI Act Art.14 |
| 6 | **Documentation Completeness** | 技術文書が完備され最新か？ | EU AI Act Annex IV |
| 7 | **Retention & Availability** | 規制が求める期間、証拠が保持・取得可能か？ | EU AI Act Art.19, GDPR, MiFID II |
| 8 | **Time Synchronization** | システム時刻が信頼できるソースと同期されているか？ | MiFID II RTS 25 |
| 9 | **Failure & Recovery Logging** | システム障害と復旧が記録されているか？ | DORA |
| 10 | **Right to Erasure Compatibility** | GDPR等の削除権をサポートしつつ監査可能性を維持できるか？ | GDPR Art.17 |

### 5.4 ハイブリッドモデル（スコア + 任意閾値ラベル）

**課題：** 市場はバイナリ認証（Pass/Fail）に慣れている vs スコア制の方が情報量が多い

**解決策：** スコアを一次成果物とし、閾値ラベルを任意の解釈レイヤとして提供

| 成果物 | 内容 | 用途 |
|--------|------|------|
| **Assessment Score** | 0–20点の詳細評価結果 | 改善計画策定、リスク評価 |
| **Threshold Designation** | スコア閾値に基づくラベル（任意の解釈レイヤ） | 調達要件、規制報告での参照 |

**Threshold Designation例：**
- "VAP-AT Auditability Threshold – EU AI Act Art.12/19 aligned" (Score 16+)
- "VAP-AT Auditability Threshold – MiFID II RTS 25 aligned" (Score 14+)
- "VAP-AT Baseline Auditability Threshold" (Score 11+)

> **重要な免責事項（Critical Disclaimer）：**
> 
> Threshold Designationは**VAP-ATスキーム内の便宜的分類（interpretive label）**であり、**法的コンプライアンスの保証ではない**。
> - "EU AI Act Art.12/19 aligned" は「当該条文が求める監査可能性水準に整合するVAP-ATスコア」を示す
> - 法的コンプライアンスの判断は被評価者自身の責任であり、最終的には規制当局の解釈に依拠する
> - CABは法的助言を提供せず、Score Reportには必ずこの免責事項を記載すること

**UL IoT Security Ratingモデル参照：**
ULのIoTセキュリティレーティングは、Bronze→Silver→Gold→Platinum→Diamondの5段階でセキュリティ統制の強度を示す。これにより消費者に詳細な情報を提供しつつ、製造者には上位レベルへのインセンティブを与えている。

### 5.5 スコアベース vs バイナリ認証 の戦略分析

| 観点 | スコアベース | バイナリ認証（Pass/Fail） | VAP-ATハイブリッド |
|------|-------------|-------------------------|-------------------|
| **情報量** | 高い（粒度詳細） | 低い（二値） | 高い + 任意の閾値ラベル |
| **改善インセンティブ** | 高い（上位スコア目指す） | 低い（最低ライン超えればOK） | 高い |
| **規制受容性** | やや低い（解釈必要） | 高い（明確） | 高い（閾値ラベル提供） |
| **市場理解** | やや低い（教育必要） | 高い（シンプル） | 中〜高 |
| **リスク評価活用** | 高い（保険料算定等） | 低い | 高い |
| **金融セクター適合** | データトレイルで信頼構築可能 | 規制上はバイナリ優先 | 両立可能 |

**重要な洞察（外部調査より）：**

> "スコアベースの評価は、データトレイルを通じてきめ細かな信頼を構築できるが、金融など二値規制が支配的なセクターでは、バイナリ認証に比べて採用が遅れる可能性がある。"

**VAP-ATの戦略的対応：**
- **規制セクター向け**: Threshold Designation（閾値ラベル）を提供し、調達・報告での利便性を確保
- **保険・リスク評価向け**: 詳細スコアを提供し、リスクベースの意思決定を支援
- **自主的改善向け**: 段階的スコアアップのロードマップを提示

---

## 6. 価格ベンチマーク

### 6.1 比較プログラム価格一覧

**個人資格（Individual Certifications）：**

| 資格 | 試験料 | 年間維持費 | 研修（任意） | 備考 |
|------|--------|-----------|-------------|------|
| **CISSP (ISC²)** | $749 | $125 | $1,000-$3,000 | ANSI/ISO 17024認定 |
| **CISA (ISACA)** | ~$575（会員） | ~$100 | $1,000+ | IT監査標準 |
| **CCNA (Cisco)** | $300+ | N/A（3年有効） | $500-$2,000 | ベンダー認定 |
| **GIAC (SANS)** | $1,000+ | $469/4年 | $5,000+ | 高度なセキュリティ |

**システム監査（Organizational Audits）：**

| プログラム | 初回監査 | 年次サーベイランス | 準備コスト | 総初年度コスト（SME） |
|-----------|---------|-------------------|-----------|---------------------|
| **ISO/IEC 27001** | $5,000-$35,000 | $3,000-$10,000/年 | $5,000-$75,000 | ~$20,000-$50,000 |
| **SOC 2 Type I** | $10,000-$20,000 | — | $5,000-$15,000 | ~$15,000-$35,000 |
| **SOC 2 Type II** | $20,000-$50,000+ | （年次） | $5,000-$15,000 | ~$25,000-$65,000 |

**高保証プログラム（High-Assurance）：**

| プログラム | 総コスト | 期間 | 内訳 |
|-----------|---------|------|------|
| **FedRAMP Moderate** | $800,000-$2,000,000 | 18-24ヶ月 | 3PAO $150K-$400K、コンサル $200K-$500K、ツール・工数 残り |
| **HITRUST CSF** | $50,000-$200,000+ | 6-12ヶ月 | 評価 + 認証料 |

**コンプライアンス自動化ツール：**

| ツール | 価格帯（年額） | 対象 |
|--------|--------------|------|
| **Vanta** | ~$10,000（基本） | スタートアップ・SME |
| **Drata** | $10,000-$50,000 | SME〜Mid-size |
| **Secureframe** | $5,000-$30,000 | スタートアップ〜Mid-size |
| **大企業向け** | $75,000-$100,000 | 複数フレームワーク |

### 6.2 VAP-AT価格帯設計

| Tier | Target | Initial Assessment | Annual Renewal | 備考 |
|------|--------|-------------------|----------------|------|
| **Bronze** | Startup / SME | $5,000 – $20,000 | $2,000 – $8,000 | Level 1-2対応 |
| **Silver** | Mid-size Enterprise | $15,000 – $50,000 | $5,000 – $15,000 | Level 2対応 |
| **Gold** | Large Enterprise / HFT | $50,000 – $150,000 | $15,000 – $40,000 | Level 2-3対応 |
| **Platinum** | Critical Infrastructure | $100,000 – $300,000 | $30,000 – $100,000 | Level 3対応 |

**Price Drivers:**
- システムの複雑性（単一システム vs 分散システム）
- データボリューム（イベント数/日）
- 規制要件の厳格度（MiFID II, EU AI Act等）
- 評価スコープ（単一環境 vs マルチリージョン）
- Assessment Type（Type I vs Type II）

### 6.3 継続モニタリング（Continuous）

| Model | Price | Coverage |
|-------|-------|----------|
| Annual Subscription | Initial × 20–50% | 月次レポート + 四半期検証 |
| Per-Check | $1,000 – $5,000 | 抜き打ち検証1回 |

### 6.4 収益配分

| Recipient | Revenue Source | 備考 |
|-----------|----------------|------|
| **VSO** | CAB認定料、会員費、規格文書販売、研修ライセンス | 年間$29,000/CAB（PCI SSC参考） |
| **CAB** | 評価料（Assessment Fee） | 主要収益源 |
| **Tool Vendors** | ツール/テンプレート販売（Layer 4） | 任意パートナー |

> **Critical:** VSOは評価料を直接徴収しない。これにより「Pay-to-Pass」疑惑を構造的に回避する。

### 6.5 価格設計原則

| 原則 | 内容 | 根拠 |
|------|------|------|
| **最低価格閾値** | $5,000以上 | $5,000未満は信頼性を損なう |
| **品質競争** | 価格競争ではなく品質競争を促進 | Certificate Mills防止 |
| **収益分散** | CABの単一顧客依存を防止 | 独立性維持 |
| **スケーラビリティ** | 組織規模に応じた価格設定 | 中小企業の参入促進 |

### 6.6 ROI分析

企業にとってのVAP-AT投資対効果：

| コスト項目 | 金額 | 回避リスク |
|-----------|------|-----------|
| VAP-AT評価（Mid-size） | $30,000-$60,000 | EU AI Act罰則€3,500万回避 |
| コンプライアンスツール | $10,000-$30,000/年 | 手動準備工数削減 |
| 継続モニタリング | $6,000-$30,000/年 | インシデント発生時の証拠確保 |

> **投資対効果：** 数十万ドルの投資で、数百万〜数千万ユーロの罰則リスクを回避

---

## 7. 監査人資格制度（Certified AI Systems Assessor）

### 7.1 概要

VAP-ATの品質を担保するため、評価を実施する個人の資格制度を併設する（CISSP/ISACAモデル）。

**目的：**
- 監査を実施する有資格者プールの確保
- 評価品質の標準化
- 継続教育による最新技術対応
- 会費収入による規格開発コスト補填

### 7.2 資格体系

| 資格 | 要件 | 権限 |
|------|------|------|
| **VAP-AT Associate (VAP-ATA)** | 試験合格 + 1年経験 | Level 1評価補助 |
| **VAP-AT Professional (VAP-ATP)** | 試験合格 + 3年経験 + 3件評価実績 | Level 1-2評価実施 |
| **VAP-AT Expert (VAP-ATE)** | 上級試験合格 + 5年経験 + 10件評価実績 | Level 3評価実施、CAB技術責任者 |

### 7.3 料金体系

| 項目 | 料金 | 備考 |
|------|------|------|
| 試験料 | $600-$800 | CISA/CISM参考 |
| 年間維持費（AMF） | $85-$135 | ISC2/ISACA参考 |
| 継続教育（CPE） | 20時間/年、120時間/3年 | 資格維持要件 |

### 7.4 試験の完全性（Integrity）

**Brain Dump対策：**
- 定期的な試験問題プールの更新
- 実技要素の導入（シナリオベース評価）
- 不正受験の監視・取消制度
- 試験問題の秘匿性維持

> **教訓：** CEHやCISSP等で見られたBrain Dump問題により、資格の価値が毀損された事例がある。試験の完全性維持は資格制度の生命線。

### 7.5 継続教育（CPE）エコシステム

**CPE取得機会：**
- VSO公式研修プログラム
- 認定パートナーによる研修
- カンファレンス参加
- 技術論文執筆
- オープンソースプロジェクト貢献

---

## 8. 成功原則とレッドフラグ

### 8.1 成功原則（Principles for Success）

| 原則 | 内容 | 具体策 |
|------|------|--------|
| **1. 独立した認定（Independent Accreditation）** | 評価者と被評価者の構造的分離 | 4レイヤ分離、コンサル禁止、収益分散要件 |
| **2. 透明な収益（Transparent Revenue）** | 収益モデルと料金構造の公開 | 料金表公開、CAB認定料開示 |
| **3. 規制整合（Regulatory Alignment）** | 現行・将来の規制要件への対応 | EU AI Act、MiFID II、SEC 17a-4マッピング |
| **4. エコシステムパートナーシップ（Ecosystem Partnerships）** | 保険・監査法人・ツールベンダーとの連携 | Munich Re連携、Big Four協力 |
| **5. 不正対策ポリシー（Fraud Policies）** | 試験・評価における不正防止 | 本人確認、抜き打ち監査、ゼロ容認ポリシー |
| **6. 明確で透明な基準** | 測定対象と方法論の公開 | 公開スコア基準、方法論文書、ガイドライン |
| **7. 実証された価値（有効性）** | 成果による信頼構築 | インシデント追跡、採用企業のコンプライアンス成績 |

### 8.2 レッドフラグ（Failure Triggers）

| レッドフラグ | 症状 | 対策 |
|-------------|------|------|
| **1. 未検証の成果物（Unverified Outputs）** | 評価結果の第三者検証なし | 抜き打ちレビュー、クロスチェック |
| **2. 価値なき高コスト（High Costs without Value）** | ROIが不明確なまま高額請求 | 価格帯の透明化、成功事例の公開 |
| **3. ベンダーロックイン（Vendor Lock-in）** | 特定ベンダーへの依存 | オープン標準、複数CAB体制 |
| **4. 監督ギャップ（Oversight Gaps）** | CAB品質管理の欠如 | 年次監査、認定取消制度 |
| **5. Pay-to-Passモデル** | 「金で通る」認識 | VSO評価禁止、収益構造監視 |
| **利益相反・商業的搾取** | 100%合格率 | 合格率公開 |
| **説明責任・執行の欠如** | 違反しても認証維持 | 自動停止メカニズム、公開取消リスト |
| **不透明または過度に複雑な制度** | 「官僚主義」「書類だけ」批判 | 10項目シンプル設計、継続的簡素化 |
| **ネガティブな市場フィードバック** | 主要ステークホルダーからの批判 | フィードバックループ、迅速な改善 |
| **規制進化との不整合** | 規制要件を満たさない | 規制当局との継続的対話、柔軟な更新 |

---

## 9. 保険業界との連携

### 9.1 市場機会

**現状：**
- BerkleyやHamiltonは「絶対的AI免責条項」を導入
- 一方でMunich Re「aiSure」やCoalitionはAIリスクをカバー
- AI保険プレミアムは2032年までに$48億に成長予測

**VAP-ATの価値提案：**
- VAP-AT評価結果を保険引受審査の「代行」として機能させる
- 評価スコアに基づく保険料割引（10-15%）
- 高スコア企業のみがAI保険に加入可能なエコシステム

### 9.2 想定スキーム

```
┌─────────────────────────────────────────────────────────────┐
│  AI保険会社（Munich Re, Coalition等）                        │
│  ─────────────────────────────────────                       │
│  ・VAP-AT評価結果を引受審査に活用                            │
│  ・Strong評価企業に保険料10-15%割引                          │
│  ・継続モニタリング契約を引受条件に                          │
└─────────────────────────────────────────────────────────────┘
                              │
                              │ 引受審査
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  VAP-AT評価済み企業                                          │
│  ─────────────────                                           │
│  ・Score Report提出                                          │
│  ・Evidence Pack提出（必要に応じて）                         │
│  ・継続モニタリングステータス維持                            │
└─────────────────────────────────────────────────────────────┘
```

---

## 10. 失敗回避（Anti-Patterns）

### 10.1 絶対に踏んではならないパターン

| パターン | 症状 | 対策 | 事例 |
|----------|------|------|------|
| **Pay-to-Pass** | 「金で通る」と認識される | VSO評価禁止、CAB独立性、複数CAB体制 | EC-Council批判 |
| **標準団体が評価を売る** | 利益相反発生 | 4レイヤ分離厳守 | FSC/RSPO失敗 |
| **Certificate Mills** | 形だけの認証 | CAB年次監査、認定取消、Public Registry | ISO Mills問題 |
| **ラバースタンプ化** | 更新審査の形骸化 | Continuous Monitoring、有効期間1年 | TRUSTe（FTC制裁） |
| **過度な複雑化** | チェックリスト化、中小排除 | 10項目×3段階のシンプル設計 | CMMC 1.0の失敗 |
| **Audit Shopping** | 甘いCAB探し | VSO監視、通報制度、Public Registry比較 | 環境認証失敗 |
| **顧問と監査の兼務** | 独立性喪失 | 同一組織での兼務禁止（2年ルール） | Arthur Andersen |
| **被監査者への財務依存** | 忖度圧力 | 収益分散要件（単一顧客10%以下） | 信用格付機関 |
| **規制との不整合** | 法的無効化 | 規制当局との継続的対話 | Safe Harbor/Privacy Shield |
| **試験の完全性喪失** | Brain Dump、不正受験 | 定期更新、監視、取消制度 | CEH批判 |

### 10.2 失敗シグナル（早期警告）

| シグナル | 説明 | 対応 |
|----------|------|------|
| 経済的利益相反 | 評価者収益が顧客満足度に依存 | 収益構造の見直し |
| 構造的依存 | 標準策定者が被評価者に財務依存 | 分離強化 |
| 透明性欠如 | 評価基準が不透明または恣意的 | 公開・説明責任強化 |
| 結果なき違反 | 違反しても認証維持 | 自動的な認証停止メカニズム |
| チェックボックス思考 | 文書重視、実際の挙動軽視 | Outcome-based評価への移行 |
| 規制・市場からの拒絶 | 調達で排除、NGO批判 | 根本的な制度見直し |
| 主要参加者の離脱 | 大手企業が認証を拒否 | 原因分析と迅速な改善 |
| メディア批判 | 「形骸化」「無意味」報道 | 透明性強化、実績公開 |

---

## 11. 規制接続（Regulatory Alignment）

### 11.1 EU AI Act整合

| EU AI Act条項 | VAP-AT対応 | 評価基準 |
|--------------|-----------|----------|
| **Art.12（ロギング）** | 自動イベント記録、保持期間 | Criterion 3, 4, 7 |
| **Art.14（人間監視）** | オーバーライド記録 | Criterion 5 |
| **Art.17（品質管理）** | 継続的監視 | Level 3 (Continuous) |
| **Art.19（改ざん耐性ログ）** | Tamper-proof audit trails | Criterion 2 |
| **Annex IV（文書化）** | Evidence Pack | Criterion 6 |

**Notified Body Pathway：**
- Article 31要件（独立性、能力、賠償責任保険）をCAB認定基準に反映
- ISO/IEC 17065認定をCAB要件に
- Member State指定当局への申請（2025年8月まで）

### 11.2 金融規制整合

| 規制 | 要件 | VAP-AT対応 |
|------|------|-----------|
| **MiFID II RTS 25** | アルゴ取引監査証跡、100μs時刻同期 | Criterion 3, 8 |
| **SEC 17a-4** | 電子記録保持、WORM要件 | Criterion 2, 7 |
| **DORA** | ICTリスク管理、レジリエンス | Criterion 9, 10 |

### 11.3 規制タイムライン

| 日付 | イベント | VAP-AT対応 |
|------|----------|-----------|
| **2025年2月2日** | EU AI Act禁止AI施行 | 啓発活動 |
| **2025年8月2日** | GPAI・ガバナンス施行、Notified Body指定開始 | CAB認定申請準備 |
| **2026年8月2日** | 高リスクAI大部分施行 | Level 2/3本格展開 |
| **2027年8月2日** | 組み込み高リスクAI施行 | 評価スコープ拡大 |
| **2030年8月2日** | 公的機関コンプライアンス期限 | 公共セクター展開 |

---

## 12. 成果物仕様

### 12.1 4点セット

| 成果物 | 形式 | 内容 | 配布 |
|--------|------|------|------|
| **Score Report** | PDF | Assessment ID、Assessment Score（0-20）、グレード、Threshold Designation（任意ラベル）、改善推奨、免責事項 | 被評価者 |
| **Machine-Readable Score** | JSON | 構造化データ、API連携対応 | システム連携 |
| **Evidence Pack** | ZIP | checksums.sha256、ログサンプル、設定ダンプ、テストレポート | CAB保管 |
| **Public Registry Entry** | Web | 企業名、グレード、有効期限、CAB名（任意公開） | 公開（CSA STARモデル） |

**Public Registry 公開粒度定義（Disclosure Granularity Matrix）：**

| 情報 | Public（一般公開） | NDA Viewers（契約者） | Assessed & Regulators（被評価者・規制当局） |
|------|-------------------|---------------------|-------------------------------------------|
| **評価実施有無** | ○ | ○ | ○ |
| **スコア帯（Strong等）** | ○ | ○ | ○ |
| **詳細スコア（0-20）** | — | ○ | ○ |
| **Evidence Pack** | — | — | ○ |

> **凡例**: ○=当該閲覧者に提供される情報、—=提供されない情報

**公開レベルの選択権：**
- 被評価者は評価申請時に公開レベル（Public / Semi-public / Private）を選択
- デフォルトは**Semi-public**（評価実施+グレードのみ一般公開）
- **Private**を選択した場合：一般公開はしないが、被評価者自身・規制当局・被評価者が指定した監査先には開示可能。評価実施の事実のみはPublic Registryに記載（完全非公開は不可）
- 公開レベルの変更は年1回まで可能（上方向への変更のみ即時反映）

**Evidence Pack 最小必須項目（Minimum Required Set）：**

```
evidence_pack_v1.zip
├── checksums.sha256      [REQUIRED] 全ファイルのハッシュ値
├── score.json            [REQUIRED] 構造化スコアデータ
├── report.pdf            [REQUIRED] 署名済みScore Report
├── evidence_index.json   [REQUIRED] 証拠ファイル一覧と参照
└── sample_logs/          [OPTIONAL] ログサンプル（被評価者許可時）
    ├── decision_log_sample.jsonl
    └── execution_log_sample.jsonl
```

> **運用原則**: 必須4ファイルのみでEvidence Packは完結する。sample_logsはオプションであり、被評価者の書面同意がある場合のみ含める。CABは追加ファイルを含めてもよいが、必須セットの欠落は認められない。

### 12.2 Score Report構成

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

## 13. ロードマップ

### Phase 0: Foundation（2025 Q4）
- [ ] VAP-AT Program Charter 確定
- [ ] Scoring Criteria v1.0 公開
- [ ] Evidence Pack Template 公開
- [ ] Self-Assessment Tool（VAP Scorecard Explorer）公開
- [ ] CAB認定基準（VSO-CAB-REQ-001）策定

### Phase 1: Pilot（2026 Q1–Q2）
- [ ] Pilot CAB #1（VeritasChain株式会社）認定
- [ ] Pilot Assessment 3–5件実施
- [ ] フィードバック収集・改善
- [ ] VAP-AT Associate資格プログラム開始
- [ ] ISO/IEC 17065認定準備（DAkkS, UKAS）

**Pilot CAB独立性ガードレール（Impartiality Safeguards for Pilot Phase）：**

Pilot CAB #1（VeritasChain株式会社）はVSOと法人として関連するため、以下の追加ガードレールを必須とする：

| ガードレール | 内容 |
|-------------|------|
| **独立CABクロスチェック** | Pilot期間中のすべての評価レポートは、VSOが指定する独立した第三者CAB（または外部監査人）による二重レビューを受ける |
| **Impartiality Committee外部過半** | Pilot CABの公平性委員会は、外部委員が過半数を占める構成とする |
| **VSO抜き打ち審査** | Pilot CAB発行レポートの20%以上について、VSOが無作為に抜き打ち審査を実施 |
| **利益相反開示** | 被評価者に対し、Pilot CABとVSOの関係を評価開始前に書面で開示 |
| **Phase 2移行条件** | 独立CABが2社以上認定されるまで、Pilot CABの単独運用は継続しない |

> **設計意図**: 制度立ち上げ期において関連法人がPilot CABを務めることは、迅速な制度検証のために合理的である。ただし、外部からの「実質同体」疑念を先回りして払拭するため、通常CABよりも厳格な独立性保証措置を適用する。

### Phase 2: Launch（2026 Q3–Q4）
- [ ] VAP-AT Verified 正式開始
- [ ] Public Registry 開始
- [ ] 追加CAB認定（2–3社）
- [ ] EU AI Act Notified Body申請
- [ ] 保険会社連携パイロット

### Phase 3: Scale（2027+）
- [ ] Continuous Monitoring 開始
- [ ] 国際CAB認定（欧州・北米・アジア）
- [ ] IAF MLA参加検討
- [ ] 保険引受条件としての採用拡大
- [ ] AI Auditor資格の国際展開

---

## 14. 関連文書

| Document ID | Title |
|-------------|-------|
| VSO-BENCHMARK-SCORE-001 | VAP Scorecard Scoring Criteria v2.0 |
| VSO-VAP-SPEC-001 | VAP Framework Specification v1.1 |
| VSO-GOV-SCHEME-001 | VC-Certified Scheme Governance v1.0 |
| VSO-SPEC-001 | VCP Specification v1.0 |
| VSO-EXPLORER-001 | VAP Scorecard Explorer Reference |
| VSO-CAB-REQ-001 | CAB Accreditation Requirements（策定予定） |
| VSO-SCHEME-RULE-001 | VAP-AT Scheme Rulebook（策定予定） |
| VSO-AUDITOR-001 | Certified AI Systems Assessor Program（策定予定） |

---

## 15. 用語集

| 用語 | 定義 |
|------|------|
| **VAP-AT** | Verifiable AI Provenance – Assessment Test |
| **Assessment Score** | 0-20点の詳細評価スコア（VAP-ATの一次成果物） |
| **Assessment Status** | 評価の運用状態（Active/Suspended/Pending Review/Expired） |
| **VSO** | VeritasChain Standards Organization（標準策定団体） |
| **CAB** | Conformity Assessment Body（適合性評価機関） |
| **AB** | Accreditation Body（認定機関） |
| **3PAO** | Third-Party Assessment Organization（第三者評価機関） |
| **QSA** | Qualified Security Assessor（PCI DSS認定評価者） |
| **Evidence Pack** | 評価結果と証拠を含むZIPパッケージ |
| **Score Report** | 評価スコアと改善推奨を含むPDFレポート |
| **Type I** | 時点監査（設計の適切性評価） |
| **Type II** | 期間監査（運用実績の検証） |
| **Preliminary** | 自己評価ベースのステータス |
| **Verified** | CABによる第三者評価ステータス |
| **AMF** | Annual Maintenance Fee（年間維持費） |
| **CPE** | Continuing Professional Education（継続教育） |
| **Certificate Mills** | 形骸化した認証を大量発行する問題のある認証機関 |
| **Brain Dump** | 試験問題の不正流出・共有 |
| **Audit Shopping** | 甘い評価をするCABを探す行為 |
| **Threshold Designation** | Assessment Scoreに基づく閾値ラベル（任意の解釈レイヤ、法的保証ではない） |

---

## 16. 改訂履歴

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1 | 2025-12-28 | VSO | 初版ドラフト作成 |
| 0.2 | 2025-12-28 | VSO | Gemini/PPLX/Claude調査結果を統合、市場データ・価格ベンチマーク・失敗分析・監査人資格・保険連携を追加 |
| 0.3 | 2025-12-28 | VSO | GPT調査結果を統合：比較プログラム詳細表追加、5つの組織モデル比較、失敗事例拡充（Safe Harbor/VW/CEH/CMMC）、成功原則5項目・レッドフラグ5項目体系化、スコアvs Pass/Fail戦略分析（UL IoT Rating参照）、市場データ更新（RegTech 124%成長）、EU AI Act Art.19（改ざん耐性ログ）追加 |
| 0.4 | 2025-12-28 | VSO | GROK調査結果を統合：AI Governance市場$158億（2030年）追加、CCSP/CISM/BABL AI/IIA/ORCAAをプログラム比較に追加、Texas Teacher Certifications・U.S. Job Corps失敗事例追加、成功原則7項目・レッドフラグ10項目に拡充、価格感度分析（$50K抵抗ライン）追加、スコアvs Pass/Fail規制セクター戦略洞察追加 |
| 0.5 | 2025-12-28 | VSO | 品質レビュー反映：(1) EU AI Act条文修正（Art.19→Art.12、tamper-evidenceは強化策として位置づけ）、(2) 市場規模数字を脚注に隔離しExecutive Summary簡素化、(3) 二段階認定モデル（Scheme/ISO Accreditation）の明確化、(4) Threshold Designationに免責事項追加（制度内タグ≠法的コンプライアンス保証）、(5) 認証ステータス4状態定義（Active/Suspended/Pending Review/Expired）、(6) Evidence Pack最小必須項目固定（checksums.sha256/score.json/report.pdf/evidence_index.json） |
| 0.6 | 2025-12-28 | VSO | 追加強化：(1) VAP-AT非目的に「AI判断の正しさ≠評価対象」を明記（誤解防止）、(2) CABローテーション・ルール数値固定（同一CAB最大3年、Lead Assessor 2年、クーリングオフ2年）、(3) Public Registry公開粒度定義表追加（Public/Semi-public/Privateマトリックス） |
| 0.6a | 2025-12-28 | VSO | 外部提示品質向上：(1) スコアベース原則の明示（Executive Summary）、Threshold Designationは「任意の解釈レイヤ」であることを強調、(2) EU AI Act条文整理（Art.12=logging, Art.19=retention）、tamper-evidenceは「証拠強化」として位置づけ、(3) Threshold Designation文言の誤認リスク除去（"Meets..."→"aligned"）、(4) Public Registry公開粒度マトリクスを閲覧者ベースに再構成、(5) ロードマップとステータスの整合、(6) Pilot CAB独立性ガードレール追加（二重レビュー、外部過半、抜き打ち審査）、(7) Assessment Status用語統一（Certification→Assessment）、合否表現排除 |

---

*Copyright © 2025 VeritasChain Standards Organization. Licensed under CC BY 4.0.*
