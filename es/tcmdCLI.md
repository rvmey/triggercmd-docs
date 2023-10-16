# Command Line Interface toolHerramienta de interfaz de línea de comando

## Descargar tcmd

* [Windows de 64 bits (el más común)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-amd64.exe)
* [Windows de 32 bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-386.exe)
* [Mac de 64 bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-darwin-amd64)
* [Linux de 32 bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-386)
* [Linux de 64 bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-amd64)
* [Linux arm (ie: Raspberry Pi o Orange Pi)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-arm)

Después de descargarlo, cámbiele el nombre a tcmd o tcmd.exe en Windows.

Muévalo a **/usr/local/bin** o **C:\Windows**, o alguna otra carpeta listada en su variable de entorno PATH si desea poder ejecutarlo desde cualquier carpeta.

## Uso de tcmd

Ejecute este comando para obtener texto de ayuda:
```
tcmd -h
```

```
NAME:
    tcmd - Run commands on computers in your TRIGGERcmd account
  USAGE:
    tcmd [options]

  OPTIONS:
    --trigger value, -t value   Nombre del activador del comando que desea ejecutar
    --computer value, -c value  Nombre de la computadora (déjelo en blanco para su computadora predeterminada)
    --params value, -p value    Cualquier parámetro que desee agregar al comando remoto
    --panel value, -P value     Nombre del panel que desea utilizar
    --button value, -b value    Nombre del botón del panel a "presionar"
    --list, -l                  Enumere sus comandos
    --listpanels, -L            Lista tus paneles
    --pair                      Inicie sesión usando un código de par
    --help, -h                  mostrar ayuda
    --version, -v               imprimir la versión
```

## Código fuente

Puede ver el código fuente de Go para la herramienta tcmd en Github [aquí](https://github.com/rvmey/triggercmdGOclient).  

## Video de Youtube

Para ver la herramienta **tcmd** en acción, mira [este vídeo de Youtube](https://www.youtube.com/watch?v=q0Uu4SNFKFY).  