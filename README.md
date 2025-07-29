# Slackエラー通知システム (Next.js 14, Fastify, tRPC)

このプロジェクトは、Next.js 14アプリケーションに統合されたSlackエラー通知システムです。バックエンドにはFastifyとtRPCを利用しています。

サーバーサイドで発生した例外を自動的に捕捉し、デバッグに役立つ詳細な通知を、指定されたSlackチャンネルに送信することを目的としています。また、エラーではないシステムイベント（例：リソース残量警告）もSlackに通知する汎用的な機能を提供します。

## 🚀 はじめに

### 1. 環境変数の設定

プロジェクトルートに `.env.local` ファイルを作成し、以下の環境変数を設定してください。

```
SLACK_BOT_TOKEN=xoxb-YOUR_SLACK_BOT_TOKEN
SLACK_CHANNEL_ID=YOUR_SLACK_CHANNEL_ID
```

*   `SLACK_BOT_TOKEN`: Slack APIで取得したボットトークン (`xoxb-...`)。
*   `SLACK_CHANNEL_ID`: エラー通知を送信したいSlackチャンネルのID。

### 2. 依存関係のインストール

プロジェクトのルートディレクトリで、以下のコマンドを実行して依存関係をインストールします。

```bash
pnpm install
```

### 3. 開発サーバーの起動

以下のコマンドを実行して、カスタムFastifyサーバーを起動します。このサーバーがNext.jsアプリケーションをホストします。

```bash
pnpm dev
```

このコマンドは `nodemon` を使用しており、TypeScriptファイルの変更を自動的に検知し、コンパイルとサーバーの再起動を行います。これにより、開発中にTypeScriptのソースコードを直接編集しながら、変更が即座に反映される快適な開発体験を提供します。

ブラウザで [http://localhost:3000](http://localhost:3000) を開くと、アプリケーションが表示されます。

## 🧪 動作確認

1.  ブラウザで [http://localhost:3000](http://localhost:3000) にアクセスします。
2.  **エラー通知の確認**:
    ページ下部にある「**Throw Test Error**」ボタンをクリックします。設定したSlackチャンネルにエラー通知が送信されることを確認してください。メインメッセージと、スレッド内のスタックトレースファイルが送信されていれば成功です。
3.  **イベント通知の確認**:
    「**Send Event Notification**」ボタンをクリックします。設定したSlackチャンネルに「[ResourceWarning] 残りのリソースが少なくなっています。」というメッセージが送信されることを確認してください。

## 📚 詳細情報

*   [Next.js Documentation](https://nextjs.org/docs)
*   [Fastify Documentation](https://www.fastify.io/docs/latest/)
*   [tRPC Documentation](https://trpc.io/docs)
*   [@slack/web-api Documentation](https://slack.dev/node-slack-sdk/web-api)
