# コマンド一覧

このAPIはあなたのコマンドを一覧表示します。

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <あなたのトークン>"
}

r = requests.post(url, headers=headers)
```

認証には[手順](https://www.triggercmd.com/user/computer/create)ページのトークンを使用してください。
