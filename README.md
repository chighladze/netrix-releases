# Netrix releases

Official Windows installers, release notes, checksums and issue reports for [Netrix](https://netrix-console.com), a local desktop terminal and connection manager.

## Download

The current Windows x64 beta, **0.3.0-beta.8**, is available (approximately 225 MB, including the full Microsoft WebView2 installer):

- [Download the Windows installer](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.8/Netrix_0.3.0-beta.8_x64-setup.exe).
- [Read release notes, testing scope and known limitations](https://github.com/chighladze/netrix-releases/releases/tag/v0.3.0-beta.8).
- [Download its SHA-256 manifest](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.8/installer-hashes.sha256).

This beta is unsigned and may display a Windows unknown-publisher warning. It removes the known dependency on a separately installed Visual C++ package, adds startup recovery guidance and copyable diagnostics, and attempts offline WebView2 recovery during setup. Setup stops if recovery fails.

Automated checks passed, but installation on clean Windows without Visual C++ has not been tested. Missing-WebView2 offline installation, desktop lock/unlock, restart/persistence, upgrade/uninstall and SSH/SFTP GUI acceptance remain unverified for this exact beta. Back up your existing workspace and keep its master password before upgrading. See [release notes](https://github.com/chighladze/netrix-releases/releases/tag/v0.3.0-beta.8) for the exact validation scope and [all releases](https://github.com/chighladze/netrix-releases/releases) for version history.

Installer: 225,425,062 bytes. SHA-256: `58f92df91599640f90e8ef9e7713f00eb346bebbb3732a9738d8879b2f7004dc`. All three public release assets were downloaded and their complete checksums verified. This confirms download integrity, not clean-Windows compatibility.

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

**Beta.8 startup failure:** use the displayed recovery guidance and **Copy diagnostics** option. Exit code 1 alone does not identify the cause. Keep the exact error and your workspace files intact; do not reset the vault to troubleshoot startup. Beta.8 no longer imports the external Visual C++ redistributable DLLs found in beta.5. Its WebView2 setup checks whether the runtime can be opened and attempts offline recovery when needed, but installation from an absent-runtime baseline has not yet been tested.

**Beta.5: backend terminated with `-1073741515` / `0xC0000135`:** Windows could not load a required DLL. Beta.5's backend requires `VCRUNTIME140.dll`, and this prerequisite is not installed by the Netrix installer. Close Netrix, install or repair the official [Microsoft Visual C++ Redistributable x64](https://aka.ms/vc14/vc_redist.x64.exe), restart Windows if Microsoft's installer requests it, then reopen Netrix. The owner confirmed that this removed the reported backend error on another test computer. Keep your Netrix workspace and vault intact. If the error persists, report the exact message; this Windows status can also refer to other missing DLLs.

**Missing WebView2 in beta.5:** if Netrix reports `Could not find the WebView2 Runtime`, close Netrix and install **Evergreen Standalone Installer — x64** from [Microsoft's official WebView2 page](https://developer.microsoft.com/en-us/microsoft-edge/webview2/). Confirm that the runtime installer is published by Microsoft, then reopen Netrix under the same Windows user. Keep your Netrix data and vault intact; deleting hosts, app data or resetting your password is not needed. This recovery restored launch on the computer reported by the owner. Beta.5 includes the full runtime installer, but a broken existing runtime registration can still cause it to skip installation. Automatic recovery from this condition is not fixed in beta.5. If Microsoft's installer fails or says the runtime is already installed, retain its exact message and report the issue.

**Unknown publisher / SmartScreen:** Netrix beta builds are unsigned, so Windows or the browser may warn about its publisher or download reputation. Verify the official release and checksum. Do not disable Windows protection or add blanket exclusions. A named malware detection is a separate issue; report its exact detection name and the installer hash without uploading private workspace files. Trusted code signing is planned, but [Microsoft notes](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation) that new signed files can still show reputation warnings. Microsoft's signature on the bundled WebView2 installer does not sign Netrix.

## Bugs and requests

Search [existing issues](https://github.com/chighladze/netrix-releases/issues), then use the appropriate form:

- [Report a bug](https://github.com/chighladze/netrix-releases/issues/new?template=bug-report.yml): include the Netrix version, Windows version, steps to reproduce, expected result and actual result.
- [Request a feature](https://github.com/chighladze/netrix-releases/issues/new?template=feature-request.yml): describe the problem, proposed improvement and any current workaround.

Reports are public. Remove passwords, tokens, private keys, personal data and private server details from screenshots or logs before posting. Do not upload workspace databases or vault files. Fixes remain in the private application repository; public release notes describe the changes delivered to users.

## License

Netrix's existing [MIT license](LICENSE) is included here and in the Windows installer. Third-party components retain their respective licenses.
