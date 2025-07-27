# Comando di attivazione

Questa API attiverà un comando su uno dei tuoi computer.

In questo esempio, supponendo che il tuo comando Notepad abbia i parametri abilitati, aprirà Notepad con il parametro MyNote sul computer "portatile".

```
import requests

url = "https://www.triggercmd.com/api/run/trigger"
json = {
    "computer": "portatile",
    "trigger": "notepad",
    "params": "MyNote"
}

headers = {
    "Authorization": "Bearer <il tuo token>"
}

r = requests.post(url, headers=headers, json=json)
```

Per l'autenticazione, utilizza un token dalla pagina [Istruzioni](https://www.triggercmd.com/user/computer/create).
