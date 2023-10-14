# Comandos de Lista

Esta API enumerará sus comandos.

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <your token>"
}

r = requests.post(url, headers=headers, json=json)
```

Para la autenticación, use un token de la página de [Instrucciones](https://www.triggercmd.com/user/computer/create).