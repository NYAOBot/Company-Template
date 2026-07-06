# Codex Operation Guide

このディレクトリはCodex用の会社運営レイヤーです。

## 推奨パターン

```bash
codex exec "AGENTS.md と codex/roles/ceo.md を読んで、今月の方針を決めて"
codex exec --full-auto "AGENTS.md と codex/roles/pm.md を読んで、projects/new-project/ に計画を作って"
codex exec "codex/workflows/weekly-review.md に沿って週次レビューして"
```

## ファイル変更を伴う場合

- `--full-auto` を使う
- 対象ディレクトリを限定する
- 最後に `git diff` を確認する

例:

```bash
codex exec --full-auto "AGENTS.md と codex/roles/pm.md を読んで、projects/pricing-review/ に brief.md, tasks.md, risks.md を作成して。最後にgit diffで確認して"
```

## 危険操作

以下はCodexに任せず、人間が確認してください。

- 本番デプロイ
- 支払い/送金
- 契約送付
- 法務・税務上の最終判断
- force pushや大量削除
