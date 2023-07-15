# Compile flatpak

If you changed any dependencies in Pipeline, you will first need to regenerate the `cargo-sources.json`-file.
For this you will need `flatpak-cargo-generator.py` from [here](https://github.com/flatpak/flatpak-builder-tools/tree/master/cargo). Put it into the flatpak repo. Then run

```
./flatpak-cargo-generator.py /path/to/tubefeeder/Cargo.lock -o cargo-sources.json
```

substituting `/path/to/tubefeeder` with the path to the Pipeline-repo.

To compile flatpak, use the following command in the `Flathub/de.schmidhuberj.tubefeeder`-repo:

```
flatpak-builder --user --install build-dir de.schmidhuberj.tubefeeder.json --force-clean
```

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
