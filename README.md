# aoiro-note（Hugo版）— 運用メモ

ドメイン: aoiro-note.com（Cloudflare Registrar）
形態: Hugo 静的サイト。記事は Markdown、見た目は layouts + static/style.css。
プレーン版（../aoiro-note/）は移植元の参考として残してある。

## 構成
- `hugo.toml` — サイト設定（タイトル、メニュー、Markdown設定）
- `layouts/` — テンプレート（baseof=共通枠、index=トップ、single=記事、list=一覧）
- `static/style.css` — デザインはこの1ファイル。色は先頭の :root 変数で変更可
- `content/articles/*.md` — 記事（比較記事、青色申告ガイド）
- `content/about.md` / `content/privacy.md` — 固定ページ
- `public/` — ビルド結果（検証用に同梱。編集するのは content と layouts のほう）

## ローカル確認
```
hugo server   # http://localhost:1313 でプレビュー
hugo          # public/ に書き出し
```

## 公開手順（Cloudflare Pages・推奨はGit連携）
1. このフォルダを GitHub リポジトリに入れる
2. Cloudflare ダッシュボード → Workers & Pages → Create → Pages → Connect to Git
3. Build settings: Framework preset = Hugo / Build command = `hugo` / Output = `public`
   - 環境変数 HUGO_VERSION = 0.152.2 を指定（ビルドに使った版と合わせる）
4. Custom domains → aoiro-note.com を追加
5. Google Search Console に登録（sitemap.xml は自動生成される）

※ Gitを使わない場合：ローカルで `hugo` を実行し、public/ の中身を Pages の Upload assets で上げる方法でも公開できる。

## 記事の書き方
- 記事は `content/articles/` に .md を追加するだけ。トップと一覧に自動で載る
- フロントマター: title / description / date / tag / summary / disclosure（広告表記）/ toc: true（目次）
- CTAボックスや結論ボックスはHTMLで書ける（hugo.toml で unsafe 許可済み）。比較記事の書き方をコピペすればよい
- 見出し（##）がそのまま目次とアンカーになる

## ASP申込チェックリスト（サイト公開後）
- [ ] A8.net — 登録済み（パスワード再発行が先）。freee／マネーフォワード／弥生の提携申請
- [ ] もしもアフィリエイト — 新規登録。会計freeeは公式に A8 と もしも のみ（freee公式アフィリエイトページで確認 2026-11-01）。給与計算freee等はもしも限定
- [ ] バリューコマース / afb — 会計freeeの取り扱いはなし。MF／弥生の案件確認用
- [ ] 提携が通ったら、比較記事のCTAボタン（href="#" の3箇所＋TODOコメント）をアフィリンクに差し替える
- [ ] 開業freee を青色申告ガイド記事に設置

## 要確認・差し替えポイント
- 料金表：改定が多いため金額を断定せず「公式で確認」に寄せている。具体額を入れる場合は申込前に公式で再確認
- about の連絡先メール（公開準備中プレースホルダ）
- テーマ丸ごとの着せ替えも可能（layouts を差し替えるだけ。記事Markdownは無傷）

## 記事ネタ backlog（優先度順）
1. 会計freee 実体験レビュー（現場フリーランスの請求・入金管理フロー）※一次情報で最強の差別化
2. 開業届と青色申告承認申請の出し方（開業freee手順つき）
3. インボイス登録はすべきか（課税事業者選択の判断軸）
4. 源泉徴収される仕事の仕訳と確定申告での精算（実例ベース）
5. 事業用口座・カードの分け方（PayPay銀行など実口座ベース）
6. freee vs マネーフォワード 乗り換え体験／データ移行の注意点
7. 確定申告シーズンの作業カレンダー（1〜3月の実務フロー）
8. 経費になるもの・ならないもの（現場仕事の実例：交通費、機材、宿泊）
9. 電子帳簿保存法対応チェックリスト
10. 税理士に頼む場合の相場と、ソフトで完結できるラインの見極め
