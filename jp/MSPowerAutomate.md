# Microsoft Power Automate

TRIGGERcmdをMicrosoft Power Automateと連携させることで、コンピューター上のコマンド実行を自動化できます。

詳細は公式ドキュメントまたはサポートフォーラムをご覧ください。

Microsoft Power Automateを使って、TRIGGERcmdコマンドを自動実行するワークフローを作成できます。

TRIGGERcmd APIにHTTPリクエストを送信してコマンドを実行するフローを作成してください。

統合の詳細は[TRIGGERcmd APIドキュメント](./API/TriggerCommand.md)をご覧ください。

**Power AutomateでのHTTPリクエスト例:**

1. フローに「HTTPリクエスト」アクションを追加します。
2. TRIGGERcmd APIのURLを使用し、必要なパラメータを入力します。
3. フローを保存してテストします。
