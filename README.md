  
#### 開発メモ
[サンプル動画](https://user-images.githubusercontent.com/40127279/126054855-eeafbedd-424e-4c55-ab95-e5e40d7f9443.mp4)
ワークフロー
<BR><img width="600" src="https://user-images.githubusercontent.com/40127279/127757593-1d2e5973-0fa3-461a-a40c-50384ba07e9d.png">
  
<BR>Lesson7などのパース系ワークフローから派生して作成しています

### 1.四字熟語のサイトを探す
　実は、この題材となるサイトをさがす作業が一番苦労します
<br>　ランダム表示するのは母数が1000個程度は欲しいのですが、1ページでこれだけの数の
<br>　情報を持っているものはなかなかありません。
<br>　で、見つけたのが[このサイト](https://yattoke.com/2018/08/28/1g-yojijyukugo/)
<br>　
<br>　このHPは四字熟語が、表になっています。
<br>　HTMLをみるとシンプルにtrタグのなかに4つのtdタグがあるだけですね
### 2.HTMLをパースして、必要な情報を取り出す
　4つのタグの中身は下記の通り
<br>　　1つ目のtdは通番
<br>　　2つ目のtdは四字熟語
<br>　　3つ目のtdは四字熟語のふりがな
<br>　　4つ目のtdは四字熟語の意味
<br>
<br>　上記tdタグを配列に格納し、数字でコントロールするだけで上手くいきそうですね
<br>　4つのtdが1組なので、四字熟語の件数(下のmax)はtdタグの総数を4で割ればわかります
```
　max=$((${#td[@]}/4))
```
<br>　その中からランダムに9件抽出します
<br>　下のコードは1からmaxまで並べて、シャッフルして、頭の9件を配列ixに格納します　
<br>　簡単ですね
```
　ix=(`seq 1 $max|shuf|head -n 9`)
```
### 3.JSON出力フォーマットのXMLを作成する
　せっかく通番があるので、uidも使いましたが、特になくてもOKです
<br>　titleは、『漢字の四字熟語：その四字熟語のふりがな』としました
<br>　subtitleにはその四字熟語の意味
<br>　linkは、四字熟語として、後続フローでデフォルトブラウザでの検索につなげています
<br>
<br>　<img width="600" src="https://user-images.githubusercontent.com/40127279/127757628-878dea45-b984-4fca-9d72-071f734199ec.png">
 
#### 背景
　 Lesson16『トリビアの泉のランダム表示』を作成したときに、四字熟語のランダム表示
<br>　思いつき作りました。
#### 取扱説明
### 機能:
　難読四字熟語を表示する
<br>　
### インストール:
　1.[Alfredworkflow](https://github.com/KitanoTamotsu/4ji/releases/download/1.0/4ji.alfredworkflow.zip)をダウンロード 
<br>　2.ファイルをダブルクリックしてワークフローに登録
### 使い方:
　キーワード『4ji』を入力するとランダムに難読四字熟語が表示されます
<br>
<br>
[トップページに戻る](https://kitanotamotsu.github.io/)
