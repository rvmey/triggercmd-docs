## Creazione comandi

Il modo più semplice per aggiungere o modificare comandi è con l'editor GUI dei comandi mostrato di seguito.

![Editor GUI](./images/windows-command.png)

| Campo | Descrizione |
| --- | ----------- |
| Trigger | Il nome del tuo trigger |
| Command | Il comando che verrà eseguito quando attivato |
| Off Command | Il comando che verrà eseguito quando il parametro è "off" (richiede che Allow Parameters sia attivo) |
| Ground | Agente in primo piano o in background |
| Voice | Cosa dirai ad Alexa o Google Assistant |
| Voice/MCP Reply | Le vecchie skill conversazionali di Alexa dicono questo in risposta, e MCP riceverà il risultato se hai {{result}} in questo campo |
| MCP Tools Description | Indica all'assistente IA cosa fa questo comando e come utilizzare i suoi parametri — vedi [Server MCP](./MCPServer.md) |
| Allow Parameters | Se consentire i parametri |
| Quote Parameters | Se attivo, i parametri vengono racchiusi tra virgolette in modo da essere passati come un'unica stringa anziché come parametri multipli |
| Icon | Un'icona per il comando — scegline una dalla lista o incolla la tua |

## Dettagli

Il campo **Trigger** è essenzialmente un nome per il tuo comando, ma Alexa e Google Assistant non usano questo nome. Usano il campo **Voice** per trovare il tuo trigger.

Il campo **Off Command** è disponibile solo quando **Allow Parameters** è attivo, poiché verrà eseguito solo se il parametro è "off".

Imposta **Ground** su background solo se hai installato l'agente in background. Puoi installare l'agente in background su Windows e Linux (incluso Raspberry Pi), ma non su Mac. L'agente in background si avvia all'accensione del computer anziché al login, quindi puoi usarlo per riavviare anche se non sei connesso.

Il campo **Voice/MCP Reply** è utilizzato dalle vecchie skill "conversazionali" di Alexa e da [MCP](./MCPServer.md). Le skill conversazionali di Alexa sono:
* [TRIGGERcmd](https://www.amazon.com/gp/product/B06XFN2TZN)
* [TRIGGER command](https://www.amazon.com/gp/product/B074TV61DK) 
* [TC](https://www.amazon.com/gp/product/B0BMGG4SHS).  

La skill/azione "[TRIGGERcmd Smart Home](https://www.amazon.com/gp/product/B07P1MMFRP)" **non** utilizza il campo **Voice/MCP Reply**.

Il campo **Voice/MCP Reply** può includere i segnaposto {{trigger}}, {{computer}} e [{{result}}](https://www.triggercmd.com/forum/topic/422/have-alexa-or-google-assistant-say-the-result-of-a-command). Il segnaposto {{result}} è dove Alexa dice il risultato del tuo comando, e dove MCP riceve il risultato del tuo comando.

Per maggiore sicurezza, i tuoi comandi **non** sono archiviati nel cloud. Sono archiviati solo sul tuo computer in un file chiamato commands.json. Puoi trovarlo nella cartella .TRIGGERcmdData nella cartella home del tuo utente. Potresti voler fare un backup nel caso in cui il tuo disco rigido si guasti.
