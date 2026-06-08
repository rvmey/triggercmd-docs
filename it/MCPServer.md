# Server MCP di TRIGGERcmd — Guida per l'utente

Il server MCP di TRIGGERcmd consente agli assistenti IA — Claude, ChatGPT o
qualsiasi strumento che parli il [Model Context Protocol](https://modelcontextprotocol.io)
— di vedere i tuoi comandi TRIGGERcmd ed eseguirli sui tuoi computer,
semplicemente conversando in linguaggio naturale. Ad esempio, puoi chiedere al
tuo assistente "Cosa puoi eseguire sul mio computer dell'ufficio?" oppure
"Spegni le luci del seminterrato", e lui troverà il comando TRIGGERcmd giusto
e lo attiverà per te.

È già attivo per ogni account TRIGGERcmd — non c'è nulla da installare sul tuo
computer per usarlo.

---

## Collegare un assistente IA

Ci sono due modi per collegarsi, a seconda di cosa supporta il tuo strumento
IA.

### Opzione 1 — HTTP Streamable (consigliata)

La maggior parte dei prodotti IA moderni che supportano "server MCP remoti" o
"connettori" (Claude.ai, ChatGPT, ecc.) può comunicare direttamente con
TRIGGERcmd via Internet. Quando il tuo strumento IA chiede un URL del server
MCP, fornisci:

```
https://www.triggercmd.com/mcp
```

Il server supporta l'OAuth2 standard, quindi quando lo aggiungi come
connettore, il tuo strumento IA aprirà automaticamente una pagina di
accesso/autorizzazione di TRIGGERcmd. Approvala una volta sola, e l'assistente
potrà quindi vedere ed eseguire i comandi del tuo account TRIGGERcmd.

> **Utenti di ChatGPT:** TRIGGERcmd è disponibile anche come app pronta
> all'uso — basta installarla da
> **https://chatgpt.com/apps/triggercmd/asdk_app_694c84d39cb881918c6d181ae69e33fc**
> e accedere con il tuo account TRIGGERcmd. Nessun URL o configurazione
> necessari.

### Opzione 2 — Server stdio locale

Se il tuo strumento IA supporta solo server MCP eseguiti localmente
("stdio") — ad esempio alcune configurazioni di Claude Desktop — usa invece
il progetto complementare:

**https://github.com/rvmey/triggercmd-mcp-stdio**

Funziona come un piccolo processo sul tuo computer, accede con il token del
tuo account TRIGGERcmd ed espone esattamente gli stessi strumenti descritti
qui sotto.

---

## Cosa può fare l'assistente una volta collegato

Una volta collegato, l'assistente ottiene l'accesso a strumenti limitati al
tuo account TRIGGERcmd — può vedere ogni computer e comando che possiedi e
attivarli per tuo conto. Esistono tre tipi di strumenti:

### `list_commands`

Chiede "quali comandi ho?". Restituisce ogni comando presente sui tuoi
computer, incluso:

- su quale computer si trova
- il suo nome
- la sua frase di attivazione vocale (se presente)
- la sua descrizione dello strumento MCP (se presente — vedi "Strumenti
  dinamici per comando" più sotto)

Il tuo assistente di solito chiama questo strumento per primo quando chiedi
qualcosa come "Quali comandi TRIGGERcmd ho?" oppure "Cosa posso eseguire sul
mio PC dell'ufficio?", così sa cosa è disponibile prima di fare qualsiasi
cosa.

### `run_command`

Lo strumento generico per "eseguire qualsiasi cosa". Funziona per
**qualsiasi** comando su **qualsiasi** dei tuoi computer, indipendentemente
dal fatto che quel comando abbia o meno una descrizione dello strumento MCP
configurata.

L'assistente compila:

- `computer` — il nome del computer a cui appartiene il comando
- `command` — il nome del comando da eseguire
- `parameters` *(facoltativo)* — testo aggiuntivo da passare, per i comandi
  che accettano parametri

In genere lo vedrai usato quando chiedi all'assistente di eseguire qualcosa
per nome, ad esempio "Esegui 'Buonanotte' sul mio PC della camera da letto"
oppure "Attiva Roku Play sul computer del soggiorno".

### Strumenti dinamici per comando

Per qualsiasi comando in cui hai compilato una **MCP Tool Description**,
TRIGGERcmd crea automaticamente uno strumento dedicato solo per quel comando,
chiamato qualcosa come `run_<computer>_<comando>` (in minuscolo, con spazi e
caratteri speciali trasformati in trattini bassi).

Ad esempio, un comando chiamato "Play Music" su un computer chiamato "Office
PC" appare all'assistente come uno strumento chiamato
`run_office_pc_play_music`, descritto usando il testo che hai inserito nella
sua MCP Tool Description — ad esempio, *"Riproduce la mia playlist di lavoro
attraverso le casse dell'ufficio."*

**Perché è utile:** dare a un comando il proprio strumento con una
descrizione chiara e specifica aiuta l'assistente a:

- trovare e scegliere rapidamente il comando *giusto*, invece di indovinare
  da un nome di comando breve o generico
- sapere come formattare eventuali parametri del comando, e quando usarli
- spiegarti, in linguaggio semplice, cosa sta per fare prima di eseguirlo

Se il comando ha anche **Allow Params** attivato, il suo strumento dinamico
accetta un valore opzionale `parameters`, proprio come `run_command`. Se
Allow Params è disattivato, lo strumento dinamico non accetta alcun input —
esegue semplicemente il comando.

---

## Dare a uno dei tuoi comandi il proprio strumento

Per far apparire un comando agli assistenti IA come un proprio strumento con
nome dedicato:

1. Apri le impostazioni del comando (nel `commands.json` del tuo agente
   TRIGGERcmd locale, o ovunque tu gestisca quel comando).
2. Compila **MCP Tool Description** con una frase breve e chiara che descriva
   cosa fa il comando e/o quando dovrebbe essere usato — ad esempio "Spegne
   tutte le luci al piano interrato" oppure "Riavvia il server Plex."
3. *(Facoltativo)* Attiva **Allow Params** se il comando deve accettare del
   testo come parametro proveniente dall'assistente.
4. Salva e lascia che l'agente si sincronizzi. Il tuo elenco di Comandi
   TRIGGERcmd mostrerà un'icona 🔧 accanto a qualsiasi comando che abbia una
   descrizione dello strumento MCP.

La prossima volta che un assistente elencherà i tuoi strumenti, vedrà uno
strumento dedicato per quel comando, descritto nel modo in cui lo hai scritto.

### Consigli per scrivere buone descrizioni

- Spiega *cosa* succede: "Accende le luci del seminterrato, oppure regola la
  luminosità. Il parametro può essere una percentuale di luminosità come 50",
  non semplicemente "Luci."
- Sii breve — una o due frasi sono più che sufficienti. L'assistente la legge
  ogni volta che decide se usare lo strumento.
