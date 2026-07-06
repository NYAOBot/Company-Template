# Workflow: project-kickoff

## 目的
新規プロジェクトを立ち上げる。brief.md, tasks.md, risks.md, success-metrics.mdを作る。

## Codexでの使い方

```bash
codex exec "AGENTS.md と codex/workflows/project-kickoff.md を読んで、<具体的なテーマ>を実行して"
```

## 進行手順

1. `AGENTS.md` で会社プロフィールと共通原則を確認する。
2. 必要なRoleを選ぶ。
3. 現状・制約・成功条件を整理する。
4. 選択肢を3案以上出す。
5. 推奨案を決める。
6. TODOを担当Role・期限・成果物つきで整理する。
7. 必要に応じて `company/` または `projects/` に保存できるMarkdown形式で出力する。

## 出力フォーマット

```markdown
# project-kickoff: YYYY-MM-DD

## 目的

## 現状

## 論点

## 選択肢
| 案 | 内容 | メリット | リスク | 必要リソース |
|---|---|---|---|---|

## 決定/推奨

## TODO
| Task | Owner Role | Due | Deliverable |
|---|---|---|---|

## 次回確認事項
```
