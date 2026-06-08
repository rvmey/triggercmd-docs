# Servidor MCP de TRIGGERcmd — Guía del usuario

El servidor MCP de TRIGGERcmd permite que los asistentes de IA —Claude, ChatGPT
o cualquier herramienta que hable el [Model Context Protocol](https://modelcontextprotocol.io)—
vean tus comandos de TRIGGERcmd y los ejecuten en tus computadoras, simplemente
conversando en lenguaje natural. Por ejemplo, puedes preguntarle a tu asistente
"¿Qué puedo ejecutar en mi computadora de la oficina?" o "Apaga las luces del
sótano", y él buscará el comando de TRIGGERcmd correcto y lo activará por ti.

Ya está funcionando para todas las cuentas de TRIGGERcmd: no hay nada que
instalar en tu computadora para usarlo.

---

## Conectar un asistente de IA

Hay dos formas de conectarse, según lo que admita tu herramienta de IA.

### Opción 1 — HTTP Streamable (recomendado)

La mayoría de los productos de IA modernos que admiten "servidores MCP remotos"
o "conectores" (Claude.ai, ChatGPT, etc.) pueden comunicarse directamente con
TRIGGERcmd a través de Internet. Cuando tu herramienta de IA te pida una URL de
servidor MCP, proporciónale:

```
https://www.triggercmd.com/mcp
```

El servidor admite OAuth2 estándar, así que cuando lo agregues como conector,
tu herramienta de IA abrirá automáticamente una página de inicio de
sesión/autorización de TRIGGERcmd. Apruébala una vez y el asistente podrá ver
y ejecutar los comandos de tu cuenta de TRIGGERcmd.

> **Usuarios de ChatGPT:** TRIGGERcmd también está disponible como una
> aplicación lista para usar — solo instálala desde
> **https://chatgpt.com/apps/triggercmd/asdk_app_694c84d39cb881918c6d181ae69e33fc**
> e inicia sesión con tu cuenta de TRIGGERcmd. No se necesita URL ni configuración.

### Opción 2 — Servidor local stdio

Si tu herramienta de IA solo admite servidores MCP que se ejecutan localmente
("stdio") — por ejemplo, algunas configuraciones de Claude Desktop —, usa en su
lugar el proyecto complementario:

**https://github.com/rvmey/triggercmd-mcp-stdio**

Se ejecuta como un pequeño proceso en tu propia computadora, inicia sesión con
el token de tu cuenta de TRIGGERcmd y expone exactamente las mismas
herramientas descritas a continuación.

---

## Qué puede hacer el asistente una vez conectado

Una vez conectado, el asistente obtiene acceso a herramientas limitadas a tu
cuenta de TRIGGERcmd: puede ver todas las computadoras y comandos que tienes, y
activarlos en tu nombre. Hay tres tipos de herramientas:

### `list_commands`

Pregunta "¿qué comandos tengo?". Devuelve todos los comandos de tus
computadoras, incluyendo:

- en qué computadora se encuentra
- su nombre
- su frase de activación por voz (si tiene una)
- su descripción de herramienta MCP (si tiene una — consulta "Herramientas
  dinámicas por comando" más abajo)

Tu asistente normalmente llama a esto primero cuando le preguntas algo como
"¿Qué comandos de TRIGGERcmd tengo?" o "¿Qué puedo ejecutar en mi PC de la
oficina?", para saber qué hay disponible antes de hacer cualquier cosa.

### `run_command`

La herramienta de propósito general para "ejecutar cualquier cosa". Funciona
para **cualquier** comando en **cualquiera** de tus computadoras, tenga o no
ese comando una descripción de herramienta MCP configurada.

El asistente completa:

- `computer` — el nombre de la computadora que tiene el comando
- `command` — el nombre del comando a ejecutar
- `parameters` *(opcional)* — texto adicional para pasar, en comandos que
  aceptan parámetros

Normalmente verás esto en uso cuando le pidas al asistente que ejecute algo por
su nombre, por ejemplo, "Ejecuta 'Buenas noches' en mi PC del dormitorio" o
"Activa Roku Play en la computadora de la sala."

### Herramientas dinámicas por comando

Para cualquier comando en el que hayas completado una **Descripción de
herramienta MCP**, TRIGGERcmd crea automáticamente una herramienta dedicada
solo para ese comando, con un nombre similar a `run_<computadora>_<comando>`
(en minúsculas, con espacios y caracteres especiales convertidos en guiones
bajos).

Por ejemplo, un comando llamado "Play Music" en una computadora llamada
"Office PC" aparece ante el asistente como una herramienta llamada
`run_office_pc_play_music`, descrita con el texto que hayas puesto en su
Descripción de herramienta MCP — por ejemplo, *"Reproduce mi lista de
reproducción de trabajo por los altavoces de la oficina."*

**Por qué esto es útil:** darle a un comando su propia herramienta con una
descripción clara y específica ayuda al asistente a:

- encontrar y elegir rápidamente el comando *correcto*, en lugar de adivinar a
  partir de un nombre de comando corto o genérico
- saber cómo dar formato a los parámetros del comando, y cuándo usarlos
- explicarte, en lenguaje sencillo, qué está a punto de hacer antes de
  ejecutarlo

Si el comando también tiene activada la opción **Allow Params**, su
herramienta dinámica acepta un valor `parameters` opcional, igual que
`run_command`. Si Allow Params está desactivada, la herramienta dinámica no
recibe ninguna entrada: simplemente ejecuta el comando.

---

## Darle a uno de tus comandos su propia herramienta

Para hacer que un comando aparezca ante los asistentes de IA como su propia
herramienta con nombre:

1. Abre la configuración del comando (en el `commands.json` de tu agente local
   de TRIGGERcmd, o donde sea que administres ese comando).
2. Completa **Descripción de herramienta MCP** con una oración breve y clara
   que describa qué hace el comando y/o cuándo debe usarse — por ejemplo,
   "Apaga todas las luces de la planta baja" o "Reinicia el servidor de Plex."
3. *(Opcional)* Activa **Allow Params** si el comando debe aceptar texto como
   parámetro proveniente del asistente.
4. Guarda y deja que el agente se sincronice. Tu lista de Comandos de
   TRIGGERcmd mostrará un ícono 🔧 junto a cualquier comando que tenga una
   descripción de herramienta MCP.

La próxima vez que un asistente liste tus herramientas, verá una herramienta
dedicada para ese comando, descrita tal como la escribiste.

### Consejos para escribir buenas descripciones

- Indica *qué* sucede: "Enciende las luces del sótano, o ajusta el brillo. El
  parámetro puede ser un porcentaje de brillo como 50", no solo "Luces."
- Mantenla breve — una o dos oraciones son suficientes. El asistente la lee
  cada vez que decide si usar la herramienta.
