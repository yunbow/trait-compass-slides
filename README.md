# trait-compass-slides

[![Deploy to GitHub Pages](https://github.com/yunbow/trait-compass-slides/actions/workflows/deploy.yml/badge.svg)](https://github.com/yunbow/trait-compass-slides/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

**プレゼン資料:** https://yunbow.github.io/trait-compass-slides/ ｜ **Trait Compassを試す:** https://trait-compass.trait-compass.workers.dev/ ｜ **Trait Compass GitHub:** https://github.com/yunbow/trait-compass

Trait Compass 提出用プレゼン資料（6枚・16:9・1280×720相当）を Slidev + Vue で実装したリポジトリです。「東京都知事杯オープンデータ・ハッカソン2026」への応募作品である trait-compass を、審査員向けに紹介します。

- **trait-compass-slides** — このリポジトリ。プレゼン資料本体（Slidev + Vue）のソースコードを管理しています。
- **trait-compass**（[yunbow/trait-compass](https://github.com/yunbow/trait-compass)） — CivicUnknot が開発しているハッカソン応募作品。実装・データ・詳細設計は上記リポジトリで管理しています。

文言・統計値は Trait Compass 本体リポジトリ（[yunbow/trait-compass](https://github.com/yunbow/trait-compass)）および大会提出用に確認した一次情報を基準としています。

## 技術スタック

Slidev / Vue 3 / CSS

## 開発

```bash
cd app             # アプリケーションディレクトリへ移動
npm install
npm run dev        # http://localhost:3030 でプレビュー（プレゼンターモードは /presenter）
```

## 書き出し

```bash
npm run build       # GitHub Pages 用の静的サイトを生成（app/dist）
npm run export      # PDF書き出し（app/dist/trait-compass.pdf）※提出物
npm run export:pptx # PPTX書き出し
npm run export:png  # スライドごとのPNG書き出し
```

`npm run export` / `export:pptx` / `export:png` は初回実行時に Playwright が Chromium をダウンロードする（`npx playwright install chromium` が必要な場合あり）。

## デプロイ（GitHub Pages）

`main` ブランチへの push をトリガーに `.github/workflows/deploy.yml` が `app/` で `npm run build` を実行し、
`app/dist` を GitHub Pages へ自動デプロイします。ビルド成果物はリポジトリにコミットしません。
GitHub Pages の **Settings → Pages → Build and deployment → Source** は **GitHub Actions** を選択してください。

`npm run build` はプロジェクトサイトのサブパス用に `--base /trait-compass-slides/` を付与しています。リポジトリ名を変更した場合は `app/package.json` の `build` スクリプトも合わせて変更してください。

ローカルで公開ファイルを確認する場合は `cd app && npm run build && npx serve dist` などで確認してください。

## ディレクトリ構成

```text
app/
├── slides.md              # 6枚（表紙／①課題／②デモ／③データ活用+技術力／④プライバシー／⑤社会実装）
├── style.css              # 配色（白背景＋濃紺＋落ち着いた緑）・余白・PDF出力時のレイアウト固定
├── components/
│   ├── MetricCard.vue     # 数字（72px）＋説明＋出典（16px）の統計カード
│   ├── DataFlow.vue       # 処理フロー図（縦: ③、横: ②）
│   └── BrowserFrame.vue   # 実UIスクリーンショットを収めるブラウザ枠（未挿入時はプレースホルダー表示）
├── public/images/         # 画面キャプチャ（本番サイトから取得済み。README参照）
│   ├── result.png         # キャプチャ① 相談分野タグ3件＋レーダーチャートの合成画像（横長）
│   ├── support-map.png    # キャプチャ② 窓口マッチング地図（台東区で撮影）
│   ├── consent.png        # キャプチャ③ AI解説の送信前プレビュー
│   └── data-sources.png   # /data-sources ページ
├── package.json
└── package-lock.json
```

## 画面キャプチャ

`app/public/images/` の4枚は、本番サイト（`https://trait-compass.trait-compass.workers.dev`）をブラウザ自動操作で実際に操作して取得したスクリーンショットで、`slides.md` の各 `<BrowserFrame>` から `src="/images/xxxx.png"` で参照済み。窓口マッチング地図は台東区（ピンが複数立ち、スライド③のデータ透明性セクションと一貫する地域）で撮影した。

提出前に本番データが更新されている場合は、`app/public/images/README.md` の手順（Chrome DevTools の Device Toolbar を1600×900pxに設定し「Capture screenshot」）で撮り直し、同じファイル名で上書きすればよい。画像が無い状態に戻すと自動的に「スクリーンショット未挿入」のプレースホルダー枠が表示される。

## レイアウトを崩さず修正する

- 数値・文言は `MetricCard` の `value` / `label` / `source` props、または各スライドの本文テキストのみを編集する。
- フロー図の文言は `DataFlow` の `:steps` 配列（`text` / `note`）を編集する。
- 配色・余白・フォントは `style.css` の CSS変数（`--tc-navy` / `--tc-green` / 余白値）で一括管理している。
- `canvasWidth: 1280` / `aspectRatio: 16/9`（`slides.md` frontmatter）は変更しない。PDF/PPTX/PNG書き出しは常にこのサイズでレンダリングされるため、画面表示と出力の見た目が一致する。
- スライド内で `v-click` 等のフラグメントアニメーションは使わない（1スライド＝書き出し1ページを保つため）。

## コントリビューション

貢献方法は [CONTRIBUTING.md](./CONTRIBUTING.md) を参照してください。

## セキュリティ

脆弱性の報告方法は [SECURITY.md](./SECURITY.md) を参照してください。

## ライセンス

[MIT License](./LICENSE)
