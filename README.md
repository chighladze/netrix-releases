# Netrix releases

Official Windows installers, release notes, checksums and issue reports for [Netrix](https://netrix-console.com), a local desktop terminal and connection manager.

## Download

Download installers from [Releases](https://github.com/chighladze/netrix-releases/releases). The first Windows candidate is currently being validated; an installer will appear after its release is published.

Each Windows release provides:

- One NSIS `.exe` installer for Windows x64.
- `installer-hashes.sha256`, containing the checksum of that exact installer.
- `release.json`, recording version, filename, size, checksum, signing status and source commit.

Choose the EXE under **Assets**. GitHub's automatically generated **Source code** ZIP/TAR archives contain this distribution repository's documentation, not the Netrix application or its installer. Application source and build logs are maintained separately.

## Verify a download

Run this in PowerShell, replacing the filename with the downloaded EXE:

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\Netrix_<version>_x64-setup.exe'
```

Compare the result with `installer-hashes.sha256` from the same release. Read its notes for the exact signing and testing status. Unsigned beta builds are explicitly marked as prereleases and may show a Windows unknown-publisher warning. A checksum verifies the downloaded bytes; it is not a publisher signature.

## Bugs and requests

Search [existing issues](https://github.com/chighladze/netrix-releases/issues), then use the appropriate form:

- [Report a bug](https://github.com/chighladze/netrix-releases/issues/new?template=bug-report.yml): include the Netrix version, Windows version, steps to reproduce, expected result and actual result.
- [Request a feature](https://github.com/chighladze/netrix-releases/issues/new?template=feature-request.yml): describe the problem, proposed improvement and any current workaround.

Reports are public. Remove passwords, tokens, private keys, personal data and private server details from screenshots or logs before posting. Do not upload workspace databases or vault files. Fixes remain in the private application repository; public release notes describe the changes delivered to users.

## License

Netrix's existing [MIT license](LICENSE) is included here and in the Windows installer. Third-party components retain their respective licenses.
