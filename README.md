# linux-file-permissions-project
A project-based guide to securing a Linux environment by managing file and directory permissions. This repository demonstrates how to use the chmod command to modify access rights (read, write, execute) for users and groups, ensuring that files and directories are protected according to specific security requirements.
## Check file and directory details
In the `/home/researcher2/projects` directory, there are five files with the following names and permissions:

*   **project_k.txt**
    *   User = read, write
    *   Group = read, write
    *   Other = read, write

*   **project_m.txt**
    *   User = read, write
    *   Group = read
    *   Other = none

*   **project_r.txt**
    *   User = read, write
    *   Group = read, write
    *   Other = read

*   **project_t.txt**
    *   User = read, write
    *   Group = read, write
    *   Other = read

*   **._project_x.txt**
    *   User = read, write
    *   Group = write
    *   Other = none

There is also one subdirectory inside the `projects` directory named `drafts`. The permissions on `drafts` are:
*   User = read, write, execute
*   Group = execute
*   Other = none

## Understanding the Permission String

The permissions for each file are represented by a 10-character string, such as `-rw-rw-rw-` for `project_k.txt`. Here is how to interpret it:

*   **Character 1: File Type**
    *   A `-` indicates a regular file.
    *   A `d` indicates a directory.

*   **Characters 2-4: User (Owner) Permissions**
    *   These three characters represent the permissions for the file's owner.
    *   `r`: Read permission.
    *   `w`: Write permission.
    *   `x`: Execute permission.
    *   A `-` means the permission is not granted.

*   **Characters 5-7: Group Permissions**
    *   These three characters represent the permissions for the group associated with the file. They follow the same `r`, `w`, `x` format.

*   **Characters 8-10: Other Permissions**
    *   These final three characters represent the permissions for all other users on the system (not the owner or a member of the group). They also follow the same `r`, `w`, `x` format.

## Change file permissions
By using the `chmod` command you are able to change the permissions to each file.

`chmod o-w project_k.txt`

## Change file permissions on a hidden file
To see a hidden file the `ls -a` command is used. The file `._project_x.txt` is a hidden file that has been archived and should not be written to by anyone. (The user and group should still be able to read this file.). The `chmod` command is then used to change the permission.

`chmod u-w,g-w,o+r ._project_x.txt`

## Change directory permissions
To change the permissions to the `drafts` directory the `chmod` command is used to only allow the `researcher2` user to enter this directory.

`chmod g-x,o-x drafts`

## Summary
By checking the permissions given to each file and directory we noticed not all permissions were authorised. By looking at the companies needs we adjusted the permissions to each file and even made sure to give the minimum amount of access to files and directory to avoid any security risks.
