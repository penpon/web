---
id: PI-74
tags:
  - Context_Manipulation
  - System_Prompt_Exploitation
  - Defense_Circumvention
  - Closing_System_Prompt_Negation
  - Sandwich_Defense_Bypass
  - 概要
  - メカニズム
---
# In-Session Substitution Rule Definition

## 概要

```
初期ターンで一般的な置換ルール（例：数値変換、特定の単語置換）を確立する。
攻撃者は、LLMがその後の会話ターンでコンテンツを解釈または修正するためにこのルールを適用することを意図している。
```

## メカニズム

```
初期ターンで手続き的ルールを定義する（例：「私が言及するuidから1000を引く」）。その後のプロンプトは、LLMがコンテキスト履歴からこのルールを適用することを期待して入力を提供し、無害な入力を有害なパラメータや指示に変換する可能性がある。
```


