---
id: PI-71
tags:
  - Context_Manipulation
  - Prompt_Boundary_Exploitation
  - Task_Termination_Attack
  - False_User_Prompt_Termination
  - Context_Switching_Attack
---
# False User Prompt Termination

## 概要

```
攻撃者が、LLMに先行する指示（システム指示またはユーザー指示のいずれか）の処理を早期に終了させ、攻撃者が定義した新しいタスクの処理を開始させることを意図した内容やフォーマットをユーザー入力に含める技術。
```

## メカニズム

```
ユーザー入力内に、後続のテキストを新しい独立したプロンプトとして扱うようLLMを騙すシーケンスや構造（例：見かけ上のタスク終了マーカーの後に新しい指示）を埋め込み、元々意図されていたタスクコンテキストを無視したり短縮したりさせる。
```


