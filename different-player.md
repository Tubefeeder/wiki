# Using a different video player

# Note

This is currently only possible in the [refactoring](https://github.com/Schmiddiii/Tubefeeder/pull/32) branch of the application or the beta-build of flatpak.

The default player is mpv.

# Change default player (not for flatpak)

To change the default video player, use the environmental variable `PLAYER`. You can for example set this variable in your `.profile`, e.g
by adding `PLAYER="myplayer"` to your `.profile`.

# Changing for flatpak

Changing the default player for the flatpak is a little bit harder as the flatpak version does not have access to run arbitrary commands on the host. You will have to change that permission manually. 

## Changing the permissions

Depending on how you have installed the flatpak (user or system-wide) you will have to run one of the following commands. If you are unsure how you have installed it, just try out both.

```
flatpak --user override de.schmidhuberj.tubefeeder --talk-name=org.freedesktop.Flatpak
sudo override de.schmidhuberj.tubefeeder --talk-name=org.freedesktop.Flatpak
```

You can check that the command worked by using

```
flatpak info --show-permissions de.schmidhuberj.tubefeeder
```

You should see:

```
[Session Bus Policy]
org.freedesktop.Flatpak=talk
```

## Apply the new player

You will have to set the `PLAYER` variable to:

```
PLAYER="flatpak-spawn --host myplayer"
```

If you are using e.g. [Clapper](https://flathub.org/apps/details/com.github.rafostar.Clapper), you will have to set it to:

```
PLAYER="flatpak-spawn --host flatpak run com.github.rafostar.Clapper"
```

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
