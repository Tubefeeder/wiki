# Using a different Downloader

Using a different Downloader is similar to the process of [using a different player](https://tubefeeder.github.io/wiki/different-player.html). 

You can again change this directly in the settings, but with Flatpak you will also make sure that it has correct permissions and it is again prefixed by `flatpak-spawn --host`. You can also adjust the `DOWNLOADER` environmental variable.

By default, this variable will be set to:

```
youtube-dl --output $HOME/Downloads/%(title)s-%(id)s.%(ext)s
```

If you are using the Flatpak-Version, `yt-dlp` will be used instead, as this is already packaged in the Flatpak.
When trying to change the `DOWNLOADER` for Flatpak, it is important to leave the `--output $HOME/Downloads/%(title)s-%(id)s.%(ext)s`, as the Flatpak only has access to the `Downloads`-directory.

## Download in a different format

By default, the best available format will be chosen. This is not desirable most of the time as this can take ages to download.

Lets say you want to download 720p instead, and you are using the Flatpak-Version.
You will have to change `DOWNLOADER` to:

```
yt-dlp -f bestvideo[height<=720]+bestaudio/best[height<=720] --output $HOME/Downloads/%(title)s-%(id)s.%(ext)s
```

__Note__: Leaving out the Quotation Marks around the format somehow seems to be important.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
