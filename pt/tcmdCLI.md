# Ferramenta de Linha de Comando

## Baixar tcmd

* [Windows 64 bits (mais comum)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-amd64.exe)
* [Windows 32 bits](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-386.exe)
* [Mac 64 bits](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-darwin-amd64)
* [Linux 32 bits](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-386)
* [Linux 64 bits](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-amd64)
* [Linux arm (ou seja, Raspberry Pi ou Orange Pi)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-arm)

Após baixá-lo, renomeie-o para tcmd, ou tcmd.exe no Windows.

Mova-o para **/usr/local/bin** no Linux ou **C:\Windows** no Windows, ou alguma outra pasta listada na variável de ambiente PATH se você quiser poder executá-lo de qualquer pasta.

## Uso do tcmd

Execute este comando para obter o texto de ajuda:
```
tcmd -h
```

```
NAME:
    tcmd - Run commands on computers in your TRIGGERcmd account
  USAGE:
    tcmd [options]

  OPTIONS:
    --trigger value, -t value   Trigger name of the command you want to run
    --computer value, -c value  Name of the computer (leave blank for your default computer)
    --params value, -p value    Any parameters you want to add to the remote command
    --panel value, -P value     Name of the panel you want to use
    --button value, -b value    Name of the panel button to "press"
    --list, -l                  List your commands
    --listpanels, -L            List your panels
    --pair                      Login using a pair code
    --help, -h                  show help
    --version, -v               print the version
```

## Código-fonte

Você pode visualizar o código-fonte em Go da ferramenta tcmd no Github [aqui](https://github.com/rvmey/triggercmdGOclient).  

## Vídeo do Youtube

Para ver a ferramenta **tcmd** em ação, confira este [vídeo do Youtube](https://www.youtube.com/watch?v=q0Uu4SNFKFY).  