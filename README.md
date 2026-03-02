# crowdworks-agent

CrowdWorks の案件検索・提案文生成・応募フォーム入力を **Cursor Agent + browser MCP** で自動化するスキル。

## できること

1. キーワード/カテゴリで CrowdWorks の案件を一括検索し、10件をブラウザタブで同時展開
2. 選んだ案件に対して提案文を自動生成
3. 応募フォームに自動入力（送信は手動で確認してから）

## セットアップ

```bash
git clone https://github.com/GitSATOMasashi/crowdworks-agent.git
cd crowdworks-agent
cursor .
```

### 前提条件

- **Cursor IDE** がインストール済みであること
- **browser MCP** (`cursor-ide-browser`) が有効であること
  - 確認: Cursor Settings → MCP → `cursor-ide-browser` が enabled
- **CrowdWorks アカウント**（応募時のみ必要。案件の閲覧はログイン不要）

## 使い方

Cursor の Agent モード（`Cmd+L`）で:

```
クラウドワークスで AI 案件を10件探して
```

これだけでスキルが自動トリガーされ、以下が実行される:

1. CrowdWorks で案件を検索・フィルタリング
2. 10件をブラウザの新規タブで一括オープン
3. 番号付きリストを提示 → 応募したい番号を聞いてくる
4. 選んだ案件の提案文を自動生成 → 確認を求める
5. 承認後、応募フォームに自動入力 → 「送信ボタンを押してください」と案内
6. 完了後、次の案件の番号を聞いて待機

## ログインについて

- 案件ページは公開 URL（`/public/jobs/{id}`）なのでログイン不要
- 応募フォームに進む時点で未ログインなら、エージェントが手動ログインを案内する
- 1つのタブでログインすれば Cookie が共有されて全タブに適用
- エージェントが自動ログインすることはない（セキュリティ上）

## カスタマイズ

`.cursor/skills/crowdworks/SKILL.md` 内の以下を自分用に書き換える:

| 項目 | 場所 | 内容 |
|------|------|------|
| プロフィール | Step 2-3 | 名前・経歴・得意分野 |
| フィルタキーワード | Step 1-2 | スキップワード・マッチキーワード |
| 提案文テンプレート | Step 2-3 | 自己紹介・提案構成・強み |

## ディレクトリ構成

```
crowdworks-agent/
├── README.md
├── CLAUDE.md
└── .cursor/
    └── skills/
        └── crowdworks/
            └── SKILL.md    ← メインスキル定義
```
