# Compile the binary

## Prerequisites (on your computer)

* [Rust](https://www.rust-lang.org/)
* [Meson](https://mesonbuild.com/)
* GTK Libraries

## Compilation

First, clone the [repository](https://github.com/Tubefeeder/Tubefeeder). Then compile the application:

```
meson setup build
meson compile -C build
```

You will also need to install the settings file. You will only need to do it once and if the settings changed.

```
sudo cp data/de.schmidhuberj.tubefeeder.gschema.xml /usr/share/glib-2.0/schemas
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

Then you can run the application from the file `build/target/release/tubefeeder`.

## Installation

Make sure you have compiled the application like in the previous section.

Copy the binary to a folder in the `$PATH`, e.g. `/usr/bin`:

```
sudo cp build/target/release/tubefeeder /usr/bin
```

Edit the `Exec`-key of the `.desktop`-file to point to the installed program, e.g. `/usr/bin/tubefeeder`.
Then copy the `.desktop`-file to `/usr/share/applications` (this path may differ depending on your distribution, e.g. Debian uses `/usr/local/share/applications`; you can also use the path `~/.local/share/applications/`):

```
sudo cp data/de.schmidhuberj.tubefeeder.desktop /usr/share/applications
```

You should now see the application in your desktop environment (if not, try restarting) and should be able to execute Tubefeeder.


## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
