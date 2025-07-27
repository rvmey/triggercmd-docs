# Lister les commandes

Cette API permet de lister vos commandes.

```
import requests

url = "https://www.triggercmd.com/api/command/list"

headers = {
    "Authorization": "Bearer <votre token>"
}

r = requests.post(url, headers=headers)
```

Pour l’authentification, utilisez un token de la page [Instructions](https://www.triggercmd.com/user/computer/create).
