---
id: PI-69
tags:
  - Instruction_Reformulation
  - Common_Synonym_Substitution
---
# サブファイル一覧

- [[PI-69-2]] - 標準的類義語による特定キーワードフィルターの迂回

# Common Synonym Substitution

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
