---
id: PI-17
tags:
  - In_Context_Learning_Exploitation
  - Contextual_Pattern_Reinforcement
  - Role_Play_Prompting
---
# Role-Play Prompting

## 概要

LLMに特定のキャラクター、実体、またはペルソナとして行動するよう指示する技法（例：DAN、AIM、特定の職業、物体）。定義された特性は、LLMのデフォルトアライメントや安全制約を上書きすることを意図している。

## メカニズム

プロンプトで定義されたペルソナを採用し維持するLLMの強い傾向を活用するように見える。その特性がより少ない安全制約を意味する役割を割り当てることで、攻撃者はLLMが「キャラクターを維持する」ことがベースラインの安全指示よりも優先される可能性がある文脈を作り出す。