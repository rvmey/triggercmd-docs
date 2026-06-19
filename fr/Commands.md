## Création de commandes

La façon la plus simple d'ajouter ou de modifier des commandes est d'utiliser l'éditeur de commandes GUI illustré ci-dessous.

![Éditeur GUI](./images/windows-command.png)

| Champ | Description |
| --- | ----------- |
| Trigger | Le nom de votre déclencheur |
| Command | La commande qui sera exécutée lors du déclenchement |
| Off Command | La commande qui sera exécutée lorsque le paramètre est "off" (nécessite que Allow Parameters soit activé) |
| Ground | Agent en premier plan ou en arrière-plan |
| Voice | Ce que vous direz à Alexa ou Google Assistant |
| Voice/MCP Reply | Les anciennes skills conversationnelles d'Alexa disent ceci en retour, et MCP recevra le résultat si vous avez {{result}} dans ce champ |
| MCP Tools Description | Indique à l'assistant IA ce que fait cette commande et comment utiliser ses paramètres — voir [Serveur MCP](./MCPServer.md) |
| Allow Parameters | Autoriser ou non les paramètres |
| Quote Parameters | Si activé, les paramètres sont entourés de guillemets pour être transmis comme une seule chaîne au lieu de plusieurs paramètres |
| Icon | Une icône pour la commande — choisissez-en une dans la liste ou collez la vôtre |

## Détails

Le champ **Trigger** est essentiellement un nom pour votre commande, mais Alexa et Google Assistant n'utilisent pas ce nom. Ils utilisent le champ **Voice** pour trouver votre déclencheur.

Le champ **Off Command** n'est disponible que lorsque **Allow Parameters** est activé, car il ne s'exécute que si le paramètre est "off".

Ne définissez **Ground** sur arrière-plan que si vous avez installé l'agent en arrière-plan. Vous pouvez installer l'agent en arrière-plan sur Windows et Linux (y compris Raspberry Pi), mais pas sur Mac. L'agent en arrière-plan démarre au démarrage de votre ordinateur plutôt qu'à la connexion, vous pouvez donc l'utiliser pour redémarrer même si vous n'êtes pas connecté.

Le champ **Voice/MCP Reply** est utilisé par les anciennes skills "conversationnelles" d'Alexa et par [MCP](./MCPServer.md). Les skills conversationnelles d'Alexa sont :
* [TRIGGERcmd](https://www.amazon.com/gp/product/B06XFN2TZN)
* [TRIGGER command](https://www.amazon.com/gp/product/B074TV61DK) 
* [TC](https://www.amazon.com/gp/product/B0BMGG4SHS).  

La skill/action "[TRIGGERcmd Smart Home](https://www.amazon.com/gp/product/B07P1MMFRP)" n'utilise **pas** le champ **Voice/MCP Reply**.

Le champ **Voice/MCP Reply** peut inclure les marqueurs {{trigger}}, {{computer}} et [{{result}}](https://www.triggercmd.com/forum/topic/422/have-alexa-or-google-assistant-say-the-result-of-a-command). Le marqueur {{result}} est l'endroit où Alexa dit le résultat de votre commande, et où MCP reçoit le résultat de votre commande.

Pour plus de sécurité, vos commandes ne sont **pas** stockées dans le cloud. Elles sont uniquement stockées sur votre ordinateur dans un fichier appelé commands.json. Vous le trouverez dans votre dossier .TRIGGERcmdData dans le dossier personnel de votre utilisateur. Vous devriez en faire une sauvegarde au cas où votre disque dur tomberait en panne.
