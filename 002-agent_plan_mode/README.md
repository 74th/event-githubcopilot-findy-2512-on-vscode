# AgentモードのPlanモードを使おう

## このアプリは？

PythonでWeb APIサーバを作り、Reactでフロントエンドを作られている。

TODOアプリを作ってあり、以下のコマンドで起動する

```
# APIサーバ(Python)の起動
uv run python -m todo_api.server.api

# フロントエンドサーバ(React)の起動
cd todo_frontend && pnpm start
```

## 実行してみるプロンプト

Planモードにする

タスク一覧中の1つのタスクのカードは、今は"done"ボタンを押すと完了される。
カードの中に"Start"ボタンを追加して、押すとタスクが"in progress"になるようにして。
