# Subscribing to a channel

## Select platform

Just go to the subscriptions tab, click the `+`-icon and type in the desired channel name and click the confirm-button.
After clickint the `+`, you will be able to select what platform to use.
Select your platform and input the information described below for your platform.

## Youtube

The channel name does not have to equal the shown name on the channel page. 
To get your desired channel name, go to the persons youtube page and click `Home`.
Now look at the URL you are currently on. 
It should look like `https://www.youtube.com/c/{}/featured`, with `{}` beeing the desired channel name.

You can also put a channel ID into the input box.
For more information about the channel ID, read the next headline.

# Currently in beta

## Youtube

Just type in your channel name. Tubefeeder will search the input in the youtube channels and take the first one.

## Peertube

You will have to input a base url and the channel name.
The base url can be any url pointing to a peertube instance, e.g. `peertube.linuxrocks.online`.
The channel name should be in the format `name@url`, e.g. `chrisweredigital@share.tube`.
You can get the name in such a format when clicking on the clipboard button below the channel name on a video channel.

__Note__: Only video channels are supported.

__Note__: Currently youtube-dl does not work with Peertube, use [yt-dlp](https://github.com/yt-dlp/yt-dlp) instead.
This is already done in the flatpak version, so nothing will need to be done there.

## Lbry

You will have to input the channel name in the format `abcdef:i` where `abcdef` is the channel name and `i` 
is a single character. You can get this format by going to the channel page of the channel, the mentioned format 
can be found in the url.

__Note__: Currently youtube-dl and yt-dlp need to download the full video before playing.
This will mean Tubefeeder will take quite a long time to open the videos.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
