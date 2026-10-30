# LINK/PAD — 矢野 乃梨佳 Portfolio

液タブの画面を操作して作品を見るポートフォリオサイト。

## 開き方
VS Code でこのフォルダを開き、拡張機能「Live Server」で `index.html` を右クリック →「Open with Live Server」。
（ダブルクリックで直接開いても動きますが、スポイトだけは Live Server か公開後でないと使えません）

## ファイル構成
```
index.html
css/style.css
js/works.js   ← 作品の情報・プロフィール（ここを編集）
js/meta.js    ← 自動生成（サイズ・コマ数・カラーパレット）
js/main.js    ← 動きのプログラム
assets/works/ ← 作品画像（.webp）・アニメ（.mp4）・サムネイル
assets/sfx/   ← 効果音（clic / clic2 / window / kdouonn）
assets/profile/aikon.jpg ← プロフィールのアイコン
```

## 作品の情報を書く
`js/works.js` の各作品に `year` `tool` `role` `time` `song` `desc` `tags` を足すと、
作品を開いたときの情報カードと右パネルに表示されます（空欄の項目は出ません）。

```js
{ id: "okusuri", title: "おくすり飲んで寝よう", type: "anim", cat: "2D Animation",
  year: "2026", tool: "CLIP STUDIO PAINT", time: "約1週間",
  desc: "ここに解説。\n改行もできます。", tags: ["アニメーション", "オリジナル"] },
```

## 作品を追加する
- 静止画：`assets/works/作品id.webp` と `作品id_thumb.webp`（幅480px程度）
- アニメ：`作品id.mp4`・`作品id_poster.webp`（1コマ目）・`作品id_thumb.webp`
  GIFは重いのでMP4にしてください（今回のGIFも MP4 に変換済み：おくすり 89MB → 5.4MB）
- `js/works.js` の `WORKS` に1行追加。`js/meta.js` にサイズ・コマ数・パレットを足すと情報欄に出ます

## 効果音
音量は `js/main.js` の `const VOL = { clic: 0.55, window: 0.28, boot: 0.85 }` で調整できます（0〜1）。
画面右上の ♪ で閲覧者がオン／オフできます。

## 並び順
サイト上でレイヤーの行をドラッグ（スマホはサムネを長押し）、または ▲▼ で入れ替えられます。
入れ替えた順はそのブラウザに保存されます。公開版の順番にしたいときは
レイヤー欄の「⋯」→「並び順をコピー」→ `works.js` の `const ORDER = [];` の行と置き換え。

## GitHub Pages で公開
このフォルダの中身をリポジトリに push → Settings → Pages → Branch: `main` / root。
