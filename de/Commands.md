## Befehle erstellen

Der einfachste Weg, Befehle hinzuzufügen oder zu bearbeiten, ist mit dem GUI-Befehlseditor, der unten gezeigt wird.

![GUI-Editor](./images/windows-command.png)

| Feld | Beschreibung |
| --- | ----------- |
| Trigger | Der Name Ihres Triggers |
| Command | Der Befehl, der beim Auslösen ausgeführt wird |
| Off Command | Der Befehl, der ausgeführt wird, wenn "off" als Parameter übergeben wird (erfordert, dass Allow Parameters aktiviert ist) |
| Ground | Vordergrund- oder Hintergrund-Agent |
| Voice | Was Sie zu Alexa oder Google Assistant sagen |
| Voice/MCP Reply | Die alten konversationellen Alexa-Skills sagen dies zurück, und MCP empfängt das Ergebnis, wenn Sie {{result}} in diesem Feld haben |
| MCP Tools Description | Teilt dem KI-Assistenten mit, was dieser Befehl tut und wie seine Parameter verwendet werden — siehe [MCP-Server](./MCPServer.md) |
| Allow Parameters | Ob Parameter erlaubt sind |
| Quote Parameters | Wenn aktiviert, werden Parameter in Anführungszeichen gesetzt, sodass sie als eine einzelne Zeichenkette statt als mehrere Parameter übergeben werden |
| Icon | Ein Symbol für den Befehl — wählen Sie eines aus der Liste oder fügen Sie Ihr eigenes ein |

## Details

Das Feld **Trigger** ist im Grunde ein Name für Ihren Befehl, aber Alexa und Google Assistant verwenden diesen Namen nicht. Sie verwenden das Feld **Voice**, um Ihren Trigger zu finden.

Das Feld **Off Command** ist nur verfügbar, wenn **Allow Parameters** aktiviert ist, da es nur ausgeführt wird, wenn der Parameter "off" ist.

Setzen Sie **Ground** nur auf Hintergrund, wenn Sie den Hintergrund-Agenten installiert haben. Sie können den Hintergrund-Agenten unter Windows und Linux (einschließlich Raspberry Pi) installieren, aber nicht auf dem Mac. Der Hintergrund-Agent startet beim Hochfahren des Computers, anstatt beim Anmelden, sodass Sie ihn zum Neustarten verwenden können, auch wenn Sie nicht angemeldet sind.

Das Feld **Voice/MCP Reply** wird von den alten "konversationellen" Alexa-Skills und von [MCP](./MCPServer.md) verwendet. Die konversationellen Alexa-Skills sind:
* [TRIGGERcmd](https://www.amazon.com/gp/product/B06XFN2TZN)
* [TRIGGER command](https://www.amazon.com/gp/product/B074TV61DK) 
* [TC](https://www.amazon.com/gp/product/B0BMGG4SHS).  

Der "[TRIGGERcmd Smart Home](https://www.amazon.com/gp/product/B07P1MMFRP)" Skill/Aktion verwendet das Feld **Voice/MCP Reply** **nicht**.

Das Feld **Voice/MCP Reply** kann die Platzhalter {{trigger}}, {{computer}} und [{{result}}](https://www.triggercmd.com/forum/topic/422/have-alexa-or-google-assistant-say-the-result-of-a-command) enthalten. Der Platzhalter {{result}} ist der Ort, an dem Alexa das Ergebnis Ihres Befehls sagt, und wo MCP das Ergebnis Ihres Befehls empfängt.

Aus Sicherheitsgründen werden Ihre Befehle **nicht** in der Cloud gespeichert. Sie werden nur auf Ihrem Computer in einer Datei namens commands.json gespeichert. Sie finden sie in Ihrem .TRIGGERcmdData-Ordner in Ihrem Benutzer-Home-Ordner. Sie sollten eine Sicherungskopie erstellen, falls Ihre Festplatte ausfällt.
