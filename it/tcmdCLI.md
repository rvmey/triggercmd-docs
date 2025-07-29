# Strumento Interfaccia a Riga di Comando

## Scarica tcmd

* [Windows 64bit (più comune)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-amd64.exe)
* [Windows 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-386.exe)
* [Mac 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-darwin-amd64)
* [Linux 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-386)
* [Linux 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-amd64)
* [Linux arm (es: Raspberry Pi o Orange Pi)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-arm)

Dopo averlo scaricato, rinominalo in tcmd, o tcmd.exe su Windows.

Spostalo in **/usr/local/bin** o **C:\Windows**, o in un'altra cartella elencata nella variabile d'ambiente PATH se vuoi poterlo eseguire da qualsiasi cartella.

## Utilizzo di tcmd

Esegui questo comando per vedere il testo di aiuto:
```
tcmd -h
```

```
NOME:
    tcmd - Esegui comandi sui computer nel tuo account TRIGGERcmd
  USO:
    tcmd [opzioni]

  OPZIONI:
    --trigger value, -t value   Nome del trigger del comando che vuoi eseguire
    --computer value, -c value  Nome del computer (lascia vuoto per il computer predefinito)
    --params value, -p value    Parametri da aggiungere al comando remoto
    --panel value, -P value     Nome del pannello che vuoi usare
    --button value, -b value    Nome del pulsante del pannello da "premere"
    --list, -l                  Elenca i tuoi comandi
    --listpanels, -L            Elenca i tuoi pannelli
    --pair                      Accedi usando un codice di abbinamento
    --help, -h                  mostra l'aiuto
    --version, -v               mostra la versione
```

## Codice sorgente

Puoi vedere il codice sorgente Go dello strumento tcmd su Github [qui](https://github.com/rvmey/triggercmdGOclient).

## Video Youtube

Per vedere lo strumento **tcmd** in azione, guarda [questo video Youtube](https://www.youtube.com/watch?v=q0Uu4SNFKFY).
