# Gitflow

## Repo Requirements
- Run in an existing GIT repository
- Use SSH to clone your repo (altough you should be, HTTPs is no longer supported in GitHub).

## System Requirements
You can check if you have everything required to run this program by running 
    `/bin/bash check-requirements`

Here is the list of requirements needed:
- Bash 4 or higher.
- Allow redirection to `/dev/null`.
    - Sometimes this fails with permission denied in MacOS. If so, follow what's stated [here](https://unix.stackexchange.com/questions/146633/bash-dev-null-permission-denied).
- Have the following commands installed and available:
    - `export`, `echo`, `eval`, `unset`, `exit`, `cd`, `pwd` (assumed exist)
    - `cat`, `rm`, `mkdir`
    - `uname`, `dirname`, `realpath`, `readlink`
    - `sed`, `cut`, `grep`, `tr`, `wc`, `awk`
    - `nano`
    - `git`
    - `curl`
    - `jq` (TODO: check if a min version is needed)

## Setup
- Go to your terminal configuration file (eg: .bashrc, .zshrc) and add an alias pointing to the gitflow script
    - `alias gitflow="/full/path/to/gitflow`
    - Or if MacOS: `alias gitflow="/bin/bash /full/path/to/gitflow`
- Create a `.env` file as explained in the file `.env-example`