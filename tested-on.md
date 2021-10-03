Even if your distribution is not listed right here, it will very likely work.

## Manjaro

* Phosh
    * Beta 5
* Plasma
    * Beta 2: `libhandy` must be installed manually: `sudo pacman -S libhandy`

## Arch Linux Arm

* Phosh
    * 2021/02/14

## PostmarketOS / Alpine

* Phosh
    * 2021/06/07 (OnePlus 6)

### Build instructions

These instructions are for native building on device.

Install dependencies:
```bash
sudo apk add git cargo glib glib-dev cairo-dev pango-dev atk-dev gdk-pixbuf-dev gtk+3.0-dev libhandy1-dev mpv youtube-dl
```

Clone the repo and build:
```bash
git clone https://github.com/Tubefeeder/Tubefeeder
cd Tubefeeder

cargo build --release
```

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
