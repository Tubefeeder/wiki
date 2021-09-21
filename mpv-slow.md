# Mpv is slow

If your video playback is slow, it is mostly because of the underpowered hardware and the lack of hardware acceleration for MPV of the Pinephone. Furthermove MPV will always play the best quality video and audio it can get, even on the low screen-resolution on the Pinephone.

The negate this issue, I recommend putting this line into `~/.config/mpv/mpv.conf`

```
ytdl-format=bestvideo[height<=?720]+worstaudio/worst
```

This will force MPV to use 720p video (the Pinephone also only has a 720p screen so it is ok) and worst audio (I hear no difference).

Video Playback should now be acceptable.

{% include_relative notice-with-header.md %}
