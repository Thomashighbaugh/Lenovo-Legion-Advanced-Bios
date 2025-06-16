# Lenovo Legion Advanced BIOS SREP Configuration

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
> Your system must have secure boot (and trusted platform) turned off in BIOS order to boot from an ISO
> For a bootable ISO you can burn in whatever way you do that (I use Linux and am competent with the terminal so I use `dd if=/dev/sdX of=/path/to/iso.iso` to burn ISOs to flashdrives, try balena-etcher or rufus if you are not comfortable with such) [check the releases](https://github.com/Thomashighbaugh/Lenovo-Legion-Advanced-Bios/releases/tag/v0.0.1)


## Tested Successfully On:

| Model                              | CPU        | GPU      | BIOS Version  |
| ---------------------------------- | ---------- | -------- | ------------- |
| Lenovo Legion Pro 5 16irx9         | i9-14900HX | RTX4070  | BIOS N0CN29WW |
| Lenovo Legion Pro 7 16IRX9H        |            |          | BIOS KWCN48WW |
| Lenovo Legion Pro 7i Gen 8 16IRX8H |            |          | BIOS KWCN48WW |
| Lenovo Legion 5 15ARH05H           | R7 4800H   | RTX 2060 | BIOS FSCN28WW |
| Lenovo IdeaPad Pro 5               | 185H       | RTX 4050 | BIOS MECN67WW |
| Lenovo IdeaPad s145                |            |          |               | 
| Lenovo LoQ                         |            |          | BIOS Q8CN12WW |
| Lenovo Legion Slim 5 14APH8        |            | RTX 4050 | BIOS MACN33WW |
| Lenovo IdeaPad Pro 5               | 185H       | RTX 4050 | BIOS MECN67WW |
| Lenovo Slim 14 14IRP8              | 13900H     | RTX 4060 |               |
| Lenovo Legion 5 15ARH05H           | R7 4800H   | RTX 2060 | BIOS FSCN28WW |






## Tested Unsuccessfully On:


> [!WARNING]
> If your model is listed below, then it is probably a bad idea to try it on your machine 

| Model | CPU | GPU | BIOS Version |
|-------|-----|-----|--------------|
| Legion pro 5 82WM 16arx8 | | | |

**If these settings work on your model, drop an issue so I can add them to the README for others with your model to know they worked (or didn't work).** Working through your debugging process or even relaying what experiences you have with undervolting using Advanced BIOS vis-a-vis SREP here is also welcome and will likely be extremely useful to others running into issues in the future so feel free to fill the issues up with anything related to this process so the community can benefit... and so can you if you are like me and would otherwise forget. 

### A huge thank you to those that have already confirmed their model works!
