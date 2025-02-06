# Homebrew

[Homebrew website](https://brew.sh)

- Package manager for MacOS(and Linux) that makes it easier to install, manage, and update software from command line
## To install

Run `/bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"` on Terminal

## Created folders

```
==> This script will install:
/usr/local/bin/brew
/usr/local/share/doc/homebrew
/usr/local/share/man/man1/brew.1
/usr/local/share/zsh/site-functions/_brew
/usr/local/etc/bash_completion.d/brew
/usr/local/Homebrew
==> The following new directories will be created:
/usr/local/bin
/usr/local/etc
/usr/local/include
/usr/local/lib
/usr/local/sbin
/usr/local/share
/usr/local/var
/usr/local/opt
/usr/local/share/zsh
/usr/local/share/zsh/site-functions
/usr/local/var/homebrew
/usr/local/var/homebrew/linked
/usr/local/Cellar
/usr/local/Caskroom
/usr/local/Frameworks
```

## Where do Homebrew packages go

- `/usr/local/Cellar/<package_name>`

## See installed packages

### List all installed packages and their locations

`brew list --versions`

### See exactly directory and more information of a package

`brew info <package_name>`

## Uninstall a package

`brew uninstall <package_name>`

### Also remove unused dependecies

`brew autoremove`

## Cleanup
- When you upgrade a package, Homebrew keeps the old versions to ensure stability

### To clean those files

`brew cleanup`

### See how much space can free up

`brew cleanup -n`

## Check package usage

If unsure whether to delete a package, see which other packages depend on it:
`brew uses <package_name>`

## Packages

### `rsync`

`rsync -av --delete /Users/thisalkenula/Desktop/ /Volumes/ThisalSSD/BackUp/Desktop/`

- `-a` (archive): Preserves file permissions, timestamps, symbolic links, and other metadata.
- `-v` (verbose): Shows detailed output during the process.
- `--delete`
    - Delete files from destination if they’re no longer available in the source
- Example
    
    `rsync -av --delete /Users/thisalkenula/Desktop/ /Volumes/ThisalSSD/BackUp/Desktop/`
    
## Terminal

### Create a `.sh` file
1. Create `.sh` file
    - Example:
        
        ```python
        #!/bin/bash
        echo "Starting the backup..."
        rsync -av --delete /path/to/source/ /path/to/destination/
        echo "Backup completed successfully."
        ```
        
        `#!/bin/bash` is required to to tell the system to use the Bash shell to run the command
        
2. save
3. run `chmod +x [myscript.sh](http://myscript.sh/)` to make it an executable file
4. Run the script: `./myscript.sh`

