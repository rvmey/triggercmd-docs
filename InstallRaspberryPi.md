# Raspberry Pi Installation

## Download

* [DEB for Raspberry Pi (headless/ARM)](https://agents.triggercmd.com/triggercmdagent_1.0.1_all.deb)

This package works on all Raspberry Pi models. It is a headless (no GUI) agent.

## Install

Run these commands in a terminal or over SSH:

```bash
sudo apt-get -y update
sudo apt-get -y upgrade
wget https://agents.triggercmd.com/triggercmdagent_1.0.1_all.deb
sudo apt install ./triggercmdagent_1.0.1_all.deb
```

## Install Node.js

The agent requires Node.js 16 or newer. Install it if it's not already on your Pi:

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y
```

## Set Up the Token

Run the agent in console mode:

```bash
node /usr/lib/triggercmdagent/resources/app/src/agent.js --console
```

1. Log into [triggercmd.com](https://www.triggercmd.com).
2. Copy your token from the [Instructions page](https://www.triggercmd.com/user/computer/create).
3. Paste it when prompted in the terminal.

## Install the Background Service

Stop the console agent with **CTRL-C**, then install the daemon:

```bash
sudo sh /usr/lib/triggercmdagent/resources/app/src/installdaemon.sh
```

### Service Management

Check if the service is running:

```bash
systemctl status triggercmdagent
```

Remove the background service:

```bash
sudo sh /usr/lib/triggercmdagent/resources/app/src/removedaemon.sh
```

## Verify

1. Log into [triggercmd.com](https://www.triggercmd.com).
2. Click **View Triggers** — you should see your Raspberry Pi listed with some built-in commands.
3. Click **Trigger** next to any command to test it.

## Next Steps

* [Add your own commands](./Commands.md)
* [Trigger commands remotely](./TriggerCommands.md)
