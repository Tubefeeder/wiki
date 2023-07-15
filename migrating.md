# Migration from other services

You can easily import subscriptions from both NewPipe and YouTube from the GUI accessible from the menu. You will just need to click the application you want to import data from, select the exported file and the subscriptions will be imported. Note that this will not override any subscriptions, only new subscriptions will be added.

For exporting the data from the applications, you will have to:

* NewPipe: Export your subscriptions in the "Subscriptions" tab. Only YouTube subscriptions will be imported, non-YouTube subscriptions will be ignored.
* YouTube: Download your YouTube subscriptions as a `.csv` [here](https://takeout.google.com/takeout/custom/youtube). 

## Old way (via scripts)

### From NewPipe

If you are using [NewPipe](https://newpipe.net/), you can migrate your subscriptions to Pipeline in the following way:

* Export your subscriptions from Newpipe in the "Subscriptions" tab.
* Move the exported subscriptions to your computer
* Run "newpipe_to_tubefeeder.sh" in this repositories "tools" folder giving the subscriptions from NewPipe as an argument
* Save the generated output in a file "subscriptions.db", move this file to your Pinephone to "~/.local/share/tubefeeder/subscriptions.csv"
* Restart Pipeline 

### From YouTube

You should be able to download your YouTube subscriptions as a `.csv` [here](https://takeout.google.com/takeout/custom/youtube). 
Run the `tools/youtube_to_tubefeeder.sh` script and move the resulting output to "~/.local/share/tubefeeder/subscriptions.csv". 
After restarting Pipeline, the subscriptions should be imported.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
