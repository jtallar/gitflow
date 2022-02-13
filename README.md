# Gitflow

## Requirements
**NOTE for MacOS**: I believe the scripts have to be ran with `/usr/local/bin/bash` instead of `/bin/bash` (which would default to the old Bash). Maybe by installing it properly, you can just run it with `bash` with no path.

### Repo Requirements
- Run in an existing GIT repository
- Use SSH to clone your repo (altough you should be, HTTPs is no longer supported in GitHub).

### System Requirements
Here is the list of requirements needed:
- Bash 4 or higher.
    - Here is an [article](https://itnext.io/upgrading-bash-on-macos-7138bd1066ba) on how to update Bash in MacOS. Skip the `Set Default Shell` section, that won't be needed.
- Allow redirection to `/dev/null`.
    - Sometimes this fails with permission denied in MacOS. If so, follow what's stated [here](https://unix.stackexchange.com/questions/146633/bash-dev-null-permission-denied).
- Have the following commands installed and available:
    - `export`, `echo`, `eval`, `unset`, `exit`, `cd`, `pwd` (assumed exist)
    - `cat`, `rm`, `mkdir`, `tty`, `shasum`
    - `uname`, `dirname`, `realpath`, `readlink`
    - `sed`, `cut`, `grep`, `tr`, `wc`, `awk`
    - `nano`
    - `git`
    - `curl`
    - `jq` (>= 1.6)

You can check if you have everything required to run this program by running 
    `/bin/bash check-requirements`
The script will only check bash version, redirection to `/dev/null` and `jq` installation. Every other commands is assumed to exist (they come installed in MacOS)

## Setup
To setup `gitflow`, you must do the following:
- Create a `.env` file as explained in the file `.env-example`
- Go to your terminal configuration file (eg: .bashrc, .zshrc) and add an alias pointing to the gitflow script
    - `alias gitflow="/full/path/to/gitflow`
    - Or if MacOS: `alias gitflow="/bin/bash /full/path/to/gitflow`

## Execution
Run gitflow with
    `gitflow <subcommand>`

Available subcommands are
- `feature` Manage your feature branches.

### Subcommand - Feature
Manage your feature branches. Available actions are
- `gitflow feature [help]`	--> Display available actions
- `gitflow feature list`	--> Lists existing local feature branches
- `gitflow feature start`	--> Start new feature from base
- `gitflow feature finish`	--> Finish a feature (push, PRs, etc)
- `gitflow feature publish`	--> Publish feature to origin
- `gitflow feature track`	--> Get feature branch from origin
- `gitflow feature diff`	--> Show all changes in feature branch vs base
- `gitflow feature checkout`	--> Switch to feature branch
- `gitflow feature rebase`	--> Rebase feature branch on base
- `gitflow feature pull`	--> Pull feature branch from origin
- `gitflow feature delete`	--> Delete feature branch
- `gitflow feature rename`	--> Rename feature branch