# Linux Installation (Ubuntu/Debian)

## Download

* [DEB for Ubuntu/Debian (x86_64)](https://agents.triggercmd.com/triggercmdagent_1.0.1_amd64.deb) — desktops and servers with a GUI
* [RPM for Red Hat/CentOS/Fedora](https://agents.triggercmd.com/triggercmdagent-1.0.1.x86_64.rpm)

For Raspberry Pi, see the [Raspberry Pi Installation](./InstallRaspberryPi.md) guide.

## Install (Ubuntu/Debian)

Run these commands in a terminal as a **regular user** (not root):

```bash
sudo apt-get -y update
sudo apt-get -y upgrade
wget https://agents.triggercmd.com/triggercmdagent_1.0.1_amd64.deb
sudo apt install ./triggercmdagent_1.0.1_amd64.deb
```

## Set Up the Token

### Desktop (X-Windows / Wayland)

If your system uses AppArmor, run this first:

```bash
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```

Then launch the agent:

```bash
triggercmdagent
```

A GUI window will appear. Log into [triggercmd.com](https://www.triggercmd.com), copy your token from the [Instructions page](https://www.triggercmd.com/user/computer/create), and paste it into the token prompt.

### Headless (No GUI)

Install Node.js 16 or newer if it's not already installed:

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y
```

Then run the agent in console mode:

```bash
node /usr/lib/triggercmdagent/resources/app/src/agent.js --console
```

Log into [triggercmd.com](https://www.triggercmd.com), copy your token from the [Instructions page](https://www.triggercmd.com/user/computer/create), and paste it when prompted.

## Install the Background Service

The background service keeps the agent running after you log out.

### Desktop

Right-click the TRIGGERcmd tray icon and select **Background Service → Install Background Service**.

### Headless

First stop the console agent with **CTRL-C**, then run:

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

## Install (Red Hat/CentOS/Fedora)

```bash
sudo yum install wget -y
wget https://agents.triggercmd.com/triggercmdagent-1.0.1.x86_64.rpm
sudo rpm -i triggercmdagent-1.0.1.x86_64.rpm
```

Then follow the same token setup and background service steps above.

## Verify

1. Log into [triggercmd.com](https://www.triggercmd.com).
2. Click **View Triggers** — you should see your computer listed with some built-in commands.
3. Click **Trigger** next to any command to test it.

## Video Walkthrough

[Linux Installation Walkthrough](https://www.youtube.com/watch?v=Iv6ifjHyWF4 ':include :type=iframe width=100% height=400px')

## Next Steps

* [Add your own commands](./Commands.md)
* [Trigger commands remotely](./TriggerCommands.md)
