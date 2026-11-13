# Netrix releases

Official Windows installers, release notes, checksums and issue reports for [Netrix](https://netrix-console.com), a local desktop terminal and connection manager.

## Download

The current Windows x64 beta, **0.3.0-beta.5**, is available (approximately 225 MB, including the full Microsoft WebView2 installer):

- [Download the Windows installer](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.5/Netrix_0.3.0-beta.5_x64-setup.exe).
- [Read release notes, testing scope and known limitations](https://github.com/chighladze/netrix-releases/releases/tag/v0.3.0-beta.5).
- [Download its SHA-256 manifest](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.5/installer-hashes.sha256).

This beta is unsigned. On the Windows 10 Pro test computer, launch required manual WebView2 recovery; SSH, SFTP browsing and file download without interrupting SSH then passed. Offline installation from an absent-runtime baseline, lock/unlock, restart/persistence, uninstall/reinstall and the full failure-path matrix remain unverified for this exact beta. Back up your existing workspace and keep its master password before replacing an installation. See [all releases](https://github.com/chighladze/netrix-releases/releases) for version history.

Some Windows computers also need a separate Microsoft Visual C++ x64 runtime installation for beta.5. See [installation help](#installation-help) if the backend terminates before your workspace opens.

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

**Backend terminated with `-1073741515` / `0xC0000135`:** Windows could not load a required DLL. Beta.5's backend requires `VCRUNTIME140.dll`, and this prerequisite is not installed by the Netrix installer. Close Netrix, install or repair the official [Microsoft Visual C++ Redistributable x64](https://aka.ms/vc14/vc_redist.x64.exe), restart Windows if Microsoft's installer requests it, then reopen Netrix. The owner confirmed that this removed the reported backend error on another test computer. Keep your Netrix workspace and vault intact. If the error persists, report the exact message; this Windows status can also refer to other missing DLLs.

**Missing WebView2:** if Netrix reports `Could not find the WebView2 Runtime`, close Netrix and install **Evergreen Standalone Installer — x64** from [Microsoft's official WebView2 page](https://developer.microsoft.com/en-us/microsoft-edge/webview2/). Confirm that the runtime installer is published by Microsoft, then reopen Netrix under the same Windows user. Keep your Netrix data and vault intact; deleting hosts, app data or resetting your password is not needed. This recovery restored launch on the computer reported by the owner. Beta.5 includes the full runtime installer, but a broken existing runtime registration can still cause it to skip installation. Automatic recovery from this condition is not fixed in beta.5. If Microsoft's installer fails or says the runtime is already installed, retain its exact message and report the issue.

**Unknown publisher / SmartScreen:** beta.5 is unsigned, so Windows or the browser may warn about its publisher or download reputation. Verify the official release and checksum. Do not disable Windows protection or add blanket exclusions. A named malware detection is a separate issue; report its exact detection name and the installer hash without uploading private workspace files. Trusted code signing is planned, but [Microsoft notes](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation) that new signed files can still show reputation warnings. Microsoft's signature on the bundled WebView2 installer does not sign Netrix.

## Bugs and requests

Search [existing issues](https://github.com/chighladze/netrix-releases/issues), then use the appropriate form:

- [Report a bug](https://github.com/chighladze/netrix-releases/issues/new?template=bug-report.yml): include the Netrix version, Windows version, steps to reproduce, expected result and actual result.
- [Request a feature](https://github.com/chighladze/netrix-releases/issues/new?template=feature-request.yml): describe the problem, proposed improvement and any current workaround.

Reports are public. Remove passwords, tokens, private keys, personal data and private server details from screenshots or logs before posting. Do not upload workspace databases or vault files. Fixes remain in the private application repository; public release notes describe the changes delivered to users.

## License

Netrix's existing [MIT license](LICENSE) is included here and in the Windows installer. Third-party components retain their respective licenses.
