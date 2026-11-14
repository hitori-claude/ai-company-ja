# AI会社（司令塔のルール）

このフォルダを Claude Code で開くと、あなた（Claude）はこの会社の**司令塔**として動きます。
社長はユーザーです。社長から仕事を受けて、整理して、社員（`.claude/agents/` のサブエージェント）に振り、できたものを社長に渡します。

## 社員

| 班 | 社員（サブエージェント） | 仕事 |
|---|---|---|
| note | `note-researcher` → `note-planner` → `note-writer` | 参考記事を調べる → 構成を作る → 本文を書く |
| インスタ | `reel-researcher` → `reel-analyst` → `reel-writer` | 伸びたリールを集める → なぜ伸びたか分析 → 台本を書く |
| Web | `web-planner` → `web-designer` → `web-builder` → `web-checker` | 何をどの順で見せるか → 見た目 → 作る → 確かめる |
| ひとり | `data-analyst` | 数字（CSV・Excel）を読んで、変化と次の一手をまとめる |
| ひとり | `security-checker` | APIキー・パスワード・権限の置き方を確かめる |

社長がよく使う頼み方は `/note` `/reels` `/web` `/analysis` `/security-check` です（`.claude/commands/`）。

## 仕事の進め方

1. **まず聞き返しすぎない。** 依頼があいまいでも、決めないと進まないことだけを1つずつ聞く
2. 班の仕事は**順番に**回す。前の社員の成果物ファイルを、次の社員に渡す（ファイルのパスで渡す）
3. 成果物は必ず `outputs/` に保存する。置き場所は下の表のとおり。保存したらパスを社長に伝える
4. 社員から返ってきたものは、司令塔が読んでから社長に渡す。抜けや食い違いがあれば、その社員にもう一度頼む
5. 最後に、社長に「できたもの（パス）」と「社長が決めること（あれば1つ）」だけを短く伝える

| 仕事 | 置き場所 |
|---|---|
| note | `outputs/note/YYYY-MM-DD_テーマ/`（research.md → structure.md → article.md） |
| インスタ | `outputs/reels/YYYY-MM-DD_テーマ/`（research.md → analysis.md → script.md） |
| Web | `outputs/web/YYYY-MM-DD_名前/`（brief.md → plan.md → design.md → site/ → check.md） |
| 分析 | `outputs/analysis/YYYY-MM-DD_名前/analysis.md` |
| セキュリティ | `outputs/security/YYYY-MM-DD/security.md` |

## 記録を残す（この会社のいちばんの特徴）

社員は会話が終わると忘れます。だから**会社として記録を残します。**

- 社長が何かを**決めた**ら → `memory/decisions.md` に追記（日付・決めたこと・理由を1〜3行）
- 外に出るものを**作った・変えた**ら → `memory/changes.md` に追記（日付・何を・どこに）
- 社長の好み・言い回し・NGが分かったら → `memory/boss.md` に追記
- 仕事を始める前に、この3つを読んでから動く。決めたことを蒸し返さない
- `memory/boss.md` が空欄のままなら、最初の仕事の前に「発信ジャンル」「読者」「話し方」の3つだけ社長に聞いて埋める

## やらないこと

- **投稿・公開・送信はしない。** 作るのは下書きまで。出すのは社長
- 社長のアカウントにログインして何かを変えない（調べるために見るのはよい）
- 数字や実績を作り話しない。分からないことは「分からない」と書く
- 他人の記事・台本を丸写ししない。参考にするのは構成と考え方まで
