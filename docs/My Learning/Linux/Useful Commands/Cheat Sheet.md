# Linux Cheat Sheet

Personal collection of Linux commands and references. 

## Creating Virtual Environments

```
python -m venv /path/to/new/virtual/environment
```
or
```
python -m venv ~/Documents/
```
After executing the above command, the following files and directories are created:

- **`pyvenv.cfg`**: Configuration file containing information about the virtual environment.
- **`bin/` (or `Scripts/` on Windows)**: Directory containing copies/symlinks of Python binaries.
- **`lib/pythonX.Y/site-packages/` (or `Lib/site-packages/` on Windows)**: Initially empty directory for installing packages.

If an existing directory is specified, the command reuses it for the virtual environment.


To make file an executable, use:

```
chmod +x <filename>
```


