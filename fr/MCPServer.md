# Serveur MCP TRIGGERcmd — Guide de l'utilisateur

Le serveur MCP de TRIGGERcmd permet aux assistants IA — Claude, ChatGPT, ou
tout outil qui parle le [Model Context Protocol](https://modelcontextprotocol.io) —
de voir vos commandes TRIGGERcmd et de les exécuter sur vos ordinateurs,
simplement en discutant en langage courant. Par exemple, vous pouvez demander
à votre assistant « Que peux-tu exécuter sur mon ordinateur de bureau ? » ou
« Éteins les lumières du sous-sol », et il trouvera la bonne commande
TRIGGERcmd et la déclenchera pour vous.

Il fonctionne déjà pour chaque compte TRIGGERcmd — il n'y a rien à installer
sur votre ordinateur pour l'utiliser.

---

## Connecter un assistant IA

Il existe deux façons de se connecter, selon ce que prend en charge votre
outil IA.

### Option 1 — HTTP Streamable (recommandée)

La plupart des produits IA modernes qui prennent en charge les « serveurs MCP
distants » ou les « connecteurs » (Claude.ai, ChatGPT, etc.) peuvent
communiquer directement avec TRIGGERcmd via Internet. Lorsque votre outil IA
vous demande une URL de serveur MCP, indiquez :

```
https://www.triggercmd.com/mcp
```

Le serveur prend en charge OAuth2 standard, donc lorsque vous l'ajoutez comme
connecteur, votre outil IA ouvrira automatiquement une page de
connexion/autorisation TRIGGERcmd. Approuvez-la une fois, et l'assistant
pourra alors voir et exécuter les commandes de votre compte TRIGGERcmd.

> **Utilisateurs de ChatGPT :** TRIGGERcmd est également disponible sous forme
> d'application prête à l'emploi — installez-la simplement depuis
> **https://chatgpt.com/apps/triggercmd/asdk_app_694c84d39cb881918c6d181ae69e33fc**
> et connectez-vous avec votre compte TRIGGERcmd. Aucune URL ni configuration
> n'est nécessaire.

### Option 2 — Serveur stdio local

Si votre outil IA ne prend en charge que les serveurs MCP exécutés localement
(« stdio ») — par exemple certaines configurations de Claude Desktop —,
utilisez plutôt le projet complémentaire :

**https://github.com/rvmey/triggercmd-mcp-stdio**

Il s'exécute comme un petit processus sur votre propre ordinateur, se connecte
avec le jeton de votre compte TRIGGERcmd, et expose exactement les mêmes
outils décrits ci-dessous.

---

## Ce que l'assistant peut faire une fois connecté

Une fois connecté, l'assistant obtient l'accès à des outils limités à votre
compte TRIGGERcmd — il peut voir tous les ordinateurs et toutes les commandes
que vous avez, et les déclencher en votre nom. Il existe trois types d'outils :

### `list_commands`

Demande « quelles commandes ai-je ? ». Il renvoie chaque commande de tous vos
ordinateurs, y compris :

- sur quel ordinateur elle se trouve
- son nom
- sa phrase de déclenchement vocal (le cas échéant)
- sa description d'outil MCP (le cas échéant — voir « Outils dynamiques par
  commande » ci-dessous)

Votre assistant l'appelle généralement en premier lorsque vous demandez
quelque chose comme « Quelles commandes TRIGGERcmd ai-je ? » ou « Que puis-je
exécuter sur mon PC de bureau ? », afin de savoir ce qui est disponible avant
de faire quoi que ce soit.

### `run_command`

L'outil polyvalent « tout exécuter ». Il fonctionne pour **n'importe quelle**
commande sur **n'importe lequel** de vos ordinateurs, que cette commande ait
ou non une description d'outil MCP configurée.

L'assistant renseigne :

- `computer` — le nom de l'ordinateur qui possède la commande
- `command` — le nom de la commande à exécuter
- `parameters` *(facultatif)* — du texte supplémentaire à transmettre, pour
  les commandes qui acceptent des paramètres

Vous verrez généralement cela utilisé lorsque vous demandez à l'assistant
d'exécuter quelque chose par son nom, par exemple « Exécute 'Bonne nuit' sur
mon PC de chambre » ou « Déclenche Roku Play sur l'ordinateur du salon ».

### Outils dynamiques par commande

Pour toute commande où vous avez renseigné une **MCP Tool Description**,
TRIGGERcmd crée automatiquement un outil dédié rien que pour cette commande,
nommé quelque chose comme `run_<ordinateur>_<commande>` (en minuscules, avec
les espaces et les caractères spéciaux transformés en tirets bas).

Par exemple, une commande nommée « Play Music » sur un ordinateur nommé
« Office PC » apparaît à l'assistant comme un outil nommé
`run_office_pc_play_music`, décrit avec le texte que vous avez saisi dans sa
MCP Tool Description — par exemple, *« Joue ma playlist de travail sur les
enceintes du bureau. »*

**Pourquoi c'est utile :** donner à une commande son propre outil avec une
description claire et précise aide l'assistant à :

- trouver et choisir rapidement la *bonne* commande, au lieu de deviner à
  partir d'un nom de commande court ou générique
- savoir comment formater les paramètres de la commande, et quand les utiliser
- vous expliquer, en langage simple, ce qu'il s'apprête à faire avant de
  l'exécuter

Si la commande a également l'option **Allow Params** activée, son outil
dynamique accepte une valeur `parameters` facultative, tout comme
`run_command`. Si Allow Params est désactivée, l'outil dynamique ne prend
aucune entrée — il exécute simplement la commande.

---

## Donner à l'une de vos commandes son propre outil

Pour faire apparaître une commande aux assistants IA comme son propre outil
nommé :

1. Ouvrez les paramètres de la commande (dans le `commands.json` de votre
   agent TRIGGERcmd local, ou là où vous gérez cette commande).
2. Renseignez **MCP Tool Description** avec une phrase courte et claire
   décrivant ce que fait la commande et/ou quand elle doit être utilisée —
   par exemple « Éteint toutes les lumières du sous-sol » ou « Redémarre le
   serveur Plex ».
3. *(Facultatif)* Activez **Allow Params** si la commande doit accepter du
   texte comme paramètre venant de l'assistant.
4. Enregistrez et laissez l'agent se synchroniser. Votre liste de commandes
   TRIGGERcmd affichera une icône 🔧 à côté de toute commande possédant une
   description d'outil MCP.

La prochaine fois qu'un assistant listera vos outils, il verra un outil dédié
pour cette commande, décrit comme vous l'avez écrit.

### Conseils pour rédiger de bonnes descriptions

- Indiquez *ce qui* se passe : « Allume les lumières du sous-sol, ou ajuste
  la luminosité. Le paramètre peut être un pourcentage de luminosité comme
  50 », et non simplement « Lumières ».
- Restez concis — une ou deux phrases suffisent largement. L'assistant la lit
  chaque fois qu'il décide d'utiliser ou non l'outil.
