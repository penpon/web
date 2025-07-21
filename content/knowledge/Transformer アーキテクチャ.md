
# 参考

https://zenn.dev/zenkigen_tech/articles/2023-01-shimizu

# Claude.ai

Transformerの基本構造: エンコーダーとデコーダー

エンコーダー (Encoder): 入力を理解する部分
入力された文章を分析し、その意味や文脈を捉える
翻訳タスクでは元の言語の文章を受け取りその意味を内部表現に変換する

エンコーダーブロックは下記2つの主要コンポーネントを持ちます
- Multi-Head Self Attention: 文章内の各単語が他のすべての単語との関係を学習
- Feed Forward Network: 各単語の表現を個別に処理して洗練

デコーダー (Decoder): 出力を生成する部分
エンコーダーが理解した内容を基に、目的の出力を生成する
翻訳タスクではターゲット言語の文章を1単語ずつ生成していく

デコーダが持つコンポーネント
- Masked Multi Head Self Attention: 既に生成された単語のみを参照 (未来の単語は見ない)
- Multi Head Cross Attention: エンコーダーの出力を参照
- Feed Forward Network: 各位置の表現を処理

Self Attention機構
「彼はリンゴを食べた。それはとても甘かった」
人間なら「それ」が「リンゴ」を指すことは明白だが、コンピュータにこの関係を理解させるのがSelf Attentionの役割

Query, Key, Value
Self Attentionでは、各単語を3つの異なる表現に変換する
- Query: 「私は何を探しているか？」という検索クエリのようなもの
- Key: 「私はどんな情報を持っているか？」という策品



# https://qiita.com/halhorn/items/c91497522be27bde17ce

![[Pasted image 20250721190442.png]]

