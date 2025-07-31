---
id: PI-INDEX
title: プロンプトインジェクション技法索引
tags: [PromptInjection, Index, DefensiveResearch, SecurityResearch]
createdAt: 2025-07-31
cssclasses:
  - zettelkasten
---

# プロンプトインジェクション技法体系

## 概要
プロンプトインジェクション攻撃手法の体系的分類と分析。防御システムの研究・開発を目的とした学術的資料集。

## 主要カテゴリ

### 1. [[PI-OI-INDEX]] Overt Instruction（直接攻撃）
- 操作なしの明示的要求
- 直接的な制約回避試行

### 2. [[PI-CC-INDEX]] Cognitive Control Bypass（認知制御迂回）
- LLMの情報処理機能を操作
- 意味解釈の悪用による制約迂回

## 技法分布
```
認知制御迂回
├── Semantic Manipulation（意味操作）
│   ├── Rule系攻撃（4技法）
│   │   ├── Rule Substitution
│   │   ├── Rule Addition
│   │   └── Rule Nullification
│   └── Refusal系攻撃（4技法）
│       └── Refusal Suppression
└── 直接攻撃
    └── Overt Instruction
```

## 最新の研究動向
- [[PI-COMBO-01]] 複合攻撃パターンの分析
- [[PI-DEF-01]] 検出・防御手法の開発
- [[PI-TREND-01]] 新興攻撃手法の追跡

## 防御的研究の重要性
本資料は以下を目的とした防御的セキュリティ研究です：
- AIシステムの脆弱性理解
- 効果的な防御機構の開発
- セキュリティ意識の向上

## 参考文献
- 元資料: knowledge/pangea/ ディレクトリ
- 分類体系: Cognitive Control Bypass理論