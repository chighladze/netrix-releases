# Netrix releases

Official Windows installers, Portable ZIP, release notes, checksums and issue reports for [Netrix](https://netrix-console.com), a local desktop terminal and connection manager.

## Download

The current Windows x64 prerelease is **0.3.0-beta.13**.

**[Download Lightweight for Windows x64 (9.4 MB)](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.13/Netrix_0.3.0-beta.13_x64-lightweight-setup.exe)** · [Offline Full with WebView2 (305.5 MB)](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.13/Netrix_0.3.0-beta.13_x64-offline-full-setup.exe) · [Portable ZIP (10.0 MB)](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.13/Netrix_0.3.0-beta.13_x64-portable.zip)

Choose **Lightweight** for most PCs. It uses the installed WebView2 runtime or downloads it from Microsoft if needed. Choose **Offline Full** for a disconnected PC. Both installers contain the same application.

Extract **Portable ZIP** to a writable folder on a PC with WebView2 Evergreen installed and open `Netrix.exe`. To move your workspace, close Netrix and copy the entire folder, including `Netrix.portable` and `Data`. Use the same master password on the next PC.

On Windows 10 LTSC, Lightweight upgraded a beta.12 workspace and its Vault opened with the original password. Offline Full installed WebView2 and opened Netrix on a clean VM with no network adapter. Installed and Portable copies ran side by side with separate hosts and Vaults. The Portable workspace moved from P: to R: between two independently installed Windows 10 virtual machines with different user accounts. The saved SSH host, terminal font settings and Vault item were available with the original master password.

The Netrix executables and installers are unsigned. [Release notes](https://github.com/chighladze/netrix-releases/releases/tag/v0.3.0-beta.13).

| Windows x64 download | Bytes | SHA-256 |
| --- | ---: | --- |
| Lightweight | 9,350,018 | `3f157c37fb625da6cff03db17519d69c50946575a067682aba4ebfbf66b6a2b6` |
| Offline Full | 305,518,698 | `7f5650b0bf3ec203a227cc293fcc0502a6052e84b8c632dd71b97b21c26fb56b` |
| Portable ZIP | 9,956,736 | `0addcc441992d8e4a580a39eb8f8c119021f7d44839a672019b05987fa0a2ff2` |

[Checksum manifest](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.13/installer-hashes.sha256) · [Release metadata](https://github.com/chighladze/netrix-releases/releases/download/v0.3.0-beta.13/release.json) · [All releases](https://github.com/chighladze/netrix-releases/releases)

Under **Assets**, select a named Netrix EXE or the **Portable ZIP**. GitHub’s **Source code** archives on this release contain the distribution repository. The application source and build guides are available in [netrix-desktop](https://github.com/chighladze/netrix-desktop).

## Verify a download

In PowerShell, use the filename of the EXE or ZIP you downloaded.

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\Netrix_0.3.0-beta.13_x64-lightweight-setup.exe'
```

Compare the result with `installer-hashes.sha256` from the same release. Read its notes for the exact signing and testing status. Unsigned beta builds are explicitly marked as prereleases and may show a Windows unknown-publisher warning. A checksum verifies the downloaded bytes; it is not a publisher signature.

## Installation help

**Beta.8 startup failure:** use the displayed recovery guidance and **Copy diagnostics** option. Exit code 1 alone does not identify the cause. Keep the exact error and your workspace files intact; do not reset the vault to troubleshoot startup. Beta.8 no longer imports the external Visual C++ redistributable DLLs found in beta.5. Its WebView2 setup checks whether the runtime can be opened and attempts offline recovery when needed, but installation from an absent-runtime baseline has not yet been tested.

**Beta.5: backend terminated with `-1073741515` / `0xC0000135`:** Windows could not load a required DLL. Beta.5's backend requires `VCRUNTIME140.dll`, and this prerequisite is not installed by the Netrix installer. Close Netrix, install or repair the official [Microsoft Visual C++ Redistributable x64](https://aka.ms/vc14/vc_redist.x64.exe), restart Windows if Microsoft's installer requests it, then reopen Netrix. The owner confirmed that this removed the reported backend error on another test computer. Keep your Netrix workspace and vault intact. If the error persists, report the exact message; this Windows status can also refer to other missing DLLs.

**Missing WebView2 in beta.5:** if Netrix reports `Could not find the WebView2 Runtime`, close Netrix and install **Evergreen Standalone Installer — x64** from [Microsoft's official WebView2 page](https://developer.microsoft.com/en-us/microsoft-edge/webview2/). Confirm that the runtime installer is published by Microsoft, then reopen Netrix under the same Windows user. Keep your Netrix data and vault intact; deleting hosts, app data or resetting your password is not needed. This recovery restored launch on the computer reported by the owner. Beta.5 includes the full runtime installer, but a broken existing runtime registration can still cause it to skip installation. Automatic recovery from this condition is not fixed in beta.5. If Microsoft's installer fails or says the runtime is already installed, retain its exact message and report the issue.

**Unknown publisher / SmartScreen:** Netrix beta builds are unsigned, so Windows or the browser may warn about its publisher or download reputation. Verify the official release and checksum. Do not disable Windows protection or add blanket exclusions. A named malware detection is a separate issue; report its exact detection name and the installer hash without uploading private workspace files. Trusted code signing is planned, but [Microsoft notes](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation) that new signed files can still show reputation warnings. Microsoft's signature on the bundled WebView2 installer does not sign Netrix.

## Source and customization

The public [Netrix desktop project](https://github.com/chighladze/netrix-desktop) contains the application source under MIT. Fork it to build and customize your own version.

- [Build and run from source](https://github.com/chighladze/netrix-desktop/blob/main/docs/build_instructions.md).
- [Customize Netrix](https://github.com/chighladze/netrix-desktop/blob/main/docs/CUSTOMIZATION.md).
- [Contribute a change](https://github.com/chighladze/netrix-desktop/blob/main/CONTRIBUTING.md).

Use this releases repository for ready-made installers and existing bug reports. Source archives downloaded from netrix-desktop contain application code; source archives here contain distribution documentation.

## Bugs and requests

Search [existing issues](https://github.com/chighladze/netrix-releases/issues), then use the appropriate form:

- [Report a bug](https://github.com/chighladze/netrix-releases/issues/new?template=bug-report.yml): include the Netrix version, Windows version, steps to reproduce, expected result and actual result.
- [Request a feature](https://github.com/chighladze/netrix-releases/issues/new?template=feature-request.yml): describe the problem, proposed improvement and any current workaround.

Reports are public. Remove passwords, tokens, private keys, personal data and private server details from screenshots or logs before posting. Do not upload workspace databases or vault files. Application source and pull requests are available in [netrix-desktop](https://github.com/chighladze/netrix-desktop); public release notes describe the changes delivered to users.

## License

Netrix's existing [MIT license](LICENSE) is included here and in the Windows installer. Third-party components retain their respective licenses.
