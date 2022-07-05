# Migration from other services

## From NewPipe

If you are using [NewPipe](https://newpipe.net/), you can migrate your subscriptions to Tubefeeder in the following way:

* Export your subscriptions from Newpipe in the "Subscriptions" tab.
* Move the exported subscriptions to your computer
* Run "newpipe_to_tubefeeder.sh" in this repositories "tools" folder giving the subscriptions from NewPipe as an argument
* Save the generated output in a file "subscriptions.db", move this file to your Pinephone to "~/.local/share/tubefeeder/subscriptions.csv"
* Restart Tubefeeder 

## From YouTube

You should be able to download your YouTube subscriptions as a `.csv` [here](https://takeout.google.com/takeout/custom/youtube). 
Run the `tools/youtube_to_tubefeeder.sh` script and move the resulting output to "~/.local/share/tubefeeder/subscriptions.csv". 
After restarting Tubefeeder, the subscriptions should be imported.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
