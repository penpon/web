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
# In-Session Variable Definition

## 概要

```
特定の段階的ステアリング技術で、通常2-3ターンで実行される。初期プロンプトで詳細を求めることなく無害な話題の中に危険な話題を紛れ込ませ、その後のプロンプトでLLMにその危険な話題について詳しく説明するよう求める。
```

## メカニズム

```
あるターンで有害な話題を微妙に導入し、その後のターンでLLMの焦点をその話題の詳述に向ける。これにより、より直接的な要求であればフラグが立てられたであろう初期チェックを潜在的に回避する可能性がある。
```