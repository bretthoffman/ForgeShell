Create your PRD as a single .md file anywhere on your computer, then run the command for your platform and agent. ForgeShell will check dependencies, ask for your PRD path and application name, create a clean workspace, and open Codex or Claude inside shell-core ready for you to type the word 'begin'.

'''
**macOS — Codex**

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/bretthoffman/ForgeShell/main/shell-core/bootstrap/mac/codex.sh)"

**macOS — Claude**

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/bretthoffman/ForgeShell/main/shell-core/bootstrap/mac/claude.sh)"

**Windows — Codex
(Powershell)**

iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/bretthoffman/ForgeShell/main/shell-core/bootstrap/windows/codex.ps1'))

**Windows — Claude
(Powershell)**

iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/bretthoffman/ForgeShell/main/shell-core/bootstrap/windows/claude.ps1'))

'''
