# AI会社（Claude Code 版）

Claude Code で開くだけで動く「AI会社」のフォルダです。無料・MIT ライセンスです。
アプリのインストールも、Node.js などの準備もいりません。Claude Code が入っていれば使えます。

あなたが社長です。仕事を頼むと、司令塔（Claude）が中身を整理して、12人の社員（サブエージェント）に順番に回し、できたものをフォルダに保存します。

| 班 | 社員 | 頼み方 | できるもの |
|---|---|---|---|
| note | リサーチ → 構成 → 書き手 | `/note テーマ` | 参考記事3本の分析、構成、本文 |
| インスタ | リサーチ → 分析 → 台本 | `/reels ジャンル` | 伸びたリールの一覧と倍率、伸びた理由、台本3案 |
| Web | 設計 → デザイン → 実装 → 確認 | `/web 作りたいもの` | 1枚のHTMLのサイト・LP |
| 分析 | 分析担当 | `/analysis ファイル` | 増減・おかしな値・次に見るべき所 |
| セキュリティ | セキュリティ担当 | `/security-check` | APIキーやパスワードの置き方の確認 |

いちばんの特徴は、**会社として記録が残る**ことです。社長が決めたことは `memory/decisions.md`、作ったものは `memory/changes.md`、社長の好みは `memory/boss.md` に書かれて、次の仕事のときに社員が読みます。毎回同じ説明をしなくて済みます。

> **投稿・公開・送信はしません。** 作るのは下書きまでで、出すのはあなたです。

## 入れ方

Claude Code に、次の文をそのまま貼ってください。

```
https://github.com/hitori-claude/ai-company-ja

このAI会社を、デスクトップに ai-company というフォルダで入れて。
入れたら、そのフォルダを開き直す方法を教えて。
```

自分でコマンドを打つ場合：

```bash
git clone https://github.com/hitori-claude/ai-company-ja.git ai-company
cd ai-company
claude
```

**大事：** 社員とコマンドは、このフォルダを開いたときだけ使えます。Claude Code は必ず `ai-company` フォルダで開いてください（デスクトップアプリなら「フォルダを開く」でこのフォルダを選ぶ）。

## 最初にやること

1. `memory/boss.md` に、自分の発信ジャンル・読者・話し方を書く（Claude に「boss.md を一緒に埋めて」と頼んでもOK）
2. `/note` か `/reels` を1回動かしてみる
3. `outputs/` に成果物ができていればOK

## 使い方の例

```
/note Claude Codeで家計簿を自動化する方法
/reels AI活用・時短術
/web 自宅でやっている料理教室のLP
/analysis 売上_2026.csv
/security-check
```

コマンドを使わずに「このCSVを見て、先月と比べて」のように普通に頼んでも、司令塔が担当を決めて回します。

## インスタ班をもっと使うなら

台本担当は、同じ作者の「インスタ運用スキル（日本語版）」が入っていると、フックの採点とAIっぽさ消しまでやってから返します。

https://github.com/hitori-claude/instagram-agent-skill-ja

## フォルダの中身

```
CLAUDE.md              司令塔のルール（仕事の回し方・記録の残し方・やらないこと）
.claude/agents/        社員12人（1人1ファイル。中を書き換えれば社員の仕事が変わる）
.claude/commands/      /note /reels /web /analysis /security-check
memory/                決めたこと・作ったもの・社長のこと
outputs/               成果物（note・reels・web・analysis・security）
```

社員を増やしたいときは、`.claude/agents/` にファイルを1つ足します。既存のファイルをコピーして、名前と仕事を書き換えるのがいちばん早いです。

## 注意

- 社員は Claude Code の利用枠を使います。1回の `/note` で、ふつうの会話の数回分くらい使います
- インスタのリサーチは、Claude in Chrome（Chrome の拡張機能）が使えるときは画面を見て集めます。使えないときは、参考にしたいリールのURLを聞かれます
- `memory/` には社長の好みや事情が書かれていきます。自分の GitHub などに公開するときは `memory/` を外してください
- フォロワーや売上が伸びることを約束するものではありません

## ライセンス

MIT
