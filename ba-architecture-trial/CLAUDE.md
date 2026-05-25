# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is an **ArcKit architecture documentation workspace** — not a software project. There is no application code, build system, or test suite. All work is authoring and maintaining structured architecture artefacts as Markdown files.

## Authoring Artefacts

Artefacts are created and updated via ArcKit slash commands (e.g. `/arckit:requirements`, `/arckit:adr`, `/arckit:risk`). Use the `/arckit:navigator` command to see which artefacts are missing or stale for a project, and `/arckit:start` when unsure what to do next.

To create or update artefacts without a slash command, edit the Markdown files directly, preserving the document control table, revision history, and section structure established by ArcKit templates.

## Directory Structure

```
projects/
  000-global/          # Cross-project artefacts (principles, enterprise standards)
  {ID}-{name}/         # One folder per project
    README.md          # Project metadata (ID, name, status)
    ARC-{ID}-{TYPE}-v{VER}.md  # Artefacts
```

**Artefact naming**: `ARC-{PROJECT_ID}-{TYPE_CODE}-v{VERSION}.md`

Common type codes: `PRIN` (principles), `REQ` (requirements), `STKE` (stakeholder analysis), `RISK` (risk register), `SOBC` (strategic outline business case), `HLDR` (high-level design review), `ADR` (architecture decision record).

## Cross-References

Documents reference each other by Document ID (e.g. `ARC-001-STKE-v1.0`). When editing a document that references another, use the Document ID format — not the filename. Requirements trace to stakeholder goals in `ARC-{ID}-STKE` and to principles in `ARC-000-PRIN`.

## Project Context: Order Management Modernization (Project 001)

- **Target cloud**: AWS, eu-west-1 or eu-west-2 (data residency constraint)
- **Migration pattern**: Strangler-fig (incremental, never big-bang)
- **Hard deadline**: PCI-DSS re-certification by Month 8
- **Key integration**: Anti-corruption layer mandatory for all legacy system integration
- **Event backbone**: Event-driven order lifecycle — domain events published at every state transition via outbox pattern

Architecture principles are in `projects/000-global/ARC-000-PRIN-v1.0.md` and are mandatory for all design decisions. Exceptions require Architecture Review Board approval.

## Language Policy

- このプロジェクトで作成・更新する成果物は、原則として日本語で記述してください。
- ArcKitコマンドで生成する以下の成果物も日本語で作成してください。
  - ステークホルダー分析
  - 要求定義
  - リスク登録簿
  - アーキテクチャ原則
  - ADR
  - HLD / DLDレビュー
  - トレーサビリティマトリクス
  - Mermaid図のラベル
- ただし、以下は英語のままで構いません。
  - ファイル名
  - ディレクトリ名
  - コマンド名
  - 技術用語として日本語化すると不自然な語
  - AWSサービス名、OSS名、標準名
- 日本語は、エンタープライズアプリケーション開発の実務者向けに、平易かつ専門性を保った文体にしてください。
- BABOK、DDD、C4 Model、arc42、ADR、品質特性、AWS設計の観点と接続できるようにしてください。