# TRIGGERcmd MCP-Server — Benutzerhandbuch

Der TRIGGERcmd-MCP-Server ermöglicht es KI-Assistenten — Claude, ChatGPT oder
jedem Tool, das das [Model Context Protocol](https://modelcontextprotocol.io)
spricht — Ihre TRIGGERcmd-Befehle zu sehen und sie auf Ihren Computern
auszuführen, einfach durch ein Gespräch in normaler Sprache. Sie können Ihren
Assistenten zum Beispiel fragen „Was kannst du auf meinem Büro-Computer
ausführen?" oder „Schalte die Lichter im Keller aus", und er sucht den
passenden TRIGGERcmd-Befehl heraus und löst ihn für Sie aus.

Er läuft bereits für jedes TRIGGERcmd-Konto — es gibt nichts, was Sie auf
Ihrem Computer installieren müssten, um ihn zu nutzen.

---

## Einen KI-Assistenten verbinden

Es gibt zwei Möglichkeiten, sich zu verbinden, je nachdem, was Ihr KI-Tool
unterstützt.

### Option 1 — Streamable HTTP (empfohlen)

Die meisten modernen KI-Produkte, die „remote MCP-Server" oder „Connectors"
unterstützen (Claude.ai, ChatGPT usw.), können direkt über das Internet mit
TRIGGERcmd kommunizieren. Wenn Ihr KI-Tool nach einer MCP-Server-URL fragt,
geben Sie Folgendes ein:

```
https://www.triggercmd.com/mcp
```

Der Server unterstützt Standard-OAuth2. Wenn Sie ihn als Connector hinzufügen,
öffnet Ihr KI-Tool daher automatisch eine TRIGGERcmd-Anmelde-/
Autorisierungsseite. Bestätigen Sie diese einmal, und der Assistent kann
danach die Befehle Ihres TRIGGERcmd-Kontos sehen und ausführen.

> **ChatGPT-Nutzer:** TRIGGERcmd ist auch als fertige App verfügbar — installieren
> Sie sie einfach unter
> **https://chatgpt.com/apps/triggercmd/asdk_app_694c84d39cb881918c6d181ae69e33fc**
> und melden Sie sich mit Ihrem TRIGGERcmd-Konto an. Keine URL oder
> Einrichtung nötig.

### Option 2 — Lokaler stdio-Server

Wenn Ihr KI-Tool nur lokal laufende („stdio")-MCP-Server unterstützt — zum
Beispiel manche Claude-Desktop-Setups —, verwenden Sie stattdessen das
Begleitprojekt:

**https://github.com/rvmey/triggercmd-mcp-stdio**

Es läuft als kleiner Prozess auf Ihrem eigenen Computer, meldet sich mit dem
Token Ihres TRIGGERcmd-Kontos an und stellt genau dieselben unten
beschriebenen Tools bereit.

---

## Was der Assistent nach der Verbindung tun kann

Sobald die Verbindung steht, erhält der Assistent Zugriff auf Tools, die auf
Ihr TRIGGERcmd-Konto beschränkt sind — er kann jeden Computer und jeden Befehl
sehen, den Sie haben, und sie in Ihrem Namen auslösen. Es gibt drei Arten von
Tools:

### `list_commands`

Fragt „Welche Befehle habe ich?". Es gibt jeden Befehl auf all Ihren Computern
zurück, einschließlich:

- auf welchem Computer er sich befindet
- seinen Namen
- seine Sprachauslösungsphrase (sofern vorhanden)
- seine MCP-Tool-Beschreibung (sofern vorhanden — siehe „Dynamische
  Befehls-Tools" unten)

Ihr Assistent ruft dies normalerweise zuerst auf, wenn Sie etwas fragen wie
„Welche TRIGGERcmd-Befehle habe ich?" oder „Was kann ich auf meinem Büro-PC
ausführen?", damit er weiß, was verfügbar ist, bevor er irgendetwas tut.

### `run_command`

Das Allzweck-Tool zum „Ausführen von allem". Es funktioniert für **jeden**
Befehl auf **jedem** Ihrer Computer, unabhängig davon, ob für diesen Befehl
eine MCP-Tool-Beschreibung eingerichtet ist.

Der Assistent füllt aus:

- `computer` — der Name des Computers, dem der Befehl gehört
- `command` — der Name des auszuführenden Befehls
- `parameters` *(optional)* — zusätzlicher Text, der mitgegeben wird, für
  Befehle, die Parameter akzeptieren

Sie werden dies typischerweise verwendet sehen, wenn Sie den Assistenten
bitten, etwas namentlich auszuführen, z. B. „Führe 'Gute Nacht' auf meinem
Schlafzimmer-PC aus" oder „Löse Roku Play auf dem Wohnzimmer-Computer aus".

### Dynamische Tools pro Befehl

Für jeden Befehl, bei dem Sie eine **MCP Tool Description** ausgefüllt haben,
erstellt TRIGGERcmd automatisch ein eigenes Tool nur für diesen Befehl, das
etwa `run_<computer>_<befehl>` heißt (in Kleinbuchstaben, wobei Leerzeichen
und Sonderzeichen in Unterstriche umgewandelt werden).

Zum Beispiel erscheint ein Befehl namens „Play Music" auf einem Computer
namens „Office PC" dem Assistenten als Tool mit dem Namen
`run_office_pc_play_music`, beschrieben mit dem Text, den Sie in seine
MCP Tool Description eingegeben haben — zum Beispiel *„Spielt meine
Arbeits-Playlist über die Lautsprecher im Büro ab."*

**Warum das nützlich ist:** Wenn ein Befehl ein eigenes Tool mit einer
klaren, spezifischen Beschreibung erhält, hilft das dem Assistenten:

- den *richtigen* Befehl schnell zu finden und auszuwählen, statt anhand eines
  kurzen oder generischen Befehlsnamens zu raten
- zu wissen, wie Befehlsparameter formatiert werden sollen und wann sie zu
  verwenden sind
- Ihnen in einfacher Sprache zu erklären, was er gleich tun wird, bevor er es
  ausführt

Wenn der Befehl außerdem **Allow Params** aktiviert hat, akzeptiert sein
dynamisches Tool einen optionalen `parameters`-Wert, genau wie `run_command`.
Ist Allow Params deaktiviert, nimmt das dynamische Tool keine Eingabe entgegen
— es führt den Befehl einfach aus.

---

## Einem Ihrer Befehle ein eigenes Tool geben

So lassen Sie einen Befehl für KI-Assistenten als eigenes benanntes Tool
erscheinen:

1. Öffnen Sie die Einstellungen des Befehls (in der `commands.json` Ihres
   lokalen TRIGGERcmd-Agenten oder wo auch immer Sie diesen Befehl verwalten).
2. Tragen Sie unter **MCP Tool Description** einen kurzen, klaren Satz ein,
   der beschreibt, was der Befehl tut und/oder wann er verwendet werden
   sollte — z. B. „Schaltet alle Lichter im Untergeschoss aus" oder „Startet
   den Plex-Server neu".
3. *(Optional)* Aktivieren Sie **Allow Params**, wenn der Befehl Text als
   Befehlsparameter vom Assistenten entgegennehmen soll.
4. Speichern Sie und lassen Sie den Agenten synchronisieren. Ihre
   TRIGGERcmd-Befehlsliste zeigt ein 🔧-Symbol neben jedem Befehl an, der eine
   MCP-Tool-Beschreibung hat.

Wenn ein Assistent das nächste Mal Ihre Tools auflistet, sieht er ein eigenes
Tool für diesen Befehl, beschrieben so, wie Sie es geschrieben haben.

### Tipps für gute Beschreibungen

- Sagen Sie, *was* passiert: „Schaltet die Lichter im Keller ein oder passt
  die Helligkeit an. Der Parameter kann ein Helligkeitsprozentsatz wie 50
  sein", nicht nur „Lichter".
- Halten Sie es kurz — ein oder zwei Sätze reichen völlig aus. Der Assistent
  liest sie jedes Mal, wenn er entscheidet, ob er das Tool verwenden soll.
