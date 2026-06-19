## Creando Comandos

La forma más sencilla de agregar o editar comandos es con el Editor de comandos GUI que se muestra a continuación.

![GUI Editor](./images/windows-command.png)

| Campo | Descripción |
| --- | ----------- |
| Trigger | El nombre de tu Trigger |
| Command | El comando que se ejecutará cuando se active |
| Off Command | El comando que se ejecutará cuando se active con "off" como parámetro (requiere que Permitir parámetros sea verdadero) |
| Ground | agente de primer plano o de fondo |
| Voice | Lo que le dirás a Alexa o al Asistente de Google |
| Voice/MCP Reply | Las antiguas skills conversacionales de Alexa dicen esto de vuelta, y MCP recibirá el resultado si tienes {{result}} en este campo |
| MCP Tools Description | Le dice al asistente de IA qué hace este comando y cómo usar sus parámetros — ver [Servidor MCP](./MCPServer.md) |
| Permitir parámetros | Ya sea para permitir parámetros |
| Quote Parameters | Si es verdadero, los parámetros se envuelven entre comillas para que se pasen como una sola cadena en lugar de múltiples parámetros |
| Icon | Un icono para el comando — elige uno de la lista o pega el tuyo propio |

## Detalles

El campo **Trigger** es básicamente un nombre para su comando, pero Alexa y el Asistente de Google no usan ese nombre. Usan el campo **Voice** para encontrar el factor desencadenante.

El campo **Off Command** solo está disponible cuando **Allow Parameters** es verdadero porque solo se ejecutará si el parámetro está "off".

Solo configura **Ground** en segundo plano si has instalado el agente en segundo plano. Puede instalar el agente en segundo plano en Windows y Linux (incluida Raspberry Pi), pero no en Mac. El agente en segundo plano se inicia cuando su computadora arranca en lugar de iniciarse cuando inicia sesión, por lo que puede usarlo para reiniciar incluso si no ha iniciado sesión.

El campo **Voice/MCP Reply** es utilizado por las antiguas skills "conversacionales" de Alexa y por [MCP](./MCPServer.md). Las skills conversacionales de Alexa son:
* [TRIGGERcmd](https://www.amazon.com/gp/product/B06XFN2TZN)
* [TRIGGER command](https://www.amazon.com/gp/product/B074TV61DK) 
* [TC](https://www.amazon.com/gp/product/B0BMGG4SHS).  

La skill/action "[TRIGGERcmd Smart Home](https://www.amazon.com/gp/product/B07P1MMFRP)" **no** utiliza el campo **Voice/MCP Reply**.

El campo **Voice/MCP Reply** puede incluir los marcadores de posición {{trigger}}, {{computer}} y [{{result}}](https://www.triggercmd.com/forum/topic/422/have-alexa-or-google-assistant-say-the-result-of-a-command). El marcador de posición {{result}} es donde Alexa dice el resultado de tu comando, y donde MCP recibe el resultado de tu comando.

Para mayor seguridad, sus comandos **no** se almacenan en la nube. Solo se almacenan en su computadora en un archivo llamado commands.json. Puede encontrarlo en su carpeta .TRIGGERcmdData en la carpeta de inicio de su usuario. Es posible que desee hacer una copia de seguridad en caso de que su disco duro falle.