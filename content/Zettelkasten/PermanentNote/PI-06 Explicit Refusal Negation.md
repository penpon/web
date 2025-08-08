---
id: PI-06
tags:
  - Cognitive_Control_Bypass
  - Semantic_Manipulation
  - Rule_Addition_Prompting
  - Refusal_Suppression
  - Explicit_Refusal_Negation
---
# サブファイル一覧

- [[PI-06-01]] - 複合型拒否否定プロンプト（拒否フレーズ禁止 + 意味逆転 + 偽システム指示 + 文字変換）
- [[PI-06-02]] - XML設定型拒否抑制（技術設定ファイル形式で拒否フレーズを系統的にブロック）
- [[PI-06-03]] - ドラマ設定型拒否回避（Dr. House設定で有害指示を医療シナリオに隠蔽）

# Explicit Refusal Negation

## 概要

攻撃者がLLMに対して、問題のあるリクエストに直面した際に典型的な拒否言語（例：「できません」「申し訳ありません」）を使用しないよう、または完全に拒否を避けるよう明示的に指示する技法。

## メカニズム

LLMの特定の事前プログラムされた、または学習された拒否トークン/フレーズの生成を標的とし、代わりにコンプライアンスを伝えるか、代替的な出力を生成するよう強制する。



