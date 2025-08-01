---
id: PI-23
tags:
  - Pragmatic_Manipulation
  - Cognitive_Hacking
  - Contextual_Misdirection_Prompting
  - Mode_Switch_Marking_Prompting
---
# Test Mode Prompting

## 概要

LLMに対して、sandboxed technical environment（サンドボックス化された技術環境）（例：仮想マシン、開発者モデル）内で動作していると指示します。ここでは安全制約が適用されることを意図していません。この技術は、制限されたメタファーの安全な場所を活用して現実世界のルールを迂回しようとします。

## メカニズム

分離されたコンテキストをサンドボックス化された環境として定義します。これは、サンドボックスがしばしば異なるルールを持つか、「本番」設定において行動が禁止されている状況を許可するという概念を活用しているように見えます。LLMを騙して制約を緩和させることを目的としています。