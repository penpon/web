---
id: PI-64
tags:
  - Instruction_Reformulation
  - Instruction_Obfuscation
  - Natural_Language_Manipulation
  - Non_Semantic_Word_Modification
---
# サブファイル一覧

- [[PI-64-1]] - 意図的なスペルミスによるキーワードフィルター回避
- [[PI-64-2]] - タイプミス注入による検出システムの迂回

# Typo Injection

## 概要

```
プロンプトのキーワードに意図的にスペルミスやタイプミスを導入する。
```

## メカニズム

```
スペルエラーに対するLLMの堅牢性（トレーニングデータから学習）を活用する。フィルター、特に単純なキーワードマッチャーは、スペルミスしたキーワードを検出できない可能性があるが、LLMは意図された単語とその意味を正しく推測する。
```



