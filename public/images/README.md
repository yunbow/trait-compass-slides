# スクリーンショットの置き場所

`trait-compass 提出用プレゼン資料...md` §3.6 の手順（Chrome DevTools の Device Toolbar を 1600×900px に設定し「Capture screenshot」）で撮影した本番画面のPNGをここに置く。

必要な3枚（本番URL: `https://trait-compass.trait-compass.workers.dev` で撮影すること。ローカル開発環境のダミーデータは使わない）:

- `result.png` — キャプチャ① 結果画面（`RadarChart` + `TagOverlapSummary`）
- `support-map.png` — キャプチャ② 窓口マッチング地図（`FacilityMapSection`、`popupVariant: full`、ピンが複数立つ区市町村で撮影）
- `consent.png` — キャプチャ③ AI解説の送信前プレビュー（`ConsentPreviewBox`。撮影前にVertex AIの実応答を一度確認してから、送信前プレビュー自体を撮る）

あれば追加:

- `data-sources.png` — `/data-sources` ページ（スライド③のデータ透明性セクション用）

配置後、`slides.md` の該当する `<BrowserFrame>` に `src="/images/xxxx.png"` を追加する（画像が無い間はプレースホルダー枠が表示される）。
