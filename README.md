# dft200-control
Just a simple Bash script I wrote for controlling an DFT200 by Sportstech via CLI or keyboard using [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk). 

I use it on Hyprland with Mako Notifications on Arch Linux. 

# Warning 
**Use at your own risk! Always have the original remote control nearby. Emergency stop is NOT implemented.**

## Usage
1. ```go install github.com/leoluk/dft200-go/cmd/dft-cli```
2. ```git clone https://github.com/sanjinso/dft200-control.git ~/.local/bin/dft200-control```
3. chmod +x ~/.local/bin/dft200-control/dft200-control
4. Set MAC Adress of your DFT200 treadmill inside the script. (find out using bluetoothctl)
5. Set filepath to dft200-go inside the script. Default is ```$HOME/go/bin/dft-cli```
6. Optional: Change path to icons for notifications inside the script.
7. Run ```dft200control --toggle```

### Commands
```dft200control --toggle``` | On/Off
```dft200control --inc``` | Increase speed
```dft200control --dec``` | Decrease speed
```dft200control --get``` | Return current speed

## Requirements
-  Bluetooth Connection to DFT200
-  [dft200-go](https://github.com/leoluk/dft200-go) by [leoluk](https://github.com/leoluk)

