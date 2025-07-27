# Interrupteurs virtuels pour maison intelligente

## Intégrations qui créent des interrupteurs virtuels

* Skill Alexa TRIGGERcmd Smart Home
* Action Google Assistant TRIGGERcmd Smart Home
* Intégration TRIGGERcmd Samsung SmartThings

## Création et nommage des interrupteurs

Les champs **voix** de vos commandes et ordinateurs déterminent le nom de vos interrupteurs virtuels. Si ces champs sont vides, un interrupteur virtuel peut ne pas être créé.

Pour qu’un interrupteur virtuel soit créé, chaque commande doit avoir une valeur dans le champ **voix** (ex : « calculatrice »), car cette valeur est utilisée dans le nom de l’interrupteur virtuel.

Pour qu’un interrupteur virtuel soit créé, chaque ordinateur doit aussi avoir une valeur dans le champ **voix** (ex : « portable »), car cette valeur est utilisée dans le nom de l’interrupteur virtuel (exemple : **calculatrice sur portable**).

L’exception concerne votre ordinateur par défaut. Le champ voix de votre ordinateur par défaut peut être vide car il n’est pas utilisé dans les noms de vos interrupteurs virtuels. Seules les valeurs du champ voix de la commande sont utilisées (exemple : **calculatrice**).

Le premier ordinateur de votre compte est votre ordinateur par défaut, mais si vous avez plusieurs ordinateurs, vous pouvez changer l’ordinateur par défaut.

Les interrupteurs virtuels pour votre ordinateur par défaut sont :

1. Nommés uniquement avec le champ voix de la commande (ex : calculatrice).
1. Créés que le champ voix de l’ordinateur soit vide ou non.

Les interrupteurs virtuels pour vos ordinateurs non par défaut sont :

1. Nommés avec les champs voix de la commande et de l’ordinateur (ex : calculatrice sur portable).
1. Seront créés même si le champ voix de votre ordinateur par défaut est vide.

# Allumer et éteindre les interrupteurs virtuels

Si votre commande a « Autoriser les paramètres » activé et que le champ « Commande d’arrêt » est vide, lorsque vous actionnez l’interrupteur virtuel, la commande sera exécutée avec **on** ou **off** comme paramètre.

Ou, si vous mettez une commande dans le champ « Commande d’arrêt », elle sera exécutée lorsque vous éteignez l’interrupteur.

Si « Autoriser les paramètres » est désactivé, la commande du champ « Commande » sera exécutée, que vous allumiez ou éteigniez l’interrupteur.

# Conseils pour éviter les problèmes lors de l’exécution de vos commandes avec Alexa ou Google Assistant

N’utilisez pas les noms de vos pièces domotiques dans les mots de voix. Cela complique la tâche pour qu’ils sachent quelle commande vous vouliez déclencher.
