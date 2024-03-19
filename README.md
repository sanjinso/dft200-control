# dft200-control
Just a simple Bash script I wrote for controlling an DFT200 by Sportstech via CLI or keyboard using [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk). 

I use it on Hyprland with Mako Notifications on Arch Linux. 

## Warning 
**Use at your own risk! Always have the original remote control nearby. Emergency stop is NOT implemented.**

## Usage
1. Install dft200-go ```go install github.com/leoluk/dft200-go/cmd/dft-cli```
2. Clone this repo ```git clone https://github.com/sanjinso/dft200-control.git ~/.local/bin/dft200-control```
3. Make it executable ```chmod +x ~/.local/bin/dft200-control/dft200-control```
4. Set MAC Adress of your DFT200 treadmill inside the script. (find out using bluetoothctl)
5. **Optional**: Set filepath to dft200-go inside the script. Default is ```$HOME/go/bin/dft-cli```
6. **Optional**: Change path to icons for notifications inside the script.
7. Run ```dft200control --toggle```

### Commands
| Command | Description |
|-------------------------------|--------------------------|
| ```dft200control --toggle``` | On/Off |
| ```dft200control --inc``` | Increase speed |
| ```dft200control --dec``` | Decrease speed |
| ```dft200control --get``` | Return current speed |

### Configuration
You have to change the MAC adress inside the script to the Mac adress of YOUR DFT200. I ran into an compatibily issue with my Bluetooth dongle using dft200-go so I slightly modified it. https://github.com/sanjinso/dft200-go 

For keyboard controls I used ```wev``` to find out the keycodes for F14 to F16 and created keybindings in my Hyprland config:

```#Sportstech DFT200 Treadmill Control

$treadmill = path/to/your/script/dft200control
#F16=Start/Pause, F15=Speed+, F14=Speed-
#Use wev to checkout keycodes
bind = , code:194, exec, $treadmill --toggle
bind = , code:193, exec, $treadmill --inc
bind = , code:192, exec, $treadmill --dec```
  

## Requirements
-  Bluetooth Connection to DFT200
-  [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk)


