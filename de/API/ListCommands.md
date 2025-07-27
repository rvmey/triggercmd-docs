# Befehle auflisten

Diese API listet Ihre Befehle auf.

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <Ihr Token>"
}

r = requests.post(url, headers=headers)
```

Für die Authentifizierung verwenden Sie ein Token von der Seite [Anleitung](https://www.triggercmd.com/user/computer/create).
