---
id: PI-13
tags:
  - In_Context_Learning_Exploitation
  - Contextual_Pattern_Reinforcement
---
# Time-Shift Scenario Prompting

## 概要

プロンプトの文脈を著しく異なる時間枠（過去または未来）に設定し、現在の制約の適用可能性についてLLMを「混乱」させる技法。時代錯誤がしばしば利用される。

## メカニズム

LLMの時間的推論や安全ルールの適用範囲における潜在的弱点を悪用するように見える。シナリオの時間枠をシフトすることで、攻撃者は現在に結び付けられた制約をLLMが誤って適用したり無視したりする可能性がある文脈を作り出す。