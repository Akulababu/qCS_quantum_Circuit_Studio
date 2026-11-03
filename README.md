# qCS 3.2

Installers are split across three branches — one per platform — so
each user only downloads the installer for their own OS.

| Platform | Branch | File |
|---|---|---|
| macOS (Apple Silicon) | [`mac`](../../tree/mac) | `qCS_3.0_installer_maca64.app/` (3.0 build — no 3.2 macOS build yet) |
| Linux (x86_64) | [`linux`](../../tree/linux) | `qCS_3.2_installer_glnxa64.install` |
| Windows (x86_64) | [`windows`](../../tree/windows) | `qCS_3.2_installer_win64.exe` |

User manual: [qCS_3.2_Manual.pdf](qCS_3.2_Manual.pdf).

## What changed in 3.2

qCS 3.2 is a bug-fix release over 3.1.

- Element and node names are kept as written; 3.1 also removed letters such as H, F, OHM and DC from names (for example `PATH_NODE` became `PAT_NODE`), which could break a netlist or silently change the circuit
- Pattern matching: `>=N` windows count events correctly, the check for extra events up to TSTOP now runs, and margin, yield and optimization simulations keep the TSTOP you set
- Pattern input is checked more strictly, so some patterns that 3.1 accepted are rejected with an error that explains the rule
- Negative Pulse and the pulse height, width and expected band are shared by the Margin, Yield and Optimization tabs
- Margin, yield and optimization results can differ from 3.1

---

## Download the installer for your OS

Each branch is an orphan branch holding a single installer. Use
`--single-branch` so only that one file is pulled.

### macOS

The macOS branch still ships the 3.0 build (a 3.2 macOS build has not
been released yet).

1. Create a folder in your own user space, then clone the mac branch inside that folder:
   ```bash
   git clone --single-branch --branch mac --depth 1 https://github.com/Akulababu/qCS_3.1.git
   cd qCS_3.1
   ```
2. Run the installer:
   ```bash
   open qCS_3.0_installer_maca64.app
   ```
3. In the wizard:
   - **License** → Accept.
   - **MATLAB Runtime** → "Use existing" → `/Applications/MATLAB_R2023b.app`
     (or any R2023b MATLAB / MCR install). Otherwise pick download
     mode (pulls ~4 GB).
   - **Install path** → a user-writable path, e.g. `~/Applications/qCS_3.0`.
     Do **not** install into `/Applications/` (admin-only, runtime
     bootstrap may fail to write its log there).
   - Click **Install**.
4. Launch:
   ```bash
   cd ~/Applications/qCS_3.0/application
   ./run_qCS.sh /Applications/MATLAB_R2023b.app
   ```
5. Inside qCS, on the **Netlist** tab, set *Simulator Choice* to
   **JoSIM** (JSIM and JSIM_n are not bundled on macOS).

### Linux

1. Create a folder in your own user space, then clone the linux branch inside that folder:
   ```bash
   git clone --single-branch --branch linux --depth 1 https://github.com/Akulababu/qCS_3.1.git
   cd qCS_3.1
   ```
2. Mark executable and run:
   ```bash
   chmod +x qCS_3.2_installer_glnxa64.install
   ./qCS_3.2_installer_glnxa64.install
   ```
3. In the wizard:
   - **License** → Accept.
   - **MATLAB Runtime** → "Use existing", point at your R2023b
     install (e.g. `/usr/local/MATLAB/R2023b`), or pick download mode.
   - **Install path** → a user-writable path, e.g. `~/qCS_3.2`.
   - Click **Install**.
4. Launch:
   ```bash
   cd <install-path>
   ./run_qCS.sh <path-to-MATLAB-R2023b>
   ```

### Windows

1. Create a folder in your own user space, then clone the `windows` branch (PowerShell or Git Bash):
   ```powershell
   git clone --single-branch --branch windows --depth 1 https://github.com/Akulababu/qCS_3.1.git
   cd qCS_3.1
   ```
2. Run the installer (or double-click the `.exe`):
   ```powershell
   .\qCS_3.2_installer_win64.exe
   ```
3. In the wizard:
   - **License** → Accept.
   - **MATLAB Runtime** → "Use existing", point at your R2023b
     install (e.g. `C:\MATLAB`), or pick download mode.
   - **Install path** → a user-writable path under
     `C:\Users\<user>\…`. Do not pick a path needing admin.
   - Click **Install**.
4. Launch:
   ```powershell
   cd <install-path>\application
   .\qCS.exe
   ```
