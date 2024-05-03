# Prepare a PDF Report

Prepare a PDF report by analyzing the provided disk images and answering the associated questions.

## Analysis/Resolution Description

Describe how you analyzed/resolved the situation and justify your answers for each one. List the tools/commands you used and how. Include screenshots if they can help clarify/support your findings.

## Tool Comparison

Use different tools and compare their results whenever possible, commenting on discrepancies.

## Verification

Before starting, verify the SHA256 hashes of the uncompressed images and contact us if they do not correspond to the ".sha256" files (you can use `sha256sum --check *.sha256` to check the three hashes).

## Image Format

All images are in RAW/dd format.

## Console Image Analysis (`console.dd`)

Something fishy is going on. Someone gave us this image of an unpartitioned FAT filesystem containing a JPEG picture. However, this volume seems to have just been (re)formatted to hide something.

### Task

Can you reconstruct the original partition scheme and recover the content of the original partition?

## Corrupted Image Analysis (`corrupted.dd`)

Is the image partitioned/bootable? If partitioned, list all partitions.

### File System Details

Inside, you'll find a FAT FS:

- what is the volume label?
- what is the sector size?
- what is the cluster size?
- how many FAT tables are present?
- are there sectors that are unused by the FS? If yes, what do they contain?

### File Recovery

How many files/deleted-files with extension TXT are there?
Can you read them by readonly-mounting them/by using TSK? Why?

### Specific File Identification

One of them should correspond to SHA256 e9207be4a1dde2c2f3efa3aeb9942858b6aaa65e82a9d69a8e6a71357eb2d03c
... which one?

### Corruption Analysis

If you cannot extract such content, something is corrupted (hint hint); find the root cause and fix the file system before continuing. You must explain how you found and fixed the problem.

### String Occurrences

Inside the file corrupted.dd there are some occurrences of the string "zxgio" (without quotes); can you list their offset in bytes?

For each occurrence of such a string, determine its location with respect to the FAT file system. For instance, is the string contained inside a file? Is it in some unused/slack space? In other areas?

## Strange Image Analysis (`strange.dd`)

What partition scheme has been used for this image?
Can you identify the file system type for each partition and extract the files that are contained?

### Anomaly Detection

What is so strange about this image?
