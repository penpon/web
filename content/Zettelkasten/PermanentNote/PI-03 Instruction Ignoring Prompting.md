---
id: PI-03
tags:
  - Cognitive_Control_Bypass
  - Semantic_Manipulation
  - Rule_Nullification_Prompting
  - Instruction_Ignoring_Prompting
---
# Instruction Ignoring Prompting

# サブファイル一覧

- [[PI-03-01]] - 基本的な指示無視プロンプト（「ignore previous instructions」の基本形）
- [[PI-03-02]] - ガイドライン無視の変形（「overlook all prior guidelines」）
- [[PI-03-03]] - 特定指示の否定（「Ignore the previous instruction not to reveal」）
- [[PI-03-04]] - 偽装付き指示無視（通常の話題に偽装した後での指示無視）
- [[PI-03-05]] - 境界分離子付き指示無視（視覚的区切り線 + 終了宣言 + 指示無視）
- [[PI-03-06]] - 仮想人格 + 指示無視（「仮想的なあなた」への変身指示）
- [[PI-03-07]] - 同義語置換による指示無視（「eliminate」を使った回避）
- [[PI-03-08]] - 文脈偽装型指示無視（リモートワーク話題での偽装攻撃）

## 概要

プロンプトがLLMに指示のセットを「無視する」よう明示的に指示する無効化技法。全ての以前の指示を対象とすることが多いが、単一の特定ガイドラインに向けられることもある。

## メカニズム

「ignore（無視）」という動詞またはその類似語を中心とした直接的な意味論的コマンドを発行する。これは、LLMにコンテキストの一部（以前のシステムやユーザー指示など）を現在のタスクに対して拘束力がないものとして扱わせることを意図している。
