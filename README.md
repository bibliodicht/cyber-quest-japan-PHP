# CYBER QUEST JAPAN for PHP（デモ版）

2026年10月21日に公表されたPHPの脆弱性（CVE-2026-109618 / CVE-2026-109619）を題材に、Webの仕組みから緊急対応・フィッシング対策までを遊びながら学ぶ、**民間の無料学習ゲーム**です。政府機関・The PHP Group等とは無関係で、公的な認定ではありません。

## 現在できること
- STAGE 0〜6（Webの仕組み／PHP／今回の脆弱性／コードレビュー／緊急対応／フィッシング／総合ミッション）
- XP・レベル・実績・ダッシュボード・進捗の保存と再開（localStorage）
- CYBER TRIAL（ランダム総合問題・タイムアタック。全ステージクリアで解放）
- マイ・ランキング（出題条件ごと・この端末内の記録のみ）／結果カード（学習の記録／CYBER TRIAL結果）のPNG保存・共有文編集・Web Share API・X・Threads投稿リンク
- 事実と出典ページ（確認状況バッジ：公的機関で確認／二次情報／未確認）

## まだできないこと（未実装）
- **オンライン（世界）ランキングは実装しない方針**です。ランキングは「出題条件ごとの、この端末内の自分の記録」だけです。
- アカウント登録・端末間同期
- 問題の正解データはブラウザに含まれます（自己学習用のため）

## 構成
依存ゼロ（TypeScript + 素のDOM + 静的HTML/CSS）。ビルドは `tsc` のみ。理由は `docs/DESIGN.md`。

## セットアップ・ビルド・確認
```bash
npm install          # typescript のみ
npm run build        # dist/ に出力
npm test             # ビルド＋ユニットテスト
npm run serve        # http://localhost:5173 で dist/ を配信
```
## 公開前に設定するもの
`src/config/game.ts` の `feedbackUrl`（Googleフォームの報告用URL）、`threadsUrl`（任意）、`publicUrl`（公開URL）。

## 1ファイル版
`npm run build` で `dist/cyber-quest-japan.html` も作られます（ダブルクリックで開けます）。

## 公開（GitHub Pages・無料枠）
1. GitHubにpush（`.github/workflows/pages.yml` が `dist/` を公開）。リポジトリ設定 → Pages → Source を「GitHub Actions」に。
2. `src/config/game.ts` の `SERVICE.publicUrl` に公開URLを設定（共有カードに入ります）。
3. 公開前に `docs/SECURITY_CHECKLIST.md` と、`#/facts` の「公開前に確認するリスト」を実施。
Cloudflare Pages / Netlify 等でも、`dist/` を配信するだけで動きます。無料枠の条件は変わり得るため、公開時に各社の公式ページで確認してください。

## 教材の更新（今回のPHP問題）
`src/content/facts.ts`（事実カード・出典・確認日・確認状況）だけを更新すれば、STAGE 2・4・6と関連問題に反映されます。問題は `src/content/questions.ts`、レベル・配点・スコア式は `src/config/game.ts`。
