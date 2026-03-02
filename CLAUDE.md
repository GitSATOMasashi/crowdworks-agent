# crowdworks-agent

CrowdWorks の案件検索・提案文生成・応募フォーム入力を Cursor Agent + browser MCP で自動化するスキル。

## 機能

- **Phase 1**: キーワード/カテゴリで案件を一括検索し、10件をブラウザタブで同時展開
- **Phase 2**: ユーザーが選んだ案件に対して提案文を自動生成し、応募フォームに入力（送信はユーザーが手動で行う）

## 前提条件

- Cursor IDE + browser MCP (`cursor-ide-browser`) が有効であること
- CrowdWorks アカウント（応募時にブラウザでログイン済みであること）

## 使い方

Cursor Agent に以下のように指示する:

- 「クラウドワークスで AI 案件を10件探して」
- 「CW で案件探して」

スキルが自動的にトリガーされ、検索 → タブ展開 → 応募ループが開始される。

## ディレクトリ構成

```
crowdworks-agent/
├── CLAUDE.md                          ← このファイル
└── .cursor/
    └── skills/
        └── crowdworks/
            └── SKILL.md               ← メインスキル定義
```

## 関連

- `client-work/tools/scout/config.mjs` — フィルタキーワード・スキップワードの定義元
- `client-work/tools/scout/apply-message-4852692.txt` — 提案文テンプレートの参考元
