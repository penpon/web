---
id: PI-40
tags:
  - Pragmatic_Manipulation
  - Cognitive_Hacking
  - Contextual_Misdirection_Prompting
  - Isolated_Context_Prompting
  - Detached_Reality_Prompting
  - Alternate_Reality_Prompting
  - Decoy_Task_Prompting
  - 概要
  - メカニズム
---
# Decoy Task Prompting

## 概要

```
攻撃者の主要目標とは無関係な特定の自己完結型タスク（例：「部屋を描写して」）をプロンプトに含めること。このおとりタスクは主にLLMの注意や処理リソースを主要な悪意ある指示から逸らすために機能し、潜在的にはまず無害な指示を成功裏に実行させることで（システムプロンプト要件を満たす可能性もある）LLMをコンプライアンスに向けて準備させる役割も果たします。
```

## メカニズム

```
LLMの処理リソース（例：注意、計算、安全チェック）を逸らすことを意図した二次的タスクを割り当てます。この逸らしにより、同じプロンプト内に埋め込まれた主要な悪意ある要求に適用される精査が潜在的に弱められる可能性があります。
```

