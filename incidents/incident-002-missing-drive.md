# Incident #002 — Missing Drive Letter

## Summary

A virtual storage volume was missing from Windows File Explorer.

The volume was present and healthy in Disk Management, but it did not have a drive letter assigned.

## Environment

- OS: Windows 11 ARM
- Virtualization: Parallels Desktop
- Host: MacBook Air M1
- Storage: 5 GB VHDX virtual disk
- File System: NTFS

## Reported Symptom

The user reported that the `IT-LAB-DISK` drive was no longer visible in "This PC".

## Troubleshooting Process

### 1. Checked Disk Management

The virtual disk was detected by Windows:

- Disk: Disk 1
- Status: Online
- Size: 5 GB
- Partition: Healthy
- File System: NTFS

The volume existed, but no drive letter was assigned.

### 2. Checked the volume using DiskPart

The following command was used:

```cmd
diskpart
list volume

## Evidence

Supporting screenshots:

- [Missing Drive](../evidence/incident-002/missing-drive.png)
- [Drive Restored](../evidence/incident-002/drive-restored.png)
