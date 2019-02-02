# LEDs
The notification LEDs are controllable via the Linux LED subsystem, even though it always does a weird fade animation with every color.
`/sys/class/leds/<green/blue/red>` control the specific colors seperately, you can run them at the same time which makes the colors mix.
On phh AOSP the LED's green and blue color stay enabled after the boot process.
To mitigate this you can either disable the LED by modifying the file `/vendor/etc/init.lge.power.rc`:
`write /sys/devices/virtual/lg_rgb_led/use_patterns/setting` from 1 to 0.
Alternatively you can "simply" run `echo "0" > /sys/class/leds/blue/brightness && echo "0" > /sys/class/leds/green/brightness` in a root shell on your phone.
