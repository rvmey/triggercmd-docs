# コマンドラインインターフェースツール

## tcmdのダウンロード

* [Windows 64bit（最も一般的）](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-amd64.exe)
* [Windows 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-386.exe)
* [Mac 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-darwin-amd64)
* [Linux 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-386)
* [Linux 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-amd64)
* [Linux arm（例：Raspberry PiやOrange Pi）](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-arm)

ダウンロード後、tcmdまたはWindowsの場合はtcmd.exeにリネームしてください。

**/usr/local/bin**や**C:\Windows**、またはPATH環境変数に含まれる他のフォルダーに移動すると、どのフォルダーからでも実行できるようになります。

## tcmdの使い方

ヘルプテキストを表示するには次のコマンドを実行してください：
```
tcmd -h
```

```
NAME:
    tcmd - TRIGGERcmdアカウント内のコンピューターでコマンドを実行
  USAGE:
    tcmd [options]

  OPTIONS:
    --trigger value, -t value   実行したいコマンドのトリガー名
    --computer value, -c value  コンピューター名（デフォルトの場合は空欄）
    --params value, -p value    リモートコマンドに追加するパラメータ
    --panel value, -P value     使用するパネル名
    --button value, -b value    「押す」パネルボタン名
    --list, -l                  コマンド一覧を表示
    --listpanels, -L            パネル一覧を表示
    --pair                      ペアコードでログイン
    --help, -h                  ヘルプを表示
    --version, -v               バージョンを表示
```

## ソースコード

tcmdツールのGoソースコードはGithubの[こちら](https://github.com/rvmey/triggercmdGOclient)で閲覧できます。

## Youtube動画

**tcmd**ツールの動作例は[このYoutube動画](https://www.youtube.com/watch?v=q0Uu4SNFKFY)をご覧ください。
