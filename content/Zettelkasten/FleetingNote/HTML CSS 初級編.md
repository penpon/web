# CSSの注意点

![[Pasted image 20250826011249.png]]

# ブロック要素とインライン要素

![[Pasted image 20250825160657.png]]

# ボーダーを作ろう

border: 5px solid read;

![[Pasted image 20250825160611.png]]

# paddingとmargin

![[Pasted image 20250825160439.png]]

margin: 1px 1px 1px 1px;
時計回りに、top、right、bottom、leftの順番となる

# お問い合わせフォームを作ろう

``` html
フォームのレイアウト
<input>
<textarea>
送信ボタン
<input type="submit">
<input type="submit" value="保存">
複数のセレクタに同じCSSを指定
input, textarea {
    border: 3px;
}
```