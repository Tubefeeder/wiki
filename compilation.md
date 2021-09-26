# Compile the binary

## Prerequisites (on your computer)

* [Rust](https://www.rust-lang.org/)

## Compilation

Just clone the [repository](https://github.com/Schmiddiii/Tubefeeder) and run

```
cargo run
```

in the repositories root.

# Compile the binary for the Pinephone

# Compiling the binary

Note: This method of installation is not recommended unless you want to contribute to Tubefeeder.

## Prerequisites (on your computer)

* [Rust](https://www.rust-lang.org/)
* [Docker](https://www.docker.com/)
* [Cross](https://github.com/rust-embedded/cross)

## Compilation

* Clone this repository, `cd` into it
* Run `docker build -t tubefeeder docker/` (this may take a long time)
* Run `cross build --target=aarch64-unknown-linux-gnu` (this may also take a long time)

## Installation on the Pinephone

### Automated installation

* Enable [ssh](https://www.ssh.com/ssh/) on the Pinephone, usually by running `sudo systemctl start sshd`
* Run `chmod +x ./tools/install.sh`
* Run `./tools/install.sh {user} {ip}`, replace `{user}` with the user on the Pinephone (e.g. `manjaro`) and `{ip}` with the ip address of the device (usually starting with `192.168.`)

### Manual installation

* Enable [ssh](https://www.ssh.com/ssh/) on the Pinephone, usually by running `sudo systemctl start sshd`
* Copy the compiled binary to the Pinephone (e.g. `scp target/aarch64-unknown-linux-gnu/debug/tubefeeder {user}@{ip}:~/.local/bin/tubefeeder`, replace `{user}@{ip}` with the user and ip of your device, create any directories if any errors happen)
* Optional but highly encouraged:
    * Change `{user}` in the `tubefeeder.desktop` file to the user of your pinephone 
    * Copy the .desktop file (e.g. `scp tubefeeder.desktop {user}@{ip}:~/.local/share/applications`)
    * Copy the .png file (e.g. `scp tubefeeder.png {user}@{ip}:~/.local/share/icons`)

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
