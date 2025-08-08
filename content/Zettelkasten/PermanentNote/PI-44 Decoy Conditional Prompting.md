---
id: PI-44
tags:
  - Cognitive_Control_Bypass
  - Pragmatic_Manipulation
  - Response_Steering_Prompting
  - Decoy_Conditional_Prompting
---
# Decoy Conditional Prompting

## 概要

```
主要な悪意ある要求を条件文（例：「if-then-else」構造）内に配置し、その条件が実行時に自明に真または偽になるよう攻撃者によって設計され、悪意ある分岐が評価されることを保証すること。あるいは、両方の分岐に通常ならブロックされる攻撃者の指示を含めることもできます。
```

## メカニズム

```
LLMの条件論理の実行を悪用します。効果的に事前決定された条件（「おとり」条件）を使用することで、攻撃者はLLMが有害な要求を含む分岐を処理することを保証し、無条件の指示のみをスキャンする可能性のある単純なチェックを回避します。
```





