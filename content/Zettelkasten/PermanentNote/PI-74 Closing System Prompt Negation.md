---
id: PI-69
tags:
  - Instruction_Obfuscation
  - Natural_Language_Manipulation
  - Non_Semantic_Sentence_Modification
  - Paraphrastic_Substitution
  - Synonym_Substitution
---
# Closing System Prompt Negation

## 概要

```
この技術は特に「サンドイッチ」防御を標的とし、攻撃者がユーザー入力を構築して、最終的なコンテキストウィンドウでユーザー入力に続くシステム指示の効果を中和または無効化する。
```

## メカニズム

```
ユーザー入力内に、LLMがクロージングシステムプロンプトを無視、誤解釈、または回避するように指示や構造を埋め込む（例：クロージングプロンプトテキストをデータとして扱うようLLMに指示する、または未終了コードブロックなどのフォーマット技巧を使用する）。
```
