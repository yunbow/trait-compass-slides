# trait-compass-slides

Trait Compass 提出用プレゼン資料（6枚・16:9・1280×720相当）を Slidev + Vue で実装したリポジトリ。

文言・統計値は `/Users/yun2/Project/hackathon/trait-compass/trait-compass 提出用プレゼン資料（PPT_PDF）・画面キャプチャ下書き（2026-08-20）.md` §2 の確定内容から一字一句変更していない。

## 構成

```
trait-compass-slides/
├── slides.md              # 6枚（表紙／①課題／②デモ／③データ活用+技術力／④プライバシー／⑤社会実装）
├── style.css              # 配色（白背景＋濃紺＋落ち着いた緑）・余白・PDF出力時のレイアウト固定
├── components/
│   ├── MetricCard.vue     # 数字（72px）＋説明＋出典（16px）の統計カード
│   ├── DataFlow.vue       # 処理フロー図（縦: ③、横: ②）
│   └── BrowserFrame.vue   # 実UIスクリーンショットを収めるブラウザ枠（未挿入時はプレースホルダー表示）
└── public/images/         # 画面キャプチャの置き場所（README参照）
```

## セットアップ

```bash
npm install
npm run dev        # http://localhost:3030 でプレビュー（プレゼンターモードは /presenter）
```

## 書き出し

```bash
npm run build       # 静的サイトとしてビルド（dist/）
npm run export      # PDF書き出し（dist/trait-compass.pdf）※提出物
npm run export:pptx # PPTX書き出し
npm run export:png  # スライドごとのPNG書き出し
```

`npm run export` / `export:pptx` / `export:png` は初回実行時に Playwright が Chromium をダウンロードする（`npx playwright install chromium` が必要な場合あり）。

## 画面キャプチャの追加

`public/images/README.md` の手順で撮影したPNGを `public/images/` に置き、`slides.md` 内の該当する `<BrowserFrame>` に `src="/images/xxxx.png"` を追加する。画像未挿入の間は「スクリーンショット未挿入」のプレースホルダー枠が表示される。

## レイアウトを崩さず修正する

- 数値・文言は `MetricCard` の `value` / `label` / `source` props、または各スライドの本文テキストのみを編集する。
- フロー図の文言は `DataFlow` の `:steps` 配列（`text` / `note`）を編集する。
- 配色・余白・フォントは `style.css` の CSS変数（`--tc-navy` / `--tc-green` / 余白値）で一括管理している。
- `canvasWidth: 1280` / `aspectRatio: 16/9`（`slides.md` frontmatter）は変更しない。PDF/PPTX/PNG書き出しは常にこのサイズでレンダリングされるため、画面表示と出力の見た目が一致する。
- スライド内で `v-click` 等のフラグメントアニメーションは使わない（1スライド＝書き出し1ページを保つため）。
