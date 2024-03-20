# dft200-control
Just a simple Bash script I wrote for controlling an DFT200 by Sportstech via CLI or keyboard using [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk). 

You could do this using dft200-go on its own and without this script but this gives you notifications about the state of the treadmill and makes it possible to increase or decrease the speed incremantally by repeatedly pressing a button.

*I use it with Hyprland and Mako Notifications on Arch Linux.*

## Warning 
**Use at your own risk!**
- Always have the original remote control nearby. 
- Emergency stop is NOT implemented.
- Bluetooth control is unauthenticated. Anyone in range can control your treadmill.
- Be careful when using speed increase or speed decrease after shutting it off on a higher speedlevel, it might ramp up back to that level first even if you intend to slow it down!

## Setup
1. Install dft200-go: ```go install github.com/leoluk/dft200-go/cmd/dft-cli```
2. Clone this repo: ```git clone https://github.com/sanjinso/dft200-control.git ~/.local/bin/dft200control```
3. Make it executable: ```chmod +x ~/.local/bin/dft200control/dft200control```
4. **Optional**: Set filepath to dft200-go via ```export DFT200_APP_PATH```. Default is: ```$HOME/go/bin/dft-cli```
5. Make sure your Bluetooth works. Checkout [dft200-go/readme.md](https://github.com/leoluk/dft200-go)
6. Run ```dft200control```

## Usage
| Command | Description |
|-------------------------------|--------------------------|
| ```dft200control --init``` | Setup |
| ```dft200control --toggle``` | On/Off |
| ```dft200control --inc``` | Increase speed |
| ```dft200control --dec``` | Decrease speed |
| ```dft200control --get``` | Return current speed |
| ```dft200control --help```| Lists cmds |

## Configuration

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

## Speed Level

| Level | Speed (KM/H) |
|-------|--------------|
| 1 | 0.7 |
| 2 | 1.5 |
| 3 | 2.4 |
| 4 | 3.3 |
| 5 | 4.3 |
| 6 | 5.2 |
| 7 | 6.1 |
| 8 | 7.1 |

## Requirements
-  Bluetooth Connection to DFT200
-  [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk)


## Changelog

20.03.2024
- Added configuration file
- Added info, error and warning messages
- Added setup wizard for setting MAC Adress
- Added timer for resetting speed level after pausing for more than 4:30 min. 


## Troubleshooting

- I ran into an compatibily issue with my Bluetooth dongle while using dft200-go so I slightly modified it. https://github.com/sanjinso/dft200-go

