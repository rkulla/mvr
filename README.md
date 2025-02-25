# mvr

## Description
`mvr` is a command that allows you to move one or more files to its default temporary directory or to a specified destination and later restore them to their original locations. This is useful for temporarily removing files without permanently deleting them.

Think of the `mv` command if it also had the option to restore (mvr is meant to mean 'mv with restore').

It works by moving files from their original locations to either a default directory (`$HOME/tmp/mvr`) or a specified destination (If last argument is a directory, it treats it as the destination). It records the original file paths in a state file (`$HOME/tmp/mvr/mvr.txt`), and when run without arguments, it restores the files back to their original locations.

## Usage

### Move files to the default temporary directory:

```bash
mvr <file1> [file2 ...]
```
Example:
```bash
mvr foo/file.txt bar/file2.txt
```
Output:
```
Moved 'file.txt' to '/home/user/tmp/mvr'
Moved 'file2.txt' to '/home/user/tmp/mvr'
Run mvr without args, to restore files back to their previous location
```

This moves `foo/file.txt` and `bar/file2.txt` to a temporary directory while recording their original paths.

### Move files using a file glob:
```bash
mvr *.log
```
Example:
```bash
mvr *.log
```
Output (if there are `.log` files in the current directory):
```
Moved 'logfile1.log' to '/home/user/tmp/mvr'
Moved 'logfile2.log' to '/home/user/tmp/mvr'
Run mvr without args, to restore files back to their previous location
```
This moves all `.log` files in the current directory to the temporary directory.

### Move files to a specific directory:

If the final arg is a directory, it will treat that as the destination to move the files to.

```bash
mvr <file1> [file2 ...] <destination>
```
Example:
```bash
mvr foo/file.txt bar/file2.txt /tmp/
```
Output:
```
Moved 'file.txt' to '/tmp/'
Moved 'file2.txt' to '/tmp/'
Run mvr without args, to restore files back to their previous location
```
This moves `foo/file.txt` and `bar/file2.txt` to `/tmp/` instead of the default temporary directory.

### Restore all moved files:
```bash
mvr
```
Example:
```bash
mvr
```
Output (assuming files were previously moved):
```
Restored 'file.txt' to 'foo/file.txt'
Restored 'file2.txt' to 'bar/file2.txt'
```
Running `mvr` without arguments restores all previously moved files to their original locations.

## Author
Ryan Kulla

