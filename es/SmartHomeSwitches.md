# Interruptores Virtuales para el Hogar Inteligente

## Integraciones que crean conmutadores virtuales

* TRIGGERcmd Smart Home Alexa skill
* TRIGGERcmd Smart Home Google Assistant acción
* Integración TRIGGERcmd Samsung SmartThings

## Cambiar creación y denominación

Tanto los comandos como las computadoras tienen un campo de **voz** que determina el nombre de sus conmutadores virtuales. Si esos campos de voz están vacíos, es posible que no se cree un conmutador virtual.

Para que se cree un conmutador virtual, cada uno de sus comandos debe tener un valor en el campo **voz** (como "calculadora") porque el valor del campo **voz** del comando se utiliza en el nombre del conmutador virtual.

Para que se cree un conmutador virtual, cada una de sus computadoras también debe tener un valor en el campo **voz** (como "laptop") porque el valor del campo **voz** de la computadora se usa en el nombre del conmutador virtual. (ejemplo: **calculadora en computadora portátil**).

La excepción es su computadora predeterminada. El campo de voz predeterminado de su computadora puede estar vacío porque no se usa en los nombres de sus conmutadores virtuales. En su lugar, solo se utilizan los valores del campo de voz del comando (ejemplo: **calculadora**).

La primera computadora en su cuenta es su computadora predeterminada, pero si tiene varias computadoras, puede cambiar su computadora predeterminada.

Los conmutadores virtuales para su computadora predeterminada son:

1. Nombrado únicamente con el campo de voz del comando (es decir, calculadora).
1. Creado independientemente de que el campo de voz de la computadora esté vacío o no.

Los conmutadores virtuales para sus computadoras no predeterminadas son:

1. Nombrado con el comando y el campo de voz de la computadora (es decir, calculadora en la computadora portátil).
1. Se creará incluso si el campo de voz predeterminado de su computadora está vacío.

# Activar y desactivar interruptores virtuales

Si su comando tiene "Permitir parámetros" establecido en verdadero y el campo "Comando apagado" está vacío, cuando encienda o apague el interruptor virtual del comando, ejecutará su comando con **on** o **off** como un parámetro de comando.

O, si coloca un comando en el campo "Comando de apagado", se ejecutará cuando apague el interruptor.

Si "Permitir parámetros" se establece en falso, el comando en el campo "Comando" se ejecuta ya sea que encienda o apague el interruptor.

# Consejos para evitar problemas al ejecutar tus comandos con Alexa o el Asistente de Google

No uses los nombres de tus habitaciones inteligentes en las palabras de voz. Eso dificulta que ellos sepan qué comando querías activar.