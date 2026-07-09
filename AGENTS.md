# b-pass-scanner

> **層：運用層（operations）｜事実変化はAIが差分提示→承認後に更新可。**

## このリポジトリについて
B-PASS用のQRスキャナー（PWA）。
GitHub Pagesで公開され、参加者の出席登録に使用される。

## 技術スタック
- 単一HTMLファイル（PWA、外部依存なし）
- GitHub Pages

## ファイル構成
- index.html : スキャナー本体（カメラAPI使用）

## 開発ルール
- iOSのカメラ権限問題が未解決（要対応）
- 単一HTMLで自己完結させる方針

## 関連
B-PASS本体（bpass-parent / bpass-child-deploy。旧 BulldonPassportSystem は `_archive\B-PASS\bulldon-bpass` にアーカイブ・読み取り専用）と連携。
詳細仕様は `../_shared/` を参照

## 上位ルール

ワークスペース `../.claude/rules/`（bulldon-workspace）を継承（commit-style / _meta-rules / brand-design）。
GAS リポジトリではないため `gas-architecture.md` / `b-pass-design.md` は対象外。全体の正本は `../AGENTS.md`。
