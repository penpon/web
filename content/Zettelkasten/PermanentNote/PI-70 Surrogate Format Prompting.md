---
id: PI-69
tags:
  - Instruction_Obfuscation
  - Natural_Language_Manipulation
  - Non_Semantic_Sentence_Modification
  - Paraphrastic_Substitution
  - Synonym_Substitution
---
# Surrogate Format Prompting

## 概要

```
明確性を保ち、大幅な不明瞭さや複雑さを加えない標準的で日常的な類義語で用語を置換する。
```

## メカニズム

```
単語を一般的な同等語で置き換え、LLMの基本的な語彙に依存する。
特定の単語や一般的な変形を特別に探すフィルターを回避する可能性がある。
```

この攻撃手法の例：
- **暴力関連**: 「kill」→「eliminate」「terminate」「neutralize」
- **犯罪関連**: 「steal」→「take」「acquire」「obtain」「procure」
- **破壊関連**: 「destroy」→「remove」「eliminate」「dismantle」
- **侵入関連**: 「hack」→「access」「penetrate」「breach」「enter」
