# b-pass-scanner

> **層：運用層（operations）｜事実変化はAIが差分提示→承認後に更新可。**

## このリポジトリについて
B-PASS用のQRスキャナー（静的ページ。技術詳細は下記「技術スタック」参照）。
GitHub Pagesで公開され、参加者の出席登録に使用される。

## 技術スタック
- 単一HTML＋jsQR（CDN: jsdelivr, v1.4.0固定）。Service Worker/manifestなし（PWAではなく単純静的ページ）。オフライン耐性はlocalStorageの名簿・送信キューのみ
- GitHub Pages

## ファイル構成
- index.html : スキャナー本体（カメラAPI使用）

## 開発ルール
- iOSのカメラ権限問題が未解決（要対応）（鮮度不明・実機確認要）
- 単一HTMLで自己完結させる方針。ビルド工程・フレームワーク・複数ファイル化を導入しない。jsQRのvendor化（インライン化）は方針に合致する改善候補
- 現行index.htmlのnavy/goldはbulldon-brandガイドライン値と不一致。是正するかは未決定（記録のみ）

## API契約（SSOT）

本フロントエンドが呼び出すAPIの契約。**本節をこの契約の正本とする**（実装・防御の詳細は稼働バックエンド側リポジトリに記載する）。

- `action=masterData`：パラメータ `pass`（パスコード認証）。レスポンス `{success, date, count, list}`。`list`の各要素は `id/name/gender/age/exp/photo`。
- `action=sync`：パラメータ `pass, ids`（出席登録済みID配列）。レスポンス `{success, count}`。
- `action=cancel`：パラメータ `pass, ids`。レスポンス `{success}`。
- 認証失敗時・パスコード未設定時の挙動（fail-closed方針）は稼働バックエンド側の実装に従う。

## publicリポ制約

publicリポ共通の禁止物は法律層 `../.claude/rules/public-repo-guard.md` を正本とする。

- `?api=`パラメータ設計（URLをコードに埋め込まず実行時パラメータで受領する仕組み）はURL秘匿のための意図的設計。ハードコード化・設定ファイル化への変更は禁止（変更したい場合は清水判断）。

## 関連
現行の接続先バックエンドは `samurai-simons`（`action=masterData|sync|cancel` を処理）。bpass-parent はScanner API未実装（Phase 3で実装予定）。旧BulldonPassportSystem（`_archive\B-PASS\bulldon-bpass`。アーカイブ・読み取り専用）は同型APIで稼働していた歴史的バックエンド。

## 上位ルール

ワークスペース `../.claude/rules/`（bulldon-workspace）を継承（commit-style / _meta-rules / brand-design / public-repo-guard）。
GAS リポジトリではないため `gas-architecture.md` / `b-pass-design.md` は対象外。全体の正本は `../AGENTS.md`。
