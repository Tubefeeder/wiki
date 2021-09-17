If your screen dimming, it might be the proximity sensor.
To test this hypothesis, wave your finger across the area left of the front speaker of the Pinephone.
If the screen start blinking, the problem is probably the proximity sensor.

I have found a few different ways to disable the dimming. Not everything works on every distribution.
If you have a distribution not listed, I would recommend checking the solution for Manjaro first and then for Arch.

# Working for Manjaro

To disable the screen dimming, you have to disable the sensor. 
Note that this might also disable other functionalities of the Pinephone like the phone receiving touch input when calling (not tested).
To disable the sensor, follow the instructions in the [comment of this reddit post](https://www.reddit.com/r/pinephone/comments/lsywno/how_to_turn_off_this_anoying_screen_dimming_thing/goya61z?utm_source=share&utm_medium=web2x&context=3). Summarized:

* Edit `/etc/modprobe.d/proximity.conf` with sudo
* Type in `blacklist stk3310`
* Reboot the phone.

# Working for Arch
Remove the file `/usr/lib/udev/rules.d/10-proximity.rules` from the Pinephone and reboot the phone.
