# Interruttori virtuali per la casa intelligente

## Integrazioni che creano interruttori virtuali

* Skill Alexa TRIGGERcmd Smart Home
* Azione Google Assistant TRIGGERcmd Smart Home
* Integrazione TRIGGERcmd Samsung SmartThings

## Creazione e denominazione degli interruttori

Sia i comandi che i computer hanno un campo **voce** che determina il nome dei tuoi interruttori virtuali. Se questi campi voce sono vuoti, un interruttore virtuale potrebbe non essere creato.

Per creare un interruttore virtuale, ciascun comando deve avere un valore nel campo **voce** (ad esempio "calcolatrice"), perché il valore del campo voce del comando viene utilizzato nel nome dell'interruttore virtuale.

Per creare un interruttore virtuale, anche ciascun computer deve avere un valore nel campo **voce** (ad esempio "portatile"), perché il valore del campo voce del computer viene utilizzato nel nome dell'interruttore virtuale (esempio: **calcolatrice su portatile**).

L'eccezione è il computer predefinito. Il campo voce del computer predefinito può essere vuoto perché non viene utilizzato nei nomi degli interruttori virtuali. Vengono invece utilizzati solo i valori del campo voce del comando (esempio: **calcolatrice**).

Il primo computer nel tuo account è il computer predefinito, ma se hai più computer puoi cambiare il computer predefinito.

Gli interruttori virtuali per il computer predefinito sono:

1. Nominati solo con il campo voce del comando (es: calcolatrice).
1. Creati sia che il campo voce del computer sia vuoto o meno.

Gli interruttori virtuali per i computer non predefiniti sono:

1. Nominati con i campi voce del comando e del computer (es: calcolatrice su portatile).
1. Verranno creati anche se il campo voce del computer predefinito è vuoto.

# Accendere e spegnere gli interruttori virtuali

Se il comando ha "Consenti parametri" impostato su vero e il campo "Comando di spegnimento" è vuoto, quando attivi o disattivi l'interruttore virtuale, il comando verrà eseguito con **on** o **off** come parametro.

Oppure, se inserisci un comando nel campo "Comando di spegnimento", verrà eseguito quando spegni l'interruttore.

Se "Consenti parametri" è impostato su falso, il comando nel campo "Comando" verrà eseguito sia che tu accenda o spenga l'interruttore.

# Suggerimenti per evitare problemi con Alexa o Google Assistant

Non utilizzare i nomi delle stanze della tua casa intelligente nelle parole di attivazione vocale. Questo rende più difficile capire quale comando volevi attivare.
