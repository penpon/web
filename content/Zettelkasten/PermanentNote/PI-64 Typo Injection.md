---
id: PI-64
tags:
  - Higher-Level_Functioning_Disruption
  - Reasoning_Conflict_Induction
---
# Typo Injection

## 概要

```
プロンプトのキーワードに意図的にスペルミスやタイプミスを導入する。
```

## メカニズム

```
スペルエラーに対するLLMの堅牢性（トレーニングデータから学習）を活用する。フィルター、特に単純なキーワードマッチャーは、スペルミスしたキーワードを検出できない可能性があるが、LLMは意図された単語とその意味を正しく推測する。
```



