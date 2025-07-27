# Déclencher une Commande

Cette API permet de déclencher une commande sur l'un de vos ordinateurs.

Dans cet exemple, en supposant que votre commande notepad ait les paramètres activés, elle ouvrira le notepad avec le paramètre MyNote sur votre ordinateur "portable".

```
import requests

url = "https://www.triggercmd.com/api/run/trigger"
json = {
    "computer": "portable",
    "trigger": "notepad",
    "params": "MyNote"
}

headers = {
    "Authorization": "Bearer <votre token>"
}

r = requests.post(url, headers=headers, json=json)
```

Pour l'authentification, utilisez un token de la page [Instructions](https://www.triggercmd.com/user/computer/create).
