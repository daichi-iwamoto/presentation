---
marp: true
---

<!-- Global CSS -->
<style>
  section h1 {
    color: #588496;
    margin-bottom: 45px;
  }
  section h2 {
    margin-bottom: 45px;
  }
  section strong {
    color: #ff6487;
  }
  section p {
    margin-bottom: 30px;
  }
</style>

<!-- Scoped CSS -->
<style scoped>
  section {
    padding: 0;
  }
  section p {
    margin: 0;
  }
  section img {
    margin: 0;
    padding: 0;
    position: absolute;
    left: 5%;
    top: 0;
    bottom: 0;
    width: 40%;
    margin: auto 0;
  }
  section h1 {
    margin-top: 0;
    padding: 0;
    margin-left: 50%;
    width: 50%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #588496;
    color: #fefefe;
  }
</style>

![logo](./img/node-logo.svg)
# Node.js 入門

---

<style Scoped>
  section {
    background-color: #588496;
  }
  section h1 {
    font-size: 62px;
    text-align: center;
    color: #fff;
  }
</style>
# そもそもNode.jsとは何ぞや🤔？

---
# Node.jsとは
 
ざっくり説明すると、**サーバーサイドで動作する`JavaScript`です。**

言葉で聞いてもピンと来ないと思うので実際に動かしてみましょう。

---

# 手順

* コンソールに`test`を出力するだけの`js`を作成する。
* エクスプローラー等から`js`ファイルをクリックして実行 → **Error**
* コマンドラインから、`Node.js`を経由して`js`実行 → **`test`が出力される。**

---

# 詳細説明

素の`js`はブラウザ上（クライアントサイド）では動作しますが、
ローカルOSやサーバー上では動作しません。

しかし、`Node.js`を介して`js`を実行する事で、
本来クライアントサイドでしか動作しない`js`を
サーバーサイド（バックエンド）でも使用できるようになります。

慣れ親しんだ`js`でバックエンドの処理もかける事から、
フロントエンドエンジニアを中心に人気が高まったようです。

---

# npm

次に、`Node.js`で使用される**パッケージ管理システム**
`npm`について見ていきましょう！

モジュールは依存関係を持っている事が多く、
「モジュールAを使用するためにはモジュールBが必要で
そのモジュールBを使用するためにはモジュールCが～…」
みたいなことが頻繁に起きます😭

`npm`はこのような事件を解決してモジュールAをインストールする。
と実行するだけでそのモジュールを実行するために必要なモジュールを
併せてインストールしてきてくれます。

こちらもまずは実際に動かしてみましょう。

---
<style Scoped>
  section {
    background-color: #588496;
  }
  section h1 {
    color: #fff;
    font-size: 62px;
    margin: 0;
  }
  section p {
    color: #c0cace;
  }
</style>
# npm ハンズオン 1

環境構築・基礎的な使用方法

---

## テスト用ディレクトリ作成

まず適当テスト用のディレクトリ作成して、
該当のディレクトリに移動・下記コマンドを実行しましょう。

```bash
# 移動
cd test

# npm（色々聞かれますが一旦全てEnterで大丈夫です）
npm init
```

すると`package.json`というファイルが出現すると思います。

---

## package.jsonの編集

作成された`package.json`の中に`scripts`という箇所があるので、
その箇所を下記の様に書き換えてください。

```json
"scripts": {
  "test": "echo hello world !"
}
```

---

## コマンド実行

この状態で下記コマンドを実行。

```bash
npm run test
```

ターミナル上に`hello world !`と表示されるはずです！

`npm run "スクリプト名"`で、`package.json`で設定した`scripts`が実行できます。

---

上記を踏まえて、
テスト用のディレクトリ直下に`test.js`というファイルを作成して、
`test2`と出力するだけのスクリプトを作成しましょう。

そして、`package.json`の`scripts`を下記の様に編集してください。
```json
"scripts": {
  "test": "echo hello world !",
  "test2": "node test.js"
}
```

---

そして下記コマンドを実行。

```bash
npm run test2
```

すると、コマンドラインに`test2`と出力されるはずです！

これが基本的な`npm-scripts`の実行方法です。

---

# ここまでの詳細説明

最初に実行した`npm init`は、`npm`の初期化処理を行うコマンドで、
`npm init`を行ったディレクトリに`node`の設定ファイルである
`package.json`が作成されます。

`package.json`の`scripts`の箇所には
`node`で実行できるスクリプトを指定しておくことができます。

---

`node`には便利なモジュール（パッケージ）が沢山あります。

下記は人気のパッケージを紹介しているページです。
https://github.com/sindresorhus/awesome#readme

`npm`は**パッケージ管理システム**。
先程までのハンズオンは、環境構築と基礎的な使用方法になりますが、
次は、実際に`npm`でモジュール（パッケージ）を使用してみましょう！

---
<style Scoped>
  section {
    background-color: #588496;
  }
  section h1 {
    color: #fff;
    font-size: 62px;
    margin: 0;
  }
  section p {
    color: #c0cace;
  }
</style>

# npm ハンズオン 2

モジュールの使用

---

# ハンズオン説明

今回、紹介するモジュールは下記~~の3つ~~

| module name | description |
| --- | --- |
| [pokemon](https://www.npmjs.com/package/pokemon) | ポケモンの名前を出力してくれる |
| ~~[onchange](https://www.npmjs.com/package/onchange)~~ | ~~ファイルの変更を検知してくれる~~ |
| ~~[browser-sync](https://www.npmjs.com/package/browser-sync)~~ | ~~仮想サーバを起動し、ファイルの変更を検知し、<br>ブラウザを自動更新してくれる~~ |

> ※ 時間の関係で省略

では、それぞれの使い方を見てみましょう。

---
<style Scoped>
  section {
    background-color: #588496;
  }
  section h1 {
    color: #fff;
    font-size: 62px;
    margin: 0;
  }
  section p {
    color: #c0cace;
  }
</style>
# pokemon モジュールの使用

ポケモンの名前を出力しよう！

---

## pokemon のインストール

まずは`pokemon`モジュールのインストールを行いましょう！
今回作成したテスト用のディレクトリ（`npm init`済み）で、
下記コマンドを入力してください。

```bash
# npm install pokemon でも可 
npm i pokemon
```

これでモジュールのインストールができます。

---

## package.json の確認

`package.json`を開いてみましょう。すると、
`dependencies`の箇所に`pokemon`が追加されていると思います。

ここにモジュール名が追加されることで、この`package.json`さえ
`git`等で共有しておけば、共有された側は`package.json`がある
ディレクトリで、`npm install`を行う事で`dependencies`に記載された
モジュールを全てインストールすることができます！

---

## package-lock.json

モジュールのインストール時に作成される`package-lock.json`ファイル

こちらは、インストールしたモジュールの詳細なバージョンや、
参照元が記載されています。`package-lock.json`が存在する場合は
そこに記載されているバージョンのモジュールがインストールされる為、
インストール時にエラーが出るときはこの`lock`ファイルを削除すると
上手くいくことも多々あります。

`git`等でバージョン管理をされている場合は、
特別な理由が無ければ管理対象から外しておきましょう。

---

## node_modules

モジュールインストール時に作成される`node_modules`
ここにはインストールしたモジュールのソースコードが保存されています。

今回、インストールしたのは`pokemon`モジュールのみですが
実際`node_modules`を確認すると、`pokemon`以外にも
幾つかモジュールがインストールされていると思います。

---

## node_modules

`node_modules`の中を見てみると、実際にモジュールがどのように作成されているかも
分かります。`pokemon`モジュールは公式でも述べられている通り、
ポケモンの配列データと、それを幾つかの形式で出力する
関数があるだけの簡単な内容になってますね！

`node_modules`は多種多様なモジュールのソースコードが保存されている為、
容量・ファイル数が膨大になる事が多いです。
`git`等でバージョン管理をされている場合は、
特別な理由が無ければ管理対象から外しておきましょう。

---

## pokemon モジュールの使用
では、ここからは実際に`pokemon`モジュールを使用してみましょう！
npmの[使用方法](https://www.npmjs.com/package/pokemon#usage)の箇所を参考に行っていきましょう。

どうやら`pokemon`モジュールは、`js`内で呼び出して使用するようです。
実際に`js`ファイルを作成して試してみましょう。

--- 

## pokemonを使用する

先程の使い方のページを見てみると、どうやらランダムでポケモンを出力する関数が
存在しており、さらに引数で言語指定もできるようです。

今回使用しているディレクトリ直下に、`pokemon.js`を作成し下記を記載してください。

```js
// モジュールの読み込み
const pokemon = require('pokemon')

// ランダムでポケモンを出力
let name = pokemon.random('ja')
console.log(name)
```

これでポケモンがランダムに出現する機能が作成されました。

---

## jsの実行

機能が実装できた所で、実際に事項の方を行っていきましょう！
`node pokemon.js`コマンドで実行もできるのですが、
基本的には`npm-scripts`経由で実行する事が推奨されているので、
`package.json`に`scripts`を書いていきましょう。

```json
"scripts": {
  "test": "echo hello world !",
  "test2": "node test.js",
  "pokemon": "node pokemon.js"
}
```

---

そして下記コマンドを実行！

```json
npm run pokemon
```

すると実際にポケモンの名前がランダムに出力されます！

---

<style Scoped>
  section {
    background-color: #588496;
  }
  section h1 {
    color: #fff;
    text-align: center;
    font-size: 82px;
    letter-spacing: 50px;
  }
</style>
# まとめ

---

## まとめ

今回ご説明した重要な単語は、下記の通りです。

| word | description |
| --- | --- |
| Node.js | サーバーサイドで実行できる`js`環境 |
| npm | Nodeのパッケージ管理システム |
| package.json | `node`, `npm`の設定ファイル |
| npm-scripts | `package.json`の`scripts`で設定できるコマンド |

---

## まとめ

`pokemon`モジュールはネタ要素が強めですが、他にも
`Sass`の圧縮を行ってくれるモジュールや、
画像の変形・リサイズ・webp化等を行ってくれるモジュール
ハリーポッターのキャラクター名を出力するモジュールなど色々な物があります。

面白そう・便利そうなモジュールを見つけたら是非教えてください！

---

<style Scoped>
  section {
    background-color: #588496;
  }
  section h1 {
    color: #fff;
    text-align: center;
    font-size: 82px;
    letter-spacing: 50px;
  }
</style>
# おわり
