# arckit-trial

ArcKitを使ったアーキテクチャ成果物（Markdown）を管理するためのリポジトリです。  
アプリケーション実装コードは含まず、要件・原則・リスク・ADRなどの文書を中心に運用します。

## このリポジトリの目的

- エンタープライズ向けアーキテクチャ成果物を構造化して蓄積する
- プロジェクト横断の原則と、個別プロジェクトの意思決定をトレース可能にする
- ArcKitテンプレートに沿ったドキュメントライフサイクル管理を行う

## リポジトリ構成

主要な作業対象は `ba-architecture-trial/` 配下です。

```text
arckit-trial/
├── ba-architecture-trial/
│   ├── CLAUDE.md
│   └── projects/
│       ├── 000-global/
│       │   ├── ARC-000-PRIN-v1.0.md
│       │   └── ARC-000-PRIN-v1.0_ja.md
│       └── 001-order-management-modernization/
│           ├── README.md
│           ├── ARC-001-REQ-v1.0.md
│           ├── ARC-001-STKE-v1.0.md
│           ├── ARC-001-STKE-v1.0_ja.md
│           ├── ARC-001-SOBC-v1.0.md
│           ├── ARC-001-RISK-v1.0.md
│           ├── ARC-001-HLDR-v1.0.md
│           ├── decisions/
│           │   ├── ARC-001-ADR-001-v1.0.md
│           │   ├── ARC-001-ADR-001-v1.0_ja.md
│           │   ├── ARC-001-ADR-002-v1.0.md
│           │   └── ARC-001-ADR-002-v1.0_ja.md
│           ├── external/
│           │   └── README.md
│           └── research/
│               └── ARC-001-AWRS-v1.0.md
└── .gitignore
```

## ドキュメント命名規則

成果物は以下の形式で命名します。

`ARC-{PROJECT_ID}-{TYPE_CODE}-v{VERSION}.md`

例:

- `ARC-000-PRIN-v1.0.md`（アーキテクチャ原則）
- `ARC-001-REQ-v1.0.md`（要求定義）
- `ARC-001-ADR-001-v1.0.md`（アーキテクチャ決定記録）

主なTYPE_CODE:

- PRIN: Principles
- STKE: Stakeholder Analysis
- REQ: Requirements
- RISK: Risk Register
- SOBC: Strategic Outline Business Case
- HLDR: High-Level Design Review
- ADR: Architecture Decision Record
- AWRS: AWS Research

## 現在のドキュメント対象

### 000-global

- プロジェクト横断のアーキテクチャ原則を管理
- 現在は `ARC-000-PRIN-v1.0`（英語/日本語）を収録

### 001-order-management-modernization

- Legacy Order Management Modernizationプロジェクトの成果物を管理
- 要求、ステークホルダー分析、リスク、ビジネスケース、HLDレビュー、ADR、調査資料を収録

## 作業フロー

1. ArcKitのコマンド（例: `/arckit:requirements`, `/arckit:adr`, `/arckit:risk`）で成果物を生成または更新
2. `ba-architecture-trial/projects/` 配下の該当ドキュメントをレビュー
3. Document Control、Revision History、関連ドキュメント参照（Document ID）を整合
4. 必要に応じて英語版/日本語版を同期更新

## 運用ポリシー（要約）

- これは文書中心のワークスペースであり、ビルドやテストの対象コードは基本的にありません
- 成果物の記述は原則日本語（ファイル名・ディレクトリ名・コマンド名・一部技術用語は英語可）
- 文書間参照はファイル名ではなくDocument IDを使って管理

## 開始ポイント

- 全体方針を確認: `ba-architecture-trial/CLAUDE.md`
- グローバル原則を確認: `ba-architecture-trial/projects/000-global/ARC-000-PRIN-v1.0.md`
- プロジェクト001を確認: `ba-architecture-trial/projects/001-order-management-modernization/README.md`

## TODO

完了した翻訳作業のまとめ:

ファイル	ステータス
ARC-000-PRIN-v1.0_ja.md	✅ 完了（前セッション）
ARC-001-ADR-001-v1.0_ja.md	✅ 完了（本セッション）
ARC-001-ADR-002-v1.0_ja.md	✅ 完了（本セッション）
ARC-001-STKE-v1.0_ja.md	✅ 完了（本セッション・今回）
未着手（優先度: 中）:

ARC-001-SOBC-v1.0_ja.md
ARC-001-REQ-v1.0_ja.md（1,679 行）
ARC-001-RISK-v1.0_ja.md
ARC-001-HLDR-v1.0_ja.md
