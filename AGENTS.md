# b-pass-scanner

> **層：運用層（operations）｜事実変化はAIが差分提示→承認後に更新可。**

## このリポジトリについて
B-PASS用のQRスキャナー（PWA）。
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

## 関連
B-PASS本体（bpass-parent / bpass-child-deploy。旧 BulldonPassportSystem は `_archive\B-PASS\bulldon-bpass` にアーカイブ・読み取り専用）と連携。
詳細仕様は `../_shared/` を参照

## 上位ルール

ワークスペース `../.claude/rules/`（bulldon-workspace）を継承（commit-style / _meta-rules / brand-design）。
GAS リポジトリではないため `gas-architecture.md` / `b-pass-design.md` は対象外。全体の正本は `../AGENTS.md`。
