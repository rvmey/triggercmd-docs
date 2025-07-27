# Elenca comandi

Questa API elencherà i tuoi comandi.

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <il tuo token>"
}

r = requests.post(url, headers=headers)
```

Per l'autenticazione, utilizza un token dalla pagina [Istruzioni](https://www.triggercmd.com/user/computer/create).
