## Criando comandos

A maneira mais fácil de adicionar ou editar comandos é com o Editor de Comandos GUI mostrado abaixo.

![Editor GUI](images/windows-command.png)

| Campo | Descrição |
| --- | ----------- |
| Trigger | O nome do seu trigger |
| Command | O comando que será executado ao ser acionado |
| Off Command | O comando que será executado ao ser acionado com "desligar" como parâmetro (requer que Permitir Parâmetros esteja ativado) |
| Ground | Agente em primeiro plano ou segundo plano |
| Voice | O que você dirá para a Alexa ou o Google Assistant |
| Voice/MCP Reply | As antigas skills conversacionais da Alexa dizem isso de volta, e o MCP receberá o resultado se você tiver {{result}} neste campo |
| MCP Tools Description | Informa ao assistente de IA o que este comando faz e como usar seus parâmetros — veja [Servidor MCP](./MCPServer.md) |
| Permitir Parâmetros | Se permite parâmetros |
| Quote Parameters | Se verdadeiro, os parâmetros são envolvidos entre aspas para que sejam passados como uma única string em vez de múltiplos parâmetros |
| Icon | Um ícone para o comando — escolha um da lista ou cole o seu próprio |

## Detalhes

O campo **Trigger** é basicamente um nome para o seu comando, mas a Alexa e o Google Assistant não usam esse nome. Eles usam o campo **Voice** para encontrar o trigger.

O campo **Off Command** só está disponível quando **Permitir Parâmetros** está ativado, pois ele só será executado se o parâmetro for "desligar". 

Defina **Ground** como segundo plano apenas se você tiver instalado o agente em segundo plano. Você pode instalar o agente em segundo plano no Windows e Linux (incluindo o Raspberry Pi), mas não no Mac. O agente em segundo plano é iniciado quando o seu computador é ligado, em vez de iniciar quando você faz login, então você pode usá-lo para reiniciar mesmo que não esteja logado.

O campo **Voice/MCP Reply** é utilizado pelas antigas skills "conversacionais" da Alexa e pelo [MCP](./MCPServer.md). As skills conversacionais da Alexa são:
* [TRIGGERcmd](https://www.amazon.com/gp/product/B06XFN2TZN)
* [Comando TRIGGER](https://www.amazon.com/gp/product/B074TV61DK) 
* [TC](https://www.amazon.com/gp/product/B0BMGG4SHS).  

A skill "[TRIGGERcmd Smart Home](https://www.amazon.com/gp/product/B07P1MMFRP)" **não** utiliza o campo **Voice/MCP Reply**.

O campo **Voice/MCP Reply** pode incluir os marcadores {{trigger}}, {{computer}} e [{{result}}](https://www.triggercmd.com/forum/topic/422/have-alexa-or-google-assistant-say-the-result-of-a-command). O marcador {{result}} é onde a Alexa diz o resultado do seu comando, e onde o MCP recebe o resultado do seu comando.

Para maior segurança, os seus comandos **não** são armazenados na nuvem. Eles são armazenados apenas no seu computador em um arquivo chamado commands.json. Você pode encontrá-lo na sua pasta .TRIGGERcmdData na pasta do seu usuário. Talvez você queira fazer backup dele caso o seu disco rígido falhe.  