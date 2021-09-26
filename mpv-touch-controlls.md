# Add touch controlls to mpv

If you want some touch-controls for mpv, follow the instructions of [this comment](https://github.com/mpv-player/mpv/issues/6434#issuecomment-658174223). I will summarize how to do it:

* Create the file `~/.config/mpv/scripts/touchscreen-seek.lua` on your Pinephone
* Paste the following script into that file:

``` lua
require 'mp.options'

local options = {
    step = 5,
}

read_options(options,'touchscreen-seek')

function touch_seek()
    local pos = get_mouse_area()
    local step = options.step

    if pos == 'left' then
        mp.commandv('seek', -1*step)
    elseif pos == 'right' then
        mp.commandv('seek', step)
    else
        toggle_pause()
    end
end

function get_mouse_area()
    local mouse_x,mouse_y = mp.get_mouse_pos()
    local winX,winY = mp.get_property('osd-width'), mp.get_property('osd-height')

    if mouse_x < winX/3 then
        return 'left'
    elseif mouse_x < winX/3*2 then
        return 'middle'
    else
        return 'right'
    end
end

function toggle_fullscreen()
    local screen_stat = mp.get_property('fullscreen')

    if screen_stat == 'yes' then
        screen_stat = 'no'
    else
        screen_stat = 'yes'
    end

    mp.set_property('fullscreen', screen_stat)
end

function toggle_pause()
    local pause = mp.get_property_native("pause")
    mp.set_property_native("pause", not pause)
end


mp.add_key_binding(nil, "touchscreen-seek", touch_seek)
mp.msg.info("Loaded touchscreen-seek Lua flavor")
```

* If you want to toggle fullscreen instead of play/pause when double tapping the middle area, change `toggle_pause()` in the function `touch_seek` to `toggle_fullscreen()`
* Create the file `~/.config/mpv/scripts-opt/touchscreen-seek.conf` on your Pinephone
* Paste the following content into that file:

```
step = 5
```

* If you want to change the step size replace the `5` with the wanted step size
* Create the file `~/.config/mpv/input.conf` on your Pinephone
* Paste the following content into that file:

```
MBTN_LEFT_DBL script-binding touchscreen-seek
```

You should now have touch controlls for mpv.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
