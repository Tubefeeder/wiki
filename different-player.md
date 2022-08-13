# Using a different video player

__Note__: Depending on the video player you use, you may not be able to play videos from all supported platforms.

# Using the settings (not for Flatpak)

Just change the value of the "Player"-field in the settings.

# Using the settings for Flatpak

Changing the default player for the Flatpak is a little bit harder as the Flatpak version does not have access to run arbitrary commands on the host. You will have to change that permission manually. Additionally, you will have to add a prefix to the command to execute it outside the sandbox.

## Changing the permissions

Depending on how you have installed the Flatpak (user or system-wide) you will have to run one of the following commands. If you are unsure how you have installed it, just try out both.

```
flatpak --user override de.schmidhuberj.tubefeeder --talk-name=org.freedesktop.Flatpak
sudo flatpak  override de.schmidhuberj.tubefeeder --talk-name=org.freedesktop.Flatpak
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

## Prefix

You need to prefix your command with `flatpak-spawn --host` for it to be able to run outside of the sandbox. 

If you are using e.g. [Clapper](https://flathub.org/apps/details/com.github.rafostar.Clapper), you will have to set it to:

```
flatpak-spawn --host flatpak run com.github.rafostar.Clapper
```

# Using environmental variables

__Note__: This overrides any values in the settings.

To change the default video player, use the environmental variable `PLAYER`. You can for example set this variable in your `.profile`, e.g
by adding `PLAYER="myplayer"` to your `.profile`.

For Flatpak, you will again have to change the permissions of the Flatpak and set the `PLAYER` to `PLAYER="flatpak-spawn --host myplayer"`

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
