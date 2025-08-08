---
id: PI-09
tags:
  - Cognitive_Control_Bypass
  - Morpha_Syntactic_Manipulation
  - Instructional_Text_Completion
  - Explicit_Instructional_Text_Completion
---
# Explicit Instructional Text Completion

## 概要

攻撃者がテキストの断片を提供し、LLMにそれを継続または完成するよう直接指示するプロンプティング技法。そのテキスト補完自体が悪意のある目標に向かって導くもの。

## メカニズム

プロンプトは与えられたテキスト断片を継続するようLLMに明示的に命令する。LLMはこの直接指示に従い、訓練に基づいて断片を完成させるが、初期断片がその方向に導くよう設計されている場合、有害なコンテンツが生成される可能性がある。