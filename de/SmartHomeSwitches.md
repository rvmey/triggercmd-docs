# Virtuelle Smart Home Schalter

## Integrationen, die virtuelle Schalter erstellen

* TRIGGERcmd Smart Home Alexa Skill
* TRIGGERcmd Smart Home Google Assistant Aktion
* TRIGGERcmd Samsung SmartThings Integration

## Erstellung und Benennung von Schaltern

Sowohl Befehle als auch Computer haben ein **Sprachfeld**, das bestimmt, wie Ihre virtuellen Schalter benannt werden. Wenn diese Sprachfelder leer sind, wird möglicherweise kein virtueller Schalter erstellt.

Damit ein virtueller Schalter erstellt wird, muss jeder Ihrer Befehle einen Wert im **Sprachfeld** haben (z. B. "Rechner"), da dieser Wert im Namen des virtuellen Schalters verwendet wird.

Damit ein virtueller Schalter erstellt wird, muss auch jeder Ihrer Computer einen Wert im **Sprachfeld** haben (z. B. "Laptop"), da dieser Wert im Namen des virtuellen Schalters verwendet wird (Beispiel: **Rechner auf Laptop**).

Die Ausnahme ist Ihr Standardcomputer. Das Sprachfeld Ihres Standardcomputers kann leer sein, da es nicht in den Namen Ihrer virtuellen Schalter verwendet wird. Stattdessen werden nur die Sprachfeldwerte des Befehls verwendet (Beispiel: **Rechner**).

Der erste Computer in Ihrem Konto ist standardmäßig Ihr Standardcomputer, aber wenn Sie mehrere Computer haben, können Sie Ihren Standardcomputer ändern.

Virtuelle Schalter für Ihren Standardcomputer sind:

1. Nur mit dem Sprachfeld des Befehls benannt (z. B. Rechner).
1. Werden erstellt, unabhängig davon, ob das Sprachfeld des Computers leer ist oder nicht.

Virtuelle Schalter für Ihre Nicht-Standardcomputer sind:

1. Benannt mit dem Sprachfeld des Befehls und des Computers (z. B. Rechner auf Laptop).
1. Werden erstellt, auch wenn das Sprachfeld Ihres Standardcomputers leer ist.

# Virtuelle Schalter ein- und ausschalten

Wenn Ihr Befehl "Parameter erlauben" auf wahr gesetzt ist und das Feld "Ausschaltbefehl" leer ist, wird beim Ein- oder Ausschalten des virtuellen Schalters Ihr Befehl mit **on** oder **off** als Parameter ausgeführt.

Oder, wenn Sie einen Befehl im Feld "Ausschaltbefehl" angeben, wird dieser ausgeführt, wenn Sie den Schalter ausschalten.

Wenn "Parameter erlauben" auf falsch gesetzt ist, wird der Befehl im Feld "Befehl" ausgeführt, egal ob Sie den Schalter ein- oder ausschalten.

# Tipps, um Probleme mit Alexa oder Google Assistant zu vermeiden

Verwenden Sie keine Namen Ihrer Smart-Home-Räume in Ihren Sprachbefehlen. Das erschwert es, den richtigen Befehl zu erkennen.
