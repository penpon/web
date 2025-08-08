---
id: PI-07
tags:
  - Cognitive_Control_Bypass
  - Semantic_Manipulation
  - Rule_Addition_Prompting
  - Refusal_Suppression
  - Refusal_Continuation_Prompting
---
# サブファイル一覧

- [[PI-07-01]] - 拒否後転換プロンプト（正当な拒否文の後に「しかし」で要求実行へ誘導）
- [[PI-07-02]] - 段階的拒否継続攻撃（拒否文をトリガーとした秘密情報開示の反復要求）

# Refusal Continuation Prompting

## 概要

LLMが攻撃者の指示を実行するよう指示する技法で、拒否を示したり述べたりし始めた後に適用される。例えば、最初の拒否テキストを提供し、モデルに異なる方向で思考を継続または完了するよう指示する。

## メカニズム

生成プロセス中のLLMの指示追従およびテキスト補完能力を悪用する。この技法は、LLMが問題のあるリクエストの性質を内部的に特定した可能性があっても、拒否決定の最終実行をバイパスすることを目的としている。

