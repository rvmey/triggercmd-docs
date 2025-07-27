# コマンド実行

このAPIはあなたのコンピューターの1台でコマンドを実行します。

この例では、Notepadコマンドでパラメータが有効になっている場合、「ノートパソコン」コンピューターでMyNoteパラメータ付きでNotepadが起動します。

```
import requests

url = "https://www.triggercmd.com/api/run/trigger"
json = {
    "computer": "laptop",
    "trigger": "notepad",
    "params": "MyNote"
}

headers = {
    "Authorization": "Bearer <あなたのトークン>"
}

r = requests.post(url, headers=headers, json=json)
```

認証には[手順](https://www.triggercmd.com/user/computer/create)ページのトークンを使用してください。
