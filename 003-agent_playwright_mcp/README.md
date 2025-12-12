# Playwright MCPを使おう

## このアプリは？

PythonでWeb APIサーバを作り、Reactでフロントエンドを作られている。

TODOアプリを作ってあり、以下のコマンドで起動する

```
# APIサーバ(Python)の起動
uv run python -m todo_api.server.api

# フロントエンドサーバ(React)の起動
cd todo_frontend && npm start
```

## GitHub MCP Registryからインストール

[https://github.com/mcp](https://github.com/mcp)

ここからインストール。

できない場合は、拡張機能ビューから`@mcp`と入れて検索。

チャット画面のツールから有効化する。

```
#playwright を使って、http://localhost:5173 にアクセスし、以下の手順を行って。
なお、サーバは起動済みだよ。

1. Task Title の入力欄に「新しいタスクのテスト」と入力する
2. 「Add」ボタンをクリックする
3. タスクの一覧として、「新しいタスクのテスト」が表示されることを確認する
```
