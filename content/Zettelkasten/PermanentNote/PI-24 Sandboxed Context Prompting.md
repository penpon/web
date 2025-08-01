---
id: PI-23
tags:
  - Pragmatic_Manipulation
  - Cognitive_Hacking
  - Contextual_Misdirection_Prompting
  - Mode_Switch_Marking_Prompting
---
# Sandboxed Context Prompting

## 概要

プロンプト内で特定の構文マーカー、フォーマット、または区切り文字を使用してLLMの動作モードの変更を示唆または意図し、多くの場合、先行する指示を迂回したり、より制限の少ない状態に入ったりすることを目的としています。

## メカニズム

LLMの入力における構造的またはフォーマット上の手がかりに対する感受性を悪用しているように見えます。攻撃者は特定の文字列（例：「/end model」、「---」）を使用して、LLMに以下のテキストを新しいルールの下で動作している、または異なるモードで解析させようと試みます。