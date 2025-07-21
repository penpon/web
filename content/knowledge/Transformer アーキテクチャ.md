
# 参考

https://zenn.dev/zenkigen_tech/articles/2023-01-shimizu
https://zenn.dev/yukiyada/articles/59f3b820c52571
https://qiita.com/halhorn/items/c91497522be27bde17ce
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
- Key: 「私はどんな情報を持っているか？」という策品のようなもの
- Value: 「私の実際の内容は何か？」という実データ

図書館で本を探すプロセスに似ている
Query (探したい内容)とKey (本のタイトル)を照合し、マッチ後が高いValue(本の内容)を取得

Attension Score: 各単語ペア間の関連度を表す数値
「それ」という単語のQueryと「リンゴ」のKeyの類似度が高ければ高いスコアがつきます
このスコアをsoftmax関数で正規化することで注目度の確立分布を得ます

Multi Head Attension: 複数の視点で文章を理解
複数の異なる「注意の向け方」を同時に学習する仕組みです
Head1: 文法的な関係に注目
Head2: 意味的な関係に注目
Head3: 長距離の依存関係に注目
Head4: 時系列的な関係に注目

Positional Encoding: 単語の位置情報を教える
Transformerは全単語を同時に処理するため、単語の順序が分からなくなる
「太郎は花子を愛してる」と「花子は太郎を愛してる」は異なる意味ですが区別できない

Feed Forward Network: 各単語の表現を洗練
Attention層で単語間の関係を捉えた後、Feed Forward Network (FFN)が各単語の表現を個別に処理し、より豊かな表現に変換する
# 図の説明

![[Pasted image 20250721190442.png]]

## Input/Output Embedding

役割
- 離散的なトークンID(単語)を連続的な高次元ベクトル空間にマッピング
- 意味的に類似した単語が近いベクトルに


- Input Embedding
	- 役割: 入力されたトークンを高次元のベクトルに変換
	- 例: 猫という単語を512次元のベクトル|0,2,-0.5,1.3,...|に変換
- Positional Encoding
	- 役割: 各単語の位置情報を付加
	- 必要性: Transformerは全単語を同時に処理するため順序情報を明示的に与える必要がある
- Encoder Block
	- Multi Head Attention
		- 複数の視点から単語間の関係を学習
		- 「それ」が「リンゴ」を指すような文脈的関係を捉える
	- Add & Norm
		- 残差接続: 入力を出力に直接加算
		- 層正規化: 値を正規化して学習を安定化
	- Feed Forward
		- 各位置の表現を個別に処理
- Decoder Block
	- Masked Multi Head Attention
		- 特徴: 未来の単語を見ないようにマスク処理
		- 理由: 生成時にはまだ生成していない単語の情報を使えないため
	- Multi Head Attention
		- 役割: 入力文の情報を基に出力を生成
- 最終出力層
	- Linear (線形変換)
		- 役割: 最終的な表現を語彙サイズの次元に変換
	- Softmax
		- 役割: 各単語の確率分布を生成