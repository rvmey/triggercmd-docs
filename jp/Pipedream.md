# Pipedream

Pipedreamを使って、TRIGGERcmdコマンドの自動実行が可能です。TRIGGERcmd経由でコマンドを実行するワークフローを作成しましょう。

詳細は公式ドキュメントまたはサポートフォーラムをご覧ください。

Pipedreamは統合・自動化プラットフォームで、TRIGGERcmdコマンドを自動実行するワークフローを作成できます。

TRIGGERcmd APIにHTTPリクエストを送信してコマンドを実行するワークフローを作成してください。

統合の詳細は[TRIGGERcmd APIドキュメント](./API/TriggerCommand.md)をご覧ください。

**PipedreamでのHTTPリクエスト例:**

1. ワークフローに「HTTPリクエスト」ステップを追加します。
2. TRIGGERcmd APIのURLを使用し、必要なパラメータを入力します。
3. ワークフローを保存してテストします。
