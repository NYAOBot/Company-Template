# Company OS for Codex

このリポジトリは、Codex CLIで会社を運営するためのCompany-Templateです。Codexはこの `AGENTS.md` を最上位の会社コンテキストとして読み、必要に応じて `codex/roles/*.md` と `codex/workflows/*.md` を参照します。

## 会社プロフィール（編集してください）

- 会社/プロジェクト名: `YOUR_COMPANY`
- ミッション: `誰のどんな課題を解決するかを書く`
- 主な顧客: `例: 個人開発者 / 中小企業 / エンタープライズ`
- 主な商品: `例: SaaS / AI Agent / コンサルティング`
- 今期の最重要KPI: `例: MRR / 利用継続率 / 商談数`
- 制約: `予算・人数・期限・ブランドトーンなど`

## Codexへの依頼ルール

Codexに依頼するときは、以下の形を推奨します。

```text
AGENTS.md と codex/roles/<role>.md を読んで、<目的>を実行して。
成果物は <path> に保存して。
```

例:

```text
AGENTS.md と codex/roles/pm.md を読んで、新規LP改善プロジェクトを projects/lp-improvement/ に作成して。
成果物は brief.md, tasks.md, risks.md。
```

## 共通原則

1. 結論→理由→次アクションの順で答える。
2. 不確実なことは「仮説」と明記する。
3. 重要な意思決定は `company/strategy/decision-log.md` に追記できる形式で出す。
4. 会議・打ち合わせの結果は `company/meetings/` に日付つきで保存できる形式にする。
5. 実行タスクは `projects/<project-name>/tasks.md` へ落とす。
6. 法務・税務・医療・投資など専門判断は、人間/専門家確認を必須にする。
7. ファイル変更前に対象ファイルを確認し、変更後は `git diff` で差分確認する。

## Roleの選び方

- 経営判断: `codex/roles/ceo.md`, `codex/roles/chief-of-staff.md`
- 日程/議事録/TODO: `codex/roles/secretary.md`
- 企画/進行: `codex/roles/pm.md`, `codex/roles/product-lead.md`
- 技術/実装: `codex/roles/cto.md`, `codex/roles/engineer.md`
- 広報/マーケ: `codex/roles/pr-lead.md`, `codex/roles/marketing-lead.md`
- 売上/顧客: `codex/roles/sales-lead.md`, `codex/roles/customer-support.md`
- 財務/法務/人事: `codex/roles/finance-lead.md`, `codex/roles/legal-risk.md`, `codex/roles/hr-lead.md`

## 標準出力フォーマット

```markdown
## 結論

## 背景/前提

## 選択肢
| 案 | 内容 | メリット | リスク | 必要リソース |
|---|---|---|---|---|

## 推奨アクション
- 担当Role:
- 期限:
- 成果物:

## TODO
| Task | Owner Role | Due | Deliverable |
|---|---|---|---|

## リスク/確認事項
```

## ファイル運用

- 会社全体の恒久情報: `company/`
- 部門別の資料: `departments/`
- 案件別の作業: `projects/<project-name>/`
- 再利用テンプレート: `templates/`
- Codex用プロンプト: `codex/`

## 禁止事項

- 不確実な情報を断定しない。
- 専門家確認が必要な領域をAIだけで最終判断しない。
- 機密情報、APIキー、個人情報をコミットしない。
- `rm -rf` や `git push --force` など破壊的操作を勝手に行わない。
