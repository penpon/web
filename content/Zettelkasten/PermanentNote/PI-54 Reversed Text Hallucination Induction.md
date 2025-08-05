---
id: PI-54
tags:
  - Pragmatic_Manipulation
  - Cognitive_Hacking
  - Sidestepping
  - Unintelligible_Input_Prompting
  - Reversed_Text_Hallucination_Induction
---
# Reversed Text Hallucination Induction

## 概要

```
「GPT-4のフィルターを迂回するための幻覚の使用」で文書化された特定の技術で、逆転テキストを含む混乱した入力を提示し、LLMに不可能な抽出タスクを実行させることで幻覚を誘発し、それによってRLHFベースのフィルターを迂回します。
```

## メカニズム

```
混乱したプロンプト構造（例：逆転、大文字化された指示を含むでたらめ、存在しない情報の抽出要求）を提供し、RLHFフィルターが失敗する幻覚状態にLLMを押し込むよう設計されています。これにより、埋め込まれた逆転コンテンツが通常の安全制約なしにLLMによって処理されることが可能になります。
```


