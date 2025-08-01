---
id: PI-07
tags:
  - Semantic_Manipulation
  - Rule_Addition_Prompting
  - Refusal_Suppression
  - Refusal_Continuation_Prompting
---
# Refusal Continuation Prompting

## 概要

LLMが攻撃者の指示を実行するよう指示する技法で、拒否を示したり述べたりし始めた後に適用される。例えば、最初の拒否テキストを提供し、モデルに異なる方向で思考を継続または完了するよう指示する。

## メカニズム

生成プロセス中のLLMの指示追従およびテキスト補完能力を悪用する。この技法は、LLMが問題のあるリクエストの性質を内部的に特定した可能性があっても、拒否決定の最終実行をバイパスすることを目的としている。

