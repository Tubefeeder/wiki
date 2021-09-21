# Migration from other services

## From NewPipe

Note: This is currently broken in the `refactor`-branch and will be changed.

If you are using [NewPipe](https://newpipe.net/), you can migrate your subscriptions to Tubefeeder in the following way:

* Export your subscriptions from Newpipe in the "Subscriptions" tab.
* Move the exported subscriptions to your computer
* Run "newpipe_to_tubefeeder.sh" in this repositories "tools" folder giving the subscriptions from NewPipe as an argument
* Save the generated output in a file "subscriptions.db", move this file to your Pinephone to "~/.local/share/tubefeeder/subscriptions.db"
* Restart Tubefeeder 

{% include_relative notice-with-header.md %}
