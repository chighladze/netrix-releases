# Netrix releases

Official Windows installers, release notes, checksums and issue reports for [Netrix](https://netrix-console.com), a local desktop terminal and connection manager.

## Download

The first public Windows x64 beta, **0.3.0-beta.4**, is available:

- [Download the Windows installer](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.4/Netrix_0.3.0-beta.4_x64-setup.exe).
- [Read release notes, testing scope and known limitations](https://github.com/chighladze/netrix-releases/releases/tag/v0.3.0-beta.4).
- [Download its SHA-256 manifest](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.4/installer-hashes.sha256).

This beta is unsigned. Existing-profile installation and basic SSH/SFTP, locking and restart checks passed; clean-profile installation and the full manual matrix remain unverified. Back up your existing workspace and keep its master password before replacing an installation. See [all releases](https://github.com/chighladze/netrix-releases/releases) for version history.

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

## Installation help

**Missing WebView2:** if Netrix reports `Could not find the WebView2 Runtime`, close Netrix and install **Evergreen Standalone Installer — x64** from [Microsoft's official WebView2 page](https://developer.microsoft.com/en-us/microsoft-edge/webview2/). Confirm that the runtime installer is published by Microsoft, then reopen Netrix under the same Windows user. Keep your Netrix data and vault intact; deleting hosts, app data or resetting your password is not needed. This recovery restored launch on the computer reported by the owner. Beta.4 embeds the online WebView2 downloader; the next installer will be tested with the full offline runtime package before publication.

**Unknown publisher / SmartScreen:** beta.4 is unsigned, so Windows or the browser may warn about its publisher or download reputation. Verify the official release and checksum. Do not disable Windows protection or add blanket exclusions. A named malware detection is a separate issue; report its exact detection name and the installer hash without uploading private workspace files. Trusted code signing is planned, but [Microsoft notes](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation) that new signed files can still show reputation warnings.

## Bugs and requests

Search [existing issues](https://github.com/chighladze/netrix-releases/issues), then use the appropriate form:

- [Report a bug](https://github.com/chighladze/netrix-releases/issues/new?template=bug-report.yml): include the Netrix version, Windows version, steps to reproduce, expected result and actual result.
- [Request a feature](https://github.com/chighladze/netrix-releases/issues/new?template=feature-request.yml): describe the problem, proposed improvement and any current workaround.

Reports are public. Remove passwords, tokens, private keys, personal data and private server details from screenshots or logs before posting. Do not upload workspace databases or vault files. Fixes remain in the private application repository; public release notes describe the changes delivered to users.

## License

Netrix's existing [MIT license](LICENSE) is included here and in the Windows installer. Third-party components retain their respective licenses.
