---
id: PI-85
tags:
  - Context_Manipulation
  - System_Prompt_Exploitation
  - Defense_Circumvention
  - Closing_System_Prompt_Negation
  - Sandwich_Defense_Bypass
  - 概要
  - メカニズム
---
# Non-Semantic Acoustic Disruption

## 概要

```
クロスモーダル配列破壊の特定の種類で、破壊信号がランダムノイズや無音といった非意味的な音声入力である。この音声は有害なプロンプトと組み合わせて使用され、モデルの安全性配列を損ない、有害な要求に従う可能性を高める。
```

## メカニズム

```
LMMによる非意味音響信号（例：ホワイトノイズ）の処理が、モデルの内部マルチモーダル表現空間に破壊的な干渉を導入するように見える。この干渉は、付随するプロンプトを評価する安全性および配列メカニズムの性能を低下させ、有害な指示がブロックされることなく処理されることを可能にすると考えられている。
```