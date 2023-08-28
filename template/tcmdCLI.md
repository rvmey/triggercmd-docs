# Command Line Interface tool

## Download tcmd

* [Windows 64bit (most common)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-amd64.exe)
* [Windows 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-windows-386.exe)
* [Mac 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-darwin-amd64)
* [Linux 32bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-386)
* [Linux 64bit](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-amd64)
* [Linux arm (ie: Raspberry Pi or Orange Pi)](https://triggercmdagents.s3.amazonaws.com/tcmd_cli/tcmd-linux-arm)

After you download it, rename it to tcmd, or tcmd.exe on Windows.  

Move it to **/usr/local/bin** or **C:\Windows**, or some other folder listed in your PATH environment variable if you want to be able to run it from any folder.  

## tcmd usage

Run this command to get help text:
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

## Source code

You can view the Go source code for the tcmd tool on Github [here](https://github.com/rvmey/triggercmdGOclient).  

## Youtube video

To see the **tcmd** tool in action, check out [this Youtube video](https://www.youtube.com/watch?v=q0Uu4SNFKFY).  