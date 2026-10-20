## What this is

This is a lightweight PowerShell-based file integrity monitoring tool that creates a SHA-512 baseline for a target folder and then watches for created, modified, or deleted files. It is designed for simple security monitoring or lab scenarios where a quick integrity check is needed without a larger SIEM or file-monitoring stack.

### Stack
- **Language(s):** PowerShell
- **Framework / runtime:** PowerShell script running in Windows PowerShell or PowerShell 7
- **Notable libraries:** built-in cmdlets including Get-FileHash, Get-ChildItem, Get-Content, Test-Path, and Out-File

## How it's organized

```text
.
├── Fim.ps1              PowerShell entry point and monitoring loop
├── Files/               sample files used for baseline testing
│   ├── a.txt
│   ├── b.txt
│   ├── c.txt
│   └── d.txt       
├── baseline.txt         generated at runtime when collecting a baseline