# Comando de Disparo

Essa API irá acionar um comando em um dos seus computadores.

Neste exemplo, supondo que o seu comando do notepad tenha os parâmetros habilitados, ele irá abrir o notepad com o parâmetro MyNote no seu computador "laptop".

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

Para autenticação, use um token da página de
[Instruções](https://www.triggercmd.com/user/computer/create).