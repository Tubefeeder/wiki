# Compile the binary

## Prerequisites (on your computer)

* [Rust](https://www.rust-lang.org/)

## Compilation

Just clone the [repository](https://github.com/Tubefeeder/Tubefeeder) and run

```
cargo run
```

in the repositories root.

# Cross Compiling the binary for the PP

__Note__: This method of compilation is heavily discouraged as it may take hours with only a small benefit on the PinePhone-side.

## Prerequisites (on your computer)

* [Rust](https://www.rust-lang.org/)
* [Docker](https://www.docker.com/)
* [Cross](https://github.com/rust-embedded/cross)

## Compilation

* Clone this repository, `cd` into it
* Run `docker buildx build --platform linux/arm64 -t tubefeeder docker` (this may take a long time)
* Run `cross build --target=aarch64-unknown-linux-gnu` (this may also take a long time, reserve at least 4 hours of maximum CPU- and memory-usage)

## Installation on the Pinephone

* Enable [ssh](https://www.ssh.com/ssh/) on the Pinephone, usually by running `sudo systemctl start sshd`
* Copy the compiled binary to the Pinephone (e.g. `scp target/aarch64-unknown-linux-gnu/debug/tubefeeder {user}@{ip}:~/.local/bin/tubefeeder`, replace `{user}@{ip}` with the user and ip of your device, create any directories if any errors happen)
* Optional but highly encouraged:
    * Change `{user}` in the `packaging/tubefeeder.desktop` file to the user of your pinephone 
    * Copy the .desktop file (e.g. `scp packaging/tubefeeder.desktop {user}@{ip}:~/.local/share/applications`)
    * Copy the .png file (e.g. `scp packaging/tubefeeder.png {user}@{ip}:~/.local/share/icons`)
    * Copy the locales file (Everything in `po/locale` with ending `.mo` into `/usr/share/locale` with the same structure)

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
