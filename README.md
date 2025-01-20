# Lenovo Legion Advanced BIOS SREP Configuration

> [!WARNING]
> The Advanced BIOS menu can brick your system, **use at your own risk**

The files in here are precisely what got me into Advanced BIOS when booting from a usb containing
these files on it specifically (which I just copy-pasted from my Linux environment, should work that
way from Windows as well).

Some files may be redundant or unnecessary, but this produced the advanced BIOS menu in the UEFI
exactly as intended and without doubling the "Advanced" menu item in "More Settings" or rendering an
unusable UI as other SREP configurations/bundles did. If you know that some elements contained here
are suboptimal or unnecessary, feel free to submit pull requests or even just drop an issue
informing me of such and I will happily modify the files and build the resulting image accordingly.

> [!NOTE]
> For a bootable ISO you can burn in whatever way you do that (I use Linux and am competent with the terminal so I use `dd if=/dev/sdX of=/path/to/iso.iso` to burn ISOs to flashdrives, try balena-etcher or rufus if you are not comfortable with such) [check the releases](https://github.com/Thomashighbaugh/Lenovo-Legion-Advanced-Bios/releases/tag/v0.0.1)

Tested On: - Lenovo Legion Pro 5 16irx9
