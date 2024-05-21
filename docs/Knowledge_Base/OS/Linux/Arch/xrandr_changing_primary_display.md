!!! info ""

    If you have multiple displays and want to change which display is the main one

    ```bash

    #list the displays
    xrandr --listactivemonitors
    Monitors: 3
    0: +*HDMI-1 1920/527x1080/296+1920+1080  HDMI-1
    1: +DP-0 1920/527x1080/296+0+0  DP-0
    2: +HDMI-0 1920/527x1080/296+0+1080  HDMI-0

    #example below shows how to change the primary display based on above output
    xrandr --output HDMI-1 --primary
    xrandr --output HDMI-0 --primary
    xrandr --output eDP-1 --primary
    ```
