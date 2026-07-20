<img width="1408" height="768" alt="Carb" src="https://github.com/user-attachments/assets/d2c91cbe-72b1-4942-8e54-eee82334ad4b" />

# Carb
🦀Carb – Open‑source Windows malware research tool. Demonstrates syscall hooking (`NtQuerySystemInformation`) for process hiding, thread explosion (10M threads), Argon2id hashing (100GB memory), GPU compute abuse, and peripheral disabling (mouse/audio/camera). Auto‑persists via Startup folder – never deploy without explicit consent.

## ⚙️ Features – Attack Vectors & Techniques

| **Feature** | **Implementation Technique** | **Impact** | **Research Purpose** |
| :--- | :--- | :--- | :--- |
| 🕵️ **Process Hiding** | Hooks `NtQuerySystemInformation` (syscall) – removes current PID from system process list | Invisible in Task Manager, Process Explorer, and most monitoring tools | Understand how malware evades user‑mode detection |
| ♻️ **Persistence** | Copies binary to `%APPDATA%\...\Startup` folder | Executes automatically on every Windows boot | Study common auto‑start persistence mechanisms |
| 💥 **CPU & RAM Exhaustion** | Spawns **10 million threads** (1MB stack each) + Argon2id hashing (`mem_cost=100GB`, `time=50`, `lanes=3667`) | Saturates all CPU cores; triggers massive pagefile thrashing; system becomes unresponsive | Analyze fork‑bomb logic and memory‑hardened hash abuse |
| 🎮 **GPU Stress** | Infinite loop dispatching compute shaders (WGSL) via `wgpu` | GPU utilization hits 100%; temperature spikes; graphical performance drops to zero | Measure GPU response under sustained compute load |
| 🖥️ **Peripheral Disable** | PowerShell: `Disable-PnpDevice` targeting mouse, audio, and camera drivers | Complete loss of input/control; user cannot interact with the system | Explore driver‑level disabling techniques |
| 🌑 **Screen Blackout** | `SetMonitorBrightness(0)` via Windows Monitor API | Screen goes completely dark (backlight remains on), causing visual denial‑of‑service | Examine low‑level monitor communication |
| ⌨️ **Keyboard Layout Hijack** | `LoadKeyboardLayoutW` + `ActivateKeyboardLayout` to force US English | Confuses user input; makes typing passwords or recovery commands difficult | Study input method manipulation |
| 🔪 **Process Killer** | PowerShell: `Get-Process \| Where-Object {$_.Id -ne $pid} \| Stop-Process -Force` | Terminates all other applications (including Explorer, Defender, Task Manager) | Analyze system takeover and defense disruption tactics |

---

> **📌 DISCLAIMER:** All features above are intentionally designed to **simulate real‑world malware behavior** for controlled testing environments. **Strictly FORBIDDEN** to use on production systems, unauthorized devices, or without explicit consent. Use only in isolated VMs or sandboxed labs. The author assumes **zero liability** for any misuse or damage.

 🦀
<img width="576" height="462" alt="burningyourmom" src="https://github.com/user-attachments/assets/60a548ae-7831-4db3-acae-5ed00a88d8a3" />
┌──────────────────┬───────────────┬──────────────────────┬─────────────┐
│ Resource         │ Usage         │ Bar                  │ Status      │
├──────────────────┼───────────────┼──────────────────────┼─────────────┤
│ CPU              │ 100%          │ ████████████████████ │ 🔴 MAX      │
│ RAM (Physical)   │ 15.8 / 16 GB  │ ████████████████████ │ 🔴 FULL     │ 
│ RAM (Pagefile)   │ 72.0 / 80 GB  │ ████████████████████ │ 🔴 CRIT     │
│ GPU              │ 98%           │ ████████████████████ │ 🟡 NEAR     │
│ Disk I/O         │ 100%          │ ████████████████████ │ 🔴 BUSY     │
└──────────────────┴───────────────┴──────────────────────┴─────────────┘
<h2 align="center">🔐 File Hashes – Carb.exe</h2>

<p align="center">
  <strong>Verify the integrity and authenticity</strong> of the binary using the following cryptographic checksums.
</p>

<table align="center">
  <thead>
    <tr>
      <th style="background-color: #2d2d2d; color: #ffffff; text-align: center;">Algorithm</th>
      <th style="background-color: #2d2d2d; color: #ffffff; text-align: center;">Hash (Lowercase)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><strong>MD5</strong></td>
      <td><code>d3eeec515c96cc5229fc4a1dc53eef7a</code></td>
    </tr>
    <tr style="background-color: #f6f8fa;">
      <td align="center"><strong>SHA-1</strong></td>
      <td><code>48b1bf84b31072f21a7ca57943911df11fd65e7a</code></td>
    </tr>
    <tr>
      <td align="center"><strong>SHA-256</strong></td>
      <td><code>26c4cfb4b689af68b71ff273c9eb11e15d6959f92317e1a19fdb84be08f2a41c</code></td>
    </tr>
  </tbody>
</table>

> 💡 **Tip:** Use `CertUtil -hashfile Carb.exe SHA256` (Windows) or `sha256sum Carb.exe` (Linux) to verify the hash locally.<h2 align="center">🔐 File Hashes – Carb.exe</h2>

<p align="center">
  <strong>Verify the integrity and authenticity</strong> of the binary using the following cryptographic checksums.
</p>

<table align="center">
  <thead>
    <tr>
      <th style="background-color: #2d2d2d; color: #ffffff; text-align: center;">Algorithm</th>
      <th style="background-color: #2d2d2d; color: #ffffff; text-align: center;">Hash (Lowercase)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><strong>MD5</strong></td>
      <td><code>d3eeec515c96cc5229fc4a1dc53eef7a</code></td>
    </tr>
    <tr style="background-color: #f6f8fa;">
      <td align="center"><strong>SHA-1</strong></td>
      <td><code>48b1bf84b31072f21a7ca57943911df11fd65e7a</code></td>
    </tr>
    <tr>
      <td align="center"><strong>SHA-256</strong></td>
      <td><code>26c4cfb4b689af68b71ff273c9eb11e15d6959f92317e1a19fdb84be08f2a41c</code></td>
    </tr>
  </tbody>
</table>

> 💡 **Tip:** Use `CertUtil -hashfile Carb.exe SHA256` (Windows) or `sha256sum Carb.exe` (Linux) to verify the hash locally.
