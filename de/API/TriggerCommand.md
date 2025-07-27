# Befehl auslösen

Diese API löst einen Befehl auf einem Ihrer Computer aus.

In diesem Beispiel wird, vorausgesetzt Ihr Notepad-Befehl hat Parameter aktiviert, Notepad mit dem Parameter MyNote auf Ihrem Computer "Laptop" gestartet.

```
import requests

url = "https://www.triggercmd.com/api/run/trigger"
json = {
    "computer": "laptop",
    "trigger": "notepad",
    "params": "MyNote"
}

headers = {
    "Authorization": "Bearer <Ihr Token>"
}

r = requests.post(url, headers=headers, json=json)
```

Für die Authentifizierung verwenden Sie ein Token von der Seite [Anleitung](https://www.triggercmd.com/user/computer/create).
