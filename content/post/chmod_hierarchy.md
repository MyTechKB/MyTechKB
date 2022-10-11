---
title: "chmod Hierarchy"
date: 2021-12-13T00:08:33-06:00
draft: false
category: Snippits
tags:
- Linux
- CLI
---

## Linux - Problem:
How to set chmod for a folder and all of its subfolders and files in Linux Ubuntu Terminal ?

## Linux - Solution 1:
chmod -R 755 will set this as permissions to all files and folders in the tree. You can use the find command. For example:
{{< highlight bash >}}
# To change all the directories to 755 (drwxr-xr-x):
find /opt/lampp/htdocs -type d -exec chmod 755 {} \;

# To change all the files to 644 (-rw-r--r--):
find /opt/lampp/htdocs -type f -exec chmod 644 {} \;
{{< / highlight >}}

## Linux - Solution 2:
Check the -R option
{{< highlight bash >}}
# chmod -R <permissionsettings> <dirname>
chmod -R 755 /folder
{{< / highlight >}}

## Linux - Solution 3:
If you want to set permissions on all files to a+r, and all directories to a+x, and do that recursively through the complete subdirectory tree, use:
{{< highlight bash >}}
chmod -R a+rX *
{{< / highlight >}}
The X (that is capital X, not small x!) is ignored for files (unless they are executable for someone already) but is used for directories.

## Linux - Solution 4:
{{< highlight bash >}}
chmod 755 $(find /path/to/base/dir -type d)
chmod 644 $(find /path/to/base/dir -type f)
{{< / highlight >}}

## Linux - Solution 5:
Here's another way to set directories to 775 and files to 664.

{{< highlight bash >}}
find /opt/lampp/htdocs \
\( -type f -exec chmod ug+rw,o+r {} \; \) , \
\( -type d -exec chmod ug+rwxs,o+rx {} \; \)
{{< / highlight >}}

It may look long, but it's pretty cool for three reasons:
 - Scans through the file system only once rather than twice.
 - Provides better control over how files are handled vs. how directories are handled. This is useful when working with special modes such as the sticky bit, which you probably want to apply to directories but not files.
 - Uses a technique straight out of the man pages:

{{< highlight bash >}}
find / \
\( -perm -4000 -fprintf /root/suid.txt %#m %u %p\n \) , \
\( -size +100M -fprintf /root/big.txt %-10s %p\n \)

# Traverse the filesystem just once, listing setuid files and  direc‐
# tories into /root/suid.txt and large files into /root/big.txt.
{{< / highlight >}}
