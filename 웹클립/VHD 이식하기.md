## Boot to a virtual hard disk: Add a VHDX or VHD to the boot menu
## In this article

1.  [Prerequisites](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#prerequisites)
2.  [Step 1: Create a VHDX from diskpart](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#step-1-create-a-vhdx-from-diskpart)
3.  [Step 2: Apply a Windows image to the VHD](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#step-2-apply-a-windows-image-to-the-vhd)
4.  [Step 3: Detach the VHD, copy it to a new device, and attach it (optional)](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#step-3-detach-the-vhd-copy-it-to-a-new-device-and-attach-it-optional)
5.  [Step 4: Add a boot entry](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#step-4-add-a-boot-entry)
6.  [Related topics](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#related-topics)

Native Boot allows you to create a virtual hard disk (VHDX), install Windows to it, and then boot it up, either on your PC side-by-side with your existing installation, or on a new device.

A native-boot VHDX can be used as the running operating system on designated hardware without any other parent operating system. This differs from a scenario where a VHDX is connected to a virtual machine on a computer that has a parent operating system.

Native boot for Windows 10 or later requires the **.vhdx** format, not the .vhd format.

VHDXs can be applied to PCs or devices that have no other installations of Windows, without a virtual machine or hypervisor. (A hypervisor is a layer of software under the operating system that runs virtual computers.) This enables greater flexibility in workload distribution because a single set of tools can be used to manage images for virtual machines and designated hardware.

You can also deploy the VHDX to a PC that already has Windows installed on it, and use a boot menu to select between the existing version of Windows, or the version on the VHD.

To learn more about using VHDXs in an enterprise environment, see [Understanding Virtual Hard Disks with Native Boot](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/deploy-windows-on-a-vhd--native-boot?view=windows-11).

## Prerequisites

-   A technician PC with the Windows Assessment and Deployment Kit (Windows ADK) tools installed on it.
-   A generalized Windows image (.WIM file). To learn more, see [Sysprep (Generalize) a Windows installation](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/sysprep--generalize--a-windows-installation?view=windows-11).
-   A bootable Windows PE drive. To learn more, see [WinPE: Create USB Bootable drive](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive?view=windows-11).
-   A destination PC or device on which to install the VHDX. This device requires 30 gigabytes (GB) or more of free disk space. You can install the VHDX to a device already running other operating system installations, or as the only operating system on a device.

## Step 1: Create a VHDX from diskpart

On the technician PC:

1.  From the Command Prompt, open Diskpart.
    
    ```
    diskpart
    ```
    
2.  Create and prepare a new VHDX. In this example, we create a 25 GB fixed-type VHDX.
    
    ```
    create vdisk file=C:\windows.vhdx maximum=25600 type=fixed
    ```
    
3.  Attach the VHDX. This adds the VHDX as a disk to the storage controller on the host.
    
    ```
    attach vdisk
    ```
    
4.  Create a partition for the Windows files, format it, and assign it a drive letter. This drive letter will appear in File Explorer.
    
    ```
    create partition primary
    format quick label=vhdx
    assign letter=v
    ```
    
5.  Exit Diskpart
    
    ```
    exit
    ```
    

## Step 2: Apply a Windows image to the VHD

On your technician PC, apply a generalized Windows image to the primary partition of the VHDX that you created and attached in [Step 1](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#step-1-create-a-vhdx-from-diskpart).

```
Dism /Apply-Image /ImageFile:install.wim /index:1 /ApplyDir:V:\
```

## Step 3: Detach the VHD, copy it to a new device, and attach it (optional)

You can deploy the VHDX to a device that already has a copy of Windows installed on it, or you can clean and prepare the destination PC's hard drive to use the VHD.

1.  Use diskpart to detach the virtual disk from your technician PC.
    
    ```
    diskpart
    select vdisk file=C:\windows.vhdx
    detach vdisk
    exit
    ```
    
2.  Copy the VHDX to a network share or removable storage drive. The following maps a drive letter to a network share, creates a directory for the VHD, and then copies the VHD.
    
    ```
    net use n: \\server\share\
    md N:\VHDs
    copy C:\windows.VHDX n:\VHDs\
    ```
    

### Clean and prepare a new device for native boot

On your destination PC:

1.  Use your bootable WinPE key to [boot the destination PC to WinPE](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/boot-to-uefi-mode-or-legacy-bios-mode?view=windows-11).
    
2.  Clean and prepare the destination PC's hard drive. Create a system partition (S), and a main partition (M) where the VHDX will be stored.
    
    **UEFI**:
    
    ```
    diskpart
    select disk 0
    clean
    convert gpt
    rem == 1. System partition =========================
    create partition efi size=100
    format quick fs=fat32 label="System"
    assign letter="S"
    rem == 2. Microsoft Reserved (MSR) partition =======
    create partition msr size=128
    rem == 3. Main partition ===========================
    create partition primary 
    format quick fs=ntfs label="Main"
    assign letter="M"
    exit
    ```
    
    **BIOS**:
    
    ```
    diskpart
    select disk 0
    clean
    rem == 1. System partition ======================
    create partition primary size=100
    format quick fs=ntfs label="System"
    assign letter="S"
    active
    rem == 2. Main partition ========================
    create partition primary
    format quick fs=ntfs label="Main"
    assign letter="M"
    exit
    ```
    
3.  Connect to the network drive or storage location where you copied the VHDX in [step 3.2](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/_generated_background_page.html#step-3-detach-the-vhd-copy-it-to-a-new-device-and-attach-it-optional).
    
    ```
    net use N: \\server\share
    ```
    
4.  Copy the VHDX from the network drive or storage location to the destination PC's main partition.
    
    ```
    copy N:\VHDs\Windows.vhdx M:
    ```
    

### Attach the VHDX

1.  While still booted into WinPE, attach your VHDX to the destination PC.
    
    ```
    diskpart
    select vdisk file=M:\windows.vhdx
    attach vdisk
    ```
    
2.  Identify the attached VHDX's volume letter. (Optional: Change it to another letter that makes more sense, for example V, and leave the diskpart command line open for the next step).
    
    ```
    list volume
    select volume 3
    assign letter=v
    ```
    

## Step 4: Add a boot entry

1.  From your destination PC, open Diskpart (if necessary) and identify the drive letters of the VHDX and the system partition, for example, V and S.
    
    ```
    diskpart
    list volume
    exit
    ```
    
2.  Add a boot entry to the device. You can add multiple VHDX files using this method.
    
    **UEFI**:
    
    ```
    V:\
    cd v:\windows\system32
    bcdboot v:\windows /s S: /f UEFI
    ```
    
    **BIOS**:
    
    ```
    V:
    cd v:\windows\system32
    bcdboot v:\windows /s S: /f BIOS
    ```
    
3.  Remove the WinPE USB key.
    
4.  Restart the destination PC.
    
    If there's only one boot entry, the device immediately boots to Windows. If there's more than one boot entry, you'll see a boot menu where you can choose between the available versions of Windows on the device.
    

[Understanding Virtual Hard Disks with Native Boot](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/deploy-windows-on-a-vhd--native-boot?view=windows-11)

[BCDboot Command-Line Options](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di?view=windows-11)

---

## Additional resources

---

Documentation

-   [Deploy Windows with a VHDX (Native Boot)](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/deploy-windows-on-a-vhd--native-boot?source=recommendations)
    
    Deploy Windows with a VHDX (Native Boot)
    
-   [BCDBoot Command-Line Options](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di?source=recommendations)
    
    BCDBoot Command-Line Options
    
-   [UEFI/GPT-based hard drive partitions](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?source=recommendations)
    
    UEFI/GPT-based hard drive partitions
    
-   [Create an ISO image for UEFI platforms - Windows Server](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/troubleshoot/windows-server/deployment/create-iso-image-for-uefi-platforms?source=recommendations)
    
    Describes how to create an UEFI bootable Windows PE RAM Disk on a CD-ROM.
    
-   [BCDEdit Command-Line Options](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/bcdedit-command-line-options?source=recommendations)
    
    BCDEdit is a command-line tool for managing Boot Configuration Data (BCD).
    
-   [DISM Overview](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/what-is-dism?source=recommendations)
    
    DISM overview
    
-   [Windows Recovery Environment (Windows RE)](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference?source=recommendations)
    
    Windows Recovery Environment (Windows RE)
    
-   [BIOS/MBR-based hard drive partitions](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions?source=recommendations)
    
    BIOS/MBR-based hard drive partitions
    

## Additional resources

---

Documentation

-   [Deploy Windows with a VHDX (Native Boot)](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/deploy-windows-on-a-vhd--native-boot?source=recommendations)
    
    Deploy Windows with a VHDX (Native Boot)
    
-   [BCDBoot Command-Line Options](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di?source=recommendations)
    
    BCDBoot Command-Line Options
    
-   [UEFI/GPT-based hard drive partitions](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?source=recommendations)
    
    UEFI/GPT-based hard drive partitions
    
-   [Create an ISO image for UEFI platforms - Windows Server](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/troubleshoot/windows-server/deployment/create-iso-image-for-uefi-platforms?source=recommendations)
    
    Describes how to create an UEFI bootable Windows PE RAM Disk on a CD-ROM.
    
-   [BCDEdit Command-Line Options](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/bcdedit-command-line-options?source=recommendations)
    
    BCDEdit is a command-line tool for managing Boot Configuration Data (BCD).
    
-   [DISM Overview](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/what-is-dism?source=recommendations)
    
    DISM overview
    
-   [Windows Recovery Environment (Windows RE)](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference?source=recommendations)
    
    Windows Recovery Environment (Windows RE)
    
-   [BIOS/MBR-based hard drive partitions](chrome-extension://pcmpcfapbekmbjjkdalcgopdkipoggdi/en-us/windows-hardware/manufacture/desktop/configure-biosmbr-based-hard-drive-partitions?source=recommendations)
    
    BIOS/MBR-based hard drive partitions
