# Company-Template

Claude Codeを「会社経営OS」として使うためのテンプレートです。  
社長・秘書・PM・広報などの役割を `.claude/agents/` に分け、案件ごとに適切なAgentへ仕事を振れるようにしています。

> 目的: ひとり社長/小規模チームが、Claude Code上で経営判断・企画・実行・広報・バックオフィスを並列化する。

## すぐ使う

```bash
gh repo create YOUR_ORG/YOUR_COMPANY --template NYAOBot/Company-Template --private --clone
cd YOUR_COMPANY
claude
```

Claude Code内で以下のように依頼します。

```text
@ceo 事業方針を整理して、今月の最重要KPIを決めて
@secretary 今日の議事録からTODOと次回アジェンダを作って
@pm 新機能リリースまでの計画をissue単位に分解して
@pr-lead 新サービス告知のX投稿案とプレスリリース草案を作って
```

## ディレクトリ構成

```text
.
├── CLAUDE.md                         # Claude Codeが最初に読む会社コンテキスト
├── .claude/
│   ├── agents/                       # 役職別Agent定義
│   ├── commands/                     # 会社運営用スラッシュコマンド
│   ├── rules/                        # 全Agent共通の判断ルール
│   └── settings.json                 # Claude Code権限・hook例
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
└── templates/                        # 再利用テンプレート
```

## Agent一覧

| Agent | 役割 | 使いどころ |
|---|---|---|
| `@ceo` | 社長/経営判断 | 方針、優先順位、意思決定、KPI |
| `@secretary` | 秘書/議事録/調整 | 議事録、予定、TODO、リマインド文面 |
| `@chief-of-staff` | 参謀/全社横断 | 経営課題の分解、部門間調整、意思決定補助 |
| `@pm` | PM/進行管理 | 要件定義、ロードマップ、issue分解、進捗管理 |
| `@product-lead` | プロダクト責任者 | ユーザー価値、仕様、リサーチ、PRD |
| `@cto` | CTO/技術責任者 | 技術選定、アーキテクチャ、実装方針 |
| `@engineer` | 実装担当 | コード変更、テスト、デバッグ |
| `@pr-lead` | 広報 | 告知、SNS、プレスリリース、ブランド文脈 |
| `@marketing-lead` | マーケ | LP、広告、グロース、ファネル改善 |
| `@sales-lead` | 営業 | 提案、商談準備、顧客課題整理 |
| `@finance-lead` | 財務 | 予算、PL、資金繰り、単価設計 |
| `@legal-risk` | 法務/リスク | 契約、規約、権利、リスク洗い出し |
| `@hr-lead` | 人事 | 採用、評価、オンボーディング |
| `@customer-support` | CS | FAQ、返信文、VOC整理 |

## 基本ワークフロー

1. `@ceo` が目的と優先順位を決める
2. `@chief-of-staff` が論点・関係者・成果物を整理する
3. `@pm` がタスクへ分解し、`projects/<project-name>/` を作る
4. 専門Agentが実行する
5. `@secretary` が決定事項・TODO・次回確認事項を記録する
6. 重要な意思決定は `company/strategy/decision-log.md` に残す

## Claude Codeコマンド例

```text
/run-company-meeting 今週の経営会議。売上、開発、広報、採用の進捗を確認して次の一手を決める
/create-project 新規LP改善プロジェクト。CVRを上げたい
/daily-standup 昨日の完了、今日やること、詰まりを整理
/decision-record 価格改定をするかどうか
/launch-plan 新機能を来月公開する
```

## 会社情報の初期設定

最初に以下を編集してください。

- `CLAUDE.md` の会社名・事業内容・制約
- `company/strategy/company-profile.md`
- `company/strategy/kpi.md`
- `.claude/settings.json` の権限範囲

## 注意

- 法務・税務・投資判断はAI出力だけで確定しないでください。専門家確認が必要です。
- Agentは役割を分けるためのプロンプトです。最終責任者は人間です。
- 機密情報や個人情報を入れる場合は、Claude Code/リポジトリ/ログの扱いを確認してください。
