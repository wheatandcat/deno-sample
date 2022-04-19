---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
title: Denoの紹介
layout: intro
colorSchema: 'light'
---

# Denoの紹介

<div class="flex justify-center">
  <img
    class="w-50 pt-2"
    src="/logo.svg"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

<div class="flex pb-5">
  <div class="px-5">
    <div class="rounded-full bg-white w-30 h-30 overflow-hidden border-2 border-black border-dotted border-opacity-20">
      <img
        class="w-40 pt-2"
        src="/account.png"
      />
    </div>
  </div>
  <div class="mt-6">
    <h2>自己紹介</h2>
  </div>
</div>
<br />

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat)）
- 🏢 フリーランスエンジニア（シェアフル株式会社CTO）
- 💻 Blog: https://www.wheatandcat.me/
- 📚 Booth: https://wheatandcat.booth.pm/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [ペペロミア](https://peperomia.app/)
  - [Atomic Design Check List](https://atomic-design-checklist.vercel.app/)


<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  color: #696969;
  @apply font-500;
  font-size:1.25rem;
}
</style>

---

# Denoとは？ 

<br/>

 - V8 JavaScriptエンジンをベースに実装されたJavaScript/TypeScriptランタイム
 - [**DenoはNode.jsの反省から生まれた**](https://news.mynavi.jp/techplus/article/programinglanguageoftheworld-34/) を修正すべく、Node.jsの開発者を中心に開発が行われている




<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-500;
  font-size:1.25rem;
}
</style>
---
clicks: 2
---

# Denoの特徴

 - 主な特徴は以下が挙げられる
   - **TypeScript**を標準でサポート
   - パーミッションシステム
   - 生産性
   - Web標準への準拠
   - **ES Modulesベース**のモジュールシステム
   - 最新のJavaScript仕様に準拠

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-500;
  font-size:1.25rem;
}
</style>


---

# サンプルを作ってみる

<br/>

以下のチュートリアルをベースに、どんな感じで実装するのか試してみる。

- [Deno チュートリアル](https://deno.land/manual)


<style>
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---
clicks: 3
---

# インストール & 実行

<br/>
Macなら以下のコマンドを実行

```bash
$ brew install deno
```

<div v-click="1">

<div class="mt-6">DenoはURLから直接ファイルを実行できるので、以下のコマンドで実行可能</div>

```bash
$ deno run https://deno.land/std@0.135.0/examples/welcome.ts 

Welcome to Deno!
```

</div>

<br/>
<div v-click="2">

実行ファイルは、[こちら](https://deno.land/std@0.135.0/examples/welcome.ts)

</div>

<style>
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
</style>

---

# スクリプト実行方法
<br/>

Denoでは以下のようなスクリプトの実行をサポートしている。

```bash
$ deno run main.ts
$ deno run https://mydomain.com/main.ts
$ cat main.ts | deno run -
```

---

# パーミッション
<br/>

Denoはファイル実行時の安全性を確保するため、デフォルトでは以下を禁止している
 - ファイルの読み込み/書き込み
 - ネットワークアクセス
 - 環境変数の取得
 - 外部コマンド実行
 - プラグインの読み込み


```bash
$ deno run --allow-net net_client.ts
$ deno run --allow-read net_client.ts
$ deno run --allow-net net_client.ts
$ deno run --allow-net=example.com net_client.ts
$ deno run --allow-env net_client.ts
```

---

# コマンドラインの紹介①
<br/>

Denoでは標準で多くのコマンドをサポートしているので紹介

### ■ lint & fmt

```bash
$ deno lint ./
$ deno fmt ./
```

<br/>
<br/>

### ■ test

```bash
$ deno test
$ deno test --coverage=cov_profile
```

---

# コマンドラインの紹介②
<br/>

### ■ Watch mode
修正ファイルをすれば自動で再起動

```bash
$ deno run --watch main.ts
$ deno test --watch
$ deno fmt --watch
```

<br/>
<br/>

### ■ bundle
依存する複数のファイルを1つのjsファイルにして出力する。

```bash
$ deno bundle https://deno.land/std@0.83.0/examples/colors.ts colors.bundle.js
```

---

# コマンドラインの紹介③
<br/>

### ■ ドキュメント出力
JSDocを元にドキュメント出力

```bash
$ deno doc
```

<br/>
<br/>

### ■ break pointを使用


```bash
$ deno run --inspect-brk --allow-read --allow-net https://deno.land/std@0.135.0/http/file_server.ts
```

上記を実行してChromeで以下のURLにアクセスする。

```
chrome://inspect
```

---

# コマンドラインの紹介の補足
<br/>

紹介したCLTツールの詳細は以下で確認できる
 - [Deno Contributing](https://deno.land/manual/contributing#deno_doc)

---

# Lifecycle Event ①

<br/>

Denoはブラウザ互換のライフサイクルイベントをサポートしている。

■ main.ts
```js
const handler = (e: Event): void => {
  console.log(`got ${e.type} event in event handler (main)`);
};

window.addEventListener("load", handler);
window.addEventListener("unload", handler);

window.onload = (e: Event): void => {
  console.log(`got ${e.type} event in onload function (main)`);
};
window.onunload = (e: Event): void => {
  console.log(`got ${e.type} event in onunload function (main)`);
};

console.log("log from main script");
```

<style>
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
</style>

---


# Lifecycle Event ②


コマンドを実行した結果は以下の通り。

```bash
$ deno run main.ts
log from main script
got load event in onload function (main)
got load event in event handler (main)
got unload event in onunload function (main)
got unload event in event handler (main)
```
---

# 試しにAPIを作ってみる

```js
import { Application, Router, RouterContext } from "https://deno.land/x/oak@v6.5.0/mod.ts";

const app = new Application();
const router = new Router();

app.addEventListener("listen", ({ hostname, port, secure }) => {
  console.log(
    `Listening on: ${secure ? "https://" : "http://"}${hostname ??
      "localhost"}:${port}`,
  );
});
app.addEventListener("error", (evt) => {
  console.log(evt.error);
});
router.get('/', (ctx: RouterContext) => {
  ctx.response.body = "Hello World!";
})
app.use(router.routes());
app.use(router.allowedMethods());

await app.listen({ port: 8001 });
```

<style>
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
</style>

---

# 試しにReactを使ってみる

```jsx
import { listenAndServe } from "https://deno.land/std@0.99.0/http/mod.ts";
import React from "https://jspm.dev/react@17.0.2";
import ReactDOMServer from "https://jspm.dev/react-dom@17.0.2/server";
function App() {
  return <div>Hello SSR</div>;
}
listenAndServe({ port: 8080 }, (req) => {
  req.respond({
    status: 200,
    headers: new Headers({
      "Content-Type": "text/html",
    }),
    body: ReactDOMServer.renderToString(
      <html>
        <head></head>
        <body>
          <div id="app">
            <App />
          </div>
        </body>
      </html>
    ),
  });
});
```

<style>
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
</style>

---

# Denoでのサードパーティの扱い

<br/>

Denoでは以下のサイトで公開されているパッケージに関して問題なく使用可能
 - https://deno.land/x

既存のnpmは以下のレジストリを経由してインストール可能
 - https://esm.sh/
 - https://jspm.org/
 
<br/>

ただし、上記が以下の使用してNode.js→Denoに変換しているので、**ポリフィルが未サポートのものを使用しているとエラーになるので注意**
 - https://deno.land/std@0.106.0/node#supported-modules

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  color: #696969;
  @apply font-500;
  font-size:1.25rem;
}
</style>

---


# まとめ

<br/>
 - Denoの標準でサポートしている内容が多く、基礎的な部分では標準だけでやっていけそう。
 - 高い柔軟性とセキュリティの両方が考慮した設計になっている。
 - バックエンドとフロンドを、両方共いい感じに実装できる感はある。
 - 既存のnpmの資産がどこまで流用できるのかで、実際に使用していくかが決まりそう。この辺は、まだ調査不足なのでもう少し実装してみて確認してみる予定。


<style>
a {
  color: #84b9cb;
  @apply font-500;
}
p {
  line-height: 1.6em;
}
</style>

---
layout: center
class: "text-center"
---

<div class="text-2xl font-700 text-enter w-full">
  <div>ご清聴ありがとうございました</div>
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>


