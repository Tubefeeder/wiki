# Publishing a new release

There are a few things that need to be done to create a new release.

- Update `Cargo.toml`: version.
- Update `packaging/de.schmidhuberj.tubefeeder.appdata.xml`: releases with description.
- Build the crate once.
- Push to GitHub.
- GitHub release.
- Update Flatpak `cargo-sources.json` using [flatpak-cargo-generator](https://github.com/flatpak/flatpak-builder-tools/tree/master/cargo).
- Update Flatpak `de.schmidhuberj.tubefeeder.json` module tubefeeder with released tar.gz and sha256.
- Validate Flatpak.
- Publish Flatpak to Flathub.
- Update AUR packaged `tubefeeder-git` (may not be needed?) and `tubefeeder` with the new version and md5sum.
- Regenenerate `.SRCINFO`.
- Publish to the AUR.
- Ask @hwittenborn to update MPR.

## Notice

{% include_relative copyright_schmidhuber_julian.md %}

{% include_relative NOTICE %}
