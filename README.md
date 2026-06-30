# Lenovo Legion Advanced BIOS SREP Configuration

> [!CAUTION]
> ## Lenovo Has Patched This Out
> Starting with certain BIOS versions, Lenovo has patched the SREP exploit that this tool relies on. For the **Legion Pro 5 16IRX9 (83DF)**, the patch was introduced in BIOS version **N0CN32WW** and later. If you are on N0CN32WW or newer, this tool will not work — the SREP loader runs successfully but the byte patterns no longer match, so the Advanced BIOS menu will not appear.
>
> I was running an older BIOS myself, but issues with excessive VRM heat and the IC chipset temperature sensor forced me to update. I will **continue to maintain this project** regardless — adding new models as they roll in while this method still works, and until another, easier method comes along.

> [!WARNING]
> The Advanced BIOS menu can brick your system, **use at your own risk**
> If you choose to ignore the warnings and brick your machine, **it is your responsibility not mine**.

The files in here are precisely what got me into Advanced BIOS when booting from a usb containing
these files on it specifically (which I just copy-pasted from my Linux environment, should work that
way from Windows as well).

Some files may be redundant or unnecessary, but this produced the advanced BIOS menu in the UEFI
exactly as intended and without doubling the "Advanced" menu item in "More Settings" or rendering an
unusable UI as other SREP configurations/bundles did. If you know that some elements contained here
are suboptimal or unnecessary, feel free to submit pull requests or even just drop an issue
informing me of such and I will happily modify the files and build the resulting image accordingly.

> [!NOTE]
> If you want to understand exactly how SREP works under the hood — what it does, why it works on some BIOS versions and not others, and why this isn't a permanent fix — [skip to the full technical explanation](#how-srep-works--a-complete-technical-explanation).
>
> Your system must have **secure boot (and trusted platform)** turned off in BIOS order to boot from an ISO
> 
> For a bootable ISO you can burn in whatever way you do that (I use Linux and am competent with the terminal so I use `dd if=/path/to/iso.iso of=/dev/sdX bs=4M status=progress` to write ISOs to flashdrives — note the `if=` is the **input file** (the ISO) and `of=` is the **output device** (your USB drive), not the other way around. Try balena-etcher or rufus if you are not comfortable with such) [check the releases](https://github.com/Thomashighbaugh/Lenovo-Legion-Advanced-Bios/releases/tag/v0.0.1)
>
> **UEFI folder naming:** If the ISO doesn't boot, make sure the folder under `EFI/` is named **`BOOT`** (all caps), not `Boot`. Some firmware is case-sensitive about this path. See [Issue #45](https://github.com/Thomashighbaugh/Lenovo-Legion-Advanced-Bios/issues/45) for details.

## Tested Successfully On:

| Model                              | CPU          | GPU        | BIOS Version(s)  |
| ---------------------------------- | ------------ | ---------- | ---------------- |
| Lenovo Legion Pro 5 16irx9         | i9-14900HX   | RTX 4070   | N0CN29WW, N0CN31WW |
| Lenovo Legion Pro 7 16IRX9H        |              |            | KWCN48WW         |
| Lenovo Legion Pro 7i 16IRX9H       |              |            | N2CN27WW         |
| Lenovo Legion Pro 7i Gen 8 16IRX8H | i9-13900HX   | RTX 4080   | KWCN48WW, KWCN50WW |
| Lenovo Legion 5 15ARH05H           | R7 4800H     | RTX 2060   | FSCN28WW         |
| Lenovo Legion 5 15ARH05            | R5 4600H     |            |                  |
| Lenovo Legion 5 15ACH6H           | R7 5800H     | RTX 3060   | GKCN65WW         |
| Lenovo Legion 18IAX10             | 275HX        | RTX 5090   | RZCN32WW         |
| Lenovo IdeaPad Pro 5               | 185H         | RTX 4050   | MECN67WW         |
| Lenovo IdeaPad s145                |              |            |                  | 
| Lenovo LoQ 15IAX9e                 |              |            | Q8CN12WW, Q8CN13WW, Q8CN17WW |
| Lenovo Legion Slim 5 14APH8        | R7 7840HS    | RTX 4050/4060 | MACN23WW, MACN24WW, MACN33WW |
| Lenovo Slim 14 14IRP8              | 13900H       | RTX 4060   |                  |
| Lenovo ThinkBook 16p G5 IRX        |              |            | P5CN28WW         |
| Lenovo Legion Pro 5i 16irx9        | i7-14650HX   | RTX 4060   | N0CN24WW         |
| Lenovo Legion S7 16ARHA7           | R9 6900HX    | Radeon 6800S | KFCN40WW        |
| Lenovo Legion 5 15ITH6H            |              |              |                  |
| Lenovo Legion 5 15IRX10 (83LY)     |              |              | QNCN33WW         |
| Lenovo Legion 5 Pro 16ACH6H (82JQ)  | R7 5800H     | RTX 3060     | GKCN65WW         |






## Tested Unsuccessfully On:

> [!WARNING]
> If your model is listed below, then it is probably a bad idea to try it on your machine 

| Model | CPU | GPU | BIOS Version | Notes |
|-------|-----|-----|--------------|-------|
| Legion Pro 5 16IRX9 (83DF) | i9-14900HX | RTX 4070 | N0CN32WW+ | Patched by Lenovo — SREP runs but byte patterns no longer match |
| Legion Pro 5 16IRX8 | i7-13700HX | | KWCN54WW | All 4 byte-pattern patches failed with "No Pattern Found" |
| Legion T5 26AMR5 | | | 04MKT2EA | Doesn't appear in boot menu |
| LOQ 15IAX9E | | | Q8CN21WW+ | Works on Q8CN17WW but not Q8CN21WW |
| Legion 18IAX10 | 275HX | RTX 5090 | 40WW, 43WW, 48WW | Only RZCN32WW works |
| Legion Pro 5 82WM 16ARX8 | | | | |
| Legion Pro 7i 16IRX9H | | | N2CN27WW | Works on N2CN27WW, broken on N2CN28WW+ |
| Legion Pro 7i 16IAX10H | | | Q7CN38WW | Booted into stock BIOS, no advanced features |
| LOQ 15ARP9 | R7 7435HS | | PQCN25WW | Doesn't work |
| Legion Pro 5 16ADR10 / R7000P 16ADR10 | | | RLCN31WW | Doesn't work |

**If these settings work on your model, drop an issue so I can add them to the README for others with your model to know they worked (or didn't work).** Working through your debugging process or even relaying what experiences you have with undervolting using Advanced BIOS vis-a-vis SREP here is also welcome and will likely be extremely useful to others running into issues in the future so feel free to fill the issues up with anything related to this process so the community can benefit... and so can you if you are like me and would otherwise forget. 

## How SREP Works — A Complete Technical Explanation

If you have no idea what BIOS, UEFI, or SREP are, start here. This is the full breakdown from the ground up.

### What Is BIOS / UEFI?

Every computer has a small piece of software stored on a flash memory chip on the motherboard. This is the **BIOS** (Basic Input/Output System) or, on modern machines, **UEFI** (Unified Extensible Firmware Interface) — they serve the same purpose but UEFI is the newer, more capable standard. When you press the power button, this is the very first code that runs. It initializes your hardware (CPU, RAM, storage, GPU), runs a quick self-test, and then hands control over to your operating system's bootloader (Windows Boot Manager, GRUB, systemd-boot, etc.).

The UEFI firmware has a **settings menu** — the one you get into by spamming F2, Fn+F2, or Del at startup. That menu is generated by a UEFI application called the **Setup Utility**. It reads configuration variables stored in NVRAM (non-volatile RAM — memory that persists when the computer is off) and presents them as a graphical interface with categories like "Main," "Advanced," "Security," "Boot," etc.

### The "Advanced" Menu and Why It's Hidden

Lenovo, like most OEMs, ships their laptops with a **stock Setup Utility** that only exposes a subset of all available UEFI configuration variables. The "Advanced" menu — which contains settings for CPU voltage offsets, memory timings, power delivery limits, VRM configuration, and other low-level tuning options — is **compiled into the firmware binary but deliberately hidden from the user interface**. The menu items, their labels, their help strings, and the code that renders them are all present in the firmware image. They are simply never linked into the menu tree that the Setup Utility displays.

Why hide them? Because changing these settings can cause instability, overheating, or permanent hardware damage. Lenovo's support team doesn't want to field calls from users who set their CPU voltage too low and now their laptop won't boot. So the Advanced menu is locked away — accessible only to the factory for validation and to a handful of enthusiasts who know how to unlock it.

### What Is SREP?

**SREP** stands for **Setup Routine Extra Path** (or sometimes "Setup Routine Extra Protocol" — the exact expansion varies by source). It is a UEFI DXE driver (DXE = Driver Execution Environment, the phase of UEFI boot where most hardware drivers and system services are loaded) that was originally developed by Insyde Software, one of the major UEFI firmware vendors. Lenovo, along with many other OEMs, licenses Insyde's UEFI framework and customizes it for their hardware.

SREP is a **debug and manufacturing tool** — it is not meant for end users. It is used on the factory floor to access every possible UEFI setting for calibration, testing, and validation. It works by **patching the Setup Utility at runtime** to re-enable the hidden menu entries.

### How SREP Works, Step by Step

Here is the exact chain of events when you boot the SREP ISO:

#### Step 1: The Boot Process

You insert a USB drive with the SREP ISO and boot from it. The UEFI firmware loads the ISO's bootloader (typically GRUB or a simple EFI application), which in turn loads the SREP DXE driver into memory. This driver is a `.efi` file — a standard UEFI executable, the same format as the operating system's bootloader.

#### Step 2: SREP Finds the Setup Utility

The UEFI firmware loads many DXE drivers during boot. One of them is the **Setup Utility** — the application that draws the BIOS settings menu. This utility is stored as a UEFI firmware volume (a section of the firmware image that contains executable code and data). SREP's job is to find this utility in memory and modify it.

SREP locates the Setup Utility by scanning memory for **known byte patterns** — specific sequences of bytes that are unique to the Setup Utility's code. These patterns are like fingerprints. The SREP configuration files in this repository contain four such patterns (you can see them in the SREP log output as long hexadecimal strings like `59B963B8C60E334099C18FD89F04022200000000`). Each pattern targets a specific location in the Setup Utility's binary code.

#### Step 3: SREP Patches the Bytecode

Once SREP finds the Setup Utility in memory, it **overwrites specific bytes** at the locations identified by the patterns. This is called **patching**. The patches do two things:

1. **Unhide the Advanced menu**: The Setup Utility builds its menu tree by iterating over a list of form IDs. Each form (a screen in the BIOS menu) has a flag that controls whether it is visible. The Advanced menu's form has its visibility flag set to `hidden`. SREP patches the bytecode that checks this flag, effectively changing the conditional jump from "skip this form" to "show this form."

2. **Unhide individual settings**: Even within visible forms, individual settings (like "CPU Overclocking" or "Memory Configuration") can have their own visibility flags. SREP patches these too, so that every possible setting is exposed.

The patches are **byte-level** — they change a few bytes of machine code in the Setup Utility's binary. For example, a `jz` (jump if zero) instruction that skips the Advanced menu might be changed to `jmp` (unconditional jump) or `nop` (no operation), effectively removing the conditional check.

#### Step 4: SREP Hands Control to the Patched Utility

After patching, SREP launches the modified Setup Utility. Because the patches were applied to the in-memory copy of the utility (not to the firmware flash chip), they are **temporary** — they only last for this boot session. When you reboot, the firmware loads the original, unpatched Setup Utility from flash, and the Advanced menu is hidden again.

The patched utility then draws the BIOS settings menu with all previously hidden options now visible. You can navigate to the "Advanced" menu (or "More Settings" on some Lenovo models) and find options like:

- **Overclocking / Underclocking** — CPU core voltage offset, cache voltage, etc.
- **Power & Thermal** — PL1/PL2 power limits, turbo power limits, VRM current limits
- **Memory Configuration** — XMP profiles, memory timing overrides
- **CPU Configuration** — Hyper-Threading, VT-d, C-states, SpeedStep
- **Graphics Configuration** — iGPU memory allocation, multi-monitor options

### Why Newer BIOS Versions Break SREP

When Lenovo releases a BIOS update, they recompile the firmware image. This can change the bytecode of the Setup Utility — the compiler may inline different functions, reorder instructions, or use different register allocations. The **byte patterns** that SREP uses to find the patch locations are specific to a particular build of the Setup Utility. If the binary changes even slightly, the patterns no longer match, and SREP cannot find the locations to patch.

Starting with BIOS version **N0CN32WW** (for the Legion Pro 5 16IRX9 / 83DF), Lenovo appears to have deliberately recompiled the Setup Utility in a way that invalidates the known SREP patterns. Whether this was an intentional anti-tamper measure or a side effect of other changes is unclear, but the result is the same: SREP loads successfully, scans memory, finds no matching patterns, and exits without patching anything. The Advanced menu remains hidden.

### Why This Is Not a Permanent Fix

SREP is a **binary patching** approach — it works by exploiting the fact that the hidden menu code is still present in the firmware. If Lenovo were to remove the hidden menu code entirely from future firmware builds (rather than just hiding it), SREP would have nothing to patch. That would require a fundamentally different approach — perhaps modifying the firmware image itself before flashing it, or finding a different DXE driver that exposes the settings through a different mechanism.

For now, SREP works on BIOS versions where the byte patterns still match. This repository tracks which models and BIOS versions are confirmed working, and I will continue to update it as new information comes in from the community.
