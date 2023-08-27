# Trigger Command

This API will trigger a command on one of your computers.

In this example, assuming your Notepad command has parameters enabled, it will launch Notepad with parameter MyNote on your "laptop" computer.

```
import requests

url = "https://www.triggercmd.com/api/run/trigger"
json = {
    "computer": "laptop",
    "trigger": "notepad",
    "params": "MyNote"
}

headers = {
    "Authorization": "Bearer <your token>"
}

r = requests.post(url, headers=headers, json=json)
```

For authentication, use a token from the [Instructions](https://www.triggercmd.com/user/computer/create) page.