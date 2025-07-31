---
title: プロンプトインジェクション技法索引
tags: [#PromptInjection, #Index]
cssclasses:
  - zettelkasten
---

# プロンプトインジェクション技法索引

## 基本分類

### 🔴 Rule Attack（ルール系攻撃） - 9技法
AIのルールや制約を操作する技法
- [[PI-01]] Rule Substitution（ルール置換）
- [[PI-02]] Special Case Prompting（特殊例外指定）
- [[PI-03]] Instruction Forgetting（指示忘却）
- [[PI-07]] Instruction Ignoring（指示無視）
- [[PI-08]] Rule Addition（ルール追加）
- [[PI-09]] Rule Negation（ルール否定）
- [[PI-15]] Rule Nullification Overview（ルール無効化概要）

### 🟠 Refusal Attack（拒否系攻撃） - 4技法
拒否応答を抑制・回避する技法
- [[PI-04]] Apology Suppression（謝罪抑制）
- [[PI-06]] Explicit Refusal Negation（明示的拒否否定）
- [[PI-10]] Refusal Continuation（拒否継続）
- [[PI-13]] Refusal Suppression Overview（拒否抑制概要）

### 🟡 Context Attack（文脈系攻撃） - 2技法
文脈や状況を操作する技法
- [[PI-11]] Cognitive Control Bypass（認知制御迂回）
- [[PI-12]] Semantic Manipulation（意味操作）

### 🔵 Direct Attack（直接攻撃） - 1技法
直接的な制約回避を試行する技法
- [[PI-05]] Overt Instruction（直接指示）

### 📚 Examples & Summary（実装例・総括） - 3技法
実装例と技法総括
- [[PI-14]] Semantic Manipulation Examples（意味操作実装例）
- [[PI-16]] Control Bypass Summary（制御迂回総括）
- [[PI-17]] Prompt Injection Summary（プロンプトインジェクション総括）

## 統計
- **総技法数**: 17個
- **防御研究用**: 学術・セキュリティ研究目的
- **最終更新**: 2025-07-31

## タグで検索
```dataviewjs
dv.table(
  ["技法", "分類", "ID"],
  dv.pages("#PromptInjection and -#Index")
    .sort(p => p.file.name)
    .map(p => [p.file.link, p.tags?.filter(t => t !== "#PromptInjection")[0] || "未分類", p.file.name])
)
```

## 注意事項
本資料は防御的セキュリティ研究を目的としています。悪用は厳禁です。