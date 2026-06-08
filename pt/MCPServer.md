# Servidor MCP do TRIGGERcmd — Guia do usuário

O servidor MCP do TRIGGERcmd permite que assistentes de IA — Claude, ChatGPT
ou qualquer ferramenta que fale o [Model Context Protocol](https://modelcontextprotocol.io) —
vejam seus comandos do TRIGGERcmd e os executem em seus computadores, apenas
conversando em linguagem natural. Por exemplo, você pode perguntar ao seu
assistente "O que você pode executar no meu computador do escritório?" ou
"Desligue as luzes do porão", e ele encontrará o comando certo do TRIGGERcmd e
o acionará para você.

Ele já está em execução para todas as contas do TRIGGERcmd — não há nada para
instalar no seu computador para usá-lo.

---

## Conectando um assistente de IA

Existem duas maneiras de se conectar, dependendo do que sua ferramenta de IA
suporta.

### Opção 1 — HTTP Streamable (recomendado)

A maioria dos produtos de IA modernos que suportam "servidores MCP remotos" ou
"conectores" (Claude.ai, ChatGPT, etc.) consegue se comunicar diretamente com o
TRIGGERcmd pela internet. Quando sua ferramenta de IA pedir uma URL de servidor
MCP, forneça:

```
https://www.triggercmd.com/mcp
```

O servidor suporta OAuth2 padrão, então, ao adicioná-lo como conector, sua
ferramenta de IA abrirá automaticamente uma página de login/autorização do
TRIGGERcmd. Aprove uma vez e o assistente poderá então ver e executar os
comandos da sua conta do TRIGGERcmd.

> **Usuários do ChatGPT:** o TRIGGERcmd também está disponível como um
> aplicativo pronto — basta instalá-lo em
> **https://chatgpt.com/apps/triggercmd/asdk_app_694c84d39cb881918c6d181ae69e33fc**
> e fazer login com sua conta do TRIGGERcmd. Sem necessidade de URL ou
> configuração.

### Opção 2 — Servidor local stdio

Se sua ferramenta de IA suportar apenas servidores MCP executados localmente
("stdio") — por exemplo, algumas configurações do Claude Desktop —, use o
projeto complementar:

**https://github.com/rvmey/triggercmd-mcp-stdio**

Ele roda como um pequeno processo no seu próprio computador, faz login com o
token da sua conta do TRIGGERcmd e expõe exatamente as mesmas ferramentas
descritas abaixo.

---

## O que o assistente pode fazer depois de conectado

Depois de conectado, o assistente obtém acesso a ferramentas restritas à sua
conta do TRIGGERcmd — ele pode ver todos os computadores e comandos que você
tem, e acioná-los em seu nome. Existem três tipos de ferramentas:

### `list_commands`

Pergunta "quais comandos eu tenho?". Ela retorna todos os comandos de todos os
seus computadores, incluindo:

- em qual computador ele está
- seu nome
- sua frase de ativação por voz (se houver)
- sua descrição de ferramenta MCP (se houver — veja "Ferramentas dinâmicas por
  comando" abaixo)

Seu assistente normalmente chama isso primeiro quando você pergunta algo como
"Quais comandos do TRIGGERcmd eu tenho?" ou "O que posso executar no meu PC do
escritório?", para saber o que está disponível antes de fazer qualquer coisa.

### `run_command`

A ferramenta de uso geral para "executar qualquer coisa". Ela funciona para
**qualquer** comando em **qualquer** um dos seus computadores, tendo ou não
esse comando uma descrição de ferramenta MCP configurada.

O assistente preenche:

- `computer` — o nome do computador que possui o comando
- `command` — o nome do comando a executar
- `parameters` *(opcional)* — texto extra a passar, para comandos que aceitam
  parâmetros

Você normalmente verá isso sendo usado quando pedir ao assistente para
executar algo pelo nome, por exemplo, "Execute 'Boa noite' no meu PC do
quarto" ou "Acione o Roku Play no computador da sala."

### Ferramentas dinâmicas por comando

Para qualquer comando em que você tenha preenchido uma **MCP Tool
Description**, o TRIGGERcmd cria automaticamente uma ferramenta dedicada só
para esse comando, com um nome parecido com `run_<computador>_<comando>`
(em minúsculas, com espaços e caracteres especiais transformados em
sublinhados).

Por exemplo, um comando chamado "Play Music" em um computador chamado "Office
PC" aparece para o assistente como uma ferramenta chamada
`run_office_pc_play_music`, descrita usando o texto que você colocou na sua
MCP Tool Description — por exemplo, *"Toca minha playlist de trabalho pelas
caixas de som do escritório."*

**Por que isso é útil:** dar a um comando sua própria ferramenta com uma
descrição clara e específica ajuda o assistente a:

- encontrar e escolher rapidamente o comando *certo*, em vez de adivinhar a
  partir de um nome de comando curto ou genérico
- saber como formatar quaisquer parâmetros do comando, e quando usá-los
- explicar para você, em linguagem simples, o que ele está prestes a fazer
  antes de executar

Se o comando também tiver **Allow Params** ativado, sua ferramenta dinâmica
aceita um valor `parameters` opcional, assim como o `run_command`. Se Allow
Params estiver desativado, a ferramenta dinâmica não recebe nenhuma entrada —
ela simplesmente executa o comando.

---

## Dando a um dos seus comandos sua própria ferramenta

Para fazer um comando aparecer para os assistentes de IA como sua própria
ferramenta nomeada:

1. Abra as configurações do comando (no `commands.json` do seu agente local do
   TRIGGERcmd, ou onde quer que você gerencie esse comando).
2. Preencha **MCP Tool Description** com uma frase curta e clara descrevendo o
   que o comando faz e/ou quando ele deve ser usado — por exemplo, "Desliga
   todas as luzes do porão" ou "Reinicia o servidor Plex."
3. *(Opcional)* Ative **Allow Params** se o comando deve aceitar texto como
   parâmetro vindo do assistente.
4. Salve e deixe o agente sincronizar. Sua lista de Comandos do TRIGGERcmd
   mostrará um ícone 🔧 ao lado de qualquer comando que tenha uma descrição de
   ferramenta MCP.

Da próxima vez que um assistente listar suas ferramentas, ele verá uma
ferramenta dedicada para esse comando, descrita do jeito que você escreveu.

### Dicas para escrever boas descrições

- Diga *o que* acontece: "Liga as luzes do porão, ou ajusta o brilho. O
  parâmetro pode ser uma porcentagem de brilho como 50", e não apenas "Luzes."
- Mantenha curto — uma ou duas frases já bastam. O assistente a lê toda vez
  que decide se vai usar a ferramenta.
