---
theme: default
title: Trait Compass ― 提出用プレゼン
info: false
canvasWidth: 1280
aspectRatio: 16/9
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: none
mdc: false
fonts:
  sans: 'Noto Sans JP'
---

<div class="h-full flex flex-col items-center justify-center text-center">
  <div class="tc-eyebrow">都知事杯2026 ハッカソン提出資料</div>
  <div style="font-size:64px; font-weight:900; color:var(--tc-navy); letter-spacing:0.02em;">Trait Compass</div>
  <div style="font-size:28px; font-weight:700; color:var(--tc-green); margin-top:18px;">気づきと相談のあいだをつなぐ</div>
  <div style="font-size:15px; color:var(--tc-text-muted); margin-top:56px;">デモはこちら：trait-compass.trait-compass.workers.dev</div>
</div>

<!--
表紙スライド。読み上げ原稿はなし(タイトルコールのみ、または無音)。
-->

---

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">課題｜アイデア力</div>
  <div class="tc-title">気づきと相談のあいだに、空白がある。</div>
  <p class="tc-body" style="margin-bottom:28px;">
    「自分は発達障害かもしれない」――そう感じても、次の一歩が分からず立ち止まる人は多い。東京発達障害者支援センター（TOSCA）をはじめとする公的相談窓口は実在するのに、情報は都の広域機関と区市町村とで管理が分かれ、掲載形式もCSV・PDF・ページ本文とばらばらで、たどり着くのは難しい。
  </p>
  <div class="flex gap-8" style="flex:1;">
    <MetricCard value="8.8%" value-sub="（11人に1人）" label="通常学級で「学習面又は行動面で著しい困難」（教員の見立て、診断ではない）" source="文部科学省（2022年）" />
    <MetricCard value="平均2.6か月" value-sub="（最長54か月）" label="専門機関の初診待機" source="厚生労働省 推進事業報告書（2020年、原文PDF確認済み）" />
  </div>
  <div class="tc-note">
    8.8%は医師の診断率ではなく、文部科学省調査における教員の見立てに基づく比率。混同を避けるため「診断」の語は使わない。
  </div>
</div>

<!--
「自分は発達障害かもしれない」――そう感じても、次の一歩が分からず立ち止まる人は少なくありません。文部科学省の調査では、通常学級の児童生徒の8.8パーセント、11人に1人に、学習面や行動面で著しい困難があるとされています。しかし専門機関の初診までの待機期間は平均2.6か月。この「気づき」と「相談」のあいだの空白を、オープンデータとプライバシー保護設計で埋めるサービスを、私たちは作りました。
(目安39秒・196字)
-->

---

<script setup>
const demoFlowSteps = [
  { text: '回答' },
  { text: '相談分野タグ' },
  { text: '窓口' },
]
</script>

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">デモ｜サービスデザイン／オーディエンス</div>
  <div class="tc-title">セルフチェックが、相談分野タグに変わる。</div>
  <p class="tc-body" style="margin-bottom:20px;">
    あらかじめ決められた30問に答えると、結果は10領域のレーダーチャートに加え、診断名ではなく「相談分野タグ」（対人・コミュニケーション、こころ・感情、不注意・段取り、感覚、学習・からだ、こだわりの6分類）で提示される。続けて、未就学児から社会人までの5段階のライフステージと居住区市町村を選ぶだけで、公的相談窓口・施設情報が地図とリストで見つかる。
  </p>
  <div style="margin-bottom:20px;">
    <DataFlow direction="horizontal" :steps="demoFlowSteps" />
  </div>
  <div class="flex gap-6" style="flex:1;">
    <BrowserFrame url="trait-compass.trait-compass.workers.dev/result" src="/images/result.png" caption="キャプチャ① 結果画面（レーダーチャート＋相談分野タグ）" height="150px" />
    <BrowserFrame url="trait-compass.trait-compass.workers.dev/support" src="/images/support-map.png" caption="キャプチャ② 窓口マッチング地図" height="150px" />
  </div>
  <div class="tc-note">
    チェックをしなくても支援情報だけを探すこともできます。
  </div>
</div>

<!--
ブラウザで30の質問に答えると、結果は病名ではなく、レーダーチャートと相談分野タグで示されます。ライフステージと区市町村を選ぶだけで、自分に合う公的相談窓口が地図と一覧で見つかります。チェックをしなくても、窓口だけを探すこともできます。
(目安24秒・118字)
-->

---

<script setup>
const dataSourceFlowSteps = [
  { text: '自治体・公的機関の支援情報\n（CSV／PDF／ページ本文など、形式はばらばら）', note: '取得・ライセンス確認・共通スキーマへ正規化' },
  { text: '共通の支援施設データ', note: 'ライフステージ × 地域 × 相談分野で分類・突合' },
  { text: '条件に合う相談窓口・施設候補を提示' },
  { text: '地図・一覧・相談準備へ' },
]
</script>

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">データ活用＋技術力</div>
  <div class="tc-title" style="margin-bottom:20px;">行政データを、「次の一歩」に変える。</div>
  <div class="flex gap-10" style="flex:1;">
    <div style="flex:1.1;" class="flex flex-col justify-center">
      <DataFlow direction="vertical" :steps="dataSourceFlowSteps" />
    </div>
    <div style="flex:1;" class="flex flex-col gap-3">
      <BrowserFrame url="trait-compass.trait-compass.workers.dev/data-sources" src="/images/data-sources.png" caption="利用しているデータ（/data-sources）" height="130px" />
      <p style="font-size:13px; color:var(--tc-text-muted); line-height:1.7;">
        オープンデータ／標準利用規約データ／個別許諾データに区分し、各データの出典・ライセンス・最終取得日・利用件数を公開。代表例: 台東区のオープンデータ、医療情報ネット（592件）、発達障害情報・支援センター（3件）、WAM NET（3,950件）、複数自治体の個別許諾データ。
      </p>
      <div style="background:var(--tc-green-soft); border-left:4px solid var(--tc-green); padding:10px 14px; font-size:13px; font-weight:700; color:var(--tc-navy);">
        日常の困りごとチェックの結果の算出には、外部データを使用していません。
      </div>
      <div class="flex gap-2" style="font-size:11px; color:var(--tc-text-muted);">
        <span style="border:1px solid var(--tc-border); border-radius:999px; padding:3px 10px;">CKAN API</span>
        <span style="border:1px solid var(--tc-border); border-radius:999px; padding:3px 10px;">Cloudflare Workers・D1・R2</span>
        <span style="border:1px solid var(--tc-border); border-radius:999px; padding:3px 10px;">カテゴリ名のみを送るAI解説</span>
      </div>
    </div>
  </div>
</div>

<!--
窓口情報は、自治体ごとにばらばらな形式のデータを共通のスキーマに正規化し、回答傾向から変換した相談分野タグで横断検索できるようにしました。バラバラなデータをひとつにつなぐこと自体が、私たちの技術です。
(目安20秒・100字)

原稿作成メモ: データセット数・自治体数の具体的な数字は本番データが変動するため口頭では言わない。最新値は画面(データページのキャプチャ・出典クレジット)で示す。実績数字は⑤の締めで一度だけ言及する。
-->

---

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">プライバシー｜サービスデザイン</div>
  <div class="tc-title">診断せず、送信前に確認できる。</div>
  <p class="tc-body" style="margin-bottom:20px;">
    回答はサーバーには送らず、端末（ブラウザ）の中だけで処理・保存する。AIによる解説機能も完全オプトインで、送信前に「送信されるもの（カテゴリ名のみ）」「送信されないもの（回答内容・スコア・年齢・地域）」を必ず確認できる。
  </p>
  <div class="flex gap-8" style="flex:1;">
    <div style="flex:1;">
      <BrowserFrame url="trait-compass.trait-compass.workers.dev/result/prepare" src="/images/consent.png" caption="キャプチャ③ AI解説の送信前プレビュー" height="210px" />
    </div>
    <div style="flex:0 0 240px;" class="flex flex-col gap-3 justify-center">
      <div style="border:1px solid var(--tc-border); border-radius:6px; padding:12px 16px; font-size:14px; font-weight:700; color:var(--tc-navy);">サーバー非送信</div>
      <div style="border:1px solid var(--tc-border); border-radius:6px; padding:12px 16px; font-size:14px; font-weight:700; color:var(--tc-navy);">非診断</div>
      <div style="border:1px solid var(--tc-border); border-radius:6px; padding:12px 16px; font-size:14px; font-weight:700; color:var(--tc-navy);">完全オプトイン</div>
    </div>
  </div>
</div>

<!--
回答はサーバーには送らず、端末の中だけで処理・保存します。AIによる解説機能も完全オプトインで、送信前に内容を必ず確認できます。
(目安13秒・64字)
-->

---

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">社会実装｜ソーシャルインパクト</div>
  <div class="tc-title" style="margin-bottom:20px;">54/62区市町村で、支援情報を掲載。</div>
  <div class="flex gap-10" style="flex:1;">
    <div style="flex:1;" class="flex flex-col justify-center">
      <p class="tc-body">
        症状ラベルではなく、次の一歩へ。すでに東京都62区市町村中54区市町村で相談窓口・施設情報を掲載できる状態まで実装済み（本番稼働中、/outcomesページで公開）。自治体ごとにデータの充足度は異なり、その充足度自体もサービス内で公開している。残る区市町村・データソースへの接続を広げながら、この窓口ナビを東京都の誰もが使える相談の入り口に育てていく。
      </p>
      <p style="font-size:13px; color:var(--tc-text-muted); margin-top:16px; line-height:1.7;">
        実装済みの「統一支援施設スキーマ提案」は、単なる技術文書ではなく、行政のデータ公開実務そのものへの提言でもある。
      </p>
    </div>
    <div style="flex:0 0 320px;" class="flex flex-col items-center justify-center text-center">
      <div style="font-size:88px; font-weight:900; color:var(--tc-navy); line-height:1;">54<span style="font-size:36px; color:var(--tc-navy-soft);">/62</span></div>
      <div style="font-size:16px; color:var(--tc-text); margin-top:8px;">区市町村で支援情報を掲載</div>
      <div class="tc-note" style="border-top:none; margin-top:20px; text-align:center;">
        自治体ごとにデータの充足度は異なります。<br />
        （/coverage: データなし8／1分類のみ41／2分類充足8／3分類すべて充足5）
      </div>
    </div>
  </div>
  <div class="tc-footer" style="position:static; margin-top:16px;">
    <span></span>
    <span>Demo Day 2027/3/27へ</span>
  </div>
</div>

<!--
症状のラベルではなく、次の一歩へ。すでに都内54の区市町村で支援情報を掲載しながら、この窓口ナビを、東京都の誰もが使える相談の入り口に育てていきます。
(目安15秒・75字)

原稿作成メモ: 「54の区市町村」は本番/outcomesの実測値。収録直前に必ず最新の自治体数を再確認し、変わっていれば数字を読み替えること。「GovTech東京や区市町村とも連携しながら」は連携実績が未検証のため削除済み・読み上げ原稿にも含めない。
-->
