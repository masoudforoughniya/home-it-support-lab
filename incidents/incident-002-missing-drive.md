# Incident #002 — Missing Drive Letter

## Summary

A virtual storage volume was missing from Windows File Explorer.

The volume was present and healthy in Disk Management, but it did not have a drive letter assigned.

## Environment

* OS: Windows 11 ARM
* Virtualization: Parallels Desktop
* Host: MacBook Air M1
* Storage: 5 GB VHDX virtual disk
* File System: NTFS

## Reported Symptom

The user reported that the `IT-LAB-DISK` drive was no longer visible in "This PC".

## Troubleshooting Process

### 1. Checked Disk Management

The virtual disk was detected by Windows:

* Disk: Disk 1
* Status: Online
* Size: 5 GB
* Partition: Healthy
* File System: NTFS

The volume existed, but no drive letter was assigned.

### 2. Checked the Volume Using DiskPart

The following commands were used:

```cmd
diskpart
list volume
```

The relevant volume appeared as:

```text
Volume 5    IT-LAB-DISK    NTFS    Partition    4982 MB    Healthy
```

The `Ltr` column was empty.

### 3. Verified Volume Health

The volume was selected and inspected using:

```cmd
select volume 5
detail volume
```

The volume was:

* Online
* Not hidden
* Not read-only
* Not offline
* Not BitLocker encrypted

The volume had approximately 4.9 GB of capacity and was mostly free.

### 4. Root Cause

The volume did not have a drive letter assigned.

This prevented Windows File Explorer from displaying the volume under "This PC".

## Resolution

The missing drive letter was restored using DiskPart:

```cmd
assign letter=E
```

Windows successfully assigned drive letter `E:` to the volume.

## Verification

The drive was verified using:

```cmd
dir E:\
```

The command confirmed that Windows could access the `E:` volume.

The file system was then verified using:

```cmd
fsutil fsinfo volumeinfo E:
```

The verification confirmed:

* Volume name: `IT-LAB-DISK`
* Drive letter: `E:`
* File system: `NTFS`
* Volume is read/write

The drive became visible again in "This PC".

## Final Status

**Resolved**

The storage volume was successfully restored without modifying or reinstalling the volume.

## Key Takeaways

* A missing drive in File Explorer does not necessarily mean the disk is faulty.
* Disk Management can be used to determine whether the volume exists and is healthy.
* DiskPart provides additional diagnostic information.
* A missing drive letter can make a healthy volume appear to be missing.
* Always verify the root cause before making changes.

## Skills Practiced

* Windows Disk Management
* DiskPart
* Storage troubleshooting
* NTFS
* Drive letter management
* Root cause analysis
* Windows command-line troubleshooting
* Technical documentation

## Evidence

Supporting screenshots:

* [Missing Drive](../evidence/incident-002/missing-drive.png)
* [Drive Restored](../evidence/incident-002/drive-restored.png)
