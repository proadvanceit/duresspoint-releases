# DuressPoint releases

Signed Windows installers for the DuressPoint workstation app: the floating duress button, the alert popups, and the agent service that runs on each clinic PC.

## Which release to use

Each build is published here first as a **pre-release**. Once it has passed lab testing, it's marked as the **latest release**. Install the latest release at clinics:

- **Release page:** https://github.com/proadvanceit/duresspoint-releases/releases/latest
- **Direct download**, always the latest release: https://github.com/proadvanceit/duresspoint-releases/releases/latest/download/DuressPointSetup.exe

Each release has the installer twice: as `DuressPointSetup-<version>.exe`, and as `DuressPointSetup.exe` for the direct download link above.

These downloads are for first installs, through Intune or an RMM. Installed workstations update themselves from the admin website.

## Check the signature

Every installer is signed by **ProAdvance Pty Ltd**. In PowerShell:

```powershell
Get-AuthenticodeSignature .\DuressPointSetup.exe | Format-List Status, SignerCertificate
```

`Status` must be `Valid`. Each release's notes also give the installer's SHA-256.

## Install silently

Run as SYSTEM or an administrator:

```bat
DuressPointSetup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART /SERVER=https://<admin website> /ENROLMENTCODE=<code>
```

The admin website's page for each site shows the exact command, with its address and an enrolment code filled in.
