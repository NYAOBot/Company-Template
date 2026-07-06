# Company-Template for Codex

Codex CLIを「会社経営OS」として使うためのテンプレートです。  
`AGENTS.md` を会社の共通ルール、`codex/roles/` を役職別プロンプト、`codex/workflows/` を定例業務の進行台本として使います。

> 目的: ひとり社長/小規模チームが、Codex上で経営判断・企画・実行・広報・バックオフィスを並列化する。

## すぐ使う

```bash
gh repo create YOUR_ORG/YOUR_COMPANY --template NYAOBot/Company-Template --private --clone
cd YOUR_COMPANY
codex exec "AGENTS.mdを読んで、@ceoとして今月の最重要KPIを決めて"
```

CodexはClaude Codeのようなネイティブ `@agent` 呼び出しではなく、`AGENTS.md` とロールプロンプトを読ませて役割を切り替えます。

## 基本の呼び出し方

### CEOに経営判断を依頼

```bash
codex exec "AGENTS.md と codex/roles/ceo.md を読んで、今月の経営方針を3案出して推奨案を決めて"
```

### 秘書に議事録化を依頼

```bash
codex exec "codex/roles/secretary.md に従って、company/meetings/raw-notes.md から決定事項・TODO・次回アジェンダを作って"
```

### PMにプロジェクト分解を依頼

```bash
codex exec --full-auto "AGENTS.md と codex/roles/pm.md を読んで、新規LP改善プロジェクトを projects/lp-improvement/ に作成して"
```

### 経営会議ワークフローを実行

```bash
codex exec "codex/workflows/company-meeting.md に沿って、今週の経営会議を実行して"
```

## ディレクトリ構成

```text
.
├── AGENTS.md                         # Codexが読む会社OSの共通ルール
├── codex/
│   ├── README.md                     # Codex運用ガイド
│   ├── roles/                        # 役職別プロンプト
│   ├── workflows/                    # 定例業務・会議の進行台本
│   └── prompts/                      # すぐ使える依頼テンプレート
├── company/
│   ├── strategy/                     # 事業戦略・KPI・意思決定ログ
│   ├── meetings/                     # 会議テンプレート・議事録
│   ├── operations/                   # SOP・業務フロー
│   ├── finance/                      # 予算・売上・資金繰り
│   ├── legal/                        # 契約・規約・リスク
│   ├── hr/                           # 採用・評価・オンボーディング
│   └── brand/                        # ブランド・広報・メッセージ
├── departments/
│   ├── product/                      # プロダクト企画・ロードマップ
│   ├── engineering/                  # 開発・技術判断
│   ├── marketing/                    # マーケ・広告・コンテンツ
│   ├── sales/                        # 営業・CRM・提案書
│   └── support/                      # 顧客対応・FAQ
├── projects/                         # 案件ごとの作業場
├── scripts/                          # Codex呼び出し補助スクリプト
└── templates/                        # 再利用テンプレート
```

## Role一覧

| Role | ファイル | 使いどころ |
|---|---|---|
| CEO | `codex/roles/ceo.md` | 方針、優先順位、意思決定、KPI |
| Secretary | `codex/roles/secretary.md` | 議事録、予定、TODO、リマインド文面 |
| Chief of Staff | `codex/roles/chief-of-staff.md` | 経営課題の分解、部門間調整、意思決定補助 |
| PM | `codex/roles/pm.md` | 要件定義、ロードマップ、issue分解、進捗管理 |
| Product Lead | `codex/roles/product-lead.md` | ユーザー価値、仕様、リサーチ、PRD |
| CTO | `codex/roles/cto.md` | 技術選定、アーキテクチャ、実装方針 |
| Engineer | `codex/roles/engineer.md` | コード変更、テスト、デバッグ |
| PR Lead | `codex/roles/pr-lead.md` | 告知、SNS、プレスリリース、ブランド文脈 |
| Marketing Lead | `codex/roles/marketing-lead.md` | LP、広告、グロース、ファネル改善 |
| Sales Lead | `codex/roles/sales-lead.md` | 提案、商談準備、顧客課題整理 |
| Finance Lead | `codex/roles/finance-lead.md` | 予算、PL、資金繰り、単価設計 |
| Legal & Risk | `codex/roles/legal-risk.md` | 契約、規約、権利、リスク洗い出し |
| HR Lead | `codex/roles/hr-lead.md` | 採用、評価、オンボーディング |
| Customer Support | `codex/roles/customer-support.md` | FAQ、返信文、VOC整理 |

## 補助スクリプト

ロール指定を毎回書くのが面倒な場合:

```bash
scripts/codex-role ceo "今月の最重要KPIを決めて"
scripts/codex-role pm "新規LP改善プロジェクトを作って"
scripts/codex-workflow company-meeting "売上、開発、広報、採用を確認して"
```

## Codex運用Tips

- Codexはgit repo内で実行してください。
- ファイル変更を任せるときは `--full-auto` を使うとスムーズです。
- 危険な一括変更を避けるため、依頼には必ず対象ディレクトリと期待成果物を書いてください。
- 会社情報はまず `company/strategy/company-profile.md` と `AGENTS.md` を編集してください。
- 法務・税務・投資判断はAI出力だけで確定しないでください。専門家確認が必要です。
