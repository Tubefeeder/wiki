# Installation

## Flatpak (recommended)

The installation of flatpak is the easiest, you can find the application on [flathub](https://flathub.org/apps/details/de.schmidhuberj.tubefeeder). Follow the instructions over there. You will not need to install any prerequisites other than mentioned on the flatpak installation guide.

## Appimage

### Prerequisites

* [mpv](https://mpv.io/) (or any other video player if you follow [this](https://github.com/Schmiddiii/Tubefeeder/wiki/Using-a-different-player)
* [youtube-dl](https://youtube-dl.org/) (will often be installed with mpv)

# Installation

To use the AppImage, just download it from the [releases](https://github.com/Schmiddiii/Tubefeeder/releases) tab to your Pinephone.
I recommend the usage of [appimaged](https://github.com/probonopd/go-appimage) to integrate the application to your 
environment.

# Alternative: Getting the binary

## Downloading the binary

* Download the newest binary in the `Releases` tab of Github
* Download `tubefeeder.desktop`, `tubefeeder.png` `tools/install.sh`, put these in the same folder as the downloaded binary
* Jump to the section `Automated installation`

## Compiling the binary
Note: This method of installation is recommended, if you want the newest features and have experience in compiling.

### Prerequisites (on your computer)
* [Docker](https://www.docker.com/)
* [Cross](https://github.com/rust-embedded/cross)

### Compilation
* Clone this repository, `cd` into it
* Run `docker build -t tubefeeder docker/` (this may take a long time)
* Run `cross build --target=aarch64-unknown-linux-gnu` (this may also take a long time)


# Installation on the Pinephone

## Automated installation
* Enable [ssh](https://www.ssh.com/ssh/) on the Pinephone, usually by running `sudo systemctl start sshd`
* Run `chmod +x ./tools/install.sh`
* Run `./tools/install.sh {user} {ip}`, replace `{user}` with the user on the Pinephone (e.g. `manjaro`) and `{ip}` with the ip address of the device (usually starting with `192.168.`)

## Manual installation
* Enable [ssh](https://www.ssh.com/ssh/) on the Pinephone, usually by running `sudo systemctl start sshd`
* Copy the compiled binary to the Pinephone (e.g. `scp target/aarch64-unknown-linux-gnu/debug/tubefeeder {user}@{ip}:~/.local/bin/tubefeeder`, replace `{user}@{ip}` with the user and ip of your device, create any directories if any errors happen)
* Optional but highly encouraged:
    * Change `{user}` in the `tubefeeder.desktop` file to the user of your pinephone 
    * Copy the .desktop file (e.g. `scp tubefeeder.desktop {user}@{ip}:~/.local/share/applications`)
    * Copy the .png file (e.g. `scp tubefeeder.png {user}@{ip}:~/.local/share/icons`)

{% include_relative notice-with-header.md %}
