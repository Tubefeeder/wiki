# Publishing a new release

There are a few things that need to be done to create a new release.

- Update `Cargo.toml`: version
- Update version in about page, `src/gui/header_bar.rs`
- Update `packaging/de.schmidhuberj.tubefeeder.appdata.xml`: releases with description
- Build AppImage
- Validate AppImage
- Github release
- Update flathub `cargo-sources.json` using [flatpak-cargo-generator](https://github.com/flatpak/flatpak-builder-tools/tree/master/cargo).
- Update flathub `de.schmidhuberj.tubefeeder.json` module tubefeeder with released tar.gz and sha256
- Validate flatpak

{% include_relative notice_with_header.md %}
