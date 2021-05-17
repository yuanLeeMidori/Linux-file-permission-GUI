# Linux File Permission Console App

A tool to help you to view/edit your file permissions.

## How to get the tool locally?

1. `git clone https://github.com/yuanLeeMidori/Linux-file-permission-console-app.git`
2. `cd` to the `Linux-file-permission-console-app` directory
3.  Add execute permission to the `script` file (e.g. `chmod u+e script`)

## How to *use* the tool?

The tool tells you the permission and other information about directories.

By default, without inputting any argument, the tool will check the current directory (`PWD`). Not just the current directory, the tool will check all parent directories and prints out their file permission as well.

You can also input the wanted directory file path as the argument. If the input argument is *not a directory*, you'll see the error message.

```bash
# argument is not a valid directory file path
$ ./permission-tool /this/is/not/a/directory/path
$ /this/is/not/a/directory/path is not a valid directory name
```

By inputting more than one argument, you'll also get the error message.

```bash
# wrong argument number
$ ./permission-tool arg1 arg2
$ Usage: permission-tool [ dir-name ]   
```

If the input number is correct, and the input value is valid, you'll see a list of permissions of each layer of directory.

```bash
$ ./permission-tool /home/Documents/Projects/Bash-Practice
                
Owner   Group   Other   Filename
-----   -----   -----   --------
r w x   r - x   r - x   /

r w x   r - x   r - x   home

r w x   r w x   r - x   Document

r w x   r - x   r - x   Projects

r w x   r w x   r - x   Bash-Practice
  Links: 3  Owner: yuanLeeMidori  Group: yuanLeeMidori  Size: 4096  Modified: May 16 21:16








Valid keys: k (up), j (down) : move between filenames
            h (left), l (right): move between permissions
            r, w, x, -: change permissions;   q: quit
```

You can use the keys to move the cursor up, down, left, and right. The additional information (such as link, size, modified date) will only be appeared when the cursor moves to the line of the directory.

By **default**, the cursor will be on the first character of the file name of the last layer of directories (which is the current directory, or the input directory)

When the cursor is on the permission character (r, w, x, or -), you can change the permission by using the keys `r`, `w`, `x`, or `-`. For example, to remove the permission, you can move the cursor to the first `r` of the `Bash-Practice` directory, you can use `-` to remove the owner's read permission. If you're allowed to change this file permission, the character will be changed (in this example, it'll be `-` instead of `r`); however, if the operation is denied, you'll see the permission character remain the same (which is still `r` after you use the `-` key).

To grant the permission, for example, you move the cursor to the `-` in the line of `Bash-Practice`, and use `w` key to add the write permission to the directory.

## Contribute

Coming soon!
