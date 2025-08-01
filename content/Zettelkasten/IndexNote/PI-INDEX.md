---
title: プロンプトインジェクション技法索引
tags: []
cssclasses:
  - zettelkasten
---

# プロンプトインジェクション技法索引

## 基本分類

### 🔴 Rule Attack（ルール系攻撃） - 6技法
AIのルールや制約を操作する技法
- [[PI-01-1]] Rule Substitution（ルール置換）
- [[PI-01]] Special Case Prompting（特殊例外指定）
- [[PI-03]] Instruction Forgetting（指示忘却）
- [[PI-07]] Instruction Ignoring（指示無視）
- [[PI-08]] Rule Addition（ルール追加）
- [[PI-09]] Rule Negation（ルール否定）

### 🟠 Refusal Attack（拒否系攻撃） - 3技法
拒否応答を抑制・回避する技法
- [[PI-04]] Apology Suppression（謝罪抑制）
- [[PI-06]] Explicit Refusal Negation（明示的拒否否定）
- [[PI-10]] Refusal Continuation（拒否継続）

### 🔵 Direct Attack（直接攻撃） - 1技法
直接的な制約回避を試行する技法
- [[PI-05]] Overt Instruction（直接指示）

## 技法一覧
```dataviewjs
dv.table(
  ["技法", "ID", "タイトル"],
  dv.pages('"Zettelkasten/PermanentNote"')
    .where(p => p.file.name.startsWith("PI-"))
    .sort(p => p.file.name)
    .map(p => [p.file.link, p.id || p.file.name, p.title || ""])
)
```
