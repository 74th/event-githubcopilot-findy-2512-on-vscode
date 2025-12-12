## システム概要
- Flask 製の API (`todo_api/`) と React + TypeScript 製の SPA (`todo_frontend/`) から成る最小構成の TODO アプリです。

## 利用ツール
- Pythonのライブラリ管理: uv
- Nodejsのパッケージ管理: npm

## プロジェクト構成
- todo_api/ : バックエンドAPIサーバ
  - domain/ : ビジネスロジック層
    - entity/ : エンティティ定義
    - usecase/ : ユースケース実装
  - memdb/ : インメモリDB実装
  - server/ : Flaskサーバ実装
- todo_frontend/ : フロントエンドSPA
  - src/
    - api/ : FlaskAPI呼び出し
    - domain/ : ビジネスロジック層
      - entity/ : エンティティ定義
    - App.tsx : ルートコンポーネント
    - views/
      - newTask.tsx : タスク追加画面
      - taskList.tsx : タスク一覧画面

## プロジェクト構成のポリシー
- エンティティ定義にはビジネスロジックは持たせない
- エンティティ定義は、バックエンドとフロントエンドで両方定義するが、JSONで同じ名前のオブジェクトをやりとりできるようにする
- ビジネスロジックはフロントエンドでは持たせず、バックエンドで実装する
  - 例: 完了していないタスクを表示するためのフィルタリングはバックエンドで行う
- HTTP ハンドラは極力薄く保ち、状態遷移やバリデーションは `OperationInteractor` に閉じ込めます。
- todo_api/domain/usecase にコードを追加する場合はユニットテストを実装する必要がある
  - operations.pyの場合には、operations_tes.pyにテストコードを実装する
  - todo_api/domain/usecase/operations_test.py

## 主要コンポーネント
- メインの1つのタスクを示すデータクラス
  - todo_api/domain/entity/task.py
  - todo_frontend/src/domain/entity/task.ts
- API
  - todo_api/server/api.py
  - todo_frontend/src/api/task.ts
- 画面
  - todo_frontend/src/views/newTask.tsx : タスク追加画面
  - todo_frontend/src/views/taskList.tsx : タスクカードと一覧画面

## 開発ワークフロー
- 開発サーバ起動
  - バックエンド: `uv run python -m todo_api.server.api`（ポート 8080。`todo_api/public` を自動 Serve）。
  - フロントエンド: `cd todo_frontend && npm start`。ポート 3000 で Flask にプロキシします。
- バックエンド
  - フォーマット: `uv run ruff format .`
  - リント: `uv run ruff check .`
  - テスト: `uv run python -m unittest discover -p "*_test.py" -v`
- フロントエンド
  - リント: `cd todo_frontend && npm run lint`
  - フォーマットも `npm run lint-fix` で行う
- コード修正後は、フォーマット、リント、テストを実行すること
