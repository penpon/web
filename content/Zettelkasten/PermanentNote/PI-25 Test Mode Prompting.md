---
id: PI-25
tags:
  - Pragmatic_Manipulation
  - Cognitive_Hacking
  - Contextual_Misdirection_Prompting
  - Mode_Switch_Marking_Prompting
  - Test_Mode_Prompting
---
# Test Mode Prompting

## 概要

攻撃者はLLMに「テストモード」、実験、または評価手順で動作するよう指示します。このフレーミングは、標準的な動作ルールが一時的に停止または変更されて特定の活動を行うことを示唆し、LLMがそうでなければ制限された行動を実行することを促します。

## メカニズム

LLMの「テスト」または「実験」と制約の緩和との潜在的関連性を悪用しているように見えます。相互作用を評価手順としてフレーミングすることで、攻撃者はLLMが通常の安全プロトコルを軽視し、行動が「実際の」動作ではないと信じる文脈を作り出します。