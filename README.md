# atomic-sync package

atomic-sync is an Atom package to sync files bidirectionally between remote host and local over ssh+rsync. It has been forked from [dingjie/atom-sync](https://github.com/dingjie/atom-sync). Inspired by [Sublime SFTP](http://wbond.net/sublime_packages/sftp).

> This package is currently in early development and has only been tested on Mac. Please kindly [try it out](http://atom.io/packages/atomic-sync) and [provide feedback](https://github.com/atymchuk/atomic-sync/issues/new).

### Features ###
* Sync over ssh+rsync — still [secure](http://www.sakana.fr/blog/2008/05/07/securing-automated-rsync-over-ssh/), but much [faster](http://stackoverflow.com/questions/20244585/what-is-the-difference-between-scp-and-rsync).
* [Multi-Folder Projects](http://blog.atom.io/2015/04/15/multi-folder-projects.html) with different sync config files supported

### Prerequisite ###
* Ensure you have `ssh` and `rsync` installed.

### Quick Start ###
* Open a project folder to sync in [Atom](http://atom.io).
* Right click on the project folder and select `Sync` -> `Edit Remote Config`.
* Edit and save the config file.
* Right click on the project folder and select `Sync` -> `Sync Remote -> Local`.
* Watch water flows.

### Notice ###
* Password based login is not supported—at least yet, you have to [assign your key file](https://www.linode.com/docs/security/use-public-key-authentication-with-ssh) and better host name in .ssh/config in advanced. Try to [Simplify Your Life With an SSH Config File](http://nerderati.com/2011/03/17/simplify-your-life-with-an-ssh-config-file/).

### Config File ###
> .sync-config.cson

```
remote:
    host: "HOSTNAME"        # server name or ip or ssh host abbr in .ssh/config
    user: "USERNAME"        # ssh username
    path: "REMOTE_DIR"      # e.g. /home/someone/somewhere
    port: "PORT_NUM"        # optional; defaults to 22

behaviour:
    uploadOnSave: true      # Upload every time you save a file
    syncDownOnOpen: true    # Download every time you open a file
    forgetConsole: false    # Never show console panel even while syncing
    autoHideConsole: true   # Hide console automatically after 1.5s
    alwaysSyncAll: false    # Sync all files and folders under the project \
                            # instead of syncing single file or folder
option:
    deleteFiles: true       # Delete files during syncing
    exclude: [              # Excluding patterns
        '.sync-config.cson'
        '.git'
        'node_modules'
        'tmp'
        'vendor'
    ]
```

### Keybindings ###
* `ctrl`+`alt`+`l` Toggle log window

### Known Problems ###
* You have to `Sync Local -> Remote` manually after renaming and deleteing files.

### Roadmap ###
* Refactoring
* ConsoleView::clean() and btnClean
* --list-only and confirm dialogue
* Listen to events
  * Create folders
  * Rename files/folders
  * What about deleting?
* SSH parameters in config file e.g. public key et al.
