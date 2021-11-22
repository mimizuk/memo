# 見出し１ Markdownっていうすごいやつ
**手間をかけたくないけどメモ帳とかワードはちょっと…みたいな時にべんり**
マークダウンはHTMLとかと同じマークアップ言語のひとつ。    
HTMLほど器用じゃないけど書くのが楽でわりと綺麗に整う。  
配布されてる拡張機能を使えばhtml変換とかもできちゃうすぐれもの。    
CSSが使えるから見た目は多分そこそこ好きにいじれる。

使ってるエディタはマイクロソフトのVSCode。サクサクうごく。

**:exclamation:ちなみにこのページは一部表示でIE非対応です:exclamation:**  
あっ:exclamation:そう、絵文字も使えます:relaxed::clap::tada:

↑はこう↓書いてる
```markdwon
**:exclamation:ちなみにこのページはIE非対応です:exclamation:**
あっ:exclamation:そう、絵文字も使えます:relaxed::clap::tada:
```
[対応絵文字一覧](https://www.webpagefx.com/tools/emoji-cheat-sheet/)

1. 導入済み拡張機能   
    <details>

    * **Markdown PDF**  
    mdファイル(Markdwonで書いたファイルの拡張子)を指定した拡張子のファイルに変換してくれるすごいやつ
    * **Auto-Open Markdown Preview**    
    VScode起動したときにmdファイル開いてたらプレビュー画面も自動で開いてくれるやつ（たぶん）
    * **Japaneseなんちゃら**    
    たぶんVScodeを日本語化するやつ
    </details>

2. 番号リスト
    <details>

    * リスト
    * リスト
    </details>
<br>

## 見出し２ Markdownのあれこれ

### 見出し３　Markdown PDF用の設定値
User Settingsに書く
```json
{
    // .mdファイルを保存すると同時にhtmlとかPDFを自動で生成してくれる
    "markdown-pdf.convertOnSave": true,
    // 編集中のファイルを相対パスの起点にする
    "markdown-pdf.outputDirectoryRelativePathFile": true,
    // 改行を有効にする
    "markdown-pdf.breaks": true,
    // Markdown-pdf.typeで指定したファイルの生成先
    "markdown-pdf.outputDirectory": "D:\\software\\01_TextEditor\\VSCode\\html",
    // ここで指定した拡張子のファイルが生成される
    "markdown-pdf.type": [
        "html"
    ],
    // 作ったファイルに適用するスタイルシート指定　cssは手作りするか誰かのもらってきて
    "markdown-pdf.styles": [
        "D:\\software\\01_TextEditor\\VSCode\\css"
    ],
    // シンタックスハイライトのスタイルシート指定　
    "markdown-pdf.highlightStyle": "atelier-dune-light.css",
    // よくわからんけどMarkdown PDFが拡張子の変換に使うらしい
    "markdown-pdf.executablePath": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
}
```
シンタックスハイライトのは適用例が見れるサイトあるからそこで探すとはかどる。    
→ [highlight.js demo](https://highlightjs.org/static/demo/)

### <a id="css">cssの中身とか</a>
<details>

```css
/* 全部に適用 */
* {
    font-family: "メイリオ" ;
}

/* --- gridレイアウト ここから--- */
/* bodyをgridのコンテナとして使うよ*/
body {
    background: burlywood;
    display: grid;
    grid-auto-rows: 150px 1fr 50px ;    /*上から150pxの枠、残りスペース枠、50px枠用意する*/
    grid-template-columns: 200px 1fr;   /*左から200pxの枠、50px枠、残りスペース枠用意する*/
    grid-template-areas:                /*コンテナ上のアイテム配置指定 . のところはアイテム無し */
        "header header"
        "nav    main  "
        ".      footer";
}

/* 以下gridアイテム */
/* ヘッダ */
.header {
    grid-area: header;
    display:flex;               /*フレックスコンテナに指定*/
    justify-content: center;    /*中身の配置場所*/
    background: rgba(172, 89, 51, 0.644);
    padding: 20px;              /*内側領域*/
    margin: 10px 0;             /*外側領域*/
    border-radius: 10px;        /*角丸*/
}

/* メイン　いろいろ書いてあるところ */
.main {
    grid-area: main;
    background: snow;
    justify-content: center;
    padding: 2em;
    border-radius: 10px;
}

/* ナビゲーションバー　左側にあるやつ */
.nav {
    grid-area: nav;
    background: rgba(165, 42, 42, 0.801);
    padding: 10px 15px;
    margin-right: 10px;
    border-radius: 10px;
}

/* フッタ */
.footer {
    grid-area: footer;
    display:flex;
    justify-content: left;
    padding:2px 20px;
}
/* ---ここまで--- */

/* ---見出しカスタム ここから--- */
/* ヘッダ内のh1装飾 */
.header > h1 {
    font-family: "游ゴシック" ;
    display:flex;
    justify-content: center;
    font-size: 2.7em;
    border-bottom: dashed 2px #010101;
}

/* main内のh1装飾 */
.main > h1 {
    font-family: "游ゴシック" ;
    padding: 0.5em;/*文字周りの余白*/
    color: #010101;/*文字色*/
    background: rgb(252, 242, 231);/*背景色*/
    border-bottom: solid 3px rgba(165, 42, 42, 0.801);/*下線*/
    border-radius: 0.5em;/*角丸*/
}

h1::first-letter {
    font-size: 1.5em;/* h1の一文字目を大きく */
}

h2 {
    font-family: "游ゴシック" ;
    padding: 0.25em;/*文字周りの余白*/
    border-bottom: dotted 5px rgba(172, 89, 51, 0.644);/*線の種類（点線）太さ 色*/
}

h3 {
    font-family: "游ゴシック" ;
    padding: 0.25em 0.5em;/*上下 左右の余白*/
    color: #494949;/*文字色*/
    background: transparent;/*背景透明に*/
    border-left: solid 5px rgba(172, 89, 51, 0.644);/*左線*/
}
/* ---ここまで--- */

/* 水平線カスタム */
hr {
    border:none;
    border-top: 3px dashed rgba(172, 89, 51, 0.644);
  }

/* リンク色カスタム */
a {color: black;}
a:link { color: burlywood; }/*未訪問のリンク*/
a:visited { color: burlywood; }/*訪問済みリンク*/
a:hover { color: rgb(94, 22, 0); }/*ポイント時のリンク*/
a:active { color: #ff8000; }/*選択中のリンク*/

/* 引用文色カスタム */
blockquote {
    border-left: solid 5px rgba(172, 89, 51, 0.644);/*左線*/
}

/* 段落下げ */
.main > p, details, pre, table, blockquote{
    margin-left: 1em;
}
```
CSSでgridレイアウトにするとき、以下の箇所を揃えること。 
これがアイテム名になる。

* コンテナ部分にあたるセレクタ`body`のプロパティ：`grid-template-areas`の中で配置指定に使う値
* アイテム部分にあたるセレクタ：`.header`の部分
* 上記セレクタのプロパティ：`grid-area`の値

</details>

---
↓CSSで用意したgridのアイテムをマークダウンで使う時↓
```markdown
<!-- mainとかheaderがアイテム名 -->
　:::header
　内容物
　:::
　:::footer
　内容物
　:::
　:::main
　内容物
　:::
```
みたいな感じ

### <a id="how_to_write">記法についてとか</a>
1. **URL張り付け**  
    *HTMLの場合
    ```html
    <a href="URL">表示文字列</a>
    ```
    
    *Markdownの場合
    ```markdown
    [表示文字列](URL)
    ```

    *ただし、ローカルフォルダのパスをリンクする場合はHTML形式で書く
    ```html
    <a href="D:\\">Dドライブ</a>
    ```
    <a href="D:\\">Dドライブ</a>    
    ちなみに、Windowsとかのフォルダパス区切りに使われているバックスラッシュ「`\`(￥)」は、いろいろあって一つだと上手く動かないので、手前にもう一つ`\`を記入してエスケープすること。  

2. **表**
    ```markdown
    |No|ゲーム|映画|  
    |:-:|:-:|:-:|
    |1|Metro|シンゴジ|
    |2|Titanfall|バトルシップ|
    |3|Splatoon|トランスフォーマー|
    |4|Fallout|パシフィックリム|
    |5|Wolfenstein|ワイルドスピード|
    ```

    |No|ゲーム|映画|  
    |:-:|:-:|:-:|
    |1|Metro|シンゴジ|
    |2|Titanfall|バトルシップ|
    |3|Splatoon|トランスフォーマー|
    |4|Fallout|パシフィックリム|
    |5|Wolfenstein|ワイルドスピード|

3. **引用**
    ```markdown
    >引用とか
    >>二重引用とか
    ```

    >引用とか
    >>二重引用とか

<br>

### <a id="reference">参考にしたページ<a/>
[vscode-markdown-pdf/README.ja.md](https://github.com/yzane/vscode-markdown-pdf/blob/master/README.ja.md)(Markdown PDFはとりあえずここ読めばわかる)
[CSS Grid Layout を極める！（基礎編）](https://qiita.com/kura07/items/e633b35e33e43240d363)
[[Reveal.js] CSS Grid Layout](https://qiita.com/vimyum/items/a8377a76dac101024ae2)
[css border-rediusで角丸](https://www.webcreatorbox.com/tech/border-radius)
[css 見出し例](https://saruwakakun.com/html-css/reference/h-design)
[GitHubでWebサイトを公開する](https://qiita.com/kouh/items/1f5d93c85871ed6cd26e)
[GitHubのmasterブランチをWebページとして公開する手順（GitHub Pages）](https://qiita.com/tonkotsuboy_com/items/f98667b89228b98bc096)
[【git】git pushがrejectされたときの対応方法](https://www.softel.co.jp/blogs/tech/archives/3569)
[git pullを使ってリモートリポジトリと同期する方法【初心者向け】](https://techacademy.jp/magazine/10274)
<br>

githubにaddしたりcommitしたりpushするときは、ローカルリポジトリに指定した場所で行うこと。   
