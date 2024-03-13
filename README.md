# ♠ SSH-deflorator - OpenSSH Server injector for Windows with RPi pico
## By amuchina (Giovanni Desio)

## Description

### This project utilizes a Raspberry Pi Pico to create a BAD USB device (similar to Rubber-Ducky) capable of executing a keystroke injection attack on a target computer using a 
### payload written in duckyscript 1.0. The ultimate goal is to open an admin PowerShell window 
### and install an OpenSSH server on the victim's computer.

## Prerequisites

### - Raspberry Pi Pico or Pi Pico W
### - Host computer with Raspberry Pi Pico support and possibly Wireshark (Linux, macOS, or Windows)
### - USB-Micro USB cable (I built an all-inside case for making it look like a normal USB hihihi)
### - Text editor to modify the source code (notepad is enough for dd scripts)
### - Basic knowledge of what you're doing

## How does it work?

### The Raspberry Pi Pico used here is modified to be recognized as a HID (Human Interface Device) device when plugged in the victim's PC, emulating a key-injecting keyboard.
### The recognition of the Pico (that will be later recognized as CIRCUITPY, due to the installation of circuitpython in the board) is modified through a file 
### dragged into the root of the board that you can find at this link: https://github.com/adafruit/Adafruit_CircuitPython_Bundle/releases/latest. 
### After that, thanks to the public repo of dbisu about turning a Pico into a bad-usb (https://github.com/dbisu/pico-ducky) I easily set up a
### payload written in duckyscript (only version 1.0 is supported) executed at the usb plugging. This payload injects a series of keyboard commands 
### in order to open an administrator Windows Powershell and type a command that will install the OpenSSH server 0.1.0 optional feature on the victim's PC within few seconds.
### Then, the payload makes the machine do a ping to my local IP address (that can be modified in the payload basing on your needs) that I will track with Wireshark to find the IP source
### of the ping, so I can connect to the machine. The payload is still in development, so I will add some improving features in order to exploit some stupid vulnerability and
### do the operations smarter, so be gentle.

## Why is the functioning so stupid?

### As you can see, the payload and prerequisities of this shit are quite foolish though. Why this? well, the functioning exploit some stupid actions that you can easily do as
### a normal user, but the point is that you should consider that most people nowadays are so silly to not protect their PCs from such stupid attacks like mine, that simply
### use the ignorancy of people about the danger of plugging weird things in their machines just to see what's inside, or maybe the distraction of a moment.
### Finally, most Windows user leave their Windows security options as default, allowing exploitable vulnerabilities such as the UAC password bypass.
### By the way, this won't work on PCs that require an administrator password in the confirmation prompt in order to open admin processes and it's also bypassable keeping
### open a notepad window! (which will receive the injected commands instead of typing them in the cmd) but most people don't know this because they are too lazy to
### change a couple of options in the settings ;)
### Note: Despite this, I will configure the payload to bypass the admin pass in the future

## Usage

### Once the Raspberry Pi Pico is modified as a pico-ducky (follow the guide here: https://github.com/dbisu/pico-ducky) and programmed with the provided source code, just plug the device 
### into the target computer and wait about 5 seconds. The source code will automatically perform the following operations:

### - Keyboard simulation: Keyboard commands will be sent to open an admin PowerShell window.
### - Execution of PowerShell commands: PowerShell commands are executed to install an SSH server on the target computer.
### - Pinging the attacker IP: The Powershell will execute a ping to my local IP address

## Warnings

### - Just use this for jokes or whatever is done to your friends or experimental devices
### - This project is provided for educational and informational purposes only. I TAKE NO RESPONSABILITY FOR MISUSE OF THE SOURCE CODE FOR MALICIOUS SCOPES.

## Credits

### This project was created by amuchina (Giovanni Desio) and distributed under the GitHub license. 
### For any questions or suggestions, text me at giovannidesio9@gmail.com.


Created with ❤️ by amuchina
