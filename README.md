# PINK INDEX

イラストのポートフォリオです。HTML が1枚あれば動きます。
サーバも、ビルドも、インストールも要りません。

## 見る

<https://irowangyue202-blip.github.io/pink-index/>

`index.html` をダウンロードしてダブルクリックしても、同じように開きます。

## 中身

| ファイル | 役割 |
| --- | --- |
| `index.html` | 公開ページ。HOME と WORKS。上のバーは **WORKS** の1項目 |
| `studio.html` | 編集用。作品の登録、HOME の組み立て、サイト内の文字の編集 |

公開ページには編集画面への入口がありません。編集は `studio.html` を
自分で開いたときだけできます。

HOME は キービジュアル → FEATURE → DETAILS → SELECTED → SPOTLIGHT の
順に並びます。中身は登録した作品と、キービジュアルに使った絵から拾います。

## 編集する

1. `studio.html` を開く
2. 作品を登録する（画像・題名・説明・分類・タグ・公開範囲）
3. HOME で、区画ごとに「どれを・どの形で見せるか」を決める
4. キービジュアルの文字は、つかんで動かす。位置のほかに、大きさ・字間・
   行間・傾き・縦書き・敷きも1枚ずつ決められる

## 公開ページに反映する

`studio.html` の **「index.html を書き出す」** を押すと、いまの内容を
同梱した公開ページが手に入ります。この `index.html` を差し替えれば、
見に来た人にも同じ内容が出ます。

編集した内容は、ふだんはブラウザの中だけに残ります。別の端末へ移すときは
`site-data.json` を書き出して、向こうで読み込みます。

## 公開範囲

作品には3つの状態があります。登録しただけでは公開されません。

- `DRAFT` — 下書き。自分だけが見る
- `PRIVATE` — 非公開。手元には残るが公開ページには出ない
- `PUBLIC` — 公開。WORKS と HOME に出る

## 作りかた

このファイルは <https://github.com/irowangyue202-blip/-> の
`apps/pink-index/` から書き出しています。

```
node tools/build.mjs          # 通常版（dist/）
node tools/build-single.mjs   # 1ファイル版（dist-single/）
node --test test/*.test.mjs   # 単体テスト
node tools/check-links.mjs    # リンク検査
node tools/check-layout.mjs   # 重なり・はみ出し検査
```

`dist-single/pink-index.html` を `index.html`、
`dist-single/pink-index-studio.html` を `studio.html` として置きます。
公開ページの名前が変わるので、`studio.html` の中の
`window.PINK_PUBLIC` を `"index.html"` に書き換えます。

外部の部品は使っていません。広告も、外部への通信もありません。
