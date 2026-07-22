# qCS 3.1

Installers are split across three branches — one per platform — so
each user only downloads the installer for their own OS.

| Platform | Branch | File |
|---|---|---|
| macOS (Apple Silicon) | [`mac`](../../tree/mac) | `qCS_3.0_installer_maca64.app/` (3.0 build — no 3.1 macOS build yet) |
| Linux (x86_64) | [`linux`](../../tree/linux) | `qCS_3.1_installer_glnxa64.install` |
| Windows (x86_64) | [`windows`](../../tree/windows) | `qCS_3.1_installer_win64.exe` |

User manual: [qCS_3.1_Manual.pdf](qCS_3.1_Manual.pdf).

---

## Download the installer for your OS

Each branch is an orphan branch holding a single installer. Use
`--single-branch` so only that one file is pulled.

### macOS

The macOS branch still ships the 3.0 build (a 3.1 macOS build has not
been produced yet).

1. Create a folder in your own user space, then clone the mac branch inside that folder:
   ```bash
   git clone --single-branch --branch mac --depth 1 https://github.com/Akulababu/qCS_3.0.git
   cd qCS_3.0
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
   git clone --single-branch --branch linux --depth 1 https://github.com/Akulababu/qCS_3.0.git
   cd qCS_3.0
   ```
2. Mark executable and run:
   ```bash
   chmod +x qCS_3.1_installer_glnxa64.install
   ./qCS_3.1_installer_glnxa64.install
   ```
3. In the wizard:
   - **License** → Accept.
   - **MATLAB Runtime** → "Use existing", point at your R2023b
     install (e.g. `/usr/local/MATLAB/R2023b`), or pick download mode.
   - **Install path** → a user-writable path, e.g. `~/qCS_3.1`.
   - Click **Install**.
4. Launch:
   ```bash
   cd <install-path>
   ./run_qCS.sh <path-to-MATLAB-R2023b>
   ```

### Windows

1. Create a folder in your own user space, then clone the `windows` branch (PowerShell or Git Bash):
   ```powershell
   git clone --single-branch --branch windows --depth 1 https://github.com/Akulababu/qCS_3.0.git
   cd qCS_3.0
   ```
2. Run the installer (or double-click the `.exe`):
   ```powershell
   .\qCS_3.1_installer_win64.exe
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
