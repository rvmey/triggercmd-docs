# List Commands

This API will list your commands.

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <your token>"
}

r = requests.post(url, headers=headers)
```

For authentication, use a token from the [Instructions](https://www.triggercmd.com/user/computer/create) page.