# TRIGGERcmd MCP Server — User Guide

The TRIGGERcmd MCP server lets AI assistants — Claude, ChatGPT, or any tool that
speaks the [Model Context Protocol](https://modelcontextprotocol.io) — see your
TRIGGERcmd commands and run them on your computers, just by chatting in plain
English. For example, you can ask your assistant "What can you run on my office
computer?" or "Turn off the basement lights," and it will look up the right
TRIGGERcmd command and trigger it for you.

It's already running for every TRIGGERcmd account — there's nothing to install
on your computer to use it.

---

## Connecting an AI assistant

There are two ways to connect, depending on what your AI tool supports.

### Option 1 — Streamable HTTP (recommended)

Most modern AI products that support "remote MCP servers" or "connectors"
(Claude.ai, ChatGPT, etc.) can talk to TRIGGERcmd directly over the internet.
When your AI tool asks for an MCP server URL, give it:

```
https://www.triggercmd.com/mcp
```

The server supports standard OAuth2, so when you add it as a connector your AI
tool will open a TRIGGERcmd sign-in/authorize page automatically. Approve it
once, and the assistant can then see and run the commands on your TRIGGERcmd
account.

> **ChatGPT users:** TRIGGERcmd is also available as a ready-made app — just
> install it from
> **https://chatgpt.com/apps/triggercmd/asdk_app_694c84d39cb881918c6d181ae69e33fc**
> and sign in with your TRIGGERcmd account. No URL or setup required.

### Option 2 — Local stdio server

If your AI tool only supports locally-run ("stdio") MCP servers — for example,
some Claude Desktop setups — use the companion project instead:

**https://github.com/rvmey/triggercmd-mcp-stdio**

It runs as a small process on your own computer, signs in with your TRIGGERcmd account token, and exposes the exact same tools described below.

---

## What the assistant can do once connected

Once connected, the assistant gets access to tools scoped to your TRIGGERcmd account — it can see every computer and command you have, and trigger them on your behalf. There are three kinds of tools:

### `list_commands`

Asks "what commands do I have?" It returns every command across your
computers, including:

- which computer it lives on
- its name
- its voice trigger phrase (if it has one)
- its MCP tool description (if it has one — see "Dynamic command tools" below)

Your assistant typically calls this first when you ask something like "What TRIGGERcmd commands do I have?" or "What can you run on my Office PC?" so it
knows what's available before doing anything.

### `run_command`

The general-purpose "run anything" tool. It works for **any** command on
**any** of your computers, whether or not that command has an MCP tool description set up.

The assistant fills in:

- `computer` — the name of the computer that owns the command
- `command` — the name of the command to run
- `parameters` *(optional)* — extra text to pass along, for commands that accept parameters

You'll typically see this used when you ask the assistant to run something by name, e.g. "Run 'Good Night' on my Bedroom PC" or "Trigger Roku Play on the Living Room computer."

### Dynamic per-command tools

For any command where you've filled in an **MCP Tool Description**, TRIGGERcmd
automatically creates a dedicated tool just for that command, named something
like `run_<computer>_<command>` (lower-cased, with spaces and special
characters turned into underscores).

For example, a command named "Play Music" on a computer named "Office PC" shows up to the assistant as a tool named `run_office_pc_play_music`, described using whatever text you put in its MCP Tool Description — for instance, *"Plays
my work playlist through the office speakers."*

**Why this is useful:** giving a command its own tool with a clear, specific description helps the assistant:

- find and pick the *right* command quickly, instead of guessing from a short or generic command name
- how to format any command parameters, and when to use them
- explain to you, in plain language, what it's about to do before running it

If the command also has **Allow Params** turned on, its dynamic tool accepts an optional `parameters` value, just like `run_command` does. If Allow Params is off, the dynamic tool takes no input — it simply runs the command.

---

## Giving one of your commands its own tool

To make a command show up to AI assistants as its own named tool:

1. Open the command's settings (in your local TRIGGERcmd agent's `commands.json`, or wherever you manage that command).
2. Fill in **MCP Tool Description** with a short, clear sentence describing what the command does and/or when it should be used — e.g. "Turns off all the lights downstairs" or "Restarts the Plex server."
3. *(Optional)* Turn on **Allow Params** if the command should accept text as a command parameter from the assistant.
4. Save and let the agent sync. Your TRIGGERcmd Commands list will show a 🔧 icon next to any command that has an MCP tool description.

The next time an assistant lists your tools, it will see a dedicated tool for that command, described the way you wrote it.

### Tips for writing good descriptions

- Say *what* happens: "Turns on the basement lights, or adjusts brightness. The parameter can be a brightness percentage like 50," not just "Lights."
- Keep it short — one or two sentences is plenty. The assistant reads it every time it decides whether to use the tool.
