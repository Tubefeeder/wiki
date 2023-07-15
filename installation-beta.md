# Installing a beta version

Beta versions often have some new features that will soon make its way into the stable branch.
If you want to help testing, you can install the beta version from Flatpak.

## Important

You should always make a backup of your data before running beta-level versions.
To make a backup of your Pipeline-data, please copy `~/.local/share/tubefeeder` to a save place and restore the data by copying it back.
Only copy the data while Pipeline is not running.

## Installing the beta version

You will first have to remove the stable version, if installed, e.g. by using

```
flatpak remove de.schmidhuberj.tubefeeder
```

Now add the `flathub-beta` repository and install Pipeline:

```
flatpak remote-add flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo
flatpak install flathub-beta de.schmidhuberj.tubefeeder
```



## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
