---
layer: operations
revision_policy:
  frequency: as_needed
  authority: claude_with_fact_check
last_reviewed: 2026-05-01
---

# b-pass-scanner

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
B-PASS本体（BulldonPassportSystem）と連携。
詳細仕様は `C:\dev\bulldon\_shared\` を参照
