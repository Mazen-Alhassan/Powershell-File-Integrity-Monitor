
## What This Is

A lightweight PowerShell-based File Integrity Monitoring (FIM) tool that creates a SHA-512 baseline for a target folder and monitors for created, modified, or deleted files. Designed for simple security monitoring and lab environments without requiring a full SIEM or file-monitoring stack.

## Tech Stack

- **Language:** PowerShell
- **Runtime:** Windows PowerShell or PowerShell 7
- **Built-in cmdlets:** `Get-FileHash`, `Get-ChildItem`, `Get-Content`, `Test-Path`, and `Out-File`

## Project Structure

```text
.
├── Fim.ps1       # PowerShell entry point and monitoring loop
├── Files/        # Sample files used for baseline testing
│   ├── a.txt
│   ├── b.txt
│   ├── c.txt
│   └── d.txt
└── baseline.txt  # Generated when collecting a baseline
```

## File Integrity Monitor (FIM)

```mermaid
flowchart TD
    A([Start]) --> B{Choose operation}

    B -->|Create baseline| C[Calculate SHA-512 hashes]
    C --> D[Save file paths and hashes to baseline.txt]
    D --> E([Baseline created])

    B -->|Monitor files| F[Load baseline.txt]
    F --> G[Check target files]
    G --> H{File exists?}

    H -->|No| I[Alert: File deleted]
    H -->|Yes| J[Calculate current hash]

    J --> K{Hash matches baseline?}
    K -->|No| L[Alert: File modified]
    K -->|Yes| M[File unchanged]

    I --> N[Continue monitoring]
    L --> N
    M --> N
    N --> G

    classDef startEnd fill:#d9eaf7,stroke:#456,color:#000
    classDef process fill:#fce8d5,stroke:#987,color:#000
    classDef decision fill:#fff2cc,stroke:#987,color:#000
    classDef alert fill:#d9ead3,stroke:#587,color:#000

    class A,E startEnd
    class C,D,F,G,J,N process
    class B,H,K decision
    class I,L alert
```
