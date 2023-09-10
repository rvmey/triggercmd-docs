# Interruptores Virtuales para el Hogar Inteligente

## Integraciones que crean conmutadores virtuales

* TRIGGERcmd Smart Home Alexa skill
* TRIGGERcmd Smart Home Google Assistant acción
* Integración TRIGGERcmd Samsung SmartThings

## Cambiar creación y denominación

Both commands and computers have a **voice** field that determines what your virtual switches will be named.  If those voice fields are empty, a virtual switch may not be created.  

For a virtual switch to be created, each of your commands must have a value in the **voice** field (like "calculator") because the command's **voice** field value is used in the name of the virtual switch.  

For a virtual switch to be created, each of your computers must also have a value in the **voice** field (like "laptop") because the computer's **voice** field value is used in the name of the virtual switch (example: **calculator on laptop**).  

The exception is your default computer.  Your default computer's voice field can be empty because it is not used in the names of your virtual switches.  Instead, just the command voice field values are used (example: **calculator**).

The first computer in your account is your default computer by default, but if you have multiple computers, you can change your default computer.  

Virtual switches for your default computer are:

1. Named with the command's voice field only (ie: calculator).
1. Created whether computer's voice field is empty or not.

Virtual switches for your non-default computers are:

1. Named with both the command and computer's voice field (ie: calculator on laptop).
1. Will be created even if your default computer's voice field in empty.

# Flipping virtual switches on and off

If your command has "Allow Parameters" set to true and the "Off Command" field is empty, when you flip the command's virtual switch on or off, it will run your command with **on** or **off** as a command parameter.  

Or, if you put a command in the "Off Command" field, it will run when you flip the switch off.    

If "Allow Parameters" set to false, the command in the "Command" field runs whether you flip the switch on or off.