# muse-artifact-skill

Muse Code用のskill。`/artifact`で自 contained なHTML artifactを作り、
一覧ページで管理し、ローカルサーバーでホストしてURLを返す。

## 動作

- `/artifact` + 作りたい内容で1枚のHTMLを `artifacts/<slug>.html` に作成(CSS/JSはインライン)
- 各ページの上部に一覧へのリンクを付与
- `artifacts/index.html` に一覧エントリを追加・更新
- `artifacts/` を分離したローカル静的サーバーでホストし、到達確認後にURLを返す

## 導入

このリポジトリをcloneし、Muse Codeのプロジェクトskillとして配置:

```sh
cp -r muse-artifact-skill /path/to/your-project/.agents/skills/artifact
muse skills validate /path/to/your-project/.agents/skills/artifact --json
```

## 開発フロー

インストール先(`~/.config/muse/skills/artifact/`)は直接編集しない。
このリポジトリを作業コピーとして編集する:

```sh
# 編集後
muse skills validate . --json
git commit -m "..." SKILL.md
git push
muse skills update artifact
```

## 要件

- ホスト用に `python3` を使用
- セッション終了後も残す分離起動に `setsid` を使用(Linuxは標準、macOSは `brew install util-linux`)

## ライセンス

MIT
