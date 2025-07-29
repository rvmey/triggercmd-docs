# コマンド

コマンドは、TRIGGERcmdを通じてコンピューター上で実行できるアクションです。必要に応じてコマンドを追加、編集、削除できます。

詳細は公式ドキュメントまたはサポートフォーラムをご覧ください。

## コマンドの作成方法

コマンドを追加または編集する最も簡単な方法は、以下に示すGUIコマンドエディターを使用することです。

![GUIエディター](./images/gui-editor.png)

| フィールド | 説明 |
| --- | --- |
| Trigger | トリガーの名前 |
| Command | トリガーされたときに実行されるコマンド |
| Off Command | パラメータが「off」の場合に実行されるコマンド |
| Ground | フォアグラウンドまたはバックグラウンドエージェント |
| Voice | AlexaやGoogle Assistantに話しかける言葉 |
| Voice Reply | AlexaやGoogle Assistantが返答する言葉 |
| Allow Parameters | パラメータを許可するかどうか |

## 詳細

**Trigger** フィールドはコマンドの名前ですが、AlexaやGoogle Assistantはこの名前を使用しません。**Voice** フィールドを使ってトリガーを見つけます。

**Off Command** フィールドは、**Allow Parameters** が有効な場合のみ利用可能で、パラメータが「off」の場合に実行されます。

**Ground** をバックグラウンドに設定するのは、バックグラウンドエージェントをインストールしている場合のみです。バックグラウンドエージェントはWindowsやLinux（Raspberry Pi含む）でインストールできますが、Macではできません。バックグラウンドエージェントはコンピューターの起動時に開始されるため、ログインしていなくても再起動などが可能です。

**Voice Reply** フィールドは、以下の「会話型」Alexaスキル専用です：
* [TRIGGERcmd](https://www.amazon.com/gp/product/B06XFN2TZN)
* [TRIGGER command](https://www.amazon.com/gp/product/B074TV61DK)
* [TC](https://www.amazon.com/gp/product/B0BMGG4SHS)

「[TRIGGERcmd Smart Home](https://www.amazon.com/gp/product/B07P1MMFRP)」スキル/アクションは **Voice Reply** フィールドを使用しません。

**Voice Reply** フィールドには {{trigger}}、{{computer}}、および [{{result}}](https://www.triggercmd.com/forum/topic/422/have-alexa-or-google-assistant-say-the-result-of-a-command) プレースホルダーを含めることができます。{{result}} プレースホルダーは、Alexaがコマンドの結果を「会話型」Alexaスキル経由で話す場所です。

セキュリティ向上のため、コマンドはクラウドに保存されません。コマンドはコンピューター上の commands.json ファイルにのみ保存されます。ユーザーのホームフォルダー内の .TRIGGERcmdData フォルダーで見つけることができます。ハードディスク故障に備えてバックアップを取ることをおすすめします。

## コマンドの追加方法

コマンドを追加するには、コンピューターページに移動し、目的のコンピューターを選択して「コマンドを追加」をクリックします。必要な詳細を入力して保存します。

## コマンドの例

一般的なコマンド例：
```
{
  "trigger": "notepad",
  "command": "notepad",
  "voice": "notepad",
  "allowParams": true
}
```
## 編集と削除

コマンドの編集や削除は、コンピューターのコマンドページから行えます。
