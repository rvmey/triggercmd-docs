# Comando de Disparo

Esta API activará un comando en una de sus computadoras.

En este ejemplo, suponiendo que su comando Bloc de notas tenga parámetros habilitados, iniciará el Bloc de notas con el parámetro MyNote en su computadora "laptop".

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

Para la autenticación, use un token de la página de [Instrucciones](https://www.triggercmd.com/user/computer/create).