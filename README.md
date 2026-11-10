# qCS: quantum Circuit Studio 3.2

Each platform has its own branch with a single installer, so you download only the one for your operating system.

| Platform | Branch | File |
|---|---|---|
| macOS (Apple Silicon) | [`mac`](../../tree/mac) | `qCS_3.2_installer_maca64.app/` |
| Linux (x86_64) | [`linux`](../../tree/linux) | `qCS_3.2_installer_glnxa64.install` |
| Windows (x86_64) | [`windows`](../../tree/windows) | `qCS_3.2_installer_win64.exe` |

User manual: [qCS_3.2_Manual.pdf](qCS_3.2_Manual.pdf).

## What changed in 3.2

qCS 3.2 fixes bugs in 3.1.

- Element and node names now stay as written. 3.1 also removed letters such as H, F, OHM and DC from names, so `PATH_NODE` became `PAT_NODE`, which could break a netlist or silently change the circuit.
- `>=N` pattern windows count events correctly, the check for extra events before TSTOP now runs, and margin, yield and optimization simulations keep the TSTOP you set.
- Pattern input is checked more strictly. Some patterns that 3.1 accepted are now rejected, and the error message names the rule they break.
- The Margin, Yield and Optimization tabs share Negative Pulse, pulse height, pulse width and the expected band.
- Because of these fixes, margin, yield and optimization results can differ from 3.1.

## Before you install

qCS needs MATLAB R2023b or the free MATLAB Runtime R2023b (version 23.2). If you have neither, download MATLAB Runtime R2023b for your operating system from the MathWorks page and install it first:

https://www.mathworks.com/products/compiler/matlab-runtime.html

The Runtime installs to these folders by default:

- Windows: `C:\Program Files\MATLAB\MATLAB Runtime\R2023b`
- Linux: `/usr/local/MATLAB/MATLAB_Runtime/R2023b`
- macOS: `/Applications/MATLAB/MATLAB_Runtime/R2023b`

The qCS installer also needs an internet connection while it runs.

The installer suggests a folder named `qCS` under `C:\Program Files`, `/usr` or `/Applications`, which need administrator rights. The steps below keep the name `qCS` and put the folder in your home directory instead.

In the steps, `>` separates the clicks in the installation wizard: `[Button]` is a button, `(...)` is something you do, and the rest are options or fields.

## Download and install

Clone only the branch for your OS with `--single-branch`.

### macOS

The macOS installer is for Apple silicon Macs (M1 or later) on macOS 13 or later. There is no Intel Mac build. The bundled JoSIM is an Intel program, so install Rosetta 2 first:

```bash
softwareupdate --install-rosetta
```

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
3. In the wizard, accept the license, select MATLAB Runtime R2023b, and install qCS to a folder whose path has no spaces:
   - (accept the license) > MATLAB Runtime: Use existing MATLAB Runtime > (select `/Applications/MATLAB/MATLAB_Runtime/R2023b`) > installation folder: `~/Applications/qCS` > [Install]
4. Start qCS from Terminal, not by double-clicking it in Finder, and pass the Runtime folder:
   ```bash
   cd ~/Applications/qCS/application
   ./run_qCS.sh /Applications/MATLAB/MATLAB_Runtime/R2023b
   ```
   If you have MATLAB R2023b, you can pass `/Applications/MATLAB_R2023b.app` instead. The first start can take a few minutes.
5. Switch the simulator to JoSIM. JSIM and JSIM_n are not included on macOS.
   - Netlist tab > Simulator Choice: JoSIM

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
3. In the wizard, accept the license, select your MATLAB R2023b or MATLAB Runtime R2023b folder, and install qCS to your home directory:
   - (accept the license) > MATLAB Runtime: Use existing MATLAB Runtime > (select `/usr/local/MATLAB/MATLAB_Runtime/R2023b`, or a MATLAB R2023b folder such as `/usr/local/MATLAB/R2023b`) > installation folder: `~/qCS` > [Install]
4. Start qCS from the `application` folder and pass the same R2023b folder:
   ```bash
   cd ~/qCS/application
   ./run_qCS.sh /usr/local/MATLAB/MATLAB_Runtime/R2023b
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
3. In the wizard, accept the license, select MATLAB Runtime R2023b, and install qCS to a folder under `C:\Users\<user>\` that does not need administrator rights. An installed MATLAB Runtime R2023b is found automatically.
   - (accept the license) > MATLAB Runtime: Use existing MATLAB Runtime > (select your R2023b folder, for example `C:\Program Files\MATLAB\MATLAB Runtime\R2023b` or `C:\MATLAB`) > installation folder: `C:\Users\<user>\qCS` > [Install]
4. Start qCS from the `application` folder:
   ```powershell
   cd C:\Users\<user>\qCS\application
   .\qCS.exe
   ```
