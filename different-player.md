# Using a different video player

__Note__: Depending on the video player you use, you may not be able to play videos from all supported platforms.

# Using the Preferences

Just change the value of the "Player"-field in the `Preferences`. This value could e.g. be `mpv` or `com.github.rafostar.Clapper`.

# Using environmental variables

__Note__: This overrides any values in the `Preferences`.

To change the default video player, use the environmental variable `PLAYER`. You can for example set this variable in your `.profile`, e.g
by adding `PLAYER="myplayer"` to your `.profile`. This will disable the `Preferences` field for changing the player.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
