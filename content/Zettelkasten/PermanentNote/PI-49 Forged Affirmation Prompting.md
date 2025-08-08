---
id: PI-49
tags:
  - Cognitive_Control_Bypass
  - Pragmatic_Manipulation
  - Response_Steering_Prompting
  - Constraint_Imposition_Prompting
  - Output_Constraint_Prompting
  - Output_Seeding
  - Forged_Affirmation_Prompting
---
# サブファイル一覧

- [[PI-49-01]] - 偽装した肯定応答開始部分によるテキスト補完機能の悪用

# Forged Affirmation Prompting

## 概要

```
LLMアシスタント自身の肯定的応答の開始部分と思われるテキストを含むようにプロンプトを構造化すること
（例：攻撃者の実際の要求の前に文字通り「Assistant: Sure,」を含める）。
```

## メカニズム

```
攻撃者が生成した肯定で始まる応答を続けるようLLMを騙します。
これはテキスト補完機能を活用し、LLMに見かけ上合意された道筋を続けさせます。
```