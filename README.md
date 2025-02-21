# mvr

## Description
`mvr` is a Bash script that allows you to move one or more files to a temporary directory and later restore them to their original locations. This is useful for temporarily removing files without permanently deleting them.

## Usage

### Move files to the temporary directory:
```bash
mvr <file1> [file2 ...]
```
Example:
```bash
mvr foo/file.txt bar/file2.txt
```
This moves `foo/file.txt` and `bar/file2.txt` to a temporary directory while recording their original paths.

### Move files using a file glob:
```bash
mvr *.log
```
This moves all `.log` files in the current directory to the temporary directory.

### Restore all moved files:
```bash
mvr
```
Running `mvr` without arguments restores all previously moved files to their original locations.

## Author
Ryan Kulla

