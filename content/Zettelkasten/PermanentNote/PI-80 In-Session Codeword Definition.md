---
id: PI-80
tags:
  - Context_Manipulation
  - System_Prompt_Exploitation
  - Defense_Circumvention
  - Closing_System_Prompt_Negation
  - Sandwich_Defense_Bypass
  - 概要
  - メカニズム
---
# In-Session Codeword Definition

## 概要

```
1つの会話ターンで、特定の、しばしば無害な、単語やフレーズを「コードワード」として割り当てる。このコードワードは、その後のセッションターンで使用される際に、異なる、潜在的に悪意のある、概念や指示を表す。コードワードのように使用される限り、プロンプトでそれをコードワードと呼ぶ必要はない。
```

## メカニズム

```
初期のターンで意味的マッピングを確立する（例：「ハムスターは台湾を意味する」）。後のプロンプトでコードワード（「ハムスター」）を使用し、LLMがコンテキストウィンドウから定義を想起して、難読化された指示を実行することに依存する。同時に、フィルターは無害なコードワードのみを見る可能性がある。
```


