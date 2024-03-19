# dft200-control
Just a simple Bash script I wrote for controlling an DFT200 by Sportstech via CLI or keyboard using [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk). 

You could do this using dft200-go on its own and without this script but this gives you notifications about the state of the treadmill and makes it possible to increase or decrease the speed incremantally by reapeatedly pressing a button.

*I use it with Hyprland and Mako Notifications on Arch Linux.*

## Warning 
**Use at your own risk!**
- Always have the original remote control nearby. 
- Emergency stop is NOT implemented.
- Bluetooth control is unauthenticated. Anyone in range can control your treadmill.
- Be careful when using speed increase or speed decrease after shutting it off on a higher speedlevel, it might ramp up back to that level first even if you intend to slow it down!

## Setup
1. Install dft200-go: ```go install github.com/leoluk/dft200-go/cmd/dft-cli```
2. Clone this repo: ```git clone https://github.com/sanjinso/dft200-control.git ~/.local/bin/dft200-control```
3. Make it executable:; ```chmod +x ~/.local/bin/dft200-control/dft200-control```
4. Set MAC Adress of your DFT200 treadmill inside the script. (find out using bluetoothctl)
5. **Optional**: Set filepath to dft200-go inside the script. Default is: ```$HOME/go/bin/dft-cli```
6. **Optional**: Change path to icons for notifications inside the script. Default is same dir as script
7. Make sure yor dft200 is connectd via Bluetooth. Checkout [dft200-go/readme.md](https://github.com/leoluk/dft200-go)
8. Run ```dft200control --toggle```

## Usage
| Command | Description |
|-------------------------------|--------------------------|
| ```dft200control --toggle``` | On/Off |
| ```dft200control --inc``` | Increase speed |
| ```dft200control --dec``` | Decrease speed |
| ```dft200control --get``` | Return current speed |

## Configuration
You have to change the MAC adress inside the script to the MAC adress of YOUR DFT200. I ran into an compatibily issue with my Bluetooth dongle while using dft200-go so I slightly modified it. https://github.com/sanjinso/dft200-go

### Keyboard Controls

#### Hyprland
For keyboard controls I used ```wev``` to find out the keycodes for F14 to F16 and created keybindings in my Hyprland config:

```
$treadmill = path/to/your/script/dft200control
#F16=Start/Pause, F15=Speed+, F14=Speed-
#Use wev to identify keycodes
bind = , code:194, exec, $treadmill --toggle
bind = , code:193, exec, $treadmill --inc
bind = , code:192, exec, $treadmill --dec
```

#### i3
```
set $tmCTL path/to/your/script/dft200control

bindsym $mod+Ctrl+1 exec $tmCTL --toggle
bindsym $mod+Ctrl+2 exec $tmCTL --inc
bindsym $mod+Ctrl+3 exec $tmCTL --dec
```

## Requirements
-  Bluetooth Connection to DFT200
-  [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk)


