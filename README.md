# Scoop bucket for aesx

[aesx](https://github.com/yohasacura/aesx) is free, offline, open-source file encryption for
Windows, macOS and Linux: one password, one file or folder in, one `.aesx` file out, with
AES-256-GCM and no third-party code.

```powershell
scoop bucket add yohasacura https://github.com/yohasacura/scoop-bucket
scoop install aesx
```

Afterwards `scoop update aesx` keeps it current, and `scoop uninstall aesx` removes it.

## What this installs

The manifest does not build anything. Scoop downloads the archive that the
[aesx release workflow](https://github.com/yohasacura/aesx/actions/workflows/release.yml) built
for your processor (x64 or ARM64), checks its SHA-256 against the value in
[bucket/aesx.json](bucket/aesx.json), unpacks it, and puts `aesx` on your `PATH`. Downloaded
this way, the file carries no "from the internet" mark, so Windows SmartScreen does not ask
about it on first launch.

## How it stays current

[update.yml](.github/workflows/update.yml) looks at the latest aesx release once a day. It
downloads the release files, verifies their build provenance attestation (releases from 1.1.0
on have one), computes the checksums itself, and commits the new manifest.
[test.yml](.github/workflows/test.yml) then downloads what the manifest names, on x64 and on
ARM64, compares the checksums, and runs the executable and its self-tests.

To follow a release at once instead of waiting for the daily run:

```powershell
gh workflow run update.yml --repo yohasacura/scoop-bucket
```

## Issues

Problems with aesx itself belong in the
[aesx repository](https://github.com/yohasacura/aesx/issues); problems with installing it
through Scoop belong here.

## License

[Apache License 2.0](LICENSE), like aesx.
