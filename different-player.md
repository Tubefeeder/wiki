# Using a different video player

# Note

This is currently only possible in the [refactoring](https://github.com/Schmiddiii/Tubefeeder/pull/32) branch of the application.
This will also not work on the flatpak version as it does not have access to other software running on your machine.

The default player is mpv.

## Change default player

To change the default video player, use the environmental variable `PLAYER`. You can for example set this variable in your `.profile`, e.g
by adding `PLAYER="myplayer"` to your `.profile`.
