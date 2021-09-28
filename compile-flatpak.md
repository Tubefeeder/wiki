# Compile flatpak

If you changed any dependencies in Tubefeeder, you will first need to regenerate the `cargo-sources.json`-file.
For this you will need `flatpak-cargo-generator.py` from [here](https://github.com/flatpak/flatpak-builder-tools/tree/master/cargo). Put it into the flatpak repo. Then run

```
./flatpak-cargo-generator.py /path/to/tubefeeder/Cargo.lock -o cargo-sources.json
```

substituting `/path/to/tubefeeder` with the path to the Tubefeeder-repo.

To compile flatpak, use the following command in the `Flathub/de.schmidhuberj.Tubefeeder`-repo:

```
flatpak-builder --install build-dir de.schmidhuberj.tubefeeder.json --force-clean
```
