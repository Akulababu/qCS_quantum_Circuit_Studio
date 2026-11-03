# qCS: quantum Circuit Studio 3.2

Each platform has its own branch with one installer, so you only download the installer for your OS.

| Platform | Branch | File |
|---|---|---|
| macOS (Apple Silicon) | [`mac`](../../tree/mac) | `qCS_3.2_installer_maca64.app/` |
| Linux (x86_64) | [`linux`](../../tree/linux) | `qCS_3.2_installer_glnxa64.install` |
| Windows (x86_64) | [`windows`](../../tree/windows) | `qCS_3.2_installer_win64.exe` |

User manual: [qCS_3.2_Manual.pdf](qCS_3.2_Manual.pdf).

## What changed in 3.2

qCS 3.2 fixes bugs in 3.1.

- Element and node names now stay as written. 3.1 also removed letters such as H, F, OHM and DC from names, so `PATH_NODE` became `PAT_NODE`. That could break a netlist or quietly change the circuit.
- `>=N` pattern windows count events correctly, the check for extra events before TSTOP now runs, and margin, yield and optimization simulations keep the TSTOP you set.
- Pattern input is checked more strictly. Some patterns that 3.1 accepted are now rejected, and the error message says which rule they break.
- Negative Pulse, pulse height, pulse width and the expected band are shared by the Margin, Yield and Optimization tabs.
- Because of these fixes, margin, yield and optimization results can differ from 3.1.

## Download and install

Clone only the branch for your OS with `--single-branch`.

### macOS

The macOS installer is for Apple silicon Macs (M1 or later) on macOS 13 or later. There is no Intel Mac build. Before you install:

- Install Rosetta 2 with `softwareupdate --install-rosetta`. The bundled JoSIM binary is an Intel program.
- Stay online. The installer downloads MATLAB Runtime R2023b, about 2.2 GB.

1. In a folder you own, clone the `mac` branch:
   ```bash
   git clone --single-branch --branch mac --depth 1 https://github.com/Akulababu/qCS_quantum_Circuit_Studio.git
   cd qCS_quantum_Circuit_Studio
   ```
2. Run the installer:
   ```bash
   open qCS_3.2_installer_maca64.app
   ```
   The installer is not signed. If macOS blocks it, allow it under System Settings > Privacy & Security, or run `xattr -dr com.apple.quarantine qCS_3.2_installer_maca64.app` and open it again.
3. In the wizard, accept the license. Install to a folder you can write to whose path has no spaces, such as `~/Applications/qCS_3.2`. Do not use `/Applications/`, which needs admin rights. Then click Install.
4. Start qCS from Terminal, not by double-clicking it in Finder:
   ```bash
   cd ~/Applications/qCS_3.2/application
   ./run_qCS.sh <MATLAB-Runtime-R2023b-folder>
   ```
   Pass the folder where the installer put MATLAB Runtime R2023b. When it sits next to qCS, that is `~/Applications/qCS_3.2/R2023b`. If you have MATLAB R2023b installed, `/Applications/MATLAB_R2023b.app` also works. The first launch can take a few minutes.
5. On the Netlist tab, set Simulator Choice to JoSIM. JSIM and JSIM_n are not included on macOS.

### Linux

1. In a folder you own, clone the `linux` branch:
   ```bash
   git clone --single-branch --branch linux --depth 1 https://github.com/Akulababu/qCS_quantum_Circuit_Studio.git
   cd qCS_quantum_Circuit_Studio
   ```
2. Make the installer executable and run it:
   ```bash
   chmod +x qCS_3.2_installer_glnxa64.install
   ./qCS_3.2_installer_glnxa64.install
   ```
3. In the wizard, accept the license. For MATLAB Runtime, choose "Use existing" and point it at your R2023b install (for example `/usr/local/MATLAB/R2023b`), or choose the download option. Install to a folder you can write to, such as `~/qCS_3.2`, then click Install.
4. Launch qCS:
   ```bash
   cd <install-path>
   ./run_qCS.sh <path-to-MATLAB-R2023b>
   ```

### Windows

1. In a folder you own, clone the `windows` branch (PowerShell or Git Bash):
   ```powershell
   git clone --single-branch --branch windows --depth 1 https://github.com/Akulababu/qCS_quantum_Circuit_Studio.git
   cd qCS_quantum_Circuit_Studio
   ```
2. Run the installer, or double-click the `.exe`:
   ```powershell
   .\qCS_3.2_installer_win64.exe
   ```
3. In the wizard, accept the license. For MATLAB Runtime, choose "Use existing" and point it at your R2023b install (for example `C:\MATLAB`), or choose the download option. Install to a folder under `C:\Users\<user>\` that does not need admin rights, then click Install.
4. Launch qCS:
   ```powershell
   cd <install-path>\application
   .\qCS.exe
   ```
