# Subscribing to a channel

## The normal way

Just go to the subscriptions tab, click the `+`-icon and type in the desired channel name and click the confirm-button.
The channel name does not have to equal the shown name on the channel page. 
To get your desired channel name, go to the persons youtube page and click `Home`.
Now look at the URL you are currently on. 
It should look like `https://www.youtube.com/c/{}/featured`, with `{}` beeing the desired channel name.

You can also put a channel ID into the input box.
For more information about the channel ID, read the next headline.

## Old way (usefull for mass subscription)

Note: This is currently broken in the `refactor`-branch and will be changed.

To subscribe to a channel, do the following:

* Launch the application at least one time and close it afterwards
* A file should have been created in `$XDG_DATA_HOME/tubefeeder` (usually `~/.local/share/tubefeeder`) named `subscriptions.db`.
The file should look like this in the beginning:

```
key str "channel_id"
```

* Modify the file to look like this:

```
key str "channel_id"
"channel_id1"
"channel_id2"
"channel_id3"
```

to get the channel id of a youtube channel, look at [this](https://stackoverflow.com/a/16326307) answer on Stackoverflow.
