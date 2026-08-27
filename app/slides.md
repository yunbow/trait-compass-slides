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
  sans: 'Hiragino Sans'
  provider: none
---

<div class="h-full flex flex-col items-center justify-center text-center">
  <div class="tc-eyebrow">東京都知事杯 オープンデータ・ハッカソン 2026</div>
  <div style="font-size:64px; font-weight:900; color:var(--tc-navy); letter-spacing:0.02em;">Trait Compass</div>
  <div style="font-size:28px; font-weight:700; color:var(--tc-green); margin-top:18px;">気づきと相談のあいだをつなぐ</div>
  <div style="font-size:17px; color:var(--tc-text-muted); margin-top:14px;">CivicUnknot</div>
  <a class="tc-demo-cta" href="https://trait-compass.trait-compass.workers.dev" target="_blank" rel="noopener" style="margin-top:56px; text-decoration:none;">デモを試す&nbsp; → &nbsp;trait-compass.trait-compass.workers.dev</a>
</div>

<!--
表紙スライド。読み上げ原稿はなし(タイトルコールのみ、または無音)。

もし、自分や家族に「何か困りごとがある」と気づいたとき、次にどこへ相談すればいいか、すぐ分かるでしょうか。
気づいてはいる。でも、次の一歩が分からない。
その“気づきと相談のあいだ”をつなぐために作ったのが、Trait Compassです。
-->

---

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">課題｜アイデア力</div>
  <div class="tc-title">気づきと相談のあいだに、空白がある。</div>
  <p class="tc-body" style="margin-bottom:28px;">
    困りごとに気づいても、どこへ相談すればよいか分からない。公的窓口は存在する一方、都・区市町村に情報が分かれ、CSV・PDF・Webページなど形式もばらばらです。
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
「自分は発達障害かもしれない」と感じても、次の一歩が分からず立ち止まる人は少なくありません。11人に1人に著しい困難があるとされる一方、専門機関の初診までは平均2.6か月かかります。この空白を、オープンデータとプライバシー保護設計で埋めるサービスを作りました。
(目安30秒・134字)
-->

---

<script setup>
const demoFlowSteps = [
  { text: '困りごとを整理' },
  { text: '相談分野が分かる' },
  { text: '相談先が見つかる' },
]
</script>

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">デモ｜サービスデザイン／オーディエンス</div>
  <div class="tc-title">セルフチェックが、相談分野タグに変わる。</div>
  <p class="tc-body" style="margin-bottom:20px;">
    30問のセルフチェックを、診断名ではなく6つの「相談分野タグ」に変換。ライフステージと居住地を選ぶだけで、条件に合う公的相談窓口・施設候補を地図と一覧で提示します。
  </p>
  <div style="margin-bottom:20px;">
    <DataFlow direction="horizontal" :steps="demoFlowSteps" />
  </div>
  <div class="flex gap-6" style="flex:1;">
    <BrowserFrame url="trait-compass.trait-compass.workers.dev/result" src="/images/result.png" caption="① 診断名ではなく、相談分野タグで示す" height="180px" object-fit="contain" />
    <BrowserFrame url="trait-compass.trait-compass.workers.dev/support" src="/images/support-map.png" caption="② 地図と一覧から、公的窓口を選べる" height="180px" object-position="bottom" />
  </div>
  <div class="tc-note">
    チェックをしなくても支援情報だけを探すこともできます。<br>
    地図表示：Google Maps（© Google）を使用。
  </div>
</div>

<!--
ブラウザで30の質問に答えると、結果はレーダーチャートと相談分野タグで示されます。ライフステージと区市町村を選ぶだけで、条件に合う公的相談窓口・施設候補を地図と一覧で確認できます。セルフチェックをしなくても、窓口だけを探すこともできます。
(目安25秒・119字)
-->

---

<script setup>
const dataSourceFlowSteps = [
  { text: '散らばった行政の支援情報\n（CSV／PDF／Webページ）', note: '取得・ライセンスを確認し、同じ形式へ整える' },
  { text: '検索できる支援施設データ', note: '地域 × ライフステージ × 相談分野で整理' },
  { text: '条件に合う相談先を提示' },
  { text: '地図・一覧から次の一歩へ' },
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
      <BrowserFrame url="trait-compass.trait-compass.workers.dev/data-sources" src="/images/data-sources.png" caption="利用しているデータ（/data-sources）" height="130px" object-position="top" />
      <p style="font-size:13px; color:var(--tc-text-muted); line-height:1.7;">
        出典・ライセンス・最終取得日・利用件数を公開し、データの根拠をたどれるようにしています。自治体、公的機関、医療情報ネット、WAM NETなどの情報を横断して扱います。
      </p>
      <div style="background:var(--tc-green-soft); border-left:4px solid var(--tc-green); padding:10px 14px; font-size:13px; font-weight:700; color:var(--tc-navy);">
        日常の困りごとチェックの結果の算出には、外部データを使用していません。
      </div>
      <div class="flex gap-2" style="font-size:11px; color:var(--tc-text-muted);">
        <span style="border:1px solid var(--tc-border); border-radius:999px; padding:3px 10px;">CKAN API</span>
        <span style="border:1px solid var(--tc-border); border-radius:999px; padding:3px 10px;">Cloudflare Workers・D1・R2</span>
        <span style="border:1px solid var(--tc-border); border-radius:999px; padding:3px 10px;">送信内容を事前確認できるAI解説</span>
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
    セルフチェックの個別回答は端末内だけで処理・保存し、サーバーへ送信しません。AI解説は完全オプトインで、送信内容を事前に確認できます。
  </p>
  <div class="flex gap-8" style="flex:1;">
    <div style="flex:1;">
      <BrowserFrame url="trait-compass.trait-compass.workers.dev/result/prepare" src="/images/consent.png" caption="キャプチャ③ AI解説の送信前プレビュー" height="210px" />
    </div>
    <div style="flex:0 0 240px;" class="flex flex-col gap-3 justify-center">
      <div style="border:1px solid var(--tc-border); border-radius:6px; padding:12px 16px; font-size:14px; font-weight:700; color:var(--tc-navy);">個別回答は非送信</div>
      <div style="border:1px solid var(--tc-border); border-radius:6px; padding:12px 16px; font-size:14px; font-weight:700; color:var(--tc-navy);">非診断</div>
      <div style="border:1px solid var(--tc-border); border-radius:6px; padding:12px 16px; font-size:14px; font-weight:700; color:var(--tc-navy);">完全オプトイン</div>
    </div>
  </div>
</div>

<!--
セルフチェックの個別回答は端末内だけで処理・保存し、サーバーへ送信しません。AI解説は完全オプトインで、送信内容を事前に確認できます。
(目安13秒・67字)
-->

---

<div class="h-full flex flex-col">
  <div class="tc-eyebrow">社会実装｜ソーシャルインパクト</div>
  <div class="tc-title" style="margin-bottom:20px;">東京都で、相談の第一歩を迷わせない。</div>
  <div class="flex gap-10" style="flex:1;">
    <div style="flex:1;" class="flex flex-col justify-center">
      <p class="tc-body">
        すでに54区市町村の相談窓口・施設情報を掲載し、本番稼働しています。データの充足度も公開しながら、残る地域とデータソースをつなぎ、誰もが相談先にたどり着ける入口を育てます。
      </p>
      <p style="font-size:13px; color:var(--tc-text-muted); margin-top:16px; line-height:1.7;">
        自治体が支援情報を共通形式で公開できる「統一支援施設スキーマ」も提案している。
      </p>
    </div>
    <div style="flex:0 0 320px;" class="flex flex-col items-center justify-center text-center">
      <div style="font-size:88px; font-weight:900; color:var(--tc-navy); line-height:1;">54<span style="font-size:36px; color:var(--tc-navy-soft);">/62</span></div>
      <div style="font-size:16px; color:var(--tc-text); margin-top:8px;">区市町村で支援情報を掲載</div>
      <div class="tc-note" style="border-top:none; margin-top:20px; text-align:center;">
        ※自治体ごとにデータの充足度は異なります
      </div>
    </div>
  </div>
  <div class="tc-footer" style="position:static; margin-top:16px;">
    <span></span>
    <a href="https://trait-compass.trait-compass.workers.dev" target="_blank" rel="noopener" style="color:inherit;">デモを試す → trait-compass.trait-compass.workers.dev</a>
  </div>
</div>

<!--
症状のラベルではなく、次の一歩へ。すでに都内54の区市町村で支援情報を掲載しながら、この窓口ナビを、東京都の誰もが使える相談の入り口に育てていきます。
(目安15秒・75字)

充足度の内訳（/coverage、口頭では言わない・スライドを指しながら「充足度は異なります」とだけ触れる）: データなし8／1分類のみ41／2分類充足8／3分類すべて充足5。

原稿作成メモ: 「54の区市町村」は本番/outcomesの実測値。収録直前に必ず最新の自治体数を再確認し、変わっていれば数字を読み替えること。「GovTech東京や区市町村とも連携しながら」は連携実績が未検証のため削除済み・読み上げ原稿にも含めない。
-->
