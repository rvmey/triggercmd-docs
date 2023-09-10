# Listar Comandos

Essa API irá listar os seus comandos.

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <your token>"
}

r = requests.post(url, headers=headers, json=json)
```

Para autenticação, use um token da página de 
 [Instruções](https://www.triggercmd.com/user/computer/create).